---
title: "testing xwayland on ubuntugnome 15.10"
date: 2015-05-30
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-05-30
Testing xwayland solves a lot of problems, ie; not having to SLAM the mouse pointer into the upper left hand corner to get the dash... but there is a problem with flickerty in ubuntuforums menus and text when scrolling , yet this does not happen on other web pages.

Firefox scrolling works much faster and smoother and there is a general feeling (or appearance) of all around 'snappiness' (not to be confused with 'snappy' ) :)

Regards..

@graham .. thanks for that link in Library :)

---

### Post by ventrical on 2015-05-30
bug here ..

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1460261](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1460261)

---

### Post by xc3RnbFO8P on 2015-05-30
How can I be sure that I run Gnome-Wayland?
I got Gnome and Gnome-Wayland sessions.

---

### Post by xc3RnbFO8P on 2015-05-30
Screenshots

---

### Post by grahammechanical on 2015-05-30
I maybe misunderstanding you but if we have hardware capable of running Gnome 3 shell on X then I would expect it to be capable of running Gnome 3 shell running on a Wayland specified compositor replacing X.

It is the same with Ubuntu. If the hardware runs Ubuntu Unity 3D on X then it will run Ubuntu Unity 3D on Mir.

The issue for all developers working on an Xserver replacement of any kind is that it supports all necessary hardware, and is supported in turn by the usual line-up of video drivers, and has a way of running X applications until the developers of those applications rewrite the applications to be independent of X.

