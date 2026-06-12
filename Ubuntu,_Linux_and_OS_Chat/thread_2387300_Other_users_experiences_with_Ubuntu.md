---
title: "Other users experiences with Ubuntu"
date: 2018-03-17
forum: Ubuntu, Linux and OS Chat
---

### Post by deanr2 on 2018-03-17
OK. I'm new to Ubuntu (about 6-7 weeks now) but I've now dual booted three of my PCs to Ubuntu (work desktop > Ubuntu Mate; work laptop > Ubuntu Mate; dedicated music laptop > Xubuntu).

I won't go into the issues I've had installing the OSs (and there have been plenty) and I consider very *fairly* competent when it comes to computers but...

Using the terminal fails to work like 98% of the time and I've no idea why. And I've read some basic books on using the terminal too to no avail. I've tried to install software, uninstall software, update packages, etc. - certainly nothing too advanced. And, almost every single time I get the same messages: unable to locate package, cannot locate package, download failed etc etc. I've checked and unchecked the boxes in the software updater and nothing makes any difference other than getting new messages along the lines of download failed...I've even tried to change swappiness values permanently following instructions exactly, copying and pasting commands - nothing happens, swappiness stays at 60 after rebooting.

Am I the only one that's having these frustrations? Is there some simple box I need to tick in the GUI to enable anything to work properly? Is it that packages just get deleted and therefore commands stop working?

It seems a lot of the software just doesn't work either. I started a thread about multimedia players elsewhere because Quod Libet is the only player that didn't crash immediately when trying to load my +500 gb music collection. But I cannot get it to retain the library and having to re-scan every time I start the computer renders the software completely useless to be frank. Do I have to go back to Microsoft and Foobar just to listen to my music library? No, I can try xnoise. Only that only comes in a tar.gz package which when I try to download alien to convert the terminal cannot locate alien package...

I'm completely sold on the idea of migrating fully away from Microsoft but will using Ubuntu always be so frustrating? 

And please, it's not my intention to a) get told to go back to Windows because I'm criticising or b) create a thread in which people just slag of Ubuntu (would that ever happen here?) but I'm very curious about other people's early experience and frustrations and whether or not they ever go away. Or maybe I'm 98% less computer competent than I imagined myself to be...

---

### Post by Autodave on 2018-03-17
Are you using the Software Center to install your programs? Or Synaptic? Or are you trying to install programs from other sources.  

Let's start with that question and we can go from there. :-)

---

### Post by deanr2 on 2018-03-17
I always search the Software Centre first, if it's not there I'll go to Synaptic. Failing that from other sources i.e. websites. I've managed to download and install WPS, for example, after simply downloading the .deb package.

I've also just this second managed to install Foobar via wine - Whoo Hoo ;-)

In between my posting and running Foobar, however, I've had more failed efforts through terminal trying to install xnoise (again) and foobnix...

---

### Post by crip720 on 2018-03-17
With the limited information, I will suggest a few basic problems you might have. One are you sure you are connected to the internet, two did you give yourself a large enough partition size, three are you using a still supported OS?  If you can answer yes to all three, give us your laptop type and what your version of Ubuntu is.

---

### Post by deanr2 on 2018-03-17
Hi crip720.

I'm connected to the internet with a decent enough (but not excellent 60 Mb/s) connection speed, I've created 4gb of swap (swap is on) and 40gb of hard drive space, I'm using version 16.04 of both Mate and Xubuntu (both 64 bit) and have updated everything regularly since installing alongside Windows 10.

Let's stick to the two laptops as the work desktop is fine with the very few programmes I need installed (Google Chrome, WPS Office, KeePass) :

Toshiba Satelitte intel dual core 3gb RAM (64 bit compatible)
Lenovo S210 touch intel dual core 4gb RAM (64 bit compatible)

Not sure about the monitors, graphics cards or sounds cards and I've not installed system profilers onto those pcs yet- all standard fare. But these wouldn't affect ability to download, install or locate packages through the terminal anyway would it?

Anyway, I'm not here on this thread so much as for a fix (I know there's also a specialised support forum) but rather for a discussion about how reliable newbies find Ubuntu OS and whether they have/had the same initial issues that's I'm experiencing...

---

### Post by wildmanne39 on 2018-03-17
*Thread moved to **Ubuntu, Linux and OS Chat, a more appropriate forum**.*

---

### Post by crip720 on 2018-03-17
Your basics and hardware seem to be good, on the software updater should have the first four boxs checked and leave the cd box unchecked.  You should just be able select a software to download and click on install.  Terminal should work just as well if everything is spelled correctly.  One or the other OSs might be corrupted but do not think both would be.  I find that Ubuntu has been very reliable and any problems can be usually fixed with a simple google search.  Unfortunately think I have come to the end of my knowledge to help, but someone else here will be able to help.

---

### Post by QIII on 2018-03-17
OK, OK, OK!

