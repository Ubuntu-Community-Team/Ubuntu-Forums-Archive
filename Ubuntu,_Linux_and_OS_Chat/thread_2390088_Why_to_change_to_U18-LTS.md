---
title: "Why to change to U18-LTS?"
date: 2018-04-25
forum: Ubuntu, Linux and OS Chat
---

### Post by cesarcosta.br on 2018-04-25
I'm using U16.04-LTS and happy about.
Today i woke up thinking why to change to U18-LTS, whats the really new  to change, most of the people talks about only fools things like the  face's desktops, appearence and blablablabla.... AH! The KDE to GNOME...  BUT KDE WORKS FINE, GNOME WORKS FINE... I DONT THINK THIS CHANGE WAS  TECHNICAL, BUT A BUSINESS/ECONOMICAL STRATEGY... Well, who knows... Lets  see... Nothing talks about an important changes like the performance  (faster or heavy), the stability, whats the new facilities to end-users  (like to conect a network without any terminal command... really not any  command...) it will be a finally front-end version?
Do you remember hows difficult was to you migrate MSWIN to LINUX?
To install a digital certificated reader was a battle... and i won using  the terminal. But, why am i still using the MSWIN in my notebook with  U16.04-LTS? in case i do not win the battle...
Im not telling to abandon the terminal, but we have to direct the UBUNTU  to end-users. Where is the old MSDOS in W10, a few people knows. I know  where is and how to work with him. But its not important to end-user.  How many people need to use the terminal in yours work, house, business  travel and etc...? With the LINUX system and yours versions or  distributions, ALL needs in sometime... The end-user, when he believes  that its really easy to use the LINUX systems, naturally will change and  in your job will do the same... and i thing that is the key to grow up  like operational system and open source philosophy. Let's FACILITATE to  install the MSOFFICE, PHOTOSHOP, EVERNOTE, FINAL CUT PRO, SKETCHUP PRO,  CAD and others MAC or MS softwares without any some virtual or terminal  command... lets cut with the protection that the open source offers for  the LINUX's developers and othes involved that probably the quality grow  up too...
Why to change to U18-LTS?????

---

### Post by Frogs Hair on 2018-04-25
Moved to *UL & OS Chat*

---

### Post by cesarcosta.br on 2018-04-25
Hi! 
It was my fault, was a mistake, sorry about!
Tks for your help.

---

### Post by TheFu on 2018-04-25
Why change to 18.04 if you are happy?  There is no immediate need.  I was running 14.04 on most of my systems until Feb.  Only reason to move was to get to a newer release that has longer support period. There was 1 program that I wanted the newer features from in 16.04 for 1 system.  That program isn't used on any other systems.

There's 1 more reason for my move from 14.04 --> 16.04 BEFORE 18.04 is released.   That was because community knowledge is lost for the common issues from the prior LTS migration. It is simply harder to find solutions for N-2 to N-1 migrations.

I don't care about Windows.
I don't care about end-users and desktops.
I do care about servers and being able to manage systems from anywhere in the world.  GUIs break that.

I switched from OS/2 to Unix to Linux.  Was forced to use MS-Windows for about 20 yrs.  I was a cross platform programmer and Windows was much more different than all the other OSes we supported.  It still is.   Once you understand the way things work below the GUI, you'll come to appreciate Unix and Linux.  GUIs tend to provide just 20% of the features that are available and are very difficult to automate.  Computers being automated is where the real power comes.  Point-n-click is highly inefficient for everything, except those 20 things  end-users need.   Pfffft.

I found a replacement for 1 more of my final 4 programs that only run on Windows a few months ago.  It has been these last 4 programs that keep any MS-Windows on my network. EVERYTHING else is handled nicely via native Linux programs.

MS-Office --> LibreOffice
Photoshop --> Gimp
Evernote --> BasketNotes (and there are 20 others)
I've never used the other tools, so can't say what replacements work.  There definitely is a CAD solution on Linux. I learned Engineering Graphics before CAD.

Of course, all the projects will happily accept *pull requests* with fixes.  People willing to actually do something to make a program better really do get to decide.  Just look at PulseAudio and SystemD.  They are being used not because they are great, but because someone works on them for 5-15 yrs and eventually, they are good enough.  PulseAudio has only been stable for me about 9 months.  For the prior 10 yrs, it sucked.  SystemD isn't stable yet, but in another 7 yrs, it might get there. Hard to say.

