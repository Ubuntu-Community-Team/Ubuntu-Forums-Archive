---
title: "planetplanet: Planet section missing error message"
date: 2008-05-11
forum: Server Platforms
---

### Post by utopyr on 2008-05-11
I'm trying to set up a feed aggregator on my server, & have first tried Planet, since that's in the repositories. I'm hoping this will save somebody else the trouble of figuring this one out.

I was hoping to run it so that the output appeared in a subdirectory of one of my users' public_html directory. After installing planet, I configured /etc/planet.conf to point there. When I then ran planetplanet, I got this:
```
me@thatplace:/home/$user/public_html/lwf$ sudo planetplanet
Configuration missing [Planet] section.
```

Couldn't find any instructions specific to Ubuntu, but did find a couple for Debian. Tried the simplest thing:
```
me@thatplace:/home/$user/public_html/lwf$ sudo planetplanet /etc/planet.conf
```

It works. Need to figure a couple more details to pretty it up, but it works.

---

