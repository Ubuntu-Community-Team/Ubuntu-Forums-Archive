---
title: "Seamless mode"
date: 2008-06-24
forum: Virtualisation
---

### Post by Robbyx on 2008-06-24
Does seamless mode work for guest win2k with dual nvidia monitors. I have just installed 1.6.2 it does not appear to work out of the box.

My Xorg.conf contains the following:

> Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

I am not sure if this means xinerama is off, but looking at other postings it might make a difference.

The manual advises that it might work:

> 4.6 Seamless windows
With the “seamless windows” feature of VirtualBox, you can have the windows that are
displayed within a virtual machine appear side by side next to the windows of your
host. This feature is supported for the following guest operating systems (provided
that the Guest Additions are installed):
    • Windows guests (support added with VirtualBox 1.5);
    • Linux or Solaris/OpenSolaris guests with an X.org server version 1.3 or higher1
      (support added with VirtualBox 1.6).
  After seamless windows are enabled (see below), VirtualBox suppresses the display
of the Desktop background of your guest, allowing you to run the windows of your
guest operating system seamlessly next to the windows of your host:


What should I do to have it working?

Robin

---

### Post by HermanAB on 2008-06-24
Dunno how to fix your problem, but you could also use seamless RDP with rdesktop [http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

That works with any kind of Windoze remote control situation, whether it is a real machine, Virtualbox or VMware.

Cheers,

H.

---

### Post by Robbyx on 2008-06-24
Herman

Thank you for that advice. Looking at the site it seems that it is designed for remote operation. 

I am using VirtualBox on my standalone desktop.

I wonder if anyone has actually got VB to work in seamless mode with Ubuntu as the host and win2k as the guest on the same machine.

Robin

---

### Post by saitoh on 2008-06-24
I have run Ubuntu as the host with XP and Vista as guests. I can run either in seamless mode. Maybe try launching VirtualBox from terminal and then activating seamless mode to view any errors. I will also say that Seamless mode has lots of issues with Compiz, it works perfectly with Metacity.

---

