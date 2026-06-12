---
title: "SLiM Failed to execute login command"
date: 2015-07-02
forum: Ubuntu/Debian BASED
---

### Post by btunny on 2015-07-02
Hello
I am trying to setup the Ubuntu minimal installation to have a basic gui. I have openbox as window manager, cairodock, and SLiM as my display manager. I have setup my xinitrc as follows:
________________________________________________
#!/bin/sh
# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession
exec /bin/sh/login
exec slim
exec openbox-session
exec cairo-dock
________________________________________________

SLiM Shows up, but when I try to login, I get that message.
please tell me what I am doing wrong
thanks

---

### Post by v3.xx on 2015-07-02
I do not know how "exec slim" is suppose to work.  Where did you find that?

Take a look at arch.
[https://wiki.archlinux.org/index.php/SLiM#Configuration](https://wiki.archlinux.org/index.php/SLiM#Configuration)

I have not used slim in years, I remember it was a pain to set up and just using startx (with scripts) was better for me.

[https://wiki.archlinux.org/index.php/Xinitrc](https://wiki.archlinux.org/index.php/Xinitrc)

---

### Post by v3.xx on 2015-07-02
Just notice this
> [h=3]Enabling SLiM[/h]**Note: **[slim]("https://www.archlinux.org/packages/?name=slim") relies on *systemd-logind*. 

---

### Post by btunny on 2015-07-02
UPDATE:I switched to lxdm. thanks anyway!

---

