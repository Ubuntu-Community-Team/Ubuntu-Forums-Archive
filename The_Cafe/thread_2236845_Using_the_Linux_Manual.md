---
title: "Using the Linux Manual"
date: 2014-07-29
forum: The Cafe
---

### Post by anon_private on 2014-07-29
I find that if I want some information I try using the manual.

man -k something.

I often find that I get not found type of messages.

Has anyone any tips for using the manual when one knows the topic, but not the right language, commands, etc?

---

### Post by vasa1 on 2014-07-29
See```
man apropos
```That may provide some pointers.

---

### Post by tgalati4 on 2014-07-29
Let's say I want to know more about bluetooth:

```
apropos bluetooth
apt-cache search bluetooth
man hcitool
```

The first gives you what is available on your system.  The second command gives you what is available in the repositories (and could be installed).  The third gives you a help page on a specific tool that you discovered in the first two.

---

### Post by ibjsb4 on 2014-07-29
There are also on-line tools.

[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

---

### Post by anon_private on 2014-07-29
Thank you.

These help

Best wishes

---

