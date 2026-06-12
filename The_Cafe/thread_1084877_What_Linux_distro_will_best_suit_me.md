---
title: "What Linux distro will best suit me?"
date: 2009-03-02
forum: The Cafe
---

### Post by gymophett on 2009-03-02
I'm trying to shuffle through distros and find the one best for me, yet Ubuntu is the only one that seems to install on my laptop. The other CD's always have an error! I have no idea why. OpenSUSE wouldn't install, Mandriva had many errors, Arch was way too expertish, and now I'm trying to install Fedora on my laptop but it has an error on has disc, and once it installs it says error 15 on the GRUB menu.

These are my computer specs:
Features/Specifications: 

    * Acer Aspire AS5315-2153 Celeron M 1.73 GHz 15.4-inch Widescreen Notebook 

    * General Features: 
    * Microsoft Windows Vista Home Basic pre-installed w/COA  
    * Intel Celeron M Processor 530 
    * 1.73 GHz CPU Speed 
    * 1 GB DDR2 RAM (2 GB maximum) 
    * 80 GB hard drive 
    * CD-RW/DVD drive 
    * Intel Graphics Media Accelerator X3100 
    * Integrated audio with built-in speakers 
    * 802.11b/g Wireless LAN 
    * 56K ITU V.92 modem 
    * 10/100 Fast Ethernet LAN 
    * 15.4-inch WXGA Acer CrystalBrite TFT LCD display w/1280 x 800 pixel resolution 
    * Keyboard with touchpad 

Okay, I want a simple, easy to use distro that just works, and needs to be very stable. I don't want one too heavy, I prefer GNOME, but thats not a necessary.. It needs to be pretty fast! I just want an all around great distro. I haven't tried Debian. Any thoughts?

---

### Post by Kingsley on 2009-03-02
Go back to Fedora, and fix the Error 15 isssue.

---

### Post by gymophett on 2009-03-02
> **Kingsley said:**
> Go back to Fedora, and fix the Error 15 isssue.

I don't know how! :[
I'm a little new to Linux.
Should I not be puttin i686 on the CD?

---

### Post by HermanAB on 2009-03-02
Always verify that the discs are good before trying to install.

$ md5sum /dev/cdrom

If the checksum fails, burn the new image at a slower rate.

Cheers,

Herman

---

### Post by mips on 2009-03-02
> **gymophett said:**
> 
I'm a little new to Linux.


Linux Mint

---

### Post by Twitch6000 on 2009-03-02
Well if you don't mind waiting... PClinuxOS2009 is almost Final and that is about as easy as it gets.

If you want something that uses .deb files though Linux Mint 6 is a great easy distro.

---

### Post by gymophett on 2009-03-02
> **mips said:**
> Linux Mint

Tried, wouldn't install right either :(

---

### Post by Simian Man on 2009-03-02
> **gymophett said:**
> I'm trying to install Fedora on my laptop but it has an error on has disc, and once it installs it says error 15 on the GRUB menu.


If the disc has an error on it, why did you go through with the install?  The Fedora installer runs a media check, if that failed then you should try reburning it.

I'd focus on getting one to work rather than trying a whole slew of them.  It could really be all the same problem, so once you figure it out, you'd have a lot of options.

---

### Post by mulligan.can on 2009-03-02
> **gymophett said:**
> I don't know how! :[
I'm a little new to Linux.
Should I not be puttin i686 on the CD?
Stick with ubuntu. Best for newbies imo. Also the repo's are huge and contain pretty much everything you could want.

Oh and ubuntu IS debian based so in a sense you have tried Debian.

Fedora takes a LOT more setting up/fooling around than ubuntu.

---

### Post by Simian Man on 2009-03-02
> **mulligan.can said:**
> Stick with ubuntu. Best for newbies imo. Also the repo's are huge and contain pretty much everything you could want.

Oh and ubuntu IS debian based so in a sense you have tried Debian.

Fedora takes a LOT more setting up/fooling around than ubuntu.

There is nothing wrong with experimenting.  I don't find that Fedora requires much more setup than Ubuntu.  Just add RPM Fusion, and you are good to go.

---

### Post by Vince4Amy on 2009-03-02
> Fedora takes a LOT more setting up/fooling around than ubuntu.

