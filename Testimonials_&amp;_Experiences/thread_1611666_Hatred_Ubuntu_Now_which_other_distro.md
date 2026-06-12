---
title: "Hatred Ubuntu? Now which other distro?"
date: 2010-11-02
forum: Testimonials &amp; Experiences
---

### Post by ario on 2010-11-02
In a rush of hate of Ubuntu tried to get rid of it and install a new distro! My reasons were:
> Bluetooth problems
Network Manager Problems:
[INDENT]No DSL Connection
No NPA or WPA2 only wireless connection
Conflict with PPPoE
[/INDENT]HDD Spin Down Problem
Very high power usage on laptop
Internet sharing is not true GUI
Murrine is not working
No way to change cursor normally
Some times you must restart the laptop just to read a card!
Tried Fedora 13 but:
After installation on virtual box decided to look around main menu. There were:
**[CENTER]NO OPEN OFFICE![/CENTER]**
That was ridiculous but no problem! I will install it by hand. Ran package manager system from Administration menu. It opened a window with a list of software categories on left side. Clicked on each of them but:
[CENTER]**THERE WERE ALL EMPTY LISTS!**[/CENTER]
No problem. I will refresh list. I have a connected NAT Internet in virtual machine trough virtual box and I hope when I install in on my laptop it will detect DSL connection without problem. Chose refresh from first menu on top left. It showed Waiting for authentication and downloaded and downloaded and... nothing happened! I noticed that when I started this application it didn't asked me to enter root password. So this must be because of some privilege problems. I decided to run it by a sudo like command. The command **sudo su** in fedora is **su -**. But I didn't know what is the command to run that GUI application for software management. I tried to run a trick! Right clicked on main menu to edit it, but:
[CENTER]**THERE WAS NO MENU EDIT COMMAND!**[/CENTER]
After about half hour searching Internet found that I must install alacarte for editing menus! It's funny fedora boys!:D
Opened a terminal and ran **yum install alacarte** as root. It installed. Then edited menus and saw that the command for software manager is **gpk-application** or something like this. By the way, ran it as root in a terminal, opened the same window, but this time it showed a progress bar and updated package list just like in synaptic. No more infinite wait for **Authentication** things! After that I decided first try to update my system and then install openoffice.org suit. but:
[CENTER]**THERE WERE NO OPTION TO UPDATE MY SYSTEM!**[/CENTER]
Ok. Still no problem Fedora is not windows and Redhat is not Bill Gates. They are good guys. They created a lot of good stuff for Linux community which we can not forget them. I selected item Update from Administration menu. It refreshed again and downloaded a list from server, after all told me it must update about 4MB of software! I was very astonished! Only 4 mega bytes of software? Ok. Go on... . It downloaded, installed and suddenly the window disappeared! I mean update window just vanished! Started it again and it refreshed again and this time told me that it must download 400 MEGA BYTES of stuff! Ok. This time it is more comprehensible. Its several months since they published Fedora 13 and it needs a bunch of update packages. But I did not have enough time and bandwidth to download them. Decided to find an option like that magical fancy command in synaptic called **Generate package download script**. But there were no option like that. Searched all over Internet, no, not at all! There are no fedora users who likes to update his system all the night using free bandwidth, thus they don't need any **Generate package download script** options for their OS.
Good luck fedora team. Keep going the good work.
I remain Ubuntu ;)

---

### Post by Engin33r on 2010-11-02
I had some problems with Ubuntu too
just installed it 2 days ago..The biggest problem was the Network Utility thing
I only have wireless internet, so when i tested Ubuntu with livecd first, everything worked fine, but when i installed it, for some reason it wouldnt pick up any wireless connections, so i re-installed it, and eventually it started picking up the wireless.

Then today I had to reset my wireless router not related to Ubuntu...but after resetting the router, UBuntu wouldnt pick up my new wireless signal, and just show my old internet connection and say that its not connected....but its working now...Thank god

Now i am having trouble with PDF lol....but I hope it gets sorted too..

---

