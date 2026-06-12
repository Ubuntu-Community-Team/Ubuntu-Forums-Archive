---
title: "VirtualBox OSE+Lucid Lynx host+Win7 guest: jawaw + acrobat pro 9 (not enough space)"
date: 2010-12-14
forum: Virtualisation
---

### Post by astrobob.tk on 2010-12-14
Hello guys,

I've been using virtualization for a short time & need your help in 2 issues:

1) I have a software written in Java (purely). It works on Lucid but cannot run on the Win7 virtual box. Everytime I try it, I am given an error that I need to install "javaw". I searched online but couldn't find an answer to my problem.

2) i set the harddisk for this box as an expandable hdd of a total 'virtual size' of 20 GB. Currently the 'actualy size' (used) is 11.58 GB. The problem arises when I try to install Adobe Acrobat Pro 9, I am confronted with the following (image):
 
[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7124[/IMG]

How can this be solved ? & Why exactly is it occurring ?

---

### Post by astrobob.tk on 2010-12-17
anyone ?

---

### Post by CharlesA on 2010-12-17
Verify that the virtual drive you created is actually 20GB in size.

Other then that, you could try cloning that drive to a larget virtual drive and then extending the partition, but that might be a bit iffy.

---

### Post by astrobob.tk on 2010-12-17
> **CharlesA said:**
> Verify that the virtual drive you created is actually 20GB in size.

It is indeed 20GB, but I raise your attention that its dynamic (is that how it's called ?)

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7151[/IMG]

> Other then that, you could try cloning that drive to a larget virtual drive and then extending the partition, but that might be a bit iffy.I don't quite get what you mean, but in any case, I prefer to keep the current drive. I believe there must be a way coz I have 9 GB left. Its 20 & i have used 11.

---

### Post by CharlesA on 2010-12-17
What does Disk Management in Win7 say?

---

### Post by leuribe2 on 2010-12-17
> **astrobob.tk said:**
> 

1) I have a software written in Java (purely). It works on Lucid but cannot run on the Win7 virtual box. Everytime I try it, I am given an error that I need to install "javaw". I searched online but couldn't find an answer to my problem.



Try reinstalling Java JDK inside your Win 7 VM...

> **astrobob.tk said:**
> 

2) i set the harddisk for this box as an expandable hdd of a total 'virtual size' of 20 GB. Currently the 'actualy size' (used) is 11.58 GB. The problem arises when I try to install Adobe Acrobat Pro 9, I am confronted with the following (image):
 
