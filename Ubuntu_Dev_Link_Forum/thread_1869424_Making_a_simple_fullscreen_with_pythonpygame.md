---
title: "Making a simple fullscreen with python/pygame?"
date: 2011-10-25
forum: Ubuntu Dev Link Forum
---

### Post by frenchn00b on 2011-10-25
Hello,

I would like to know slightly how to make something like this under python/pygame in fullscreen? 

Would you have a begin of code for this simple thing, to help to start? 

thank you in advance !

---

### Post by VirtualOzelot on 2011-10-30
If I recall correctly, fullscreen can be activated by the display.set_mode() method any time after pygame and pygame.display have been initialized; for example by doing:

```
pygame.display.set_mode((640,480),pygame.FULLSCREEN)

```

...where (640,480) is the desired resolution. There's a great set of tutorials on [http://pygame.org/docs/]("http://pygame.org/docs/") that will help you get started.

---

