---
title: "Help me decide"
date: 2015-04-29
forum: Ubuntu, Linux and OS Chat
---

### Post by Holden_Anderson on 2015-04-29
I have always used Windows, I have never been to happy with it , having a crash message about every half hour or so. I have gotten pretty fed up with it.  

I am building a PC, and I was sure that I was going to use Windows again, I didn't really know to much about Linux, after finding Ubuntu touch, I looked into the PC ubuntu os, just because I saw it on the website. 

I am now contemplating switching to Ubuntu, and I was hoping the great people of the forums could help me out. 

I don't know if what I will be doing is to resource heavy for Linux or something, I don't know. 

I was also worried that not all software I would like would be compatible with Linux. 

Here is what I will be using it for: 
-Photoshop
-Game Development (By this I mean I will be using a very heavy game engine, as well  as some other programs)
-Tinkering with lots of different hardware, such as the Raspberry Pi
-Heavy gaming

And my specs, in case their important

NVIDIA GeForce GT-730
AMD A8 7650K
MSI B75MA mATX Mobo

I do not know if any of this will help anyone, it's just in case someone can use that to help me

Thanks in advance for the replys
Holden

---

### Post by Bucky Ball on 2015-04-29
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Welcome. Photoshop will not work natively in Ubuntu. It is a Win/Mac program. You might be able to get it to work with Wine, depending on the version of Photoshop you have.

One thing to remember is Ubuntu is NOT a free, drop in replacement for Windows (or OSX for that matter). It will NOT run Win/Mac software natively and may or may not run it with some degree of coaxing. Therefore, you are better to find Linux alternatives for your software (Gimp is a replacement for Photoshop and runs in Win and Mac also if you want to try it out).

Game development is fine, if you're working on games for Linux. Unsure and not qualified to advise on how suitable it would be for Win/Mac game development.

Goes hand in hand with the RPi (I have one, and an Odroid, they ONLY run Linux, so it figures). You can use Putty to SSH directly in to the RPi. As for the ability to tinker with ALL external hardware, that will be largely down to the manufacturers/developers of the hardware and whether they (or someone else) supply open or closed source software or the device is intended to be Linux friendly at all. 

Heavy gaming? See answer one. If you are heavily gaming with Win/Mac games, then your results will be mixed. Again, Win software needs to be run using Wine. It may, or may not, work. Or some bits will work while others won't. See [here]("https://appdb.winehq.org/"). Look up the Win software you are wanting to run in Wine and check the ratings. Linux games, naturally, run very well in Linux! 

Bottom line: if you're wanting to use lots of Windows software, you have some choices: Use Wine to run them in Ubuntu (no guarantees on the efficacy of this); boot Windows as a virtual machine inside Ubuntu and run your Win software in that (although I've heard games and video can suffer with this approach); dual-boot with Ubuntu and Win; or, stick with Windows. Might be easier if you rely heavily on Win software in your day to day computing routine.

Good luck whichever way you go. Hope that has cleared some things up and any more questions, just ask. The main thing about Linux is that you are prepared for at least some degree of a learning curve if you are coming from a life of Win as you need to be prepared to make a slight change of mindset re. how you compute ... but in a good way. ;)

PS: You might be interested in having a read of [this]("http://linux.oneandoneis2.org/LNW.htm").

---

### Post by mattharris4 on 2015-04-29
Holden, the biggest problem I see is the Nvidia card.  Support for Nvidia cards is uneven in Linux at best.  However, there appears to be a driver for that card.  Here are a couple of links to read before attempting the Linux install.

