---
title: "Just a quick question - can somebody reccomend me a floppy-size distro?"
date: 2009-04-26
forum: The Cafe
---

### Post by rhcm123 on 2009-04-26
I have an aging desky that i want to throw linux on. It's so old it has a 1 GB hard drive, 50 MB RAM, and no cdrom drive - otherwise i would have put slackware or DSM on it a while ago.

It only has two 3+1/2 floppy drives. Yeah. those ones. Do you guys know of any good floppy sized versions of these?

---

### Post by cariboo on 2009-04-26
Have a look at this [page]("http:///mypage.uniserve.ca/~thelinuxguy/small_and_floppy_linux/all.html"), at has a list of quite a few floppy based distros.

---

### Post by snowpine on 2009-04-26
Hope this link helps... the higher up on the list, the more likely it will work for your situation. :)

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

If you can get DSL loaded from floppy, that's probabably the most full-featured distro that might possibly work.

---

### Post by albinootje on 2009-04-26
> **cariboo907 said:**
> Have a look at this [page]("http:///mypage.uniserve.ca/~thelinuxguy/small_and_floppy_linux/all.html"), at has a list of quite a few floppy based distros.

Interesting page. 
I'd like to recommend, from that list, this one : [http://www.toms.net/rb/](http://www.toms.net/rb/)

---

### Post by Mehall on 2009-04-26
Debian can fit inside 1GB IIRC, and you don't mind having no GUI.

It has netboot from 3 floppies :D

---

### Post by rhcm123 on 2009-04-26
> **Mehall said:**
> Debian can fit inside 1GB IIRC, and you don't mind having no GUI.

It has netboot from 3 floppies :D

good idea, however... this machine only has a 56k modem. no ethernet, so netboot is kinda outta the options

---

### Post by Mehall on 2009-04-26
Any spare PCI slots or anything? Ethernet cards are dirt cheap, and that would give you a full system.

Also, it's not Linux, but MenuetOS might be a possible thing you want to check out. Fits in a single Floppy ;) I can;t remember the url, but google will hit it fast

---

### Post by pwnst*r on 2009-04-26
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by -grubby on 2009-04-26
> **pwnst*r said:**
> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

DSL is 50 MB...

---

### Post by jespdj on 2009-04-26
50 MB, that would be 35 diskettes (of 1.44 MB each).

Even the very first version of Linux that I tried, Slackware, back in 1994, came on a CD-ROM.

CD-ROM drives are very cheap (probably less than $20). Maybe you can get a CD-ROM drive somewhere and connect it to the old computer. (Watch out that it has the right kind of interface, IDE, not SATA).

---

### Post by Mehall on 2009-04-26
> **jespdj said:**
> 50 MB, that would be 35 diskettes (of 1.44 MB each).

Even the very first version of Linux that I tried, Slackware, back in 1994, came on a CD-ROM.

CD-ROM drives are very cheap (probably less than $20). Maybe you can get a CD-ROM drive somewhere and connect it to the old computer. (Watch out that it has the right kind of interface, IDE, not SATA).

assuming there are any available expansion slots, a NIC would be cheaper than a CD drive, and would maybe let OP use it for a torrent slave or something.

---

### Post by pwnst*r on 2009-04-26
> **nathangrubb said:**
> DSL is 50 MB...

oops

---

### Post by albinootje on 2009-04-26
> **jespdj said:**
> Even the very first version of Linux that I tried, Slackware, back in 1994, came on a CD-ROM.

Slackware had, back then, for a long time, the option to install from floppies only (yes, a lot of floppies). 
I remember doing a Slackware installation from only floppies, but I think I luckily only needed the A,D, and X parts :-)

---

### Post by rhcm123 on 2009-04-26
> **jespdj said:**
> 50 MB, that would be 35 diskettes (of 1.44 MB each).

Even the very first version of Linux that I tried, Slackware, back in 1994, came on a CD-ROM.

