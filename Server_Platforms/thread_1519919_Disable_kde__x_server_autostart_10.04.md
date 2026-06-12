---
title: "Disable kde / x server autostart 10.04"
date: 2010-06-28
forum: Server Platforms
---

### Post by syuzh on 2010-06-28
Hi.
I installed KDE for very limited uses. However, everytime I start up, it brings me to the KDE login screen. I want to revert it back to console login. How do I go about doing that? And if possible, prevent future GUI packages from autostarting.

Thanks!

OK, so this seemed to work:[FONT=monospace]
[/FONT]```
sudo mv -f /etc/init/kdm.conf /etc/init/kdm.conf-disabled
```
That basically renames it so it doesn't start.
And if you do need to use the GUI, just run
startx

---

### Post by cariboo on 2010-06-29
All you have to do is remove kdm and start X manually when you need it. To remove kdm, at the prompt type:

```
sudo apt-get purge kdm
```

Then when you need a desktop just type:

```
startx
```

at the prompt

---

### Post by syuzh on 2010-06-30
Hey, that's even better. Thanks!

---