Expecting Linux to work like Windows is a mistake. It clearly is a different OS with a very different philosophy.  If you aren't familiar, learning the [Unix philosophy]("https://en.wikipedia.org/wiki/Unix_philosophy") would be very helpful. At least it will help understanding why programs like MS-Office aren't loved by Unix people.

I'm probably missing many of the other points.

---

### Post by Skaperen on 2018-04-25
my *System 76 Kudu laptop* came with 14.04 LTS _pre-installed_.  although i have shifted to doing much less OS installation work (and no more hardware building) i went ahead and did a full (not incremental) install of 16.04 LTS when it came out.  one reason i did this was to see if i could get the whole system to reside on one 1 TB drive.  my laptop was ordered with a 2nd 1 TB drive.  it was a success.  now both drives are bootable.  i tested the 2nd drive by first booting a recovery system from a USB memory stick, and copying the first 8 GB of drive 1 to another USB memory stick and comparing to verify it was a good copy.  then i used dd to zero out the first 8 GB of drive 1.  i tried to boot drive 1 first and confirmed it failed (lack of an OS).  then i tried to boot drive 2.  i had previously done a separate full install to it.  it came up fine.  this let me know that the setup on drive 2 had no dependency on drive 1 (well, at least not the first 8 GB where the boot loader is).

so i have a full independently bootable backup system.  too many times the install sequences ends up with some part(s) on drive 1, such as some blocks of the bootloader image or the Linux kernel.  so, not in this case.

to answer the thread: **16.04 LTS and happy with it.**  i see no reason to go to 18.04 LTS; i'll wait for 20.04 LTS and do another dual full install.  maybe i'll buy new hardware by then, either 2x 4 TB spinning rust or 2x 1 TB SSD, depending on what's cheap enough when.  **so, no 18.04 for me.**  i'll stay with 16.04 LTS for now.

FYI, i used to be a *Slackware* user (on a big desktop and a couple servers ready to be desktops just in case, plus a couple antique Sun boxes).  it was fun to customize everything but life has changed.  now i'm running things in the cloud (IaaS) and automating it.  think of that as "building hardware the point and click way".  and my programming has added Python to the assembly+bash+C mix.

---

### Post by kerry_s on 2018-04-25
if your running just fine don't.

others may have newer systems & want the support of more updated app's, better compatibility between software & hardware.
some just want to. :)

---

### Post by mastablasta on 2018-04-26
> **cesarcosta.br said:**
>  Let's FACILITATE to  install the MSOFFICE, PHOTOSHOP, EVERNOTE, FINAL CUT PRO, SKETCHUP PRO,  CAD and others MAC or MS softwares without any some virtual or terminal  command... 


how would that go? Linux is not making this software.  why MS, Adobe and others are not making the linux ports of their software?

---

### Post by Gottier on 2018-04-27
I'm typing to you from Ubuntu 14.04. Still works fine. No reason to upgrade yet.

---

### Post by thenailedone on 2018-04-28
> **Gottier said:**
> I'm typing to you from Ubuntu 14.04. Still works fine. No reason to upgrade yet.

Well until next year ;)

---

### Post by Gottier on 2018-04-28
> **thenailedone said:**
> Well until next year ;)

I know that support for 14.04 is facing EOL. I have been thinking about switching to 18.04 before then. I was just trying to point out that there's no urgent need to upgrade. I'll probably do my upgrade on a holiday weekend, or some other time when I'm really bored.

---

### Post by Tadaen_Sylvermane on 2018-04-28
I'll be riding 16.04 awhile yet. Downloaded and tried 18.04 in a virtualmachine. The new .yaml files for network configuration are a pain. Had to do a bunch of googling to find that you need to use spaces and not tabs. Kind of an important bit of info. Then no amount of fiddling would get a bridge to work. Lost all network when I tried to create a bridge. Without a bridge, no sense changing yet until its sorted out.

---

### Post by Qassis on 2018-05-17
On my home computer I changed to 18.04 for fun and to play with it (tweak, learn, etc.).
On other boxes I've left 16.04 LTS because it has a secure, guest sessions (guest account) whereas 18.04 does not.
Well, those are my reasons.....
qassis

---

