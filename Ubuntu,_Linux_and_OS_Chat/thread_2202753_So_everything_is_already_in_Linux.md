---
title: "So everything is already in Linux?"
date: 2014-01-30
forum: Ubuntu, Linux and OS Chat
---

### Post by maazmahmood on 2014-01-30
Was reading some comments to an article, and this is what I gathered, that EVERYTHING, or just about, is already on Linux, it just has to be installed. Like this guy made a guide to install nvidia drivers, and all he had to do was write in the commands to install, how does that work, and how is Ubuntu not much larger if that's true? Like if every software was already there, then shouldn't the .iso file be like huge? And what is the general command to install something, like let's say I wanted to install chrome.

---

### Post by vasa1 on 2014-01-30
> **maazmahmood said:**
> Was reading some comments to **an article**, ...
When you refer to something, it would be nice to post a link if available.

---

### Post by maazmahmood on 2014-01-30
[http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml](http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml)

sorry

---

### Post by SeijiSensei on 2014-01-30
> **maazmahmood said:**
>  Like if every software was already there, then shouldn't the .iso file be like huge? And what is the general command to install something, like let's say I wanted to install chrome.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by deadflowr on 2014-01-30
Normally I would advise anyone interested in installing programs on Ubuntu to simply start out by using the software center.
A few programs, like google-chrome, are not available within the Ubuntu repository system.
And quite a few programs are not available on linux, natively.
So I would say that not everything is already on linux.
But there are some great-to-okay alternatives for most of them.(but not all)

---

### Post by maazmahmood on 2014-01-30
Then, and I don't mean this in an accusing way, why do people say Linux is all faster and stuff. Again, I've never really used one for longer then 15 minutes, but like I get how just entering a command, and you can have some repositories installed is awesome, but what about stuff you download, can you just download the files, then enter the command to install them? 

Also, is there a general command to remove/uninstall? Just in case there are some stuff I download that aren't quite ready for linux yet.

---

### Post by jshanks24 on 2014-01-30
You would be better off installing software from the software center than running commands with your experience level. You can find a tutorial on how to use the Ubuntu Software Center [here]("http://thelinuxstartup.com/2014/01/30/managing-software-in-ubuntu-13-10/").

---

### Post by deadflowr on 2014-01-30
> **maazmahmood said:**
> Then, and I don't mean this in an accusing way, why do people say Linux is all faster and stuff. Again, I've never really used one for longer then 15 minutes, but like I get how just entering a command, and you can have some repositories installed is awesome, but what about stuff you download, can you just download the files, then enter the command to install them? 

Also, is there a general command to remove/uninstall? Just in case there are some stuff I download that aren't quite ready for linux yet.


I think you misinterpret what the repositories are.
You don't(normally) install a repository, but rather you pull the packages from a repository.

And yes, you can download packages and then install those packages at a later time.
and to remove packages, it is the same command as installing them, except change the word install to remove.

Here's some idea of [apt-get]("https://help.ubuntu.com/12.04/serverguide/apt-get.html") and [more apt-get]("https://help.ubuntu.com/community/AptGet/Howto")

---

### Post by Mark Phelps on 2014-01-31
> EVERYTHING, or just about, is already on Linux, it just has to be installed.

WOW -- it's a big leap (actually, a ridiculous one) from finding one set of video drivers to using that to claim that EVERYTHING else is available.

What Linux does have is LOTS of apps that are available for free -- and some folks might interpret that as EVERYTHING.

But personally, I thinks it's a bad idea to "hype" Linux as folks then expect EVERYTHING, and when that does not happen, they become very disappointed.

---

### Post by mörgæs on 2014-01-31
I guess reading the [Ubuntu Manual]("http://ubuntu-manual.org/") is a good first step. It describes many of the differences from Windows. Please begin here.

Linux does not have everything, but unlike Windows it has a lot of drivers built-in from the beginning. Windows people are used to hunt here and there for drivers and download strange stuff, but that's normally not the case for a Linux distro. That's why a live boot often works without any modifications. 

Some companies do not provide open-source drivers. These drivers have to be added after the installation.

---

### Post by oldfred on 2014-01-31
Actually chromium is in repository. So you can install from Software Center, synaptic or command line.
sudo apt-get install chromium-browser
> Chromium serves as a base for Google Chrome, which is Chromium rebranded (name
and logo) with very few additions such as usage tracking and an auto-updater
system.


       Linux is not Windows:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Some software in Linux is better than Windows, most of the software you use a lot is just as functional, but different and some software not as good, but may be good enough depending on your needs. Special software like Adobe products, CADD, Business accounting and others are often not compatible with major Windows software that everyone uses, so Linux may not be for everyone all the time, but still could be used with dual booting.

