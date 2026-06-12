---
title: "Why do you dual-boot with Win XP?"
date: 2007-07-23
forum: The Cafe
---

### Post by babya on 2007-07-23
May sound like a strange question, but what are your reasons for dual-booting with any Linux distro and Windows XP*?  Why not just use XP then?

I'm asking because Linux is, unfortunately, not meeting my needs at this time and I have to go back to XP to do want I want.  Someone suggested I do a dual-boot, but then I was thinking "why bother? I can do everything and more with XP."  

So I'm asking this question because maybe there are some reasons I'm not seeing as to why it would be more beneficial for me to do a dual-boot.


(Edit)

I should have also asked, how does a dual-boot work in terms of swapping files? Is it like a network where you have to connect a certain way to do file swapping?

I'd feel safer surfing the net with Linux, but thought it might be a pain if I saved pics/videos/documents to my Linux partition and having to transfer them to my XP partition. If transferring files between the two partitions is a snap, then a dual-boot might be worthy for me to try.


(*or any non-Linux OS.)

---

### Post by asmoore82 on 2007-07-23
I don't.

Haven't used Windoze since 2001.

---

### Post by bodhi.zazen on 2007-07-23
Moved to the Cafe.

I have multiple OS on my box because I like to play.  None of them are windows.

OS are just tools, they have advantages and disadvantages, best choose the best tool for the task at hand. I suspect most folks dual boot Windows XP either for games or for software development.

---

### Post by candtalan on 2007-07-23
You may need to review your motives for trying linux. Dual boot is less convenient than single boot, obviously, but an abrupt change of OS is needlessly brutal, usually.

I helped an elderly friend with their PC - a new one, with XP. They were concerned about security but had a number of dos games and one financial application on windows.

I installed kubuntu as dual boot, with thunderbird for email in Kubuntu. They now use linux for all internet related things - web, email etc. XP is used for the legacy stuff. In theory it might be possible to use wine or another method, but the concept of dual boot is straightforward. 

When I myself moved to linux I used dual boot for a time, as a convenience for some familiarity and to get time to arrange linux-only apps for my needs.

I do not use windows now except  to demonstrate that dual boot works to sceptics.....
:-)

I chose to move to linux over a period. Open Office, Firefox, and thunderbird - all were used initially in windows and then on linux.

good luck

---

### Post by rax_m on 2007-07-23
I have XP on a partition but haven't actully booted into it in over 3 months.. when I do it's normally just to "patch" it with the latest fixes, anti-virus etc. Not sure why I bother. 
The reason it's there is because this is my first "fully-fledged" leap into using Linux full-time. And with university, you never know when you might need some software that might be windows only.. 

But on my next upgrade of Ubuntu, I'm going to be reducing the size of the XP partition to something small like 15GB.

---

### Post by m10sang10 on 2007-07-23
Because smart people do things step by step, thus avoiding unnecessary risks and getting their objectives by the best method possible. In other words, they do not damage their fun nor games until the learning curve in relation to Linux is complete. And then they get to banish XP out of their lives. But from the moment you question that, I have doubts that you'll understand the spirit of the answer.

---

### Post by phrostbyte on 2007-07-23
Because my computer isn't powerful enough to virtualize  it. :-({|=

---

### Post by babya on 2007-07-23
I should have also asked, how does a dual-boot work in terms of swapping files?  Is it like a network where you have to connect a certain way to do file swapping?

I'd feel safer surfing the net with Linux, but thought it might be a pain if I saved pics/videos/documents to my Linux partition and having to transfer them to my XP partition.  If transferring files between the two partitions is a snap, then a dual-boot might be worthy for me to try.

---

### Post by walkerk on 2007-07-23
i don't dual boot.. my os is ubuntu 7.04 and i use vbox to run: fedora7, opensuse10.3a6, pclinuxos07, and xp

just to mess around..

---