CD-ROM drives are very cheap (probably less than $20). Maybe you can get a CD-ROM drive somewhere and connect it to the old computer. (Watch out that it has the right kind of interface, IDE, not SATA).
> **Mehall said:**
> assuming there are any available expansion slots, a NIC would be cheaper than a CD drive, and would maybe let OP use it for a torrent slave or something.

There are expansion slots, and a free drive bay for a cd-rom drive... hmm... maybe ill just get with the times, grab both, slam in my 8.04 server cd, and be done with it :P

---

### Post by Mehall on 2009-04-26
> **rhcm123 said:**
> There are expansion slots, and a free drive bay for a cd-rom drive... hmm... maybe ill just get with the times, grab both, slam in my 8.04 server cd, and be done with it :P

NOOO!!!

not Ubuntu Server, too weighty. With only a 1GB HDD, you need to choose distro carefully. If you get a CD Drive, Puppy will run probably, DSL definitely will.

As I said before, Debian is a good idea if you wanna netboot, whether from floppies or CD.

If you HAVE to use Ubuntu, get the mini.iso and pick and choose your packages VERY wisely.

---

### Post by albinootje on 2009-04-26
> **Mehall said:**
> NOOO!!! not Ubuntu Server, too weighty. 

Erhmm, can you cool down a little ? :-)