[http://wayland.freedesktop.org/xserver.html](http://wayland.freedesktop.org/xserver.html)

[http://mjg59.dreamwidth.org/26254.html](http://mjg59.dreamwidth.org/26254.html)

Xwayland and Xmir are not the full deal as fas as I can see. As I remember we had the full Ubuntu distribution running on Xmir more than a year ago. The only family member that I could not switch to Xmir was Ubuntu Gnome and that was because GDM had not been patched to look for anything else other than X. Whereas, LightDM had been patched.

Regards.

---

### Post by xc3RnbFO8P on 2015-05-30
can I use some Terminal command showing that I use Wayland
this what I get:
> ringi@ringi-Lenovo-Ideapad-Flex-15:~$ screenfetch
                          ./+o+-       ringi@ringi-Lenovo-Ideapad-Flex-15
                  yyyyy- -yyyyyy+      OS: Ubuntu 15.10 wily
               ://+//////-yyyyyyo      Kernel: i686 Linux 3.19.0-18-generic
           .++ .:/++++++/-.+sss/`      Uptime: 2d 9h 8m
         .:++o:  /++++++++/:--:/-      Packages: 3820
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 4.3.30
       .:+o:+o/.          `+sssoo+/    Resolution: 1366x768
  .++/+:+oo+o:`             /sssooo.   WM: GNOME Shell
 /+++//+:`oo+o               /::--:.   WM Theme: DeLorean-Dark-3.14
 \+/+o+++`o++o               ++////.   GTK Theme: DeLorean-Dark-3.14 [GTK2], DeLorean-Dark-3.14 [GTK3]
  .++.o+++oo+:`             /dddhhh.   Icon Theme: Dalisha
       .+.o+oo:.          `oddhhhh+    Font: Play Regular 9
        \+.++o+o``-````.:ohdhhhhh+     CPU: Intel Core i3-4010U CPU @ 1.7GHz
         `:o+++ `ohhhhhhhhyo++os:      RAM: 1609MB / 3767MB
           .o:`.syhhhhhhh/.oo++o`     
               /osyyyyyyo++ooo+++/    
                   ````` +oo+++o\:    
                          `oo++.      
ringi@ringi-Lenovo-Ideapad-Flex-15:~$

---

### Post by deadflowr on 2015-05-30
Try
```
printenv
```
it should show wayland under XDG_SESSION_DESKTOP

---

### Post by xc3RnbFO8P on 2015-05-30
XDG_SESSION_DESKTOP=gnome

---

### Post by ventrical on 2015-05-30
@ringi


```

sudo apt-get install gnome-session-wayland

```

It will give you an option in gdm to choose the wayland protocol.

[https://lists.launchpad.net/ubuntugnome-qa/msg00702.html](https://lists.launchpad.net/ubuntugnome-qa/msg00702.html)

Regards..

---

### Post by ventrical on 2015-05-30
> **deadflowr said:**
> Try
```
printenv
```
it should show wayland under XDG_SESSION_DESKTOP

Thanx :)

```

DESKTOP_SESSION=gnome-wayland
QT_IM_MODULE=ibus
PWD=/home/ventrical
XMODIFIERS=@im=ibus
LANG=en_CA.UTF-8
GDMSESSION=gnome-wayland

```

---

### Post by ventrical on 2015-05-30
> **Ringi said:**
> XDG_SESSION_DESKTOP=gnome

here..

```

XDG_SESSION_DESKTOP=gnome-wayland
LOGNAME=ventrical

```

---

### Post by xc3RnbFO8P on 2015-05-30
I got it installed

---

### Post by Chanath on 2015-05-30
You are using Muon Package Manager on Ubuntu-Gnome. Any reason why? Is it better than Synaptic?

---

### Post by xc3RnbFO8P on 2015-05-30
I just like it better than synaptic package manager

---

### Post by xc3RnbFO8P on 2015-05-30
I got 2 GNOME in /usr/share/xsessions:

> [Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session --session=gnome
TryExec=gnome-shell
Icon=
Type=Application
DesktopNames=GNOME
X-LightDM-DesktopName=GNOME
X-Ubuntu-Gettext-Domain=gnome-session-3.0
> [Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session --session gnome-wayland
TryExec=gnome-shell
Icon=
Type=Application
DesktopNames=GNOME
X-LightDM-DesktopName=GNOME
X-Ubuntu-Gettext-Domain=gnome-session-3.0

---

### Post by Chanath on 2015-05-30
> **ventrical said:**
> Testing xwayland solves a lot of problems, ie; not having to SLAM the mouse pointer into the upper left hand corner to get the dash... but there is a problem with flickerty in ubuntuforums menus and text when scrolling , yet this does not happen on other web pages.

Firefox scrolling works much faster and smoother and there is a general feeling (or appearance) of all around 'snappiness' (not to be confused with 'snappy' ) :)

Regards..

@graham .. thanks for that link in Library :)

Thanks for pointing this out. Installed the Wayland session. Firefox starts slowly at first, but later it start pretty quickly. LibreOffice Writer, Gimp etc starts faster. Auto hiding the top panel doesn't work--it stays hidden. Scrolling in the Dash doesn't work yet. I still have to go to top left corner. I also have Dash to Dock extension installed, which does lot of work, including minimize, maximize.

---

### Post by deadflowr on 2015-05-30
> **Ringi said:**
> I got 2 GNOME in /usr/share/xsessions:
Odd.
Wayland sessions should be in /usr/share/wayland-sessions.

I've noticed lightdm and wayland is a no go.
So I have to kill it and start up gdm.
Then in the dropped down session selection it'll list *gnome on wayland*, unmistakably.

---

### Post by xc3RnbFO8P on 2015-05-30
I am using gdm
and I have  /usr/share/wayland-sessions/GNOME on Wayland
the cat must have copy it to xsessions :)

---

### Post by xc3RnbFO8P on 2015-05-30
Well I am in, no left click on touchpad and it is fast
> GDMSESSION=gnome-wayland
SHLVL=1
XDG_SEAT=seat0
HOME=/home/ringi
LANGUAGE=en_US:en
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_SESSION_DESKTOP=gnome-wayland
LOGNAME=ringi

---

### Post by xc3RnbFO8P on 2015-05-30
and screenshots

---

### Post by Chanath on 2015-05-31
How does Lenovo Flex 15 work with Gnome3 with the touchscreen, Ringi?
This might look like off topic, but there'd be more touch screens in the future, so the question.
Also, how did you install Ubuntu-Gnome alongside Windows, or are you having it without Windows?

---

### Post by ventrical on 2015-05-31
A whole bunch of mir updates including a new libmircommon4 package. I wonder what gives?

```

Preparing to unpack .../libmircommon4_0.13.1+15.10.20150520-0ubuntu1_amd64.deb ...
Unpacking libmircommon4:amd64 (0.13.1+15.10.20150520-0ubuntu1) ...
Preparing to unpack .../libmirprotobuf0_0.13.1+15.10.20150520-0ubuntu1_amd64.deb ...
Unpacking libmirprotobuf0:amd64 (0.13.1+15.10.20150520-0ubuntu1) over (0.12.1+15.04.20150324-0ubuntu1) ...
Preparing to unpack .../libmirclient8_0.13.1+15.10.20150520-0ubuntu1_amd64.deb ...
Unpacking libmirclient8:amd64 (0.13.1+15.10.20150520-0ubuntu1) over (0.12.1+15.04.20150324-0ubuntu1) ...
Preparing to unpack .../mir-client-platform-mesa2_0.13.1+15.10.20150520-0ubuntu1_amd64.deb ...
Unpacking mir-client-platform-mesa2:amd64 (0.13.1+15.10.20150520-0ubuntu1) over (0.12.1+15.04.20150324-0ubuntu1) ...

```

---

### Post by xc3RnbFO8P on 2015-05-31
> **Chanath said:**
> How does Lenovo Flex 15 work with Gnome3 with the touchscreen, Ringi?
This might look like off topic, but there'd be more touch screens in the future, so the question.
Also, how did you install Ubuntu-Gnome alongside Windows, or are you having it without Windows?

Not off topic, I tested my touch screen in this Gnome Wayland and it works well. I cant "double click", dont know to enable it.
There is no real program for touch screens at the moment, Chromium works well (resize, swipe back and forth), you just have to make windows button bigger.
I tried Unity Next, wonder if it is gone be ready in 16.04.

---

### Post by Chanath on 2015-05-31
> **Ringi said:**
> Not off topic, I tested my touch screen in this Gnome Wayland and it works well. I cant "double click", dont know to enable it.
There is no real program for touch screens at the moment, Chromium works well (resize, swipe back and forth), you just have to make windows button bigger.
I tried Unity Next, wonder if it is gone be ready in 16.04.

Ringi, maybe you should open a new topic with this. I used Lenovo Yoga with Windows RT 8.1 once, but sold it. I'm not that keen on Windows, but would be happy to use Ubuntu/Linux with touchscreen. Your and others experience would help. I'd like to buy a touchscreen in the future.

---

