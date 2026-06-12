---
title: "Trusty Tahr Release Schedule, Partial Upgrades and Common Questions"
date: 2013-04-28
forum: Ubuntu Development Version
---

### Post by cariboo on 2013-04-28
This is where you will find the Trusty Tahr release schedule, as well as the answers to frequently asked questions.

[Release Schedule]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule")

[Cadence testing Schedule]("https://wiki.ubuntu.com/QATeam/Cadence/Saucy")

If you are asked to do a partial upgrade, please read this first:

[Partial upgrade]("https://wiki.ubuntu.com/U%2B1/partial_upgrade")

There always are many questions about what to do and how to do thngs during a release cycle:

[Common problems]("https://wiki.ubuntu.com/U%2B1/common-problems")

[SIZE=3][COLOR="#FF0000"]Warning[/COLOR][/size]: Unless you are willing to have a broken system, please make sure that that Pre-released updates are disabled in Software & Updates, as this repository is now used as a holding area while packages are waiting for dependencies to be built. **[COLOR="#B22222"]See attached thumbnail.[/COLOR]**


If you are looking for the Daily iso's, have a look here:

[Ubuntu]("http://cdimage.ubuntu.com/daily-live/current/")
[Kubuntu]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/")
[Xubuntu]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/")
[Lubuntu]("http://cdimage.ubuntu.com/lubuntu/daily-live/current/")
[UbuntuGnome]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/")

As many of you may know we have created a U+1 testing team to do a better job of reporting bugs, and generally to make things better for all during the testing cycle. To that end, we have created a wiki where a lot of information regarding testing is available. You don't have to be a team member to be able to test , testing is open to everyone regardless of your experience level. That being said, to get the most possible feedback from your bug reports, check this out, before creating a bug report:

[Create a good bug report]("https://help.ubuntu.com/community/ReportingBugs")

Here are some more useful links:

[Trusty Changes Mailing List]("https://lists.ubuntu.com/mailman/listinfo/Trusty-changes")

[Ubuntu Developers]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel") 

[Unity Design Discussion]("https://launchpad.net/~unity-design")

[U+1 Team chat]("webchat.freenode.net/?channels=u+1") 

[Talk to developers]("webchat.freenode.net/?channels=ubuntu+1") 

[Chat with other forum members]("webchat.freenode.net/?channels=ubuntuforums")

Edited: October 18/2013

---

### Post by cariboo on 2013-10-19
I'll update the links in the next couple of days, I've already added the Trusty release schedule.

---

### Post by ventrical on 2013-10-19
Thanks ..

---

### Post by Cavsfan on 2013-10-23
Man, I downloaded the top one not thinking it was 13.10 final release. #-o
I thought that md5sum looked familiar. :rolleyes:

Downloading the correct one now. Should have paid better attention. 

Thanks

---

### Post by kevpan8152 on 2013-10-25
What exactly do you mean by Pre-Release Updates? Are you referring to Trusty-Preposed?

---

### Post by Cavsfan on 2013-10-25
Yes
[ATTACH=CONFIG]247228[/ATTACH]

---

### Post by kevpan8152 on 2013-10-25
Thank You Cavsfan for Clarifying what Cariboo907 said. I will check and make sure that Trusty-Proposed is Disabled.

---

### Post by Cavsfan on 2013-10-25
> **kevpan8152 said:**
> Thank You Cavsfan for Clarifying what Cariboo907 said. I will check and make sure that Trusty-Proposed is Disabled.

You're very welcome! This is a great forum where everyone tries to help each other. :)

---

### Post by Cavsfan on 2013-11-12
Risking a dumb question, here goes. For Trusty is software sources for partners supposed to look like this?

I don't remember what happened yesterday sometimes. #-o

[ATTACH=CONFIG]247787[/ATTACH]

---

### Post by cariboo on 2013-11-12
I see the same thing when checking Software & Updates->Other Software. I'm not sure whether I disabled it myself, or it was done automagically.

I just did a fresh Lubuntu Trusty install on another system, I'll check when it's done to see if I see the same thing on that installation.

**Edit:** I just checked, and the partners repositories were disabled, but extras was still enabled on my fresh Lubuntu install.

---

### Post by Cavsfan on 2013-11-13
> **cariboo907 said:**
> I see the same thing when checking Software & Updates->Other Software. I'm not sure whether I disabled it myself, or it was done automagically.

I just did a fresh Lubuntu Trusty install on another system, I'll check when it's done to see if I see the same thing on that installation.

**Edit:** I just checked, and the partners repositories were disabled, but extras was still enabled on my fresh Lubuntu install.

