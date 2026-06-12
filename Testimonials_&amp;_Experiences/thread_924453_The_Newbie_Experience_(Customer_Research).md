---
title: "The Newbie Experience (Customer Research)"
date: 2008-09-19
forum: Testimonials &amp; Experiences
---

### Post by aaror on 2008-09-19
Before we start this shared journey to the Nirvanna Narwhal I wanted to explain what this forum is for, and request that discussion be at least somewhat on topic.

Specifically, I am looking for the experiences of new Ubuntu users, especially those migrating from windows and Mac.  If you have a story of your first install, a new addition you are working on, etc.  Please post it here.

If someone has described a problem they had, and you have a solution, feel free to post.

But if you want to debate the usefulness of this thread, please create a new post and reference it here, that way the original thread can stay on tack.

The idea behind this thread is that a new user will provide valuable information about what Linux and Ubuntu are doing right, and what they are doing wrong.  Someone who is used to Linux will have blind spots because "that is how we have always done it," which a new user will see past.  Also, we tend to forget which fixes took us hours to find, but the new user will remember and can tell us here.

So new users, please post your trials and tribulations, as well as your clever discoveries, here.

---

### Post by Ms_Angel_D on 2008-09-19
Just wanted to say... Good Idea for a thread :)

---

### Post by Lenus on 2008-09-19
For me everything went fine in my 64-bit Intel C2D :KS.

---

### Post by jaqie on 2008-09-19
It was xubuntu, not ubuntu, but I posted a thread in a format similar to what you are asking.  You can find it here:
[http://ubuntuforums.org/showthread.php?t=916054](http://ubuntuforums.org/showthread.php?t=916054)
That however was
1) specific to xubuntu
2) not asking others to share theirs
so this thread is a great idea to continue, just posting the link here instead of copy pasting the entire post I made again. :)

---

### Post by 73ckn797 on 2008-09-19
I am approx. 2 months into the Ubuntu Experience. My initial installation went well as a dual boot system with WinXP on my Toshiba laptop and BYOC desktop box. Being a tinkerer I created many issues that I had to work out. The forums have been a life preserver on many occasions. It does take some searching but the answers can be found.

There are things that I have quit searching for answers on due to the time involved. Those problems have not been with my system but my son's and an ATI HD3450 graphics card. Solutions have been suggested, tried and failed on the graphics card. Several calls for help have gone unanswered in the forums but through further searching some of those things were found to have been addressed before. I still have not received a clear answer about a video capture device compatible with Ubuntu. (I was at the local MicroCenter store today and none of the capture cards specifically stated they were V4L compatible).

It has been a change from the ways of MS Windows to the ways of Linux/Ubuntu. My very first reactions to issues was of frustration and considering going back to Windows. I decided to stick with it and am now becoming more at home with Ubuntu. I use it daily in my work now. I am not a gamer which avoids many problems.

Probably the one question that lingers, but I have figured out the work-around, has to do with HDD designations. (This may need to be moved to the appropriate forum beyond these comments here.) I currently have 3 HD's; 250g, 40g & 160g. The 160g is partitioned 30/130. 30g for XP and the rest for Linux. I have loaded many of the derivatives to check them out, onto that drive. The 250 drive is dedicated solely for Ubuntu Hardy.. The 40 is a back-up drive. When I have loaded another distro to the 160 drive there is always a failure to be able to boot into it. It seems that the installation reads my drives differently than the actual configuration. Any drive beyond hd0.0 is designated one drive higher. The Grub is written as hd3.0 instead of hd2.0 ... and so forth.  
 

 The actual physical connections are:
 250g = hd0/sda
 40g = hd1/sdb
 160g = hd2/sdc  (it took a few days to catch on to the drive titles, no more C, D stuff)
 

 It took several times to figure out what was happening. I was able to quickly make the corrections to the Grub using terminal and gedit. I have not read of others with this issue.
 

 I am certain there will be other things that I will have to figure out but I feel that just goes with the territory of trying something new/different.
 

 Since beginning this journey into Ubuntu I have been reading people's panic stories and other such things. That has not swayed me from Ubuntu due to their issues. I have, in fact, been able to help out from my experiences as a newbie.
 

 I now proclaim the Linux/Ubuntu experience but also understand people are different and what works for one does not work for others. That tempers my words. As I referred to earlier, the temptation is to run back to what I have used for so long. You cannot move forward when you are always running backwards!

