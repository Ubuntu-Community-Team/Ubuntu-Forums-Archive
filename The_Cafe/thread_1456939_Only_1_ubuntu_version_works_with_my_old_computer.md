---
title: "Only 1 *ubuntu version works with my old computer"
date: 2010-04-17
forum: The Cafe
---

### Post by kenweill on 2010-04-17
I have this old computer of mine, ASRock P4i45GV with 2x 256mb of ram.
And, only 1 *ubuntu version that works with this 5-6 year-old computer, 8.04.

Ubuntu / Kubuntu 8.04 version is the only working distro that works with this computer.

I've tried Arch, sidux, Debian Lenny, Debian Testing, Debian Unstable, Fedora 12, openSUSE 11.2, PCLinuxOS 2009/2010beta, Mandriva 2010, Chakra, Linux Mint 8, Ubuntu 8.10 until Ubuntu 10.04 beta 2, KahelOS, paldo, and other disros, i can't remember them all. All these don't work with my old computer. Some ended up with a kernel panic error. Some ended up with some too fast scrolling text of errors (i can' read it since its too fast). Some ended up with some acpi errors, not syncing errors, buffer errors, etc.

I was wondering why. It must be kernel related.
Posting this thread from Kubuntu 8.04 [Linux kubuntu 2.6.24-27-generic #1 SMP Fri Mar 12 01:10:31 UTC 2010 i686 GNU/Linux], in this old machine i was referring.

---

### Post by juancarlospaco on 2010-04-17
[I]No

use MinimalCD[/I]

---

### Post by Khakilang on 2010-04-17
I had a similar spec once and it work fine on 8.10 and 9.04 but I forgot what the brand of the motherboard.

---

### Post by kenweill on 2010-04-17
> **juancarlospaco said:**
> [I]No

use MinimalCD[/I]

I happened at boot time. Be it a Live CD or install CD.

By the way, i forgot to mention that FreeBSD 8 also works, with sync errors, but at least, it brings me to the login prompt. Not like in linux distros that it really halts.

---

### Post by juancarlospaco on 2010-04-17
HW problems?

install CD != MinimalCD

---

### Post by kenweill on 2010-04-17
> **juancarlospaco said:**
> HW problems?

install CD != MinimalCD

I don't think its hardware problems since Ubuntu 8.04 (both Desktop and Server) works with this machine. Also, Kubuntu 8.04 (im using righ now) also works withou problem

Haven't tried MinimalCD. Don't know about MinimalCD. :(
But i think it's probably kernel related. Probably, this old machine is not supported anymore with newer kernels? I don't know. Im not sure.

I think Arch is considered MinimalCD. And still, it doesnt work.

---

### Post by -jay- on 2010-04-17
all builds before 9.10 work wonders on my desktop  9.10 & 10.04 do not work , i get either no mouse pointer showing to no resume working it suspends but refuses to resume so im pretty much staying with 9.04

---

### Post by kenweill on 2010-04-17
> **-jay- said:**
> all builds before 9.10 work wonders on my desktop  9.10 & 10.04 do not work , i get either no mouse pointer showing to no resume working it suspends but refuses to resume so im pretty much staying with 9.04

Neither lower builds of 8.04 doesn't work as well in this old machine.

---

### Post by cariboo on 2010-04-18
You can get the mini.iso [here]("https://help.ubuntu.com/community/Installation/MinimalCD"), it is a diy type of installation, do a CLI install, then go [here]("http://www.psychocats.net/ubuntu/index") and check out the **Playing Around** section to add a DM (desktop Manager)

---

### Post by the_karmic_koala on 2010-04-18
Xubuntu!!!!!!!!!!!!!!

---

### Post by Dayofswords on 2010-04-18
xubuntu is actually just as heavy as ubuntu

check up lubuntu(in beta though) or do a cli install and 
```
sudo aptitude update
sudo aptitude install xorg lxde
sudo mkdir /usr/share/backgrounds 


```The LXDE screen saver app requires that this directory exist or it returns annoying error messages.

much much lighter than ubuntu or xubuntu

---

### Post by kenweill on 2010-04-18
> **cariboo907 said:**
> You can get the mini.iso [here]("https://help.ubuntu.com/community/Installation/MinimalCD"), it is a diy type of installation, do a CLI install, then go [here]("http://www.psychocats.net/ubuntu/index") and check out the **Playing Around** section to add a DM (desktop Manager)

Thanks. Downloaded the minimal CD of 9.10. Currently installing. Hoping this would work.

> **the_karmic_koala said:**
> Xubuntu!!!!!!!!!!!!!!

Only Xubuntu 8.04 works. Older/newer version doesn't work.

> **Dayofswords said:**
> xubuntu is actually just as heavy as ubuntu

check up lubuntu(in beta though) or do a cli install and 
```
sudo aptitude update
sudo aptitude install xorg lxde
sudo mkdir /usr/share/backgrounds 


```The LXDE screen saver app requires that this directory exist or it returns annoying error messages.

much much lighter than ubuntu or xubuntu

my problem is not how light the *buntu is. It's about this kernel problem at boot time. That only 8.04 *ubuntu's are the one's that's working in this old machine.

---

### Post by Kai69 on 2010-04-18
If its a Kernel problem surely when you do updates the Kernel updates as well ?? Have you tried using ubuntu 9.10 but with an older Kernel.

---

### Post by kenweill on 2010-04-18
> **Kai69 said:**
> If its a Kernel problem surely when you do updates the Kernel updates as well ?? Have you tried using ubuntu 9.10 but with an older Kernel.

it actually happen when booting the cd. haven't tried using ubuntu 9.10 with an older kernel. 9.10 cd should have a new kernel by default in the installer.

@cariboo907
minimal cd of 9.10 doesn't work. got a full screen of errors...

starts with:

pid: 10508, comm: frontend Tainted: G D 2.6.31-14-generi#48-Ubuntu
Call Trace:
__schedule_bug+0x5d/0x70
................
................ too many to type it all..

last line of call trace:
is about page fault... with error_code+0x73/0x80
Killed

Picture of error taken from my cellphone (attached)

---

### Post by -grubby on 2010-04-18
It sounds like a serious hardware problem, frankly. Most likely the motherboard is shot.

---

### Post by kenweill on 2010-04-18
> **-grubby said:**
> It sounds like a serious hardware problem, frankly. Most likely the motherboard is shot.

Windows xp works in this machine. It's just a little slow/laggy.
Ubuntu/Kubuntu/Xubuntu 8.04 also works in this machine without any error messages. It's just that, older and newer versions of ubuntu doesn't work with this machine. only 8.04. Also, other distros doesn't work as well with this machine.

---

### Post by Kai69 on 2010-04-18
Just a sugestion you only have 500MB of ram if you use a live cd the whole cd runs in ram so maybe causing the problems [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)  there is not enough ram to run cd and and os at the same time.

---

### Post by witeshark17 on 2010-04-18
Whatever it is, it's interesting, and rather strange.

---

### Post by -grubby on 2010-04-18
> **kenweill said:**
> Windows xp works in this machine. It's just a little slow/laggy.
Ubuntu/Kubuntu/Xubuntu 8.04 also works in this machine without any error messages. It's just that, older and newer versions of ubuntu doesn't work with this machine. only 8.04. Also, other distros doesn't work as well with this machine.

If only Ubuntu's derivates and XP work on the computer, I still think the problem is deeper than the OS.

---

### Post by kenweill on 2010-04-18
> **witeshark17 said:**
> Whatever it is, it's interesting, and rather strange.

It's really strange.

I removed the NVIDIA GeFORCE FX5500, now using the video adapter built-in in the motherboard, and now it works with newer distros.

Hmmm... Maybe, newer kernels doesn't play well with this NVIDIA card i have with ASRock motherboard combined?

My 2 year old machine with the same NVIDIA GeFORCE FX5500 video card but with ASUS motherboard works well with all distros. I mean, all the distro CDs that I have posted in my first post.

Does that mean, NVIDIA video card + ASROCK motherboard, combined, doesn't play well with new kernels?

Strange.

---

### Post by FuturePilot on 2010-04-18
> **kenweill said:**
> It's really strange.

I removed the NVIDIA GeFORCE FX5500, now using the video adapter built-in in the motherboard, and now it works with newer distros.

Hmmm... Maybe, newer kernels doesn't play well with this NVIDIA card i have with ASRock motherboard combined?

My 2 year old machine with the same NVIDIA GeFORCE FX5500 video card but with ASUS motherboard works well with all distros. I mean, all the distro CDs that I have posted in my first post.

Does that mean, NVIDIA video card + ASROCK motherboard, combined, doesn't play well with new kernels?

Strange.

More likely your graphics card is bad.

---

### Post by Trison on 2010-04-19
Bit of a random shot, but when was the last time you did a BIOS update?  My Fujitsu N6110 laptop refused to boot a large number of live CDs until I updated the bios supplied at their website.  Most CDs wouldn't even load Grub on my laptop though.

edit: Flashing your bios can brick your motherboard if something goes wrong (obviously), so backup your data first.

---

### Post by swoll1980 on 2010-04-19
Sounds like gremlins (not the AMC kind either) Just keep them dry, and ***make sure*** you never feed them after midnight!

---

### Post by kenweill on 2010-04-19
> **Trison said:**
> Bit of a random shot, but when was the last time you did a BIOS update?  My Fujitsu N6110 laptop refused to boot a large number of live CDs until I updated the bios supplied at their website.  Most CDs wouldn't even load Grub on my laptop though.

edit: Flashing your bios can brick your motherboard if something goes wrong (obviously), so backup your data first.

With the asus motherboard, i have updated the bios with the latest bios file found at their website. it was easy on asus board. you just have to download the iso file with the bios update file save it in flash drive, then boot in flash drive.

but with this asrock board, the only way to update the bios is through a floppy drive. i have a floppy drive, but im not sure if it's working or not, but, i don't have a floppy disk. can't find floppy disks anymore in stores. also, booting from flash drive is not supported with this old motherboard. bios can't detect flash drive.

---

### Post by Kai69 on 2010-04-19
I updated my BIOS using a cd you could try that got the driver from Dells website and burned to cd
[http://www.asrock.com/mb/download.asp?Model=P4i45GV%20R5.0&o=BIOS](http://www.asrock.com/mb/download.asp?Model=P4i45GV%20R5.0&o=BIOS)
[http://www.asrock.com/mb/download.asp?Model=P4i45GV%20R5.0&o=XP](http://www.asrock.com/mb/download.asp?Model=P4i45GV%20R5.0&o=XP)

---

### Post by kenweill on 2010-04-20
> **Kai69 said:**
> I updated my BIOS using a cd you could try that got the driver from Dells website and burned to cd
[http://www.asrock.com/mb/download.asp?Model=P4i45GV%20R5.0&o=BIOS](http://www.asrock.com/mb/download.asp?Model=P4i45GV%20R5.0&o=BIOS)
[http://www.asrock.com/mb/download.asp?Model=P4i45GV%20R5.0&o=XP](http://www.asrock.com/mb/download.asp?Model=P4i45GV%20R5.0&o=XP)

<EDIT>
Done updating BIOS but still it doesn't solve the problem. with NVIDIA card installed on ASROCK board, still the problem occurs. It can't be the NVIDIA card as this is the NVIDIA card from another PC with asus board. I swapped the video card. Still it works with NVIDIA+ASUS but not with NVIDIA+asrock.

---

