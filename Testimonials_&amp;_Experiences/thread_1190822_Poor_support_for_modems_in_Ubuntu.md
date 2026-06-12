---
title: "Poor support for modems in Ubuntu"
date: 2009-06-18
forum: Testimonials &amp; Experiences
---

### Post by ArnoldGove on 2009-06-18
I have two different PCs, and two different modems. I installed Ubuntu on both PCs, but couldn't get online. The first modem was a very common dial-up, which Ubuntu couldn't cope with, but which PCLinuxOS installed in seconds. The other modem (Linux compatible) caused problems (DHCP setting or something), but which Windows XP installed in seconds.

I get the impression that the Ubuntu developers are more concerned with the newest devices than the broadest compatibility. Fair enough - that's up to them.

Obviously, I have since removed Ubuntu from my systems.

---

### Post by caravel on 2009-06-18
Are we talking PCI winmodems here or real modems:

[img]http://img268.imageshack.us/img268/4595/41li6q92sjlsl500aa280.jpg[/img]

?

---

### Post by ArnoldGove on 2009-06-18
Note that PCLinuxOS installed the dialup winmodem effortlessly. The other device was a modem-router - which I bought because of Ubuntu's lack of support for my first modem.

---

### Post by caravel on 2009-06-18
> **ArnoldGove said:**
> Note that PCLinuxOS installed the dialup winmodem effortlessly.
Which shows that it might have been supported by Linux?  So logically you would then hunt for a "driver" as one has to at times?  I've not used PCLinuxOS but if the device was detected and a driver installed, then it may be because it comes with the "linmodems" drivers.  Ubuntu may never have shipped with these drivers or may have removed these drivers at some point in order to keep the distro on one CDROM (while fitting on all the other stuff).

Also you should note that your modem may be working and detected in Ubuntu but you will not have a ppp client installed and so won't be able to connect up to your ISP.  This is something else that was removed in 9.04.  Installing something like kppp (offline obviously) might be enough to get it up and running.

> **ArnoldGove said:**
> The other device was a modem-router - which I bought because of Ubuntu's lack of support for my first modem.
An ADSL modem router?  Well if it's a router of any kind it would have an ethernet port which means problem solved.  A router is a much better and safer way to connect to the net than using a winmodem.

If you'd posted for some help you may have got further.

---

### Post by caravel on 2009-06-18
Hmmm... looking at your old posts I think you may be talking about a USB ADSL "modem"?  If this is the case then you're no better off.  If the USB modem you have is one of those "speedtouch 330" things then forget it.  Their Linux support has always been poor due to the device itself being mainly software based (as is also the case with internal PCI winmodems).  Any drivers for these are usually reverse engineered and make use of the Windows firmware.

You have a router and you need to get that up and running first.  The router is nothing to do with the OS and does not require a driver because it connects by ethernet.  It's the best and securest way to connect and is not platform specific.

---

### Post by arnoldjames on 2009-06-18
I have 2 usb hardware modems.  Both work in Fedora and Xandros Linux plug and play.  For some crazy reason, the hardware support for these is not available for Ubuntu withour recompiling.  This is not about winmodems.  It is about something left out in Ubuntu.  My experience is for 8.10. Searching around these forums indicates that they have registered this a bug and will put in this hardware support for subsequent ubuntu versions.   Good for them and glad it is being addressed.  I managed to get a third usb fax modem for $5 (not many of us need to fax or use dial-up anymore I guess) and it is supported.  For most of us, it is easier to find working hardware than tinkering with kernal modules!

---

### Post by ArnoldGove on 2009-06-18
Thanks arnoldjames! It's not just me then.

---

### Post by arnoldjames on 2009-06-18
No it;s not you.  And I like your name!  I find that it is hard to find help in these forums for specific problems like this one.  People give the same "must be a winmodem" and "have you tried scanmodem" responses, often with an evangelistic tone.  This is actually the only weakness I've found for this distro.  Most everything else simply seems to work okay.

Do make sure you run in a console:
lsusb
sudo wvdialconf /etc/wvdial/conf

lsusb - will show that it thinks it is connected
wvdial will show where it connected if the driver is loaded.  It actually took a day to find this one.  But I am slow sometimes with new problems.

My working modem showed up at /dev/tty/ACM0

---

### Post by ddrichardson on 2009-06-18
Having had to attempt to write the system help for modems in Jaunty I feel your pain - we, as a distro, should NOT have removed gnome-network-admin.

---

### Post by cariboo on 2009-06-18
Gnome-network-admin is still in the repositories, I'm using it on my Jaunty based media center pc, as network-manager-gnome says my D-Link USB wireless device is unmanaged.

I have a Cardinal serial hardware modem, just to see how newer distros handle modems I hooked it up to my server and had it working in less than 5 minutes.

---

### Post by HappyFeet on 2009-06-19
> **arnoldjames said:**
> For most of us, it is easier to find working hardware than tinkering with kernal modules!