### Post by Spice Weasel on 2010-11-02
Which Fedora version were you using that didn't have an option to update your system? O.o

su -c "yum upgrade"

or (picture attached)

The update manager first downloads repository infomation (which is small, like you said, around 4MB.) then refreshes it and downloads then installs the updates. Sounds like you'd prefer a less updated and more stable system if you consider that too much and don't want to update often. There are lots out there, Scientific Linux, CentOS, Debian or Ubuntu.

The no OpenOffice.org is one of Fedora's policies, they include complete desktop environments and try to keep them as unmodified as possible for a consistent experience. AbiWord and Gnumeric are part of GNOME, whereas OpenOffice isn't.

---

### Post by Refalm on 2010-11-02
Have you tried [Linux Mint](http://www.linuxmint.com)? It's supposed to be an enhanced version of Ubuntu.

---

### Post by overdrank on 2010-11-02
Moved to Ubuntu Testimonials & Experiences

---

### Post by ario on 2010-11-02
> **Spice Weasel said:**
> Which Fedora version were you using that didn't have an option to update your system? O.o

su -c "yum upgrade"

or (picture attached)

The update manager first downloads repository infomation (which is small, like you said, around 4MB.) then refreshes it and downloads then installs the updates. Sounds like you'd prefer a less updated and more stable system if you consider that too much and don't want to update often. 
Thanks for your reply Spice Weasel. As I mentioned (You may read my article from first to end buy anyway), first it was 4MB but I tried second time and yes, it became 400MB to update.> There are lots out there, Scientific Linux, CentOS, Debian or Ubuntu.
Maybe I try CentOS. But decided to try LinuxMint too.> 
The no OpenOffice.org is one of Fedora's policies, they include complete desktop environments and try to keep them as unmodified as possible for a consistent experience. AbiWord and Gnumeric are part of GNOME, whereas OpenOffice isn't.
Oh, It's not good. I also seen that they are using default gnome them as well.
I mentioned a lot of problems above. But the main problem for me to try another distro is whether it creates a list of needed packages to download or not? This is very important to me. Is it possible in Fedora and other RPM based distros?
Thanks

---

### Post by ario on 2010-11-02
> **Refalm said:**
> Have you tried [Linux Mint](http://www.linuxmint.com)? It's supposed to be an enhanced version of Ubuntu.

Will try it maybe tomorrow.

---

### Post by 3Miro on 2010-11-02
Fedora does have some issues with their graphical software manager. I think most of the fedora guys use "yum" form the command line anyway.

There is Open Office for Fedora. The default Ubuntu install includes OO as well as the community repository. Most of the Ubuntu software is maintained by the community not Canonical. In the same manner, most of Fedora's software is in the RPM Fusion repository, which for them is not activated by default. Google RPM fusion for the commands to set it up, that will unlock a ton of extra software. Also after upgrade (su -c "yum upgrade") many of the glitches of the graphical software manager go away (no all however).

As far as being easy to use, nothing beats the Ubuntu family. Fedora is the next thing to it, but not quite there. I am afraid that any other distro will seem even harder for you.

---

### Post by ubunterooster on 2010-11-02
> **ario said:**
> Will try it maybe tomorrow.
Please do. :D

---

### Post by TBABill on 2010-11-02
I tend to disagree with Fedora being #2 in ease of use next to the Ubuntu family. This can start a flame war and that is not the intent. I believe there are a few fairly easy distros to keep up to date and do things graphically. PCLinuxOS and LinuxMint and Ubuntu all provide easy updating and configuration, but I can say the only command line I ever used in PCLinuxOS was to configure CPU Frequency Scaling with CPUFREQ, but even that can be done graphically. And so easy to update....Synaptic....click reload, click mark all upgrades, apply, enjoy.

---

### Post by 3Miro on 2010-11-02
> **TBABill said:**
> I tend to disagree with Fedora being #2 in ease of use next to the Ubuntu family. This can start a flame war and that is not the intent. I believe there are a few fairly easy distros to keep up to date and do things graphically. PCLinuxOS and LinuxMint and Ubuntu all provide easy updating and configuration, but I can say the only command line I ever used in PCLinuxOS was to configure CPU Frequency Scaling with CPUFREQ, but even that can be done graphically. And so easy to update....Synaptic....click reload, click mark all upgrades, apply, enjoy.

There is no reason to flame, so lets just be objective. When you say that you disagree with Fedora being #2, do  you mean that Fedora is easier than Ubuntu or that PCLinuxOS is easier than Fedora. To be honest I have almost no experience with PCLOS, it was nice to pick the drivers automatically, I got 3D effects off the LiveCD, however, my only attempt to install it failed due to Lilo vs Grub vs Initrd issues. I curently have 5 distros installed on my desktop computer so I try to have only one bootloader installed and not overwrite it when I put a new distro on. I should probably give PCLOS another chance.

The only issue with Fedora that I had was the graphical software utility, which worked fine once it was updated and had RPM fusion installed.

The main advantage of Ubuntu is that it assumes that users have no prior experience not only with Linux, but with computers in general. Depending on your philosophy, this may be a good or a bad thing, however, for people new to Linux it is definitely good. All other distros fall short of that.

---

### Post by krishnandu.sarkar on 2010-11-02
I use Ubuntu, Fedora, CentOS, Arch :)

Like Ubuntu most. Arch is also good too.

Planning to try out OpenSUSE and Mandriva :P

---

### Post by TBABill on 2010-11-02
@3Miro, my disagreement was aimed at the perspective of a new user trying to use Fedora. Experienced users may love the distro and be able to adeptly manage the system, tweaks, breaks, etc., but it is not a distro a new user to Linux would have the easiest time making the switch with. I was more stating it to computer users in general who may well know how to get the things done with a computer that they are accustomed to doing, but who may not be as skilled in fixing an issue when it arises. I'm thinking along the lines of my parents, kids, wife, co-workers not in the IT field, etc....people who know how to do their work with their software, but have little knowledge when things fail. In that respect Fedora can be a challenge compared to some of the more hand holding distros like Mint, PCLinuxOS, Ubuntu and even openSUSE. Fedora Fusion was even created to take the Fedora base and simplify it by incorporating some of Mint, Fedora and others to make a system more friendly to that new user.
 
I don't disagree that Fedora is a great distro. My only disagreement was that it is not easy to learn on as some others. I personally want to give Fedora 14 a shot since I have not used it since Fedora 12. Maybe I'll do that one evening soon.

---

### Post by 3Miro on 2010-11-02
We don't have much of a disagreement, if at all. We both think Fedora is less suitable for new users than Ubuntu. Maybe PSLOS is better than Fedora, I cannot really judge. I installed OpenSUSA once and it broke X when it was supposed to install the proprietary ATI driver. I didn't bother to try and fix it. I am not a new user so my 30 minutes of Susa experience should point that it isn't that good either (I have not tried ATI under Fedora, so I don't know if it would have been better).

