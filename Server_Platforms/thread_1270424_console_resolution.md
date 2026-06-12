---
title: "console resolution"
date: 2009-09-19
forum: Server Platforms
---

### Post by laytek on 2009-09-19
Hello all,

I am doing a new install of sever 8.04 on a Dell Dimension 2400. After the fresh install and sudo apt-get update and sudo apt-get dist-upgrade, I am attempting to change the console resolution by following this link.

[https://help.ubuntu.com/community/ConsoleFramebuffer](https://help.ubuntu.com/community/ConsoleFramebuffer)

When I add vga=791 (or all other resolutions) all I get is a message that says:

Undefined video mode number: xxx    (xxx depends on which video mode I have tried.)

Also:

alan@altair:~$ lsmod | grep fb
vesafb                  8964  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon


Is there a problem with my video driver? How can I determine which driver is being used? I know that this is an old problem that should be easy to solve. I have searched ubuntuforums.org and google for several days. Thanks for your time in helping me solve this.

LayTek

---

### Post by laytek on 2009-09-19
The Dell 2400 uses the Intel 82845G Extreme Graphics on-board video controller. I just read that I should use:

video=intelfb:1024x768-16@60

instead of:

vga=791

on the boot line. How do I install the intelfb in the initrd?

LayTek

---

### Post by laytek on 2009-09-21
What if I compiled a custom kernel? I could add vesafb and intelfb into the kernel, right?

---

### Post by laytek on 2009-09-22
After much playing, I have better console resolution.
First:
```
sudo apt-get install v86d
```
Then:
```
sudo modprobe uvesafb mode_option=1024x768-16 maxvf=60
```

The consoles are now in a 1024x768 resolution.

But I can't it to work on the kernel boot line?:
```
video=uvesafb:1024x768-16,maxvf:60
```

Any suggestions are greatly appreciated.
LayTek

---

