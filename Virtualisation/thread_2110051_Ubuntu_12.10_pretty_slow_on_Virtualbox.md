---
title: "Ubuntu 12.10 pretty slow on Virtualbox"
date: 2013-01-29
forum: Virtualisation
---

### Post by Blackbug on 2013-01-29
Hi All,

I have windows 8 machine, and have installed ubuntu 12.10 on virtualbox.
But, its too slow, almost not workable at all.

I have decent specs, corei5 1.8ghz, 4GB RAM, 2GB ATI 7670 GPU and SSD.

Any clue whats wrong?

Thanks.

KK

---

### Post by ibjsb4 on 2013-01-29
Seems to be a lot of that going around.  Have not tried it myself.

[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+12.10+slow+in+virtualbox&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+12.10+slow+in+virtualbox&ie=utf-8&oe=utf-8)

I find 12o4 runs good in vBox, but I am not running the full blown desktop either.  Think its worth a try though.

---

### Post by Warren Hill on 2013-01-29
This is a known problem and it has a lot to do with the absence of Unity2D which was in 12.04 but not 12.10

see here
[http://www.geekthisway.com/ubuntu-12-10-slow-as-virtualbox-guest-os/](http://www.geekthisway.com/ubuntu-12-10-slow-as-virtualbox-guest-os/)

and here
[http://ubuntuforums.org/showthread.php?t=2073625](http://ubuntuforums.org/showthread.php?t=2073625)

Xubuntu 12.10 and Lubuntu 12.10  fun fine under Virtualbox with a Windows 7 host or XP host.  Ubuntu 12.10 is painfully slow however

---

### Post by Blackbug on 2013-01-29
Thanks for the information.

I was thinking may be to try 32-bit version of ubuntu12.10, but looking the post and links you posted, it seems like a generic issue.

---

### Post by stevevasili on 2013-01-29
Does this bug apply to VMware also? I've currently got 5 physical boxes running 10.04 that I'm virtualising and putting in to a hosted VMware envioronment. To keep things simple I've built new VM's on 12.10 and am importing the data rather than any physical -> virtual process. They are performing really slow. At first I thought it could be down to the hosting environment which is Stratogen ([VMware hosting]("http://www.stratogen.com/products/vmware-hosting.html")) but now I'm thinking it's some kind of compatibility issue. I haven't got VMware tools installed so could that be related also?

Does anyone know a good stable release that performs well on VMware?

Steve.

---

### Post by haqking on 2013-01-29
I have got 12.10 running in virtualbox and only got 512Mb ram assigned, 128GB Video memory and I have enabled 3D acceleration.

It works fine

---

### Post by markbl on 2013-01-29
> **haqking said:**
> I have got 12.10 running in virtualbox and only got 512Mb ram assigned, 128GB Video memory and I have enabled 3D acceleration. 

It works fine

What version of VB and what host OS and version?

I have not heard of anybody who can run a Ubuntu 12.10 guest reliably in VB with 3D acceleration enabled. For me, and most others it seems, it aborts within minutes after boot. I run current version 4.2.6 VB on both current version 10.8.2 Mac OSX host, and Ubuntu 12.04 and 12.10 hosts, with the same problems. The problems occur in both Unity and Gnome shell. The problem is compatibility between VB and the new Xorg 1.13 used in Ubuntu 12.10.

I can turn off 3D acceleration and it runs without crashing but, as the OP says here, it is too darn slow.

OP, the reason 12.10 is much slower is because without 3D acceleration Ubuntu 12.10 Unity falls back to LLVMpipe software rendering. This is different to 12.04 which fell back to Unity 2D. Unity 2D project has been dropped.

---

### Post by haqking on 2013-01-30
> **markbl said:**
> What version of VB and what host OS and version?

I have not heard of anybody who can run a Ubuntu 12.10 guest reliably in VB with 3D acceleration enabled. For me, and most others it seems, it aborts within minutes after boot. I run current version 4.2.6 VB on both current version 10.8.2 Mac OSX host, and Ubuntu 12.04 and 12.10 hosts, with the same problems. The problems occur in both Unity and Gnome shell. The problem is compatibility between VB and the new Xorg 1.13 used in Ubuntu 12.10.

I can turn off 3D acceleration and it runs without crashing but, as the OP says here, it is too darn slow.

OP, the reason 12.10 is much slower is because without 3D acceleration Ubuntu 12.10 Unity falls back to LLVMpipe software rendering. This is different to 12.04 which fell back to Unity 2D. Unity 2D project has been dropped.


Vbox 4.2.6
Host- Slackware Current
16Gb Ram
Intel i7 2700K
EVGA Precision GTX580 3Gb Video Card

The 12.10 guest has 512 Mb Ram, 3d Acceleration enabled, 1 processor assigned.

I dont use it that often, but when I do I dont notice any particular lagginess and it has never crashed.

Everyones mileage varies I gues

---

### Post by Paddy Landau on 2013-01-31
There is a mismatch with 3D in 12.10 because of what is installed. Try this:


[LIST=1]
[*]In your VM settings, ensure that you have enabled 3D (Settings > Display > Video > Extended Features > Enable 3D Acceleration).
[*]Start your 12.10 guest. Then:
[*]Install [FONT=Lucida Console]linux-headers-quantal[/FONT] and [FONT=Lucida Console]build-essential[/FONT] (you can do this from a terminal, from Ubuntu Software Centre, or however you prefer).
[*]Install Guest Additions if you have not already done so.
[*]Edit [FONT=Lucida Console]/etc/modules[/FONT] (you can do this by pressing [FONT=Lucida Console]Alt+F2[/FONT] and entering the command [FONT=Lucida Console]gksudo[/FONT] [FONT=Lucida Console]gedit[/FONT] [FONT=Lucida Console]/etc/modules[/FONT]). If not already present, add the line [FONT=Lucida Console]vboxvideo[/FONT] to the end of the file.
[*]Reboot your guest (not your host).
[/LIST]

Let us know if this works for you.

---

### Post by markbl on 2013-01-31
Paddy, the vboxvideo module does not fix the problem as even when the module is loaded correctly in the guest we get almost immediate guest crashes. That vboxvideo loading and other Xorg 1.13 related issues existed with VB 4.2.4 and were supposed to be fixed in current version 4.2.6. If anything, I think the guest crashes are more frequent in 4.2.6. As an example, I could at least run a Ubuntu 12.04 guest with 3D in VB 4.2.4 but 12.04 now crashes in VB 4.2.6. Ubuntu 12.10 guest crashes on both VB 4.2.4 and 4.2.6. These findings are on both my Mac and Ubuntu host systems. In short, VB support for 3D acceleration with Ubuntu guests is currently a huge mess.

---

### Post by Paddy Landau on 2013-02-01
Sorry to hear that, Mark. Unfortunately, I have no further suggestions to make :(

---

### Post by mwolfe on 2013-02-15
I have a macbook pro 2011 with an i7 and 16gb of ram. Ubuntu 12.10 runs horribly as well. I've installed the headers, vbox additions, and added vboxvideo to /etc/modules and then I was unable to get screens to load from unity as screens were not showing. I finally got ccsm installed and was able (with lots of time and persistence) able to uncheck the framebuffer object option (I followed this here:
[http://askubuntu.com/questions/207813/why-does-an-ubuntu-12-10-guest-in-virtualbox-run-very-very-slowly/214968#214968](http://askubuntu.com/questions/207813/why-does-an-ubuntu-12-10-guest-in-virtualbox-run-very-very-slowly/214968#214968))

Now my ubuntu works but it's still painfully slow. It takes 30 seconds to bring up the unity dash. Honestly I ran vm's in 2006 with a single core processor host and a guest with 128mb of ram years ago and they were much smoother than this (gui and all).. Seems we've taken several steps backwards!

---

### Post by mwolfe on 2013-02-15
I figured out the solution, just increase the number of CPU's you give to the guest OS.. This makes a huge difference. Virtualbox says that this will hurt performance but it's not true. It was a major difference.. It works reasonably fast now.

---

