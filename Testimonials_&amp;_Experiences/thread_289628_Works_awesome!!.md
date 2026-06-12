---
title: "Works awesome!!"
date: 2006-10-31
forum: Testimonials &amp; Experiences
---

### Post by Leogen on 2006-10-31
[FONT="Arial"]Well I decided to come back to the forums and give a big /cheers and /thankyou for the great distro.  I would also like to describe my installation experience and specs so others may benefit from it.
[B][U]
Distro: Ubuntu 6.06[/U][/B]

[Computer specs]
**Motherboard**: Asus P5LD2
**Ram**:         2 gig dual channel corsair
**CPU**:         3.4 Intel Pentium D 950 3.4 4MB Cache
**Video Card**:  Ati Radeon X1900 XT
**Hardrive**:    SATA 200g WD X2

**_[Complications]_**

**[Video]**
After install video was laggy.  Moving around windows was a little chunky.  Downloaded *ati-driver-installer-8.28.8* and did a default install.  Made sure I had a copy of my xorg.conf incase things screwed up.  Automatic install was smooth, so was *aticonfig --initial*.  

After restart things were very smooth and it auto set my default resolution to a nice widescreen *1680x1050*. 

**[CD BIN/ISO BURNING]**
Didn't know how to do it... yes I have a few things to learn but so far everything has been smooth.  Went to the add/remove proggies and searched for an assortment of burning software.  Came across K3b which has a very nice looking interface.  First attempt:  Burned  myself a coaster.. I had a cd with just the *.cue on it.  Realized there is a seperate spot in the program for CD image burning.  Burned the program no problem.  I am unsure why it wanted me to set speed of CD burning initially when it can auto detect it later..

**[Mounting]**
Added my other drives with /etc/fstab:
**# <file system> <mount point>   <type>  <options>   <dump>  <pass>**
**/dev/hdf1	/storage	ext3	defaults,user	0	0**

Now I needed to make a group so my wife and I could access the drive.  I went to the terminal and did *addgroup skelly*.  Then went into System> Admin> Users and Groups> 

I added my wife and myself into the skelly group.

The command I used to give my wife and myself access is:

*sudo chown root:skelly -R /storage*

I'm sure others may have other ways of doing it, but the method seemed to work fine for me.  

**[GCC]**
I am a university student and the course I am in requires me to do C++ programming.  GCC is very powerful and fast.  The class uses VS 2005 for windows which I find laggy.  An easy way to install GCC:

*sudo apt-get install build-essential*

**[QUESTION]**
This brings me into a question, I'd like to be able to cross compile and create a win32 *.exe because the prof. requires it.  


**_[MINOR PROBLEMS/SETBACKS]_**
[VIDEO]
--Full screen downloaded divx/ect movies are a laggy/choppy

**[ENCODED DVD]**
Followed the directions on the UBUNTU forums, still no luck.  All other dvd's work, might be a region error?  I don't watch dvd's often anyway..


**[WIRELESS CARD]**
I installed a new DLINK DWA-542 Rangebooster N Desktop Adapter.  There seems to be no linux support for it /cry.  I can direct connect with a wire but, I like the Wireless N technology.

**[WINE]**
I'd like to be able to run my CCTV Video surveillance software on the machine.  It is a small windows program.  Been getting allot of bugs/ect trying to make it work.  I suppose when I go to install world of warcraft I'll get my experience debugging wine.

For the people that don't know.  (Took me a while to figure this out) the wine folder is hidden.  You need to run wine for it to show up as well.
so
Run wine, then go to* /home/user/.wine *

**[CONCLUSION]**
The distro speeds by windows XP.  I haven't had to restart the machine since I've had everything working.  Does not lag up, the desktop usage is a breeze.  My wife really enjoys her user account and making it look "fancy"   with the emblems, borders and backgrounds.

I am amazed at how so much stuff worked out-of-the-box!  /Cheers again to you fellows, I am now a big UBUNTU fan.  I suppose now all i have to wait for is my laptop.  Sound is an issue, if I set ACPI=OFF on my toshiba satellite p100 there is sound but acpu off on a lappytop isn't so good.  Maybe on the new distro it will work.  I'll be waiting

[COLOR="Lime"]**Thanks**[/COLOR] again
Richard[/FONT]

---

### Post by Leogen on 2006-10-31
Oh yes forgot to mention.

Installing an OS while I am able to surf the net and play games is funny.  I enjoyed the Live CD Installation!!

---

### Post by Leogen on 2006-10-31
Followed the directions on these forums about wine with World of warcraft.  Did the install and loaded WoW to find everything was very choppy and could hardly move my mouse.  Realized that my direct 3d wasn't enabled so installed the fglrx".  After restart loaded WoW fullscreen and had amazing results.. now wish the servers were not down today so I can play.... /sigh

---

### Post by rax_m on 2006-11-06
Hi Richard, 

Which Toshiba did you install Ubuntu on? And does your CPU/GPU fans work ok? 

I just bought the Toshiba P100-429 this weekend. 
I repartitioned the drive (keeping WinXP) and installed Ubuntu. 

First time around, the install froze as it was setting the clock ( I think due to overheating). I then let it cool down and tried again, at which point it worked. 

However, when booting into Linux I definitely notice that the laptop is running hotter. 

A lot of ppl have said you need to set ACPI=off in grub. 
But it seems like you aren't doing this? 

Any extra info would be great. 

Cheers
Rax

PS Machine specs:
Toshiba P100-429
Dual Core 2 (1.66 GHz)
Nvidia Geforce Go 7600
SATA 100GB HDD
1.5 GB Memory

---

