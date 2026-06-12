---
title: "Paranoid or Under Attack ?"
date: 2014-02-07
forum: Ubuntu, Linux and OS Chat
---

### Post by james_smith2 on 2014-02-07
Hi guys,
 
Admittedly I'm faily new to linux but something just seems very strange.  I downloaded alpine Linux because of the Grsecurity, PAX etx and additional protections I feel nessacery.  3 days after being plugged into a BT router things stated going odd.
 
Maybe I'm paranoid but firstly,
 
1. A script appeared a long with a load of others, one of them was called GFXPAYLOAD

Now this actualy turns off the graphics on the motherboard if I attempt to change any of the core system files.
2.  A third partition that is only visible under certain circumstances &#8211; yet Im faily sure I only setup 1 partition and a swap on SDA2 yet theres 3 visible but only if I bot in with certain disks like  M linux &#8211; strangely even if I enter as root or with M linux I cannot access or change permissions of most of the file system of the third partition.
 
Now heres what makes it interesting, this is  
1.  A brand new PC
2.  A brand new copy of Alpine-Linux written off by the computer shop
3.  Brand new phone line, router and ISP

None of my old media have been near the system and wireless is turned off and I'm ethernet only.
I also noticed it has created an Atheros wi-fi emulation driver &#8211; yet I don't have a wi-fi card and if I did it wouldn't be atheros since they are used for hacking.

Now, today I attempted to download Lubuntu &#8211; the file size was reported by the website at 696mb and would fit on a CDR.   The download however was 729mb once finished???

I've stated to analyse my system more and there are so far 34 TTY connections via the serial bus.  Although Terminal reports only 2 belong to me.  The root account is now in a group called root as well.  I never created a group for it.  It was simply a username root account.  There appears to be another 16 groups as well which are anonymous logins, samaba shares etc

Theres a strange directory that is a never ending loop.  You click it and it just continues forever /boot/boot/boot/boot/boot/boot/boot etc etc

My GRSECURITY file seems to of altered and is now a symlik to a program called BUSYBOX.  What is this?
Also a dir appeared called tmp and I looked inside and theres a locked file called  orbit.pulse  that I cannot access  and theres an SSH-xxxxxx dir with a file caled agentxxxx and inside this a PID number.

I also found in my /SBIN directory ZFS executables although tried ZPOOL but it wouldn't allow me access.  I thought no Linux kernals used the ZHS/ZFS filesystem???   I read that in a magazine last week.

Another file apeared in sbin called OCS-onthefly   any idea what this is?

I just want to know &#8211; am I getting worried about nothing &#8211; normal Linux processes or is something very bad happening.  It just doesn't seem right to me.  Oh yeah I also ran some digital forensics and it stated &#8220;CD-rom drive has triple octet magic-mime&#8221;  I don't know what that means though or if it supposed to be there.
 
It appears I'm being blocked too, any ISO's I download I cannot write to CD.  Ive tried every GUI program out there and they all report &#8220;mount&#8221; errors. 

The computer seemed fine &#8211; until I plugged in my BT router.  I changed the admin PW and turned off WIFI for security ut ever since all this stuff has happened.  It appears to me to be a government /ISP attack on my system.  Unless I'm just paranoid :/

---

### Post by deadflowr on 2014-02-07
You're paranoid.

---

### Post by james_smith2 on 2014-02-07
What worries me - is a brand new pc, brand new ISP.

It has to be a government attack.  I'm wondering if this is part of the gov take over of the internet thats been all over the news in past months.

OK cool - I'm happier to be paranoid!!!    Why does a tmo dir appear stating SSH-43643429 and why can't I access files as root anymore though.  Seems very odd.

Also why does Ubuntu have a load of anonymous login groups.  Windows does that, I thought unix was more secure finding 20 odd remote login groups that you can't remove is far from secure :/

Also why does linux have a GFX pay load ?  I actually had to take the PC back to the shop and pay to get it working again and we found the script but couldn't remove it.  Linux sounds less secure than windows and more like a virus if thats part of it.

You can't view the scripts either, theres some kind of block in place and leafpad ect etc won't view them but libre office would.

There all

!\bin/bash
and
elf32 binaries

---

### Post by dragonfly41 on 2014-02-07
Start by running a ShieldsUp scan on your ports ...

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by james_smith2 on 2014-02-07
is it normal for Lubuntu to grow in size too?  It said it was 696mb

but downloade it was 729mb    :/

---

