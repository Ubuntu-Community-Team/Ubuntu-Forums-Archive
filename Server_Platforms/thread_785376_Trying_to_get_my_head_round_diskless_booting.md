---
title: "Trying to get my head round diskless booting"
date: 2008-05-07
forum: Server Platforms
---

### Post by Cadmus on 2008-05-07
Ok, so let us imagine we've got the usual setup of a desktop connected to a server serving dhcp, and the desktop has a local OS (or two) installed on it, all controlled by GRUB.

Now this is fine, but let's say we want to take it a little further and have network booting available also. We'll assume that it's a modern desktop that has no driver problems or anything else stopping it form doing a network boot as described [here on the wiki]("https://help.ubuntu.com/community/DisklessUbuntuHowto") (is this up to date?).

What I'm trying to fathom is if it's possible to have GRUB (or some other menu system) on the server and presented to the desktop after you've chose to do a network boot so that you could chose between say, a utility disk (like Knoppix) on ISO or a diskless boot of Ubuntu. Please see attached diagram to see what I'm trying to do.

According to evidence [on LinuxQuestions]("http://www.linuxquestions.org/questions/linux-software-2/grub-booting-an-iso-image-315354/") if you have no problems messing with partitions you can make a machine boot from an ISO that's been 'burned' onto an HD partition, with LVM I can't see this being too hard.

However I just can't seem to find anywhere that says "Yes, here's how to offer GRUB to a machine doing a network boot, even if it has no HD".

I'm still waiting for a project to finish so I get access to the spare servers that will free up to test things, but I was hoping someone might have tried something like this and give me a few pointers. Even 'Bootloaders for the hard of thinking' would help me understand the relationships better.

---

### Post by songshu on 2008-05-07
not 100% sure, but i think the double GRUB  theory will not work

what i think you can easily do:

*boot from harddisk to grub
grub will show the following options

1 boot XP on local hd
2 boot other on local hd
3 boot from network

1 when you select boot from network the request is send to the server
2 the server will reply to the request by presenting the kernel to load
the server can choose on mac or ip wich os it will present the client but it will not let the client decide (somebody correct me if i'm wrong)

this would imply that you can only PXE boot the os that the server presents you.


nevertheless i think there is still a workaround by using GDM in choosing wich X-server to log in too (local or remote), wich will give you the same result in the end.

by using virtualisation you can run different OS's on your server to connect to from GDM

should work i think

---

### Post by timcredible on 2008-05-07
the pure netboot installations i've done have had no ability to present choices - the client machine powers on, does a broadcast on the network to get it's server, and connects.

if you want a choice, how about booting from cd and then being presented with being able to choose xdm (unix/linux), rdp (windows), citrix (whatever it's protocol is), etc.?  that's what pxes will do for you.  you will need a server accepting connections though.

---

### Post by Cadmus on 2008-05-08
Thanks for the information, it's giving me places to look to understand netbooting in better detail.

I think what I'm after is a little beyond where the software is at the moment, but you must admit, there's no reason why you *couldn't* have a selector on a network boot.

---

### Post by songshu on 2008-05-08
just an idea,

i'm not really up to date on netbooting, but the server should be able to direct clients to their correct location to find their kernel to load based on things like IP and MAC address

meaning you would need to make a grub entry that enables the server (dhcp or ftp) to identify the choice you made, some kind of ip or mac spoofing should be doable.

GRUB will give you the choice BEFORE you load an OS, not after.

not sure what you are trying to accomplish but as said before you might look again at the option of GDM that can present you the choice wich xserver on wich server to log in to..

whatever....

have fun and keep us posted on your results

---

### Post by Cadmus on 2008-05-08
What am I trying to acheive? That's a good question, still trying to figure it out myself :)

One use for it would be in my office environment, for various reasons I'm unlikely to get to install Linux on my own workstation, but I reckon I could get a chance to do a diskless boot as this would leave the machine unmolested so anyone else can use it or have it swapped.

This gave me a thought, as we have windows machines which are wont to accumulate cruft I've got a disc image on a server which I put on with a Knoppix disc (also used for general examination and cleaning), if only it were possible to have a choice of things to boot over a network, that way I could leave the workstation HD untouched while still being able to choose my own OS and do admin stuff. Even better it would save me loosing disc-image cds ad boot cds and install media.

So yes, a bit pie in the sky, but isn't that what we do with FLOSS? :lolflag:

---

### Post by koenn on 2008-05-08
> **Cadmus said:**
> 
So yes, a bit pie in the sky, but isn't that what we do with FLOSS? :lolflag:
Interesting question.

I think the left-hand part of your diagram is correct. 
It's the BIOS that will select the boot device (eg PXE or HDD). 
Assuming you select / get PXE, what will happen next is that the dhcp-server will tell your client what file it should load next, and from which server to get it. 
I can imagine you can mess with server names and IP addresses to manipulate what server you'll get, and use that as a means to select an OS to boot. I also think this is going to be ugly. 

Probablymore feasable is that you netboot a syslinux. Syslinux has a menu and config mechanism that lets you decide which kernel to boot, and with which boot parameters. It's the sort of menu you get when you boot an Ubuntu Alternate or Debian install CD. If you create one option that boots a knoppix kernel with the correspnding initramfs, and another option  to boot  an ubuntu desktop kernel with the corresponding initramfs, you're half way there, I think. 
I'm not sure you can netboot syslinux, and if you can you'll still need to work out the thinclient configs for both net-booted systems on one server (a Knoppix filesystem, an ubuntu filesystem, ...) but I think it's worth a shot. It's FLOSS: experimenting is encouraged.

---

### Post by songshu on 2008-05-08
offcourse the entire operation would be simple if you would use FreeNX or something.

but that would ruin the fun ;)

---

