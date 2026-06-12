---
title: "Need help with stuff on ubuntu server.."
date: 2008-10-07
forum: Server Platforms
---

### Post by judgey on 2008-10-07
Hey all i just installed ubuntu804-server - 32 bit. The server is not hosted in my country. I use Putty to connect to it.

Things i need todo -

1st i need to access its desktop, wot do i need to install so i can use vnc to access the desktop.

Many thx, im a nub so cmd lines would be great

:)

---

### Post by darkmode on 2008-10-07
first you have to install xserver and the gnome desktop try :

apt-get install x-window-system-core xserver-xorg gnome-desktop-environmen

when you finish you have to install the VNC-server :

1) Install packages 
sudo aptitude install x11vnc vnc-java
2) Set up password to allow clients to view
x11vnc -storepasswd
3) Open up ports 5800 and 5900 on your firewall

4) Run this command:
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800

That's it!

And an optional step 5:

5) Add the command from 4) to your sessions, so that it starts at each login

If you want to test it out on a browser, type this in the URL field:

25.542.161.414:5800

Of course, replace the 25.etc. w/ your external IP address.

but i prefer to use webmin for as server administrator check this
[http://www.webmin.com](http://www.webmin.com)

---

### Post by judgey on 2008-10-07
Many thx for taking time to help m8

On the 1st cmd line im getting -

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package x-window-system-core is a virtual package provided by:
  xorg 1:7.3+10ubuntu10.2
You should explicitly select one to install.
E: Package x-window-system-core has no installation candidate

Wot should i do

Many thx again :)

---

### Post by analoog on 2008-10-07
-oop wrong topic-

---

### Post by lykwydchykyn on 2008-10-07
all you need to install is xorg and gnome.  That takes care of all the dependencies:
```

sudo aptitude install xorg gnome

```

---

### Post by judgey on 2008-10-08
Hey guys, nearly there...

When i try to login via http it just disconets and i get this from ssh..

08/10/2008 09:45:11 wait_for_client: running: env X11VNC_SKIP_DISPLAY='' /bin/sh /tmp/x11vnc-find_display.SqWtyK
xauth:  creating new authority file /root/.Xauthority
08/10/2008 09:45:11 wait_for_client: find display cmd failed
08/10/2008 09:45:11 wait_for_client: FINDCREATEDISPLAY cmd: /bin/sh /tmp/x11vnc-find_display.SqWtyK Xvfb
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
trying N=20 ...
08/10/2008 09:45:11 wait_for_client: read failed: /bin/sh /tmp/x11vnc-find_display.SqWtyK Xvfb
08/10/2008 09:45:11 fgets: Bad file descriptor
root@ks363461:~#


Any help would be kool :)

---

### Post by judgey on 2008-10-08
Done the same cmd got this

root@ks363461:~# x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 580
08/10/2008 11:14:05 passing arg to libvncserver: -httpport
08/10/2008 11:14:05 passing arg to libvncserver: 580
08/10/2008 11:14:05 -usepw: found /root/.vnc/passwd
08/10/2008 11:14:05 x11vnc version: 0.9.3 lastmod: 2007-09-30
08/10/2008 11:14:05
08/10/2008 11:14:05 *** XOpenDisplay failed. No -display or DISPLAY.
08/10/2008 11:14:05 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
08/10/2008 11:14:05 *** 1 2 3 4
08/10/2008 11:14:09

08/10/2008 11:14:09 ***************************************
08/10/2008 11:14:09 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.

---

### Post by judgey on 2008-10-08
plz help, i only have 4 days left with this test server b4 i have to move my sites over :(

---

### Post by lykwydchykyn on 2008-10-08
After installing xorg and gnome, did you start it?  Sounds like the display isn't active.  Maybe try this:
```

sudo invoke-rc.d gdm restart

```

Then try your vnc command.  I've never used X11vnc myself, I always used vnc4server or tightvncserver.

---

### Post by judgey on 2008-10-09
thx for taking your time out to try and help m8, but that did not work. Im going to give up i only have the server for less than 40 hours boo! So going to leave it for now.

Again thx

---

### Post by cariboo on 2008-10-09
I note that you are connecting to your server as root, that is not very secure. Try connecting as a normal user and using sudo, that may stop some of your problems.

Jim

---

