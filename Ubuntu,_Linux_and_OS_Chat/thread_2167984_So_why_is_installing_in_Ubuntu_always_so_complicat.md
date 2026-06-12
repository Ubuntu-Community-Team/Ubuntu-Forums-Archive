---
title: "So why is installing in Ubuntu always so complicated?"
date: 2013-08-15
forum: Ubuntu, Linux and OS Chat
---

### Post by jonathanp2 on 2013-08-15
I know this is a noob question, and I have been using Ubuntu since 6.04, and multiple Linux Dist. But why is things so complicated in Ubuntu and Linux in general. In mac, an application never is actually installed, but usually just ran from the download, and in windows, it is installed just by clicking install. Why in Linux do you have to rely on Terminal to install things? Using the configure, make, and install command. Why can't things be simply get the file (capable with Linux) and click, install? I know about software center, but we all know that not everything is available there. So almost any user will have to compile files, and get dirty in terminal.

---

### Post by ibjsb4 on 2013-08-15
What isn't available in the software center?

---

### Post by deadflowr on 2013-08-15
I've never had to run configure,make and install commands.
I learned how, but I've never needed to do so in a real situation.

This isn't 1999 anymore, a lot of packages have been built since then to install easily.

---

### Post by Gilad_Pellaeon on 2013-08-15
I've noticed a lot of sites usually show various sudo commands as shortcuts to install various packages in a terminal because it can be more efficient. However if you are more comfortable using the GUI as an example you can use the Synaptic Package Manager to install packages that way. Good example was in Lubuntu I installed a bunch of x screensavers via the package manager and not Lxterminal and it worked just as well. :)

---

### Post by newb85 on 2013-08-15
Indeed.  The configure, make, install procedure is only necessary if the packages aren't pre-compiled.  Non-pre-compiled programs aren't really any easier to install on Windows or Mac.

Installing from a repository or PPA is quite easy using a GUI program like Synaptic or Ubuntu Software Center.  For that matter, it's not difficult using apt-get in the terminal, though it might seem a bit cryptic at first.

---

### Post by Irihapeti on 2013-08-16
*Thread moved to **Ubuntu, Linux and OS Chat**, since it is not a request for support.*

---

### Post by MadmanRB on 2013-08-16
I too ask what program are you trying to install that cannot be simply installed via the repos?
Ubuntu is only as complicated as you want it to be.

---

### Post by mastablasta on 2013-08-16
usually they have a PPA. soemtimes they don't that's true and they offer precompiled binaries for windows. i guess it woudl be hard to offer those for linux since every linux distribution is the same. nevertheless there are usually .deb files one can use if there is no PPA. rarely a compile is actualyl needed. maybe with some drivers.

---

### Post by su:bhatta on 2013-08-16
I've come across a couple of programs that i use for audio production that had to be compiled or had to download deb packages and then use Software center to install, no ppa's available!
If at least there was everything available as deb packages then it would be easier for guys who don't want to be troubled with compiling! 

But compiling, is failsafe, thats what i can say and not very difficult to follow, in case the documentation page of the concerned application lists the dependencies well!

Also, tho' checkinstall is the recommended option, i've found it not always working, i haven't dug deeper into it coz its working with 'make install' & i'd hate to change a winning combination!

A lot of things are not available in Ubuntu Software Center, but then again, all the basic needs of the enthusiast is mostly available in the Software Center....

---

### Post by buzzingrobot on 2013-08-16
If you can't find the software you need in the repos or in a PPA or in  in a deb someplace else, it means the developers have not packaged  it for Ubuntu. Rather than  doing the configure, make, install dance, you  might look into learning how to build your own deb from source. Makes  things more convenient down the road.

The items available in the Software Center are in the Ubuntu repositories.  The Center is just a program for listing and accessing them. Any other program -- Synaptic, for example, or apt-get -- that accesses the same repos, will duplicate that functionality. (The list of repos a system uses is maintained for all such programs in the sources.list and other files in /etc.)

The real advantage of the repository system in combination with these tools is that the software can resolve the dependencies. Linux software applications are seldom packaged as monolithic entities containing every library, etc., needed to get the thing to run. So, the packages in the repositories contain lists of each package's dependencies. Tools like the Center or Synaptic or apt-get are clever enough to know which dependencies are already installed and which it needs to download and install, assuming they're also in the repos.

That's the major problem these programs solve. 

Windows and OS X package software differently and do not use a dependency resolution tool.

But, in all 3 operating systems, the actual installation of a package, once the archive is on the target machine, amounts to following an internal script that copies the files to the correct locations.  That's what's happens when you click an icon on OS X or Windows, and exactly the same thing happens when you install something in Ubuntu.  It's just not as obvious to the user.

---

### Post by philinux on 2013-08-16
Never had to compile anything in 6 years of using Ubuntu.

I tend to use synaptic more the SC.

---

### Post by coldraven on 2013-08-16
In Windows you have to update all of your programs manually, one at a time.
If you have missed a security alert for say Adobe Reader then you risk getting malware.
In Ubuntu it is a one click process to update everything.
Which is easier?

