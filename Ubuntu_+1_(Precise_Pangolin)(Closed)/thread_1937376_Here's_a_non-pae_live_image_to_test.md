---
title: "Here's a non-pae live image to test"
date: 2012-03-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-03-07
Just noticed this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44)

> I just created a custom Live-CD, based on 12.04 beta1, with the only difference that it boots and installs a non-pae kernel instead of the pae one.

It's available here for those who want it:
[http://people.canonical.com/~diwic/12.04-nonpae/](http://people.canonical.com/~diwic/12.04-nonpae/)

Note that this is work made by somebody who is not a LiveCD expert by any means, never made a custom LiveCD before, and merely followed the instructions at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) - you have been warned. :-)


I'm recovering from one of the worst seizures I've had in years so everything is still foggy to me, hope I got all the links right :)

---

### Post by grahammechanical on 2012-03-07
I wish you better.

Regards.

---

### Post by ventrical on 2012-03-07
> **kansasnoob said:**
> Just noticed this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44)



I'm recovering from one of the worst seizures I've had in years so everything is still foggy to me, hope I got all the links right :)


Sorry to hear of your ailment K-noob. Get well soon.  In the last three years I have had 6 upgrades to my eye-glasses and I feel like my head is in a cage sometimes. In 1990 I wrote a theory about spending too much time on ega/vga moinitors... and how it can affect our eyesight :) ok .. now I m off topic..now .. get well soon ..

---

### Post by Starks on 2012-03-07
Pentium M machine?

---

### Post by joey-elijah on 2012-03-08
Nice! Thanks for this, been wanting to see how much of a strain 12.04 puts on one of my older netbooks (celron M CPU)

---

### Post by zika on 2012-03-08
> **kansasnoob said:**
> I'm recovering from one of the worst seizures I've had in years so everything is still foggy to me, hope I got all the links right :)
I wish You all the best!!!

---

### Post by kansasnoob on 2012-03-08
> **Starks said:**
> Pentium M machine?

I should have provided a bit of an explanation :(

This is a good place to start:

[http://ubuntuforums.org/showpost.php?p=11661116&postcount=1](http://ubuntuforums.org/showpost.php?p=11661116&postcount=1)

Currently there are only three "tried and tested" procedures to maintain a non-pae kernel in Precise:

#1: Upgrade from Lucid, specifically 10.04.4, using "update-manager -d -c". I should note that this won't work for Lubuntu!

#2: Upgrade from Oneiric. I've tested that in both Ubuntu and Lubuntu using "update-manager -d -c" after applying all security updates to Oneiric.

#3: Use the non-pae mini.iso as discussed here:

[http://ubuntuforums.org/showthread.php?t=1924455](http://ubuntuforums.org/showthread.php?t=1924455)

Unfortunately most of those effected are Thinkpad owners, some of whom lack access to a wired connection :(

And we all know that upgrades can sometimes be problematic, may drop a wireless connection, and a wired connection is absolutely necessary with the mini.iso. So I'm still looking for other options.

---

### Post by jerrylamos on 2012-03-08
> **Starks said:**
> Pentium M machine?

Starks, glad to see your post - I've gotten a lot of good info from you before.

This is IBM Thinkpad T40

 Intel(R) Pentium(R) M processor 1500MHz

jerry@ThinkPad-T40:~$ cat /proc/meminfo
MemTotal:         765636 kB

flags		: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2

jerry@ThinkPad-T40:~$ cat /proc/version
Linux version 3.2.0-18-generic-pae (buildd@rothera) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu2) ) #28-Ubuntu SMP Fri Mar 2 22:11:12 UTC 2012

ls /boot
abi-3.2.0-18-generic-pae         memtest86+.bin
config-3.2.0-18-generic-pae      memtest86+_multiboot.bin
grub                             System.map-3.2.0-18-generic-pae
initrd.img-3.2.0-18-generic-pae  vmlinuz-3.2.0-18-generic-pae

Downloaded Daily Live using Lucid Lynx LTS on another partition

Booted the .iso direct from the hard disk

Installed precise pangolin Beta as above, it's running here for this post.

Early on in precise there were some precise .iso that refused to boot I assume they checked for the pae flag which this Pentium M doesn't have.

Running fine now.  Do note the odd memory size, a 256 MB and a 512 MB.  Many Thinkpads are at 1 GB I don't know what that has to do with the price of eggs in China.

Do note I have another partition built from the mini.iso which is just "generic".  I used the regular mini.iso not the non-pae one, and it installed the "generic" like I intended.  I may have used a wired connection I forget.  

precise doesn't support the built in Cisco wireless so I have an old Realtek wireless plugged into the pc card slot.

This thinkpad running fine, a bit creaky I have to prop up the left front corner of the keyboard sometimes the screen goes blank and I have to twist the case.  Loose connection somewhere inside, or maybe a crack or something.

My son-in-law has a Thinkpad T60 but he's in Salt Lake City and doesn't do linux.  That's a Pentium R.

Good luck.

Jerry

---

### Post by nm_geo on 2012-03-08
> **kansasnoob said:**
> Just noticed this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44)



I'm recovering from one of the worst seizures I've had in years so everything is still foggy to me, hope I got all the links right :)