Let's stop a moment.  

@deanr -- if you need help, start a thread for one issue at a time.  Not ten.  Not five.  Not three.  One issue per thread.

That avoids everyone stepping all over each other.

If you really aren't asking for an answer to a particular question, then I think I can answer your general question thus:  No, it is not common for people to run into the things you are talking about; and yes, most of us get along just fine.

---

### Post by rbmorse on 2018-03-17
Xnoise died almost five years ago, and it appears the Foobnix developer stopped working on it about three years ago.  Based on that, it's likely that some of the error messages you see when attempting to install them relate to the package manager not being able to find the necessary support files (or the version specified by the application).  

This being Linux, it's quite likely the required files or specified versions are available _somewhere_., but trying to install them will almost certainly introduce you to a condition known as "dependency hell."  Sorting it all may be possible, but it will take a lot of time and monkey-motion, and is probably beyond the ability and patience of most new users.  

My advice for new users is to stick to applications in your distribution's repository wherever possible.  If not, at least make sure the application is still actively supported and all the required support files/libraries are available to your distribution.

BTW...this is not just a new user problem.  I've been using Ubuntu since 2004 and still occasionally run into version conflicts/dependency issues for a couple of the applications I've come to depend upon.  In general, however, it is not a problem and not something users new to Linux, especially one of the Ubuntus, encounters.

---

### Post by oldos2er on 2018-03-17
Can you post the full output from ```
sudo apt update && sudo apt upgrade
``` and also the output showing errors of ```
sudo apt install mc
``` "mc" is a small text mode file manager; it makes a good test package.

---

### Post by kerry_s on 2018-03-17
try solus, it's a new linux, from my experience if the software is in the software center it should work.
wps is in the third party section. you just click install, enter your password & done

my thoughts:
ubuntu is great, but they been having a lot of oops lately, stuff not working the way it should, etc....
i'm hoping 18.04 will just work right, but until it's released. well i'll just try others

---

### Post by Geoffrey_Arndt on 2018-03-17
To build on QIII comments, . . . no . . . most users do not have these issues IF they avoid trying to run Linux like it's a Windows OS.

For example:

>   For for 3 - 4 months, ONLY install software from the Official Repositories (and make sure that only the default servers are activated),
>   Do not get programs from random web sites.   Even getting Debian Packages can have some risk if unsure of the source and maintainability of packaging support.
>   Best NOT to run more than 1 desktop environment (which should be the default DE for the distro (e.g., XFCE for Xubuntu).   Budgie for Ubuntu Budgie and so on).
>   Do not try to use the CLI (command line interface) as a routine way to install programs or update the system UNTIL you have the concepts of repos and sources well understood (unlike Windows) and then the BASH environment in not forgiving of syntax errors or any other user error at all (like trying to install packages but not being in the right directory)!.   

The CLI is a great tool, but only for those that study it first and practice.  After a few months, it becomes second nature.   

Perhaps choose the easiest DE's first.   This is very subjective of course, but Budgie is like an enhanced version of ChromeOS and a great place to start.  (Ubuntu-Budgie is an impressive new official version of the Ubuntu family).

Note:   I run two distros - - Ubuntu Unity & Gnome, and Solus Budgie.    But I would not recommend Solus to a new Linux user as it uses an unconventional package system (not debian, not rpm).   For example, getting a Brother Printer installed can be a royal PITA if not downright impossible.   Plus, far less help (compared to Ubuntu or Fedora) on user forums etc.    Down the road, I think this is/will be a non-issue.

---

### Post by kerry_s on 2018-03-17
>     Note: I run two distros - - Ubuntu Unity & Gnome, and Solus Budgie. But I would not recommend Solus to a new Linux user as it uses an unconventional package system (not debian, not rpm). For example, getting a Brother Printer installed can be a royal PITA if not downright impossible. Plus, far less help (compared to Ubuntu or Fedora) on user forums etc. Down the road, I think this is/will be a non-issue. 


very true, but i personally haven't had to use the term yet for installing stuff.
doesn't hurt to try other things, even if it may not be a fit, it's good to scratch it off the list.

---

### Post by kenj69 on 2018-03-17
I started out full-time using Linux three years ago. I wanted something that looked and ran just like Windows 7 so I chose Mint 17. It was a rewarding experience - Linux, in my estimation, was finally ready for every day users. Mint is very cautious in testing their repositories which is great for newbies but, I was repeatedly running into ancient software releases. Finally realizing that I was ready for a more cutting edge distro I recently installed KDE Neon. It is great to now always have updated software and security patches. KDE Neon is claimed to NOT be a distro but a package DE on ubuntu (16.04 IIRC).

During the last three years I have mainly used the default repos but also tried the command line. My experience is that Linux, for the most part, installs software easier than ever - following the command line instructions in each case. KDE Neon uses something they call the the Discover Software Center. One of the great joys I had was downloading a deb file not in the repos and up pops Discover to install it for me, including adding it to the menu.

