---
title: "Bug #1706146 : cannot run GUI application programs with elevated permissions"
date: 2017-07-24
forum: Ubuntu Development Version
---

### Post by sudodus on 2017-07-24
This bug appears, when I try to run GUI application programs with elevated permissions using **sudo -H** and **gksudo** in an installed Ubuntu Artful system on Wayland.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1706146](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1706146)

I discovered it while testing mkusb: version 12 alias mkusb-dus works because the GUI is running as the regular user. Only the executing scripts are running with elevated permissions; version 11 with the classic interface fails.

During the troubleshooting I discovered that no GUI application works. I tested **xterm**, **nautilus** and even **gparted**, which is made to run in graphics mode with elevated permissions, and **none of them works**.

```
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]sudo -H xterm[/COLOR]
[sudo] password for tester:
No protocol specified
Warning: This program is an suid-root program or is being run by the root user.
The full text of the error or warning message cannot be safely formatted
in this environment. You may get a more descriptive message by running the
program as a non-root user or by removing the suid bit on the executable.
xterm: Xt error: Can't open display: %s
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]sudo -H nautilus[/COLOR]
No protocol specified
Unable to init server: Could not connect: Connection refused

(nautilus:7987): Gtk-WARNING **: cannot open display: :0
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]sudo -H gparted[/COLOR]
Created symlink /run/systemd/system/-.mount &#8594; /dev/null.
Created symlink /run/systemd/system/media-tester-966d0a59\x2d9e02\x2d45d8\x2d8d27\x2d6916fdf9a4ee.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-1000.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-120.mount &#8594; /dev/null.
Created symlink /run/systemd/system/tmp.mount &#8594; /dev/null.
No protocol specified

(gpartedbin:8044): Gtk-WARNING **: cannot open display: :0
Removed /run/systemd/system/-.mount.
Removed /run/systemd/system/media-tester-966d0a59\x2d9e02\x2d45d8\x2d8d27\x2d6916fdf9a4ee.mount.
Removed /run/systemd/system/run-user-1000.mount.
Removed /run/systemd/system/run-user-120.mount.
Removed /run/systemd/system/tmp.mount.
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]gksudo xterm[/COLOR]
Error copying '/home/tester/.Xauthority' to '/tmp/libgksu-GQiFHn': No such file or directorytester@tester-SATELLITE-PRO-C850-19W:~$
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]gksudo nautilus[/COLOR]
Error copying '/home/tester/.Xauthority' to '/tmp/libgksu-gFaMxY': No such file or directorytester@tester-SATELLITE-PRO-C850-19W:~$
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]gksudo gparted[/COLOR]
Error copying '/home/tester/.Xauthority' to '/tmp/libgksu-rkGkLW': No such file or directorytester@tester-SATELLITE-PRO-C850-19W:~$
```


See also this link, [https://ubuntuforums.org/showthread.php?t=1958073&page=36&p=13667109#post13667109](https://ubuntuforums.org/showthread.php?t=1958073&page=36&p=13667109#post13667109)

Please mark 'affects me too', if this bug affects you too.

---

### Post by #&amp;thj^% on 2017-07-24
Yep it has showed up here a few times now.
As a work around sudodus maybe see if this will work in that case useage:
```
xhost +si:localuser:root
```
It only last's for that session though, so if you reboot or logout you will need that code again.

---

### Post by sudodus on 2017-07-24
Thanks 1fallen,

Your fix is working with **sudo -H** but not with **gksudo**. Please add this tip into the bug report as a comment :-)

```
sudo -H gparted
```

---

### Post by ventrical on 2017-07-24
+1ned it.

:)

---

### Post by #&amp;thj^% on 2017-07-24
> **sudodus said:**
> Thanks 1fallen,

Your fix is working with **sudo -H** but not with **gksudo**. Please add this tip into the bug report as a comment :-)

```
sudo -H gparted
```

Will do!
Have you tried "pkexec" with gparted?
sudodus I'm stlll having problems with a login @LP
> Oops!

Sorry, something just went wrong in Launchpad.

We&#8217;ve recorded what happened, and we&#8217;ll fix it as soon as possible. Apologies for the inconvenience.

(Error ID: OOPS-8efc63561819dbc0665c6b99c0ff9202) 
Been that way for months now...But feel free to add it yourself if you wish. (Sorry out of my control)

