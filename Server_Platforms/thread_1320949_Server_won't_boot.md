---
title: "Server won't boot"
date: 2009-11-09
forum: Server Platforms
---

### Post by Paul dH on 2009-11-09
Hello,

I've installed the server edition of Ubuntu 9.10 several times on various configurations but I can't get it to boot up.

Hardware:
- HP DC7900
- Onboard raid controller (Intel Q45/ICH10-D0 chipset)
- 2x WD 1TB WD10EADS
- PCI-E Adaptec 1430SA, I did see some notes of this card that it sucks under Linux because of the lack of support from Adaptec. But the newer versions of the kernel should have fixed this.

I tried to install Debian 5.03 (Lenny) But he can't recognize my network card, and since I am no hero at tweaking kernels I gave it up.

Setup 1
Attached the 2 drives to the Adaptec card and made a raid 1 array (Full Mirroring)
Booted up Ubuntu Server CD and installed it, the installation stopped at installing GRUB boot loader. This wouldn't install correct. I tried to complete the installation without bootloader, but this wasn't a great success. I thought that I could boot the system with the help of the installation CD, but no.

Setup 2
Deleted the array and connected the 2 drives to my mainboard and configured the onboard raid to raid 0. Booted up the CD and did the installation. Same story, couldn't boot when installation finished and GRUB didn't install.

Setup 3
This was really weird, I deleted the array and set my bios to handle my disks with AHCI. So that the 2 disks were recognized as normal disks. I Installed the OS with total erase of the partitions. Set the partitions up with guided and entire use with LVM and grub did got installed this time but the system still wouldn't boot. It gave me an error saying that it was waiting to long to load root.....

I ended up with a Ash shell

Setup 4
Detatched one disk and did the same install as above but then without LVM. The whole thing installed correctly as fas as I could see. But I got the same result as above.

Now to the point, I really love to step over to Linux and especially Ubuntu but how can I get this to work. I would like to use the onboard raid or the Adaptec raid. I also have the possibilities of adding a 160GB disk just for the OS but that shouldn't be necessary I think.

If this will work at the end we finally can ditch Windhoze, I just have to convince my father that everything will work in Ubuntu.

Thanks, Paul

---

### Post by Paul dH on 2009-11-16
Bump ...

---

### Post by dca on 2009-11-16
That Adaptec I believe is HostRAID, not so much an actual HW RAID card...  Here's a complaint from someone from years ago which was probably the last time I played around with them:
 
[http://www.brentnorris.net/blog/archives/158](http://www.brentnorris.net/blog/archives/158)
 
Here's the card in question:
 
[http://www.adaptec.com/NR/rdonlyres/47755D37-950A-4E06-9868-B0AF8235A1A3/0/SATA_1430SA_ds2.pdf](http://www.adaptec.com/NR/rdonlyres/47755D37-950A-4E06-9868-B0AF8235A1A3/0/SATA_1430SA_ds2.pdf)
 
...under OS support it's kind of limited to MS, SuSE, & RH.  You can research CentOS ([http://www.centos.org](http://www.centos.org)) and see if it now offers native support for it seeing as how CentOS 5.4 is identical (minus branding) to RHEL 5.4...  Even though there's a possibility of it being supported in 2.6.32 (unlikely), RH back ports a lot of the new HW back to its 2.6.18 kernels...

---

### Post by Paul dH on 2009-11-18
> **dca said:**
> That Adaptec I believe is HostRAID, not so much an actual HW RAID card...  Here's a complaint from someone from years ago which was probably the last time I played around with them:
 
[http://www.brentnorris.net/blog/archives/158](http://www.brentnorris.net/blog/archives/158)
 
Here's the card in question:
 
[http://www.adaptec.com/NR/rdonlyres/47755D37-950A-4E06-9868-B0AF8235A1A3/0/SATA_1430SA_ds2.pdf](http://www.adaptec.com/NR/rdonlyres/47755D37-950A-4E06-9868-B0AF8235A1A3/0/SATA_1430SA_ds2.pdf)
 
...under OS support it's kind of limited to MS, SuSE, & RH.  You can research CentOS ([http://www.centos.org](http://www.centos.org)) and see if it now offers native support for it seeing as how CentOS 5.4 is identical (minus branding) to RHEL 5.4...  Even though there's a possibility of it being supported in 2.6.32 (unlikely), RH back ports a lot of the new HW back to its 2.6.18 kernels...

Ok great, thanks for the reply. I can try out some different configuration options now with the suggested documentation. 

Do you know by any chance if it is possible to update the installation cd of Ubuntu Server Edition with the lates kernel and grub version? Then mostlikely will the new installation of Ubuntu continue the boot process instead of hanging at a boot delay.

And for Centos, I've worked with it a couple of years ago, is it possible to install apt there? If yes that would be great.

I am going to try CentOs now and shall post my results.

---

### Post by Paul dH on 2009-11-21
Here are the results of the installations from CentOS and Fedora 12

I configured the internal raid controller (Intel Q45/ICH10-D0 chipset) to use my 2 disks (2TB) in raid 0 configuration (1TB) I made 2 partitions on it, 1 40GB and the other one 960GB for all home storage and all shares.

I launched the CentOS cd and tried to install, but he wouldn't recognize my card in any way.

Then I tried the Fredora CD and that gave the same results.

The thing I an goint to try tomorrow are, resetting the bios and delete the raid configuration. So that I have a clean system with no special options on it.

It is a shame that all distro's wouldn't work, I think the kernel is the problem. I read somewhere that the .32 kernel would solve all this issues.

I will post my new results tomorrow.

---

### Post by Vegan on 2009-11-21
I would suggest a small disk for boot, and mount the other 2 disks in some folders and this will make life a lot easier.

---

### Post by Paul dH on 2009-11-22
> **Vegan said:**
> I would suggest a small disk for boot, and mount the other 2 disks in some folders and this will make life a lot easier.

After all the trial and error today I realized the same. The only downside of what you proposed is that when that smaller disk crashes the OS is gone to. Thats why I took so much effort in it to try to get it to work.

And I can't have it that Windows ( xp, vista, 7, 2003 and 2008 ) all work like a charm on the raid configuration, unbelievable. But I am definitely staying with linux, cause I want to use Amahi or some other home server app.

---

### Post by jrrivers on 2009-12-13
I had the same issue... I had installed 9.10, then I got the bright idea to configure my system with RAID.  At that point, the installation was hung up at GRUB install (it wouldn't).  Then, I removed the RAID configuration from both the Intel HostRAID SW as well as the BIOS, removed one of the disks, and successfully completed the full install.

I'm installing on the SUPERSERVER 6016T-MT with an ICH10 using the Intel HostRAID solution.

JR

---