I did a fresh install too and immediately edited my software sources file to comment out extras since I was aware that there is no Trusty repository set up yet.
I guess that would explain why they were both unchecked here. 

Aren't the partners repositories supposed to be checked?

---

### Post by jerrylamos on 2013-11-13
> **Cavsfan said:**
> Aren't the partners repositories supposed to be checked?
First thing in my install setup exec is:

sudo software-properties-gtk

where I check on "Partners".  Since whenever Ubuntu never has that as default?

Ubuntu does have

"Unsupported  updates"

checked as default, so I always turn that off.  

Do the defaults make any sense to you?

---

### Post by Cavsfan on 2013-11-13
> **jerrylamos said:**
> First thing in my install setup exec is:

sudo software-properties-gtk

where I check on "Partners".  Since whenever Ubuntu never has that as default?

Ubuntu does have

"Unsupported  updates"

checked as default, so I always turn that off.  

Do the defaults make any sense to you?

I guess not when you put it that way lol! :)

I just did as you suggested and unchecked "Unsupported  updates" and checked "Partners".
I'll keep that in mind for the future.

Does this mean any thing?
```
cavsfan@cavsfan-GTO-1969:~$ sudo software-properties-gtk
[sudo] password for cavsfan: 
gpg: /tmp/tmp36v2tq/trustdb.gpg: trustdb created

```

Notice the computer name? I got creative with this insall lol. :lol:

---

### Post by zika on 2013-11-13
> **jerrylamos said:**
> First thing in my install setup exec is:
```
sudo software-properties-gtk
```
```
gksu software-properties-gtk
```

---

### Post by Cavsfan on 2013-11-13
^ +1 for GUI.

---

### Post by Hazzabin on 2013-11-13
I've been running Ubuntu Gnome 'Trusty' since it was first out and am very impressed, even with my additional bits and stuff I like

One question though, where how do I turn off/uncheck 'Extras' in the repos, (an image would be helpfull)  all others either on or off as suggested in previous post here

thanks in advance guys

Hazz

---

### Post by kansasnoob on 2013-11-13
> **Hazzabin said:**
> I've been running Ubuntu Gnome 'Trusty' since it was first out and am very impressed, even with my additional bits and stuff I like

One question though, where how do I turn off/uncheck 'Extras' in the repos, (an image would be helpfull)  all others either on or off as suggested in previous post here

thanks in advance guys

Hazz

Open gnome-terminal and run this command:

```
gksu gedit /etc/apt/sources.list
```

Then enter your password when requested and the following file will open:

```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20131021.1)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
**[COLOR="#FF0000"]#[/COLOR]** deb http://extras.ubuntu.com/ubuntu trusty main
**[COLOR="#FF0000"]#[/COLOR]** deb-src http://extras.ubuntu.com/ubuntu trusty main
```

Then just add the comments "#" that I highlighted in red, click on Save and then File > Quit.

Or if you prefer using the GUI just open Software Updater and click on Settings:

[ATTACH=CONFIG]247807[/ATTACH]

You'll find they're called "Independent" in the GUI:

[ATTACH=CONFIG]247808[/ATTACH]

---

### Post by cariboo on 2013-11-13
> **Hazzabin said:**
> I've been running Ubuntu Gnome 'Trusty' since it was first out and am very impressed, even with my additional bits and stuff I like

One question though, where how do I turn off/uncheck 'Extras' in the repos, (an image would be helpfull)  all others either on or off as suggested in previous post here

thanks in advance guys

Hazz

You can go to System Settings->Software & Updates->Other Software, and uncheck the repositories that are updated to Trusty yet.

---

### Post by Hazzabin on 2013-11-13
Thanks so much guys

---

### Post by kevpan8152 on 2013-11-15
> **Cavsfan said:**
> Risking a dumb question, here goes. For Trusty is software sources for partners supposed to look like this?

I don't remember what happened yesterday sometimes. #-o

[ATTACH=CONFIG]247787[/ATTACH]

I disabled all of them on my installation, but that was because I had to do so in order to Upgrade from 13.10 using sudo update-manager -d. Edit: The reason why I Upgrade from 13.10 is that my Pen Drive Linux Software for Windows 8.1 has NOT yet been Updated to Support 14.04 LTS Nightly Builds by the way.

---

### Post by cariboo on 2013-11-15
I don't have Windows installed on any of my systems, and that last time I used a Windows system I got so frustrated, that it wouldn't do anything the way I was used to. :-)

I use dd to create a usb thumb drive using the following command:

```
dd if=trusty-desktop-i386.iso of=/dev/sdc bs=1M
```

