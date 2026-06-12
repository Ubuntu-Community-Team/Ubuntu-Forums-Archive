---
title: "Wayland is not going to be default in 18.04"
date: 2018-01-26
forum: Ubuntu Development Version
---

### Post by Chanath on 2018-01-26
Wayland is not going to be default in 18.04
[https://community.ubuntu.com/t/xorg-will-be-the-default-in-18-04-lts/3623](https://community.ubuntu.com/t/xorg-will-be-the-default-in-18-04-lts/3623)

---

### Post by TheFu on 2018-01-26
Golf clap.  That give them 2 more years to get all those little details working.  Remote windows, like X11 has, is mandatory for my daily workflow.  I hope they can make it work acceptably between continents without extra addons like vnc or NX with secure tunnels.  

But, I won't hold my breath.

---

### Post by xeizoo on 2018-01-28
And Wayland and Nvidia doesn't play together particularly well, a blank screen is unproductive so thanks for this news ...

---

### Post by curts on 2018-02-01
> **xeizoo said:**
> And Wayland and Nvidia doesn't play together particularly well, a blank screen is unproductive so thanks for this news ...

Oh, so is that why I've not been able to properly install the NVIDIA driver since installing 18.04? Earlier this week I finally managed to get it to install and successfully reboot with it by manually blacklisting the nouveau driver and then manually running 'update-initramfs -u' post-install, but the next daily upgrade cycle broke it. So, I had it working for all of ten minutes.  :(

What is the transition plan/process to revert to Xorg now that this decision has been made? Will a future update automagically make the change for us?

Curt

---

### Post by kurt18947 on 2018-02-02
I don't have 18.04 installed but do have 17.10. I can select either a Wayland or Xorg session prior to log on by clicking the little gear thingy. I'm unaware of any Wayland related issues except the inability to use Synaptic but then I use defaults and have Intel & AMD graphics.

---

### Post by ya-paulle on 2018-02-02
> **kurt18947 said:**
> I don't have 18.04 installed but do have 17.10. I can select either a Wayland or Xorg session prior to log on by clicking the little gear thingy. I'm unaware of any Wayland related issues except the inability to use Synaptic but then I use defaults and have Intel & AMD graphics.

[FONT=arial][SIZE=3]If you use this command:

[/SIZE][/FONT][COLOR=#000000][FONT=-webkit-standard][FONT=arial][SIZE=3]xhost +SI:localuser:root

you can use synaptic under Wayland. Works for me (artful)
[/SIZE][/FONT]

[/FONT][/COLOR]

---

### Post by Frogs Hair on 2018-02-02
This can be added to startup applications as well. 
```
[COLOR=#000000][FONT=arial]xhost +SI:localuser:root[/FONT][/COLOR]
```

---

### Post by Chanath on 2018-02-03
> **Frogs Hair said:**
> This can be added to startup applications as well. 
```
[COLOR=#000000][FONT=arial]xhost +SI:localuser:root[/FONT][/COLOR]
```
You are not exactly encouraged to be the root in Ubuntu. 

Why Wayland is not going to be default is given here, [https://community.ubuntu.com/t/xorg-will-be-the-default-in-18-04-lts/3623](https://community.ubuntu.com/t/xorg-will-be-the-default-in-18-04-lts/3623)

---

### Post by Frogs Hair on 2018-02-03
> You are not exactly encouraged to be the root in Ubuntu. 

The command allows for the use of synaptic and other graphical applications with elevated permissions it does not eliminate the need for using sudo when appropriate or password authentication.

---

### Post by curts on 2018-02-03
I saw Xorg installed in the next update after my previous post. Thanks to this thread I found and selected 'Ubuntu with Xorg'.

I would argue from a UX perspective that if Xorg is to be the default, then the options when clicking on the little gear icon should be 'Ubuntu' & 'Ubuntu with Wayland'.

---

### Post by curts on 2018-02-03
With Xorg selected, I once again tried to install the NVIDIA driver. My first attempt has failed on the subsequent reboot following the seemingly successful install of the driver from the Additional Drivers control panel. The NVIDIA driver did not load properly:

```
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (--) PCI:*(0:1:0:0) 
10de:1244:1462:809d rev 161, Mem @ 0xf8000000/33554432, 0xc8000000/134217728, 0x
d4000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (II) LoadModule: "gl
x"
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (II) Loading /usr/li
b/xorg/modules/extensions/libglx.so
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (II) Module glx: ven
dor="X.Org Foundation"
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: #011compiled for 1.1
9.6, module version = 1.0.0
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: #011ABI class: X.Org
 Server Extension, version 10.0
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (==) Matched nvidia 
as autoconfigured driver 0
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (==) Matched nouveau
 as autoconfigured driver 1
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (==) Matched nvidia 
as autoconfigured driver 2
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (==) Matched nouveau
 as autoconfigured driver 3
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (==) Matched modeset
ting as autoconfigured driver 4
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (==) Matched fbdev a
s autoconfigured driver 5
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (==) Matched vesa as
 autoconfigured driver 6
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (==) Assigned the dr
iver to the xf86ConfigLayout
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (II) LoadModule: "nv
idia"
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (WW) Warning, couldn
't open module nvidia
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (II) UnloadModule: "
nvidia"
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (II) Unloading nvidi
a
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (EE) Failed to load 
module "nvidia" (module does not exist, 0)
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (II) LoadModule: "no
uveau"
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (II) Loading /usr/li
b/xorg/modules/drivers/nouveau_drv.so
Feb  3 12:24:08 panther2 /usr/lib/gdm3/gdm-x-session[1234]: (II) Module nouveau:
 vendor="X.Org Foundation"
```

---

### Post by wildmanne39 on 2018-02-03
Hello curts, please start your own thread about the nvidia issue as it is off topic in this thread, please start the thread in the appropriate sub-forum.

Thanks

---

### Post by Chanath on 2018-02-03
> **Frogs Hair said:**
> The command allows for the use of synaptic and other graphical applications with elevated permissions it does not eliminate the need for using sudo when appropriate or password authentication.

One of the reasons, why it is good that Wayland is not default in 18.04
In one way, Ubuntu devs would have 3 years at least to experiment on Wayland, whether it'd be good enough for the next LTS. 
Or drop it.  
Wayland had been on development for 9 years, and that is quite a long time considering hardware development in *that* 9 years.

---