[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7124[/IMG]

There's no image or at least I can't see it... if you could write down what the system pops when you're trying to install Adobe, I'd appreciate that... :-\"

---

### Post by CharlesA on 2010-12-17
The installer basically thinks that the drive is only 11GB (with 900MB free), instead of 20GB.

---

### Post by astrobob.tk on 2010-12-18
> **leuribe2 said:**
> Try reinstalling Java JDK inside your Win 7 VM...

I already tried that [Java Se Runtime Environment 6.0]; same result :(
Actually the problem is solved now. What I was doing is trying to launch the software from the shared folder; the folder shared between the virtual box & lucid. It was giving me another error
> Could not find the main class: 
de.lehmannet.om.ui.navigation.ObservationManger. Program will exit.were observation manager is the software. I thought why not try it after copying the software folder to the Win7 desktop ? This solved the problem; it launched :D


> There's no image or at least I can't see it... if you could write down what the system pops when you're trying to install Adobe, I'd appreciate that... :-\"the image i attached is a screenshot of acrobat's installer. Its is here were I can't proceed anymore due to "memory". No other "pops". Its acrobat not the system that is not allowing the installation to proceed.

---

### Post by astrobob.tk on 2010-12-18
> **leuribe2 said:**
> Try reinstalling Java JDK inside your Win 7 VM...



There's no image or at least I can't see it... if you could write down what the system pops when you're trying to install Adobe, I'd appreciate that... :-\"

> **CharlesA said:**
> The installer basically thinks that the drive is only 11GB (with 900MB free), instead of 20GB.

that's what I thought

---

### Post by astrobob.tk on 2010-12-28
so how can i make the acrobat installer recognize that there's enough space ? is there a way instead of changing the disk ? in case i have to change the disk, its evident that ineed to reinstall the virtual box right (i mean Win 7 here)?

---

### Post by CharlesA on 2010-12-28
You never posted what Disk Management in Win7 says the size of the disk is.

---

### Post by astrobob.tk on 2011-05-23
> **CharlesA said:**
> You never posted what Disk Management in Win7 says the size of the disk is.

Well the size was smaller than what virtualbox assigned.

Anyways, Its been a long time since then; i already removed the hard disk but am now facing problems after upgrading virtualbox. I upgraded it to 4.0.4_OSE r70112

The main problem is that when creating a new hard disk (whether fixed or dynamic), It hangs on zero. I tried this several times & nothing new :S

---

### Post by CharlesA on 2011-05-23
Try using the version from Oracles's site - purge OSE and install the version here:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by astrobob.tk on 2011-06-01
> **CharlesA said:**
> Try using the version from Oracles's site - purge OSE and install the version here:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

It is what I've used :S

Moreover, is there a ppa to add to automatically update the version instead of removing & reinstalling it ? (is it the deb's on the page you linked ?)

thanks

---

### Post by CharlesA on 2011-06-01
> **astrobob.tk said:**
> It is what I've used :S

Moreover, is there a ppa to add to automatically update the version instead of removing & reinstalling it ? (is it the deb's on the page you linked ?)

thanks
If you add the repo per the instructions on that page. That'll allow you to upgrade to newer versions without uninstalling the old versions first.

---

### Post by astrobob.tk on 2011-06-04
> **CharlesA said:**
> If you add the repo per the instructions on that page. That'll allow you to upgrade to newer versions without uninstalling the old versions first.

I did that yesterday & tried it twice (once yesterday with Win7 -30GB fixed- & once just now with Sabayon5 -8GB fixed-; of course i didn't insert any disk to install yet). I am always confronted with this:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7902[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7901[/IMG]

When i hit the cancel button, I get this (which also hangs without actually cancelling)

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7903[/IMG]

and in top i see:

```

S %CPU %MEM    TIME+  COMMAND
S   99  0.2   6:29.94 VBoxSVC

S    2  0.9   0:13.32 VirtualBox
```Once this happens (i.e.; hangs when creating the disk), the fan keeps on running (constantly) even after I kill the process "VBoxSVC" which when killed leaves
```

S %CPU %MEM    TIME+  COMMAND
Z   98  0.0  15:35.18 VBoxSVC <defunct>
```under top & closes the window (in the 3rd figure) to give the following error:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7904[/IMG]

The fan doesn't stop until the system is rebooted.

---

### Post by CharlesA on 2011-06-04
Hrm. This sounds like something that might be better to post over on the virtualbox forums.

Does it do the same thing if you try to create a dynamic disk?

---

### Post by astrobob.tk on 2011-06-04
> **CharlesA said:**
> Hrm. This sounds like something that might be better to post over on the virtualbox forums.

Does it do the same thing if you try to create a dynamic disk?


I did try it earlier but not recently, with the same result.

I just posted it on the forums as you suggested. Here's the link if you wish to follow it [http://forum.virtualbox.org/viewtopic.php?f=7&t=42067&sid=76ee231afdc3819160843a58cc7ec025#p189386](http://forum.virtualbox.org/viewtopic.php?f=7&t=42067&sid=76ee231afdc3819160843a58cc7ec025#p189386)

Thanks for the help :D

---

### Post by CharlesA on 2011-06-04
Hrm. Hope you get pointed in the right direction.

Have you already done a fsck on the drive you are storing the VMs?

---

### Post by astrobob.tk on 2011-06-05
> **CharlesA said:**
> Hrm. Hope you get pointed in the right direction.

Have you already done a fsck on the drive you are storing the VMs?

Never used this command before; would you assist me please ?

Mentioning this, and having just read that the command checks for I/O errors, I think its useful to mention that a few weeks ago I had an init problem which I overcome (by chance); you can check the following thread for details: [http://ubuntuforums.org/showthread.php?t=1751541](http://ubuntuforums.org/showthread.php?t=1751541)

---

### Post by CharlesA on 2011-06-05
I wonder if that might be part of the problem.

Run this then reboot:

```
sudo touch /forcefsck
```

---

### Post by astrobob.tk on 2011-06-05
> **CharlesA said:**
> I wonder if that might be part of the problem.

Run this then reboot:

```
sudo touch /forcefsck
```


Just did that; should I have expected anything besides the boot disk checkup ?

---

### Post by CharlesA on 2011-06-05
> **astrobob.tk said:**
> Just did that; should I have expected anything besides the boot disk checkup ?
Nope. That'll just scan the OS drive.

---