---

### Post by ventrical on 2017-07-24
> **1fallen said:**
> Yep it has showed up here a few times now.
As a work around sudodus maybe see if this will work in that case useage:
```
xhost +si:localuser:root
```
It only last's for that session though, so if you reboot or logout you will need that code again.

Seen your link in other .. definetly wayland specific. A lof of .deb packages will not work in wayland.

Regards..

---

### Post by sudodus on 2017-07-24
> **1fallen said:**
> Will do!
Have you tried "pkexec" with gparted?
sudodus I'm stlll having problems with a login @LP

Been that way for months now...But feel free to add it yourself if you wish. (Sorry out of my control)

1. **pkexec gparted** does not work without xhost, but it works after the xhost command is run.

2. OK, I'll add it.

---

### Post by sudodus on 2017-07-24
> **ventrical said:**
> Seen your link in other .. definetly wayland specific. A lof of .deb packages will not work in wayland.

Regards..

Thanks for confirming :-)

---

### Post by #&amp;thj^% on 2017-07-24
> **sudodus said:**
> 1. **pkexec gparted** does not work without xhost, but it works after the xhost command is run.

2. OK, I'll add it.
Thanks! ;)
This works for me:
```
sudo gpartedbin
```
Name sake is very important in a wayland session:
For example: "sudo gdebi" dose not work, but "sudo gtk-gdebi" dose, so you might have to find/experiment the naming involved in a wayland session.
So far I found no issues running anything with elevated privileges yet. :p

---

### Post by mc4man on 2017-07-24
The bug is against xorg-xserver, why?
At the end of the day it would likely be requested to bug apps that can't work in wayland themselves as this is expected behavior.

---

### Post by sudodus on 2017-07-25
> **mc4man said:**
> The bug is against xorg-xserver, why?
At the end of the day it would likely be requested to bug apps that can't work in wayland themselves as this is expected behavior.

I did not manage to convince the tool to report bugs to accept reporting against any program package with a name containing the string 'wayland' although they are obviously recognized by for example **apt-cache** and even running and reported by **ps**. Maybe a bug in **ubuntu-bug** or some missing package names in a list of possible packages to report against.

---

### Post by ventrical on 2017-07-25
```


ubuntu-bug xwayland


```

---

### Post by sudodus on 2017-07-25
@ventrical,

My bug report is declared invalid. Instead I will continue the bug reporting via the following link for **gparted**, that seems to be accepted and worked upon,

