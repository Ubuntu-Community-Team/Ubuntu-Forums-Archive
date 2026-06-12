---
title: "Installing Utopic"
date: 2014-09-17
forum: Ubuntu Development Version
---

### Post by matt_symes on 2014-09-17
Hi

At the risk of being berated for raising a thread not directly related to Utopic, i was interested in how you lot are testing and getting the ISOs onto your test machines.

My media server also serves as a PXE server and i can and do install ISOs onto my machines by PXE booting into the live ISO environment and installing over NFS. 

There is no need to unpack the ISO as i mount it as a loop device and bind mount casper to the tftp folder so the kernel and initramfs can be served via tftp. The main loop mount is exported via NFS and this allows me to install and play with new installations easily on which ever machine i like.

It occurred to me that it may be possible to install the Utopic and future development ISOs using this method.

The idea is to use a script to zsync the daily ISO. This script will be called from a cron job at a time when i am not using the network such as when i am asleep.

The script will also loop mount the ISO and and set up the bind mount. 

Then when i need to install i just PXE boot the test machine and install away. No messing about with USB sticks or CDs and it gets installed to bare metal.

I have not been on the forums much recently as i have been too busy for the forums or testing but i thought this idea may be useful to some of you testers, especially those with multiple test machines.

So my questions are:

Are any of you using this method ?
If not then how are you testing ?
Would this method be of interest to anybody ?

Kind regards

---

### Post by jerrylamos on 2014-09-17
I do something of the sort.
zsync amd64 or i386 or Lubuntu or Xubuntu or kubuntu .....  even debian.  
Goes pretty quick in the background since I have cable internet.  (just internet, no cable TV, no cable or land line phone, we use mobile).

Then I make an entry in /etc/grub.d/40_custom