### Post by lisati on 2007-07-23
Apart from possible warranty and recovery issues (my desktop came with a recovery partition instead of XP or recovery disks) and familiarity some of the people I work with use XP and some of the software I've purchased works better in a "native" windows environment. Although there are probably ways around it (haven't had the patience to check out stuff like ndiswrapper yet) some of the extra hardware I've got only came with windows drivers

---

### Post by rillip on 2007-07-23
For myself, I don't like working in XP.  I can, and do at work every day, but for my own projects, I feel like Ubuntu fits my style more.  I play games in XP because they work better.  That's it.  Everything else I do from Linux, and if I could get my games to play in Linux as well as I can in Windows, I'd just use Linux.  But that's the gaming industry's fault, not Linux's.

Windows is my neccessary evil; I leave it around because I need it, but hard drive space isn't so precious that I must only have what I need.

---

### Post by phrostbyte on 2007-07-23
> **babya said:**
> I should have also asked, how does a dual-boot work in terms of swapping files?  Is it like a network where you have to connect a certain way to do file swapping?

I'd feel safer surfing the net with Linux, but thought it might be a pain if I saved pics/videos/documents to my Linux partition and having to transfer them to my XP partition.  If transferring files between the two partitions is a snap, then a dual-boot might be worthy for me to try.

apt-get install ntfs-3g ntfs-config

It will let you read and write to Windows partitions

Then what I do is symlink my "Documents" folder to my /home/jonathan folder in Linux, so all my docs are visible and writable from Linux, alongside my regular Linux stuff :guitar:

On Windows you can get the ext2-driver which can mount ext3 to read your Linux stuff. It's quite useful, but Windows doesn't support symlinks so it shows up as a drive letter :mad:

Pretty much great support to share files between the OSes

---

### Post by rillip on 2007-07-23
> **babya said:**
> I should have also asked, how does a dual-boot work in terms of swapping files?  Is it like a network where you have to connect a certain way to do file swapping?

I'd feel safer surfing the net with Linux, but thought it might be a pain if I saved pics/videos/documents to my Linux partition and having to transfer them to my XP partition.  If transferring files between the two partitions is a snap, then a dual-boot might be worthy for me to try.

It depends on how you set up your dual boot.  If you're looking to share files easily, then set up a partition as Fat32.  Both can read this natively and you can move files just as you'd expect.  Linux and Windows can both be set to read the other's FS, but it's more of a pain then a Fat 32 partition.  Better in the long run as both OS's will have access to everything, but more trouble than what it's worth for some people.

---

### Post by phrostbyte on 2007-07-23
> **rillip said:**
> It depends on how you set up your dual boot.  If you're looking to share files easily, then set up a partition as Fat32.  Both can read this natively and you can move files just as you'd expect.  Linux and Windows can both be set to read the other's FS, but it's more of a pain then a Fat 32 partition.  Better in the long run as both OS's will have access to everything, but more trouble than what it's worth for some people.

No it's actually quite simple (takes about 1 minute) and ironically probably safer to use NTFS in Linux then Fat32 (which has much more mature support) simply because of journaling!

YOu can also do it vise-versa, access Linux from Windows, although the support isn't as good as the other way around. I do it both ways, it's really good experience imo.

---

