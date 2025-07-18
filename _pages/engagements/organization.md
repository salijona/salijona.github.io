---
title: "Organizations"
permalink: /engagements/organization/
layout: page
nav: false  # typically children don't appear as top-level nav
---


## Conference and Event Organization
{% for event in site.data.organization %}
  {% assign has_link = event.link %}
  {% if has_link %}
  <a href="{{ event.link }}" target="_blank" rel="noopener noreferrer" class="text-decoration-none text-reset">
  {% endif %}
  
  <div class="card mb-4 shadow-sm">
    <div class="row g-0">
      <div class="col-md-4">
        {% if event.images %}
          <div id="carousel-{{ forloop.index }}" class="carousel slide" data-bs-ride="carousel">
            <div class="carousel-inner">
              {% for img in event.images %}
                <div class="carousel-item {% if forloop.first %}active{% endif %}">
                  <img src="{{ img }}" class="d-block w-100" alt="Slide {{ forloop.index }}">
                </div>
              {% endfor %}
            </div>
            <button class="carousel-control-prev" type="button" data-bs-target="#carousel-{{ forloop.index }}" data-bs-slide="prev">
              <span class="carousel-control-prev-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#carousel-{{ forloop.index }}" data-bs-slide="next">
              <span class="carousel-control-next-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Next</span>
            </button>
          </div>
        {% else %}
          <img src="{{ event.image }}" class="img-fluid rounded-start" alt="{{ event.title }}">
        {% endif %}
      </div>

      <div class="col-md-8">
        <div class="card-body">
          <h5 class="card-title">
            {% if has_link %}
              {{ event.title }} 🔗
            {% else %}
              {{ event.title }}
            {% endif %}
          </h5>
          <p><strong>Role:</strong> {{ event.role }}</p>
          <p>{{ event.description }}</p>
        </div>
      </div>
    </div>
  </div>

  {% if has_link %}
  </a>
  {% endif %}
{% endfor %}