Basically I hold the position that when it comes to users new to Linux, ubuntu and family is by far the best choice.

---

### Post by ventrical on 2010-11-02
I have a Fedora 13 install on a 10GB mini HDD and can run it on any PC in my lab, including through my   USB to IDE converter. It updates just beautiful and the graphics are much smoother than Ubuntu  while using a compiz config. Flash in Firefox also works excellent ,   but then  Meerkat 10.10 works excellent video graphics also.

At least on my Acer Aspire 3620, 1.5GHz. 512MBDDR flash_player looks like HQ 3D!! running Fedora 13.

---

### Post by ventrical on 2010-11-02
Fedora13 updater:

To install programs goto:

System>Administration>Add&Remove Programs:

---

### Post by 3Miro on 2010-11-02
> **ventrical said:**
> Fedora13 updater:

To install programs goto:

System>Administration>Add&Remove Programs:

Straigt from a clean install on two different computers I had this very program work incredibly slow or crash. Even when it does work, it requires couple of attempts to update all the software. After you do it once, it works fine.

The only other issue that I had was that RPM Fusion is not enabled right of hand and many people that are new to Linux will have hard time understanding that.

---

### Post by ventrical on 2010-11-02
> **3Miro said:**
> Straigt from a clean install on two different computers I had this very program work incredibly slow or crash. Even when it does work, it requires couple of attempts to update all the software. After you do it once, it works fine.

