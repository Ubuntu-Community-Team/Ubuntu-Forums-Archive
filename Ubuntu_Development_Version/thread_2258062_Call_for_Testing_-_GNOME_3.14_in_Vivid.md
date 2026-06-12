---
title: "Call for Testing - GNOME 3.14 in Vivid"
date: 2014-12-24
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-12-24
Tim Lunn recntly put out a [call for testing]("https://lists.launchpad.net/ubuntugnome-qa/msg00660.html") GNOME 3.14 in Vivid:

> We will be landing a big update into vivid early next week which is now staged on ppa:ubuntu-gnome-packaging/core3.14. Please test and let us
know of any issues you might find. **[COLOR="#FF0000"]Needs to be installed over a clean vivid system or all gnome3-team ppa's purged first[/COLOR]**.

I ran into two problems; (1) highlighted items in the launcher remain highlighted even after moving the mouse, and (2) the frequently used menu items are garbled:

[ATTACH=CONFIG]258766[/ATTACH]

I wasn't sure what package to file a bug report against so I just [told Tim on the mailing list]("https://lists.launchpad.net/ubuntugnome-qa/msg00665.html"):

> Sorry to take so long. I notice that if I "mouse-over" menu items in the launcher they stay highlighted even after moving the mouse away from the item, and if I open the menu by selecting the bottom item in the launcher the menu is very garbled. Since a picture is worth a thousand words I'll attach a screenshot.

I've so far only tried this in Ubuntu GNOME but I'll try it in Ubuntu soon. Ultimately it would be nice to see this tested in all the flavors just to be sure we're not breaking things for others :redface:

---

### Post by ventrical on 2014-12-24
To the devs working on this :

Very very awsome with the 'show applications' theme. This is everything that unity8 and desktop next is not.

*note*

  I have been running a gnome3 install since vivid inception. It has not hic-upped once.  The vortex-graphicals are really sassy and effervescent. People will take notice. Great work ...

Regards..

---

### Post by ventrical on 2014-12-24
> **kansasnoob said:**
> Tim Lunn recntly put out a [call for testing]("https://lists.launchpad.net/ubuntugnome-qa/msg00660.html") GNOME 3.14 in Vivid:



I ran into two problems; (1) highlighted items in the launcher remain highlighted even after moving the mouse, and (2) the frequently used menu items are garbled:

[ATTACH=CONFIG]258766[/ATTACH]

I wasn't sure what package to file a bug report against so I just [told Tim on the mailing list]("https://lists.launchpad.net/ubuntugnome-qa/msg00665.html"):





I've so far only tried this in Ubuntu GNOME but I'll try it in Ubuntu soon. Ultimately it would be nice to see this tested in all the flavors just to be sure we're not breaking things for others :redface:

When working properly the 'show applications' items will spew out from the  icon in a sort of vortex and then place themsleves on to the screen :)  No problems here with frequently used.  It's  awesome work they did on this.

Regards.

---

### Post by sammiev on 2014-12-24
I have been using vivid gnome from the start and look forward to testing the updates. Will likely be a few more days before I can play.

---

### Post by grahammechanical on 2014-12-24
I am in and I am not getting the effect that Kansasnoob reports. Both Fequently Used and All spill the application icons into the Dash in a quick and orderly fashion.

There is definitely a left screen edge mouse swip guesture to reveal the combined launcher and dash. It works intermittenly when an application is open but with an empty workspace a left edge swipe guesture reveals the launcher/dash.

The help application is crashing. Yelp closed unexpectedly = SIGSEGV etc.

Regards.

---

### Post by ventrical on 2014-12-25
Mouse will freeze, screen will lock after succesive spills-to-screen  from apps icon. Also..  what appears to be a ?unity-panel? auto hide function :)

Regards..

---

### Post by harry332 on 2014-12-25
I have installed all those, that are needed to run Gnome-shell DE with GDM** only** and they do work just fine.
Gnome-backgrounds is already in Vivid
I installed clutter, gnome-control-center, gnome-shell, gnome-settings-daemon, gnome-themes-standard, mutter.

More info:
I do not have any issues with mouse-over nor menu launcher highlighting nor opening the menu with the bottom launcher.
Everything works just fine.

---

### Post by zika on 2014-12-25
It works nicelly for the first couple of minutes. Hide bar also works nicely.

---

### Post by VinDSL on 2014-12-25
> **ventrical said:**
> I have been running a gnome3 install since vivid inception. It has not hic-upped once. 

Same here!  Actually, I've been using the Gnome-Shell DE for a couple of years...

I can't think of one issue with GS xxx in Vivid.

I do get occasional non-critical warning/error dialogs during boot, but it has EVERYTHING to do with systemd and/or the Linux kernel RCs that I run, and NOTHING to do with Gnome.

Tim has been doing a good job, behind the scenes!  :)

Hrm...

I guess I'll test GS 3.14 Staging on a USB stick install.  I don't want to do a wash, rinse, and restyle on my HD.

---

