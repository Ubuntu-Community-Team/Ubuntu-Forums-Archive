---
title: "Ubuntu Gnome daily images now available."
date: 2013-03-14
forum: Ubuntu Development Version
---

### Post by philinux on 2013-03-14
[http://www.webupd8.org/2013/03/ubuntu-gnome-1304-daily-images.html](http://www.webupd8.org/2013/03/ubuntu-gnome-1304-daily-images.html)

---

### Post by jerrylamos on 2013-03-14
I test several types of Ubuntu's.  They seem to all call themselves "raring-desktop-i386.iso" (or amd64).

Why can't they call themselves kubuntu-raring... or gnome-raring or unity-raring or ....

Anyway I rename them to reduce confusion.

zsync gets pretty confused, I can point zsync to a different URL but it is still looking for different versions of ubuntu with the same file name.

I keep them all in an archive directory and boot whichever with a /etc/grub.d/40_custom entry.  Let me try different directories.  Install gets horribly confused if there are two (or more) "ubuntu-desktop-i386.iso" anywhere on any of the hard drives on any directory.

---

### Post by zika on 2013-03-14
> **jerrylamos said:**
> I test several types of Ubuntu's.  They seem to all call themselves "raring-desktop-i386.iso" (or amd64).

Why can't they call themselves kubuntu-raring... or gnome-raring or unity-raring or ....

Anyway I rename them to reduce confusion.

zsync gets pretty confused, I can point zsync to a different URL but it is still looking for different versions of ubuntu with the same file name.

I keep them all in an archive directory and boot whichever with a /etc/grub.d/40_custom entry.  Let me try different directories.  Install gets horribly confused if there are two (or more) "ubuntu-desktop-i386.iso" anywhere on any of the hard drives on any directory.```
man zsync
```
I use```
/usr/bin/zsync http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/raring-desktop-i386.iso.zsync -i raring-desktop-i386-Gnome.iso -o raring-desktop-i386-Gnome.iso
```for i386 and smilarly for other...

---

### Post by Cheesemill on 2013-03-14
> **zika said:**
> ```
man zsync
```
I use```
/usr/bin/zsync http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/raring-desktop-i386.iso.zsync -i raring-desktop-i386-Gnome.iso -o raring-desktop-i386-Gnome.iso
```for i386 and smilarly for other...

+1

I use the following script run from cron to keep all of my daily images up to date (I've just updated it to include Ubuntu Gnome as well).
```
#!/bin/sh

# Script to update Ubuntu daily iso builds.

echo "Updating Raring Ringtail Daily ISO's"
echo
cd /mnt/data/isos/Linux/Ubuntu/Raring

echo -n "Ubuntu Desktop amd64    -  "
zsync -q -i raring-desktop-amd64.iso -o raring-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso.zsync
echo "Updated"

echo -n "Ubuntu Desktop i386     -  "
zsync -q -i raring-desktop-i386.iso -o raring-desktop-i386.iso http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync
echo "Updated"

echo -n "Ubuntu Server amd64     -  "
zsync -q -i raring-server-amd64.iso -o raring-server-amd64.iso http://cdimage.ubuntu.com/ubuntu-server/daily/current/raring-server-amd64.iso.zsync
echo "Updated"

echo -n "Ubuntu Server i386      -  "
zsync -q -i raring-server-i386.iso -o raring-server-i386.iso http://cdimage.ubuntu.com/ubuntu-server/daily/current/raring-server-i386.iso.zsync
echo "Updated"

echo -n "Xubuntu Desktop amd64   -  "
zsync -q -i xraring-desktop-amd64.iso -o xraring-desktop-amd64.iso http://cdimage.ubuntu.com/xubuntu/daily-live/current/raring-desktop-amd64.iso.zsync
echo "Updated"

echo -n "Xubuntu Desktop i386    -  "
zsync -q -i xraring-desktop-i386.iso -o xraring-desktop-i386.iso http://cdimage.ubuntu.com/xubuntu/daily-live/current/raring-desktop-i386.iso.zsync
echo "Updated"

echo -n "Kubuntu Desktop amd64   -  "
zsync -q -i kraring-desktop-amd64.iso -o kraring-desktop-amd64.iso http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.iso.zsync
echo "Updated"

echo -n "Kubuntu Desktop i386    -  "
zsync -q -i kraring-desktop-i386.iso -o kraring-desktop-i386.iso http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-i386.iso.zsync
echo "Updated"

echo -n "Lubuntu Desktop amd64   -  "
zsync -q -i lraring-desktop-amd64.iso -o lraring-desktop-amd64.iso http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-amd64.iso.zsync
echo "Updated"

echo -n "Lubuntu Desktop i386    -  "
zsync -q -i lraring-desktop-i386.iso -o lraring-desktop-i386.iso http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-i386.iso.zsync
echo "Updated"

echo -n "Lubuntu Alternate amd64 -  "
zsync -q -i lraring-alternate-amd64.iso -o lraring-alternate-amd64.iso http://cdimage.ubuntu.com/lubuntu/daily/current/raring-alternate-amd64.iso.zsync
echo "Updated"

echo -n "Lubuntu Alternate i386  -  "
zsync -q -i lraring-alternate-i386.iso -o lraring-alternate-i386.iso http://cdimage.ubuntu.com/lubuntu/daily/current/raring-alternate-i386.iso.zsync
echo "Updated"

echo -n "Gubuntu Alternate amd64 -  "
zsync -q -i graring-desktop-amd64.iso -o graring-desktop-amd64.iso http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/raring-desktop-amd64.iso.zsync
echo "Updated"

echo -n "Gubuntu Alternate i386  -  "
zsync -q -i graring-desktop-i386.iso -o graring-desktop-i386.iso http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/raring-desktop-i386.iso.zsync
echo "Updated"

rm *old

echo -n "Mini ISO amd64          -  "
wget -q -N http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-amd64/current/images/netboot/mini.iso
echo "Updated"
echo
echo "All Raring ISO's updated."
```

---

### Post by jbicha on 2013-03-14
> **jerrylamos said:**
> I test several types of Ubuntu's.  They seem to all call themselves "raring-desktop-i386.iso" (or amd64).

Why can't they call themselves kubuntu-raring... or gnome-raring or unity-raring or ....

Would you be interested in filing a bug on that? I'm not sure the right place, but you could try filing against livecd-rootfs.

---

### Post by ronacc on 2013-03-14
I'm not sure they would call that a bug since the greeter/login  give you a choice of which de to start .

edit: I often have several de's all in one install .

---

### Post by ronacc on 2013-03-14
I tried to install ubuntu-gnome amd64 both the original and a zsync'd one .  The installer hangs on both . I tried both direct install without going to the live session  and also from the live session .

---

### Post by Stinger on 2013-03-15
I successfully installed the daily live image (amd64) from the live-session, have to wiggle the mouse or hit the keyboard during install though to prevent idle which will freeze the screen.
So If you stay with Gnome 3.6 every thing seems to work.
I tried to upgrade to pre Gnome 3.8 by using the Gnome3 ppa, the update itself went well but when i restarted the only thing I got was the blue blinds background with a mouse courser.

I tried hitting Ctrl-Alt-Del which brought up the log out dialog box and asked if I wanted to log out from GDM-session ? Strange...

I tried pushing the power button once instead which brought up the shutdown dialog box telling me again I was logged in as GDM ?

Anyone else having this issue with pre Gnome 3.8 ?

---

### Post by sgage on 2013-03-15
> **Stinger said:**
> I successfully installed the daily live image (amd64) from the live-session, have to wiggle the mouse or hit the keyboard during install though to prevent idle which will freeze the screen.
So If you stay with Gnome 3.6 every thing seems to work.
I tried to upgrade to pre Gnome 3.8 by using the Gnome3 ppa, the update itself went well but when i restarted the only thing I got was the blue blinds background with a mouse courser.

I tried hitting Ctrl-Alt-Del which brought up the log out dialog box and asked if I wanted to log out from GDM-session ? Strange...

I tried pushing the power button once instead which brought up the shutdown dialog box telling me again I was logged in as GDM ?

Anyone else having this issue with pre Gnome 3.8 ?

Everything fine here with the gnome3 ppa.

---

### Post by Stinger on 2013-03-15
@ sgage
And you are having an installation with Ubuntu GNOME only and using GDM as login manager like I am ? :-k

---

### Post by ronacc on 2013-03-15
the ubiquity used in ubuntu-gnome don't like my box, I have tried several installs including a freshly d/l'd . iso  and ubiquity always hangs at the second screen ( I tried moving the mouse as Stinger suggested but no luck) it isnt going to sleep just ubiquity hanging . I had the same problem with the reglar ubuntu early in raring but todays daily of that installed with no problem . I guess i'll just keep trying until they update the ubiquity in Ubuntu-gnome .

---

### Post by kansasnoob on 2013-03-15
> **ronacc said:**
> the ubiquity used in ubuntu-gnome don't like my box, I have tried several installs including a freshly d/l'd . iso  and ubiquity always hangs at the second screen ( I tried moving the mouse as Stinger suggested but no luck) it isnt going to sleep just ubiquity hanging . I had the same problem with the reglar ubuntu early in raring but todays daily of that installed with no problem . I guess i'll just keep trying until they update the ubiquity in Ubuntu-gnome .

Sounds like this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

---

### Post by ronacc on 2013-03-15
thanks kansasnoob , it was worth a look but i'm not even getting that far (partman) . For me it hangs as soon as I hit continue from the screen where it shows if ou are connected to the internet  and asks if you want to d/l the updates while installing , I've tried various conbinations but all hang . next try I'll check the logs before I shut down , the live session works even when ubiquity is hung .

---

### Post by ronacc on 2013-03-15
update I tried another install and this time read the syslog after the hang , it reads similar to (not exactly) the same as some of those in the bug you referenced so it may be partman after all . either that or it may be trying to run wubi because it sees the windows install on the same box since it references that install in the syslog .

---

### Post by cariboo on 2013-03-16
I ran the iso build script last weekend, so I really don't need the daily image right now, everything works as it should on my atom powered netbook, I even got to test what happens when I pull the plug, and then leave for a couple of hours, the system went into suspend, and recovered gracefully when I plugged the power cord back in.

The only problem I seem to have is that when running a second monitor, I can only successfully set the resolution to 1280X1024, but that may be more of a hardware limitation, than the intel graphics driver.

I plan on enabling the 3 ppas this weekend, as the last time I did it, my system went into a constant loop, using up all the ram, then restarting, and starting the cycle all over again.

---

### Post by jinjorge on 2013-03-18
> **Cheesemill said:**
> +1

I use the following script run from cron to keep all of my daily images up to date (I've just updated it to include Ubuntu Gnome as well).
```
#!/bin/sh

# Script to update Ubuntu daily iso builds.

echo "Updating Raring Ringtail Daily ISO's"
echo
cd /mnt/data/isos/Linux/Ubuntu/Raring

echo -n "Ubuntu Desktop amd64    -  "
zsync -q -i raring-desktop-amd64.iso -o raring-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso.zsync
echo "Updated"

echo -n "Ubuntu Desktop i386     -  "
zsync -q -i raring-desktop-i386.iso -o raring-desktop-i386.iso http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync
echo "Updated"

echo -n "Ubuntu Server amd64     -  "
zsync -q -i raring-server-amd64.iso -o raring-server-amd64.iso http://cdimage.ubuntu.com/ubuntu-server/daily/current/raring-server-amd64.iso.zsync
echo "Updated"

echo -n "Ubuntu Server i386      -  "
zsync -q -i raring-server-i386.iso -o raring-server-i386.iso http://cdimage.ubuntu.com/ubuntu-server/daily/current/raring-server-i386.iso.zsync
echo "Updated"

echo -n "Xubuntu Desktop amd64   -  "
zsync -q -i xraring-desktop-amd64.iso -o xraring-desktop-amd64.iso http://cdimage.ubuntu.com/xubuntu/daily-live/current/raring-desktop-amd64.iso.zsync
echo "Updated"

echo -n "Xubuntu Desktop i386    -  "
zsync -q -i xraring-desktop-i386.iso -o xraring-desktop-i386.iso http://cdimage.ubuntu.com/xubuntu/daily-live/current/raring-desktop-i386.iso.zsync
echo "Updated"

echo -n "Kubuntu Desktop amd64   -  "
zsync -q -i kraring-desktop-amd64.iso -o kraring-desktop-amd64.iso http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.iso.zsync
echo "Updated"

echo -n "Kubuntu Desktop i386    -  "
zsync -q -i kraring-desktop-i386.iso -o kraring-desktop-i386.iso http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-i386.iso.zsync
echo "Updated"

echo -n "Lubuntu Desktop amd64   -  "
zsync -q -i lraring-desktop-amd64.iso -o lraring-desktop-amd64.iso http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-amd64.iso.zsync
echo "Updated"

echo -n "Lubuntu Desktop i386    -  "
zsync -q -i lraring-desktop-i386.iso -o lraring-desktop-i386.iso http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-i386.iso.zsync
echo "Updated"

echo -n "Lubuntu Alternate amd64 -  "
zsync -q -i lraring-alternate-amd64.iso -o lraring-alternate-amd64.iso http://cdimage.ubuntu.com/lubuntu/daily/current/raring-alternate-amd64.iso.zsync
echo "Updated"

echo -n "Lubuntu Alternate i386  -  "
zsync -q -i lraring-alternate-i386.iso -o lraring-alternate-i386.iso http://cdimage.ubuntu.com/lubuntu/daily/current/raring-alternate-i386.iso.zsync
echo "Updated"

echo -n "Gubuntu Alternate amd64 -  "
zsync -q -i graring-desktop-amd64.iso -o graring-desktop-amd64.iso http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/raring-desktop-amd64.iso.zsync
echo "Updated"

echo -n "Gubuntu Alternate i386  -  "
zsync -q -i graring-desktop-i386.iso -o graring-desktop-i386.iso http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/raring-desktop-i386.iso.zsync
echo "Updated"

rm *old

echo -n "Mini ISO amd64          -  "
wget -q -N http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-amd64/current/images/netboot/mini.iso
echo "Updated"
echo
echo "All Raring ISO's updated."
```

awesome script!! Thanks for sharing.

---

### Post by rsrocha on 2013-03-18
I installed the daily image to the hard drive and when booting for first time after install completed i dont get any login screen. Just the blue gnome background and the mouse pointer.

Am i doing anything wrong?

---

### Post by Stinger on 2013-03-19
@ rsrocha
I'm getting exactly the same with the Gnome3 ppa enabled as [I reported earlier]("http://ubuntuforums.org/showthread.php?t=2125539&p=12558547#post12558547")

So unless a solution comes up, I'm waiting for the beta release.

---

### Post by kansasnoob on 2013-03-22
Ubuntu GNOME images are now on the QA Tracker also:

[ATTACH=CONFIG]240426[/ATTACH]

The i386 images and testcases are here:

[http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/40290/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/40290/testcases)

The amd64 images and testcases are here:

[http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/40289/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/40289/testcases)

Edit: I was a bit premature with this announcement :redface:

Stéphane Graber is still working on getting the Ubuntu GNOME images synced from daily to the QA Tracker but we're very close :)

---

### Post by Stinger on 2013-03-22
@ kansasnoob

Do you know if there will be any testing of upgrading using the gnome3 ppa ?

It would be quite relevant for those of us who would like a Gnome 3.8 installation IMO. 

Cheers :)

---

### Post by kansasnoob on 2013-03-22
> **Stinger said:**
> @ kansasnoob

Do you know if there will be any testing of upgrading using the gnome3 ppa ?

It would be quite relevant for those of us who would like a Gnome 3.8 installation IMO. 

Cheers :)

There have been recent questions about the [GNOME3 PPA]("https://launchpad.net/~gnome3-team/+archive/gnome3") on the [mailing list]("https://lists.ubuntu.com/archives/ubuntu-gnome/") and my personal opinion is that one should follow the instructions listed with the PPA, namely:

> Before upgrading your system to a new Ubuntu release (i.e. from Ubuntu 11.10 to 13.04), you should probably run ppa-purge ppa:gnome3-team/gnome3 first.

And:

> === Ubuntu 13.04 (Raring) ===
GNOME 3.8 that won't make it into the normal Ubuntu 13.04 repositories. Other parts of GNOME 3.8 are available in the [https://launchpad.net/~gnome3-team/+archive/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/gnome3-staging) PPA but **[COLOR="#FF0000"]beware that many of those components have known regressions from their GNOME 3.6 versions[/COLOR]**.

AFAIK the GNOME 3.8 RC was only released yesterday and final is not due for another week or so, meaning that it's far too young and immature to expect it to be stable ;)

I do know that many of the extensions used with 3.6 do not yet work with 3.8, in fact some of the old 3.4 extensions still haven't been properly updated to work with 3.6 :(

---

### Post by sgage on 2013-03-22
> **kansasnoob said:**
> There have been recent questions about the [GNOME3 PPA]("https://launchpad.net/~gnome3-team/+archive/gnome3") on the [mailing list]("https://lists.ubuntu.com/archives/ubuntu-gnome/") and my personal opinion is that one should follow the instructions listed with the PPA, namely:



And:



AFAIK the GNOME 3.8 RC was only released yesterday and final is not due for another week or so, meaning that it's far too young and immature to expect it to be stable ;)

I do know that many of the extensions used with 3.6 do not yet work with 3.8, in fact some of the old 3.4 extensions still haven't been properly updated to work with 3.6 :(

There is a separate thread about extensions going on - other than 3.4 extensions abandoned by their developers, most all of the 3.4 ones work on 3.6. Already many (most all of the ones I use) of the 3.6 extensions work on 3.8 with a tweak to their metadata.json files.

---

### Post by Stinger on 2013-03-22
@ kansasnoob

Yeah I know " I have been warned " and all that, but I don't mind breakage as long as I have a chance to recover :wink:

As for the extensions, they'll only work if their author will port them to the next Gnome version.
There has been some talk on having ["Automatic Extension Updates"]("http://worldofgnome.org/gnome-3-8-features-automatic-extension-updates/") but I think thats a work still in progress :lol:  

BTW I stumbled over this, ["How to fix the broken GDM in GNOME 3.8 Beta"]("http://worldofgnome.org/how-to-fix-the-broken-gdm-in-gnome-3-8-beta/") on worldofgnome.
Maybe thats the bug I was referring to [earlier on this thread]("http://ubuntuforums.org/showthread.php?t=2125539&p=12558547#post12558547") ?

---

### Post by Cavsfan on 2013-03-22
Anyone see this:

[[COLOR=blue]_GNOME 3.8 Release Candidate Now Available_[/COLOR]]("http://www.phoronix.com/scan.php?page=news_item&px=MTMzMjk")

As I have a spare partition, I am downloadingt the ISO from here:
(off of the mailing list on the first link)

[[COLOR=blue]_GNOME 3.7.92 Release Candidate!_[/COLOR]]("https://mail.gnome.org/archives/devel-announce-list/2013-March/msg00004.html")

---

### Post by Cavsfan on 2013-03-22
> **Cavsfan said:**
> Anyone see this:

[[COLOR=blue]_GNOME 3.8 Release Candidate Now Available_[/COLOR]]("http://www.phoronix.com/scan.php?page=news_item&px=MTMzMjk")

As I have a spare partition, I am downloadingt the ISO from here:
(off of the mailing list on the first link)

[[COLOR=blue]_GNOME 3.7.92 Release Candidate!_[/COLOR]]("https://mail.gnome.org/archives/devel-announce-list/2013-March/msg00004.html")

I tried to install from that iso and it would not work. Said it got an error and I had to login again..... I had to press reset and remove the DVD,

Guess I'll wait until March 27th for the 3.8 stable release. [https://live.gnome.org/ThreePointSeven](https://live.gnome.org/ThreePointSeven)

---