[https://bugs.launchpad.net/ubuntu-gnome/+bug/1652282](https://bugs.launchpad.net/ubuntu-gnome/+bug/1652282)

It seems that the problem is by intention, and each application program must be fixed individually (in order to increase the security).

Luckily for me **mkusb version 12 works**, because everything with elevated permissions can be done without a GUI in separate shellscipts. Only the GUI dialogue is run with the normal user ID.

---

### Post by ventrical on 2017-07-26
> **sudodus said:**
> @ventrical,

My bug report is declared invalid. Instead I will continue the bug reporting via the following link for **gparted**, that seems to be accepted and worked upon,

[https://bugs.launchpad.net/ubuntu-gnome/+bug/1652282](https://bugs.launchpad.net/ubuntu-gnome/+bug/1652282)

It seems that the problem is by intention, and each application program must be fixed individually (in order to increase the security).

Luckily for me **mkusb version 12 works**, because everything with elevated permissions can be done without a GUI in separate shellscipts. Only the GUI dialogue is run with the normal user ID.

Could you be more clear (or someone else) about this. Is this saying that we have to have each .deb app tested before it will run on GNOME shell or GNOME with wayland?

For example; If you install the program vokoscreen (which is a screen capturing app) on GNOME shell or GNOME with wayland it will not work (last I tried) but it will work just great on xubuntu or unity-session running on a GNOME install,

```

sudo apt-get install vokoscreen

```

---

### Post by sudodus on 2017-07-26
@ventrical,

I am afraid, that this is the case for GUI applications in order to run with sudo (root permissions) on Wayland.

We know that it is a problem, and we don't know how willing the Wayland people are to make things easier. After all, a lot of application programs have this problem, and a lot of people will probably complain, when the first main linux distros release versions where Wayland is the default. So maybe they will respond to such complaints by making things easier.

But this is only what *I think*. I would also be happy if someone else can chip in and make things more clear :-P

---

### Post by #&amp;thj^% on 2017-07-26
I also "heard" that those outside of the default debian/ubuntu apps will have to be dealt with by the devs of those particular applications.

---

### Post by rrnbtter on 2017-07-26
Greetings,
Ubuntu is switching to Wayland and GDM. It doesn't matter if you login with Gnome, Gnome-Wayland, Ubuntu, Ubuntu-Wayland, if you run "top" you will find Wayland running.  And Yes, Xserver is also running, but Wayland is taking the calls and farming them out to Xserver. Hence, since they (the x11 apps) have to meet Wayland security protocols first, they won't run right with X since the apps are not (in most cases) Wayland compatible. In my understanding it is XWayland that is sorting it out. This is the way it is. Most of us have some work-a-rounds, but none of them are quite good enough. Canonical wants Wayland and will get most of it fixed before release date (I suppose). In the mean time we are in the same situation as when we were testing Unity8 and Libertine, etc.  There are plenty of Wiki's on Wayland, XWayland, and Wayland-client as it pertains to X11 apps and Xserver. They may be worth a read.  These things are not incompatible but they need to be fixed first. In that vein I would prefer a complete switch to Wayland and Wayland-Client and Wayland apps than more patchwork. We have the patchwork because users want control of the system.  But we have "flavors" that can provide that so it makes more sense to me to have a refined Ubuntu and not a patched system that just gets thing working "one way or another".  Quite frankly, I "love" Gnome desktop which I didn't think I would, and I "love" the speed and robustness of Wayland which I didn't think I would. However I too would like to see what it is like when it all works. Thanks to some of you "old timers" for the work-a-rounds. I'm getting by just fine right now. 
Please don't beat up on me too hard. Its just my opinion.

---

### Post by sudodus on 2017-07-26
@rrnbtter,

Thanks for taking part in our discussion :-)

> There are plenty of Wiki's on Wayland, XWayland, and Wayland-client as it pertains to X11 apps and Xserver. They may be worth a read.

Please make it easy and give us a couple of links to wikis on Wayland that you think are worth a read :-)

---

### Post by rrnbtter on 2017-07-26
Greetings,
I have to go to work right now but this is a good place to start to see the variables and resulting problems. It is a well worn path so I think Canonical knows where it is going. [https://wiki.archlinux.org/index.php/wayland](https://wiki.archlinux.org/index.php/wayland). I didn't keep track of my readings but I will find some of the rest of it tomorrow. 
Thanks for your interest.

---

### Post by ventrical on 2017-07-26
> **sudodus said:**
> @rrnbtter,

Thanks for taking part in our discussion :-)



Please make it easy and give us a couple of links to wikis on Wayland that you think are worth a read :-)

Please see .. "Will applications have to be re-written...

[https://wiki.ubuntu.com/Wayland](https://wiki.ubuntu.com/Wayland)

it's a little outdated but on topic.

Regards..

---

### Post by sudodus on 2017-07-26
Thanks for the links, rrnbtter & ventrical :-)

---

### Post by Cavsfan on 2017-07-27
> **1fallen said:**
> Yep it has showed up here a few times now.
As a work around sudodus maybe see if this will work in that case useage:
```
xhost +si:localuser:root
```
It only last's for that session though, so if you reboot or logout you will need that code again.

Same thing here. I used it and Synaptic opened and then logged out and back in and it would not open.
 I created an alias with that workaround:
```
#temorary session fix for root
alias root-fix='xhost +si:localuser:root'

```
> **sudodus said:**
> Thanks 1fallen,

Your fix is working with **sudo -H** but not with **gksudo**. Please add this tip into the bug report as a comment :-)

```
sudo -H gparted
```

I also added myself to the bug. :)

So, far I have only found a gnome session with wayland that I can login to.

---

### Post by Cavsfan on 2017-07-28
So, I found the gear :redface: and have Ubuntu and Ubuntu with Wayland as the only 2 options.

Either one works and there is no difference that I can tell. I can confirm Wayland is running on both.

---

### Post by sudodus on 2017-07-28
> **Cavsfan said:**
> So, I found the gear :redface: and have Ubuntu and Ubuntu with Wayland as the only 2 options.

Either one works and there is no difference that I can tell. I can confirm Wayland is running on both.

Yes, that's what I have observed too :-P

---

