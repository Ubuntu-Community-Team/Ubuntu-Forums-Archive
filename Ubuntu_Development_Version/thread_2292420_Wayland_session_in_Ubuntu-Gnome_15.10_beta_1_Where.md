---
title: "Wayland session in Ubuntu-Gnome 15.10 beta 1? Where?"
date: 2015-08-27
forum: Ubuntu Development Version
---

### Post by e270889o on 2015-08-27
I've just install the last version of Ubuntu-gnome 15.10 beta 1 

They said that it includes a wayland session for testing but I cannot find it. 

I have tried wayland in 15.04 installing it but I thought 15.10 beta 1 would include it by default. 

Do I need to install it too in 15.10 beta 1 o it is hidden waiting for some command to be activated?

Thanks

---

### Post by dino99 on 2015-08-28
wayland packages are into the archive; but the default is still X11

---

### Post by ventrical on 2015-08-28
> **e270889o said:**
> I've just install the last version of Ubuntu-gnome 15.10 beta 1 

They said that it includes a wayland session for testing but I cannot find it. 

I have tried wayland in 15.04 installing it but I thought 15.10 beta 1 would include it by default. 

Do I need to install it too in 15.10 beta 1 o it is hidden waiting for some command to be activated?

Thanks

Choose 'Gnome on Wayland' at the login. After you click /username/ a cog will come up Click that and it should give you option to login to wayland - unless ppa is still required.

Regards..

---

### Post by e270889o on 2015-08-28
No Wayland at login, thats what i mean.

---

### Post by flocculant on 2015-08-28
> **e270889o said:**
> ...
I have tried wayland in 15.04 installing it but I thought 15.10 beta 1 would include it by default. 

Do I need to install it too in 15.10 beta 1 o it is hidden waiting for some command to be activated?

Thanks
You need to install it.

> Experimental wayland session is now available. Install gnome-session-wayland and then select "GNOME on wayland" from login screen (Only works with OSS GPU drivers). 

[https://wiki.ubuntu.com/WilyWerewolf/Beta1/UbuntuGNOME#Software_Updates](https://wiki.ubuntu.com/WilyWerewolf/Beta1/UbuntuGNOME#Software_Updates)

---

### Post by zika on 2015-12-30
I know I'm guilty for using PPAs but, aside from that, what is the future of Waland in XX?```
:~$ sudo apt-get install -s gnome-session-wayland
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-session-wayland : Depends: gnome-session-bin (< 3.19) but 3.19.2+git20151227-0ubuntu2~xenial1 is to be installed
                         Depends: gnome-session-common (= 3.18.1.2+git20151107-0ubuntu1~xenial1) but 3.19.2+git20151227-0ubuntu2~xenial1 is to be installed
E: Unable to correct problems, you have held broken packages.
```I've been using Wayland from CLI but that is not possible either or some time. I'm aware of a point when gnome-session-wayland was purged in order to make room for other Gnome pieces to be installed. Just checking if there is anybody who know what the future is for Wayland in XX... ;)
I know I'm guilty, here, of sort of cross-threading but I felt more appropriate to post my question here than to open new thread. If I was wrong I hope officials will correct that mistake of mine.

---

### Post by tista on 2015-12-30
@zika,

Are you using my PPA? : [https://launchpad.net/~tista/+archive/ubuntu/wayland](https://launchpad.net/~tista/+archive/ubuntu/wayland)
In my PPA, 'gnome-session-wayland' package is now outdated because Next Fedora would do this as well. Yes, now the combination of Gdm 3.19.x and Gnome-session 3.19.x is detecting wayland-capability on your system automatically, and if it's true, it tries to load xwayland 1st as higher priority than classical X11 session. If you guys don't want to run gdm/gnome-shell with xwayland, please set it in /etc/gdm3/custom.conf to avoid loading xwayland:
```
[daemon]
WaylandEnable=false
```
After that, gdm would ignore any /usr/share/wayland-session/* desktop files and then runs itself with X11.

I don't know why though, but ricotz may have a bit different opinion for this upstream change. In a couple of weeks ago, he still produced gnome-session-wayland package on his famous PPA...

Regards,
Tista

---

### Post by tista on 2015-12-30
Oh forgot to mention...

Gnome-session 3.19.x package provides both **GNOME** and **GNOME on Xorg** session entries on Gdm. So if you guys want to load classical gnome-shell/X11 session, please select "GNOME on Xorg". As I said above, "GNOME" session is today for use of both xwayland and x11.

Regards,
Tista

---

### Post by zika on 2015-12-30
> **tista said:**
> @zika,

Are you using my PPA? : [https://launchpad.net/~tista/+archive/ubuntu/wayland](https://launchpad.net/~tista/+archive/ubuntu/wayland)
In my PPA, 'gnome-session-wayland' package is now outdated because Next Fedora would do this as well. Yes, now the combination of Gdm 3.19.x and Gnome-session 3.19.x is detecting wayland-capability on your system automatically, and if it's true, it tries to load xwayland 1st as higher priority than classical X11 session. If you guys don't want to run gdm/gnome-shell with xwayland, please set it in /etc/gdm3/custom.conf to avoid loading xwayland:
```
[daemon]
WaylandEnable=false
```
After that, gdm would ignore any /usr/share/wayland-session/* desktop files and then runs itself with X11.
I don't know why though, but ricotz may have a bit different opinion for this upstream change. In a couple of weeks ago, he still produced gnome-session-wayland package on his famous PPA...
Regards,
Tista
> **tista said:**
> Oh forgot to mention...
Gnome-session 3.19.x package provides both **GNOME** and **GNOME on Xorg** session entries on Gdm. So if you guys want to load classical gnome-shell/X11 session, please select "GNOME on Xorg". As I said above, "GNOME" session is today for use of both xwayland and x11.
Regards,
TistaYes I do have Your PPA active, not on this machine (at work). I think You've answered to the queston of mine. I'll see tonight. I should see if Ricotz's PPAs are still active on that install. That could be the source of these hickups...
Have a good and prosperous 2016. Thank You for all good work (You, Ricotz and the rest...)

---

