---
title: "Ubuntu for Beginners"
date: 2011-03-11
forum: The Cafe
---

### Post by dandandrums on 2011-03-11
**Guys, i wrote a guide to Ubuntu for beginners and would appriciate it if you could give me feedback and distribute it to possible future ubuntu users. thanks.**


**Linux? Ubuntu? Meerkats? What is this?!**
 
Linux is the kernel that powers Ubuntu, whilst Maverick Meerkat was the development name for 10.10. To make this more simple, it's equal to:
Linux = MS-DOS
Ubuntu = Windows
10.10 = XP, Vista, 7
Maverick Meerkat = Window's Neptune. 
 
**Okay, so... Why should I care?**
 
Ubuntu is a free operating system (compared to Windows 7 Ultimate costing £177) which is developed by a company called Canonical, but more importantly, the community.
 
If you know anything about programming (given this is an idiot's guide, you probarbly don't), You can contribute to the project and fix some bugs, report bugs or use experience to help other people on Forums (google anything then add on ubuntu, you usually find something to help you).
 
**What's so cool about Ubuntu then?** 
 
Ubuntu is everything Window's isn't. You don't have to pay for it, 99% of the software is free (and legal, may I add) and everything is much less complicated. Bootup times and shutdown times are much faster, you can do what you turnt on your laptop or computer to do and you can do it without worrying about things slowing down over time. Many of the issues in Windows do not exist at all on Ubuntu.Surely their's viruses though?
 
I'm not going to be a camel, stick my head in the sand and say their isn't but Ubuntu (being Linux) is naturally much more secure due to the way file permissions are done (don't worry, doesn't effect you much). What it means is, if you decide to install a program, the computer will ask for your user password then that's it, you're installing. It also means programs cannot install other things without your knowledge (unless you have downloaded a virus, trojan, malware etc).
 
Ubuntu comes with something called a software centre. Anything green-lighted by canonical will appear in the Software Centre (similar to Apple and the I-Tunes store). Anything here will not have viruses (as Canonical have to test EVERYTHING).
 
**But Ubuntu/Linux/Anything that isn't Windows/etc is for the geeks!**
 
That is entirely untrue. Many people are using Linux without even realising! In fact, here's some examples!
 
Android is based on Linux, Google use's Linux (how many times have you used google? You've used Linux!), Many routers (for internet) use Linux and many set top boxes (freeview boxes for example) use linux, Including specialist kit I.T companie's use. 
 
Ubuntu can be used by anyone willing to put the tiniest bit of time into learning how things can work differently. Think about the OSX that Apple Computers use (and the iOS that the devices use). If you can spend the time to use that, why not use Ubuntu and speed up, secure and enjoy your computer more!
 