### Post by zika on 2014-12-25
A bit radical?```
:~$ sudo apt-get dist-upgrade [sudo] password for zika: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  libopts25 ntp
Use 'apt-get autoremove' to remove them.
Done
The following NEW packages will be installed:
  libgeocode-glib0
The following packages will be upgraded:
  gnome-control-center gnome-control-center-data gnome-settings-daemon
  gnome-settings-daemon-schemas
4 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8457 kB of archives.
After this operation, 18,4 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```I'll have to catch some time to read changelog(s). Before I loose automatic time synchronization due to forgetfulness until next &#8222;autoremove&#8220;... ;)

---

### Post by grahammechanical on 2014-12-25
The lock screen requires a swipe up from the bottom edge to reveal the password panel. It is a neat little trick. Then after switching to the TV mode for several minutes and then switching back to HDMI when I swiped upwards to reveal the lock screen password panel, the thing crashed. It restored itself all right. But the applications I had open were shut down and incorrectly at that. As expected with such a crash.

Reproducible bug? Do not know as yet.

Regards.

---

### Post by ventrical on 2014-12-25
> **zika said:**
> A bit radical?```
:~$ sudo apt-get dist-upgrade [sudo] password for zika: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  libopts25 ntp
Use 'apt-get autoremove' to remove them.
Done
The following NEW packages will be installed:
  libgeocode-glib0
The following packages will be upgraded:
  gnome-control-center gnome-control-center-data gnome-settings-daemon
  gnome-settings-daemon-schemas
4 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8457 kB of archives.
After this operation, 18,4 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```I'll have to catch some time to read changelog(s). Before I loose automatic time synchronization due to forgetfulness until next „autoremove“... ;)


I didn't get those ones.

```

The following packages have been kept back:
  cabextract
The following packages will be upgraded:
  binutils gir1.2-mutter-3.0 gnome-shell gnome-shell-common
  gnome-shell-extensions libmutter0e mutter mutter-common unzip
9 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 4,986 kB of archives.
After this operation, 14.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

---

### Post by ventrical on 2014-12-25
> **zika said:**
> It works nicelly for the first couple of minutes. Hide bar also works nicely.

All of a sudden that (hide bar) stopped working after startup.

edit:

 It's working but the mouse is very touchy . I have to try several clicks to get that panel to pop out like it did before. It does not slide like it did. Very abrupt now.

---

### Post by ventrical on 2014-12-25
> **VinDSL said:**
> Same here!  Actually, I've been using the Gnome-Shell DE for a couple of years...

I can't think of one issue with GS xxx in Vivid.

I do get occasional non-critical warning/error dialogs during boot, but it has EVERYTHING to do with systemd and/or the Linux kernel RCs that I run, and NOTHING to do with Gnome.

Tim has been doing a good job, behind the scenes!  :)

Hrm...

I guess I'll test GS 3.14 Staging on a USB stick install.  I don't want to do a wash, rinse, and restyle on my HD.

Yes :)  Looks like some bugs are popping up now. Look likes a few canaries (quetzels) on the cave floor. :) lol

---

### Post by zika on 2014-12-26
> **ventrical said:**
> I didn't get those ones.

```

The following packages have been kept back:
  cabextract
The following packages will be upgraded:
  binutils gir1.2-mutter-3.0 gnome-shell gnome-shell-common
  gnome-shell-extensions libmutter0e mutter mutter-common unzip