Hope you are doing well kansas.. You will be included in my prayers.  

I will give that kernel modified iso a run later thanks for the link..

---

### Post by kansasnoob on 2012-03-08
> **nm_geo said:**
> Hope you are doing well kansas.. You will be included in my prayers.  

I will give that kernel modified iso a run later thanks for the link..

Don't waste a prayer on this agnostic ;)

I'll be fine, but the taste of my own tongue has me worried :D

---

### Post by kansasnoob on 2012-03-08
> **ventrical said:**
> Sorry to hear of your ailment K-noob. Get well soon.  In the last three years I have had 6 upgrades to my eye-glasses and I feel like my head is in a cage sometimes. In 1990 I wrote a theory about spending too much time on ega/vga moinitors... and how it can affect our eyesight :) ok .. now I m off topic..now .. get well soon ..

I was airing up a tractor tire and I wonder if it wasn't due to flickering fluorescent lights in the shop :confused:

They're old school lights and they tend to flicker when it's below about 60 degrees Fahrenheit.

---

### Post by jerrylamos on 2012-03-08
Kansasnoob, lot of people out here rooting for you.  

I'm even caving in to the inevitable ubuntu unity.  I've seen pictures of similar desktops on pc, tablet, and smartphone from competition.  Also a pic of ubuntu unity on a tablet, though it runs so well on this netbook I'm not sure i'll try.  It's the same size as my tablet though heavier and shorter battery life, ...

Jerry

---

### Post by kansasnoob on 2012-03-08
> **jerrylamos said:**
> Kansasnoob, lot of people out here rooting for you.  

I'm even caving in to the inevitable ubuntu unity.  I've seen pictures of similar desktops on pc, tablet, and smartphone from competition.  Also a pic of ubuntu unity on a tablet, though it runs so well on this netbook I'm not sure i'll try.  It's the same size as my tablet though heavier and shorter battery life, ...

Jerry

The current iteration of Unity is sweet IMHO!

But I'll still provide a guide for those really wanting a classic DE in Precise shortly after it's released :)

That's how I roll. It's like this "non-pae" thing, I have no effected hardware but I want everyone to be able to enjoy some flavor of Ubuntu :D

---

### Post by kansasnoob on 2012-03-08
I completed one test on a VIA C7 w/P4M800 which does support the pae kernel and it worked just fine so I think it's a good image.

I need to know if it actually works on a machine that requires non-pae :)

---

### Post by ventrical on 2012-03-08
I have 12.04 pae n.n.n.17 fresh beta1 install running on a Coppermine PIII (750MGz which is really only 600) and just over 512MB of SDRAM.  What I did was install it on an HDD using another PC, took the HDD and installed it here. Works beautifully. This was my machine that I was using to  test GNOME Classic. I updated a while ago on the original drive and it blew right up .. that harddrive started playing a jazz drum tempo...doo doo ,da , click doo ddo da, click-click: doo doo da .. etc.. just plain weird - so now I am going to install gnome-classic and gnome (no effects) .. ok .. back on topic ..

lventrical@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0f.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
00:11.0 USB controller: NEC Corporation USB (rev 41)
00:11.1 USB controller: NEC Corporation USB (rev 41)
00:11.2 USB controller: NEC Corporation USB 2.0 (rev 02)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage 128 Pro Ultra TF
ventrical@ubuntu:~$

---

### Post by kansasnoob on 2012-03-08
> **ventrical said:**
> I have 12.04 pae n.n.n.17 fresh beta1 install running on a Coppermine PIII (750MGz which is really only 600) and just over 512MB of SDRAM.  What I did was install it on an HDD using another PC, took the HDD and installed it here. Works beautifully. This was my machine that I was using to  test GNOME Classic. I updated a while ago on the original drive and it blew right up .. that harddrive started playing a jazz drum tempo...doo doo ,da , click doo ddo da, click-click: doo doo da .. etc.. just plain weird - so now I am going to install gnome-classic and gnome (no effects) .. ok .. back on topic ..

