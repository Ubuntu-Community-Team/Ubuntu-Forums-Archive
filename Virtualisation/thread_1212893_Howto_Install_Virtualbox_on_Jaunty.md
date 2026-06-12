---
title: "Howto: Install Virtualbox on Jaunty?"
date: 2009-07-14
forum: Virtualisation
---

### Post by Malik on 2009-07-14
anyone have a link to something new? Seems like the how to's ive found on the forums are outdated and obselete. Thank You.

---

### Post by Tibuda on 2009-07-14
Open your software sources managers: System > Admin > Software sources.
Open the third party tab, and add this entry:
```
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
```
It will ask you to update the software sources data. Do it. You'll probably get an error message about keys, with a strange key at the end. There's a way to add this key from GUI, but it's too much point-and-click to explain here. Better open a terminal and run:
```
wget -c http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```
Now you just have to install the virtualbox-3.0 package from synaptic or clicking [here]("apt:virtualbox-3.0") if you are using Firefox. You can also use the terminal to install this package:
```
sudo apt-get install virtualbox-3.0
```

Then you have to add your user to the vboxusers groups. You can do it in System > Admin > Users and groups, or in the terminal:
```
sudo adduser YOUR_USERNAME vboxusers 
```

---

### Post by Malik on 2009-07-14
> **danielrmt said:**
> Open your software sources managers: System > Admin > Software sources.
Open the third party tab, and add this entry:
```
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
```
It will ask you to update the software sources data. Do it. You'll probably get an error message about keys, with a strange key at the end. There's a way to add this key from GUI, but it's too much point-and-click to explain here. Better open a terminal and run:
```
wget -c http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```
Now you just have to install the virtualbox-3.0 package from synaptic or clicking [here]("apt:virtualbox-3.0") if you are using Firefox. You can also use the terminal to install this package:
```
sudo apt-get install virtualbox-3.0
```
thanks I did everything you've said to do but I cant find where to open the virtualbox. THe old one was in accessories.

---

### Post by Hospadar on 2009-07-14
before you 
sudo apt-get install virtualbox-3.0

You need to 
sudo apt-get update

Make sure the one you installed before (the Open Source Edition) is uninstalled.

---

### Post by theozzlives on 2009-07-14
It's always been in Applications > System Tools on my computer.

---

### Post by scorp123 on 2009-07-14
> **Malik said:**
> thanks I did everything you've said to do but I cant find where to open the virtualbox. The icon won't be immediately visible ... some install quirk it seems. You have to logout and login again. Or you simply reboot ... overkill, but it will work too. You should then get a "VirtualBox" icon in the "System Tools".

---

### Post by hyperdude111 on 2009-07-14
Why bother with terminal. Get it here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Tibuda on 2009-07-14
> **Malik said:**
> thanks I did everything you've said to do but I cant find where to open the virtualbox. THe old one was in accessories.

I got it in system.

> **Hospadar said:**
> before you 
sudo apt-get install virtualbox-3.0

You need to 
sudo apt-get update

Make sure the one you installed before (the Open Source Edition) is uninstalled.
When you add a new entry in software sources, it asks you to "apt-get update" in GUI.

> **hyperdude111 said:**
> Why bother with terminal. Get it here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Adding a the virtualbox repository to the software sources, the update manager will prompt you about new versions.

---

### Post by drs305 on 2009-07-14
> **Malik said:**
> thanks I did everything you've said to do but I cant find where to open the virtualbox. THe old one was in accessories.

Take a look in System Tools.

---

### Post by moma on 2009-07-14
Hello

