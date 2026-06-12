---
title: "Win XP to Ubuntu success story- mostly."
date: 2015-04-28
forum: Ubuntu, Linux and OS Chat
---

### Post by PoorOldChap on 2015-04-28
I have an old IBM Thinkpad, which ran Win XP, and became very sluggish over the years. I could not even reinstall the OS. So, installed Ubuntu 64 bit, and after a couple of days getting used to it, I find it a good system. It was a spare computer, so I dId a full install, and dumped Windows from that machine. Luckily, it had 2 GB RAM, which the guy who sold me the computer originally said was far too much. You know, due to all the people who take computers back to the shop and complain because they have too much memory ;).

Then after using a specialist mapping program in Windows for 20 years, i decided to try to instal it via PlayOnLinux. There is no Linux equivalent that would cope with my 20 years of data. It seems to have finally installed, but there is a lot of (to me) confusing information about how to do such an installation. I just kept clicking buttons, and following whatever advice i found (not always the same advice, though). We will see how it works. 
I think Ubuntu is better for a young computer user who is not set in too many old Windows ways, or dependent on particular software. But as a second computer, for non-specialist stuff, great!

All in all, I am sorry i did not find Linux years ago- I will keep using Windows for work, but it's Ubuntu at home from now on. Next step- replace the creaky Win XP on the even creakier  old desktop computer with Ubuntu, and see how we go.

PoorOldChap

---

### Post by mörgæs on 2015-04-29
Congratulations.
For old computers there are better alternatives than Ubuntu. Please see the link in my signature for more info.

---

### Post by RobGoss on 2015-04-29
That's great I have 5 computers at home I use daily and all of them are running some form of Linux and it is now my primary os of choice. Yes there are lighter versions of Linux that work flawlessly  on older computers.

---

### Post by coffeecat on 2015-04-29
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Good luck with Ubuntu on the creaky desktop! If you have any problems with that or anything to do with running Ubuntu or an Ubuntu flavour, do please ask your questions. There are plenty of people here able and willing to help.

Welcome to the forum.

---

### Post by newb85 on 2015-04-29
> **PoorOldChap said:**
> 
All in all, I am sorry i did not find Linux years ago- I will keep using Windows for work, but it's Ubuntu at home from now on.
PoorOldChap

Just remember, Ubuntu has only been around for a decade, and when it was first released, it was nowhere near as easy to use as it is now.

Generally, Linux is only a good option for really specialized work if there is Linux software available that meets your requirements.

But for browsing the web, checking email, basic office suite operations, etc., it's great!

---

### Post by mattharris4 on 2015-04-29
> **PoorOldChap said:**
> I have an old IBM Thinkpad, which ran Win XP, and became very sluggish over the years. I could not even reinstall the OS. So, installed Ubuntu 64 bit, and after a couple of days getting used to it, I find it a good system. It was a spare computer, so I dId a full install, and dumped Windows from that machine. Luckily, it had 2 GB RAM, which the guy who sold me the computer originally said was far too much. You know, due to all the people who take computers back to the shop and complain because they have too much memory ;).

Then after using a specialist mapping program in Windows for 20 years, i decided to try to instal it via PlayOnLinux. There is no Linux equivalent that would cope with my 20 years of data. It seems to have finally installed, but there is a lot of (to me) confusing information about how to do such an installation. I just kept clicking buttons, and following whatever advice i found (not always the same advice, though). We will see how it works. 
I think Ubuntu is better for a young computer user who is not set in too many old Windows ways, or dependent on particular software. But as a second computer, for non-specialist stuff, great!

All in all, I am sorry i did not find Linux years ago- I will keep using Windows for work, but it's Ubuntu at home from now on. Next step- replace the creaky Win XP on the even creakier  old desktop computer with Ubuntu, and see how we go.

PoorOldChap