### Post by Habitual on 2014-02-07
The "**ocs-onthefly**" is used to do disk to disk or partition to partition copy on-the-fly. - Clonezilla
[http://en.wikipedia.org/wiki/Zfs#Platforms](http://en.wikipedia.org/wiki/Zfs#Platforms) - zfs

I'd re-install Alpine-Linux yourself with [http://wiki.alpinelinux.org/cgi-bin/dl.cgi/v2.7/releases/x86/alpine-2.7.4-x86.iso](http://wiki.alpinelinux.org/cgi-bin/dl.cgi/v2.7/releases/x86/alpine-2.7.4-x86.iso)

---

### Post by james_smith2 on 2014-02-07
im running traffic analysis and gufw to blobk al ports but theres ICMP packets flying in and out still?

What is this madness    :/

is the root user suposed to be in a group called root?  and how do you secure your root?

looks like someone else owns it now lol

I dunno if this PC is broken but it won't burn any ISO files.

Ive tried and in the end I had to buy a magazine and use Linux Mint or Ubuntu on the cover disc.   The cover disc alos seeme to alter a dir call isolinux appears.  All kernals change to VMLINUZ
and .com32 .menu32 has appeared in front of the boot lines.  I assume thats normal though?

---

### Post by james_smith2 on 2014-02-07
> **dragonfly41 said:**
> Start by running a ShieldsUp scan on your ports ...

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)



Thank you - looks like the shields are comprimised though Spock!!!

I think I'm gonna build a hardware PF-sense firewall, hire a VPN and change the whole setup!

---

### Post by buzzingrobot on 2014-02-07
I'd never heard of "Alpine Linux" but Google says it's another one of those so-called security distros. They seem to have a forum, so these kind of "so-good-I-posted-it-twice" questions might be better adressed there.

However... most, if not all, of the OP's questions betray a profound ignorance of Unix/Linux.

---

### Post by Don_Stahl on 2014-02-07
I really don't know anything about Alpine either, but according to Wikipedia it's "...[COLOR=#000000][FONT=sans-serif]primarily designed for x86 routers, firewalls, VPNs, VoIP and servers." Perhaps it there lacks some drivers for certain hardware? It also sounds like the C libraries used are not compatible with Gnu C libraries. Meaning, I guess, that Alpine isn't going to work like Ubuntu? Does this shed any light?[/FONT][/COLOR]

---

### Post by mastablasta on 2014-02-08
> **buzzingrobot said:**
> 
However... most, if not all, of the OP's questions betray a profound ignorance of Unix/Linux.

+1
it's not just that it's also the file systems knowledge...

and why Alpine linux as desktop? why the quesiton posted here in Ubuntu forums instead of at Alpine linux support sites?



to check if downloaded iso is good use md5 sum hash or sdh: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

normal download especially ifdoen via wi-fi can get corrupted due to packet loss. to prevent this, it's better to use a torrent download. good luck with your linux experience.

---

### Post by 3rdalbum on 2014-02-08
Unfortunately we do see a lot of paranoia from new users; they barely know anything about Linux, but they think they've found something "unusual" or "suspicious".

Everything described sounds totally normal to me. The only thing you described I didn't know about was the "gfxpayload" thing. A bit of quick research has shown it's a normal part of GRUB. It's even present on my Linux Mint system. Nothing to worry about. And to get in the mind of a virus writer or attacker, there's no way would they use a word like "payload" in a malicious file.

You just have to accept that you don't know much about Linux, and what's normal. A bit of quick Googling will tell you if you've found anything out of the ordinary. Linux is very, very, INCREDIBLY different to Windows; you can be the world's foremost expert on Windows and still be a complete newb on Linux, that's how different things are.

And remember, if an attacker can put files into your system, then they can also convince the system to ignore those files and not show that any changes have been made.

Just relax a bit. Everything you described is normal, and the chances of you getting any sort of malware infection on a normal desktop system are considerably less than you being involved in a car accident. As for being infected on a default install, it's more likely that you'll be killed by a shark.

---

### Post by buzzingrobot on 2014-02-08
> **james_smith2 said:**
> is it normal for Lubuntu to grow in size too?  It said it was 696mb

but downloade it was 729mb    :/

It  didn't grow.  The size was just reported by two different techniques in two different environments.

---

### Post by The Cog on 2014-02-08
I too think you are being overly paranoid. I don't recognise some of the things you mention, but then I have never even heard of your distro. Other people have pointed out some things that they think are normal.

The extra partition is probably a "hidden" system diagnostics partition. If you can post the output of this command then maybe people will be able to explain more:
```
sudo parted -l
```