### Post by Depressed Man on 2007-07-23
Why do I dual boot? To play the games I still play (that Wine or Cedega can't work with yet).

I have a similar problem (well most of my files are in NTFS not ext3) since I don't feel like redoing my media drive partition. I use ntfs-3g to take care of that. Any files I save off the internet are saved into the NTFS drive.

---

### Post by babya on 2007-07-23
> **phrostbyte said:**
> apt-get install ntfs-3g ntfs-config

It will let you read and write to Windows partitions

Then what I do is symlink my "Documents" folder to my /home/jonathan folder in Linux, so all my docs are visible and writable from Linux. :guitar:

On Windows you can get the ext2-driver which can mount ext3 to read your Linux stuff. It's quite useful, but Windows doesn't support symlinks so it shows up as a drive letter :mad:

Pretty much great support to share files between the OSes
Ok that all sounds complicated to this noob, but when it's all setup like you mention, is it convenient to swap files?

My thinking is that I'll be surfing the net with Linux, save pics/videos/whatever, and transfer them to windows to edit with windows video editors (which is one of the main reasons for keeping XP as I saw others here are mentioning too).  My concern is that while in Windows, I won't easily able to grab pic/videos I forgot to transfer over while booted in Linux.  If grabbing a file from the Linux partition will booted in Windows is a piece of cake, then dual-booting might work for me.

---

### Post by phrostbyte on 2007-07-23
> **babya said:**
> Ok that all sounds complicated to this noob, but when it's all setup like you mention, is it convenient to swap files?

My thinking is that I'll be surfing the net with Linux, save pics/videos/whatever, and transfer them to windows to edit with windows video editors (which is one of the main reasons for keeping XP as I saw others here are mentioning too).  My concern is that while in Windows, I won't be able to find pic/videos I forgot to transfer over while booted in Linux.  If grabbing a file from the Linux partition will booted in Windows is a piece of cake, then dual-booting might work for me.

The best way is to install the NTFS driver in Linux and save onto NTFS, as I said Linux has much better support for NTFS then Windows has for ext3 (major Linux filesystem). 

All you got to do is install the packages "ntfs-3g" and "ntfs-config"

Use apt-get to do this. If you don't know how I suggest you do some reading because without knowing how to use apt-get is like not knowing how to use the Start Menu in Windows.

Then you go into Applications -> System Tools -> and follow the the directions. It involves clicking one checkbox and your set.

---

### Post by ryanVickers on 2007-07-23
My reasons used to be strange, arguable, and plentiful, but now, I only occasionally use windows for games, thats it!  I've switched to linux for everything else finally when 7.04 came out. hooray!

---

### Post by Depressed Man on 2007-07-23
I personally don't like using a driver (well software) in Windows to write to Linux drivers. Mainly because if WIndows doesn't shut down cleanly then Linux has to do a system check on the drive when it boots up. At least that's happened to me enough times (grr.. stupid Windows' Dr. Watson). 