9 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 4,986 kB of archives.
After this operation, 14.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```After I applied autoremove and manually installed ntp no more offers for autoremove of ntp.
It seems that GDM 3.14 does not honor autologin switch.
Update&#8321;: Looks like turning that switch off/on does do the trick.
Update&#8322;: HideBar extension does not start on on reboot and must be manually turned on (almost) always.
Update&#8322;.&#8321;: That [SIZE=2][SIZE=2][COLOR=#252525][FONT=sans-serif]&#7936;&#956;&#957;&#951;&#963;&#943;&#945; [/FONT][/COLOR][/SIZE]happens only in UpStart session, in SystemD session everything is OK.[/SIZE]
Update&#8323;: [http://ubuntuforums.org/showthread.php?t=2249915&p=13195223#post13195223](http://ubuntuforums.org/showthread.php?t=2249915&p=13195223#post13195223)

---

### Post by zika on 2014-12-30
[http://www.phoronix.com/scan.php?page=news_item&px=MTg3NTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTg3NTQ)
Any news of PPA to offer 3.16?

---

### Post by harry332 on 2014-12-30
> **zika said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=MTg3NTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTg3NTQ)
Any news of PPA to offer 3.16?

Of course 3.16 is very early in its development (3.15.3).
However this PPA has some of it (gnome-shell, gnome-themes-standard and GTK+3):
[https://launchpad.net/~ricotz/+archive/ubuntu/testing/+packages?field.name_filter=&field.status_filter=published&field.series_filter=vivid](https://launchpad.net/~ricotz/+archive/ubuntu/testing/+packages?field.name_filter=&field.status_filter=published&field.series_filter=vivid)

---

### Post by zika on 2014-12-30
> **harry332 said:**
> Of course 3.16 is very early in its development (3.15.3).
However this PPA has some of it (gnome-shell, gnome-themes-standard and GTK+3):
[https://launchpad.net/~ricotz/+archive/ubuntu/testing/+packages?field.name_filter=&field.status_filter=published&field.series_filter=vivid](https://launchpad.net/~ricotz/+archive/ubuntu/testing/+packages?field.name_filter=&field.status_filter=published&field.series_filter=vivid)Regular subscriber. Forgot to put a smiley after my question. Mea culpa.
Update&#8321;: While on this off-topic: anyone else have lost keyboard shortcuts in Ricotz's version of Gnome-Shell? Will look into it once I get some time for that... It is fast though and that is what keeps me trying it...
Update&#8322;: Back on-topic: ppa:ubuntu-gnome-packaging/core3.14 stuff is working nicely. Stable and fast. If You introduce ppa:ricotz/testing+ppa:gnome3-team/gnome3+ppa:gnome3-team/gnome3-staging then lot of stuff becomes unstable and uncoherent. It is nice that ppa-purge goes nicely and without hickups. So, nice testing of a nice stuff coming into Vivid.
Update&#8323;: Funny but GS seems to run faster if started from LightDM. I've tried that just to see if there is an issue mentioned in [http://ubuntuforums.org/showthread.php?t=2259396](http://ubuntuforums.org/showthread.php?t=2259396)

---

### Post by sgage on 2015-01-03
[Deleted - I misread the OP]

---

### Post by dino99 on 2015-01-03
I have upgraded to all the gnome3-staging packages a few weeks back. Everything run smootly on a i386 gnome-shell session (booted with systemd)
[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging)

---

### Post by zika on 2015-01-05
It seems that a process of transfering packages from PPA to vivid/proposed is going on... Nice.
Will PPA remain alive or it served its purpose...?

---

### Post by ventrical on 2015-01-05
I just went ahead and removed it.

```

ventrical@ventrical-System-Product-Name:~$ sudo add-apt-repository --remove ppa:ubuntu-gnome-packaging/core3.14
[sudo] password for ventrical: 
 
 More info: https://launchpad.net/~ubuntu-gnome-packaging/+archive/ubuntu/core3.14
Press [ENTER] to continue or ctrl-c to cancel removing it

ventrical@ventrical-System-Product-Name:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-24 linux-headers-3.16.0-24-generic
  linux-image-3.16.0-24-generic linux-image-extra-3.16.0-24-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude aptitude-common aptitude-doc-en libcwidget3
