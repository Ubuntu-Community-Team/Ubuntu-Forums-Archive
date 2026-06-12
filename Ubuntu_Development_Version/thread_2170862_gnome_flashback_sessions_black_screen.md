---
title: "gnome flashback sessions black screen"
date: 2013-08-27
forum: Ubuntu Development Version
---

### Post by Vanishing on 2013-08-27
Is it just me? I have tested this on an old install(partially broken due to dbus and systemd issues), a semi new install(installed yesterday) and a brand new install, logging into flashback sessions hangs at a black screen.
This behavior started about this morning.

---

### Post by Cavsfan on 2013-08-28
This happens to me after today's update. I thought it was Grub2 as it was updated.
```
cavsfan@cavsfan-MS-7529:~$ grub-install -v
grub-install (GRUB) 2.00-18ubuntu1

```
But, I can confirm it is not caused by that that I can see. I am in Unity now which is unaffected.

I cannot login to flashback though all I have is a black screen too. I can bring up a terminal with ALT+TAB+t but that is about all.

---

### Post by mc4man on 2013-08-28
I believe this is from the upgrade of upstart to 1.9.1-0ubuntu5
(not the only issue with upstart but certainly significant for flashback users

---

### Post by mc4man on 2013-08-28
Pretty easy to fix -- 
```
sudo nano /etc/upstart-xsessions
```

change 
gnome-fallback
gnome-fallback-compiz
to
gnome-flashback
gnome-flashback-compiz

Or maybe install the dummy fallback packages to match this dummy upgrade

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1217991](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1217991)

---

### Post by muktupavels on 2013-08-28
> **mc4man said:**
> Pretty easy to fix -- 
```
sudo nano /etc/upstart-xsessions
```

change 
gnome-fallback
gnome-fallback-compiz
to
gnome-flashback
gnome-flashback-compiz

Or maybe install the dummy fallback packages to match this dummy upgrade

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1217991](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1217991)

Thanks!

---

### Post by ventrical on 2013-08-28
I installed ..
```

sudo apt-get install gnome-session-fallback

```

eary thismorning while doing some overclocking on one of my systems. I was not able to get Unity to work in full screen mode so I used gnome fallback. It worked just fine with (no effects). It worked for a while @ 4.002GHz in gnome-flashback (classic) but eventually became unstable during an upgrade. ( the upgrade process [unpacking/installing]  caused a heavier than normal load on the cpu).

---

### Post by jamesward on 2013-08-29
I'm having the same problem as of 2 days ago.  The suggested fixes above didn't work for me.  But logging into tty1 and running the following got things up and running:
> sudo service lightdm restart
gnome-session-flashback

Not sure why that works though.

---

