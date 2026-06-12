---
title: "I can't install Linux based software on my old PIII, but XP installs just fine"
date: 2017-03-06
forum: Ubuntu/Debian BASED
---

### Post by lammert-nijhof on 2017-03-06
I have an old HP Vectra VLi8 Small Form Factor PC, PIII and 384MB. I have grown fond of that machine; in 2008 I put a 250MB and 320MB HDD in it; put it in a cabinet and used it as file server for the family till 2013, when it stopped working. It was running a Dutch version of XP in the Dominican Rep. Now I resurrected the PC, the 250MB disk was dead and did shut down the PSU. 

My idea was to put Peppermint 32 bits on it, because it looks like an visually attractive alternative to Lubuntu and Spanish is readily available. Then I realized that the newer versions needed PAE, so I stepped back to Peppermint 3, based on 12.04 I believe. In trying to install it, it freezes in the first installation screen, no reaction to the keyboard. No problem I still had a Freedos CD lying around to investigate the problem, but that did also freeze at the first screen. 

Then I tried to copy a Vbox peppermint VM to a disk mounted in an USB case. That I got working somewhat, using some Grub commands till after the area where it was finished with initrd.img and destroyed the RAM disk, then it halted again. But that is another problem described in virtualization section of this forum. 

As a last resort I loaded the famous boot repair iso, but again it did freeze, on the first screen. The screen where I have to choose, to use it normally or in safe mode. The crazy thing is that Windows XP installs OK, at least it reacts normally to the keyboard and start to read all the drivers it needs for the installation and I can nicely stop the installation. It works and does not freeze on the first screen. My question is: "What stupid thing do I overlook?" And the second question: "Do I really have to install Windows XP again?"

---

### Post by howefield on 2017-03-06
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by mörgæs on 2017-03-07
Windows XP has not received security patches for years. It was unsafe while it was supported but even more now. 

A Pentium 3 has PAE so no problem here.

I suggest that you read the link in my signature and search for the very lightest alternatives, both within the Buntu family and without.

---

### Post by lammert-nijhof on 2017-03-07
I googled and the article said, the PIII processor did support PAE, but not all motherboards did support PAE. I started with Peppermint 6. I think after that went wrong, I decided to use Peppermint 3 to exclude the PAE issue. I know about the XP security patches, but if it is the only system that can be installed, I have no choice.
I like Peppermint the child of Lubuntu, but my problem is not the selection of a distro. My problem is why do all those grub/linux based systems (Freedos, Boot Repair and Peppermint 3 and 6) freeze on the first installation screen on this PIII. Basically Peppermint uses the standard Ubuntu install, so I strongly expect Lubuntu would freeze too. Remember the PIII installs XP and from harddisk I managed to get the OS initialization process half way. It is not the ISO, because I used the same ISO to install Peppermint on Virtualbox without problems. 

My desktop DVD writer is defect, so I used an old CD writer to write the CD with Brasero. I try to read it using a DVD ROM. I remember Brasero did give an error message about permissions, but I could copy the CD to my desktop without any problems, so I ignored it upto now. However Freedos has been written half a year ago. I will try booting my desktop from that CD and come back to you.

---

### Post by $yl9pAR%t on 2017-03-07
Try to install Ubuntu 16.04 Server Edition 32-bit, if successful you can add later LXDE or full Lubuntu-desktop package.

I have to admit, for 384 MB RAM, Windows XP is the best choice.

---

### Post by lammert-nijhof on 2017-03-07
I cleaned the CD writer with a cleaning disk, wrote Peppermint 6 again with slow speed. Checked the disk on my desktop, by choosing that menu item and I also loaded the try version of the OS on my desktop. Went to the PIII and again it froze in the installer boot menu. 

I like the server idea, but unfortunately I only have CDs and a working CD writer and the server version is over 800MB. I will have to replace my defect DVD writer and buy some empty DVDs. But because of your remark I remembered the day that I used a 'Lubuntu 12.04 alternate install' with the real simple blue screen XP type of installation. I installed it on another PIII as music player for a restaurant. For 16.04 the Lubuntu pages point again to the server for the alternate install, but I now download the Lubuntu 14.04 alternate install version <800 MB and upgrade that over the internet to 16.04. The disk is no problem 250 MB.

---