Suggested packages:
  tasksel debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude aptitude-common aptitude-doc-en libcwidget3 ppa-purge
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,788 kB of archives.
After this operation, 12.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ vivid/main libcwidget3 amd64 0.5.17-2ubuntu1 [328 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ vivid/main aptitude-common all 0.6.11-1ubuntu2 [787 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ vivid/main aptitude amd64 0.6.11-1ubuntu2 [1,402 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ vivid/main aptitude-doc-en all 0.6.11-1ubuntu2 [264 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe ppa-purge all 0.2.8+bzr57 [5,704 B]
Fetched 2,788 kB in 7s (377 kB/s)                                              
Selecting previously unselected package libcwidget3:amd64.
(Reading database ... 214572 files and directories currently installed.)
Preparing to unpack .../libcwidget3_0.5.17-2ubuntu1_amd64.deb ...
Unpacking libcwidget3:amd64 (0.5.17-2ubuntu1) ...
Selecting previously unselected package aptitude-common.
Preparing to unpack .../aptitude-common_0.6.11-1ubuntu2_all.deb ...
Unpacking aptitude-common (0.6.11-1ubuntu2) ...
Selecting previously unselected package aptitude.
Preparing to unpack .../aptitude_0.6.11-1ubuntu2_amd64.deb ...
Unpacking aptitude (0.6.11-1ubuntu2) ...
Selecting previously unselected package aptitude-doc-en.
Preparing to unpack .../aptitude-doc-en_0.6.11-1ubuntu2_all.deb ...
Unpacking aptitude-doc-en (0.6.11-1ubuntu2) ...
Selecting previously unselected package ppa-purge.
Preparing to unpack .../ppa-purge_0.2.8+bzr57_all.deb ...
Unpacking ppa-purge (0.2.8+bzr57) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up libcwidget3:amd64 (0.5.17-2ubuntu1) ...
Setting up aptitude-common (0.6.11-1ubuntu2) ...
Setting up aptitude (0.6.11-1ubuntu2) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode
Setting up aptitude-doc-en (0.6.11-1ubuntu2) ...
Setting up ppa-purge (0.2.8+bzr57) ...
Processing triggers for libc-bin (2.19-13ubuntu3) ...
ventrical@ventrical-System-Product-Name:~$ sudo ppa-purge ppa:ubuntu-gnome-packaging/core3.14
Updating packages lists
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/vivid/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: ubuntu-gnome-packaging core3.14
Package revert list generated:
 gir1.2-clutter-1.0/vivid gir1.2-mutter-3.0/vivid 
gnome-accessibility-themes/vivid gnome-backgrounds/vivid 
gnome-control-center/vivid gnome-control-center-data/vivid 
gnome-control-center-shared-data/vivid gnome-settings-daemon/vivid 
gnome-settings-daemon-schemas/vivid gnome-shell/vivid gnome-shell-common/vivid 
gnome-shell-extensions/vivid gnome-themes-standard:amd64/vivid 
gnome-themes-standard-data/vivid libclutter-1.0-0:amd64/vivid 
libclutter-1.0-common/vivid libgnome-control-center1/vivid libmutter0e/vivid 
mutter/vivid mutter-common/vivid plymouth-theme-ubuntu-gnome-logo/vivid 
plymouth-theme-ubuntu-gnome-text/vivid ubuntu-gnome-default-settings/vivid 
ubuntu-gnome-desktop/vivid

Updating packages lists
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/vivid/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release 'vivid' for 'libmutter0e' was not found
Unable to find an archive "vivid" for the package "libmutter0e"
Unable to find an archive "vivid" for the package "libmutter0e"
The following packages will be DOWNGRADED:
  gir1.2-clutter-1.0 gir1.2-mutter-3.0 gnome-control-center 
  gnome-control-center-data gnome-control-center-shared-data 
  gnome-settings-daemon gnome-settings-daemon-schemas gnome-shell 
  gnome-shell-common gnome-shell-extensions libclutter-1.0-0 
  libclutter-1.0-common libgnome-control-center1 mutter mutter-common 
  plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text 
  ubuntu-gnome-default-settings 
The following NEW packages will be installed:
  libmutter0d{a} 
The following packages will be REMOVED:
  libmutter0e{u} libxcb-randr0{u} libxcb-xkb1{u} libxkbcommon-x11-0{u} 
The following packages will be upgraded:
  gnome-accessibility-themes gnome-themes-standard 
  gnome-themes-standard-data 
The following partially installed packages will be configured:
  cups printer-driver-gutenprint 
3 packages upgraded, 1 newly installed, 18 downgraded, 4 to remove and 14 not upgraded.
Need to get 8,248 kB/8,345 kB of archives. After unpacking 23.4 MB will be freed.
Do you want to continue? [Y/n/?] y
Get: 1 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe gir1.2-mutter-3.0 amd64 3.12.2-1ubuntu4 [19.6 kB]
Get: 2 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe gnome-shell-extensions all 3.12.2-1ubuntu1 [127 kB]
Get: 3 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe gnome-control-center amd64 1:3.12.1-5ubuntu3 [1,445 kB]
Get: 4 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe gnome-control-center-data all 1:3.12.1-5ubuntu3 [439 kB]
Get: 5 http://ca.archive.ubuntu.com/ubuntu/ vivid/main gnome-settings-daemon-schemas all 3.12.2-1ubuntu4 [47.4 kB]
Get: 6 http://ca.archive.ubuntu.com/ubuntu/ vivid/main gnome-settings-daemon amd64 3.12.2-1ubuntu4 [578 kB]
Get: 7 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe gnome-shell amd64 3.12.2-1ubuntu8 [591 kB]
Get: 8 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe gnome-shell-common all 3.12.2-1ubuntu8 [596 kB]
Get: 9 http://ca.archive.ubuntu.com/ubuntu/ vivid/main gir1.2-clutter-1.0 amd64 1.18.4-1ubuntu1 [104 kB]
Get: 10 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe mutter amd64 3.12.2-1ubuntu4 [17.8 kB]
Get: 11 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe mutter-common all 3.12.2-1ubuntu4 [611 kB]
Get: 12 http://ca.archive.ubuntu.com/ubuntu/ vivid/main libclutter-1.0-0 amd64 1.18.4-1ubuntu1 [521 kB]
Get: 13 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe libmutter0d amd64 3.12.2-1ubuntu4 [375 kB]
Get: 14 http://ca.archive.ubuntu.com/ubuntu/ vivid/main gnome-accessibility-themes all 3.14.2.3-0ubuntu1 [2,346 kB]
Get: 15 http://ca.archive.ubuntu.com/ubuntu/ vivid/main gnome-themes-standard amd64 3.14.2.3-0ubuntu1 [14.6 kB]
Get: 16 http://ca.archive.ubuntu.com/ubuntu/ vivid/main gnome-themes-standard-data all 3.14.2.3-0ubuntu1 [55.1 kB]
Get: 17 http://ca.archive.ubuntu.com/ubuntu/ vivid/main libgnome-control-center1 amd64 1:3.12.1-5ubuntu3 [88.4 kB]
Get: 18 http://ca.archive.ubuntu.com/ubuntu/ vivid/main gnome-control-center-shared-data all 1:3.12.1-5ubuntu3 [187 kB]
Get: 19 http://ca.archive.ubuntu.com/ubuntu/ vivid/main libclutter-1.0-common all 1.18.4-1ubuntu1 [85.1 kB]
Fetched 8,248 kB in 22s (367 kB/s)                                              
dpkg: warning: downgrading gir1.2-mutter-3.0 from 3.14.3-0ubuntu1~vivid2 to 3.12.2-1ubuntu4
(Reading database ... 214850 files and directories currently installed.)
Preparing to unpack .../gir1.2-mutter-3.0_3.12.2-1ubuntu4_amd64.deb ...
Unpacking gir1.2-mutter-3.0 (3.12.2-1ubuntu4) over (3.14.3-0ubuntu1~vivid2) ...
dpkg: warning: downgrading gnome-shell-extensions from 3.14.3-0ubuntu1~vivid1 to 3.12.2-1ubuntu1
Preparing to unpack .../gnome-shell-extensions_3.12.2-1ubuntu1_all.deb ...
Unpacking gnome-shell-extensions (3.12.2-1ubuntu1) over (3.14.3-0ubuntu1~vivid1) ...
dpkg: warning: downgrading gnome-control-center from 1:3.14.2-2ubuntu1~ppa2 to 1:3.12.1-5ubuntu3
Preparing to unpack .../gnome-control-center_1%3a3.12.1-5ubuntu3_amd64.deb ...
Unpacking gnome-control-center (1:3.12.1-5ubuntu3) over (1:3.14.2-2ubuntu1~ppa2) ...
dpkg: warning: downgrading gnome-control-center-data from 1:3.14.2-2ubuntu1~ppa2 to 1:3.12.1-5ubuntu3
Preparing to unpack .../gnome-control-center-data_1%3a3.12.1-5ubuntu3_all.deb ...
Unpacking gnome-control-center-data (1:3.12.1-5ubuntu3) over (1:3.14.2-2ubuntu1~ppa2) ...
dpkg: warning: downgrading gnome-settings-daemon-schemas from 3.14.2-2ubuntu1~ppa3 to 3.12.2-1ubuntu4
Preparing to unpack .../gnome-settings-daemon-schemas_3.12.2-1ubuntu4_all.deb ...
Unpacking gnome-settings-daemon-schemas (3.12.2-1ubuntu4) over (3.14.2-2ubuntu1~ppa3) ...
dpkg: warning: downgrading gnome-settings-daemon from 3.14.2-2ubuntu1~ppa3 to 3.12.2-1ubuntu4
Preparing to unpack .../gnome-settings-daemon_3.12.2-1ubuntu4_amd64.deb ...
Unpacking gnome-settings-daemon (3.12.2-1ubuntu4) over (3.14.2-2ubuntu1~ppa3) ...
dpkg: warning: downgrading gnome-shell from 3.14.3-0ubuntu1~vivid1 to 3.12.2-1ubuntu8
Preparing to unpack .../gnome-shell_3.12.2-1ubuntu8_amd64.deb ...
Unpacking gnome-shell (3.12.2-1ubuntu8) over (3.14.3-0ubuntu1~vivid1) ...
dpkg: warning: downgrading gnome-shell-common from 3.14.3-0ubuntu1~vivid1 to 3.12.2-1ubuntu8
Preparing to unpack .../gnome-shell-common_3.12.2-1ubuntu8_all.deb ...
Unpacking gnome-shell-common (3.12.2-1ubuntu8) over (3.14.3-0ubuntu1~vivid1) ...
dpkg: warning: downgrading gir1.2-clutter-1.0 from 1.20.0-1~ppa1 to 1.18.4-1ubuntu1
Preparing to unpack .../gir1.2-clutter-1.0_1.18.4-1ubuntu1_amd64.deb ...
Unpacking gir1.2-clutter-1.0 (1.18.4-1ubuntu1) over (1.20.0-1~ppa1) ...
dpkg: warning: downgrading mutter from 3.14.3-0ubuntu1~vivid2 to 3.12.2-1ubuntu4
Preparing to unpack .../mutter_3.12.2-1ubuntu4_amd64.deb ...
Unpacking mutter (3.12.2-1ubuntu4) over (3.14.3-0ubuntu1~vivid2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.57ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu4) ...
Processing triggers for libglib2.0-0:amd64 (2.43.2-1ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
(Reading database ... 214556 files and directories currently installed.)
Removing libmutter0e (3.14.3-0ubuntu1~vivid2) ...
Processing triggers for libc-bin (2.19-13ubuntu3) ...
dpkg: warning: downgrading mutter-common from 3.14.3-0ubuntu1~vivid2 to 3.12.2-1ubuntu4
(Reading database ... 214551 files and directories currently installed.)
Preparing to unpack .../mutter-common_3.12.2-1ubuntu4_all.deb ...
Unpacking mutter-common (3.12.2-1ubuntu4) over (3.14.3-0ubuntu1~vivid2) ...
dpkg: warning: downgrading libclutter-1.0-0:amd64 from 1.20.0-1~ppa1 to 1.18.4-1ubuntu1
Preparing to unpack .../libclutter-1.0-0_1.18.4-1ubuntu1_amd64.deb ...
Unpacking libclutter-1.0-0:amd64 (1.18.4-1ubuntu1) over (1.20.0-1~ppa1) ...
Selecting previously unselected package libmutter0d.
Preparing to unpack .../libmutter0d_3.12.2-1ubuntu4_amd64.deb ...
Unpacking libmutter0d (3.12.2-1ubuntu4) ...
Preparing to unpack .../gnome-accessibility-themes_3.14.2.3-0ubuntu1_all.deb ...
Unpacking gnome-accessibility-themes (3.14.2.3-0ubuntu1) over (3.14.2.3-0ubuntu1~ppa2) ...
Preparing to unpack .../gnome-themes-standard_3.14.2.3-0ubuntu1_amd64.deb ...
Unpacking gnome-themes-standard:amd64 (3.14.2.3-0ubuntu1) over (3.14.2.3-0ubuntu1~ppa2) ...
Preparing to unpack .../gnome-themes-standard-data_3.14.2.3-0ubuntu1_all.deb ...
Unpacking gnome-themes-standard-data (3.14.2.3-0ubuntu1) over (3.14.2.3-0ubuntu1~ppa2) ...
dpkg: warning: downgrading libgnome-control-center1 from 1:3.14.2-2ubuntu1~ppa2 to 1:3.12.1-5ubuntu3
Preparing to unpack .../libgnome-control-center1_1%3a3.12.1-5ubuntu3_amd64.deb ...
Unpacking libgnome-control-center1 (1:3.12.1-5ubuntu3) over (1:3.14.2-2ubuntu1~ppa2) ...
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.43.2-1ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
(Reading database ... 214554 files and directories currently installed.)
Removing libxcb-randr0:amd64 (1.10-2ubuntu1) ...
Removing libxkbcommon-x11-0:amd64 (0.4.3-2) ...
Removing libxcb-xkb1:amd64 (1.10-2ubuntu1) ...
Processing triggers for libc-bin (2.19-13ubuntu3) ...
dpkg: warning: downgrading gnome-control-center-shared-data from 1:3.14.2-2ubuntu1~ppa2 to 1:3.12.1-5ubuntu3
(Reading database ... 214540 files and directories currently installed.)
Preparing to unpack .../gnome-control-center-shared-data_1%3a3.12.1-5ubuntu3_all.deb ...
Unpacking gnome-control-center-shared-data (1:3.12.1-5ubuntu3) over (1:3.14.2-2ubuntu1~ppa2) ...
dpkg: warning: downgrading libclutter-1.0-common from 1.20.0-1~ppa1 to 1.18.4-1ubuntu1
Preparing to unpack .../libclutter-1.0-common_1.18.4-1ubuntu1_all.deb ...
Unpacking libclutter-1.0-common (1.18.4-1ubuntu1) over (1.20.0-1~ppa1) ...
dpkg: warning: downgrading plymouth-theme-ubuntu-gnome-logo from 15.04.2~vivid1 to 15.04.1
Preparing to unpack .../plymouth-theme-ubuntu-gnome-logo_15.04.1_all.deb ...
Unpacking plymouth-theme-ubuntu-gnome-logo (15.04.1) over (15.04.2~vivid1) ...
dpkg: warning: downgrading plymouth-theme-ubuntu-gnome-text from 15.04.2~vivid1 to 15.04.1
Preparing to unpack .../plymouth-theme-ubuntu-gnome-text_15.04.1_all.deb ...
Unpacking plymouth-theme-ubuntu-gnome-text (15.04.1) over (15.04.2~vivid1) ...
dpkg: warning: downgrading ubuntu-gnome-default-settings from 15.04.2~vivid1 to 15.04.1
Preparing to unpack .../ubuntu-gnome-default-settings_15.04.1_all.deb ...
Unpacking ubuntu-gnome-default-settings (15.04.1) over (15.04.2~vivid1) ...
Processing triggers for libglib2.0-0:amd64 (2.43.2-1ubuntu1) ...
Setting up libclutter-1.0-0:amd64 (1.18.4-1ubuntu1) ...
Setting up gir1.2-clutter-1.0 (1.18.4-1ubuntu1) ...
Setting up mutter-common (3.12.2-1ubuntu4) ...
Setting up libmutter0d (3.12.2-1ubuntu4) ...
Setting up gir1.2-mutter-3.0 (3.12.2-1ubuntu4) ...
Setting up gnome-settings-daemon-schemas (3.12.2-1ubuntu4) ...
Setting up gnome-settings-daemon (3.12.2-1ubuntu4) ...
Setting up gnome-shell-common (3.12.2-1ubuntu8) ...
Setting up gnome-themes-standard-data (3.14.2.3-0ubuntu1) ...
Setting up gnome-themes-standard:amd64 (3.14.2.3-0ubuntu1) ...
Setting up gnome-shell (3.12.2-1ubuntu8) ...
Setting up gnome-shell-extensions (3.12.2-1ubuntu1) ...
Setting up libgnome-control-center1 (1:3.12.1-5ubuntu3) ...
Setting up gnome-control-center-data (1:3.12.1-5ubuntu3) ...
Setting up gnome-control-center (1:3.12.1-5ubuntu3) ...
Setting up mutter (3.12.2-1ubuntu4) ...
Setting up gnome-accessibility-themes (3.14.2.3-0ubuntu1) ...
Setting up gnome-control-center-shared-data (1:3.12.1-5ubuntu3) ...
Setting up libclutter-1.0-common (1.18.4-1ubuntu1) ...
Setting up plymouth-theme-ubuntu-gnome-logo (15.04.1) ...
update-initramfs: deferring update (trigger activated)
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-28-generic
Found initrd image: /boot/initrd.img-3.16.0-28-generic
Found linux image: /boot/vmlinuz-3.16.0-25-generic
Found initrd image: /boot/initrd.img-3.16.0-25-generic
Found linux image: /boot/vmlinuz-3.16.0-24-generic
Found initrd image: /boot/initrd.img-3.16.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sda5
Found Ubuntu 10.10 (10.10) on /dev/sda9
done
Setting up plymouth-theme-ubuntu-gnome-text (15.04.1) ...
update-initramfs: deferring update (trigger activated)
Setting up ubuntu-gnome-default-settings (15.04.1) ...
Processing triggers for libc-bin (2.19-13ubuntu3) ...
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-28-generic
                                         
Current status: 14 updates [-3].
PPA purged successfully using aptitude fallback
ventrical@ventrical-System-Product-Name:~$ 

```


Regards..

---

### Post by zika on 2015-01-05
Why?

---

### Post by ventrical on 2015-01-05
Well.. to be perfectly honest ... when I had first installed it there was this unique way the left-hand side panel would slip in and out with a slight gesture of the mouse. It had a certain ambiance that I liked, Then, after a few updates later it started to get clunky - to the point where I had to practically ram the mouse pointer over to the left hand side to get the panel to come out from unhide.

Also .. since it appears to  most likely be comming in from up stream I thought now would be a good a time as any to purge it.

Regards..

---

### Post by zika on 2015-01-07
Still waiting (for some time) for resolution of```
The following packages will be REMOVED:  gnome-applets gnome-panel gnome-session-flashback libical1
The following NEW packages will be installed:
  libical1a
The following packages will be upgraded:
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts
  evolution-plugins gnome-shell gnome-shell-common indicator-datetime
  libcamel-1.2-49 libecal-1.2-16 libedata-cal-1.2-23 libevolution
```...
Update&#8321;: Resolved```
Start-Date: 2015-01-07  09:07:17Commandline: apt-get upgrade
Upgrade: gir1.2-panelapplet-5.0:amd64 (3.14.0-1~ubuntu1, 3.14.0-1~ubuntu2), libpanel-applet0:amd64 (3.14.0-1~ubuntu1, 3.14.0-1~ubuntu2)
End-Date: 2015-01-07  09:07:28


Start-Date: 2015-01-07  09:08:20
Commandline: apt-get dist-upgrade
Install: libical1a:amd64 (1.0-1.3, automatic)
Upgrade: evolution:amd64 (3.12.9-0ubuntu2, 3.12.9-0ubuntu3), gnome-shell:amd64 (3.14.3-0ubuntu1~vivid1, 3.14.3-0ubuntu1), evolution-data-server-common:amd64 (3.12.9-0ubuntu1, 3.12.9-0ubuntu2), libevolution:amd64 (3.12.9-0ubuntu2, 3.12.9-0ubuntu3), evolution-data-server-online-accounts:amd64 (3.12.9-0ubuntu1, 3.12.9-0ubuntu2), gnome-panel-data:amd64 (3.14.0-1~ubuntu1, 3.14.0-1~ubuntu2), gnome-shell-common:amd64 (3.14.3-0ubuntu1~vivid1, 3.14.3-0ubuntu1), gnome-panel:amd64 (3.14.0-1~ubuntu1, 3.14.0-1~ubuntu2), evolution-plugins:amd64 (3.12.9-0ubuntu2, 3.12.9-0ubuntu3), libcamel-1.2-49:amd64 (3.12.9-0ubuntu1, 3.12.9-0ubuntu2), indicator-datetime:amd64 (13.10.0+15.04.20141208-0ubuntu1, 13.10.0+15.04.20141208-0ubuntu2), evolution-common:amd64 (3.12.9-0ubuntu2, 3.12.9-0ubuntu3), libecal-1.2-16:amd64 (3.12.9-0ubuntu1, 3.12.9-0ubuntu2), evolution-data-server:amd64 (3.12.9-0ubuntu1, 3.12.9-0ubuntu2), libedata-cal-1.2-23:amd64 (3.12.9-0ubuntu1, 3.12.9-0ubuntu2)
Remove: libical1:amd64 (1.0-1.2)
``````
The following packages will be REMOVED:  libical1
The following NEW packages will be installed:
  libical1a
The following packages will be upgraded:
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts
  evolution-plugins gnome-panel gnome-panel-data gnome-shell
  gnome-shell-common indicator-datetime libcamel-1.2-49 libecal-1.2-16
  libedata-cal-1.2-23 libevolution
```Now it might be a good moment to purge [COLOR=#000000][I]ppa:ubuntu-gnome-packaging/core3.14 ...
[/I]```
[/COLOR]:~$ sudo ppa-purge ppa:ubuntu-gnome-packaging/core3.14Updating packages lists
PPA to be removed: ubuntu-gnome-packaging core3.14
Disabling ubuntu-gnome-packaging PPA from 
/etc/apt/sources.list.d/ubuntu-gnome-packaging-ubuntu-core3_14-vivid.list
Updating packages lists
Package revert list generated:
 gir1.2-clutter-1.0/vivid gir1.2-mutter-3.0/vivid 
gnome-accessibility-themes/vivid gnome-backgrounds/vivid 
gnome-control-center/vivid gnome-control-center-data/vivid 
gnome-control-center-shared-data/vivid gnome-settings-daemon/vivid 
gnome-settings-daemon-schemas/vivid gnome-shell/vivid gnome-shell-common/vivid 
gnome-themes-standard:amd64/vivid gnome-themes-standard-data/vivid 
libclutter-1.0-0:amd64/vivid libclutter-1.0-common/vivid 
libgnome-control-center1/vivid libmutter0e/vivid mutter/vivid 
mutter-common/vivid


Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-accessibility-themes is already the newest version.
gnome-themes-standard is already the newest version.
gnome-themes-standard-data is already the newest version.
gnome-backgrounds is already the newest version.
gir1.2-clutter-1.0 is already the newest version.
gnome-control-center-shared-data is already the newest version.
gnome-settings-daemon is already the newest version.
gnome-settings-daemon-schemas is already the newest version.
libclutter-1.0-0 is already the newest version.
libclutter-1.0-common is already the newest version.
libgnome-control-center1 is already the newest version.
gir1.2-mutter-3.0 is already the newest version.
gnome-control-center is already the newest version.
gnome-control-center-data is already the newest version.
gnome-shell is already the newest version.
gnome-shell-common is already the newest version.
libmutter0e is already the newest version.
mutter is already the newest version.
mutter-common is already the newest version.
Selected version '1.20.0-1build2' (Ubuntu:15.04/vivid-proposed [amd64]) for 'gir1.2-clutter-1.0'
Selected version '3.14.3-0ubuntu1' (Ubuntu:15.04/vivid-proposed [amd64]) for 'gir1.2-mutter-3.0'
Selected version '3.14.2.3-0ubuntu1' (Ubuntu:15.04/vivid [all]) for 'gnome-accessibility-themes'
Selected version '3.14.1-1' (Ubuntu:15.04/vivid [all]) for 'gnome-backgrounds'
Selected version '1:3.14.2-2ubuntu1' (Ubuntu:15.04/vivid-proposed [amd64]) for 'gnome-control-center'
Selected version '1:3.14.2-2ubuntu1' (Ubuntu:15.04/vivid-proposed [all]) for 'gnome-control-center-data'
Selected version '1:3.14.2-2ubuntu1' (Ubuntu:15.04/vivid-proposed [all]) for 'gnome-control-center-shared-data'
Selected version '3.14.2-2ubuntu1' (Ubuntu:15.04/vivid-proposed [amd64]) for 'gnome-settings-daemon'
Selected version '3.14.2-2ubuntu1' (Ubuntu:15.04/vivid-proposed [all]) for 'gnome-settings-daemon-schemas'
Selected version '3.14.3-0ubuntu1' (Ubuntu:15.04/vivid-proposed [amd64]) for 'gnome-shell'
Selected version '3.14.3-0ubuntu1' (Ubuntu:15.04/vivid-proposed [all]) for 'gnome-shell-common'
Selected version '3.14.2.3-0ubuntu1' (Ubuntu:15.04/vivid [amd64]) for 'gnome-themes-standard'
Selected version '3.14.2.3-0ubuntu1' (Ubuntu:15.04/vivid [all]) for 'gnome-themes-standard-data'
Selected version '1.20.0-1build2' (Ubuntu:15.04/vivid-proposed [amd64]) for 'libclutter-1.0-0'
Selected version '1.20.0-1build2' (Ubuntu:15.04/vivid-proposed [all]) for 'libclutter-1.0-common'
Selected version '1:3.14.2-2ubuntu1' (Ubuntu:15.04/vivid-proposed [amd64]) for 'libgnome-control-center1'
Selected version '3.14.3-0ubuntu1' (Ubuntu:15.04/vivid-proposed [amd64]) for 'libmutter0e'
Selected version '3.14.3-0ubuntu1' (Ubuntu:15.04/vivid-proposed [amd64]) for 'mutter'
Selected version '3.14.3-0ubuntu1' (Ubuntu:15.04/vivid-proposed [all]) for 'mutter-common'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
PPA purged successfully
```

---

### Post by kansasnoob on 2015-01-07
> **zika said:**
> Still waiting (for some time) for resolution of```
The following packages will be REMOVED:  gnome-applets gnome-panel gnome-session-flashback libical1
The following NEW packages will be installed:
  libical1a
The following packages will be upgraded:
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts
  evolution-plugins gnome-shell gnome-shell-common indicator-datetime
  libcamel-1.2-49 libecal-1.2-16 libedata-cal-1.2-23 libevolution
```...

Interesting - I hadn't even checked the flashback session yet. Guess I better get busy.

---

