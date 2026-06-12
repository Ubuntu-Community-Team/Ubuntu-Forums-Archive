---
title: "GNOME-SESSION in VNC producing errors on Startup"
date: 2015-10-25
forum: Server Platforms
---

### Post by bstrawt90 on 2015-10-25
Hi All-

I am back and running my home systems again. Question:

I have installed Ubuntu Server 14.04 LTS and installed vnc4server and gnome-core, hoping to run a vnc session and start gnome-core desktop so I can control desktop for tools such as android studio.

However when I start a vnc session and try```
 gnome-session 
```I receive the following error:


```
gnome-session-is-accelerated: Nocomposite extension.
gnome-session-check-accelerated: Helper Exited with code 256
gnome-session-is-accelerated: No Composite extention
gnome-session-check-accelerated: Helper Exited with code 256
gnome-session[15004]: WARNING: software acceleration checkfailed: Child exited with code 1
gnome-session[15004]: CRITICAL: We failed, but the fail whale is dead.

```

My xstartup script is default as:

```
#!/bin/sh


# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &



```


Am I missing anything? Thanks in advance!

Strizzy

---

### Post by sandyd on 2015-10-25
Moved to *Server Platforms*

---

### Post by TheFu on 2015-10-25
Remote desktops don't work well, if at  all, with heavy GUIs like Unity/Gnome. Look to XFCE, LXDE, or a pure WM-only solution like openbox, fvwm, fluxbox...etc.

BTW,  vnc is sorta slow and definitely not secure.  x2go solves both those issues and might be worth a look.

---

### Post by bstrawt90 on 2015-10-27
Thanks for the heads up. I will be looking into these and already found, what looks like, to be a good guide. [https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative](https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative)

---

### Post by TheFu on 2015-10-27
> **bstrawt90 said:**
> Thanks for the heads up. I will be looking into these and already found, what looks like, to be a good guide. [https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative](https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative)

For any lurkers ... 

a) Best to get into the habit of following guides from the help.ubuntu.com sites, if they aren't too out of date and apply for the release you are on. 
b) Next, look to the software author for their How-To.  I know the x2go folks have GREAT documentation which also lists some gotchas. Use their PPA, definitely.
c) HowToForge is reputable (in my RSS feed list), however, not always secure with their setups. I didn't look over this guide, so cannot say if they handled some of the known security issues. I do know that FreeNX (older NX implementation) shipped with pre-installed ssh-keys that everyone had. Not exactly secure if you didn't remove those and recreate them fresh. Just sayin'.  Security is where those details matter.  I wonder how many people are using NX with highly published keys still ... after all, it does work and it is ssh. ;(

AskUbuntu and these forums are the next places to check.  Lots of eyes should catch mistakes in how-tos and questions. That's the theory.

---

### Post by bstrawt90 on 2015-10-28
> **TheFu said:**
> For any lurkers ... 

a) Best to get into the habit of following guides from the help.ubuntu.com sites, if they aren't too out of date and apply for the release you are on. 
b) Next, look to the software author for their How-To.  I know the x2go folks have GREAT documentation which also lists some gotchas. Use their PPA, definitely.
c) HowToForge is reputable (in my RSS feed list), however, not always secure with their setups. I didn't look over this guide, so cannot say if they handled some of the known security issues. I do know that FreeNX (older NX implementation) shipped with pre-installed ssh-keys that everyone had. Not exactly secure if you didn't remove those and recreate them fresh. Just sayin'.  Security is where those details matter.  I wonder how many people are using NX with highly published keys still ... after all, it does work and it is ssh. ;(

AskUbuntu and these forums are the next places to check.  Lots of eyes should catch mistakes in how-tos and questions. That's the theory.


Thanks for the wisdom here. Really appreciate that. I will start paying closer attention to the guides from a security stand point as well, Good call out.

---

### Post by bstrawt90 on 2015-10-28
> **TheFu said:**
> Remote desktops don't work well, if at  all, with heavy GUIs like Unity/Gnome. Look to XFCE, LXDE, or a pure WM-only solution like openbox, fvwm, fluxbox...etc.

BTW,  vnc is sorta slow and definitely not secure.  x2go solves both those issues and might be worth a look.


Hi- So I installed LXDE and x2goserver + x2goserver-session. When I run the client on my win 8.1 PC I receive the error in the attached photo.

Any ideas?

---