### Post by LHammonds on 2018-05-17
I don't use Ubuntu Desktop.  But I do use the LTS version of server since 10.04.  When 12.04 was at EOL, I had 1 server still on that version and the rest on 14.04.  When I finally upgraded the complicated/peculiar 12.04 server to 16.04, I moved all my servers to 16.04.

I have started making 18.04 versions of my 16.04 servers but have not yet pulled the trigger to switch over...mainly because the MariaDB was going to be the 1st server but MariaDB does not yet officially support 18.04.  I have until April of 2021 to switch over to 18.04 so I do not feel a rush to do so yet.

The main differences between 16.04 and 18.04 that I have seen so far are:

[LIST=1]
[*]30 second pause during startup (have yet to track it down...might be related to still [using swap partition]("https://ubuntuforums.org/showthread.php?t=2391335") instead of swap file) 
[*]Different network configuration using NetPlan (but was [easy to figure out]("https://ubuntuforums.org/showthread.php?t=2389846&p=13758724#post13758724")...and seems more flexible for complicated settings) 
[*]Confusing ISO download of the server image.  Default is a fairly worthless installer they call "live" which has no support for LVM or RAID.  The "real" version is called "alternative."  I started a thread about the [differences here]("https://ubuntuforums.org/showthread.php?t=2390785"). 
[/LIST]

---

### Post by espressobeanie on 2018-05-17
All I can say is that if U18 is the new face of Ubuntu, then it's headed into a full-blown disaster. I'm going to rant in a separate thread.

---

### Post by uRock on 2018-05-20
No need to upgrade if things are still working correctly.  I had to upgrade because I was having endless problems with WiFi in 16.04.

Those softwares you listed as needing to be available for Linux are programs I have not wanted to use for almost ten years now.

As for users not wanting/needing to use CMD in Windows, that is why I got paid to remote into their systems and fix things that couldn't be fixed any other way.  Don't fear the terminal.

---

### Post by rrnbtter on 2018-05-20
Greetings,
I agree that 16.10 had a persistent wifi problem.  However it should be working fine today since those problems have been long solved. For myself, I am currently running Ubuntu 18.10 with Gnome/Wayland. I don't see much use for the terminal with this release, but I do have "terminal habits" that I haven't tried to break. Since I usually install Linux and a computer with a deleted MS system, I don't see the terminal going away completely. There are usually problems. I have a VM that takes care of the two programs that I need from MS. I don't see any need to update from 16LTS other than the fact that 18LTS is just plain nice.

---

### Post by uRock on 2018-05-20
> **rrnbtter said:**
> ...I am currently running Ubuntu 18.10 with Gnome/Wayland....
Did you mean 18.04?

---

### Post by rrnbtter on 2018-05-20
Greetings,

> **uRock said:**
> Did you mean 18.04?

I mean 18.10  as my header implies "Ubuntu Development version"

Description:	Ubuntu Cosmic Cuttlefish (development branch)
Release:	18.10
Codename:	cosmic
Type=wayland

---

### Post by uRock on 2018-05-22
> **rrnbtter said:**
> Greetings,



I mean 18.10  as my header implies "Ubuntu Development version"

Description:	Ubuntu Cosmic Cuttlefish (development branch)
Release:	18.10
Codename:	cosmic
Type=wayland

Whew hoo! Keep up the good work!  My laptop is running that, too, but it is kubuntu.  I don't normally mention the pre-beta releases outside the development sub-forum. I usually find the workarounds without having to post.

---

### Post by rrnbtter on 2018-05-23
Greetings,
@ uRock, Running dev isn't quite the same as in the past. With the new kernel patching system, I don't have to worry about vbox breaking.  There is currently a Wine compatibility problem  that I am working around by running the Windows port of Kompozer in my Win7 VM. I normally run the Kompozer.exe in Wine since the linux port has been broken for a few generations. I believe pre-Zenial.  Other than that it is a real beautiful system. I suggested 18.04LTS to the OP because it is stable and I love running both Bionic and Cosmic with Wayland and Gnome desktop. I have been using dev versions since Natty and with only thirty of forty reinstall's. Not bad for a journey that long. So I have survived all of the Canonical screw up's a long the way.  Today's Ubuntu is the very best I have ever used. I personally wouldn't want anything else. 
Best regards, to you.

---