Ubuntu will run on computers that used to run Windows 2000 (far as i've tested) with reasonable speed and usability.
 
**Awesome, so how do I install this thing then?**
 
**FIRST OF ALL!!!**
Back up all your data onto external harddrives, DVD's, Memory sticks, whatever. Make sure any files, photos and music you want to keep is backed up.
If you want to use both Windows and Ubuntu, make sure you have defragged the computer beforehand (if you don't know how to, Google is your friend!)
 
**Now we can begin the step by step process (i promise you, it's really simple!)**
 
Go to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) 
Click the Big ol' download button. (free download, FYI) 
Get yourself a memory stick with about 2 gigabytes free. (1 gig will probarbly suffice, i haven't checked)
Once the download has completed, save that file to the empty memory stick.
Restart your computer.
Go through the Graphical Installation Process (posh for "that screen with colours and pictures that come up to install ubuntu)
If you run the LiveCD, make sure after messing about, you click "Install" which you find on the desktop.
If you want to use Ubuntu only (recommended), just tell Ubuntu to use the whole drive (this will delete all the information contained, including Window's!)
If you want to Dual-Boot (have the choice on startup to use either Ubuntu or Windows, give ubuntu a sizable partation on the install screen.
Once completed, restart for safety, and you're done!
 
**Awesome, I'm running Ubuntu, any tips?**
 
Well, i'm guessing you'll be wanting to use YouTube (or flash in general), MP3's etc so you'll be wanting to download the Ubuntu Restricted Extra's (stuff that can't be downloaded with Ubuntu for legal reason's, pesky lawyers!).
 
To do this, you'll have to run... **THE TERMINAL! **
 
**THE TERMINAL?! WHAT IS THE TERMINAL?!**
 
Ever gone on windows, or seen old computers, and seen that black background with white writing, and everything looked old? That's MS-DOS, the thing that tell's Windows "Go" (with a shoelace untied of course). In Ubuntu, the terminal is rather the same, but with a funky purple background instead (why not?). 

**Awesome, history lesson, love it. COME ON, HURRY UP YOU GIT!**
 
Alright, alright. Go to Applications > Terminal.
 
Once the terminal comes up, take a deep breath, chill out and then type " sudo apt-get install ubuntu-restricted-extras".
 
It will then ask for your password (in the terminal), then it will run lots of things on the screen and do some downloading. Just leave it be for a while. Once everything seems to have stopped (and you see no numbers or anything), close the terminal (the X in the corner), then that's it! YouTube is all yours!
 
**Awesome, thanks. I tried watching a DVD and it failed. Why?**
 
Most DVD's are commerical, and thus use a commerical codec not included in Ubuntu Restricted Extras. To install this codec, it's time to open up the terminal again (note, this is for DVD's, i have no idea about Blue Ray and stuff).
 
Type in "sudo apt-get install libdvdread4", click enter, then type your password (then hit enter again). Then once that has installed, type in "sudo /usr/share/doc/libdvdread4/install-css.sh" (this sometimes asks for a password, sometimes not, no worries about either).
 
Once that is done, restart your computer and enjoy those Family Guy boxsets and Christmas DVD's as you see fit!
 
[B]Thanks for reading!
 
Dan :)
[/B]

---

### Post by ikt on 2011-03-11
It's good but there are already some very polished guides out there, ubuntu manual: [http://ubuntu-manual.org/](http://ubuntu-manual.org/) is one, they could definitely use your help:

[http://ubuntu-manual.org/jobs](http://ubuntu-manual.org/jobs)

:)

---

### Post by frup on 2011-03-11
Your example of Linux being like MS-DOS is wrong.

Linux is a kernel. Windows has the win32 kernel.

I suppose you could equate bash and the gnu userland to being similar to MS-DOS in visual appearance but GNU has far more functionality, even a 1980's unix would have had more functionality than MS-DOS.

Linux and the MS-DOS / Windows OSes are so different that trying to compare them like this is going to be very difficult... and pointless for a new user to understand. For the purposes of what you are trying to do, comparing them like this is unnecessary surely?

But keep it up, it's awesome you're trying to spread the word about something we all enjoy using.

---

### Post by kidsodateless on 2011-03-11
not bad :D


imho. Why don't just directly explaining the ubuntu versions and code names rather than comparing it to doze:

> The official name of ubuntu derives from the year and month of its release. ex. 10.10(2010,October). Ubuntu also given its code name, start with an adjective and name of an animal (Maverick Meerkat).

---

### Post by Dustin2128 on 2011-03-11
> **frup said:**
> Your example of Linux being like MS-DOS is wrong.

Exactly. You do not need to elaborate any further.

---

### Post by Lucradia on 2011-03-12
> **Dustin2128 said:**
> Exactly. You do not need to elaborate any further.

That's why people who don't use linux dislike linux users. They don't explain *why*.

---

### Post by ikt on 2011-03-12
> **Lucradia said:**
> That's why people who don't use linux dislike linux users. They don't explain *why*.

But the person who suggested the issue did?

---

### Post by Lucradia on 2011-03-12
> **ikt said:**
> But the person who suggested the issue did?

People who don't use linux regularly often don't explain the issues, etc. fully either. It's why they still use Windows, IE, etc. too.

But there is one thing between Linux and Microsoft that bugs me: Devs / Support Gurus don't like it when problems exist that they cannot fix / control; so they just leave the issue sit around. For example, I have an issue where Windows Live Messenger will randomly drop ALL history from a conversation I've been having for over 5 hours. Unfortunately, none of the fixes that have been suggested help, at all. (Yes, including moving the convo history to another location) At times, I am forced to go to Pidgin. Unfortunately for Pidgin; I can't add contacts via MSN, nor send/receive files.

Similarly, ANY non-WLM client disallows me to send/receive files, and will not allow me to add contacts. (eBuddy, Meebo, Miranda, etc. will all say the contact doesn't exist.)

And if someone tries to add me while I'm still using one of the non-WLM clients, either "Cannot add the user <insert strange HTML Code> to buddy list." Error appears, or nothing happens, and they can't see me online ever, until I go into WLM to add them.

Or on cross-platform issues, this userscript: [http://userscripts.org/scripts/show/57971](http://userscripts.org/scripts/show/57971)

Only works perfect in Firefox. In Chrome, it will randomly stop playing at the end of a youtube movie, and will not play at all until I drag the seeker to the beginning of the video.

Or in Linux, where the WineHQ people won't respond to a bug report (Example: [http://bugs.winehq.org/show_bug.cgi?id=26371](http://bugs.winehq.org/show_bug.cgi?id=26371)) and leave it lay for possibly up to 6 month before responding to it, only to say something like, "It's a game issue" or "You're using too many DLLs," or "Won't fix, it's a microsoft issue." Etc. Why can't devs explain their reasonings in full? They expect us too.

I love linux distributions, but it would be nice with more explanations behind a sudden "won'tfix" or "worksforme" in detail.

---

### Post by or3x on 2011-03-12
Great guide, I'm sure it'll be helpful for beginners, and it's funny!

---

### Post by Old_Grey_Wolf on 2011-03-12
> **ikt said:**
> It's good but there are already some very polished guides out there, ubuntu manual: [http://ubuntu-manual.org/](http://ubuntu-manual.org/) is one, they could definitely use your help:

[http://ubuntu-manual.org/jobs](http://ubuntu-manual.org/jobs)

:)

I also like this guide [http://ubuntuforums.org/showthread.php?t=1602315](http://ubuntuforums.org/showthread.php?t=1602315).

---

### Post by Old_Grey_Wolf on 2011-03-12
> **dandandrums said:**
> **Now we can begin the step by step process (i promise you, it's really simple!)**
 
Go to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) 
Click the Big ol' download button. (free download, FYI) 
Get yourself a memory stick with about 2 gigabytes free. (1 gig will probarbly suffice, i haven't checked)
Once the download has completed, save that file to the empty memory stick.
Restart your computer.
Go through the Graphical Installation Process (posh for "that screen with colours and pictures that come up to install ubuntu)

If I follow those steps as written it will not work. You can't just copy the file to a USB and expect it to boot.

---

### Post by perspectoff on 2011-03-12
Ubuntuguide and Kubuntuguide have free eBooks (PDF format) for download at:

[http://www.kubuntuguide.info/index.php/Category:Books](http://www.kubuntuguide.info/index.php/Category:Books)

They are about 450 pages and are quite comprehensive. They are not strictly for absolute beginners and are not "dumbed down" like many beginner manuals out there, but are oriented towards those who want to actually do something after installing Ubuntu or Kubuntu.

---

### Post by Dustin2128 on 2011-03-12
It was a half joke, the dos thing. I was taking offense at the linux kernel being compared to the dos kernel.

---

### Post by dandandrums on 2011-04-25
thanks for all the feedback, I wasn't aware of other guides so I'll definitely offer help to them.

I apologise for any mistakes, I haven't been using Ubuntu long but I tried hard as I could to be as accurate and beginner friendly as possible.

Thanks for reading, have a great day! :)

---

