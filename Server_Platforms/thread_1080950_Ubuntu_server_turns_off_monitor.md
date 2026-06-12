---
title: "Ubuntu server turns off monitor"
date: 2009-02-25
forum: Server Platforms
---

### Post by Cl0cKw0rK on 2009-02-25
Ubuntu server by default turns the screen blank after a certain amount of time. Is there a way to stop it from doing this?
Thanks.
~Clockwork

---

### Post by kevin11951 on 2009-02-26
> **Cl0cKw0rK said:**
> Ubuntu server by default turns the screen blank after a certain amount of time. Is there a way to stop it from doing this?
Thanks.
~Clockwork

I have the same problem, let me know if you find a fix for this.

---

### Post by volkswagner on 2009-02-26
I had followed kevin11951's [thread]("http://ubuntuforums.org/showthread.php?t=1063566") out of curiosity, a couple weeks back.

I am still wondering why you would want the screen to stay active.

I don't have a monitor attached to my server so I can't do any tests, but I was wondering if a running task such as top will stop the screen from blacking out.

```
top
```

---

### Post by Cl0cKw0rK on 2009-02-26
Well, i don't know if top would do it. im running a cp -v with a lot of files being transfered, and it still turns the monitor off. Also, running top defeats the purpose of being able to see whats going on.

---

### Post by jdcnosse on 2009-02-26
I just press the NumLock key on my keyboard and it comes back...it never seemed to bother me but if there's a way to stop it, then I'll gladly except it :)

I run my server headless too, so the only time I ever actually use it locally is if I connect my monitor to it and use the keyboard connected to it...

---

### Post by Inigo Montoya on 2009-02-26
> To turn off Linux system console power saving mode, use the setterm command. For example, append these two lines in the login scripts

setterm -blank 0
setterm -store
[http://bloggerdigest.blogspot.com/2006/10/disable-linux-console-power-saving-mode.html](http://bloggerdigest.blogspot.com/2006/10/disable-linux-console-power-saving-mode.html)

---

