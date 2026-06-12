---
title: "LXDE GUI not booting in Ubuntu 14.04 server"
date: 2014-06-22
forum: Virtualisation
---

### Post by benjamin24 on 2014-06-22
Hi all.


I tried searching but I couldn't find anybody with the same problem. I have installed Ubuntu 14.04 server as a guest on virtualbox (host is macbook pro running osx 10.6.8). I have installed a couple of programs on it but I now want a very basic and light GUI. I tried installing LXDE (sudo apt-get install lxde-core) and it seemed to download properly. however when I restart the virtual machine it just boots to terminal as usual and doesn't startup with the GUI. Any advice on what to try next?


Many thanks!

---

### Post by teeks99 on 2014-06-22
I've had the same problem, except running under KVM. I also installed the 'lxde' package instead of 'lxde-core'. I was planning to write up a bug report on it (haven't gotten around to it yet).

---

### Post by ajgreeny on 2014-06-22
Do those packages also pull in a display-manager such as lightdm, and all the packages of xorg, both of which would be needed for the auto-startup of the GUI.

Can you start lxde GUI with the command **startx**?

---

### Post by benjamin24 on 2014-06-22
> **ajgreeny said:**
> Do those packages also pull in a display-manager such as lightdm, and all the packages of xorg, both of which would be needed for the auto-startup of the GUI.

Can you start lxde GUI with the command **startx**?

Thanks for your help! I installed lightdm and xorg and it booted up to a GUI login screen. The interesting thing is that once I got there I could select between LXDE or openbox (which I never manually installed). I was able to log into both of them once and then when I restarted the virtual box it wouldn't let me log in again.

I can login with openbox as a guest but not with LXDE as a guest. When I try to login with my password I get the following message flash really quickly before returning me to the login screen.

[http://imgur.com/uTqHlvy](http://imgur.com/uTqHlvy)

[IMG]http://imgur.com/uTqHlvy[/IMG]

Any idea how to fix this?

Many thanks!

---

### Post by ajgreeny on 2014-06-23
Openbox is the window manager for LXDE so is installed by default with the DE and can be run without the DE itself if you so wish, that is why you have the option for that at login.

It sounds as if the display-manager is not starting automatically when you boot the VM, but can you still start a GUI with command **startx** from your command line?

Otherwise I don't think I can help you more.

---