### Post by mc4man on 2017-07-28
> **Cavsfan said:**
> 

Either one works and there is no difference that I can tell. I can confirm Wayland is running on both.
xwayland on tty2 should only be running in a 'ubuntu on wayland' session. The default session should just be X11.

Ex.
on a ubuntu on wayland session
> $ env | grep -i wayland  
DESKTOP_SESSION=ubuntu-wayland
WAYLAND_DISPLAY=wayland-0
XDG_SESSION_TYPE=wayland
XDG_SESSION_DESKTOP=ubuntu-wayland
GDMSESSION=ubuntu-wayland

ps -A |grep wayland
 1047 tty1     00:00:00 gdm-wayland-ses
 1097 tty1     00:00:00 Xwayland
 4165 tty2     00:00:00 gdm-wayland-ses
 4221 tty2     00:00:03 Xwayland


On the 'actual' default session

> $ env | grep -i wayland
(nothing returned)

ps -A |grep wayland
1047 tty1     00:00:00 gdm-wayland-ses
1097 tty1     00:00:00 Xwayland

---

### Post by Cavsfan on 2017-07-29
> **Cavsfan said:**
> Either one works and there is no difference that I can tell. I can confirm Wayland is running on both.

> **mc4man said:**
> xwayland on tty2 should only be running in a 'ubuntu on wayland' session. The default session should just be X11.