note, needs to be executable: chmod 777 40_custom

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "utopic64 14.10" {
set isofile="/utopic-desktop-amd64.iso"
loopback loop (hd0,06)$isofile 
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
menuentry "utopic32 14.10" {
set isofile="/utopic-desktop-i386.iso"
loopback loop (hd0,06)$isofile 
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
menuentry "lubunyu utopic 32 14.10" {
set isofile="/utopic-desktop-i386.iso"
loopback loop (hd0,06)$isofile 
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
... for as many entries as you wish.

On the boot ubuntu
sudo update-grub

Do note some of the entries are ...vmlinuz.efi....   and some just vmlinuz.

reboot and make your choice.

Typically I use an external USB hard drive with several 10 MB partitions for testing and a larger archive partition.
In one case there are ubuntu partitions alongside Windows 7 however I've been bit bad by that, usually just stable ubuntu's now,
I test on tower, desktop, notebook, netbook.
Just had a 5 week episode on the Intel Core 2 Duo 3.0 gHz where amd64 ubuntu 3.16.0-7 thru 13 had compiz/unity failures.  
Can't do a whole lot with just the wallpaper.  3.16.0-14 & rc-5 are O.K. so far.

---

### Post by matt_symes on 2014-09-18
Hi

> **jerrylamos said:**
> I do something of the sort.
zsync amd64 or i386 or Lubuntu or Xubuntu or kubuntu .....  even debian.  
Goes pretty quick in the background since I have cable internet.  (just internet, no cable TV, no cable or land line phone, we use mobile).

Then I make an entry in /etc/grub.d/40_custom

note, needs to be executable: chmod 777 40_custom

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "utopic64 14.10" {
set isofile="/utopic-desktop-amd64.iso"
loopback loop (hd0,06)$isofile 
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
menuentry "utopic32 14.10" {
set isofile="/utopic-desktop-i386.iso"
loopback loop (hd0,06)$isofile 
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
menuentry "lubunyu utopic 32 14.10" {
set isofile="/utopic-desktop-i386.iso"
loopback loop (hd0,06)$isofile 
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
... for as many entries as you wish.

On the boot ubuntu
sudo update-grub

Do note some of the entries are ...vmlinuz.efi....   and some just vmlinuz.

reboot and make your choice.

Typically I use an external USB hard drive with several 10 MB partitions for testing and a larger archive partition.
In one case there are ubuntu partitions alongside Windows 7 however I've been bit bad by that, usually just stable ubuntu's now,
I test on tower, desktop, notebook, netbook.
Just had a 5 week episode on the Intel Core 2 Duo 3.0 gHz where amd64 ubuntu 3.16.0-7 thru 13 had compiz/unity failures.  
Can't do a whole lot with just the wallpaper.  3.16.0-14 & rc-5 are O.K. so far.

That sounds like a pretty good method. Not so scalable but good for one machine.

I assume you only have one test machine ?

I think my method may be better for multiple machines. I currently have 6 different machines although three of them would never be used for testing.

Kind regards

---

### Post by zika on 2014-09-18
> **jerrylamos said:**
> Do note some of the entries are ...vmlinuz.efi....   and some just vmlinuz.Now, that You've mentioned, can You elaborate why/when there are different entries (.efi, .)...? Thank You in advance.

---

### Post by zika on 2014-09-18
> **matt_symes said:**
> Would this method be of interest to anybody?Yes, please.

---

### Post by matt_symes on 2014-09-18
Hi

> **zika said:**
> Yes, please.

No problem. I keep a wiki on my media server - my media server also serves as a lamp stack; i know it has many roles - where i document all the steps i take to my configure servers and other useful pieces of information that i come across.

Maybe someday I'll sanitise it, as it contains some sensitive information, and publish it as it may be useful to someone.

BTW: My media server is not connected to the Internet.

Anyway, it has all the steps to setup a DHCP server, a TFTP server and an NFS server. I'll look over it over the next couple of days and come up with a write up of the commands i used and how i configured it.

You will need a PC to run it but you can, like me, multi role your media server if you like.

Kind regards

---

### Post by jerrylamos on 2014-09-18
> **zika said:**
> Now, that You've mentioned, can You elaborate why/when there are different entries (.efi, .)...? Thank You in advance.

Launch file manager
navigate to the desired .iso
Select it, open as folder
select the folder casper
then you'll see
Ubuntu 14.10 amd64/casper/vmlinuz.efi

A while ago on this development forum there was a discussion about efi.  My vague memory is it showed up on ubuntu amd64 but not amd32 etc.

BTW, I test on four machines.  Usually quicker for me to zsync each than transmit the .iso over my home network.  One is 32 bit and uses a different .iso than  the others are which 64.

Oh, don't have two same named copies of the .iso example one on the usb and one on the hard drive.  Ubuntu gets confused and starts reading from both.

---

### Post by ventrical on 2014-09-18
I have 12 machines, 8 over three KVMs. 1 KVM is 4 for 4 PCs and 2 two for 2 PCs KVMs. Rest are not attatched to KVM. I can have 10 machines at a time on the same router connected to the internet and be able to switch back and forth between them.

Regards..

---

### Post by matt_symes on 2014-09-19
Hi

> **ventrical said:**
> I have 12 machines, 8 over three KVMs. 1 KVM is 4 for 4 PCs and 2 two for 2 PCs KVMs. Rest are not attatched to KVM. I can have 10 machines at a time on the same router connected to the internet and be able to switch back and forth between them.

Regards..

Maybe Installing using a PXE server  may help you then, with that number of machines.

Kind regards

---

### Post by ventrical on 2014-09-19
> **matt_symes said:**
> Hi



Maybe Installing using a PXE server  may help you then, with that number of machines.

Kind regards


Agreed.  I used to use PXE during 1989  on other networks using Accpac. Now .. I forget :) lol

Any pointers on how to with ethernet cards?
(note cariboo suggested somethign of the same sort a while back. I installed the ubuntu-server, got it to work but could never get it to connect to a local machine using ethernet cables. Somthing I did or did not do..
.

Using KVMs allows me to do hard installs and gauge the various milestones as they roll out. Yes .. it's a lot of work .. but I enjoy it immensely, time permitting.

Regards..

---

### Post by cariboo on 2014-09-20
> **ventrical said:**
> Agreed.  I used to use PXE during 1989  on other networks using Accpac. Now .. I forget :) lol

Any pointers on how to with ethernet cards?
(note cariboo suggested somethign of the same sort a while back. I installed the ubuntu-server, got it to work but could never get it to connect to a local machine using ethernet cables. Somthing I did or did not do..
.

Using KVMs allows me to do hard installs and gauge the various milestones as they roll out. Yes .. it's a lot of work .. but I enjoy it immensely, time permitting.

Regards..

Make sure all the systems in your local network are in the same subnet. either let your router supply ip addresses via DHCP, or set static ip address in the sub-net as the router uses eg:

If you router ip address is 192.168.0.1, then all the ip addresses should be in the 192.168.0.2 - 192.168.0.255 range.

If you set static ip addresses, make sure all the systems on the network have a seperate ip address, over the years I've set the same ip address on two computers by accident, and when you do that, the results can get pretty strange. :)

---

### Post by ventrical on 2014-09-20
> **cariboo907 said:**
> Make sure all the systems in your local network are in the same subnet. either let your router supply ip addresses via DHCP, or set static ip address in the sub-net as the router uses eg:

If you router ip address is 192.168.0.1, then all the ip addresses should be in the 192.168.0.2 - 192.168.0.255 range.

If you set static ip addresses, make sure all the systems on the network have a seperate ip address, over the years I've set the same ip address on two computers by accident, and when you do that, the results can get pretty strange. :)


 Well .. that's what happened to me. I guess I'll have to try again.  :)

edit:

 It used to be so simple.  Just hook all your locals to a hub that's connected to a server and then use a PXE floppy and , voila' you on the network. ie; like a Token Ring.

---

### Post by sudodus on 2014-09-20
I think you are describing a good method in this thread, [matt_symes]("http://ubuntuforums.org/member.php?u=1067998")      [URL="http://ubuntuforums.org/showthread.php?t=2245020"]

[/URL]and I wish that you will have time enough to make a ***tutorial*** for us (me and I'm sure several other people, who want to use it, but do not understand how to make it work).

-o-

I'm 'competing' with the mkusb method, described at

[mkusb - fast, simple and safe copy from iso file to pendrive for iso testing]("http://ubuntuforums.org/showthread.php?t=2245020")

---

### Post by anika200 on 2014-09-22
> **jerrylamos said:**
> I do something of the sort.

Then I make an entry in /etc/grub.d/40_custom

note, needs to be executable: chmod 777 40_custom



Brilliant :KS Thanks for this method.

---

### Post by matt_symes on 2014-09-22
Hi

> **sudodus said:**
> I think you are describing a good method in this thread, [matt_symes]("http://ubuntuforums.org/member.php?u=1067998")      [URL="http://ubuntuforums.org/showthread.php?t=2245020"]

[/URL]and I wish that you will have time enough to make a ***tutorial*** for us (me and I'm sure several other people, who want to use it, but do not understand how to make it work).

-o-

I'm 'competing' with the mkusb method, described at

[mkusb - fast, simple and safe copy from iso file to pendrive for iso testing]("http://ubuntuforums.org/showthread.php?t=2245020")

I'm about half way through it sudodus :) 

I will post it by the end of the week.

Kind regards

---

### Post by sudodus on 2014-09-23
Thanks a lot, I'm looking forward to it :-)

---

### Post by ventrical on 2014-09-23
> **cariboo907 said:**
> Make sure all the systems in your local network are in the same subnet. either let your router supply ip addresses via DHCP, or set static ip address in the sub-net as the router uses eg:

If you router ip address is 192.168.0.1, then all the ip addresses should be in the 192.168.0.2 - 192.168.0.255 range.

If you set static ip addresses, make sure all the systems on the network have a seperate ip address, over the years I've set the same ip address on two computers by accident, and when you do that, the results can get pretty strange. :)

  I did that experiment and was able to get a connect between two PCs but that's all I got. Of course I would need some more software installs , right ? 

  I got plenty of old wireless routers and lots of cat5 cables, My question first is; would it be better to use a router NOT connected to the internet with Straight_through Cat5 cables or should I simply use crossover Cat5 cables.

Second Question:

 What if I just set up a wireless LAN?

 Now for me, since I have a USB to IDE/SATA bridge cable, it is in fact easier for me to just hook up any hdd via USB but since I have a lot of machines on 3 seperate routers (hooked to main internet router) I just thought that it would be novel to try some of the network experiments, at least to the one PC with my 1.5TB hdd with all my .iso on it.

---

### Post by ventrical on 2014-09-23
My unrelated ethernet to ehternet  cable problem solved here with  neat little programs called Kontrolpack and iptux  both in the USC.

Many thanks to cariboo.

Regards..

*note*

Kontrolpack looks like it is more designed for kubuntu and although it will place an icon on the unity panel in Utopic, it displays a message about a "panel' near the Unity dash icon on the unity panel. However .. works great.

---

### Post by cariboo on 2014-09-24
My home network consists of two routers Dlink and an SMC . There are a  5 port and 8 port switches. I normally have 12 devices connected in a mix of wireless and cabled connections. Except for my two servers, which have static ip addresses. The /etc/network/interfaces files for the servers look like this:

```
cariboo@willy:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

The SMC routers serves as a wireless extender out in my garage, it has a static ip address and dhcp is turned of

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address		192.168.0.205
	netmask		255.255.255.0
	broadcast	192.168.0.254
	gateway		192.168.0.1
	dns-nameserver	8.8.8.8 192.168.0.1
```

The SMC serves as a wireless extender out in my garage, and has a static ip address and dhcp turned of. The D-link router serves ip addresses to all the other devices.

---

### Post by Chanath on 2014-09-27
Jerry, I tried your method, but utopic doesn't boot. Here is what I have in 40_custom >  #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry “Utopic64” {
set isofile=”/home/czanat/Downloads/utopic/utopic-desktop-amd64.iso”
loopback loop (hd0,09)$isofile
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} noprompt noeject
initrd (loop)/casper/initrd.lz
}


I  checked and it is vmlinuz.efi in casper. Could you tell me, where I've gone wrong.

---