---

### Post by jonathanp2 on 2013-08-16
Probably everything. But every now and again you will need to use make. I use alot of command line programs and advanced programs that are not available on software center.

---

### Post by jonathanp2 on 2013-08-16
I had to multiple times with programs that are not standard. Then again, Ubuntu is my main OS, but I also have a less popular Debian OS that I have to use nothing but command line to install. Ubuntu is very user friendly, alot has changed since 6.04

---

### Post by jonathanp2 on 2013-08-16
> **Gilad_Pellaeon said:**
> I've noticed a lot of sites usually show various sudo commands as shortcuts to install various packages in a terminal because it can be more efficient. However if you are more comfortable using the GUI as an example you can use the Synaptic Package Manager to install packages that way. Good example was in Lubuntu I installed a bunch of x screensavers via the package manager and not Lxterminal and it worked just as well. :)

Truthfully I kind of am more comfy with the Terminal. I have the Terminator Emulator, and it is all set up. I do use synaptics to look up packages and uninstall if I dont really know the name (or dont know if there is a caps in the name)

---

### Post by jonathanp2 on 2013-08-16
> **newb85 said:**
> Indeed.  The configure, make, install procedure is only necessary if the packages aren't pre-compiled.  Non-pre-compiled programs aren't really any easier to install on Windows or Mac.

Installing from a repository or PPA is quite easy using a GUI program like Synaptic or Ubuntu Software Center.  For that matter, it's not difficult using apt-get in the terminal, though it might seem a bit cryptic at first.

I perfer apt-get sometimes. Its quicker. I never had a none pre-compiled package in windows or mac. Didnt know there was any.

---

### Post by jonathanp2 on 2013-08-16
> **MadmanRB said:**
> I too ask what program are you trying to install that cannot be simply installed via the repos?
Ubuntu is only as complicated as you want it to be.


I guess. I just take the complicated way? ha.

---

### Post by jonathanp2 on 2013-08-16
> **buzzingrobot said:**
> If you can't find the software you need in the repos or in a PPA or in  in a deb someplace else, it means the developers have not packaged  it for Ubuntu. Rather than  doing the configure, make, install dance, you  might look into learning how to build your own deb from source. Makes  things more convenient down the road.

The items available in the Software Center are in the Ubuntu repositories.  The Center is just a program for listing and accessing them. Any other program -- Synaptic, for example, or apt-get -- that accesses the same repos, will duplicate that functionality. (The list of repos a system uses is maintained for all such programs in the sources.list and other files in /etc.)

The real advantage of the repository system in combination with these tools is that the software can resolve the dependencies. Linux software applications are seldom packaged as monolithic entities containing every library, etc., needed to get the thing to run. So, the packages in the repositories contain lists of each package's dependencies. Tools like the Center or Synaptic or apt-get are clever enough to know which dependencies are already installed and which it needs to download and install, assuming they're also in the repos.

That's the major problem these programs solve. 

Windows and OS X package software differently and do not use a dependency resolution tool.

But, in all 3 operating systems, the actual installation of a package, once the archive is on the target machine, amounts to following an internal script that copies the files to the correct locations.  That's what's happens when you click an icon on OS X or Windows, and exactly the same thing happens when you install something in Ubuntu.  It's just not as obvious to the user.

Very well explained. Thanks. That does make since. I guess we have to be thankful for apt-get and the other programs. :)

---

### Post by jonathanp2 on 2013-08-16
> **coldraven said:**
> In Windows you have to update all of your programs manually, one at a time.
If you have missed a security alert for say Adobe Reader then you risk getting malware.
In Ubuntu it is a one click process to update everything.
Which is easier?

That is a yes and no thing. Adobe usually updates through system updates in windows, but yes some programs you must update manually in the program. BUT the programs that have a security say in your computer always go through update center. Mac is actually less like both. Although your right, in ubuntu the update center does an amazing job in keeping everything up to date.

---

### Post by MadmanRB on 2013-08-16
> **jonathanp2 said:**
> Probably everything. But every now and again you will need to use make. I use alot of command line programs and advanced programs that are not available on software center.


I have only bumped into a handful of apps that needed me to compile them, but they are getting more rare these days.

---

### Post by oldos2er on 2013-08-16
> **jonathanp2 said:**
> Probably everything. But every now and again you will need to use make. I use alot of command line programs and advanced programs that are not available on software center.

Do these programs have names and/or websites? Just curious.

---

### Post by ikt on 2013-08-17
> **oldos2er said:**
> Do these programs have names and/or websites? Just curious.

That's my first thought as well.

---

### Post by newb85 on 2013-08-17
If something isn't available in the Ubuntu repos, I would do some searching for a PPA with it.  If you can find a good one (maintained and trustworthy), not only does it bypass the compilation process, but it lets the high-level package manager handle updates (which you would have to do manually for packages you compile yourself).

---

### Post by su:bhatta on 2013-08-17
Ok, I will list you 1: linuxband ([linuxband.org]("http://www.linuxband.org")), itz a gui for Musical Midi Accompaniment or mma, which itself comes as a deb file! 
Linuxband is also featured in linuxaudio.org 

