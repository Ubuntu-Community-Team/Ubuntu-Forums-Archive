---
title: "rss filter for shows with generic names like house"
date: 2011-07-22
forum: The Cafe
---

### Post by newbiefly on 2011-07-22
i wrote va cool little regex for my sabnzbd+ rss filters that i'd like to share.  i believe other programs use regex support for their filters too like vuze. so on my recent new install of ubuntu i forgot to copy sabnzbd.ini and have been rebuilding my filters and have recently discovered a nice little regex filter i think you guys might find useful. see the problem is i like shows with generic names like house, mad, and treme but when you accept house you don't just get house you get tyler perry's house of pain, clean house, this old house, ALL the different kinds of real hosewives, etc. but all the house episodes i want are format "house S06E09..." so in my regex i use the carat(^) to denote primary location in the string followed by SXXEXX to get:```
re:^house.S[0-9][0-9]E[0-9][0-9]*
```its been very effective for other shows too:```
re:^mad.S[0-9][0-9]E[0-9][0-9]*
re:^episodes.S[0-9][0-9]E[0-9][0-9]*
re:^treme.S[0-9][0-9]E[0-9][0-9]*
re:^extreme.cuponing.S[0-9][0-9]E[0-9][0-9]*
re:^top.gear.S[0-9][0-9]E[0-9][0-9]*
re:^top.gear.[0-9][0-9]*
```see i like british top gear but don't like top gear us or top gear au but need an extra rule because sometimes format is "top gear S17E03" other times "top gear 17x02"

here is a little filter i've worked out for new shows:```
Reject re:^ice.pilot*
Accept *pilot*
Accept s01e01
Accept s00e00
```try and use it as an rss filter for some of your favorite shows and let me know how it works for you or if you have any better ideas

---

