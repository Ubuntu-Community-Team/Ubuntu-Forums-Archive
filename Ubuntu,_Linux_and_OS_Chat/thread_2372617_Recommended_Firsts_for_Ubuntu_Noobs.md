---
title: "Recommended Firsts for Ubuntu Noobs"
date: 2017-09-27
forum: Ubuntu, Linux and OS Chat
---

### Post by geekygirl36 on 2017-09-27
Hay all!  :)  I checked out this thread and I know nothing (or nearly nothing) on any topic of the posts!  Being an Ubuntu noob, I don't even have it installed . . . YET!  I was wondering what are the top THREE things you would recommend for a noob?.

Example (from just basic computer knowledge)-

1 - Make sure you have your drivers!  (Very important if you want to use your sound card, video card, internet, etc to it's best ability.)

2 - Backup, backup and don't forget to backup!  (Yes I will have three backups before doing any new install, a new partition or setting up a dual boot and yes I have needed to use the second backup once . . . or twice.)

3 - Make sure you have your prefered applications (mine happens to be Gimp, Notepad++, OpenOffice(Libre), etc) on a USB drive JUST in case for any reason you can't connect to the internet.  (Stranger things have happened and this way you still have a semi-usable computer.

Thank you for all of your experience tips!  ):P

---

### Post by mastablasta on 2017-09-27
> **geekygirl36 said:**
> 
1 - Make sure you have your drivers!  (Very important if you want to use your sound card, video card, internet, etc to it's best ability.)

in linux unlike in windows, the drivers are part of the kernel. newer kernel usually means newer drivers. 

only a few proprietary drivers are added to kernel after install (some are optional). whatever works with linux usually has drivers already available.

i would suggest you try it out in live session first before installing. that way you can painlessly see if all your things work in linux. 

i am not sure why you would need to have applications on USB or what they have to do with internet connection. the mentioned applications are offline applications. if you can't ocnnect ot internet with Ubutnu, what is the point in using it then?

---

### Post by geekygirl36 on 2017-09-27
> **mastablasta said:**
> in linux unlike in windows, the drivers are part of the kernel. newer kernel usually means newer drivers.

That is great!  I didn't know that, thank you! 

> **mastablasta said:**
> i would suggest you try it out in live session first before installing. that way you can painlessly see if all your things work in linux.

Yes I am going to do a live session to see which flavor will work best on my machine considering the hardware.  It was suggested to me that I should try Lubuntu or Xubuntu.

> **mastablasta said:**
> i am not sure why you would need to have applications on USB or what they have to do with internet connection. the mentioned applications are offline applications. if you can't ocnnect ot internet with Ubutnu, what is the point in using it then?

Things go awry with computers, most of us probably know this all too well, so for years I have downloaded my main applications install programs onto a USB just in case I can not connect to the internet for any reason after a new install.  That way the computer doesn't become basically useless because I can still run my word processor, play music through my choice of player or do some photo editing.

---

### Post by vasa1 on 2017-09-27
Moved here since the original post isn't a specific support question.

---

### Post by ian-weisser on 2017-09-27
> **geekygirl36 said:**
> 2 - Backup, backup and don't forget to backup!

These forums have many threads with a querant who backed up faithfully...only to discover that -for whatever reason- they could not restore the data they needed.
Usually the backups worked just fine...but they had chosen to do the wrong *kind* of backup.

Ubuntu is free, and can be easily reinstalled. That's different from Windows (especially older versions), and leads to different backup strategies.

---

### Post by kurt18947 on 2017-09-27
> **geekygirl36 said:**
> That is great!  I didn't know that, thank you! 



Yes I am going to do a live session to see which flavor will work best on my machine considering the hardware.  It was suggested to me that I should try Lubuntu or Xubuntu.



Things go awry with computers, most of us probably know this all too well, so for years I have downloaded my main applications install programs onto a USB just in case I can not connect to the internet for any reason after a new install.  That way the computer doesn't become basically useless because I can still run my word processor, play music through my choice of player or do some photo editing.

You can do the first two from most live distros. I'm not sure about photo editing, I guess it depends on much photo editing capability you need. For instance I find gthumb covers most of my needs but it's no Gimp or photoshop.

---

### Post by mastablasta on 2017-09-27
> **geekygirl36 said:**
> 
Things go awry with computers, most of us probably know this all too well, so for years I have downloaded my main applications install programs onto a USB just in case I can not connect to the internet for any reason after a new install.  That way the computer doesn't become basically useless because I can still run my word processor, play music through my choice of player or do some photo editing.

you can install the whole OS on USB or use a live session with persistency for that.

---

### Post by Bucky Ball on 2017-09-27
Gimp and OpenOffice are available in the package manager. (Notepad is a Win thing? There are alternatives.) In Ubuntu, you generally install apps via a package manager. In Lubuntu (which we discussed in your other thread) I think it is Synaptic Package Manager (don't quote me). It will have one if not. You can also install apps via the terminal. (For instance, 'sudo apt install gimp' in a terminal would install Gimp.)

All apps are kept in software repositories. There are the official Canonical repos and others you can manually add (at your own risk) for specific apps that aren't in the official repos.

So, once you have installed the apps you want, the apps are installed. After that, doesn't matter whether you are online or not. To download the app's actual .deb installer file (like an .exe or app installer file), guess you'd just go to the app's website and download the .deb, if available, or download whatever filetype is available to install the app for future use (although it may be outdated by the time you need to use it). 

As apps are generally installed via repositories, when you update your system it will update all your installed software. No more updating this here and that there and entering long authorisation codes to do so.

Installing apps from the official repo is the way to go, if what you are after is there. Always check before looking elsewhere (for instance, don't go to the Gimp site to install Gimp; just open the package manager and install the perfect version for your Lubuntu release from there). :)

My two cents worth.

---

### Post by sonicwind on 2017-09-27
Welcome to the forum! I'm definately still a Noob two years in, but here are a few from me:

1) Stick with it. Know that there will be times of frustration while learning. The frustration will eventually start turning into satisfaction and knowledge as you overcome obstacles.

2) There's a ton of information online. Try to solve things yourself, then seek help or confirmation on the forum when that fails.

Having said that, there is also outdated (or wrong) information online. Ubuntu has undergone several significant changes just in the short time I've been using it. I started with Ubuntu using Upstart, now it's systemd. Snaps are new since I started. Unity is going away in the next long term release, and that's caused me to have to look into the Gnome desktop to see what's coming. Some commands are the same way (deprecated).

If you do seek help on these forums, you're in a great place. The people here are knowledgeable, patient, friendly and amazing. Help them help you by being clear, tell them what you're working with and what you've tried to solve things yourself. Thank them for their time.

3) One of my favorite things about Ubuntu is that you can boot it from anything. A DVD, USB flash drive, internal or external hard drive. When I first started, I saw people were having a lot of problems with dual booting, so I decided (after trying out the Live DVD) to install my system to my external hard drive in it's USB 3.0 dock. If you're not impatient having to wait maybe tenths of a second for some things, I think its a good option. It works for me.