No it doesn't, there's also less bloat to remove!

---

### Post by gymophett on 2009-03-02
Burned Fedora on new CD. Fail! :(

---

### Post by Simian Man on 2009-03-02
> **gymophett said:**
> Burned Fedora on new CD. Fail! :(

Did you verify the ISO before burning?  To do so, run sha1sum on the iso file.  Then check that it matches the value in the SHA1SUM file distributed with the iso.

---

### Post by gymophett on 2009-03-02
> **Simian Man said:**
> Did you verify the ISO before burning?  To do so, run sha1sum on the iso file.  Then check that it matches the value in the SHA1SUM file distributed with the iso.

What do I run it with? I'm using Windows XP at the moment.

---

### Post by Simian Man on 2009-03-02
> **gymophett said:**
> What do I run it with? I'm using Windows XP at the moment.

[Here you go]("ftp://ftp.gnupg.org/gcrypt/binary/sha1sum.exe").  Did you download the iso from bit torrent or from http/ftp?  Because I believe that torrent programs will do their own checksums as they download.  Still wouldn't hurt to run sha1sum though.

---

### Post by inobe on 2009-03-02
simian' your avatar is hilarious lols


i would burn the iso with imgburn, it will verify the data on the fly

---

### Post by ArtF10 on 2009-03-02
> **gymophett said:**
> I'm trying to shuffle through distros and find the one best for me, yet Ubuntu is the only one that seems to install on my laptop. The other CD's always have an error! I have no idea why. OpenSUSE wouldn't install, Mandriva had many errors, Arch was way too expertish, and now I'm trying to install Fedora on my laptop but it has an error on has disc, and once it installs it says error 15 on the GRUB menu.

These are my computer specs:
Features/Specifications: 

    * Acer Aspire AS5315-2153 Celeron M 1.73 GHz 15.4-inch Widescreen Notebook 

    * General Features: 
    * Microsoft Windows Vista Home Basic pre-installed w/COA  
    * Intel Celeron M Processor 530 
    * 1.73 GHz CPU Speed 
    * 1 GB DDR2 RAM (2 GB maximum) 
    * 80 GB hard drive 
    * CD-RW/DVD drive 
    * Intel Graphics Media Accelerator X3100 
    * Integrated audio with built-in speakers 
    * 802.11b/g Wireless LAN 
    * 56K ITU V.92 modem 
    * 10/100 Fast Ethernet LAN 
    * 15.4-inch WXGA Acer CrystalBrite TFT LCD display w/1280 x 800 pixel resolution 
    * Keyboard with touchpad 

Okay, I want a simple, easy to use distro that just works, and needs to be very stable. I don't want one too heavy, I prefer GNOME, but thats not a necessary.. It needs to be pretty fast! I just want an all around great distro. I haven't tried Debian. Any thoughts?

Depending on your finances, you *may* want to upgrade to 2 GB RAM.

Start out with Ubuntu(Standard Gnome) and then learn how to do an Ubuntu minimal install(XFCE/Gnome on Ubuntu minimal).

---

### Post by gymophett on 2009-03-02
> **Simian Man said:**
> [Here you go]("ftp://ftp.gnupg.org/gcrypt/binary/sha1sum.exe").  Did you download the iso from bit torrent or from http/ftp?  Because I believe that torrent programs will do their own checksums as they download.  Still wouldn't hurt to run sha1sum though.

Downloaded through torrent. The sums seem to be fine.

---

### Post by gymophett on 2009-03-02
I bought some new CD-R's and am now buring the Fedora image to a CD using Imgburn.

---

### Post by gn2 on 2009-03-02
Ubuntu 8.04 would be my suggestion.

---

### Post by gymophett on 2009-03-02
I think I will go back with Ubuntu 8.04. it ran faster than 8.10 does. :]

---

### Post by ArtF10 on 2009-03-02
> **gymophett said:**
> I bought some new CD-R's and am now buring the Fedora image to a CD using Imgburn.

> **gymophett said:**
> I think I will go back with Ubuntu 8.04. it ran faster than 8.10 does. :]

Are you dual booting?  If NOT, can we assume that Ubuntu > Fedora, which is why you ditched Fedora?

---

