---
title: "[SOLVED] IFTOP running in a screen session"
date: 2008-08-05
forum: Server Platforms
---

### Post by kihjin on 2008-08-05
So I'd like to run iftop in a screen session like so:

screen -S Bandwidth iftop

but, this is what it looks like in screen.

If I run iftop outside of screen, it looks fine, however I don't have the ability to detach it.

[solved]

blame cygwin... display works perfectly in ubuntu from home..

---