4) Learn to use the terminal. You will thank yourself in the long run. Just be careful! Small mistakes can become big problems!

5) OMG! Ubuntu! is a great site for keeping up with what's changing in the Linux & Ubuntu world. They are also on Twitter. [URL="http://www.omgubuntu.co.uk/"]http://www.omgubuntu.co.uk/
[/URL]

---

### Post by geekygirl36 on 2017-09-27
Thank you ALL for responding!  :)  Coming from pre of Windows to now, a lot of what you all said seems similar to what I am used to; wrong file types and learning the CMD line/terminal.  The new stuff is great as well, learning that Ubuntu has the (or at least the most common) drivers and I can install programs that I used often (like Gimp) can be installed via repositories.

As with any new OS/program/anything tech it is a learning curve and I am so excited to be finally getting away from Windows as my only OS.  (Let's face it, we will see a day where you can install just about any program on all three OSs; it's just a matter of time and getting there.)  lol

---

### Post by Geoffrey_Arndt on 2017-09-27
Just a few things to add:

>   ALL Intel PC's are by far the most Linux friendly . . . these are the units that have baked-in kernel level support for drivers.   Best scenario is Intel CPU's, Intel Integrated Graphics AND Intel Wireless.    All have "plug & play" with little or no tweaking required.

>   All distros have 1 or on occasion, 2 package managers (Software Installers) . . . very good to use this and NOT look for stand-alone apps off the internet like is done in Windows.

>   Go easy on "change mgmt" . . . . excessively installing, uninstalling, changing themes, etc. UNTIL you get a bit more used to Linux/Unix ways . . . they are considerably different than consumer grade Windows, although not so much different than Business class windows (i.e., what the directory tree looks like, where programs go, where you have write/change permissions, user & group management).      Your /home directory is controlled by you,  the others not so much.

>   No really good reason to install heavy apps like LibreOffice on usb . . . unless that usb is a portable SSD connected via usbv3.

---

### Post by geekygirl36 on 2017-09-27
Thank you!  I personally grew up with Intel, so I do tend to stay with that CPU and the integrated Intel Wireless is great for laptops.  As far as the Graphics card, when building a computer or even buying one, I typically go for Nvidia; but will keep in mind that the Intel is better for Ubuntu when I build my desktop next year.  :)

I will keep my desktop theme changes to a minimum until I get more comfortable with the OS and I don't typically install/uninstall programs much.  I also only suggest installing the program instal file for a new install of an OS just so that the computer can be usable if any bugs appear that can't be quickly fixed and so the computer can still be functional.

---

### Post by Geoffrey_Arndt on 2017-09-27
Nvidia also works well with Ubuntu . . . but requires installation of proprietary drivers . . . which again is easy.    Just not quite as seamless as Intel video.

---

### Post by mastablasta on 2017-09-28
AMD and certain S3 graphics are also well supported. 

however some intels are not. it is hard to know which ones, but generally it is those for which intel outsourced the GPU part of the chip. i amnot sure if they are sitll doing this. in the past they were found under their Atom brand, which i think is now celeron.

Other than Nvidia, AMD, Intel and certain S3 models, others have poor support. yes, there are a few others especially on older desktop PC models.
on older devices AMD has excelent support, where only a few chips do not work as well as in windows (for desktop use). gamin and such is another matter.

---

### Post by geekygirl36 on 2017-09-28
Thank you ALL for your input!  You have been a great source of experience!  :)

---

### Post by Bucky Ball on 2017-09-28
This place is a font of knowledge, experience and opinion. Just prod the forum beast with a question. A beautiful thing. ;)

---

### Post by sonicwind on 2017-09-28
Here are some more resources I found useful when I started.

[https://ubuntu-manual.org/](https://ubuntu-manual.org/) - You can download a free copy of Getting Started with Ubuntu 16.04

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - On the right side you can download a free copy of The Linux Command Line 3rd edition.

[https://linuxjourney.com/](https://linuxjourney.com/) - easy to digest online tutorials for getting started

---

