---
title: "GUI problems with 6.06 Server"
date: 2006-06-22
forum: Server Platforms
---

### Post by cltrenholm on 2006-06-22
Hi all,

New to Ubuntu and I installed v6.06 Server yesterday on a Dell Desktop so that I could get familiar with it. The install was fairly straighforward however when I startup the system, the GUI doesn't initialize. No big deal as I did some snooping and found the exec file to start the xession.

Ran "X" at the prompt and it appears to do something but then it returns me to a command line and returning errors, two of which are:

Error opening /dev/wacom : No such file or directory - self explanatory

Could not init font path element /usr/share/X11/fonts/blahblah - this is due to the fact that there is no fonts directory under X11.

Is any of this familiar to someone? If so, is there a small step that I am missing?

---

### Post by DanielArdelian on 2006-06-22
The Server edition does not come with a GUI. 
If you really want to install a GUI, run:

```
 apt-get install ubuntu-desktop 
```

and then run "startx" at the command prompt.

---

### Post by cltrenholm on 2006-06-22
Thank you.

---

### Post by foxystoatyweasely on 2006-08-06
I've installed the GUI on the server no problem but I don't want it to run automatically when it boots up. Can someone tell me please which config file(s) I need to edit so that I can just run startX from the command line?

Thanks.

---

### Post by az on 2006-08-06
Either remove the GDM package or remove the gmd symlink in /etc/rc2.d.

And you may need the linux-386 kernel if some of your desktop hardware does not work.

---