It is normal for every user, including root, to also have a group of the same name. In Ubuntu it's not possible to log in as root though. You have to log in as someone else and use sudo to raise your privilege.

/boot/boot/boot... is probably the /boot directory containing a symbolic link to itself. Not normal in Ubuntu, but I don't know your distro.

Zsh is available on Linux as a userspace program, not as a kernel module as far as I know. So I'm not surprised to hear that there is a command for it in /sbin.

696 vs 729: This is a difference in reporting. 696 Mebibytes  (696 MiB) is 729,808,896 bytes (730 MB). 729 Megabytes is of course 729,000,000 bytes. 
Some of you software is reporting file sizes in MebiBytes and incorrectly using the MB symbol for it. 

We need more info to sort out your problem with ISO images.

---

### Post by buzzingrobot on 2014-02-08
> **The Cog said:**
> 

The extra partition is probably a "hidden" system diagnostics partition. If you can post the output of this command then maybe people will be able to explain more:
```
sudo parted -l
```



Could also be a recovery partition for another OS.  Those "hidden" partitions are more or less SOP these days.  Installing another OS in a dual-boot setup won't remove them.  You need to deliberately un-hide and remove it. (In my own experience, at least.)

---

### Post by rrnbtter on 2014-02-08
Greetings,
Alpine's own documentation states that help is scattered across the internet. Since it is a non GNU OS I doubt that any but the old timers on this forum that are experienced with the older tool sets can give assistance with that server. I doubt that it [Alpine] is appropriate for a new user as a desktop. Could be that you can get some assistance on a Slackware or Arch forum. I get the security thing though. It's doubtful that any virus programmer would waste their time on something that retro. I'm betting that it is a screaming machine when working properly.

---

### Post by james_smith2 on 2014-02-08
> **buzzingrobot said:**
> I'd never heard of "Alpine Linux" but Google says it's another one of those so-called security distros. They seem to have a forum, so these kind of "so-good-I-posted-it-twice" questions might be better adressed there.

However... most, if not all, of the OP's questions betray a profound ignorance of Unix/Linux.


Correct.

Unfortunately I used to hav faith in Windows and my FW, AVs etc etc then my business was held to randsom and destroyed when I didn't pay.

Afterwards I moved to Linux.  Setup business and was destroyed again.


I know I'm an idiot - but I had faith in Windows and Kaspersky - then I heard Linux was secure so put faith in that.

HENCE - my paranoia.

Truth is - knowledge is security.

For example - Ubuntu is very very far from secure yet the commen myth is that it is.  As standard it requires about 2 hours work and kernal modifications to get to a secure levelwhere its safe to use online.  The grub is the well known target.  Hackers use all sorts though.  SSH-off port tunnels.  Malicious bin/bash and Elf binaries.  Its hard to keep up with it all at my agge and after having 3 menal breakdowns, losing my job twice etc

---

### Post by james_smith2 on 2014-02-08
I chose alpine because it has GRSECURITY, PAX and buffer overflow security built into the kernal already - unlike ubuntu.   :p

These prevent people taking root control of memory access,acpi and the bios!

I'm sorry for my "ignorance"

I should of been here first.  Reading.   But like the windows users I fell for the commen myths.

I'm off to the security forum where I belong, as I'm intreted in lubuntu.  Its way better IMO.  I just need to add a lot of kernal mods and apps - a hardware FW, tripwire and other IDs systems, file size checkers, cloud logging etc etc  theres a list of about 20 things I need to secure any home PC in the modern world thats using the internet.

Linux simply allows this, where as windows has so many built in back doors it doesn't stand a chance.  Thats why people shouldn't dual boot BTW - now you have 2 unsecured operating systems.  Def use a unix varient, then harden it.

Odd.

I used various other Linux environments - the thing is I can md5check but yet Linux comes with a program for altering the MD5. 

Mine have always failed too.  I've never been able to secure any OS as I have to go online to read about it - as soon as I'm on - Im under attack, even by my own ISP!!!

---

### Post by 3rdalbum on 2014-02-10
Very sorry to say this, sir, but you don't need computer help. You are showing some very worrying symptoms of paranoia, and although I hold no medical degrees I think you should consider seeing a professional who can help you deal with personal stress.

You might want to switch off the computer until you have dealt with the stress. After that if you still want help with Ubuntu, I am happy to answer any queries you have. But please see somebody about the stress first.

---

### Post by Irihapeti on 2014-02-10
This is not sounding like a computing problem.

***Thread closed.***

---