### Post by lammert-nijhof on 2017-03-07
Tried with alternate install. Did run the first 5 memory test without errors, so no hardware defects. But Lubuntu 14.04 died almost directly, black screen and no light on disk and CD. I tried the command line option with the same effect. Also the disk checking option resulted in a black screen. I give up and will install Windows XP again.

---

### Post by $yl9pAR%t on 2017-03-07
Standard CD is enough for Ubuntu 16.04 Server. I don't know where you saw 800 MB, I see "ubuntu-16.04.1-server-i386.iso" has 652 MB. You will find it in link below.

[http://old-releases.ubuntu.com/releases/xenial/](http://old-releases.ubuntu.com/releases/xenial/)

---

### Post by lammert-nijhof on 2017-03-07
OK that was the indicated size of the CD I wanted to download through a bit torrent from the Ubuntu site. In adding the torrent it said: Ubuntu-16.04.02-server-i386.iso     839.9 MB. That is why I stopped. I do not believe the size increased from 16.04.01 to 16.04.02 with around 200 MB. Something must be wrong, the Bittorent or the the size indication of your link or the server has gained a lot of weight between 01 and 02. But anyhow I have run out of CDs.

But in the mean time installing XP went OK for phase 1, where it formats the system partition and copies the files to disk and prepares the disk for booting. After the restart it did not boot from disk but died with a black screen. I'm completely lost now and lost my confidence in Microsoft, at least I expected a blue screen from them.

I start too think about a hardware problem
- CD media, I had them checked unfortunately by the same drive that wrote them.
- CD writer, I did use the DVD writer from a laptop the first few times and that did give the same issue.
- DVD Reader, it did read all the XP files from CD to Disk and it did get relatively far with executing the repair function of Lubuntu 14.04.
- Memory, it did pass the first 4-5 tests of the memory test of the Lubuntu CD, I will now try the whole test.
- CPU seems to work with some failed boots and with the memory test.
- The machine has been running XP before and I do not remember any problems from that time.
- Disk has been used in the USB/IDE case and I could even boot the system from the disk on my desktop. XP has formatted the OS partition without problems.
- Power, I use a 90 W power supply from an IBM desktop (RIP). According to specs (HP and on HDD & DVD) the power consumption is CPU: 30W, Video 10-15W, HDD 12W, DVD 22W, PCI Card ? It is on the edge or just over it, dependent on the idle PCI card.

OK to be sure, I will take the PCI card out and use the USB/IDE case for powering the CD/DVD. And I will connect the same CD RW to the PC IDE cable.

+++++++++++++++++++++++++++++++++++++++
OK did that and no result or better the same issues with both Peppermint and the Lubuntu alternate install. 
Power is not the problem. The PIII PC only powered: CPU: 30W, Video 10-15W, HDD 12W = 57W in total from the 90W supply.
No CD/DVD compatibility problem, because I used the same CD this time.

Running the complete memory test now....

A small mistake the original power supply of the Vectra VLi8 was 90 Watt, that IBM power supply is 145 Watt.

Internal gpu finished? It freezes after displaying the graphical installation screens or with XP on the moment XP restarts in graphical mode, but it does not explain the black screen after the alternate install of Lubuntu 14.04.

---

### Post by mörgæs on 2017-03-08
> **lammert-nijhof said:**
> I googled and the article said, the PIII processor did support PAE, but not all motherboards did support PAE.

Links, please.

Have you tried the minimal ISO? First step could be aiming for a text-only system. When that works we can consider a GUI.

---

### Post by lammert-nijhof on 2017-03-08
I thank everybody for the support, but I spend two days on that machine and that is enough. I bought it for &#8364;40 around 2006 and used it for a few months as my desktop. Afterwards it got promoted to family server from 2008 till 2013/14 running XP and 2000. It has been real value for money. It has only 2 PCI slots and I tried it with a PCI 128 MB Radeon video card, but I got the same problem. The motherboard is defect I think, because it does not install XP and it does not install any of the grub-linux distros I tried. Remember I did run and install XP and 2000 on that machine in the past without any problem. It has been fun, but sometimes you loose. I removed all parts and will dump motherboard and case. At least I learned in the process, how to move a VirtualBox VDI to a real hard disk using Gparted and how to include it in my main desktop boot menus.

---

