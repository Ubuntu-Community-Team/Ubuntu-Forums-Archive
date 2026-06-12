---
title: "Ubuntu Suggestion!"
date: 2010-01-21
forum: The Cafe
---

### Post by Ghost Hacks on 2010-01-21
I didn't know where to put this, if this is even the right site lol, but I'm reinstalling Ubuntu Linux and I must say, can you please add an easy "reinstall" option to reinstall the OS to it's original state.  This also would allow a user to save their files and be able to get their OS working again if something goes wrong, as of right now the way I know to do it, is to re-format the partition and mount it as / or root.  This destroys all the data on that partition, can you guys please try to add this.  Other then that the Installer and Partitioner are awesome, I hate the Windows Partitioner but the Ubuntu Linux one is terrific, except for the lack of re-install.

---

### Post by SmittyJensen on 2010-01-21
> **Ghost Hacks said:**
> I didn't know where to put this, if this is even the right site lol, but I'm reinstalling Ubuntu Linux and I must say, can you please add an easy "reinstall" option to reinstall the OS to it's original state.  This also would allow a user to save their files and be able to get their OS working again if something goes wrong, as of right now the way I know to do it, is to re-format the partition and mount it as / or root.  This destroys all the data on that partition, can you guys please try to add this.  Other then that the Installer and Partitioner are awesome, I hate the Windows Partitioner but the Ubuntu Linux one is terrific, except for the lack of re-install.
xandros has this on their install cd.

you could try reinstalling ubuntu from the live cd but without formatting the root partition (/)

---

### Post by Dayofswords on 2010-01-21
be cool if there was a "export perfernces and files" on an installed system, put on one big file, and have an import option during the install.


you know what, look into remastersys

---

### Post by Ghost Hacks on 2010-01-21
I think it's an important feature that should be added to Ubuntu Install, I have no data on install because I messed it up trying to install the video drivers, but for other newbies like me out there this is an extremely important feature, and it could benefit anyone who damages their linux install and wants to save their data.  Would it be feesable the option added to all the ISOs?  Including the Kubuntu and other Ubuntu Distro's?

---

### Post by Dayofswords on 2010-01-21
boom
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

What is remastersys?

[LIST=1]
[*]**It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.**
[*]It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it.
[/LIST]

---

### Post by m4tic on 2010-01-21
You could copy your home folder into your new install, you'll be able to see your wallpapers, firefox bookmarks, themes but not the programs you had

---

### Post by humphreybc on 2010-01-22
A recovery option would be nice. I'm not sure how this would be implemented though... probably the best way would be to create something in aptitude that basically takes a "snapshot" of all your installed packages before it performs any changes. Then if your computer breaks, there could be an option on the LiveCD that would basically just tell aptitude to read the snapshot data, provide you with some recent options so you can choose what to restore to, and then restore everything to how it was at that snapshot - if that meant uninstalling new packages, or installing ones that were autoremoved etc etc..

Obviously sounds a lot like Windows "System Recovery" but I can't think of any other way to do it. It would, in theory, work better than System Recovery because we don't have a nasty registry, and we have more control over installed packages, libraries and dependencies. Plus, aptitude is very powerful.

The other option is to [create an install script like I have]("http://ubuntuforums.org/showthread.php?t=1387434"), and just run it on a fresh install to automagically install your programs again.

---

### Post by t0p on 2010-01-22
> **SmittyJensen said:**
> you could try reinstalling ubuntu from the live cd but without formatting the root partition (/)

Maybe I'm misunderstanding something here: but if you don't format /, what exactly will be re-installed?  Nothing?

In VirtualBox you can take a "snapshot" of the virtual machine's current state before doing something potentially machine-wrecking; then, if you wreck the machine, you can revert to the snapshot.  Something like that would fit the bill, methinks.

---

### Post by juancarlospaco on 2010-01-22
[B]FixIfBroken/Update/Reinstall/Reconfigure ALL packages:

sudo apt-get install -f ; sudo apt-get update ; sudo apt-get autoremove ; sudo apt-get upgrade ; sudo dpkg-reconfigure -phigh -a[/B]

/fixed
:)

---

### Post by eltama on 2010-01-22
The best thing is to have /home on a different partition. That way you can reinstall the operating system without loosing your data. You can even use different OSes and have only one place where you have your data and the configuration files.

---

### Post by pricetech on 2010-01-22
Well, if you bought a computer with Ubuntu on it from a major retailer because you didn't have any choice, it would probably come with a "restore" disk containing everything the OEM wanted you to have.

Sound familiar ??

---