I used the device to create a new Lubuntu installation on an old Celeron powered system, that was having a hard time running XP with all the latest service packs.

---

### Post by kevpan8152 on 2013-11-16
> **cariboo907 said:**
> I don't have Windows installed on any of my systems, and that last time I used a Windows system I got so frustrated, that it wouldn't do anything the way I was used to. :-)

I use dd to create a usb thumb drive using the following command:

```
dd if=trusty-desktop-i386.iso of=/dev/sdc bs=1M
```

I used the device to create a new Lubuntu installation on an old Celeron powered system, that was having a hard time running XP with all the latest service packs.

Thank You Cariboo907 for that line of code, it will help a lot. :-)

---

### Post by kevpan8152 on 2013-11-16
> **cariboo907 said:**
> I don't have Windows installed on any of my systems, and that last time I used a Windows system I got so frustrated, that it wouldn't do anything the way I was used to. :-)

I use dd to create a usb thumb drive using the following command:

```
dd if=trusty-desktop-i386.iso of=/dev/sdc bs=1M
```

I used the device to create a new Lubuntu installation on an old Celeron powered system, that was having a hard time running XP with all the latest service packs.

Just tried your method on Lubuntu 14.04 and it worked! Thanks again.

---

### Post by kevpan8152 on 2013-11-16
> **cariboo907 said:**
> I don't have Windows installed on any of my systems, and that last time I used a Windows system I got so frustrated, that it wouldn't do anything the way I was used to. :-)

I use dd to create a usb thumb drive using the following command:

```
dd if=trusty-desktop-i386.iso of=/dev/sdc bs=1M
```

I used the device to create a new Lubuntu installation on an old Celeron powered system, that was having a hard time running XP with all the latest service packs.

You should have Ventrical post that in his Sticky as the USB Software Disk Creator usually crashes on my systems.

---

### Post by heir4c on 2013-11-17
> Edit: The reason why I Upgrade from 13.10 is that my Pen Drive Linux Software for Windows 8.1 has NOT yet been Updated to Support 14.04 LTS Nightly Builds by the way. 
Use multisystem (in Ubuntu) and it will work: [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

### Post by kansasnoob on 2013-11-27
Please read this:

[http://ubuntuforums.org/showthread.php?t=2184682&page=13&p=12859153#post12859153](http://ubuntuforums.org/showthread.php?t=2184682&page=13&p=12859153#post12859153)

Should the initial warning be changed from:

> Warning: Unless you are willing to have a broken system, please make sure that that Pre-released updates are disabled in Software & Updates, as this repository is now used as a holding area while packages are waiting for dependencies to be built. 

To something like:

> Warning: Unless you are willing to have a broken system, please make sure that that **[COLOR="#FF0000"]proposed-updates[/COLOR]** are disabled in Software & Updates, as this repository is now used as a holding area while packages are waiting for dependencies to be built. 

I'm sort of clueless ATM so this is NOT a recommendation, just a question :)

---

### Post by mc4man on 2013-11-27
> **kansasnoob said:**
> Please read this:

[http://ubuntuforums.org/showthread.php?t=2184682&page=13&p=12859153#post12859153](http://ubuntuforums.org/showthread.php?t=2184682&page=13&p=12859153#post12859153)

Should the initial warning be changed from:



To something like:



I'm sort of clueless ATM so this is NOT a recommendation, just a question :)
have you actually opened Software & Updates >  Updates tab?

---

### Post by philinux on 2013-11-27
Screenshot attached to post #1 for new testers.

---

### Post by kansasnoob on 2013-11-27
> **mc4man said:**
> have you actually opened Software & Updates >  Updates tab?

Of course I have, but based on recent comments maybe we need to amend that to reflect the entire message :confused:

I was puzzled how this happened:

[http://ubuntuforums.org/showthread.php?t=2184682&page=12&p=12859139#post12859139](http://ubuntuforums.org/showthread.php?t=2184682&page=12&p=12859139#post12859139)

Or, *thinking harder,* are proposed updates already applied in current testing isos????

That's why I made sure to say, "I'm sort of clueless ATM so this is NOT a recommendation, just a question" :confused:

---

### Post by kansasnoob on 2013-11-27
> **philinux said:**
> Screenshot attached to post #1 for new testers.

Awesome! Thank you :)

---

### Post by Cavsfan on 2014-03-04
Just a question probably a noobish one. What is the difference between a regular Ubuntu iso and a UbuntuGnome iso?
I would suspect that UbuntuGnome iso comes with 1) Gnome Flashback (with compiz) 2) Gnome Flashback (with metacity) and 3) Gnome Shell without Unity.

