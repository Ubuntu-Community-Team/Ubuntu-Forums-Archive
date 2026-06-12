---
title: "VirtualBox / VMWare tried in 9.10 Karmic"
date: 2009-11-16
forum: Virtualisation
---

### Post by coskierken on 2009-11-16
Ok, I did a full install on 9.10 Karmic on my laptop (Asus A7jp/ATI 1800/3gigs Ram) and it is working fully.  I really have not had one problem to speak of.  When running 9.04, I had VMWare Workstation with XP has guest.  VMWare ran great and was an easy install.  XP worked rather well inside and was fairly snappy.  So, after the full install, I thought I would try VB to see what gains have been made.  XP worked, but it does not compare to VMWare. Maybe it is because I used Synaptic to load it, and I will try downloading it direct from the VB site.  The seamless mode and USB are grayed out and can't figure out how to get them working yet.  I then loaded VMWare 7 and the install was even easier than before.  I then restored a copy of XP I used in 9.04 and it worked great.  Unity in VMWare works great!  For those who have not tried it, it just plain works once installed without any further loading of any files.  Once you have the virtual XP built, then just use VMWare Player to load it. VM saw every piece of equipment I had with no fuss.  After I try the download of VB from there site, I will update if the problems I had are fixed.  I will then load up my desktop with 9.10 with VM 7 and see how it works.  It is a FAST machine with 3.4G C2Q, 8Gigs RAM, and GTS 250 (9800 GTX+).  More later!

---

### Post by fjgaude on 2009-11-17
You are reporting that VMware Workstation 7.0 works with 9.10 perfectly?

---

### Post by coskierken on 2009-11-17
I have not had a problem with it so far.  Granted, I got it loaded with XP Pro SP3, but no problems so far. I did download and tried VB (from their site) last nite and the USB worked.  It was version 3.0.10, not the 3.0.08 in Synaptic.  But, I still could not get "seamless" to work.  Unity, in VM, still worked great.  I may load up the desktop with 9.10 tonight and see what happens.  I will then try VB again as well as VM.  We will see.

---

### Post by fjgaude on 2009-11-17
Thanks for the report... VMware Player 3.0 works perfectly with 9.10, but Server 1.x doesn't. Most don't seem to be able to get Server 2.x to work either.

I await something easy with Server and 9.10, something that doesn't require patching code into the 9.10 kernel.

---

### Post by jchatham on 2009-11-17
Easy you may not get, but I do have server 2.x working, reliably, on Ubuntu 9.10.

Installation and mouse focus issue fix can be found [here]("http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html").
And the remaining tweaks I needed to get it running reliably are described [here]("http://communities.vmware.com/thread/242151?tstart=15") (vmware-hostd crash fix) and [here]("http://ubuntuforums.org/showthread.php?t=1124066&page=2#15") (webAccess stability improvements).

---

### Post by darco on 2009-11-17
VMWare 7.0 Working in Lucid 2.6.32-4!!!



darco

---

### Post by fjgaude on 2009-11-17
I can't say what VMware is doing, I'm sure it has something to do with fixing how 9.10, kernel 2.6.31 and above handles nm, netmanagement. Player 3.0 doing no remote so no nm issues. So they fixed WS 7.0 and then it must be doable for Server 1.0.x. We wait!

---

### Post by coskierken on 2009-11-18
I worked with VMWare 7 Workstation last nite and seems to work fine with 9.10 (64 bit).  I have not used the VM Server, though.

---

### Post by fjgaude on 2009-11-18
Well, certainly this is good news... for VMware knows how to  handle kernel 2.6.30 and above, so there are no issues, at least with Player 3.0 and Workstation 7.0.

I await for them to fix Server 1 and 2.

---

### Post by coskierken on 2009-11-18
Ok, just loaded 9.10 64-bit on my desktop.  Everything seems to be working great.  It did load 107 updates!  I loaded VMWare 7 Workstation and is working as it should.  I just restored my virtual XP to my home directory and works great.  Handbrake will not work in 9.10 :(.  I really like that program and hope they come up with an update soon.  Right know, loading common apps via Quickstart.  For those who use it and load the codecs, there is an error in Movie Player which says you need the gstreamer element dvdspu plugin.  If you hit cancel on the error, the movie will play anyway.  The solution, which I will tell my buddy about (he wrote Quickstart) is that the plugin is in the gstreamer bad set.  It should be fixed in Quickstart by tonight or tomorrow. 

So far, the fresh load of Karmic seems to work rather well.  It worked on my laptop without any problems, either.  I am pretty happy with it.  I got my Epson Artisan 700 scanner working in 9.04, but will not work, yet, in 9.10.  Any help out there on the Epson?  I just run XP virtually, scan, and share the folder with the scans to work with them in Karmic.  Unity is working well, as it did in 9.04.:)

-------------------------------------
MSI MB,C2Q 9550 @ 3.4G, WD Black 500G boot HD, 1 TB Hitachi HD
8 Gigs Ram, Karmic 64-bit/Vista 64 (gaming) dual boot.
Asus A8JP laptop, C2D T7200, 120G HD, 3Gigs Ram/ Karmic 32bit only!

---

### Post by JohnAStebbins on 2009-11-19
> Handbrake will not work in 9.10 
The [development snapshot]("http://forum.handbrake.fr/viewtopic.php?f=6&t=12842") works on karmic.  HandBrake is in a code freeze preparing for an official release.  Should be soonish.

---

### Post by coskierken on 2009-11-19
I will download it tonite and give a try!  Thanks!

---

### Post by coskierken on 2009-11-19
Just got home and was going to download Handbrake.  Went to the site and all programs have been updated for versions for Karmic in 32 and 64 bit.  I loaded the 64 bit and it works great.:D  I just did a movie in 9 minutes (1 gig )and the quality is pretty good.  Now to just fix the Epson scanner.

---

### Post by madtom1999 on 2009-12-27
Just tried to load VMware on my 9.10 but synaptic says 
Depends: libstdc++5  but it is not installable

this is cos 6 is installed! Will it work if I force an install?

---

### Post by coskierken on 2009-12-28
Which version of VMWare did you try to install?  I know VMWare Workstation 7 works on 9.10.  Once you get the VMware version of Windoz working, you can just load VMWare Player on any other machine and then copy the Windows folder (in home directory) to a usb stick and move it to another machine to use that has VmWare Player installed.

---

### Post by madtom1999 on 2009-12-28
I tried to load the 'standard' one that appeared in Synaptic.

---

