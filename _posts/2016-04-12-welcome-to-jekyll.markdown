---
layout: post
title:  "Om Jekyll"
date:   2016-04-12 11:32:13 +0200
categories: jekyll update
---


*Trädstrukturen* i en standard Jekyllsite finns på [denna sida](https://jekyllrb.com/docs/structure/).

[Front matter](https://jekyllrb.com/docs/frontmatter/) är Jekylls sätt att handskas med inledningen på varje sida. Syntaxen är så här:

[//]: # (Kommentar i Markdown, som inte publiceras skrivs så här)

    ---
    layout: post
    title: Blogging Like a Hacker
    ---

##Postinlägg

Jekyll är "inställd" på att skriva postinlägg. Det räcker med att lägga till en fil i  mappen \_posts. Den måste ha en giltig FrontMatter. Namnet måste ha följande syntax:

    YYYY-MM-DD-name-of-post.MARKUP

Filändelsen kan vara .md för markdown, om man använder det. Om man vill länka till en sida inom sajten, kan man använda  följande syntax, med *post_url*

     post_url 2010-07-21-name-of-post    - i liquidtaggar

##Infoga bild mm

Ett vanligt sätt att lagra bilder m.m. är i mappen *assets* eller *downloads*. Att länka dit gör man lämpligen med variablen *site.url*. Ex så här:

    .. you can [get the PDF]({{ site.url }}/assets/mydoc.pdf) directly

    Men - om webbplatsen finns i rooten räcker det med: /path/file.jpg

För att skapa en förteckning över poster på sajten är denna koden bra. bygger på liquid:

[//]: # (Här använder jag escapetaggarna i liquid som inledning och avslutning:)

    {% raw %}
    Här använder jag escapetaggarna i liquid, för att visa koden, dvs.: {% raw %} och
    {{ {%  }} endraw %} (Hur man nu escapar dem...)
    {% endraw %}

Det blir så här:

    {% raw %}
    <ul>
    {% for post in site.posts  %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
        </li>   
     {% endfor %}
    </ul>
    {% endraw %}

Det går bra att göra [utdrag ur poster](https://jekyllrb.com/docs/posts/#post-excerpts)


### Utkast
Det är enkelt att skapa utkast. Lägg filen i \_dratfs-mappen. För att visa använd

    jekyll serve --drafts

Dessa kommer att få tidsstämpel för uppdatering och visas överst.

Ville inte funka när jag testade.


### Sidor    
Det finns två huvudsätt att [skapa sidor](https://jekyllrb.com/docs/pages/) - och en genväg.

1. Antingen skapa html/md-filer i rooten. Ger filnamn som url.
2. Eller skapa en underkatalog med en index html/md fil i. Det ger en snygg url till mappen.
3. Det går att få en snygg url om man i FrontMatter använder variabeln *permalink*. Ex för koden

    permalink: /diverse

så blir url:en /diverse/ - även om sidan ligger i roten.




[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
