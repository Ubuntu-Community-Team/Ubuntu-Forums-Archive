---
title: "Virtual Box Install Failed Attempt(s)"
date: 2009-02-21
forum: Virtualisation
---

### Post by pstefanini on 2009-02-21
I tried installing VirtualBox but when I try to start, I get the following error message:

****
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
***

 I have Hardy 8.04 LTS.  I'm sure it has something to do with the command line entry I made  

sudo apt-get install virtualbox-ose virtualbox-ose-source virtualbox-ose-modules 2.6.24-23-generic

It wouldn't wouldn't load and kept asking for a specific version and I think I may have ended loading an earlier kernel -21 instead of 23.  Naturally, it loaded and asked me to delete a number obsolete files, which I did.  

I've tried a bunch of terminal commands that make me think I've messed things up.  Bottom line I can't describe everything I've done so I'm confused as to how to back out and start over... or 

Should I leave well enough alone and  forget VirtualBox.?  (Maybe this was too ambitious an endeavor this early in my Ubuntu life! Any guidance appreciated (including going back to Windows)

---

### Post by yeats on 2009-02-21
I'm a huge fan of VirtualBox - don't give up unless your computer doesn't have the resources (you need extra RAM and plenty of hard disk space to take full advantage of it).  How did you install to begin with, from the OSE version in the repositories?

---

### Post by yeats on 2009-02-21
Here - take a look at this page:

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

The OSE version is okay (and is free in the software freedom sense) but the non-free version has many more functions.  As you see on the page, you can download the .deb file to your desktop, then double click on it to install, or you can add a repository to your apt-get list (Synaptic), which will automatically include any updates.  Either way - give it a shot.  It's a great way to learn about other Linux OS's (and to use Windows inside Linux if you need Windows and don't want to dual boot). :-)

---

### Post by pstefanini on 2009-02-21
Thanks for Responding Chrissharp.  I Googled "Install VirtualBoxl Ubuntu 8.04 and went to UlyssisOnLine and followed these instructions:

Installing Virtual Box in Ubuntu should be an easy endeavor. I have come across several how-to documents that were confusing to say the least. This document will try to simplify the steps involved in installing Virtual Box in Ubuntu 8.04 Hardy Heron. Ok, let’s get started.

1. First, determine the current Linux kernel you are using. Click on Applications > Accessories > Terminal. Type the command:

$ uname -a
Linux penelope 2.6.24-19-generic

The result shows I’m running the Linux 2.6.24-19 kernel.

2. Next, install Virtual Box using the apt-get command. Substitute your current Linux kernel for virtualbox-ose-modules-generic.

$ sudo apt-get install virtualbox-ose virtualbox-ose-source
virtualbox-ose-modules-2.6.24-19-generic **<This is where things went very wrong>**

3. Add yourself to the vboxusers group using one of the 3 commands. Choose only one command. I ran the first one.

sudo gpasswd -a `whoami` vboxusers
sudo usermod -Gvboxusers -a `whoami`
sudo adduser $USER vboxusers

4. Log out of your desktop session by hitting CTRL-ALT-Backspace. When you log in, your group membership will be updated.

5. Congratulations. You have successfully installed Virtual Box.

<Unfortunately, not so.  I went to Applications>System Tools>Virtual Box OSE.  Used the manager... I can give you the specs I entered.  Biggest problem was with the CD, but I think I allocated plenty of RAM and disk space.>

I'm glad you are a fan.  VBox sounds great.  I have a dual boot system with Windows XP Home on one hard drive and Ubuntu 8.04 on a separate hard drive.  I could REALLY make use of XP within Ubuntu because of work applications... but I think Ubuntu is so much cooler, I'm just finding the learning curve difficult if you know what I mean.  Thanks for responding.  I thought the silence meant everyone thought I was dope.  Phil

---

### Post by Therion on 2009-02-21
Tutorial for installing VirtualBox, including how to get past that error message you're getting:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

Get the latest version of VirtualBox from their website, though, don't use the download link in the tutorial.

---

### Post by Mercury_Alpha on 2009-02-21
I had all kinds of trouble with OSE when I attempted to build an update from source. It built okay, but I got pretty much the same errors you did when I attempted to run it. I fixed this by removing the OSE version

```

sudo apt-get remove virtualbox-ose

```

...and installing the non-free "Sun xVM" version. It runs flawlessly. You just have to remember to adjust the video RAM allocated to the VM, because the default is like 8MB. And USB support is not enabled by default.

---

### Post by yeats on 2009-02-21
Hmm - I've never had any trouble installing VirtualBox from the site I linked to, meaning I've never had to get into all the multi-step configurations you two are mentioning.  If you don't mind using free-as-in-beer-not-as-in-speech software, just download the .deb and double-click on it.  You might want to uninstall virtualbox-ose first to avoid needless dependency conflicts, but it's worth a shot.

> I'm just finding the learning curve difficult if you know what I mean. Thanks for responding. I thought the silence meant everyone thought I was dope. Phil

No worries - everyone learns this way - by getting curious and taking risks on learning something new.  In general, non-response on the forums either means that no one knows or that the topic has already been covered in previous (and searchable) posts.  There's no judgment here, as long as you're civil and have reasonable expectations. :-)

---

### Post by pstefanini on 2009-02-21
Thank you all for the help and encouragement.  

I downloaded i386 deb and the package installer indicated "Error: Conflicts with the installed package 'virtualbox-ose'.  I put it on my desktop and tried to uninstall what I've done

Thank you for the instructions on uninstalling.  I used you command  and got this:

philip-desktop:~$ apt-get remove virtualbox-ose
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by LordIshamael on 2009-02-21
you need to run it as root
ie run this:
sudo apt-get remove virtualbox-ose

then enter your password
itll work then

---

### Post by pstefanini on 2009-02-21
Thank you LORD!!!  That worked.... 

$ sudo apt-get remove virtualbox-ose
[sudo] password for philip: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done

The following packages were automatically installed and are no longer required:
  ispell ibritish gimp-help-en libsnmp15 librdf0 libicu38 cupsddk libggzmod4
  libxalan110 libaccess-bridge-java librasqal0 gimp-help-common uno-libs3
  libgmp3c2 python-imaging libggz2 ure cupsddk-drivers libraptor1 libggzcore9
  libwebkitgtk1d iamerican linux-headers-2.6.24-16-generic libxerces27
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-ose
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 20.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 225920 files and directories currently installed.)
Removing virtualbox-ose ...
 * Shutting down VirtualBox host networking...                           [ OK ] 
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
$

