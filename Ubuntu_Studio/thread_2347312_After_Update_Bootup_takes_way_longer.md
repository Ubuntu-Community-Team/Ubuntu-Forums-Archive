---
title: "After Update Bootup takes way longer"
date: 2016-12-23
forum: Ubuntu Studio
---

### Post by James_Dunn on 2016-12-23
I am running Ubuntu Studio 16.04.1. I installed a new update on Dec/2016. I used to get a boot screen in about 5 seconds after power on. Now it takes 20 seconds or longer. The screen is blank while it is booting. Finally it does the usual boot.  Is something going on ? Why the long delay with a blank screen in the booting process? One of the things I liked about Ubuntu Studio was the short boot up time. Now it takes as long as win7.

Today I timed it. From the end of the bios screen when the screen goes blank it was 65 seconds until anything Ubuntu came on screen. One more problem. My wacom Tablet doesn't work with Inkscape or GIMP. It was working fine before. If there is a way to tell what the last update was, or better yet how to roll it back please let me know.

---

### Post by Autodave on 2017-01-03
Since no one has jumped into this yet, let me offer one thing you can try. From the terminal, type, *sudo apt-get update* .  Enter your password when asked. After that is done, type, *sudo apt-get upgrade .* Let that run and finish. Reboot to allow the new updates to finish installing. Now, reboot again and see if you are better than before.

---

### Post by howefield on 2017-01-03
> **James_Dunn said:**
> I am running Ubuntu Studio 16.04.1.

What was the update that caused the issue ? You'll find some clues in ..

```
/var/log/apt/history.log
```
```
/var/log/apt/term.log
```

If it was a new kernel, try booting into the previous one, does that one still boot quicker ?

---

