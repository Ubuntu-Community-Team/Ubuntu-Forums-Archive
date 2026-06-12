---
title: "How to disable xfce by default"
date: 2006-07-24
forum: Server Platforms
---

### Post by kenquad on 2006-07-24
Hi all:

I'm sure this a simple question.  I hope so, anyway.  I have installed xfce on my server for admin tasks but I don't want it to come on at boot time by default.  How do I take care of this?

Ken Ha Quad

---

### Post by Kurt` on 2006-07-24
You can remove it (gdm, or whatever) from /etc/X11/default-display-manager

Not sure if that's the "proper" way, but it worked for me.

---

### Post by kenquad on 2006-07-24
But wouldn't that disable xfce permanently?  I want to be able to start it when necessary.

---

### Post by Kurt` on 2006-07-24
Well on the desktop-turned-server machine I have (running gnome), after disabling the default X11 display manager, I just type /etc/init.d/gdm start, and my login screen comes up.

(of course, then I have to ctrl-alt-F1 back to the root console that started it and logout, then ctrl-alt-f7 back into gnome)

---

### Post by harisund on 2006-07-24
basically GDM starts up when you boot. 

If you execute ```
sudo update-rc.d -f gdm remove
``` this prevents GDM from starting up everytime. 

If you want to start XFCE from the command line you would do ```
sudo invoke-rc.d gdm start
``` and you would get your regular GUI. 

The only problem I see is if there is a software update to the gdm package, you will once again have gdm running every time you reboot and will once again have to execute ```
sudo update-rc.d -f gdm remove
```

---

### Post by Kurt` on 2006-07-24
Cool, thanks for the post! :)

---

### Post by kenquad on 2006-07-24
Okay.  But I found another way in the interim that seems to work.  If you go into system services within xfce and un-check the GDM service, it seems to keep it from starting automatically.  It can be started later with startx.  This didn't work at first but later began to.  ???

---