Check also these notes. 
[http://www.futuredesktop.org/virtualization-solutions-ubuntu-9.04.html](http://www.futuredesktop.org/virtualization-solutions-ubuntu-9.04.html)

---

### Post by Tibuda on 2009-07-14
Hey, you have also to add your user to the vboxusers groups. You can do it in System > Admin > Users and groups, or in the terminal:
```
sudo adduser YOUR_USERNAME vboxusers 
```
I'll add it to my first reply.

---

### Post by Shpongle on 2009-07-14
> **Malik said:**
> thanks I did everything you've said to do but I cant find where to open the virtualbox. THe old one was in accessories..

its path is /usr/bin/VirtualBox but if you restart it should appear in system tools

---

### Post by Malik on 2009-07-14
> **drs305 said:**
> Take a look in System Tools.
thanks found it but when I opened it. and started it, it said no bootable media was found and my mouse did not work :(.

---

### Post by Ra-Hoor-Khuit on 2009-07-14
Download the latest PUEL version of Virtual Box from their website and then to install it see this tutorial:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

---

### Post by Malik on 2009-07-14
looks like im in way over my head.

---

### Post by Malik on 2009-07-14
this is damn near impossible not even worth the trouble lmao

---

### Post by TalkHero on 2009-07-14
I've done a bit of reading on this as i am new to Ubuntu. I was going to do a duel boot but thought i may as well see what it is like in a VM first.

First off, if you want anything in the Virtual Box to read files from a USB drive (i have a netbook and so will be installing W7 from a USB drive) you need to get the non Open Source one. It can be found here:

[http://dlc.sun.com/virtualbox/vboxdownload.html#linux](http://dlc.sun.com/virtualbox/vboxdownload.html#linux)

Once it has been installed follow these instructions to get the USB drives working:

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

Then you need to set up the virtual machine, and you should be able to find plenty of help out there on how to do that with a simple google search.

What OS are you wanting to put in the Virtual Box?

---

### Post by Malik on 2009-07-14
> **TalkHero said:**
> I've done a bit of reading on this as i am new to Ubuntu. I was going to do a duel boot but thought i may as well see what it is like in a VM first.

First off, if you want anything in the Virtual Box to read files from a USB drive (i have a netbook and so will be installing W7 from a USB drive) you need to get the non Open Source one. It can be found here:

[http://dlc.sun.com/virtualbox/vboxdownload.html#linux](http://dlc.sun.com/virtualbox/vboxdownload.html#linux)

Once it has been installed follow these instructions to get the USB drives working:

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

Then you need to set up the virtual machine, and you should be able to find plenty of help out there on how to do that with a simple google search.

What OS are you wanting to put in the Virtual Box?
I wanted to put XP, I got a tinyxp iso. The USB instructions still did not work ugh! :(

---

### Post by Malik on 2009-07-14
> **Malik said:**
> I wanted to put XP, I got a tinyxp iso. The USB instructions still did not work ugh! :(
now it says the ntldr is missing when i boot up virtual machine.

---

### Post by tacantara on 2009-07-14
Did you install the 3.0 version, or did you get the recently updated 3.0.2?  I downloaded 3.0.2 last night and it gave me all sorts of trouble, so I reverted to 3.0.
 
If you can't get the program open, you will be able to tell the version by the file name on the package (if you downloaded the .deb package from the website).

---

### Post by Malik on 2009-07-14
> **tacantara said:**
> Did you install the 3.0 version, or did you get the recently updated 3.0.2?  I downloaded 3.0.2 last night and it gave me all sorts of trouble, so I reverted to 3.0.
 
If you can't get the program open, you will be able to tell the version by the file name on the package (if you downloaded the .deb package from the website).
oh snap it is 3.0.2

how do I uninstall that?

---

### Post by tacantara on 2009-07-14
To uninstall VB, open up a terminal and use the command:

```
sudo apt-get remove virtualbox-3.0
```

That should take care of the removal.  Next, download the .deb package for VirtualBox 3.0 from the VirtualBox website and install that on your computer.

I don't know if anyone has filed a bug report on 3.0.2 yet, or if the great folks at Sun are working on the problem (if a problem actually exists - the problems could be caused by any number of things).

Good luck with the installation process.  Generally, VB is easy to install and set up.  Once you have it installed, you'll find it to be worth the effort.  I've been using VB for as long as I've been an Ubuntu user, and it serves its purpose very well.

---

### Post by scorp123 on 2009-07-15
I was under the impression that the version on the web site and in the repos is the very same one??

Version on their web site:
[http://download.virtualbox.org/virtualbox/3.0.2/virtualbox-3.0_3.0.2-49928_Ubuntu_jaunty_i386.deb](http://download.virtualbox.org/virtualbox/3.0.2/virtualbox-3.0_3.0.2-49928_Ubuntu_jaunty_i386.deb)

==> according to the file name that's version 3.0.2 build 49928 we're looking at.

And in the repos:

```
> dpkg -l virtualbox-3.0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  virtualbox-3.0                    3.0.2-49928_Ubuntu_jaunty         Sun VirtualBox
```

==> The version string "3.0.2-49928_Ubuntu_jaunty" indicates that this is the same version as on the VirtualBox web site.


So why is OP supposed to remove the version he installed from the repo and then install the version from the web site? It's both the same software ....

---

### Post by TalkHero on 2009-07-15
> **Malik said:**
> oh snap it is 3.0.2

how do I uninstall that?


No need. I got Windows 7 installed on my Acer Aspire One in Virtual box with no problems at all last night. 

USB, sound and network all work, and i even got the res down to 1024*600.

---

### Post by scorp123 on 2009-07-15
> **Malik said:**
> now it says the ntldr is missing when i boot up virtual machine. Sounds like a broken virtual machine. Installing and re-installing VirtualBox will hardly change anything about that.

---

### Post by Malik on 2009-07-18
> **scorp123 said:**
> Sounds like a broken virtual machine. Installing and re-installing VirtualBox will hardly change anything about that.
was this a joke? lol

---

### Post by Michaelg14 on 2009-07-18
Not a joke.  VB keeps its virtual machines in a seperate place from the actual software.  Reinstalling the software would have no effect on the VMs.

I suggest that you burn your xp.iso onto a CD and have that in the reader when you start Virtualbox.  It has to install an operating system just like any other computer.

---

### Post by tacantara on 2009-07-18
> **scorp123 said:**
> I was under the impression that the version on the web site and in the repos is the very same one??

Version on their web site:
[http://download.virtualbox.org/virtualbox/3.0.2/virtualbox-3.0_3.0.2-49928_Ubuntu_jaunty_i386.deb](http://download.virtualbox.org/virtualbox/3.0.2/virtualbox-3.0_3.0.2-49928_Ubuntu_jaunty_i386.deb)

==> according to the file name that's version 3.0.2 build 49928 we're looking at.

And in the repos:

```
> dpkg -l virtualbox-3.0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  virtualbox-3.0                    3.0.2-49928_Ubuntu_jaunty         Sun VirtualBox
```==> The version string "3.0.2-49928_Ubuntu_jaunty" indicates that this is the same version as on the VirtualBox web site.


So why is OP supposed to remove the version he installed from the repo and then install the version from the web site? It's both the same software ....

I merely suggested that the OP might consider reverting to 3.0 to get VB working again.  I had problems with 3.0.2 myself.  The OP confirmed that he'd installed 3.0.2.  Version 3.0 is still available on the website.  I know this because that's where I downloaded it from when I had to revert.  There is a link on the downloads page that will allow you to access previous versions of VB.

---

### Post by ysNoi on 2009-07-22
Thanks for this thread...! Awesome...! :popcorn:

---

### Post by ramnarayan on 2009-08-06
> **danielrmt said:**
> 
Then you have to add your user to the vboxusers groups. You can do it in System > Admin > Users and groups, or in the terminal:
```
sudo adduser YOUR_USERNAME vboxusers 
```

I don't understand this - is this to be done on the host system or the guest system ??

Pt. of ref. I just installed virtualbox on my Jaunty System and i cannot get USb devices to work - they appear greyed out and i am quite sure that the closed source edition is installed and am wondering if this is because the guest system does not have the right permissions.

would appreciate the help

thanks
ram

---

### Post by RED Lemming on 2009-08-06
Okay I had a slightly older version of Virtual Box when I read your post, so I thought I'd have a play, and this is what I did....ish:


[LIST]
[*] Firstly go to: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
[/LIST]

[LIST]
[*] Have a look at what it says there, if your new it may not mean much, but look and see if anything makes sense. (and before anyone comments, yes I know this is a bit of a mash-up of GUI and terminal and it would be easier if it was all done in the terminal, but why not use the GUI if its been made....?)
[/LIST]
 
[LIST]
[*] Copy the appropriate lines eg: > deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
[/LIST]

[LIST]
[*]Go to System>Administration>Software Sources.
[/LIST]
 
[LIST]
[*] In the Software Sources box go to the Third Party Software Tab.
[/LIST]
 
[LIST]
[*] Click the Add button.
[/LIST]
 
[LIST]
[*] Paste the line you copied eg: > deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free(make sure there isn't a funny character at the end, the last character should be the "e" from "free").
[/LIST]
 
[LIST]
[*] Click okay. Check the new source is in the list.
[/LIST]
 
[LIST]
[*] Close Software Sources, let it refresh/check when it prompts (it should prompt).
[/LIST]
 
[LIST]
[*] Back on the web page where it is written: > The Sun public key for apt-secure can be downloaded here. You can add this key with  Right click on the "here" link and save as. Leave the title default, save it to your home folder.
[/LIST]

[LIST]
[*]Go to Applications>Accessories>Terminal
[/LIST]
 
[LIST]
[*] Type in the line as it says on the website:```
sudo apt-key add sun_vbox.asc
```
[/LIST]
There are some choices to make while you install this and the chances are it'll make any VM you have in existence go wrong (or even more wrong if they are already wrong), so be warned. Any old virtual machines may still be accessible using an old snapshot, but if you have a damaged .dll (especially if it is hal.dll or something like that...) it would be best to start afresh.


[LIST]
[*] In the terminal type: ```
apt-get install virtualbox-3.0
```(you may have to add sudo to the front of that if it asks for you to be root).
[/LIST]

[LIST]
[*]Twiddle your fingers....
[/LIST]
  
[LIST]
[*]Eventually it should all be nice and installed :-)
[/LIST]
 
To make a new virtual machine start up VirtualBox (it should be under Applications>System Tools), Click new. A wizard should guide you through the process....
I have checked my VM all have the ability to link to my USB devices.

Was that any use? If I got a little side tracked then apologies :-)

---