On hardware side, it often takes 6 months for Linux to reverse engineer & catch up with new hardware. So if a very new system you need the newest version of Linux which may work, but the next version may have more fixes & work better. Some vendors are better than others in working with Linux.

---

### Post by grahammechanical on 2014-01-31
The Ubuntu ISO/Install image is too large to fit on a CD. We now need a DVD but that image does not contain every Linux application nor does it contain proprietary video drivers such as the Nvidia video driver even though there is plenty of room left on the DVD. When we install Ubuntu get a default set of applications that is considered sufficient as starting in point. We can remove these applications and we can install other applications according to our choice and we can do this without using commands because we have a utility with a graphical user interface (Ubuntu Software Centre).

We can also install proprietary video drivers without needing to use a command. The Additional Drivers utility does that for us. Actually we can have proprietary video drivers and proprietary audio and video codecs installed during the Ubuntu install process simply by ticking a box during the install process. Those drivers are then downloaded from servers on the Internet.

If we do not tick that box we get an open source video driver that is very good. So, in a simple sense Linux has driver modules available for the hardware. That is not the same as saying that Ubuuntu comes with every application available. An install of Ubuntu is best done with an Internet connection then the installer can download from servers on the Internet and this avoids needing an unthinkably large ISO image.

Regards.

---

### Post by RadicaX on 2014-01-31
> **maazmahmood said:**
> Then, and I don't mean this in an accusing way, why do people say Linux is all faster and stuff. Again, I've never really used one for longer then 15 minutes, but like I get how just entering a command, and you can have some repositories installed is awesome, but what about stuff you download, can you just download the files, then enter the command to install them? 

Also, is there a general command to remove/uninstall? Just in case there are some stuff I download that aren't quite ready for linux yet.

Often people say it is faster, because it lacks things slowing it down. Like there is not often a need to install an anti-virus, but rather it is better to use good security measures (Firewall, browser add-ons, etc). Also since malware is not prevalent on Linux, it is not bogged down by it. I believe the way it also handles files helps also. I have installed a few programs, but am still booting under 20 seconds, even on a 8 year old machine, better than most of my friends. 

Linux in no way has everything, as quite a few have pointed out. And sometimes you have to wrestle with things to get it to work with certain hardware. A lot of people do not like to do any extra work for their computers either, even with how easy Ubuntu is, you may have to read and troubleshoot, and you are not going to just have a hotline to call. Linux is great at what it does, and if you use Gimp for example, over photoshop, it is not that hard switching over. But often, there are programs that people are so tuned to, they are locked into Windows too, photoshop for example, or Microsoft word. Add this on to the fact there are so many choices, it can bother people. Some people like to take their vehicle and modify it, be it from decorations inside, like a little bobble head, or be it something complex like switching out the motor for something more powerful, Linux gives you the chance to do that, this is not really possible on Windows. You can have any Windows "car" so long as it is black...

---

### Post by stalkingwolf on 2014-02-01
While Linux may not have "everything" synaptic package manager shows as of about 30 minutes ago 40301 packages available for download and installation.
I think when someone says linux has everything they are simply saying that the particular version they are talking about has everything installed to give the user basic
functionality after installation.  Things like basic photo editor, browser (many include chrome),office package, audio,graphics and video for most hardware,drivers for printers (i have always used HP),and scanner (since 7.10 as i recall maybe 8.04).

In short a functioning system "out of the box".   Then you can customize to your hearts content.

---

### Post by Don_Stahl on 2014-02-01
1. So far all the drivers I've needed for graphics, sound, wireless connectivity, wireless mouse, USB hard drives, and USB optical drives has been in Ubuntu already. So "everything" I needed to get my system up and running was already there. Plug it in and watch it go. 

2. As far as software: 

In Windows, you can download a variety -- a HUGE variety -- of programs from places like TuCows, SoftPedia, MajorGeeks, etc. Some programs -- Irfanview and Paint.net, for instance -- are free, stable, and excellent. Others cost money, and/or install as nagware or crippleware. Some even contain trojans or other kinds of virus.

In Ubuntu (and other distributions of Linux), a LARGE variety of programs are linked through software "repositories". All these programs have been evaluated and are free of malware, adware, viruses, etc. Nearly all are free of cost, as well. It's easy to install them using one of the built-in package managers.

And of course Ubuntu (and other distributions of Linux) come with web browsers, office software, video and audio software, and a lot of other commonly used applications already installed. That's true of Windows and Mac as well -- all mature operating systems give the user necessary software in the primary installation package.

Finally, if there are specialty drivers or applications that are not in the distribution package, or not listed in the package manager, there are ways to find and install these anyway. It's similar in concept to side-loading apps for an Android phone.  

So Linux has "everything" in the same sense that Windows has "everything" and Mac has "everything." It has the necessary software and drivers for a standard operating system, and there are ways  to get lots of other software too. 

Does that answer work for you? :P

---

