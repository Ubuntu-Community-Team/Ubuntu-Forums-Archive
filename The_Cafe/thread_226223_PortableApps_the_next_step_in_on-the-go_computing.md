---
title: "PortableApps: the next step in on-the-go computing?"
date: 2006-07-31
forum: The Cafe
---

### Post by Jucato on 2006-07-31
Thanks to an RSS subscription, I came across an article in DesktopLinux.com about the Portable Firefox ([http://www.desktoplinux.com/news/NS4837753834.html/url]), which led me to a project called PortableApps.com ([url]http://portableapps.com/](http://www.desktoplinux.com/news/NS4837753834.html/url]), which led me to a project called PortableApps.com ([url]http://portableapps.com/))

According to the website:
> 
A portable app is a computer program that you can carry around with you on a portable device and use on any Windows computer. When your USB flash drive, portable hard drive, iPod or other portable device is plugged in, you have access to your software and personal data just as you would on your own PC. And when you unplug, none of your personal data is left behind.


Isn't that convenient? I, for one, can just imagine the possible uses and advantages of such a program. And right now, it seems that they have a lot, and I mean a lot, of programs already available: Abiword, the GIMP, Firefox, Thunderbird, Sunbird, NVU, OpenOffice.org, etc.

AFAIK, all of these apps are cross-platform apps. 

Wouldn't it be nice if somehow some of Linux's best and finest would be able to do something similar, but this time be able to run some popular Linux apps, too. I'm thinking about Evolution/Kontact, KOffice/GNOME Office, or maybe even Nautilus/Konqueror! Very useful when you're on a PC that's not yours (a shop, a friend/neighbor), and you want the full program but don't want to load the entire OS (like a Live CD).

I hope that day would come soon... =P~

---

### Post by adamkane on 2006-07-31
It's only a matter of time before we have simply packaged/portable apps a la MAC OS X. All you have to do is store all the files in a single directory/file, and have subfolders for each machine where the app is used. You would simply need common folders for bookmarks, and email messages, and the like.

The issue with Ubuntu as always is that Ubuntu handles sudo and permissions in a unique way, so that the MOTUs always need to rewrite code for major software distributions to take account of the way permissions are used in Ubuntu.

---

### Post by Xzallion on 2006-07-31
Portable apps rock.  Been using portable firefox and abiword for over a year now.  Perfect for school research on any internet able computer ;)

---

### Post by Jucato on 2006-07-31
Yeah, now if only there was a portable Konqueror, Kontact (including Akregator), and KOffice, I'd be extremely happy. :D

Ok, maybe not so much on Konqueror, as without the underlying KDE components (KParts and KIO), it's practically useless. :p

---

### Post by Kimm on 2006-07-31
That shouldnt be to difficult to do with any application.

./configure --prefix=/media/usbdrive1

Should fix it, and make it work on pretty much any Ubuntu computer (providing all the dependencies are installed on the system by default, or they are also included on the USB Drive).

Apps like thunderbird and firefox might require a little hacking to store data on the pendrive instead of in $HOME, but nothing too extreme.

I think my father actually got a pendrive with OpenOffice.org from work, a couple of weeks back he talked to me about it. He told me that there was an Office program on the drive that he could use on any computer without installing it, and that it wasnt MS Office. He thought it was StarOffice (I supose he has earlier experiance with it), but I guess it might just as well have been OpenOffice.org

---

### Post by Jucato on 2006-07-31
Would that also work with a non-Linux computer? I guess not.

The biggest problem that I see in a sort of PortableApps Linux version would be how to make those Linux apps run in Windows, without having to use stuff like Qemu or VMWare.

I know that both GTK+ and Qt have Cygwin-related projects, but as of the moment, they're quite out of date, and very much a geek's toy.

---

### Post by slimdog360 on 2006-07-31
I know its great isnt it, I tried using portable openoffice about a year ago but it didnt work. Though portable abiword and firefox is great for uni.

---

### Post by adamkane on 2006-07-31
There would be 2 classes of apps. Apps that are portable between Linux and apps that are portable between Linux/Mac/Windows.

The latter would have to be written using light-weight GUIs with something like HTML or XML.

---

### Post by Jucato on 2006-07-31
> **adamkane said:**
> There would be 2 classes of apps. Apps that are portable between Linux and apps that are portable between Linux/Mac/Windows.

The latter would have to be written using light-weight GUIs with something like HTML or XML.

But Firefox, Thunderbird, and Nvu fall under the 2nd class (portable between Linux/Mac/Windows, at least Linux/Windows) and they don't use lightweight GUIs. AFAIK, HTML/XML only control some elements of the GUI, like menu, placements of certain elements, toolbars, some settings, etc., and that the GUI itself is determined by the toolkit of the OS. I might be off the mark, though.

---

### Post by BWF89 on 2006-07-31
I save all my school papers as ODF and since most people use MS Office I put portable OpenOffice on my flashdrive incase I need to openthem somewhere other than on my computer.

Kinda sucks that portable OOo only runs on Windows since 90% of the computers at my school run OSX, I wouldn't be able to view them unless I saved as PDF but taht would take away my ability to copy and paste something out of one of them if I had to.

---

### Post by slimdog360 on 2006-07-31
> **BWF89 said:**
> I save all my school papers as ODF and since most people use MS Office I put portable OpenOffice on my flashdrive incase I need to openthem somewhere other than on my computer.

Kinda sucks that portable OOo only runs on Windows since 90% of the computers at my school run OSX, I wouldn't be able to view them unless I saved as PDF but taht would take away my ability to copy and paste something out of one of them if I had to.

You should give protable Abiword a try, you can now install the plug-ins to give it odf support. Just as its a lot lighter than OpenOffice it might work on more computers. Just a thought.

---