---

### Post by aaror on 2008-09-20
73ckn797, I am totally shooting in the dark here, but is there any possibility that Ubuntu or Grub is interpreting your windows partition as a drive?  It is probably the first partition, so it may be defaulting to 0, forcing all the other drives to +1 to compensate.  Of course, if that is it, that would mean I was right about something, so I doubt it...

For a little background on what I am about to type, I messed up my original install enough that I figured I may as well just start over, so I have a few things I am re-installing...

I was trying to watch a movie, and I had already downloaded the medibuntu patch that lets me do so, but totem wasn't cooperating.  So I decided to install mplayer.  Last time I did that it took like two hours to figure out (I estimate one hour for normal user, plus one hour for me being dense).  This time I figured that it would be faster since I had done it before.

About 15 minutes into trying to figure out what worked last time, I decided to take a shot in the dark.  I went to the applications bar on the top of the screen, went to add/remove, and typed mplayer in the search box.  Five minutes later mplayer was installed and I was cursing myself for not looking at it earlier.

Recommend that be the first place us newbies look for software, I even found Opera there, though I don't think it worked.

---

### Post by 73ckn797 on 2008-09-20
> **aaror said:**
> 73ckn797, I am totally shooting in the dark here, but is there any possibility that Ubuntu or Grub is interpreting your windows partition as a drive?  It is probably the first partition, so it may be defaulting to 0, forcing all the other drives to +1 to compensate.  Of course, if that is it, that would mean I was right about something, so I doubt it...

I may not have clarified things enough. Yes, the Windows partition is being read as a separate drive. but the grub was still going +1 on the second partition (ie ... the Xp drive is hd3.0 but after install grub listed it as hd4.0 and the remainder was going to hd4.1, not hd3.1). I had to edit grub to hd3.1 .... etc and everything then booted up fine. The wacky thing is that on different installs, I was playing around with loading different distros, it would give different designations each time. One time while loading PCLinuxOS the drive designations were all messed up. I never could get it to become a part of the doot sequence in grub due to the designations. Count it all on being a newbie to Linux but Ubuntu was a more easier install. The drive designations were being misread when using the LiveCD. Once into the loaded system the designations were different.

If the physical connections are one way (250g = hd0, 40g = hd1 & 160g = hd2), all on their individual master drive connections (one is IDE and 2 are SATA), shouldn't the system recognize that as a given and not shuffle the designations? There were several times that the physical #2 drive (in BIOS order) was being made the #3 drive. That was causing some real confusion at times. I understand about the partitioning on any one drive would thus make a difference but not so much where it would list it as a totally separate drive (as if it were a 4th physical drive unit). The hd0 is never being changed through all of this venture.

I have settled into Ubuntu Hardy with Gnome. I personally did not like KDE. PCLinux has Gnome and KDE environments to choose but in the end I felt that it was basically the same thing as Ubuntu but, to me, more of a task to install. It would be easy if it was only a single system installation. Things would have probably worked fine.

I am still very pleased with the Ubuntu experience and do not plan on going back MS Windows.

Does all of this make sense?

---

### Post by BGrigg on 2008-09-20
I'm five days (well, evenings!) into my foray with Ubuntu. I've been mucking about with Windows since 3.0, so I'm no stranger to an OS that don't quite work right out of the box!

The install itself went well, and I've managed to get internet, email and printing handled without any issues. Even pulled over my Outlook contacts and email along with my desktop pic and bookmarks from Firefox.

Ubuntu isn't my first distro, that was Xandros 2, though at the time I was less interested in sticking with Linux. It was also a few years ago.

I've had a few "issues": 

[LIST]
[*]I can't seem to find a font that looks right.
[*]Firefox refuses to save my home page.
[*]ForecastFox and Google Toolbar refuses to remember my home code or that I don't want to use page rank, and have been disabled pending further research.
[*]Had to download a codec to play MP3!?!
[*]Still haven't figured out how to make the desktop cube work properly.
[*]Google Earth can only run from the Terminal, or I get Google Stars instead.
[/LIST]

