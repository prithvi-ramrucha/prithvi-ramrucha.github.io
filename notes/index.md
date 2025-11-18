---
layout: page
title: Notes
permalink: /notes/
---

<div class="notes-index">
  <h1>Study Notes & Books</h1>
  <p>Collection of my study notes and reference materials organized as books.</p>
  
  <div class="books-grid">
    {% assign books = site.books | where: "layout", "book_index" | sort: "order" %}
    {% for book in books %}
      <div class="book-card">
        <h2><a href="{{ book.url }}">{{ book.book_title }}</a></h2>
        {% if book.description %}
          <p class="book-description">{{ book.description }}</p>
        {% endif %}
        
        {% assign chapter_count = site.books | where: "book", book.book | size %}
        <div class="book-meta">
          <span class="chapters">{{ chapter_count | minus: 1 }} chapters</span>
          {% if book.tags %}
            <div class="book-tags">
              {% for tag in book.tags %}
                <span class="tag">{{ tag }}</span>
              {% endfor %}
            </div>
          {% endif %}
        </div>
        
        <div class="book-progress">
          <div class="progress-bar">
            <div class="progress" style="width: {% if book.progress %}{{ book.progress }}{% else %}0{% endif %}%"></div>
          </div>
          <span class="progress-text">{% if book.progress %}{{ book.progress }}% complete{% else %}Not started{% endif %}</span>
        </div>
      </div>
    {% endfor %}
  </div>
</div>
