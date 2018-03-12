---
layout: home
---

{% assign categories = site.games | map: "categories" | uniq | sort %}
{% unless categories == empty %}
{% for gameType in categories %}
# {{ gameType | capitalize }} Games
  {% for game in site.games %}
    {% if game.categories contains gameType %}
  - [{{ game.title }}]({{ game.url | relative_url }})
    {% endif %}
  {% endfor %}
{% endfor %}
{% endunless %}

# Other Games
{% for game in site.games %}
  {% if game.categories == empty %}
  - [{{ game.title }}]({{ game.url | relative_url }})
  {% endif %}
{% endfor %}