The only other issue that I had was that RPM Fusion is not enabled right of hand and many people that are new to Linux will have hard time understanding that.

On this matter I agree.I think I spoke out of turn. I use Fedora 13 sort of like out of my back-pocket.

And also OpenOffice is not installed by default . I must have been thinking of somthing else..

My apologies.

regards

---

### Post by 1roxtar on 2010-11-02
> **ario said:**
> In a rush of hate of Ubuntu tried to get rid of it and install a new distro! My reasons were:

Tried Fedora 13 but:
After installation on virtual box decided to look around main menu. There were:
**[CENTER]NO OPEN OFFICE![/CENTER]**
That was ridiculous but no problem! I will install it by hand. Ran package manager system from Administration menu. It opened a window with a list of software categories on left side. Clicked on each of them but:
[CENTER]**THERE WERE ALL EMPTY LISTS!**[/CENTER]
No problem. I will refresh list. I have a connected NAT Internet in virtual machine trough virtual box and I hope when I install in on my laptop it will detect DSL connection without problem. Chose refresh from first menu on top left. It showed Waiting for authentication and downloaded and downloaded and... nothing happened! I noticed that when I started this application it didn't asked me to enter root password. So this must be because of some privilege problems. I decided to run it by a sudo like command. The command **sudo su** in fedora is **su -**. But I didn't know what is the command to run that GUI application for software management. I tried to run a trick! Right clicked on main menu to edit it, but:
[CENTER]**THERE WAS NO MENU EDIT COMMAND!**[/CENTER]
After about half hour searching Internet found that I must install alacarte for editing menus! It's funny fedora boys!:D
Opened a terminal and ran **yum install alacarte** as root. It installed. Then edited menus and saw that the command for software manager is **gpk-application** or something like this. By the way, ran it as root in a terminal, opened the same window, but this time it showed a progress bar and updated package list just like in synaptic. No more infinite wait for **Authentication** things! After that I decided first try to update my system and then install openoffice.org suit. but:
[CENTER]**THERE WERE NO OPTION TO UPDATE MY SYSTEM!**[/CENTER]
Ok. Still no problem Fedora is not windows and Redhat is not Bill Gates. They are good guys. They created a lot of good stuff for Linux community which we can not forget them. I selected item Update from Administration menu. It refreshed again and downloaded a list from server, after all told me it must update about 4MB of software! I was very astonished! Only 4 mega bytes of software? Ok. Go on... . It downloaded, installed and suddenly the window disappeared! I mean update window just vanished! Started it again and it refreshed again and this time told me that it must download 400 MEGA BYTES of stuff! Ok. This time it is more comprehensible. Its several months since they published Fedora 13 and it needs a bunch of update packages. But I did not have enough time and bandwidth to download them. Decided to find an option like that magical fancy command in synaptic called **Generate package download script**. But there were no option like that. Searched all over Internet, no, not at all! There are no fedora users who likes to update his system all the night using free bandwidth, thus they don't need any **Generate package download script** options for their OS.
Good luck fedora team. Keep going the good work.
I remain Ubuntu ;)

Maybe you just have a crappy computer....:rolleyes:

---

### Post by ario on 2010-11-03
> **1roxtar said:**
> Maybe you just have a crappy computer....:rolleyes:

Maybe...!

---

### Post by ventrical on 2010-11-03
Well I spent the last 24 hours doing a tryout on PCLinuxOS Zen Mini and THAT particular distro is really uncooperative when it comes to explaining how to format the HDD. Then , once installed , firefox just loads up and then just blanks out into the  etherland nowhere to be found.

 So I'm sticking with Ubuntu  for a bit .. but will still try other distros.

And I know I got a bunch of really crappy puters in my lab :)

---