And it was relatively easy to compile, and i quiet enjoyed doing it since it was a small program with only 5-6 dependencies, and I got a lot of help from 'steeldriver'!

---

### Post by codingman on 2013-08-17
So, Ubuntu is hard? Ubuntu is probably the easiest distros out there.

---

### Post by su:bhatta on 2013-08-18
I've only tasted a few distros, Debian, Fedora, Openbox, Sabayon, OpenMamba, Mint, Elementary OS, Gentoo & Chakra & i've felt Ubuntu to be the easiest among all, and any Debian based distro is better than any other is what i've felt !

Only point was, still today you come across some apps that need to be compiled, but thanks to the help in forums and a little googling it can be done!

---

### Post by OrangeCrate on 2013-08-18
> **jonathanp2 said:**
> I know this is a noob question, and I have been using **Ubuntu since 6.04**, and multiple Linux Dist. But why is things so complicated in Ubuntu and Linux in general. In mac, an application never is actually installed, but usually just ran from the download, and in windows, it is installed just by clicking install. Why in Linux do you have to rely on Terminal to install things? Using the configure, make, and install command. Why can't things be simply get the file (capable with Linux) and click, install? I know about software center, but we all know that not everything is available there. So almost any user will have to compile files, and get dirty in terminal.

Linux isn't hard or complicated, it's just not intuitive. Which means, like anything new, there is a learning curve, which can be steep for some, including, apparently, you. Here's an article to read before you decide to go any further with Linux as your operating system of choice, which you probably won't, but hey, it's an interesting read none-the-less:

**Linux is NOT Windows**

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

And honestly, I find it hard to believe that you used Ubuntu since "6.04", since there wasn't an Ubuntu 6.04. It wasn't released until June of 2006, hence the designation of Ubuntu 6.06 (Dapper Drake).

Macs and Windows PCs are both good choices, if configured correctly, so, good luck with either one of them if you find Linux too complicated.

---

### Post by su:bhatta on 2013-08-18
Loved the article, thanks for sharing !!!

---

### Post by mamamia88 on 2013-08-18
What exactly is so complicated?  Look at it like a menu and you tell the waitress what you want and she'll bring it to you.   It's really simple when you think about it. And there is synaptic which has everything is software center doesn't.

---

### Post by monkeybrain20122 on 2013-08-18
You can install most software form synaptic/software centre/ muon .,, by just checking a box and click "apply", if you want up to date versions chances are you can add a ppa. What is so hard about it?? On the other hand in Windows you go on random websites to download your applications and it is one of the main reason why Windows get infected. There are some odd software that you need to install from source, but that is because the developers didn't make a binary for Linux, nothing to do with the platform. I have seen applications that only provide source codes for any platform, and looking at the instructions compiling in Windows is much more complicated then doing it in Linux (and Mac)

---

### Post by Vanlal on 2014-04-23
Oh! am late :D ! but the subject still relevant. I've read almost all of the comments on your subject, I see not the actual answer for your query! In windows and Mac, we can install applications with "Just Double Click" = JDC. But in Linux(all), we need to use "sudo" or terminal...so and so...bla bla..bla..! also let me tell you all, application manager never makes easy to the users to install their applications, NOW the simple question is "WHY NOT JUST DOUBLE CLICK" and install what ever application we need, not go around terminal..ssss and application manger...sssss bla..bla...bla...

Well, to be honest, I like Linux more than Windows... once the dev guys makes installation process as Windows and Mac, these Linux family would be the FIRST in the entire alien nations...:)

---

### Post by deadflowr on 2014-04-23
> **Vanlal said:**
> Oh! am late :D ! but the subject still relevant. I've read almost all of the comments on your subject, I see not the actual answer for your query! In windows and Mac, we can install applications with "Just Double Click" = JDC. But in Linux(all), we need to use "sudo" or terminal...so and so...bla bla..bla..! also let me tell you all, application manager never makes easy to the users to install their applications, NOW the simple question is "WHY NOT JUST DOUBLE CLICK" and install what ever application we need, not go around terminal..ssss and application manger...sssss bla..bla...bla...

Well, to be honest, I like Linux more than Windows... once the dev guys makes installation process as Windows and Mac, these Linux family would be the FIRST in the entire alien nations...:)


I don't need to use a terminal to install stuff.
I open the software center and click on what I want to install.
Simple as that.

---

### Post by Tar_Ni on 2014-04-23
The software center and the synaptic package manager is all one need to install/uninstall packages.

- The software center to install open-source applications and uninstall them.

- The synaptic package manager to delete proprietary applications (Google Talk, Skype, Chrome ect ect.) and to clean residual of packages left after removal of applications.

I rarely made any command line for that purpose in Ubuntu, Xubuntu or Lubuntu. Since 12.04, Ubuntu is a lot more user-friendly than it used to be. You can download things online (compatible with Ubuntu/Debian, of course) and install the deb. packages right away. No command needed.

---

