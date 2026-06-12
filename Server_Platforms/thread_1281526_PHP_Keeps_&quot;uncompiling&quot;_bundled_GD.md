---
title: "PHP Keeps &quot;uncompiling&quot; bundled GD?"
date: 2009-10-03
forum: Server Platforms
---

### Post by bacterozoid on 2009-10-03
Ubuntu server doesn't use a version of PHP with bundled GD due to security issues, and thus lacks support for functions like imagefilter. I recompiled PHP with the bundled version of GD, restarted apache and found that the GD library was working with all the functions I was using.

However, I've done that TWICE now. After some period of time I go back and try to use those GD functions and I get an error saying they do not exist. I'm not quite sure what's going on here...any ideas?

---

