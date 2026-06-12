---
title: "Apache2 Question"
date: 2010-10-30
forum: Server Platforms
---

### Post by Vegan on 2010-10-30
I was wondering of APache2 needs configuration or mods or ? to support conditional get.

[http://www.microsoft.com/search/Tools/default.aspx]("http://www.microsoft.com/search/Tools/default.aspx")

---

### Post by Ryan Dwyer on 2010-10-31
I'm sure Apache does this out of the box, whether it be part of the core or part of a module that's enabled by default.

---

### Post by Vegan on 2010-11-01
I ran my site against that checker and it said its not. Try it and see with any URL you want.

---

### Post by Ryan Dwyer on 2010-11-01
It only works on static content. Run the checker with this URL:
[http://www.contract-developer.tk/images/bg_body.jpg](http://www.contract-developer.tk/images/bg_body.jpg)

It fails because you modified it on the 12th of October and the default date selected is the 11th. If you change the date to the 13th then run again it works.

---

### Post by Vegan on 2010-11-02
I use mostly PHP for my pages, for example the date stamp is a chunk of PHP.

Virtually all my pages are dynamic, but I tried a number of sites, and it seems few work with conditional get.

---