I didn't have any issue installing Ubuntu on my eight year old HP desktop (Pentium 4 3.0 GHz 32 bit) that ran XP before the install.  Both work as designed in a dual boot environment.  You simply select what OS you want to run in a screen that appears after turning the computer on (commonly called the GRUB screen in Linux).  Later on I did have to upgrade the 2GB RAM to 3.5GB after a couple of websites were redesigned and started needing more RAM to run (running off of swap is painful at best) but otherwise it still runs fine.  However, if you don't wish to install more RAM you may wish to try a lighter Canonical OS like Lubuntu.  I have that running on a laptop and even the biggest RAM hog sites with 7-8 tabs running only uses about 1.3GB of RAM and it is easier to run on low power processors.

In the future there is an easier way to install a Linux OS.  Install UNetBootin on a computer running Linux (it should be in the Ubuntu Software Center), then using a USB stick install whatever distro you want on it using UNetBootin.  The USB stick will be formatted automatically before the OS files transfer so make sure you don't need whatever is on that stick.  Then boot the USB stick (you probably already know you need to modify the boot order in the BIOS to boot a DVD or USB).  Next follow the prompts to either install or test (installation can be done from a test boot if you want to try out the OS first).  As long as the computer does not have a UEFI instead of a BIOS (which is mainly on computers that shipped with Win 8 or 8.1) either the install alongside other OS or install alone options work well, if you dual-boot with Windows a screen will come up where you adjust the size of each OS partition to whatever you need.  Be sure to defrag the hard drive in Windows before attempting a dual-boot install.  

Since the OP is a computer guy I will say that if you ever decide to install a Linux OS (whether it is a Canonical OS or not) on a computer that shipped with Win 8 or 8.1 do your research.  Some install fine after disabling Fast Boot and Secure Boot, some need some other steps taken and HP computers with Win 8 or 8.1 require modifying programming code and aren't in most cases worth even attempting a Linux install on (the newer cheap Stream 11 and 13 32 bit laptops from HP will not run and install Linux properly no matter what you do -- too bad since they are only $199, the newer 64 bit HPs are designed in the UEFI to only run Windows and need to be tricked into running Linux or GRUB by changing the name of some code in the Linux install and/or GRUB).  Win 8/8.1 Toshibas are all over the place regarding Linux installs (my one year old Toshiba took Lubuntu dual-boot without major issue after turning Fast Boot and Secure Boot off, it was just as easy as the old XP computer install), my research tells me that new Dells and Lenovos usually take a Linux install fine after disabling Fast Boot and Secure Boot (as far as Dell that is to be expected as they sell developer laptops with Ubuntu pre-installed but they cost $1300 compared to $299 for the cheapest Win 8.1 laptop from them).  Newer Sonys are another computer that you can forget installing Linux on, they also have a UEFI designed to foil Linux installs similar to HP's.  There are companies that sell computers with a Linux OS pre-installed, Linux City ([www.linucity.com](www.linucity.com)) is cheapest at $415 for a mid-line i3 with (IIRC) 4GB RAM, System76 ([www.system76.com](www.system76.com)) is more expensive at $659 for their cheapest but the computers are not anywhere near bottom of the line in RAM, HDD, etc.

---

### Post by Mark Phelps on 2015-04-29
> I think Ubuntu is better for a young computer user who is not set in too many old Windows ways, or dependent on particular software.

Your first part (age of the user) varies enormously by individuals.  We have regular posters on this form who retired years ago and have had no trouble learning how to do stuff in Linux.  The major hangup of folks coming over here from Windows is that they, all too often, expect to see a free version of Windows -- with all the same menus and selections.  When confrunted with a very different look and feel, the get frustrated and quit.  Willingness to learn new ways to do old things is a key part of a successful transition to Linux.

As to the latter (dependency on Windows apps), once again, this is a big stumbling block for some folks.  They think they can install Wine and reuse their common Windows apps (e.g., Internet Explorer and Microsoft Office), but discover that Wine is NOT the emulator they thought it was.  And then, they are faced with transition over to using a different browser and different office suite -- which again, proves too much for some folks.