No chit. That's what a smart computer user does, although I have loaded modules when needed.

---

### Post by caravel on 2009-06-19
The truth is that such threads as these get innacurate or incomplete responses because the problem is never described correctly.  I am still unclear as to which of the following we're talking about here:

1) USB dial up modems
2) PCI winmodems
3) USB DSL modems
4) DSL modem/router

Because you've not described your problem correctly, you haven't got an in depth answer.

You didn't answer any of my questions, you've simply responded with "well it worked in distro x !" "or it detected it in distro y !".  My response to that is: Then ask for support, providing as much info as possible, or use distro x/y.

The simple fact is that no distro will have the kernel modules for every single piece of hardware and if a distro lacks a particular kernel module/driver then you can always get it later.

---

### Post by ArnoldGove on 2009-06-19
> **caravel said:**
> The truth is that such threads as these get innacurate or incomplete responses because the problem is never described correctly.  I am still unclear as to which of the following we're talking about here:

1) USB dial up modems
2) PCI winmodems
3) USB DSL modems
4) DSL modem/router

Because you've not described your problem correctly, you haven't got an in depth answer.

You didn't answer any of my questions, you've simply responded with "well it worked in distro x !" "or it detected it in distro y !".  My response to that is: Then ask for support, providing as much info as possible, or use distro x/y.

The simple fact is that no distro will have the kernel modules for every single piece of hardware and if a distro lacks a particular kernel module/driver then you can always get it later.

The truth is that such threads as these get inaccurate or incomplete responses because the answer is never described correctly. I am still unclear as to whom you are replying.

This is the Testimonials & Experiences subforum. I know where to ask technical questions, and have done so. I made my point - in the right place - that in my experience there is poor support for modems in Ubuntu. Don't criticize me for that! (Especially since in an understandably pro-Ubuntu forum I have nevertheless been agreed with to some extent.)

---

### Post by caravel on 2009-06-19
> **ArnoldGove said:**
> The truth is that such threads as these get inaccurate or incomplete responses because the answer is never described correctly. I am still unclear as to whom you are replying.
No, I think you'll find that's strictly your perception of things.  You I was actually replying to you, because you started the thread.  It may also come as a shock to you that I was trying to help you out, as were those in the other thread.

> **ArnoldGove said:**
> This is the Testimonials & Experiences subforum. I know where to ask technical questions, and have done so. I made my point - in the right place - that in my experience there is poor support for modems in Ubuntu. Don't criticize me for that! (Especially since in an understandably pro-Ubuntu forum I have nevertheless been agreed with to some extent.)

You posted another thread for support.  This was your *one and only* post in that thread:

> **ArnoldGove said:**
> I've a fresh install of Ubuntu 9 (no other OS on the PC) and a Safecom SAMR-4112 ADSL Modem Router all wired up (but not the USB connection). The ADSL light is on, the LAN light is on, and of course the PWR light is on. What now? I've gone to the Network icon, and keyed in what I could, but I'm still offline.

You asked for help about an _ADSL router_, you received responses that you did not even have the grace to reply to and then you came here and complained about *modem* support.

All credit to those that responded, because you did not provide enough info to start with.

In case you're still interested in solving your problems, a router is *independent to the OS*, you don't need to install any software in Ubuntu or Windows, or any OS to get a router working.  This means that an OS does not need to "support" a router.

The problem is likely to be how you've configured the router, yet no one can help you as you've not provided enough info and haven't even made a statement to the effect that you've tried plugging another PC or Laptop into the router and that this PC/Laptop was working fine.  That would be starting point at least.  To get help you must first help yourself.

Have a good one.

---

### Post by ddrichardson on 2009-06-19
> **cariboo907 said:**
> Gnome-network-admin is still in the repositories, I'm using it on my Jaunty based media center pc, as network-manager-gnome says my D-Link USB wireless device is unmanaged.
In the repos, yes - on the installation image, no.  If you only have dial up then you're going to have to download it elsewhere and install it manually.

---

### Post by cariboo on 2009-06-19
@ddrichardson

Would it be worth creating a bug to get gnome-network-admin, just like ndiswrapper and build-essential? It is only a 328kb file, and all the dependencies are met with the installation of network-manager-gnome.

---

### Post by ddrichardson on 2009-06-20
> **cariboo907 said:**
> @ddrichardson

Would it be worth creating a bug to get gnome-network-admin, just like ndiswrapper and build-essential? It is only a 328kb file, and all the dependencies are met with the installation of network-manager-gnome.
I don't know to be honest but I'm inclined to say yes.  The bug was aimed at us in ubuntu-docs [here]("https://bugs.launchpad.net/ubuntu-docs/hardy/+bug/310331"), which got quite heated but after changing the help files to explain how to obtain, install and use said package we've had no replies.

I assume this is still an issue but as I had to borrow a modem to test it with I'm in a position to report it further (and I don't know anyone in those projects).

---