Hmmm, maybe Google is causing me more problems than Ubuntu!

If I can figure out how to play games (other than the handful of "cute" games that is distributed with the distro) I might never boot back into XP.

Except for work, that is! :(

---

### Post by fballem on 2008-09-20
I started this journey in mid-May 2008 with ubuntu 8.04, coming from Windows Vista, MS Office 2007, including Outlook and Visio. I also had a full MS Programming environment (VS 2008 Professional, SQL Server Express).

I installed Thunderbird on the Windows machine before conversion and got everything out of outlook. I then saved all of the required files to an external drive. I also saved My Documents to an external drive.

I made the decision that I would not dual boot - and everything I have read in the forums confirms that there are problems with a dual boot. It's kind of like the old fashioned way of teaching a kid to swim - throw them in the water and be ready to rescue them if needed.

The first machine was an HP 9231ca laptop. It generally went well out of the box (and I even had wireless working at one point). One of the system updates killed wireless and I was never able to get it going. I used 32-bit hardy. I had found an excellent tutorial on installing ubuntu on HP and Compaq laptops, but it seems that the link has disappeared.

My wife fried her laptop, so I had to give her mine (and convert back to Windows Vista).

I bought bits and pieces and built a desktop. The ubuntu installation went very well. I had problems with a logitech USB headset, but was able to solve those. There are multiple threads in the forum that describe how to solve that problem.

The kids also have a computer, which is also running ubuntu. They are very happy with it.

I do miss a couple of things: haven't found a really good replacement for Visio, and I'm still searching for a good set of tools that I can use in my Business Analysis practice - the tools that I have found so far are either expensive or not very good. In Windows, I used Enterprise Architect from Sparx Systems Pty in Australia. I have heard that it will run in a Windows emulator, but it looks really complicated. 

Other than that, I have been happy with ubuntu. I have set up one of my clients on ubuntu. She was using Windows XP. I know Windows well, and even so, it takes about a day-and-a-half to do a reasonable install with all programs, including testing. Fine tuning the configuration used to take another day. I can get a reasonable first cut install of ubuntu in about 3 hours, and the fine tuning takes the rest of the day.

I have found the following link helpful. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I usually follow the instructions in that link after the video drivers are installed and before I do a full system update. It's easy and relatively quick.

Hope this helps,

---

### Post by aaror on 2008-09-20
First, thank you all for the great input...

Fballem, have you tried Wine?  I'm not saying it will work (I have not even gotten it to work with something it should work for), but it won't take long to try and it isn't complicated.  Wine is basically just a windows skin that fools programs into trying to run on Linux (Yes, I know it is more than that, but lets not get bogged down here).  Once it installs, it works a lot like windows, so you shouldn't have any trouble figuring it out.

Minor complaint with Totem, every time I launch I have to fix the volume... no idea for a fix.

Can't get Neverwinter Nights 2 to run on my machine, even though both the Wine app list and the neverwinter nights 2 forums say it will.  I just get a black screen, will talk more about it when I get more of a handle on what I am doing wrong.  It could be my ATI driver...

Minor annoyance (and this is a problem in windoze too), any pop up system messages should use "always on top," instead of "bring to front."  Otherwise when you are typing and a system message appears, your typing will select an option before you realize it was there, and then you are asking yourself "what did I just say OK to?"

---

### Post by fballem on 2008-09-20
> **aaror said:**
> First, thank you all for the great input...

Fballem, have you tried Wine?  I'm not saying it will work (I have not even gotten it to work with something it should work for), but it won't take long to try and it isn't complicated.  Wine is basically just a windows skin that fools programs into trying to run on Linux (Yes, I know it is more than that, but lets not get bogged down here).  Once it installs, it works a lot like windows, so you shouldn't have any trouble figuring it out.


No haven't tried Wine. The Enterprise Architect product uses an MS Access database, which means MDAC and a few other odds and sods needs to be installed. In addition, the EA site suggests a different emulator that is not free. At the moment it is not a super-critical 'must have'. Besides, it will encourage me to participate in finding or developing a solution. If it does become super-critical, then I'll have to go back to Windows, since I will need both Visio and Enterprise Architect. What I'm hoping is that there will be an alternative to EA that I will be able to use without having to go back to Windows. I think I'm at least two years away before I even need to worry. Besides, I do have access to my wife's laptop - at least once in a while.

---

### Post by Ms_Angel_D on 2008-09-20
> **aaror said:**
> Can't get Neverwinter Nights 2 to run on my machine, even though both the Wine app list and the neverwinter nights 2 forums say it will.  I just get a black screen, will talk more about it when I get more of a handle on what I am doing wrong.

I managed to get NWN2 running under [cedega]("http://www.cedega.com/start/"), you may wanna try it out, of course it's not free ($5.00 a Month with a minimal 3 month purchase to begin) but it works well for me.

---

### Post by spandanj on 2008-09-20
a scare of my life....this is what happens
Ok, I got a perfect example to support my belief that configuration should be wizard based instead of command line

So, I own magicjack, a VoIP telephone. I didnt work in virtualbox-winxp. I thought it had to do with networking. So, i started looking up on that. I found the problem could be solved if i set vbox networking from NAT to host interface using bridging. I set upon setting up the bridge. I did not know what I was up against.

I came upon this page to help me set it up: [https://help.ubuntu.com/community/Vi...x#8.04%20Hardy](https://help.ubuntu.com/community/Vi...x#8.04%20Hardy). So, I followed it's instruction of setting a bridge connection between vbox and host. Took me about 10 mins which involved change system files such as etc/network/interface, etc. installed bridge-utilities, etc. Ran several commands which I had no clue what it was doing except it was part of the 15-20 step process. I kept my cool running all the steps and being careful doing them just as they said (they looked weird since I am a newbie--a normal person who does not want to and shouldn't have to know how a linux operating system works).

When all was done and finished, magicjack still did not work in vbox. So, I said, I will just go back to NAT since it had no other problem.

I restarted the computer...

WOAH, it now tells me something like

kinit: boot image missing
resume normal boot
user tty1...something

my screen size had gone from 1280x800 to very low. all effects were off. I was scared shitless. Not only did I not know what went wrong, I had no idea wat to do fix it.

so, i re-edited all system files to the way they were. uninstalled bridge utilies. and restarted. still the same problem.
-->restarted again, chose 'recovery' ubuntu. did all the recovery-->restart. NOW, it worked fine.

So, the GIST of the story is: I had no knowledge/understanding of what the steps were telling me to do. I did not know how to reverse the effects if I wished to uninstall in future. And, it almost broke my computer setting up a bridge connection. Had it been windows, how would I have set up a bridge connection? Network connections-->right click-->bridge connection. that is it.


So, WHY can't we have a wizard to do mundane tasks like setting up bridge connections? or a script? The question is not WHY the command line? Because there might be benefits to command line to a programmer. The question is WHY NOT a wizard to make it easy? and I will tell you why NOT the command line....because guys like me can and possibly will mess up a lengthy procedure like this with no way of getting out or fixing it (or atleast not knowing how to).

So, tell me, why not a wizard or a script?

---

### Post by aaror on 2008-09-21
> **spandanj said:**
> a scare of my life....this is what happens
Ok, I got a perfect example to support my belief that configuration should be wizard based instead of command line

So, I own magicjack, a VoIP telephone. I didnt work in virtualbox-winxp. I thought it had to do with networking. So, i started looking up on that. I found the problem could be solved if i set vbox networking from NAT to host interface using bridging. I set upon setting up the bridge. I did not know what I was up against.

I came upon this page to help me set it up: [https://help.ubuntu.com/community/Vi...x#8.04%20Hardy](https://help.ubuntu.com/community/Vi...x#8.04%20Hardy). So, I followed it's instruction of setting a bridge connection between vbox and host. Took me about 10 mins which involved change system files such as etc/network/interface, etc. installed bridge-utilities, etc. Ran several commands which I had no clue what it was doing except it was part of the 15-20 step process. I kept my cool running all the steps and being careful doing them just as they said (they looked weird since I am a newbie--a normal person who does not want to and shouldn't have to know how a linux operating system works).

When all was done and finished, magicjack still did not work in vbox. So, I said, I will just go back to NAT since it had no other problem.

I restarted the computer...

WOAH, it now tells me something like

kinit: boot image missing
resume normal boot
user tty1...something

my screen size had gone from 1280x800 to very low. all effects were off. I was scared shitless. Not only did I not know what went wrong, I had no idea wat to do fix it.

so, i re-edited all system files to the way they were. uninstalled bridge utilies. and restarted. still the same problem.
-->restarted again, chose 'recovery' ubuntu. did all the recovery-->restart. NOW, it worked fine.

So, the GIST of the story is: I had no knowledge/understanding of what the steps were telling me to do. I did not know how to reverse the effects if I wished to uninstall in future. And, it almost broke my computer setting up a bridge connection. Had it been windows, how would I have set up a bridge connection? Network connections-->right click-->bridge connection. that is it.


So, WHY can't we have a wizard to do mundane tasks like setting up bridge connections? or a script? The question is not WHY the command line? Because there might be benefits to command line to a programmer. The question is WHY NOT a wizard to make it easy? and I will tell you why NOT the command line....because guys like me can and possibly will mess up a lengthy procedure like this with no way of getting out or fixing it (or atleast not knowing how to).

So, tell me, why not a wizard or a script?

I'm going to go out on a limb here and say that there may be a wizard.  When I wanted to install Mplayer, after 2 hours of trying to find a command line way to do it, I clicked on add/remove programs and added it (5 minutes later I was watching my movie).

That being said, I have absolutely no clue where that wizard would be or what it is called.  I used the little blue help button, and found a server guide, but it may as well have been written in Greek for all the good it did me in thinking about your problem.  Sorry.

---

### Post by jolx on 2008-09-21
> **spandanj said:**
> a scare of my life....this is what happens
Ok, I got a perfect example to support my belief that configuration should be wizard based instead of command line

So, I own magicjack, a VoIP telephone. I didnt work in virtualbox-winxp. I thought it had to do with networking. So, i started looking up on that. I found the problem could be solved if i set vbox networking from NAT to host interface using bridging. I set upon setting up the bridge. I did not know what I was up against.

I came upon this page to help me set it up: [https://help.ubuntu.com/community/Vi...x#8.04%20Hardy](https://help.ubuntu.com/community/Vi...x#8.04%20Hardy). So, I followed it's instruction of setting a bridge connection between vbox and host. Took me about 10 mins which involved change system files such as etc/network/interface, etc. installed bridge-utilities, etc. Ran several commands which I had no clue what it was doing except it was part of the 15-20 step process. I kept my cool running all the steps and being careful doing them just as they said (they looked weird since I am a newbie--a normal person who does not want to and shouldn't have to know how a linux operating system works).

When all was done and finished, magicjack still did not work in vbox. So, I said, I will just go back to NAT since it had no other problem.

I restarted the computer...

WOAH, it now tells me something like

kinit: boot image missing
resume normal boot
user tty1...something

my screen size had gone from 1280x800 to very low. all effects were off. I was scared shitless. Not only did I not know what went wrong, I had no idea wat to do fix it.

so, i re-edited all system files to the way they were. uninstalled bridge utilies. and restarted. still the same problem.
-->restarted again, chose 'recovery' ubuntu. did all the recovery-->restart. NOW, it worked fine.

So, the GIST of the story is: I had no knowledge/understanding of what the steps were telling me to do. I did not know how to reverse the effects if I wished to uninstall in future. And, it almost broke my computer setting up a bridge connection. Had it been windows, how would I have set up a bridge connection? Network connections-->right click-->bridge connection. that is it.


So, WHY can't we have a wizard to do mundane tasks like setting up bridge connections? or a script? The question is not WHY the command line? Because there might be benefits to command line to a programmer. The question is WHY NOT a wizard to make it easy? and I will tell you why NOT the command line....because guys like me can and possibly will mess up a lengthy procedure like this with no way of getting out or fixing it (or atleast not knowing how to).

So, tell me, why not a wizard or a script?

dude could u stop trolling? please?

---

### Post by mailtwogopal on 2008-09-21
Hi all,

  I am a 100% ubuntu user, approximately for past 4 months and before that i had dual boot of ubuntu hardy with Win XP. I am happy with the way ubuntu is going on, but still i have few issues to get sorted. I am sure that i will get help from this forums. Even i had lot of help from here. My ubuntu installation started with Wubi installer and it went fine without any riddles. All i can say is UBUNTU LINUX is the powerful OS and one who wants to learn more can surely come for UBUNTU. As i read earlier "LINUX IS NOT WINDOWS" rather it is ahead of windows. A quote in my signature area reflects my experience on usage of UBUNTU for this short span.

---

### Post by azirk on 2008-09-21
I'm on Day 2 of 8.4.  Upon installation, I deleted Windows Vista, and Ubuntu is the only OS on my system.  My desktop is an upgraded POS (By POS I mean AMD Sempron(tm) Processor LE-1250) eMachine w/ an Nvidia 8400 graphics card and 4 gigs RAM (200 Gigs ROM).  I've mostly been turning on features and trying to figure out how to learn the OS, and it's been a generally pleasant experience for two reasons:

1) I'm not ashamed of saying "I have no idea what to do".  I've been Googling a lot of terms I see but don't know the meaning of.  It'd be nice to have a more centralized place where all the FAQs go, but otherwise I've had no trouble trying to set up my desktop to outperform Vista (I find the Cube entertaining but rather pointless).  I'm gradually coming to love the extended features that Ubuntu offers.

2) I'm perhaps a bit simple, but I enjoy learning new things.  I've heard a lot about Ubuntu and decided to jump in the pool rather than test the water with my foot (well, I ran the Live cd for 20 mins or so, but only really learned that indeed it would boot on my computer, and the GUI looked similar enough to windows).  And I work at a university that has an agreement with Microsoft, so I can technically get Vista back for free if I ever feel the need.  

I ran into the hybernation issue I've seen here, before I ever looked at this board.  I also ran into a problem with the cube caps, as in they don't work (at least, not for me).  Overall, fairly insignificant problems.

Otherwise, it runs clean and neat.

---

### Post by steveneddy on 2008-09-21
I guess you could look back about 2500 post ago and read about my noobie-ness with Ubuntu.

I started at 5.04 and have loved it ever since.

I have been Windows free for almost four years now.

(I used Linux before I found Ubuntu)

---

### Post by aaror on 2008-09-22
So I was (still) trying to get my computer to play my game-I have about decided to install XP and dual boot-and guessed that the graphics driver might be to blame.  A friend suggested envy ng.
So I took my ATI driver offline, and installed it.  When I rebooted my computer, and logged on, I had a completely white screen.  After trying several times to load it up with some sort of "last known good," configuration using the bootup utility, I finally booted the computer with the Ubuntu CD.  There I did something truly rash, and read the manual (RTFM, I won't say what the F stands for).
Turns out that others have had this problem, and the easy fix is typing envyng --uninstall-all.
I suspect that would work for any other program you install that breaks your system.  Of course, you have to know how to get to the root menu.  From the boot menu, chose the recovery option, and at some point it will ask you for another selection, root is one of the options.
Sorry I am not giving better info, this is all from memory of what I did last night, and I have only done it once.
Anyone else have newbie problems that might be worth telling others about?

---

### Post by TwiceOver on 2008-09-22
I've been solely using Ubuntu since the release of Hardy.  Only 6 months in and I run it as the sole operating system on my Desktop and Laptop (well there is a Vista partition on my lappy but I haven't booted it in at least 5 months).

I'm currently changing over my Windows XP "Server" to 8.04 Server Edition.  You can read about it and me over [Here]("http://experienceubuntu.blogspot.com/").

---

### Post by starcannon on 2008-09-22
I use and love Ubuntu exclusively.
That said, my only true banes are:

[LIST=1]
[*]suspend/resume/hibernate
[*]VIA (even though they have opened the drivers)
[*]Multimedia keys
[/LIST]
Thats it, once those issues are resolved my angst will be completely resolved. I listed them in my personal order of importance.

Great thread, thanks. If I posted off topic by mistake I apologize, but I think this kinda fits the theme of the thread.

---