### Post by mc4man on 2013-08-29
They'll get this fixed up sooner than later
As mentioned in report the maintainer says not to change the names in /etc/upstart-xsessions as they should match what's in /usr/share/xsessions
(though if running a dev one can do as they please to **workaround** released issues..

Installing gnome-session-fallback would have no effect as it doesn't install any .session files anymore like it did in 13.04

Another 'workaround' in lieu of editing that upstart file would be to create a symlink(s), ex. for flashback (no effects
 ```
sudo ln -s /usr/share/gnome-session/sessions/gnome-flashback.session /usr/share/gnome-session/sessions/gnome-fallback.session
```

(I do find the tendency of upgrades being approved/released without the reviewer/maintainer/uploader actually using them first to see how they work out interesting, I guess they sometimes don't have the time

---

### Post by Cavsfan on 2013-08-29
I believe my problem is a bit more serious. Today I cannot get into either flashback or unity. 
Unity freezes and ALT+TAB+F1 to get to CLI mode and attempt the updates there yields some odd errors about dpkg and will not update.
I believe it is time for a fresh install. But, I don't have time for that now.

In Precise at present and glad I have more than one install so I can copy stuff from my Saucy partition to my USB drive.
Not sure why my situation is different but, I think it is borked.

Oh, and I seen another option to login something like NVIDIA Persistent *something*. Don't know where that came from or why.

---

### Post by Vanishing on 2013-08-29
> **mc4man said:**
> Pretty easy to fix -- 
```
sudo nano /etc/upstart-xsessions
```

change 
gnome-fallback
gnome-fallback-compiz
to
gnome-flashback
gnome-flashback-compiz

Or maybe install the dummy fallback packages to match this dummy upgrade

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1217991](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1217991)
Thank you for this..
I was playing with gnome3 ppa and gnome3-staging ppa(oh noes)...that.did.not.go.well.
After ppa-purge I was left blackscreen, and thats when I thought my whole year of tweaking on this install is done for..
I started fresh, and encountered this problem(After I installed, I tried to chroot & upgrade, so the old install got this problem as well).
After 2 days of endless log reading, file diffing, I magically fixed my old friend :D

Yay for Thursday!

---

### Post by mc4man on 2013-08-29
There is a new build that should fix without any mucking around
(if one edited the upstart file then set back
> gnome-panel (1:3.6.2-0ubuntu13) saucy; urgency=low

  * Drop bin/gnome-session-flashback as it wasn't consistently used and
    caused problems with upstart user sessions. (LP: #1217991)
  * Add aliases for gnome-fallback to gnome-flashback and
    gnome-fallback-compiz to gnome-flashback-compiz.

Here I just purged gnome-session-flashback then re-installed with new one, seems ok

---

### Post by Cavsfan on 2013-08-30
Glad I had time to give this some thought. Today I ended up being able to alt+tab+f1 into a cli session and installed gnome-session-fallback.
Then I attempted to get the updates again and it updated fine. Then sudo service lightdm restart brought me back to the login screen
and flashback works like a champ now. Noticed that gnome-session-fallback and gnome-session-flashback were in the updates.

Oddly yesterday the login screen was the default Ubuntu color and today it is back to matching my background. So glad I didn't have to re-install.
Although I was prepared to. :)

---

### Post by kansasnoob on 2013-08-30
I'm too busy to follow up on this but maybe someone needs to amend the sessions here:

[https://lists.ubuntu.com/archives/ubuntu-gnome/2013-August/000511.html](https://lists.ubuntu.com/archives/ubuntu-gnome/2013-August/000511.html)

> From: Stéphane Graber <stgraber at ubuntu.com>
Date: 26 August 2013 09:00
Subject: Uploading upstart tomorrow, turning on user sessions for everyone
To: gilir at ubuntu, com at castiana, jriddell at ubuntu.com, knome at ubuntu.com,
jbicha at ubuntu.com

Hi,

I talked to every one of you independently a while back about enabling
Upstart user sessions for the desktop environment used in your flavours.

Back then I said I'd wait a couple of weeks then switch to that by
default, unfortunately due to other work commitments, traveling and
conferences I never quite got to that. With Feature Freeze fast
approaching, I'm now planning to do that tommorow unless one of you has
a very good reason not to go ahead.

The change I'd be pushing would basically be adding the following to
/etc/upstart-xsessions:
ubuntustudio
xfce
xubuntu
kde-plasma
Lubuntu
Lubuntu-Netbook
lubuntu-nexus7
lxgames
qlubuntu
gnome
gnome-fallback
gnome-fallback-compiz

All of those were tested a while back and confirmed not to cause any
obvious regressions. Some extra testers for each flavour have been
playing with that and so far I've not heard of any problem caused by
this, so I'm pretty confident it should be a painless change.

--
Stéphane Graber
Ubuntu developer

I seem to recall Jeremy Bicha requesting they add "gnome-classic" but I can't find that message right now. Maybe the "flashback" sessions need to be added too :confused:

Sorry to play hit-n-run.

---

### Post by Cavsfan on 2013-08-30
The problem with not being able to uninstall gnome-screensaver so Xscreensaver can be used needs to be fixed as well.
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074)
Jeremy Bicha agreed with that also.

---

### Post by mc4man on 2013-08-30
> **kansasnoob said:**
> I'm too busy to follow up on this but maybe someone needs to amend the sessions here:

[https://lists.ubuntu.com/archives/ubuntu-gnome/2013-August/000511.html](https://lists.ubuntu.com/archives/ubuntu-gnome/2013-August/000511.html)



I seem to recall Jeremy Bicha requesting they add "gnome-classic" but I can't find that message right now. Maybe the "flashback" sessions need to be added too :confused:

Sorry to play hit-n-run.
It's in the file - (/etc/upstart-xsessions
> # xsessions listed below are run inside an Upstart user session.
gnome
[COLOR="#0000CD"]gnome-classic[/COLOR]
gnome-fallback
gnome-fallback-compiz
kde-plasma
Lubuntu
Lubuntu-Netbook
lubuntu-nexus7
lxgames
qlubuntu
ubuntu
ubuntustudio
xfce
xubuntu


> **Cavsfan said:**
> The problem with not being able to uninstall gnome-screensaver so Xscreensaver can be used needs to be fixed as well.
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074)
Jeremy Bicha agreed with that also.
Don't see that anything was changed there, flashback still deps on gnome-screensaver

---

### Post by Cavsfan on 2013-08-30
> **Cavsfan said:**
> The problem with not being able to uninstall gnome-screensaver so Xscreensaver can be used needs to be fixed as well.
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074)
Jeremy Bicha agreed with that also.

> **mc4man said:**
> Don't see that anything was changed there, flashback still deps on gnome-screensaver

I know Jeremy wrote in that bug "it's possible to use Debian's alternative system to have a generic  screensaver package that could be listed in RequiredComponents and then  have gnome-session-flashback depend on any one of the packages that provide the generic screensaver functionality."

I'm thinking about trying your fix for it; editing the control file for gnome-session-flashback and removing gnome-session-fallback.
Is that still working for you? I had some problems and had to re-install gnome-session-flashback wiping out the fix.

If it's still working for you I will do it again. I cannot get rid of gnome-screensaver! I bring up Xscreensaver and it says Gnome screen saver is currently running.
Do I want to kill it and I click Yes but it is still running in System Monitor. I even killed it via System Monitor and some how it re-spawns lol. :)

---

### Post by Cavsfan on 2014-06-23
> **mc4man said:**
> Pretty easy to fix -- 
```
sudo nano /etc/upstart-xsessions
```

change 
gnome-fallback
gnome-fallback-compiz
to
gnome-flashback
gnome-flashback-compiz

Or maybe install the dummy fallback packages to match this dummy upgrade

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1217991](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1217991)


I know I'm going to get in trouble for this and this thread will be closed but here goes:
A few days ago I lost the ability to login to Mint 17 Gnome Flashback (with Compiz) - it would just go to a blank screen just like it did when this thread was active.

I had installed the RC and yesterday downloaded the final relase of Mint 17 (Mint's Trusty) and did a clean install. Then had the exact same problem. :o
No matter what I did Flashback would just go to a black screen.
I was about to give up and found this thread. The above sessions were named incorrectly just like mc4man stated and 
changing **gnome-fallback-compiz** to **gnome-flashback-compiz** fixed the problem. I just had to logout and back in and viola!
:popcorn:

Mc4man you are great! :D

Thanks! Now my life can proceed! :D

---

### Post by Cavsfan on 2014-06-23
It would be sweet if this got moved to general help as it saved my life definitely! And surely I am not the only one out there with this problem.

---

### Post by Elfy on 2014-06-23
being in here doesn't make it invisible :)

closed

---