While the Ubuntu iso just comes with Unity. Would that be correct?

---

### Post by sgage on 2014-03-04
Not quite. It has Gnome Shell as default, of course, and Gnome Classic (Gnome Shell with some extensions to make it seem somewhat like Gnome 2) offered as a session option, but not Gnome Flashback, with or without 'effects' (compiz).

There is some different theming and such, and perhaps some other different default packages, but I'm not sure about that - I haven't used stock 'Unity' Ubuntu in a long time.

---

### Post by kansasnoob on 2014-03-04
> **Cavsfan said:**
> Just a question probably a noobish one. What is the difference between a regular Ubuntu iso and a UbuntuGnome iso?
I would suspect that UbuntuGnome iso comes with 1) Gnome Flashback (with compiz) 2) Gnome Flashback (with metacity) and 3) Gnome Shell without Unity.

While the Ubuntu iso just comes with Unity. Would that be correct?

No. None of the iso's ship with GNOME Flashback, but it's installable during an Edubuntu installation.

Ubuntu GNOME has the Gnome Shell DE + the new GNOME Classic.

Ubuntu has only the Unity DE.

Flashback is installable post-installation in both Ubuntu and Ubuntu GNOME though:

[http://ubuntuforums.org/showthread.php?t=2184682](http://ubuntuforums.org/showthread.php?t=2184682)

---

### Post by Cavsfan on 2014-03-04
> **sgage said:**
> Not quite. It has Gnome Shell as default, of course, and Gnome Classic (Gnome Shell with some extensions to make it seem somewhat like Gnome 2) offered as a session option, but not Gnome Flashback, with or without 'effects' (compiz).

There is some different theming and such, and perhaps some other different default packages, but I'm not sure about that - I haven't used stock 'Unity' Ubuntu in a long time.

> **kansasnoob said:**
> No. None of the iso's ship with GNOME Flashback, but it's installable during an Edubuntu installation.

Ubuntu GNOME has the Gnome Shell DE + the new GNOME Classic.

Ubuntu has only the Unity DE.

Flashback is installable post-installation in both Ubuntu and Ubuntu GNOME though:

[http://ubuntuforums.org/showthread.php?t=2184682](http://ubuntuforums.org/showthread.php?t=2184682)

Thanks for the replies! I was about to get all excited, backup and do a fresh install of UbuntuGnome in Beta. I guess I still could. :)
Not real fond of classic as no matter what I did cairo dock would remain behind the bottom panel. Although that could easily be a CCSM or cairo dock setting you just never know.

I don't know enough about the others to try them; always have been a generic Ubuntu kind of guy. But I do not like Unity; never have and never will. It wastes too much of my screen.
I already have a very useful conky on the right side that VinDSL came up with so I like the rest of the screen for me. :)

---

### Post by kansasnoob on 2014-03-04
> **Cavsfan said:**
> Thanks for the replies! I was about to get all excited, backup and do a fresh install of UbuntuGnome in Beta. I guess I still could. :)
Not real fond of classic as no matter what I did cairo dock would remain behind the bottom panel. Although that could easily be a [COLOR="#FF0000"]CCSM [/COLOR]or cairo dock setting you just never know.

I don't know enough about the others to try them; always have been a generic Ubuntu kind of guy. But I do not like Unity; never have and never will. It wastes too much of my screen.
I already have a very useful conky on the right side that VinDSL came up with so I like the rest of the screen for me. :)

CCSM would not be a problem in Ubuntu GNOME because 'compiz' is not even installed.

If you're interested in the "flashback sessions" you should either open a new thread or reply to mine ;)

ATM it's more problematic in Ubuntu GNOME than it is in Ubuntu because or separating g-s-d and u-s-d :D

---

### Post by Cavsfan on 2014-03-04
> **kansasnoob said:**
> CCSM would not be a problem in Ubuntu GNOME because 'compiz' is not even installed.

If you're interested in the "flashback sessions" you should either open a new thread or reply to mine ;)

ATM it's more problematic in Ubuntu GNOME than it is in Ubuntu because or separating g-s-d and u-s-d :D

Oh yeah and don't install any meta-packages like gnome right? :p

---

### Post by kansasnoob on 2014-03-04
> **Cavsfan said:**
> Oh yeah and don't install any meta-packages like gnome right? :p

The meta-package 'gnome' is basically the most compatible Debian version of GNOME and includes a load of stuff most users would not want or need.

That said some things have also changed with the separation of g-s-d from u-s-d so I'm still learning ................... but this is the wrong place to discuss it.

---