I have always built my own desktop PCs and my experience is that laptops can be "fiddly" containing odd hardware with unusual driver requirements. You didn't tell us what hardware you have beyond desktop/laptop, so hard to help there. Nevertheless, I am amazed these days how well the trial disks for these distros manage to find and install suitable drivers. In conclusion, I have had a much better experience with Linux distros and software.

-=Ken=-

---

### Post by QIII on 2018-03-17
Please spell "Windows" correctly.

As a point of order, Mint and KDE Neon are *not* Ubuntu, but independent distributions.

---

### Post by kansasnoob on 2018-03-17
Broken updates and package installation problems are frequently caused by the use of PPA's.

---

### Post by Geoffrey_Arndt on 2018-03-17
Yes - - especially bad to have those sources active when trying to upgrade to the next release (e.g., 17.10 to 18.04).    But here's the thing, I wonder how much the stability and upgrade processes will be affected by the growing use of encapsulated packages such as snaps, flatpaks and even AppImages.  These add a lot of size and some disk complexity to our historically stable Linux systems. 

Anyway, I digress from the OP's main topic . . . so . . . the OP will see these newer methods will make Linux a bit more like our friendly OS in Redmond.

---

### Post by deanr2 on 2018-03-18
Thanks for the responses. Maybe I'm just jinxed with Linux but now my music player has lost it's library again and I had to reboot the computer just to get it to find my hard drive. Can I even be bothered to let it scan my library for another two hours only to have to do it all again tomorrow? Doubtful...

This was actually the point of the thread - despite my best efforts and patience, almost nothing seems to work as it should. I understand the vast majority of software is perhaps not professionally (i.e. financially) well supported but when a lot of it just doesn't work it's maddening and extremely time wasting. 

QIII you answered my question in your statement 'No, it's not common' to experience such problems. 

rbmorse - thanks for taking the time and effort to explain. I suspected some of the problems may be related to unsupported software. I also think sticking to software in the boutiques is a logical thing to do for newbies. It's just a shame that there is no software there at all that will a) cope with the size of my music library and b) remember it from one day to the next. 

For later responses, I'm not familiar with Solus. I stumbled upon Mate because I didn't like the GUI of the regular Ubuntu (apologies if that's not what/how I should call it) and Xubuntu because I thought it would run better on an old laptop. Plus, of course, If I'm correct these are both official Linux distros so I figured these would be more stable and better supported overall. However, as I'm still kinda playing around on the laptops I can install Solus maybe it and see how it runs - and stay away from the terminal for a while ;-) 

Thanks again for all the discussion so far.

No doubt I'll keep persisting.

---

### Post by poorguy on 2018-03-23
Here's a good read.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by lighthousebeacon on 2018-03-28
Try Ubuntu Mate 16.04.4 LTS. It comes with the "software boutique" and "app grid". Both of these software sources I found to be beneficial in selecting what software to go with and try out in the early days. 
Stay clear of synaptic for now, first time I opened it I was just like wow, a little too overwhelming for me. Really does open up a whole new world but if you dont know what you are doing can easily lead to a quick downfall.
You like your music collection, start with the audio apps in the mate boutique and move on from there.
App Grid you can sort by top rated and read other users comments about it.

---

### Post by mastablasta on 2018-03-28
> **deanr2 said:**
>  Maybe I'm just jinxed with Linux but now my music player has lost it's library again and I had to reboot the computer just to get it to find my hard drive. Can I even be bothered to let it scan my library for another two hours only to have to do it all again tomorrow? Doubtful...

as you've established yourself - the issue seems to be with your music player. try another one. there are some that are made from ground up to work with large music collections. Linux is modular . it kernel with many components. many times components can be exchanged. also all these components are made by enthusiasts and if you can't help them with the programing you can at least report your experience (bug). it can help a lot. if no one reports it they assume it all works fine.

> 
For later responses, I'm not familiar with Solus. I stumbled upon Mate because I didn't like the GUI of the regular Ubuntu (apologies if that's not what/how I should call it) and Xubuntu because I thought it would run better on an old laptop. Plus, of course, If I'm correct these are both official Linux distros so I figured these would be more stable and better supported overall. 

There is no "official" linux distro. Ubuntu is made an supported by Cannonical. All other buntu's have let's say logistic and moral support, but they are entirely made by community. However, they do use Ubuntu as base and build on that (exchange components, test...).

I did not run into the mentioned issues. so far the only issue i have is with sound on my motherboard, however even for that i found a workaround i can use to fix it. another issue was with Firefox on KDE, it would act up, but using Chromium instead avoided that problem as well.

---

### Post by deanr2 on 2018-03-29
> **poorguy said:**
> Here's a good read.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Interesting read indeed. Having recently discovered Linux Mint, however, I'd say some of this article (esp. user-friendliness etc.) is no longer that pertinent.

---