[http://askubuntu.com/questions/524648/missing-ubuntu-drivers-for-gt-730-in-ubuntu-14-04](http://askubuntu.com/questions/524648/missing-ubuntu-drivers-for-gt-730-in-ubuntu-14-04)
[http://www.bleepingcomputer.com/forums/t/549534/nvidia-drivers-how-to-install-it-in-ubuntu-14041204/](http://www.bleepingcomputer.com/forums/t/549534/nvidia-drivers-how-to-install-it-in-ubuntu-14041204/)

This card is in some Ubuntu certified systems so evidently that particular Nvidia card should work OK.  Here is a link:  [http://www.ubuntu.com/certification/catalog/component/pci/10de%3A1290/](http://www.ubuntu.com/certification/catalog/component/pci/10de%3A1290/)

Some versions of the motherboard you cite actually come with a version of Linux pre-installed (although it is a distro I haven't heard of).  Therefore I expect with the usual disable Fast Boot and possibly Secure Boot I would expect it to work fine.  Link:  [http://www.msi.com/product/mb/B75MA-P45.html#hero-overview](http://www.msi.com/product/mb/B75MA-P45.html#hero-overview) 

Good luck and I hope all goes well with your Ubuntu install.

---

### Post by chris376 on 2015-04-29
As Bucky Ball said, as far as support for gaming, the amount of games that are actually supported on linux at the moment aren't anywhere near the number of windows. You could always try a dual boot if you fancy, especially handy when tinkering with Raspberry Pi's and the like. Also, perhaps try Ubuntu on a LiveCD before you go installing it, gives you a small chance to see if you like it or not. But do not expect the same compatibility as windows, not everything works on both, so read up about which games are supported etc. 

All that said, Ubuntu is great so why not give it a try ey? ;)
Good Luck!

---

### Post by Rob Sayer on 2015-04-29
I'm not a gamer, and if I was I'd still have a Windows partition.

---

### Post by mörgæs on 2015-04-29
If you begin developing games for Linux it would be most welcome.

---

### Post by garyed on 2015-04-29
I recently built a new system dual booting with Windows & Ubuntu. I'm into making music so i use windows for my DAW  & Ubuntu for everything else. The only negative to a dual booting system is paying the extra money for Windows if it didn't already come with the system.

---

### Post by Bucky Ball on 2015-04-29
> **garyed said:**
> I recently built a new system dual booting with Windows & Ubuntu. I'm into making music so i use windows for my DAW  & Ubuntu for everything else.

My desktop has been set up like that for about eight years for exactly the same reason. ;)

My laptop, my main squeeze, came with Win7. It's there somewhere. I never use it.

---

### Post by Mark Phelps on 2015-04-29
If your Windows OS is crashing frequently, you have a serious underlying problem, most likely hardware related, and that is NOT going to be fixed simply by switching over to Ubuntu.  As a first pass, you should create Ubuntu install media, boot from it, and see how well your PC behaves.  It will be slower, but if it continues to crash, then you have a serious hardware problem that needs to be fixed -- and for that, you should post on the appropriate Windows forum.

As to what you want do do, none of those items lend themselves particularly well to running Ubuntu.  As already mentioned, Photoshop works poorly in Wine.  Game development for native Linux games would work, but development for Windows games is going to be a serious problem -- as you will then need a native Windows environment in which to run and test the games. Heavy "Windows" gaming works poorly or not at all (depending on the game and version) in Linux, as not only are the Linux drivers often behind the times with respect to Windows drivers (especially if you use AMD video chipsets), there are also Windows runtime components that may be required that won't work in Linux.  As to hardware tinkering, that's a very mixed bag, as well.  Lots of enthusiasts tend to do their work in Linux, so you may be able to find the drivers you need -- but that will require lots of searching a digging to find them.  Hardware that comes with drivers on CD is wasting your time, as those are nearly always only Windows/Mac drivers.

Based on what you want do to, I would say you are already in the best environment to do that -- Windows.  You need to work seriously on fixing the Windows PC problems before jumping ship to switch over to Linux.

---

### Post by Holden_Anderson on 2015-04-30
Thanks for all the replys, I hate to go back to Windows, but I want everything to work as smooth as possible. Who knows, maybe I will find windows 8 alot more stable.

---

### Post by mörgæs on 2015-04-30
Why not try a dual boot?

---

### Post by Y^2om&amp;#7sgP on 2015-04-30
With regards to Photoshop not running...sortof

I've got Photoshop CS5 running on Ubuntu 12.04 LTS with the help of this

[http://www.makeuseof.com/tag/idiots-guide-installing-photoshop-cs5-ubuntu-1004/](http://www.makeuseof.com/tag/idiots-guide-installing-photoshop-cs5-ubuntu-1004/)

Works a treat :p

---

### Post by TheFadedBrit on 2015-04-30
If i was you id create a second hard drive partition and have windows on it and the other with linux as you never know when you will need either.
I mean I have 3 SSD Drives and one has Linux And the other has windows but the third is a backup drive for games and the likes so yeah.

Hope It Helps

Faded

---

### Post by sam-c on 2015-05-02
Try Peppermint a Cross Between Ubuntu Mint Very Secure Low Resources and works beside Windows, With Firefox Chromium 
I added Opera too,
Happy To Help
Uncle Sam

---