### Post by ario on 2010-11-03
> **ventrical said:**
> Well I spent the last 24 hours doing a tryout on PCLinuxOS Zen Mini and THAT particular distro is really uncooperative when it comes to explaining how to format the HDD. Then , once installed , firefox just loads up and then just blanks out into the  etherland nowhere to be found.

 So I'm sticking with Ubuntu  for a bit .. but will still try other distros.

And I know I got a bunch of really crappy puters in my lab :)

Keep trying man. Have you ever find something like "Create package download script option" of Deb based distro's with synaptic, for RPM based ones?

---

### Post by ventrical on 2010-11-04
> **ario said:**
> Keep trying man. Have you ever find something like "Create package download script option" of Deb based distro's with synaptic, for RPM based ones?

I'm not sure. But I recall that with Fedora 13 when I installed AVG anti-virus. In my case it borked up due to user inability. This also happened with Ubuntu 8.4 Hardy Heron about 2 years ago. I downloaded the AVG package , installed it using synaptic package manager and then nothing would happen. I would say to myself .. "where is it" (expecting that it would be in the drop-down menu (doh!)). So I put 8.4 on the shelf for a year and went back to windows XP and malware removal of all kinds of dirt , filth and malware -- ya know .. worms , viruses and trojans .. and so I got sick of it and then went back on a search for alternative OSes and decided to give Lucid Lynx a try.

Surprise, surprise , SURPRISE!!! compiz and Firefox just took off like I  could not believe and then with VBox , I was sold on Ubuntu.

 I plan to continue trying different distros .. no giving up here .. and it is always a joy to revive an old robot from the scrapheap now and again :)

  It's been a tough learning curve for me because I've been an MS customer for over 20 years, but I'm getting there real fast !

  One thing I have to say is that , from my own scope of things, if something doesn't work with a Linux distro then it's probably  90%  due to user_inability and thats a tough pill to swallow - but , hey , then again ... it's an honesty program.

regards..

---

### Post by cacycleworks on 2010-11-04
Great thread .... reminds me of when 9.10 ruined my life. I was on a Dell D630 and it just didn't work well at all. 

I tend to never update my main work desktop and then will perform a clean install of something new-ish while leaving /home untouched (on its own partition).

What I do suggest for people wanting to experiment, play, etc, is to have a couple of bootable USB sticks. I have slitaz on one and knoppix 5.??? on another. A third one is my ubuntu stick and #4 is for the install I'm experimenting with (or I'll blow away the knoppix one to do this). These two are my computer chainsaws. They let me fix just about anything. 

With all the huge hard drives today, when shopping around for a new distro, put 4 or 5 50G partitions and install trial OSs to these. **Then I use the ubuntu USB to boot to my original working ubuntu install on the hard disk and re-install grub to it!** This way, you keep a LOT of usability and reliability while experimenting.

BTW slitaz boots wicked fast. I just wish I could admin it more like ubuntu... i'd probably leave and never come back. I can boot a system to the desktop in slitaz faster than firefox loads in ubuntu 10.10 64bit! Of course, what's there to admin in 10.04? Everything seems to work out of the box...

:) Chris

---

### Post by ventrical on 2010-11-04
Thats right on with the USB boots. I have a 8 GB and a 16 GB plus a bunch of HDs with other distros that work through the USB to IDE converter cable. I bought the USB&IDE cable for Windows thinking I could use my old HDs for backup but it was useless under Windows XP.  Ubuntu 10.4 turned that little converter into gold (plus all my USB sticks also.)

  But one thing I have to try is a back-up of the /home directory and then try a fresh install. But so far I have had minimal problems with  10.4 and 10.10 and problems I do have seem to get resolved real quick.

  It's a real break for me not having to  worry about malware and viruses and spending 80 percent of my PC downtime on working malware removal.

  Ubuntu really  makes PCeeing enjoyable again. And the stability of Firefox is absolutely amazing. These Ubuntu distros really get me out of the cage, hands free, malware straight-jacket off and a real opportunity to study in real time how a solid and secure kernel really works !!

---

