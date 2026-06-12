---
title: "PHP options"
date: 2009-03-25
forum: Server Platforms
---

### Post by Vegan on 2009-03-25
In a book I have, PHP Programming, Oreily, there is a table in the back that enumerate all manor of extensions that the table suggested you need to add in a build of PHP to enable.

Things like Oracle (no needed), ZIP and the like.

Are all these extensions enabled with the disto here?

---

### Post by Bachstelze on 2009-03-25
[font="monospace"]phpinfo();[/font] will tell you.

---

### Post by Danilo Chilene on 2009-03-25
You can check with phpinfo().

Also if you wanna know what new extensions you can install just type:
apt-cache search php5-

---

