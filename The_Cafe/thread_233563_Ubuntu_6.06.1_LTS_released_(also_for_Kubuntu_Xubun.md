---
title: "Ubuntu 6.06.1 LTS released (also for Kubuntu Xubuntu Edubuntu) !"
date: 2006-08-10
forum: The Cafe
---

### Post by ubuntu_demon on 2006-08-10
From [http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444) :

[quote=Colin Watson]
The Ubuntu team is proud to announce the release of Ubuntu 6.06.1 LTS, the first maintenance release of &#8220;Dapper Drake&#8221;. This release includes both installable Desktop CDs and alternate text-mode installation CDs for several architectures, for Ubuntu, Kubuntu and Edubuntu. Xubuntu is also included, although commercial support for it is not available from Canonical Ltd.
[/quote]

This is great news! It also saves you a lot of time upgrading on a new installation (especially if you are on a slow internet connection).

I blogged about this here :
[http://ubuntudemon.wordpress.com/2006/08/10/ubuntu-6061-lts-released-also-for-kubuntu-xubuntu-edubuntu/](http://ubuntudemon.wordpress.com/2006/08/10/ubuntu-6061-lts-released-also-for-kubuntu-xubuntu-edubuntu/)

---

### Post by kaffelars on 2006-08-10
I'm **so** happy I didn't have time to install Dapper on my desktop computer yesterday :D

---

### Post by Jucato on 2006-08-10
The release cause quite a stir, specially since there was no official press release yet from Ubuntu. Some thought they need to dist-upgrade or reinstall to get 6.06.1. :D

Here's the (probably draft) announcement for the Point Release: [https://wiki.ubuntu.com/DapperPointOneAnnouncement](https://wiki.ubuntu.com/DapperPointOneAnnouncement)

---

### Post by ubuntu_demon on 2006-08-10
At the Ubuntu Developers Summit there was a BOF scheduled for the planning of the Point Release. 

From [http://en.wikipedia.org/wiki/BOF](http://en.wikipedia.org/wiki/BOF) :
> 
    * Birds of a Feather: This idiom is a shortening of the proverb "birds of a feather flock together", meaning that people (birds) of the same kind or interest (of a common feather) enjoy spending time (flocking) together. This proverb is believed to date back as far as Greek and Roman times, but has become commonly used as jargon by various groups since the nineteenth century.

        * The acronym is used by the Internet Engineering Task Force (IETF) to denote initial meetings of members interested in a particular issue. The term is also used by computer science professionals at gatherings such as industry conferences to describe a meeting in which a topic of specific interest is discussed. Such meetings are referred to as Birds-of-a-Feather Meetings, or simply as BoFs.


When I read on ubuntu-devel (mailinglist) that the Point Release was coming soon I wrote about it here :

[http://ubuntudemon.wordpress.com/2006/08/01/dapper-point-release-is-coming-soon/](http://ubuntudemon.wordpress.com/2006/08/01/dapper-point-release-is-coming-soon/)

---

### Post by tikal26 on 2006-08-10
how do i upgrade. I know that on the kubuntu  page they sayas that I just have to make sure that I update from dapper-updates is that a differete repo?:confused:

---

### Post by tseliot on 2006-08-10
> **tikal26 said:**
> how do i upgrade. I know that on the kubuntu  page they sayas that I just have to make sure that I update from dapper-updates is that a differete repo?:confused:

If you kept your system up-to-date then you already have Ubuntu 6.06.1 LTS.

Ubuntu 6.06.1 LTS has all the updates you have (and they have also fixed some bugs of the Desktop installer)

---

### Post by bruce89 on 2006-08-10
If you press Control+Alternate+F1 (Control+Alternate+F7 to get back), you can see if you have 6.06.1 LTS already.  You should, as it is just Dapper+updates.

---

### Post by siimo on 2006-08-10
woot woot!

Initial 6.06 live cd didn't boot on my main system.  I will download this one probably on the weekend and give it a test run.

---

### Post by dougdockery on 2006-08-10
Okay, serious noob question here.  I ran Update Manager and it says that my system is up to date.  However, when I go the <ctrl, alt F1> page it still says 6.06 LTS not the 6.06.1 LTS that I was expecting.  Any ideas why?  I mean I'm feeling sort of left out here...:confused: 

Thanks for your help.

Doug

---

### Post by confused57 on 2006-08-10
Someone in another thread suggested running this command:
lsb_release -a

to see what version you have.

---

### Post by dougdockery on 2006-08-10
> **confused57 said:**
> Someone in another thread suggested running this command:
lsb_release -a

to see what version you have.

Here's what I get from lsb_release -a

dougdockery@dougdockery-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06 LTS
Release:        6.06
Codename:       dapper

I received a notice of an update today - something about a windows media format or something that I installed - but nothing about the maintenance release.  And when I run Update Manager it still says I'm up to date.

Am I doing something wrong?

Thanks for your help -

Doug

---

### Post by confused57 on 2006-08-10
Here's what I get:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper

Do you have the universe & multiverse repositories enabled?  That's the only thing I can think of that may help...I've just installed all the updates since I installed Dapper about a month ago.

---

### Post by dougdockery on 2006-08-11
Here's the content of my sources.list file:

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
#
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


Is there a repository that I need to add?

Thanks again.

D

---

### Post by MetalMusicAddict on 2006-08-11
Anyone where the DVD releases are for X/K/Ubuntu?

---

### Post by TravisNewman on 2006-08-11
I had to restart before it showed up as .1, just fyi. I had a lot of updates that I hadn't restarted from.

---

### Post by jason.b.c on 2006-08-11
So then , Now that an updated version has been released does that mean that **the damn hibernation/suspend** problems have been corrected...???

In ubuntu and kubuntu...???

[https://launchpad.net/distros/ubuntu/+source/hibernate/+bug/39006]("https://launchpad.net/distros/ubuntu/+source/hibernate/+bug/39006")

[Here's the main problems.]("http://www.ubuntuforums.org/showpost.php?p=1201351&postcount=1")

> **[SIZE="3"]Problem #3[/SIZE]**

Why does dapper naturally assume that i want it to put my computer into hibernation after (i think) like twenty minutes of inactivity..???

Thats another one that i can't figure out, Now in breezy there's option to disable the ubuntu power managment from being able to shutdown, suspend or hibernate the computer after so many minutes by simply un-checking a check box, But i can't figure this one out in dapper.!

I set the screensaver to come on after five minutes and that works fine although the fade in fade out feature dosen't quite work right, it fades out to screensaver but not when returning to desktop ( senses activity )..

But i don't get it.!, Where/How do you disable the power management ( permanently) from being able to hibernate/suspend the computer when i'm away from it.?
I looked and looked for an hour and a half or so and couldn't figure it out..


[Here's the thread i started...]("http://http://www.ubuntuforums.org/showthread.php?t=207014")

Yea i guess i'm not the only one after-all..!

---

### Post by dougdockery on 2006-08-11
> **panickedthumb said:**
> I had to restart before it showed up as .1, just fyi. I had a lot of updates that I hadn't restarted from.

One restart later and still 6.06 LTS...

I posted the content of my sources.list file - have I mucked something up in that file so that Update Manger doesn't see the 6.06.1 updates?

D

---

### Post by ubuntu_demon on 2006-08-11
**HOWTO FIX 6.06.1 not showing up**

Don't worry If "lsb_release -a" doesn't tell you that you are using 6.06.1. It's probably easy to solve. **Please follow all steps.**Try this :

**1)** Do a reboot and try "lsb_release -a" again.
**2)** Make sure your sources.list is alright. 

Use a clean Dapper sources.list :
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

A little note :
You **could** disable multiverse and universe **if** you had them disabled previously and you have no universe nor multiverse packages installed. IMHO multiverse and universe should be used for most users. So you probably don't have to comment them.

**3)**
Start the terminal. Don't type the $.

$sudo apt-get update
$sudo apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop [I](or xubuntu,kubuntu,edubuntu)
[/I]
$sudo apt-get upgrade
$sudo apt-get dist-upgrade

if it says "package A is being kept back" either force it to update like this :
$sudo apt-get install *packageA*

Or remove it if you don't like the package :
$sudo apt-get remove *packageA*

**4)** reboot
**5)** lsb_release -a should return 6.06.1. If it doesn't let us know :)
**6)** Now you can create a custom sources.list again. Please be a bit conservative with it.

Here's a sources.list which is suitable for most average users :
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by dolby on 2006-08-11
wtf is "*Xubuntu is also included, although commercial support for it is not available from Canonical Ltd.*" supposed to mean?!?

---

### Post by BWF89 on 2006-08-11
Ubuntu idea of long term support: 18 months

CentOS's idea of long term support: 7 years

---

### Post by ice60 on 2006-08-11
do you think it will install on my RAID ARRAY now? the first realise can't see my HDD becasue of the SATA STRIPE RAID ARRAY. i had to install SUSE 10.1 with the gnome desktop. i want to use Ubuntu Dapper. SUSE has lots of KDE stuff which i don't like and it uses RPMs to. i can't install anything!!!

---

### Post by ubuntu_demon on 2006-08-11
> **BWF89 said:**
> Ubuntu idea of long term support: 18 months

CentOS's idea of long term support: 7 years
Normal Ubuntu releases are supported for 18 months. Dapper is supported for 5 years for servers and for 3 years for desktops. IMHO that's real Long Time Support.

---

### Post by 5-HT on 2006-08-11
> **dolby said:**
> wtf is "*Xubuntu is also included, although commercial support for it is not available from Canonical Ltd.*" supposed to mean?!?

Canonical does not offer [commercial tech support]("http://www.ubuntu.com/support/paid") for Xubuntu.

---

### Post by FatherDale on 2006-08-11
> **confused57 said:**
> Someone in another thread suggested running this command:
lsb_release -a

to see what version you have.

Did that. Both my (constantly updated) boxen show 6.06. Wonder if it's because I'm not using the 386 kernel?

---

### Post by ubuntu_demon on 2006-08-11
I moved vtel57's posts to a new thread in the installation and upgrade section here :

"lsb_release -a" won't show 6.06.1
[http://www.ubuntuforums.org/showthread.php?t=234630](http://www.ubuntuforums.org/showthread.php?t=234630)

---

### Post by jerinjoy on 2006-08-15
> **dougdockery said:**
> Okay, serious noob question here.  I ran Update Manager and it says that my system is up to date.  However, when I go the <ctrl, alt F1> page it still says 6.06 LTS not the 6.06.1 LTS that I was expecting.  Any ideas why?  I mean I'm feeling sort of left out here...:confused: 

Thanks for your help.

Doug

Doug, Click either 'Check' option in update manager or 'Reload' in Synaptic. It will get the list of latest updates available.

---