Ex.
on a ubuntu on wayland session
> [COLOR=#000000]*$ env | grep -i wayland *[/COLOR]
[COLOR=#000000]*DESKTOP_SESSION=ubuntu-wayland*[/COLOR]
[COLOR=#000000]*WAYLAND_DISPLAY=wayland-0*[/COLOR]
[COLOR=#000000]*XDG_SESSION_TYPE=wayland*[/COLOR]
[COLOR=#000000]*XDG_SESSION_DESKTOP=ubuntu-wayland*[/COLOR]
[COLOR=#000000]*GDMSESSION=ubuntu-wayland*[/COLOR]

[COLOR=#000000]*ps -A |grep wayland*[/COLOR]
[COLOR=#000000]*1047 tty1 00:00:00 gdm-wayland-ses*[/COLOR]
[COLOR=#000000]*1097 tty1 00:00:00 Xwayland*[/COLOR]
[COLOR=#000000]*4165 tty2 00:00:00 gdm-wayland-ses*[/COLOR]
[COLOR=#000000]*4221 tty2 00:00:03 Xwayland*[/COLOR]

On the 'actual' default session

[QUOTE][COLOR=#000000]*$ env | grep -i wayland*[/COLOR]
[COLOR=#000000]*(nothing returned)*[/COLOR]

[COLOR=#000000]*ps -A |grep wayland*[/COLOR]
[COLOR=#000000]*1047 tty1 00:00:00 gdm-wayland-ses*[/COLOR]
[COLOR=#000000]*1097 tty1 00:00:00 Xwayland*[/COLOR]
[/QUOTE]

That is not what I get: I get the same on both.
I rebooted from another system, logged in thinking I would be in a "default session" since I did not change it.
Then I seen your post. I got what you have for a wayland session. So then logged out and back in on a wayland session, same thing, which was expected.

Then I rebooted and checked to make sure it was a default session and still got this:
> env | grep -i wayland
DESKTOP_SESSION=ubuntu-wayland
WAYLAND_DISPLAY=wayland-0
XDG_SESSION_TYPE=wayland
XDG_SESSION_DESKTOP=ubuntu-wayland
GDMSESSION=ubuntu-wayland

ps -A |grep wayland
  918 tty1     00:00:00 gdm-wayland-ses
 1037 tty1     00:00:00 Xwayland
 1703 tty2     00:00:00 gdm-wayland-ses
 1760 tty2     00:00:00 Xwayland


Rebooted again and logged in to a wayland session and got this:

> env | grep -i wayland
DESKTOP_SESSION=ubuntu-wayland
WAYLAND_DISPLAY=wayland-0
XDG_SESSION_TYPE=wayland
XDG_SESSION_DESKTOP=ubuntu-wayland
GDMSESSION=ubuntu-wayland

ps -A |grep wayland
 1027 tty1     00:00:00 gdm-wayland-ses
 1048 tty1     00:00:00 Xwayland
 1279 tty2     00:00:00 gdm-wayland-ses
 1336 tty2     00:00:00 Xwayland


So, I wonder what is up with that?

@[COLOR=#000000]sudodus, what do you get here?[/COLOR]

---

### Post by #&amp;thj^% on 2017-07-29
He's referring to The default session should just be X11.
So mine with xwayland shows
```
DESKTOP_SESSION=gnome-wayland
WAYLAND_DISPLAY=wayland-0
XDG_SESSION_TYPE=wayland
XDG_SESSION_DESKTOP=gnome-wayland
GDMSESSION=gnome-wayland

```
On just X11 it shows:
```
me@me-750-417c:~$ env | grep -i wayland 
me@me-750-417c:~$ 

```
Nothing returned.:)

---

### Post by sudodus on 2017-07-29
> **Cavsfan said:**
> @[COLOR=#000000]sudodus, what do you get here?[/COLOR]

The same as you, Cavsfan.

---

### Post by sudodus on 2017-07-29
> **1fallen said:**
> He's referring to The default session should just be X11.
So mine with xwayland shows
```
DESKTOP_SESSION=gnome-wayland
WAYLAND_DISPLAY=wayland-0
XDG_SESSION_TYPE=wayland
XDG_SESSION_DESKTOP=gnome-wayland
GDMSESSION=gnome-wayland

```
On just X11 it shows:
```
me@me-750-417c:~$ env | grep -i wayland 
me@me-750-417c:~$ 

```
Nothing returned.:)

How to activate the default session (just X11)?

---

### Post by #&amp;thj^% on 2017-07-29
> **sudodus said:**
> How to activate the default session (just X11)?
It will depend on Drivers though.
```
nano /etc/gdm3/custom.conf

```
Uncomment this:
```
[daemon]
# Uncoment the line below to force the login screen to use Xorg
[COLOR="#FF0000"]#WaylandEnable=false[/COLOR]

```
I have Dual GPU's here so my mileage may vary from yours.:)
So I can use the prime-select nvidia/intel
But I know you  also have the skills to fix if things go wrong with this setup.:)
Cavsfan has only Nvidia GPU so word of **caution** here>.(Just a heads up)
```
Graphics:  Card-1: Intel HD Graphics 530
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: x11 (X.Org 1.19.3) drivers: modesetting,nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz, 1360x768@60.02hz, 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 560 Ti/PCIe/SSE2 version: 4.5.0 NVIDIA 384.59

```

---

### Post by sudodus on 2017-07-29
Thanks @1fallen :-) I will look into this later ...

---

### Post by Cavsfan on 2017-07-29
> **1fallen said:**
> It will depend on Drivers though.
```
nano /etc/gdm3/custom.conf

```
Uncomment this:
```
[daemon]
# Uncoment the line below to force the login screen to use Xorg
[COLOR=#FF0000]#WaylandEnable=false[/COLOR]

```
I have Dual GPU's here so my mileage may vary from yours.:)
So I can use the prime-select nvidia/intel
But I know you  also have the skills to fix if things go wrong with this setup.:)
Cavsfan has only Nvidia GPU so word of **caution** here>.(Just a heads up)
```
Graphics:  Card-1: Intel HD Graphics 530
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: x11 (X.Org 1.19.3) drivers: modesetting,nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz, 1360x768@60.02hz, 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 560 Ti/PCIe/SSE2 version: 4.5.0 NVIDIA 384.59

```

Maybe I didn't read something or another but, I didn't realize that was how to get an X11 session.
I edited that file and rebooted. I finally got an X11 session or so Inxi showed. But, it kept reporting error after error about X11.
So, I commented it out again and rebooted. Now it's basically back where it was. Wayland works better here I reckon you could say. 

But Nautilus has not been able to open up since deja-dup was upgraded to 35.1 which seems like yesterday or so.
Finally it reported a Nautilus bug and I found it here:  [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1707346](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1707346)
(in the bug is where I found out deja-dup caused it not to open)

When you cannot even open a folder to see a file, there's not much you can do... I'd imagine that will be fixed soon.

---

### Post by mc4man on 2017-07-29
> **sudodus said:**
> How to activate the default session (just X11)?
You need to cycle the greeter as it Always shows an ubuntu session even if it's not.
See here
[https://ubuntuforums.org/showthread.php?t=2366538](https://ubuntuforums.org/showthread.php?t=2366538)
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157)

---