### Post by gymophett on 2009-03-02
> **ArtF10 said:**
> Are you dual booting?  If NOT, can we assume that Ubuntu > Fedora, which is why you ditched Fedora?

Hmm. I don't know :P
I haven't even tried Fedora to know yet, its just that 8.10 was a bit buggy. =/
I am not dual booting, I'm kind of just screwing around right now. :P

---

### Post by gnomeuser on 2009-03-02
A friend of mine uses Fedora on a very similar Aspire One machine and seems very happy with it. If you experience problems please do go to bugzilla.redhat.com and file a bug so we might know you have problems - then we can fix it and help you have a pleasant computing experience.

---

### Post by gymophett on 2009-03-02
Pfft. Why did I even try to leave Ubuntu. It's amazing, I think the 8.10 image I burned last time was corrupted, because its running flawlessly now!

---

### Post by mulligan.can on 2009-03-03
> **Vince4Amy said:**
> No it doesn't, there's also less bloat to remove!
True? Its been a few years since I used it. Fedora used to be MASSIVE and a royal pain to set up.

---

### Post by gnomeuser on 2009-03-03
> **mulligan.can said:**
> True? Its been a few years since I used it. Fedora used to be MASSIVE and a royal pain to set up.

It is very nice, unlike in Ubuntu I can cleanly remove all of firefox and openoffice without losing my translations (it's apparently a feature not a bug).

Aside that, Fedora is much like any other modern distro, it just works. For legal reasons one has to go to rpmfusion.org and follow the instructions for codec support though.

---

### Post by RichardLinx on 2009-03-03
> **gnomeuser said:**
> It is very nice, unlike in Ubuntu I can cleanly remove all of firefox and openoffice without losing my translations (it's apparently a feature not a bug).

Aside that, Fedora is much like any other modern distro, it just works. For legal reasons one has to go to rpmfusion.org and follow the instructions for codec support though.

Looking forward to Fedora 11. I hear there are a lot of new developments being made there. I downloaded Fedora 10 through a torrent and mistakenly chose the x64 version.

---

### Post by Orlsend on 2009-03-03
> **gn2 said:**
> Ubuntu 8.04 would be my suggestion.

I would recomend that too.

Have tried WUBI? Its a windows installer that installs Ubuntu Inside Of Windows, Ive used Wubi for 1 year, because my computer its messed up badly (CD drive is defective and many other things)
With Wubi you cant go wrong because to get rid of its just like uninstalling  a game on windows. No partitions :D and you get the same exact experience.

You just need that ISO of Ubuntu (All versions are supported) I would recomend 8.04 or 8.10 and the wubi.exe file (its 1 MB) and you are ready to go!

---

### Post by inobe on 2009-03-03
wubi+1

i have worked on computers that would only boot a win-dos os.....

for the life of me' know matter what i tried' it was a meaningless effort !

for whatever reason that being the case' wubi will stick ubuntu in within minutes.

of course certain hardware setups should be considered prior to that, if it's a software raid or even via igp chipsets will either give you the grub 21 or a 2d desktop.

please' folks that read this' do your homework first and always have a cheap nvidia agp or pci-e card laying around .

---

### Post by rosencrantz on 2009-03-03
Maybe this is a stupid question, but which of the distros you tried out install from CD and which from DVD? Possibly your system just can't install from DVD and you might be more lucky with an Ubuntu-style installable live-CD (I know there is one for openSuSE at least, don't know about other distros).

Good luck

rosencrantz

---

### Post by gnomeuser on 2009-03-03
> **RichardLinx said:**
> Looking forward to Fedora 11. I hear there are a lot of new developments being made there. I downloaded Fedora 10 through a torrent and mistakenly chose the x64 version.

The Beta for F11 is coming out soon, there will be LiveCDs so you can get an early glimpse.

Here's a list of the feautures:
[https://fedoraproject.org/wiki/Releases/11/FeatureList](https://fedoraproject.org/wiki/Releases/11/FeatureList)

These are potential features which has not been reviewed by our technical commitee yet.
[https://fedoraproject.org/wiki/Category:FeatureReadyForFesco](https://fedoraproject.org/wiki/Category:FeatureReadyForFesco)
(of which I own one, yay)

---