One of the really BIG items about Linux is the flexibility of desktops!  I grew up in the home computer industry using windows that have the control buttons on the right -- and that's something I like to keep the same.  When Unity moved them to the left, for a while, there were hacks we could do to move them "back" to the right.  But then, Canonical changed Unity so those hacks didn't work -- so I switched over to using Linux Mint.  Now, there is Ubuntu 15.04 Mate -- which I am using primarily due to its similarity to the previous Ubuntu UI.

With Windows, you get two UIs -- Tiles and Desktop -- and while you can change aspects of the latter, there is nowhere near the flexibility that you have with Linux distros.

---

### Post by Bucky Ball on 2015-04-29
> **Mark Phelps said:**
> Willingness to learn new ways to do old things is a key part of a successful transition to Linux.

+1. My mother in law asked me to build her a Linux only box when she was in her late 60s. She'd used Windows for years. She is now 75, only uses Kubuntu/Xubuntu and now finds Windows illogical and befuddling. ;)

PS: Xubuntu would rock on that 2Gb machine, Lubuntu faster, but I prefer Xubuntu for its easy customisation (you may not, of course). Not sure about the creaky machine, but that may also not be so creaky with one of the previously mentioned flavours rather than attempting Ubuntu (which, even if it does install, may not be the greatest of computing experiences). Good luck.

---

### Post by monkeybrain20122 on 2015-04-29
> **newb85 said:**
> 
But for browsing the web, checking email, basic office suite operations, etc., it's great!

Well it can do a lot more than that. There are many levels of  intermediate use cases between browsing the web and checking email and "very specialised use" and very specialised use !=  using Windows software, it depends on what specialised use one has in mind. Linux is much better for scientific computation for example. Don't make it sound like a phone. :)

---

### Post by Bucky Ball on 2015-04-29
> **monkeybrain20122 said:**
> Well it can do a lot more than that. There are many levels of  intermediate use cases between browsing the web and checking email and "very specialised use" and very specialised use !=  using Windows software, it depends on what specialised use one has in mind. Linux is much better for scientific computation for example. Don't make it sound like a phone. :)

And a +1 to this, also. My machine functions as much more than a Ubuntu web and email box. I cracked through seven years at uni with it and am now back for another three. I used Ubuntu 95% of the time. Throw in Libreoffice and Zotero, Zim and Freeplane, and a few other bits and bobs, and you have the perfect research environment. 

Create presentations, mind maps, gannt charts, bibliographies, desktop wiki, fifty page + documents ... the list goes on. And that's just uni stuff, not mentioning my other shenanigans (creating web pages, basic audio recording/editing, Gimp, watching TV with a USB TV dongle, dual-monitor laptop and desktop, backup routines, downloading/uploading data to my web host using Filezilla, communicating with my Odroid and Raspberry Pi using Putty, running virtual machines ... blah blah ...). ;)

My box must be a versatile and stable workhorse. A breakdown would be a nightmare. This is another reason I use Ubuntu LTS releases, a minimal install with only what I want/need and little bloat. There are times my machine has been on for weeks on end without a peep of complaint.

---

### Post by yoshii on 2015-05-03
I went from Windows to Ubuntu Studio, to Lubuntu.  I had experimented with Puppy Linux and that's what sold me on Linux along with gParted.  Almost all of my main Windows XP programs work just fine in wine.  
I only use used computers, so it's all good to me.  Therefore, I can very much relate to the good feeling associated with Linux.

---

### Post by newb85 on 2015-05-03
Didn't mean to make it sound like a phone.  Honestly, I would bet most people don't use their PCs for much more than what I mentioned.  Documents and spreadsheets with calculations fall into the whole "office suite tasks" thing I mentioned.

And yes, there are many other things that can be done.  For specialized use, though, how effective Linux is depends on how good the Linux software for that use is.  If, for example, you're a professioal mechanical engineer, using Linux would depend on whether the tools and usability in packages like librecad or freecad suit your needs.

---