### Post by jerrylamos on 2014-03-06
> **Cavsfan said:**
>  But I do not like Unity; never have and never will. It wastes too much of my screen.
I already have a very useful conky on the right side that VinDSL came up with so I like the rest of the screen for me. :)
?  I don't like Unity, I use it because I'm looking for bugs.

I have the launcher icons size 32 and hidden at the left.  Most of the time nowhere in sight.

Unity takes one line at the top of the screen.

All the rest of the screen is for me.

I also have a Chromebook, faster video than Ubuntu (!)  even though the dual processors are slower than the dual processor Atom I'm using here.  Chromebook takes 2 lines at the bottom of the screen, a little more than Unity.  I use the same TV/monitor on both of them, 1280x720 for visibility.

BTW, on this testing forum,I install tahr every couple of weeks on my netbook, notebook, and tower.  Last week of February tahr didn't support wireless on my netbook.  It does now.

---

### Post by craig10x on 2014-03-06
Unity really doesn't waste any screen space if you auto hide it...i set mine to 38 pixels for my 17" laptop screen (which is my desktop) and the panel on top (because of it's "global menu" nature) does not steal any space when your browser is open and you are web surfing (even if you use the new 14.04 option of putting the menus back in application windows, which i do use now and love that new feature because it doesn't affect the top panel's normal behavior at all)...That is why i also can't understand Cavsfan's comments about unity wasting screen space...really guy, it doesn't... :rolleyes:

In fact, because of those features, it is very space efficient :D

---

### Post by Cavsfan on 2014-03-06
> **jerrylamos said:**
> ?  I don't like Unity, I use it because I'm looking for bugs.

I have the launcher icons size 32 and hidden at the left.  Most of the time nowhere in sight.

Unity takes one line at the top of the screen.

All the rest of the screen is for me.

I also have a Chromebook, faster video than Ubuntu (!)  even though the dual processors are slower than the dual processor Atom I'm using here.  Chromebook takes 2 lines at the bottom of the screen, a little more than Unity.  I use the same TV/monitor on both of them, 1280x720 for visibility.

BTW, on this testing forum,I install tahr every couple of weeks on my netbook, notebook, and tower.  Last week of February tahr didn't support wireless on my netbook.  It does now.

> **craig10x said:**
> Unity really doesn't waste any screen space if you auto hide it...i set mine to 38 pixels for my 17" laptop screen (which is my desktop) and the panel on top (because of it's "global menu" nature) does not steal any space when your browser is open and you are web surfing (even if you use the new 14.04 option of putting the menus back in application windows, which i do use now and love that new feature because it doesn't affect the top panel's normal behavior at all)...That is why i also can't understand Cavsfan's comments about unity wasting screen space...really guy, it doesn't... :rolleyes:

In fact, because of those features, it is very space efficient :D

Thanks for the insight! I'll take that into consideration and set it to auto hide if I get back into Unity. Also putting the menus back in application windows.
Right now I'm riding an install from January 9th and everything is working fairly smooth so I am hanging on to it until final release. I'm not one to openly look for breakage. :D

---

### Post by craig10x on 2014-03-06
@Cavsfan: yeah, i have to tell you, with that new added feature on 14.04 that puts the menus back on the app's windows (but fortunately does not affect the top panel's space saving feature) and of course, auto hiding the unity launcher and making the pixels smaller (which i think actually makes it look better... plus it enables one to have more favorites and frequently used apps on the launcher that are easily visible) it's really, really nice to use now...i think you will enjoy it ;)

---

### Post by Cavsfan on 2014-03-06
> **craig10x said:**
> @Cavsfan: yeah, i have to tell you, with that new added feature on 14.04 that puts the menus back on the app's windows (but fortunately does not affect the top panel's space saving feature) and of course, auto hiding the unity launcher and making the pixels smaller (which i think actually makes it look better... plus it enables one to have more favorites and frequently used apps on the launcher that are easily visible) it's really, really nice to use now...i think you will enjoy it ;)

But, but, I'm too old to change. I hate change ;). Naw, I may give it a try. But I think we're going to get into trouble if we keep posting on this thread.

---

### Post by craig10x on 2014-03-06
Yes, you are right...i can feel cariboo907 closing in ;)
Anyway, give it a try...maybe it will grow on you... :D

---

### Post by cariboo on 2014-03-06
I create a new thread for every release, so it really doesn't matter that much if you post in this thread. :)

---

### Post by Cavsfan on 2014-03-07
> **cariboo907 said:**
> I create a new thread for every release, so it really doesn't matter that much if you post in this thread. :)

Good to know. :D

---