lventrical@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0f.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
00:11.0 USB controller: NEC Corporation USB (rev 41)
00:11.1 USB controller: NEC Corporation USB (rev 41)
00:11.2 USB controller: NEC Corporation USB 2.0 (rev 02)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage 128 Pro Ultra TF
ventrical@ubuntu:~$

Sounds like a tune I'd enjoy :D

Odd indeed.

---

### Post by jerrylamos on 2012-03-08
> **kansasnoob said:**
> I was airing up a tractor tire and I wonder if it wasn't due to flickering fluorescent lights in the shop :confused:


That's classic.  My daughter's mother-in-law will get a screeching migrain even from the bright white painted lane separators on the highway.  In Japan they've reported severe effects on some children to cartoons with brightly flashing images.  When the TV flashes rapidly from one image to another I can't stand it and don't look.

Sounds like time to replace those old lights just in case.

Jerry

---

### Post by Irihapeti on 2012-03-08
Another install option, though it's definitely not beginner-friendly: [https://help.ubuntu.com/community/Installation/FromLinux#Without_CD](https://help.ubuntu.com/community/Installation/FromLinux#Without_CD)

I've used it several times, and installed the non-pae kernel on two of those occasions.

Although I have a reasonable monthly bandwidth allowance, it's not unlimited either, so I use apt-cacher-ng and a few other tricks to "recycle" as many packages as possible.

---

### Post by jerrylamos on 2012-03-08
> **kansasnoob said:**
> The current iteration of Unity is sweet IMHO!

But I'll still provide a guide for those really wanting a classic DE in Precise shortly after it's released :)

That's how I roll. It's like this "non-pae" thing, I have no effected hardware but I want everyone to be able to enjoy some flavor of Ubuntu :D

I do use Lubuntu for a more classic feel on my Thinkpad T40.  It's running precise generic-pae but shouldn't so who knows when it will stop.  Nice quick handy usable laptop but ubuntu is only interested in "new" pc's.

I always keep backup Lucid LTS or Meerkat around for straightening out partitions & big downloads and grub2.  For some reason precise calls the boot hard drive "b" and the secondary hard drive "a" while every ubuntu since dapper drake called the boot hard drive "a" and the secondary hard drive "b".  Yes I entered a bug which was ignored.

The mini-iso is fun, seeing what I need and what I don't.

Jerry

---

### Post by verymadpip on 2012-03-10
> **kansasnoob said:**
> 
Unfortunately most of those effected are Thinkpad owners, some of whom lack access to a wired connection :(

Hi folks.  
With regard to this, I was able to install from the March 3rd non-PAE mini iso ***without*** a wired connection.

The installation was on a Compaq TC1000 tablet PC which has a built in Atmel at76c506 wireless network adaptor which I ***didn**'t*** use.  My main reason was that it can't handle WPA/WPA2 encryption & that's what the 2 networks I'll be using most have. (I guess it's fine if one is out & about & using some coffee shop's unsecured network).  Anyway, I also needed to install firmware that I didn't have for this to work, very much like what happens with the Debian installer.

Instead I used a USB wireless adaptor that I have lying around.  This worked like a charm.  I just had to enter the SSID, encryption type & password when prompted.

From lsusb I gather that the adaptor has an Atheros AR9271 chip that does all the work.

Hope this is useful to someone :)

---

### Post by kansasnoob on 2012-03-10
> **verymadpip said:**
> Hi folks.  
With regard to this, I was able to install from the March 3rd non-PAE mini iso ***without*** a wired connection.

The installation was on a Compaq TC1000 tablet PC which has a built in Atmel at76c506 wireless network adaptor which I ***didn**'t*** use.  My main reason was that it can't handle WPA/WPA2 encryption & that's what the 2 networks I'll be using most have. (I guess it's fine if one is out & about & using some coffee shop's unsecured network).  Anyway, I also needed to install firmware that I didn't have for this to work, very much like what happens with the Debian installer.

Instead I used a USB wireless adaptor that I have lying around.  This worked like a charm.  I just had to enter the SSID, encryption type & password when prompted.

From lsusb I gather that the adaptor has an Atheros AR9271 chip that does all the work.

Hope this is useful to someone :)

Thanks for the info. That should be helpful to others. I'll make note of it in my mini.iso testing thread.

Oops, I see it's already there.

Must acquire more memory ................ human memory!

---

### Post by verymadpip on 2012-03-10
lol

kansasnoob, it got moved to its own thread as it descended into stuff about ndiswrapper not working.  I should have kept to the short version :)

(Hey man, hope you're feeling better).

---

