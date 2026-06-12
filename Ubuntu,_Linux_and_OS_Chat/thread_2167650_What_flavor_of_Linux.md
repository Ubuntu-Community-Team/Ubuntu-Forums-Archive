---
title: "What flavor of Linux?"
date: 2013-08-14
forum: Ubuntu, Linux and OS Chat
---

### Post by jason13 on 2013-08-14
I have a new laptop computer on the way. I am going to start teaching myself programming (and eventually go to grad school). I am going to set it up as a dual boot machine Win8/*Linux. What flavor of Linux would support my new needs? I'm still not excellent with CL in ubuntu but I'd like to learn more. My priorities are usability and stability, I don't want to be changing things around too much, a distro that come with or can be changed to GNOME would be preferable.

---

### Post by SweetAurora on 2013-08-14
For stability in the Ubuntu Camp, version 12.04 will suffice. it will get 5 years of support so no need to constantly upgrade to the next release or anything and it is fairly stable. As for the Ubuntu desktops, XFCE (Xubuntu) has a gnome-like interface so Xubuntu 12.04 would be good.

As for other Linux Distros, For stability and a good Gnome experience, try Debian. It is rock solid and stable and is supported for very long periods of time. Be aware it could take some time to setup as it takes a bit of know-how to get everything running and installed. Other good, but not as stable, but still usable distros you could use are Fedora, OpenSuSE, and Mangeia. All of which have Gnome Support but take more setup to use, like Debian does.

---

### Post by sudodus on 2013-08-14
I would suggest Ubuntu 12.04.2 LTS 64-bit. It is a long time support version and it is more stable and polished than the newest versions. It is also possible to select a gnome shell desktop environment instead of the default Unity. (Unity uses gnome).

---

### Post by jason13 on 2013-08-14
I was just chatting with a rep from Lenovo and said the computer doesn't support 64 bit software. but I'm not sure I believe them. it comes with a corei7 4700MQ. none of the specs on the chip I've found state one way or the other.

---

### Post by mastablasta on 2013-08-14
that a CPU that supports 64 bit OS. in fact i think all dual cores support 64 bit and also some old single core CPU.

i hope you made sure the laptop is compaitble with ubuntu. you will probably need to read about UEFI and secure boot (especially if it comes windows 8 preloaded).

Ubuntu uses Gnome. but witha unity shell. i am not sure what you want. if oyu want old Gnome 2 then it's better to use Xubuntu.

then again i don't know what is wrong with KDE. I eman for someone that likes to learn stuff and fiddle arroudn with things. Gnome is known for hiding features to users, so it's easier to use it. It doesn't overwhelm the user with options. and i believe it did a good job with gnome2 in that. i am not sure hwo well Unity or Gnome shell are doing in this respect sice i haven't sued themin a while. but i am sure they are doing well since they seem easy to use from what i read about them.

 besides there is so many windows managers and desktops to choose from...

---

### Post by Boab1993 on 2013-08-14
There alot of distos, it all depends on your hardware and what you want.

If i was going to go for stability and usability, i'd agreed with sudodus Ubuntu 12.04LTS is your best bet. I personally like the Unity desktop, if its not your thing, my personal Gnome favourite is Xubuntu, very clean and comfortable.

A bit of friendly advice, go out to a dollar/pound shop and buy a rack of CD-Rs, burn some live CD's of favourite candiates and test them out on the CD.

However since your doing dual-boot along side windows 8 id look into this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Ubuntu has problems booting with UEFI, luckily all of have been addressed and can be avoided/fixed with a bit of reading.

Hope you enjoy.

---

### Post by jason13 on 2013-08-14
I read through the Wikipedia article on UEFI and it doesn't raise any red flags in my mind. I was unaware that there were significant changes to boot processes. I'll burn that bridge when I come to it. Does 12.04 still work with WUBI and Win8?

---

### Post by Boab1993 on 2013-08-14
As far as i know Wubi is being phased out, or well so ive heard on other threads.

The Wubi download says 'please install..directly to its own partition' - my assumption is, it is possible, just not advised.
[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

Im sure someone else can shed some more light on the subject, ive never used Wubi so don't know the in's and out's.

Happy hunting.

---

### Post by sudodus on 2013-08-14
> **jason13 said:**
> Does 12.04 still work with WUBI and Win8?

12.04 and wubi work with Windows 7 and previous versions, but the newest versions of Ubuntu have given up wubi, because it was not possible to make wubi work with UEFI and Windows 8.

You need the 64-bit version for UEFI. Please read what you can find about it before trying to install a dual boot system, you can start with this link

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Artemis3 on 2013-08-14
> **Boab1993 said:**
> A bit of friendly advice, go out to a dollar/pound shop and buy a rack of CD-Rs, burn some live CD's of favourite candiates and test them out on the CD.

Don't do this, it is wasteful and slow/frustrating. Instead, get a couple of 1gb+ thumbdrives, iso images can quickly be put in those these days, and at the end of the day, you can still re-use the thumbdrives later for data moving instead of producing a rack of coasters you won't use again.


I would recommend one of the Ubuntu derivatives, ie. Zorin to ease transition from windows or Linux Mint (Cinnamon). If you want the classic gnome experience, get one with Mate; if you want the new tablet like thing, ubuntu gnome i believe. Lubuntu and Xubuntu are good choices too, just try them for a while, most can run off the iso without installing and decide yourself.

Ubuntu (Desktop) itself is rapidly detaching from the community, not only with Unity, now with Mir, becoming an island; with canonical alone to push it, it will lag behind other desktops soon. But the core (minimal) and repositories (with ppas) are still good (for things like Steam), so a derivative that avoids unity is still good to use.

---

### Post by craig10x on 2013-08-14
If it's a new computer, it certainly has to be 64 bit!  In fact, 64 bit has been pretty much the standard over the past bunch of years...
I'd try the main version of Ubuntu first, if you don't mind the Unity desktop it has...which is kind of like a "mac-like" dock on the left side of the screen which you can auto-hide....

If you must have something that somehow resembles windows, then probably xubuntu or kubuntu would be a better bet, but why not try something a bit different first?  
It may take a week or two to get use to it, but you may find you like ubuntu with unity...so why not give it a shot?

You can run these live first when you boot up the dvd to take a look at play with them a bit, and also helps you to get some idea of how they will run on your system....but remember, a live session will not be quite as fast as an installed one...

---

### Post by jason13 on 2013-08-14
Thanks, I've got Debian and Xubuntu downloading now, I already have an image for ubuntu 12.04. I've used Fedora, Knoppix and OpenSuse in the past. What kind of knowledge is necessary to install and use Slackware? (something I've wanted to try)

---

### Post by jason13 on 2013-08-15
Assuming Win8 will already be installed to the entire drive (laptop has a SSD for OS + HDD) would it be better to format, partition with the linux partitioner and then reinstall windows or the other way around? I've done it both ways it the past and I feel good about partitioning with the ubuntu setup disk. I don't know how UEFI will work in one case or the other.

---

### Post by sudodus on 2013-08-15
If you are able to reinstall Windows, and the computer can run without UEFI, it will make things much easier :-)

I prefer the following sequence

1. Make partitions and file systems
2. Install Windows (if you need it)
3. Install Ubuntu with 'Something else' at the partitioning screen

---

### Post by jason13 on 2013-08-15
I've been playing around with different live disks. and while I find Unity different, I kind of like it. I also like Xubuntu because of it's similar look, 12.04 looks to be a big step forward from 10.04. I noticed it has a backup application, I'm trying to switch my desktop currently too. I have two 3.0 TB drives for my desktop, would the backup application work in my favor? Are there other programs that are better options?

---

### Post by sudodus on 2013-08-16
There are lots of threads at the Ubuntu Forums about backup. I suggest that you browse for ***ubuntu backup*** or ***linux backup*** and read about the experience of other people, and then you can start a new thread about backup.

A new good descriptive title will attract persons interested in that new field, so you will get better help than switching subject in this thread, (but keeping the title).

Anyway, first you must decide what kind of backup you want: what, how much, how often, how automatic, to where ...

---

### Post by mastablasta on 2013-08-16
redo backup or clonezilla for full disk/partition  image backup

mintbackuptool (available via PPA) for backing up settings/programmes and home data separatelly.

i suggets a full disk/partition image backup. it will take compressed space on another disk. so let's say you have parittion that is 100 Gb big but has 20 GB occupied image will be about 20-22GB big.

---

### Post by jason13 on 2013-08-16
I don't really need to compress what I'm backing up. An application or script that does a scheduled rolling backup of my /home folder is all I really need.

---

### Post by sudodus on 2013-08-16
***rsync*** is a good tool. It has a simple command line interface (terminal window commands), and it is really flexible and powerful. See the manual page ```
man rsync
``` which is good.

There are graphical user interfaces with rsync as the engine under the hood, and there are also several other good tools. Browse the internet for more details. You can start at this page

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by mamamia88 on 2013-08-18
I would just use dropbox for small stuff and occassionally just copy large stuff to an external harddrive.  That way it shows up on everything you own as well.

---

### Post by kevdog on 2013-08-18
What's the purpose of your backup -- a one time thing used intermittently, backup only /home, full backup of everything?? -- do you need the backups encrypted?? -- how often do you want to back up?? -- do you need to often access the backups or mount them as a file system?  what medium are you backup up to?  A lot of questions to ponder since there are about 20 different backup solutions I can think of.

As far as distros go, if you've never tried Unix before or have little cmd line knowledge, I'd definitely stick with an Ubuntu derivative -- they are pretty idiot proof except for the UEFI part where you are going to have to do some reading.  Advanced distros such as Slackware, Arch, etc. take a lot more TLC.  They are incredibly quick, but at least with Arch, since its running bleeding edge packages, things often break and need fixing -- which just consumes a lot of time.  It's not hard to fix things that break, its just a lot of reading, posting and then trying about 5 minutes of commands to solve the problem.  Supposedly Slackware should be more stable, however Slackware has its own methods of doing things as well, and I believe it supports KDE by default.  

Debian is rock solid and great for servers, however if you're going to be learning things and using the machine as your daily driver, your going to be missing out on new packages and such.  

I recently gave up on Gnome and switched to KDE.  KDE years ago IMO sucked, however the new plasmoid desktop is really cool and it seems rather fast.  It also gives some eyecandy such as the rotating cube and window transition animations, which although technically their ridiculous, I've learned to like them a lot.

---

