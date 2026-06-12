---
title: "[gnome shell] few questions and bugs"
date: 2013-01-07
forum: Ubuntu Development Version
---

### Post by ft_ on 2013-01-07
Hi,

I upgraded without any issue from 12.10.
I want to know if somme issues I get now are common with some of you or not...

- often get BIG crashes of gnome shell when I close a window
- no more desktop background when using the upper left hot corner (black background instead)
- alacarte crashes when starting
- the lightdm login screen shows "ubuntu 12.10"
- my laptop fan sometimes get nervous, have to restart a session (maybe firefox-related, but "top" is not showing any trouble)
- firefox scrolling is quite choppy

Nothing really annoying, except the first one.
I noticed that I now get a fast and clean shutdown (in 12.10 there were delays with killing processes and networks).

Thanks for any reply, good night.

---

### Post by grahammechanical on 2013-01-07
We are talking about Ubuntu Gnome Remix, are we?

I installed both of these PPAs

[https://launchpad.net/~gnome3-team/+archive/gnome3]("https://launchpad.net/~gnome3-team/+archive/gnome3")

[https://launchpad.net/~gnome3-team/+archive/gnome3-staging]("https://launchpad.net/~gnome3-team/+archive/gnome3-staging")

It was the second one (gnome3-staging) that seems to have solved this on my install

> - often get BIG crashes of gnome shell when I close a window

Actually, it was a freeze with the mouse still moveable but nothing active.

I do not get the other issues. I do not use alacarte. Nor, have I installed any extensions.

This

> - the lightdm login screen shows "ubuntu 12.10"

should not be a surprise because it is Ubuntu 12.10 that is slowly being converted to 13.04. The standard Ubuntu 13.04 says the same. Logos get changed towards the end of the development cycle.

The logo on the LightDM login screen is actually an image. It is not put there by some script that scans for some identification label.

If you are using gnome shell on top of Ubuntu then go to /usr/share/unity-greeter/ and look for logo.png. That is the image that is put on the LightDM login screen. On my Ubuntu Raring it is still saying Ubuntu 12.10.

Unity-greeter is not installed in Gnome Remix.

Regards.

---

### Post by mc4man on 2013-01-07
> **ft_ said:**
> Hi,

I upgraded without any issue from 12.10.
I want to know if somme issues I get now are common with some of you or not...

- often get BIG crashes of gnome shell when I close a window


still see gmone-shell & or gnome session locking up on windows closing here, thought some updates from the staging ppa had resolved but they didn't.
Has been happening since the  gnome-shell upgrade to 3.6.2 from 3.6.1 & makes Gs completely unusable.
I guess it affects some hardware but not others as few have complained

The unacceptable workaround here is to run GS from a terminal, then it never happens as long as the windows being closed are on the same workspace as the terminal running Gs.

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1094571](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1094571)

---

### Post by ronacc on 2013-01-07
my experience here is that the freezes were temporarily fixed by adding the staging PPA but started recurring after a recent update .

---

### Post by serdotlinecho on 2013-01-08
> **ft_ said:**
> Hi,

I upgraded without any issue from 12.10.
I want to know if somme issues I get now are common with some of you or not...

- often get BIG crashes of gnome shell when I close a window
- no more desktop background when using the upper left hot corner (black background instead)
- alacarte crashes when starting
- the lightdm login screen shows "ubuntu 12.10"
- my laptop fan sometimes get nervous, have to restart a session (maybe firefox-related, but "top" is not showing any trouble)
- firefox scrolling is quite choppy

Nothing really annoying, except the first one.
I noticed that I now get a fast and clean shutdown (in 12.10 there were delays with killing processes and networks).

Thanks for any reply, good night.

Hi ft_ :D 

I've had a similar problem when using gnome-shell 3.6.x or 3.7.x on ubuntu 13.04. Read my previous thread:

[http://ubuntuforums.org/showthread.php?t=2088736](http://ubuntuforums.org/showthread.php?t=2088736)

I've solved black background on Activities overview with this method:

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10#Upgrade](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10#Upgrade)

For alacarte, it's a bug and unusable atm:

[http://ubuntuforums.org/showpost.php?p=12442870&postcount=2](http://ubuntuforums.org/showpost.php?p=12442870&postcount=2)

And don't worry about lightdm unity greeter still showing "Ubuntu 12.10". It will change in 13.04 beta i guess? ;)

---

### Post by zika on 2013-01-08
> **grahammechanical said:**
> We are talking about Ubuntu Gnome Remix, are we?

I installed both of these PPAs

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

[https://launchpad.net/~gnome3-team/+archive/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/gnome3-staging)

It was the second one (gnome3-staging) that seems to have solved this on my install



Actually, it was a freeze with the mouse still moveable but nothing active.

I do not get the other issues. I do not use alacarte. Nor, have I installed any extensions.

This



should not be a surprise because it is Ubuntu 12.10 that is slowly being converted to 13.04. The standard Ubuntu 13.04 says the same. Logos get changed towards the end of the development cycle.

The logo on the LightDM login screen is actually an image. It is not put there by some script that scans for some identification label.

If you are using gnome shell on top of Ubuntu then go to /usr/share/unity-greeter/ and look for logo.png. That is the image that is put on the LightDM login screen. On my Ubuntu Raring it is still saying Ubuntu 12.10.

Unity-greeter is not installed in Gnome Remix.

Regards.[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3) on Raring?
As far I can see there is no Raring branch in that PPA...

---

### Post by serdotlinecho on 2013-01-08
> **grahammechanical said:**
> 

We are talking about Ubuntu Gnome Remix, are we? 

I think ft_  is using Ubuntu 12.10 unity desktop and  installed gnome-shell from repo, upgrade to 13.04 and using lightdm instead of gdm. This:

>  - the lightdm login screen shows "ubuntu 12.10" 

---

### Post by ft_ on 2013-01-08
Right : I installed in 12.10 :
0) kubuntu-desktop (purged now)
1) ubuntu-desktop
2) gnome-shell (power usage is much better than KDE)

So my DM is lightdm, that's true !
I really do not worry for the "12.10" tag.

I have to do some things from the real life, and after that I'll follow your tips. Thanks !

(Anyway, I do not want to use some PPA, that's a choice.)

---

### Post by ft_ on 2013-01-08
so :

With the official repos Gs 3.6.2 I can't get the wallpaper background when showing the apps windows. I installed the ubuntu-gnome-desktop (just the dependancies, not the recommended packages) and ubuntu-gnome-settings.

:-k

---

### Post by Harry33 on 2013-01-09
> **zika said:**
> [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3) on Raring?
As far I can see there is no Raring branch in that PPA...

Well yes there is, at least now.
Here:
[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring)

---

### Post by zika on 2013-01-09
> **Harry33 said:**
> Well yes there is, at least now.
Here:
[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring)
I know that, and I use it now... At the time I wrote that post there was not, I checked just before/while I wrote...

---

### Post by ft_ on 2013-01-11
the new 3.8 kernel seems to have stopped the random high power usage bug (-> not in top -> kernel). Now the power usage is lower than ever for my PC.

---

### Post by cariboo on 2013-01-11
Seeing as we are discussing gnome-shell problems and bugs in this thread. I've got a question. I have gnome-shell installed on my netbook, both the Quantal version and Raring. On the Quantal install the background is tiled on the login screen, but the desktop background is as it should be, nay suggestions on how to fix the tiling problem?

---

### Post by ft_ on 2013-01-13
(I have no answer to your question.)

Some infos about the black screen when showing windows with the hot corner.
When I set (in gnome tweak tool) Nautilus to not handle the desktop, everything is ok. But when I check this item (as usual), the issue does appear.

edit :
1- open dconf editor
2- go to org/gnome/desktop/background
3- set picture-uri,draw-background and show-desktop-icons to default
4- check the two last one again
5- select a wallpaper image
6- now the background does appear when using the hot corner
7- unfortunately it does not survive a logout/login.....

---

### Post by ft_ on 2013-01-18
black background bug solved switching to SNA accel :
[http://ubuntuforums.org/showthread.php?t=2106231](http://ubuntuforums.org/showthread.php?t=2106231)

---

### Post by kevpan815 on 2013-01-19
First of all, I would Recommend that you Install 13.04 as a Clean Install (start with a Nightly Build .ISO and then update it each day with the zsync command in a command line terminal) at least until we hit Beta, as we are still pretty much in an Alpha Phase right now and Upgrading from 12.10 may not work as intended just yet.

---

### Post by ft_ on 2013-01-19
yeah ok, here I think we are all aware of the fact that Raring is in an alpha state... Thanks...
Anyway, the only remaining bug in my first post's list is the one related to Alacarte. Quite a huge progress, since it's not critical.

---

### Post by kevpan815 on 2013-01-19
I am sorry if I offended you, I am just simply speaking from my own experiences that usually by downloading the .ISO Nightly Build and than updating the .ISO with zsync on a daily basis works better then trying to update using the program itself, as you will get offered a Partial Upgrade quite often if that is the road you take.

---

### Post by ft_ on 2013-01-19
no doubt you're right, but here the subject is GS, and I do not think that the bugs we talk about are related to an upgrade mode (maybe I'm wrong).

---

### Post by kevpan815 on 2013-01-20
The other post about how someone's Networking Connection stopped working is a very good example of what can go wrong when you update through the program itself, even at the command line.

---

### Post by ft_ on 2013-01-20
is it :
[http://ubuntuforums.org/showthread.php?t=2106038](http://ubuntuforums.org/showthread.php?t=2106038)
?

If it does, I do not understand why it should be an upgrade mode stuff, since the last post :
[http://ubuntuforums.org/showpost.php?p=12464243&postcount=8](http://ubuntuforums.org/showpost.php?p=12464243&postcount=8)
does the right remark imho.
I rather think to a driver issue with the last kernel update.

Does alacarte work in your zsync install ?

---

### Post by kevpan815 on 2013-01-20
I don't know what that program you mentioned is, and I think you are also misunderstanding exactly what Zsync really is. First you need a full .ISO Nightly Build File that your going to want to save on some kind External File Source before Burning the .ISO to disk and installing today's Nightly Build from the disk. Then tomorrow, copy the .ISO to your home Directory and possibly rename it while leaving the .ISO alone so the file that you retrieve from Zsync is not the same as you already have in your home directory. next do a Sudo Apt-Get Install Zsync at the Command Line (do an Apt-Get Update if it fails). Then do either a zsync [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync) -I /home/(username)/Filename) or a zsync [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso.zsync) -I /home/(username)/(filename) if your using AMD64 Ubuntu. Do NOT put Sudo in front ofZsync as that will LOCK the Downloaded File. Next burn the Updated .ISO File to DVD. Finally Boot to the DVD and select Install Ubuntu, and than select Erase Raring and Reinstall, this will give you a fresh 13.04 Nightly Build Installation but it will leave all your other Partitions alone. Let it finish installing and Reboot. If everything goes as planned you should Window Pop Up asking if you want to Boot to 13.04 or something else (for me it asks if I want to boot to 13.04 or Windows 8).

---

### Post by kevpan815 on 2013-01-20
P.S. If you read one of Cariboo907's Replies, he said that he recommends that you do NOT use Update Manager AND Turn OFF Automatic Updates, Especially with Builds still in Development.

---