Here's some requirements for Ubuntu server :
[https://help.ubuntu.com/8.10/serverguide/C/preparing-to-install.html](https://help.ubuntu.com/8.10/serverguide/C/preparing-to-install.html)

1 Gb of disk space can be fine for a server, depending on what you do with it. The 50 Mb of RAM is much more of a problem for the installation apparently.
Debian has more choice in booting from cdrom (business card, netinstall) than Ubuntu has, and it probably needs less RAM for the installation too.
Slackware could be a wise choice to play with this machine.

---

### Post by jmszr on 2009-04-26
rhcm123,

This site has quite a list, Tiny Linux might do: [http://www.linuxlinks.com/Distributions/Mini_Distributions/](http://www.linuxlinks.com/Distributions/Mini_Distributions/) .

---

### Post by gymophett on 2009-04-26
DSL is a dead project. Try this: [http://www.angelfire.com/anime/db/gcl/](http://www.angelfire.com/anime/db/gcl/)

---

### Post by Mehall on 2009-04-26
> **gymophett said:**
> DSL is a dead project. Try this: [http://www.angelfire.com/anime/db/gcl/](http://www.angelfire.com/anime/db/gcl/)

To be honest, I wouldn't use grey cat either. (I don't use DSL unless I have to)

If I need something minimal to that extent, I use tiny core. Tiny core only hits issues if you have less than 32MB of RAM (by issues I mean "won't run at all")

With fewer than 32MB, I would switch to a BSD (maybe NetBSD) becuase you won't get much done in Linux with less than 32MB, but bsd's stand a chance at being useful

---

### Post by zmjjmz on 2009-04-26
BasicLinux ([http://basiclinux.com.ru](http://basiclinux.com.ru)) is a good distro, and the mailing list is pretty active even if development has gone the way of the XMMS.

---

### Post by rhcm123 on 2009-04-26
> **Mehall said:**
> NOOO!!!

not Ubuntu Server, too weighty. With only a 1GB HDD, you need to choose distro carefully. If you get a CD Drive, Puppy will run probably, DSL definitely will.

:shock:
I just slapped my head with stupidity. it won't run on 50 mb ram and wont fit on a 1 gb hard drive... hmm.. better dig out my arch or gentoo cd.

Also, is DSL really a read project? I just wget (wgot?) the iso.

---

### Post by Sublime Porte on 2009-04-26
You should be able to boot [Tinycore Linux](http://www.tinycorelinux.com) from floppy. The distro is all up 10mb, and has plugins, and is really snappy even on very low end systems. I use it on a 200mhz 128mb ram ebox (about the size of a CD case) and it's lightening fast.

It's actually made by some of the same people as DSL I believe.

---

### Post by Mehall on 2009-04-26
Arch won't run probably. The computer is probably pre-686, so you need Debian or Puppy are best bets. (DSL is good, but limited, and apparently dead)

EDIT: +1 to TinyCore :D

---

### Post by mingtien on 2009-04-27
Some thoughts -- I've just downloaded Slitaz (see Distrowatch for details), and it looks quite slick, so if you do get a CD ROM, it might be a nice choice.  I am going to install it on a mate's machine that has a very basic config (although it does have a CD drive).

Failing that -- go for Slackware 1.1.1.2 -- here is a tar image that has all the floppies: 

[http://www.oldlinux.org/Linux.old/distributions/slackware/](http://www.oldlinux.org/Linux.old/distributions/slackware/)

You will need to make a lot of floppies, but so did everyone else back in the day!  

This will work fine with a 56k Modem; get a vintage version of fvwm, and a basic web browser (I honestly can't remember what I used back then...there wasn't much on the web really).

Let us know how you get on -- I love hearing about people making use of old iron :)

By the way: if anyone knows where I can get hold of OLD slackware iso images (pre 1996), I would greatly appreciate it!  (I want to play with it in Virtualbox, but really don't want to go subbing all those floppies!!!!).

---

### Post by sertse on 2009-04-27
BasicLinux, which was linked earlier in the thread and fits on a single floppy is entirely Slackware *4* compatible. No need for Slackware 1 yet ;)

DSL has a lot of drama, and development isn't as fast, it's death is overstated. :)

The big (small?) four are still DSL, Puppy, TinyCore and Slitaz..

---

### Post by Ticketoride on 2009-04-27
> **rhcm123 said:**
> ... no cdrom drive
The local Buy & Sells should be selling them for $ 5 if you also take away a Bag of Kitchen Trash.

Futzing with Floppies isn't worth anyone's Time.

---

### Post by rhcm123 on 2009-04-27
Well, let me first say this. I caved and installed some (2 acutally) cd drives. I couldent find a ethenet card, but ill keep looking. (I actually had the cd-rom drives in a box in my closet, and stumbled upon them by accident :D) Debating between arch, gentoo, and slitaz - i got all the iso's and stashed them on the file server last night.

Now, to the replying :shock:.
> **Sublime Porte said:**
> You should be able to boot [Tinycore Linux](http://www.tinycorelinux.com) from floppy. The distro is all up 10mb, and has plugins, and is really snappy even on very low end systems. I use it on a 200mhz 128mb ram ebox (about the size of a CD case) and it's lightening fast.

It's actually made by some of the same people as DSL I believe.
Does it support things like xfce? I was able to get a gui running on a similar lappy box (p1 500 mhz processor, 80 mb ram, floppy drive, no network card).


> **mingtien said:**
> Some thoughts -- I've just downloaded Slitaz (see Distrowatch for details), and it looks quite slick, so if you do get a CD ROM, it might be a nice choice.  I am going to install it on a mate's machine that has a very basic config (although it does have a CD drive).

Failing that -- go for Slackware 1.1.1.2 -- here is a tar image that has all the floppies: 

[http://www.oldlinux.org/Linux.old/distributions/slackware/](http://www.oldlinux.org/Linux.old/distributions/slackware/)

You will need to make a lot of floppies, but so did everyone else back in the day!  

This will work fine with a 56k Modem; get a vintage version of fvwm, and a basic web browser (I honestly can't remember what I used back then...there wasn't much on the web really).

Let us know how you get on -- I love hearing about people making use of old iron :)

By the way: if anyone knows where I can get hold of OLD slackware iso images (pre 1996), I would greatly appreciate it!  (I want to play with it in Virtualbox, but really don't want to go subbing all those floppies!!!!).
I actually grabbed slitaz last night while hunting for lightweight distros, and may throw it onto the experiment (mwahahaha) laptop to test it out. I also grabbed the tarball you recomended - im on my windows machine now, ill check it out when i go over to linux. I don't care about making floppies - i have a bunch of radio shack gift cards :D.

I also personally love testing out old machines -  i have 3 pre 2000, and they run linux great. I boot into the old win 95 or 98 for the lulz occasionally. I have to get ethernet working on them though - im a little annoyed with that. (Of couse, i have to get cards for a few of them :)) I also can't help you with slackware isos, but i can help you with ubuntu iso's - ive got a 4.0(whatever) iso lying around somewhere.



> **sertse said:**
> BasicLinux, which was linked earlier in the thread and fits on a single floppy is entirely Slackware *4* compatible. No need for Slackware 1 yet ;)

DSL has a lot of drama, and development isn't as fast, it's death is overstated. :)

The big (small?) four are still DSL, Puppy, TinyCore and Slitaz..
I tried puppy out a while ago, but couldent figure out the package manger for the life of me. 

> **Ticketoride said:**
> The local Buy & Sells should be selling them for $ 5 if you also take away a Bag of Kitchen Trash.

Futzing with Floppies isn't worth anyone's Time.
Floppies rule. I have all my server config files backed up to a 3 1/2 inch disk. :)

---

### Post by Eisenwinter on 2009-04-27
I haven't tried it, but google up FD Linux

---

### Post by Ticketoride on 2009-04-27
> **rhcm123 said:**
> Floppies rule. I have all my server config files backed up to a 3 1/2 inch disk.
Maybe a Quarter of all the Floppies I got are still readable. Bad Security. If your Config. Files are important to you, burn them to bootable Disk if necessary.

---

### Post by zmjjmz on 2009-04-27
> **sertse said:**
> BasicLinux, which was linked earlier in the thread and fits on a single floppy is entirely Slackware *4* compatible. No need for Slackware 1 yet ;)

DSL has a lot of drama, and development isn't as fast, it's death is overstated. :)

The big (small?) four are still DSL, Puppy, TinyCore and Slitaz..

Two floppies actually.

---

### Post by rhcm123 on 2009-04-28
> **Ticketoride said:**
> Maybe a Quarter of all the Floppies I got are still readable. Bad Security. If your Config. Files are important to you, burn them to bootable Disk if necessary.

unless they've suffered physical damage (e.g. cracked case, damaged disk) they should be fine. I've only had two where a fdformat and mkfs round couldent fix. And i know it's bad secuirty, but who really wants to break into my closet and hijack a config-backup floppy :shock:

> **Eisenwinter said:**
> I haven't tried it, but google up FD Linux
FD stands for ?

> **zmjjmz said:**
> Two floppies actually.
I just bought 20 at radio shack (15$!!!!). I think i'll be ok :)

---

### Post by rhcm123 on 2009-04-29
Just bumping out of curiosity to see if there are any distros ive missed or if anybody knows an old FTP site with a bunch of these iso's lying around. I know this is possible - i remember booting windows from DOS (stick in one floppy, A://windows/system32/explorer.exe)

---

### Post by Mehall on 2009-04-29
I still say get debian on there, make sure you don't install the Desktop environment.

If, however, you can't deal with CLI only, then choose one of these more minimalist distros.

Installed Debian the other day, and I haven't takena anyhting out of the default yet, there's probably some I could cut.

It's using 737MB of HDD space, and that's having ADDED some things (ssh server and irssi to name but two.)

---

### Post by Mehall on 2009-04-29
EDIT: double pst

---

### Post by rhcm123 on 2009-05-03
Sorry to bump this, but i just wanted to post that i went with basic linux. It boots completely from one floppy, and the second floppy has all the add-ons - just what i wanted :)

---

### Post by Mehall on 2009-05-03
Glad you got what you needed :D

---