But yeah, you can do what I do. Just save the files onto the NTFS drive. That way Windows can access it (because it's NTFS) and Linux can still use it (with the ntfs-3g software). 

Symlinking just makes it easier to track file changes across different points in hard drives (s). You don't need it if you do what I do.

---

### Post by babya on 2007-07-23
> **phrostbyte said:**
> The best way is to install the NTFS driver in Linux and save onto NTFS, as I said Linux has much better support for NTFS then Windows has for ext3 (major Linux filesystem). 

All you got to do is install the packages "ntfs-3g" and "ntfs-config"

Use apt-get to do this. If you don't know how I suggest you do some reading because without knowing how to use apt-get is like not knowing how to use the Start Menu in Windows.

Then you go into Applications -> System Tools -> and follow the the directions. It involves clicking one checkbox and your set.
So if I'm booted in Windows and I want to grab a file in my Linux partition, it's just as easy as going to a shared folder and transferring it over?

Sorry for my noob questions.  I just want to be triple sure before diving into the murky water.

---

### Post by crimesaucer on 2007-07-23
My iRiver T30 device will not load songs in the correct order using usb on xubuntu.


I looked into ways to fix this but have found nothing.


I also have Daemon Tools to play kvcd movies...and I have never been able to get VLC working properly on my xubuntu...where as Xine-ui works beautifully.


Plus, I have my uTorrent set perfectly in Windows using a TCPIP.sys file patch and a TCP/IP Optimizer and can download torrents at unbelievable speeds...but I am looking to start using Deluge as soon as I figure out how to make it as fast...


...And my last reason is that I like to have a back up OS if in case I run into problems with wifi (I have it configured and working with wifi-radar, but I haven't been to a coffee shop or hot spot to try it out yet, so I don't know if everything works perfectly)....and I like to have a dual boot of Xp, just in case I break my xubuntu with something that I can't fix, then I can boot into Windows Xp (I only own a lap top), and get onto the Ubuntu Forums for help.


Eventually I would like to use Gparted and decrease the size of my Windows partition and only use my Windows for my iRiver device...or maybe even get a new music device that plays flac files and not use my Xp for anything other then a back up OS with nothing on it but Firefox.


(p.s. I also like to have the Firefox 3 alpha6 on that partition just to see how it is with out using it on my everyday xubuntu)

---

### Post by sonofusion82 on 2007-07-23
> **rax_m said:**
> I have XP on a partition but haven't actully booted into it in over 3 months.. when I do it's normally just to "patch" it with the latest fixes, anti-virus etc. Not sure why I bother. 

yes, me too. i still keep an XP partition mainly for legacy stuffs that don't work in linux and to ease migration.

as i venture deeper and deeper in FOSS, i find my self less dependent on Windows softwares as i discover more FOSS alternatives.  it can be several months i don't boot into windows. and when i do boot to windows to do things, my feeling linux superiority gets stronger when i see all those antivirus, anti-spyware softwares popping up for updates and slow boot-up time that really puts me off.

---

### Post by whayong on 2007-07-23
I do most of my computing these days in Ubuntu.  I still need Windows for those times that Ubuntu is not compatible with certain apps (i.e. netfilx online movie viewing) and ofcourse for games.  I also keep it because Linux is a little unfriendly to me as a previous Windows user.  I look forward to the day when I'll be M$ free.

---

### Post by eljoeb on 2007-07-23
Games, work, and Eve online (Ought to be a game, but I can't treat it that way!)

My Flash drives don't work in Ubuntu for some ungodly reason.

Why the !@$#!%#!%@^%#@ isn't my microphone working?

Joystick won't function, even though appropriate game does. 

Open Office keeps trying to restore files that don't need it.  

Keyboard randomly stops working.  Especially in AbiWord.

And Ubuntu is still not doing laundry or making toast.  I messed with the idea of using my power source (much bigger than needed) to run a toaster.  That would have been cool.)  Right now, there's so little on my Windows XP boot that it actually runs quite well (In some ways, better than Ubuntu).  Creepy.  The Windows XP was pretty smooth, too.  No finnadling with the Ubuntu NVIDIA drivers, and all I had to do was put a CD in and install.  It was swell.

---

### Post by thisllub on 2007-07-23
> **crimesaucer said:**
> My iRiver T30 device will not load songs in the correct order using usb on xubuntu.


I looked into ways to fix this but have found nothing.


I also have Daemon Tools to play kvcd movies...and I have never been able to get VLC working properly on my xubuntu...where as Xine-ui works beautifully.


Plus, I have my uTorrent set perfectly in Windows using a TCPIP.sys file patch and a TCP/IP Optimizer and can download torrents at unbelievable speeds...but I am looking to start using Deluge as soon as I figure out how to make it as fast...


...And my last reason is that I like to have a back up OS if in case I run into problems with wifi (I have it configured and working with wifi-radar, but I haven't been to a coffee shop or hot spot to try it out yet, so I don't know if everything works perfectly)....and I like to have a dual boot of Xp, just in case I break my xubuntu with something that I can't fix, then I can boot into Windows Xp (I only own a lap top), and get onto the Ubuntu Forums for help.


Eventually I would like to use Gparted and decrease the size of my Windows partition and only use my Windows for my iRiver device...or maybe even get a new music device that plays flac files and not use my Xp for anything other then a back up OS with nothing on it but Firefox.


(p.s. I also like to have the Firefox 3 alpha6 on that partition just to see how it is with out using it on my everyday xubuntu)

The Iriver software works inside a VM.

I have audio applications and plugins that don't work with Linux.
When Ardour can replace them all or a VM is good enough I will never dual boot.

---

### Post by forrestcupp on 2007-07-23
XP is for games only.

I use Linux for everything else.  Why don't I just use XP only?  Because I like Linux better.  But it's just not as good for Windows games.  Go figure.

---

### Post by macogw on 2007-07-23
I don't.  I don't need Windows for anything that I care about (I have a digital keychain that I can't use in Linux, but *shrug* I don't care that much except insofar as it gives me an excuse to attempt to write a driver....not like I ever actually used the thing to begin with, got it after I switched and I'm not adding a Windows partition just for that...or a Windows VM or Wine [not that it works with Wine]...I'm staying as MS-free as I can).

To share files, just make a partition to hold your junk.  If it's FAT32, both can access it easily, but the max file size is 4GB.  If it's ext3 you have to install a driver in Windows.  For NTFS, you need a driver for Ubuntu.  It'll just show as E:\ on Windows probably and /media/disk on Ubuntu.

---

### Post by metallicamaster3 on 2007-07-24
I use Windows because of iTunes and dual montiors. yes, i know. but today I am getting a new nVidia card, so that I can use TwinView instead of Xinerama, so that Beryl and Dualies work nicely ^_^

---

### Post by BigSilly on 2007-07-24
Why do I dual-boot XP with Ubuntu? 

That's a bloody good question! 

It's hard to think of genuine reasons these days. I suppose I'm keeping it around because my stupid printer is a Lexmark and will only work on Windows. I suppose I also keep it around because of 2 or 3 games I occasionally play on Windows. 

Really these are stupid reasons to keep it around now, since I only really use Ubuntu now. The games constantly crash and send me potty, and the Lexmark is a piss-poor printer. As soon as the new Ubuntu comes out, I'm dual booting two Linux distros instead. I think Ubuntu as the main OS, and PCLOS on the other partition. 

Windows has caused me more stress than any Linux distro I've ever used. Soon, it'll be gone!

---

### Post by use a name on 2007-07-24
> **babya said:**
> May sound like a strange question, but what are your reasons for dual-booting with any Linux distro and Windows XP*?  Why not just use XP then?

I'm asking because Linux is, unfortunately, not meeting my needs at this time and I have to go back to XP to do want I want.  Someone suggested I do a dual-boot, but then I was thinking "why bother? I can do everything and more with XP."  

So I'm asking this question because maybe there are some reasons I'm not seeing as to why it would be more beneficial for me to do a dual-boot.

My *main* OS is Ubuntu. I've still got XP installed to test if ports for software I write for linux come out as intended... So, that's basically the other way around. I do not have a *big* reason to dual boot either, but since I have enough diskspace, I don't care having that other OS around.

Sidenote: linux is growing real fast. I've seen quite a few of my own devices that did not work getting supported in only some eight months. I can imagine that certain software may keep you tied to windows though, but wine is being worked on as well. You may want to check back later to see if linux meets your needs then.

---

### Post by arkiedan on 2007-07-24
I've been running a triple boot grub with Ubuntu Studio, PCLos and Windows xp. I can't decide between Ubuntu and PCLos yet. They're both great and the difference between Gnome and KDE is insignificant to me.

I'd have left windows behind by now except I can't do without a couple applications such as Legacy and FTW, both genealogy software. Sadly, they won't run under Wine and the only gen program for Linux is Gramps, which is not even close. 

Sadly, I just realized I'm sitting here writing this in Windows xp, rather than Linux, because I was doing some genealogy work a minute ago. Dang! I gotta boot over to Linux right now!

arkiedan

---

### Post by AndyCooll on 2007-07-24
I haven['t dual-booted for a couple of years. I originally used to in order to play my Football Manager game. I then transferred that to an XP VMware image. However I've now got the game running under Wine so even the image is now gathering dust!

:cool:

---