Whewww!  Sorry I'm asking so many questions.... Should I remove the packages noted above or should I press on and try installing the i386.deb version? Thank you so much for the help!

---

### Post by Mercury_Alpha on 2009-02-21
> **pstefanini said:**
> Thank you LORD!!!  That worked.... 

$ sudo apt-get remove virtualbox-ose
[sudo] password for philip: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done

The following packages were automatically installed and are no longer required:
  ispell ibritish gimp-help-en libsnmp15 librdf0 libicu38 cupsddk libggzmod4
  libxalan110 libaccess-bridge-java librasqal0 gimp-help-common uno-libs3
  libgmp3c2 python-imaging libggz2 ure cupsddk-drivers libraptor1 libggzcore9
  libwebkitgtk1d iamerican linux-headers-2.6.24-16-generic libxerces27
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-ose
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 20.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 225920 files and directories currently installed.)
Removing virtualbox-ose ...
 * Shutting down VirtualBox host networking...                           [ OK ] 
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
$

Whewww!  Sorry I'm asking so many questions.... Should I remove the packages noted above or should I press on and try installing the i386.deb version? Thank you so much for the help!

Take note that it's just Vbox OSE that's being removed. Bash is just giving you a list of packages that are no longer *required*. The deb file you downloaded will link up with those other packages when you install it.

---

### Post by pstefanini on 2009-02-21
Ok Folks... I got some liquid courage and 'autoremoved' the files indicated.

... I'm going in to install virtualbox-2.1 now... !

I'll let you know how it goes!

---

### Post by pstefanini on 2009-02-21
I got some liquid courage and removed the files as indicated....

I'm going in to install the new virtualbox 2.1 i386.deb package!

I'll let you know what happens!

---

### Post by pstefanini on 2009-02-22
I thought I posted a thank you note and to thank everyone for their great help.  I have VirtualBox working and I'm reinstalling my Windows software.  So far so good.  I couldn't have done it without you and I greatly appreciate the much needed assistance/guidance.

---

### Post by Mercury_Alpha on 2009-02-22
Heh, I got kinda worried when you didn't post an update. Glad to hear that you got it worked out :)

There's also a Virtualization sub-forum here, if you need further assistance or have questions: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

(There are so many links on the main forum page that it's easy to miss.)

---

### Post by yeats on 2009-02-22
> I thought I posted a thank you note and to thank everyone for their great help. I have VirtualBox working and I'm reinstalling my Windows software. So far so good. I couldn't have done it without you and I greatly appreciate the much needed assistance/guidance.

Awesome - happy to help.

---

