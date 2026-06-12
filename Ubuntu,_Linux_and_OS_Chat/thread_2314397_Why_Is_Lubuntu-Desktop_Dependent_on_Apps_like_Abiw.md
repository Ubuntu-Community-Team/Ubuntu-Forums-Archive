---
title: "Why Is Lubuntu-Desktop Dependent on Apps like Abiword &amp; Gnumeric?"
date: 2016-02-20
forum: Ubuntu, Linux and OS Chat
---

### Post by buzzingrobot on 2016-02-20
I've never done much with Lubuntu or LXDE, but I gave 14.04.04 Lubuntu a look today in a VM.  I noticed that trying to remove Abiword or Gnumeric or any one of several other packages that are part of the default install would also remove lubuntu-desktop and trigger an autoremove suggestion that would have removed a few dozen core packages and rather definitively broken things.

I checked and both lubuntu-desktop and the lxde meta-packages have dependencies that include standalone apps like Abiword, Leafpad, etc.

I'm not looking for a workaround here, but I am curious how and why those dependencies were established like that.

---

### Post by vasa1 on 2016-02-20
That's because 'lubuntu-desktop' isn't a conventional package but a metapackage.

As you've seen, lubuntu-desktop will be removed if you remove abiword, gnumeric, or several other packages. But the functionality of the desktop, per se, is unaffected.

Here are some links I've bookmarked on the topic:
[http://ubuntuforums.org/showthread.php?t=2091576&p=12389408](http://ubuntuforums.org/showthread.php?t=2091576&p=12389408)
[www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html)
[http://askubuntu.com/questions/233662/how-do-i-remove-ace-of-penguins-without-removing-lubuntu-desktop](http://askubuntu.com/questions/233662/how-do-i-remove-ace-of-penguins-without-removing-lubuntu-desktop)
[http://forums.debian.net/viewtopic.php?t=104157](http://forums.debian.net/viewtopic.php?t=104157)
[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

For me, the only relevance a metapackage has after the initial upgrade is done, is that it needs to be installed back just before I do an upgrade from 14.04 to 14.10 (or 16.04).

Incidentally, most other desktop environments of the official Ubuntu flavors have a similar reliance on a desktop metapackage. What you've seen isn't restricted to Lubuntu/LXDE.

---

### Post by buzzingrobot on 2016-02-21
> **vasa1 said:**
> That's because 'lubuntu-desktop' isn't a conventional package but a metapackage.



Yes, but the accompanying autoremove suggestion would have removed a few dozen "real" essential packages and left the system unusable. I didn't do that, of course.  But, we often see here that inexperienced users are victimized by autoremove suggestions.  

The other autoremove suggestion I saw immediately after the install is suspect, I think.  Why would the package manager on a new and pristine system have a reason to generate it?

---

### Post by kansasnoob on 2016-02-21
Lubuntu also builds a "core" package that can be installed on top of Ubuntu:

```
lance@lance-desktop:~$ sudo apt-get install **lubuntu-core** -s
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  consolekit desktop-base gnome-icon-theme-full gnome-themes-standard
  gnome-themes-standard-data gtk2-engines libck-connector0 libfm-data
  libfm-extra4 libfm-gtk-data libfm-gtk4 libfm-modules libfm4 libgif4
  libid3tag0 libimlib2 libmenu-cache-bin libmenu-cache3 libobrender29 libobt2
  libpam-ck-connector lightdm-gtk-greeter lubuntu-artwork
  lubuntu-artwork-14-04 lubuntu-default-settings lubuntu-icon-theme
  lubuntu-lxpanel-icons lxmenu-data lxpanel lxsession lxsession-data
  lxsession-logout obconf openbox pcmanfm plymouth-theme-lubuntu-logo
  plymouth-theme-lubuntu-text
Suggested packages:
  gnome kde-standard xfce4 wmaker libfm-tools nautilus-actions amixer scrot
  galculator xscreensaver gpicview lxde-common menu fonts-dejavu libxml2-dev
  tint2 openbox-menu openbox-gnome-session openbox-kde-session
[B]The following NEW packages will be installed:
  consolekit desktop-base gnome-icon-theme-full gnome-themes-standard
  gnome-themes-standard-data gtk2-engines libck-connector0 libfm-data
  libfm-extra4 libfm-gtk-data libfm-gtk4 libfm-modules libfm4 libgif4
  libid3tag0 libimlib2 libmenu-cache-bin libmenu-cache3 libobrender29 libobt2
  libpam-ck-connector lightdm-gtk-greeter lubuntu-artwork
  lubuntu-artwork-14-04 lubuntu-core lubuntu-default-settings
  lubuntu-icon-theme lubuntu-lxpanel-icons lxmenu-data lxpanel lxsession
  lxsession-data lxsession-logout obconf openbox pcmanfm
  plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text[/B]
0 upgraded, 38 newly installed, 0 to remove and 0 not upgraded.

```

So maybe if 'lubuntu-desktop' is removed in the process of removing unwanted packages just directly installing 'lubuntu-core' would correct the autoremove behavior?

---

### Post by vasa1 on 2016-02-21
> **buzzingrobot said:**
> Yes, but the accompanying autoremove suggestion would have removed a few dozen "real" essential packages and left the system unusable. I didn't do that, of course.  But, we often see here that inexperienced users are victimized by autoremove suggestions.  

The other autoremove suggestion I saw immediately after the install is suspect, I think.  Why would the package manager on a new and pristine system have a reason to generate it?

Maybe things have changed. I've been removing software that would also entail removing lubuntu-desktop and haven't seen *a few dozen "real" essential packages* being suggested for removal. Why, even on my present install, I don't have lubuntu-desktop anymore:```
05:31 PM ~ $ apt-cache policy lubuntu-desktop
lubuntu-desktop:
  Installed: (none)
  Candidate: 0.55
  Version table:
     0.55 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
05:31 PM ~ $ 
```
And this is an extract from the relevant history.log:```
Start-Date: 2014-11-14  18:24:18
Commandline: apt-get purge firefox
Purge: firefox:amd64 (33.0+build2-0ubuntu0.14.04.1), lubuntu-desktop:amd64 (0.55)
End-Date: 2014-11-14  18:24:22

```

---

### Post by buzzingrobot on 2016-02-21
Still seems anomalous to me. Admittedly, I overlooked the fact that lubuntu-desktop is a meta-package. But, the non-meta packages the accompanying autoremove wanted to delete included among others, the xserver-xorg-XXXXX packages. And, I don't think that separate immediate post-install autoremove suggestion should have been there, at all. Makes me wonder if there's a flaw in the package list installed in the new 14.04.4 images. Otherwise, why would the first use of the package manager on a new install produce it?

(I'm not fond of autoremove, in any case.  It's potentially dangerous and relies on user savvy to avoid that potentiality.  If packages need to be removed, and can be safely, then they should be removed as part of the action that triggers these autoremove suggestions. If not, don't remove them and don't suggest they be removed.)

---

### Post by vasa1 on 2016-02-21
I guess I'm fortunate that I've never encountered problems with *autoremove*.

---

### Post by buzzingrobot on 2016-02-21
Did a new VM install from  a new ISO image, rebooted, opened a terminal, did "sudo apt update && sudo apt upgrade", and saw the same autoremove suggestion. C'est la vie.

---

### Post by ian-weisser on 2016-02-21
Which .iso image?
Lubuntu? Ubuntu? Server? Mini? Something else?

There are a few autoremote-tries-to-uninstall-X threads, most were users who built up from the mini .iso.

The desktop images apt-marks all packages as 'manual' (human selected, inelegible for autoremove), but building up from the server or mini images doesn't do that.
The 'manual' marking is a workaround. It's working around the very problem you seem to be describing - users can erroneously autoremove most of their system by deleting one GUI application.
The rather minor down side of the workaround is that all those originally-installed packages, and their dependencies, can never be autoremoves. If you want to

---

### Post by vasa1 on 2016-02-22
> **ian-weisser said:**
> Which .iso image?
Lubuntu? Ubuntu? Server? Mini? Something else?
...
That would be interesting to know.
Also, the output of **apt-get purge -s abiword** for example.

---

### Post by buzzingrobot on 2016-02-22
> **ian-weisser said:**
> Which .iso image?




Lubuntu 14.04.4. (See first post). The release image.

---

### Post by buzzingrobot on 2016-02-22
> **vasa1 said:**
> That would be interesting to know.
Also, the output of **apt-get purge -s abiword** for example.
> 
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  abiword-common apturl apturl-common evolution-data-server-common
  gecko-mediaplayer gnome-mplayer gstreamer1.0-plugins-bad-faad
  gstreamer1.0-plugins-bad-videoparsers language-selector-gnome libabiword-3.0
  libavresample1 libbluray1 libcamel-1.2-45 libchamplain-0.12-0
  libchamplain-gtk-0.12-0 libchromaprint0 libclutter-1.0-0
  libclutter-gtk-1.0-0 libcogl-pango15 libcogl15 libdiscid0
  libebook-contacts-1.2-0 libedataserver-1.2-18 libfs6 libgbm1 libgda-5.0-4
  libgda-5.0-common libglu1-mesa libgmlib1 libgmtk1 libgmtk1-data libgpod4
  libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-good1.0-0 libgtkglext1
  libical1 libilmbase6 libjs-jquery libloudmouth1-0 liblua5.2-0
  libmusicbrainz3-6 libopencv-calib3d2.4 libopencv-contrib2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4
  libopencv-ml2.4 libopencv-objdetect2.4 libopencv-video2.4 libopenexr6
  libots0 libpostproc52 libquvi-scripts libquvi7 libsbc1 libsrtp0 libtbb2
  libtelepathy-glib0 libtidy-0.99-0 libvdpau1 libwmf0.2-7 libwpd-0.9-9
  libwpg-0.2-2 libwps-0.2-2 libwv-1.2-4 lubuntu-core mplayer2 x11-apps
  x11-session-utils x11-xfs-utils xinit xorg
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  abiword* lubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.

```
sudo apt-get upgrade
``` produces:
> Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  gstreamer1.0-plugins-bad-faad gstreamer1.0-plugins-bad-videoparsers
  libchromaprint0 libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-good1.0-0
  libgtkglext1 libilmbase6 libopencv-calib3d2.4 libopencv-contrib2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4
  libopencv-ml2.4 libopencv-objdetect2.4 libopencv-video2.4 libopenexr6
  libsbc1 libsrtp0 libtbb2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by vasa1 on 2016-02-22
I removed abiword and some other stuff a long time ago, shortly after Lubuntu 14.04 was released:```
Start-Date: 2014-11-14  20:16:54
Commandline: apt-get purge abiword*
Purge: libabiword-3.0:amd64 (3.0.0-4ubuntu1.1), abiword:amd64 (3.0.0-4ubuntu1.1), abiword-common:amd64 (3.0.0-4ubuntu1.1)
End-Date: 2014-11-14  20:17:42

Start-Date: 2014-11-14  20:18:38
Commandline: apt-get purge audacious*
Purge: audacious-plugins:amd64 (3.4.3-2), audacious-plugins-data:amd64 (3.4.3-2), audacious:amd64 (3.4.3-1)
End-Date: 2014-11-14  20:18:43

Start-Date: 2014-11-14  20:19:42
Commandline: apt-get purge fonts-nanum*
Purge: fonts-nanum:amd64 (20131007-1)
End-Date: 2014-11-14  20:19:46

Start-Date: 2014-11-14  20:21:18
Commandline: apt-get purge pidgin*
Purge: pidgin-data:amd64 (2.10.9-0ubuntu3.2), pidgin:amd64 (2.10.9-0ubuntu3.2)
End-Date: 2014-11-14  20:21:23

Start-Date: 2014-11-14  20:21:38
Commandline: apt-get purge sylpheed*
Purge: sylpheed-doc:amd64 (20120629-1), sylpheed:amd64 (3.4.0~beta7-1ubuntu1), sylpheed-i18n:amd64 (3.4.0~beta7-1ubuntu1), sylpheed-plugins:amd64 (3.4.0~beta7-1ubuntu1)
End-Date: 2014-11-14  20:21:44

Start-Date: 2014-11-14  20:22:52
Commandline: apt-get purge xul-ext-ubufox*
Purge: xul-ext-ubufox:amd64 (2.9-0ubuntu0.14.04.1)
End-Date: 2014-11-14  20:22:53

```I had already "lost" lubuntu-desktop as I posted earlier. So I obviously didn't experience what you're seeing.

One thing comes to mind ... My Lubuntu 14.04.4 is the sum of all the six-monthly releases so far whereas yours is a "clean" 14.04.4. One main difference is that anyone "clean" installing *buntu 14.04.2 upwards will have newer kernels and other embellishments. For example, I'm still on 3.13:```
07:34 PM ~ $ uname -r
3.13.0-77-generic
07:34 PM ~ $ 

```
> The 14.04.2 and newer point release will ship with an updated kernel and X stack by default
from [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

It would be interesting to see if other Lubuntu users (or for that matter Xubuntu users) see what you see or what I see.

Edit: from what I see, several Lubuntu heavy-weights seem to be "unaware" of the existence of the Ubuntu Forums. Pity.

---

### Post by gregoryo2013 on 2016-02-23
Last week I downloaded and installed Lubuntu 14.04 (at long last I replaced 12.04!), and am facing the situation described in this thread.

```

$ grep DESC /etc/lsb-release
DISTRIB_DESCRIPTION="Ubuntu 14.04.4 LTS"
$
$ uname -r
3.19.0-49-generic
$
$ sudo apt-get -y remove abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  abiword-common apturl apturl-common evolution-data-server-common
  gecko-mediaplayer gnome-mplayer language-selector-gnome libabiword-3.0
  libcamel-1.2-45 libchamplain-0.12-0 libchamplain-gtk-0.12-0 libclutter-1.0-0
  libclutter-gtk-1.0-0 libcogl-pango15 libcogl15 libebook-contacts-1.2-0
  libedataserver-1.2-18 libfs6 libgbm1 libgda-5.0-4 libgda-5.0-common
  libgdome2-0 libgdome2-cpp-smart0c2a libgmlib1 libgmtk1 libgmtk1-data
  libgtkmathview0c2a libical1 libjs-jquery liblink-grammar4 libloudmouth1-0
  libmusicbrainz3-6 libots0 libtelepathy-glib0 libtidy-0.99-0 libwv-1.2-4
  link-grammar-dictionaries-en lubuntu-core x11-apps x11-session-utils
  x11-xfs-utils xinit xorg
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  abiword abiword-plugin-grammar abiword-plugin-mathview lubuntu-desktop
0 to upgrade, 0 to newly install, 4 to remove and 0 not to upgrade.
After this operation, 5,308 kB disk space will be freed.
(Reading database ... 166878 files and directories currently installed.)
Removing abiword-plugin-mathview (3.0.0-4ubuntu1.1) ...
Removing abiword-plugin-grammar (3.0.0-4ubuntu1.1) ...
Removing lubuntu-desktop (0.55) ...
Removing abiword (3.0.0-4ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...

```

apt-get autoremove also attempts to remove the packages listed above, and I figure that's not a good plan. I am now looking for a way to have abiword removed (or at least disabled) programmatically, in a way that doesn't break with upgrades. I am left wondering if I should use some kludge to leave it installed and disabled, thereby leaving Lubuntu closer to a vanilla install.

Advice would be welcome.

Cheers,
Greg.

---

### Post by vasa1 on 2016-02-23
Greg, thanks for posting and including your kernel version. It seems that at least two users, I'm assuming that OP has the same kernel version, are having this quite serious issue.

I've PM'ed sudodus about this thread but I'm guessing he's tied up testing the upcoming 16.04 version.

BTW, instead of *grep DESC /etc/lsb-release*, you can use *lsb_release -a*.

---

### Post by ian-weisser on 2016-02-23
> **gregoryo2013 said:**
> apt-get autoremove also attempts to remove the packages listed above, and I figure that's not a good plan. I am now looking for a way to have abiword removed (or at least disabled) programmatically, in a way that doesn't break with upgrades. I am left wondering if I should use some kludge to leave it installed and disabled, thereby leaving Lubuntu closer to a vanilla install.

Your lubuntu-core package is eligible for autoremove.
Simply change it's apt-marking from 'auto' to 'manual' to make it ineligble for autoremove.

There are two easy ways to do it:
```
sudo apt-mark manual lubuntu-core
sudo apt install lubuntu-core        ## Specified packages are marked 'manual', dependencies are marked 'auto'
```

Then you should be able to uninstall abiword (and it's dependencies) without removing the rest of your desktop environment.

---

### Post by sudodus on 2016-02-23
Hello,

I just tested these commands in an installed Lubuntu Xenial system. ***autoremove*** seems to work well after removing abiword and gnumeric, only [COLOR="#FF0000"]one[/COLOR] package will be removed :-) Maybe there are problems with Trusty (I have not tested that)

See this command line dialogue (in today's Lubuntu Xenial beta 1 candidate)

```
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]sudo apt-get remove abiword gnumeric[/COLOR]
[sudo] password for tester: 
Läser paketlistor… Färdig
Bygger beroendeträd       
Läser tillståndsinformation… Färdig
Följande paket har installerats automatiskt och är inte längre nödvändigt:
  [COLOR="#FF0000"]libwmf0.2-7[/COLOR]
Använd ”sudo apt autoremove” för att ta bort det.
Följande paket kommer att TAS BORT:
  abiword gnumeric lubuntu-desktop
0 att uppgradera, 0 att nyinstallera, 3 att ta bort och 0 att inte uppgradera.
Efter denna åtgärd kommer 12,6 MB att frigöras på disken.
Vill du fortsätta? [J/n] j
(Läser databasen ... 117080 filer och kataloger installerade.)
Tar bort lubuntu-desktop (0.63) ...
Tar bort abiword (3.0.1-6) ...
Tar bort gnumeric (1.12.27-1) ...
Hanterar utlösare för man-db (2.7.5-1) ...
Hanterar utlösare för hicolor-icon-theme (0.15-0ubuntu1) ...
Hanterar utlösare för desktop-file-utils (0.22-1ubuntu3) ...
Hanterar utlösare för mime-support (3.59ubuntu1) ...
Hanterar utlösare för libc-bin (2.21-0ubuntu6) ...
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]sudo apt-get update[/COLOR]
Läs:1 http://se.archive.ubuntu.com/ubuntu xenial InRelease [95,8 kB]
Bra:2 http://se.archive.ubuntu.com/ubuntu xenial-updates InRelease                                    
Bra:3 http://se.archive.ubuntu.com/ubuntu xenial-backports InRelease                                  
Läs:4 http://se.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1 436 kB]  
Bra:5 http://security.ubuntu.com/ubuntu xenial-security InRelease                    
Läs:6 http://se.archive.ubuntu.com/ubuntu xenial/main Translation-en [841 kB]        
Läs:7 http://se.archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7 336 kB]
Läs:8 http://se.archive.ubuntu.com/ubuntu xenial/universe Translation-en [4 889 kB]
Läs:9 http://se.archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [136 kB]
Läs:10 http://se.archive.ubuntu.com/ubuntu xenial/multiverse Translation-en [110 kB]
Hämtade 14,8 MB på 6s (2 414 kB/s)                                                                    
Läser paketlistor… Färdig
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]sudo apt-get dist-upgrade[/COLOR] 
Läser paketlistor… Färdig
Bygger beroendeträd       
Läser tillståndsinformation… Färdig
Beräknar uppgradering… Färdig
Följande paket har installerats automatiskt och är inte längre nödvändigt:
  libwmf0.2-7
Använd ”sudo apt autoremove” för att ta bort det.
Följande paket kommer att uppgraderas:
  cpp-5 gcc-5-base gir1.2-gtk-3.0 gstreamer1.0-plugins-good libglib2.0-0 libglib2.0-bin
  libglib2.0-data libgomp1 libgstreamer-plugins-good1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgupnp-1.0-4 libpython3.5 libpython3.5-minimal libpython3.5-stdlib libquadmath0 libstdc++6
  python3.5 python3.5-minimal
20 att uppgradera, 0 att nyinstallera, 0 att ta bort och 0 att inte uppgradera.
Behöver hämta 40,9 MB arkiv.
Efter denna åtgärd kommer ytterligare 92,2 kB utrymme användas på disken.
Vill du fortsätta? [J/n] n
Avbryter.
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]sudo apt-get autoremove[/COLOR]
Läser paketlistor… Färdig
Bygger beroendeträd       
Läser tillståndsinformation… Färdig
Följande paket kommer att TAS BORT:
  [COLOR="#FF0000"]libwmf0.2-7[/COLOR]
0 att uppgradera, 0 att nyinstallera, 1 att ta bort och 20 att inte uppgradera.
Efter denna åtgärd kommer 532 kB att frigöras på disken.
Vill du fortsätta? [J/n] y
(Läser databasen ... 116719 filer och kataloger installerade.)
Tar bort libwmf0.2-7:i386 (0.2.8.4-10.5ubuntu1) ...
Hanterar utlösare för libc-bin (2.21-0ubuntu6) ...
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Xenial Xerus (development branch)
Release:	16.04
Codename:	xenial
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]uname -a[/COLOR]
Linux tester-SATELLITE-PRO-C850-19W 4.4.0-6-generic #21-Ubuntu SMP Tue Feb 16 20:31:49 UTC 2016 i686 i686 i686 GNU/Linux
tester@tester-SATELLITE-PRO-C850-19W:~$ 
```

---

### Post by vasa1 on 2016-02-23
Sudodus, many thanks for looking into this! Looks like it works as expected for 16.04 and for Lubuntu 14.04.4 only when the LTS enablement stack is **not** installed. In other words, there's no problem for the user who starts off with Lubuntu 14.04 and only upgrade to the next point release without installing the LTS enablement stack.

---

### Post by vasa1 on 2016-02-23
> **ian-weisser said:**
> Your lubuntu-core package is eligible for autoremove.
Simply change it's apt-marking from 'auto' to 'manual' to make it ineligble for autoremove.

There are two easy ways to do it:
```
sudo apt-mark manual lubuntu-core
sudo apt install lubuntu-core        ## Specified packages are marked 'manual', dependencies are marked 'auto'
```

Then you should be able to uninstall abiword (and it's dependencies) without removing the rest of your desktop environment.
It's a bit scary that one has to resort to *apt-mark*. I remember reading, a couple of years ago, that apt-marking was something that didn't work perfectly or isn't simple to understand: see [http://askubuntu.com/questions/432743/how-are-packages-classified-in-apt-mark-showauto-showmanual](http://askubuntu.com/questions/432743/how-are-packages-classified-in-apt-mark-showauto-showmanual) as an example.



Anyway, on my Lubuntu 14.04.4, I see this:```
08:52 PM ~ $ apt-mark showauto | grep lubuntu
lubuntu-artwork-14-04
lubuntu-icon-theme
lubuntu-lxpanel-icons
08:53 PM ~ $ 

```And even then, if I run apt-get purge gnumeric, the system doesn't want to removed any of the three items listed above:```
08:53 PM ~ $ sudo apt-get purge gnumeric
[sudo] password for vasa1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  lp-solve
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  gnumeric*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 7,100 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
09:03 PM ~ $ 

```(The "1 not to be upgraded" refers to google-chrome-stable which I've put a hold on.

---

### Post by vasa1 on 2016-02-23
> **gregoryo2013 said:**
> Last week I downloaded and installed Lubuntu 14.04 (at long last I replaced 12.04!), and am facing the situation described in this thread.

... apt-get autoremove also attempts to remove the packages listed above, and I figure that's not a good plan. I am now looking for a way to have abiword removed (or at least disabled) programmatically, in a way that doesn't break with upgrades. I am left wondering if I should use some kludge to leave it installed and disabled, thereby leaving Lubuntu closer to a vanilla install.

Advice would be welcome.

Cheers,
Greg.
If you don't mind downloading, I suggest you give the original Lubuntu 14.04 (as opposed to Lubuntu 14.04.4) a try: for a 64-bit system, the torrent is this: [http://cdimages.ubuntu.com/lubuntu/releases/trusty/release/lubuntu-14.04-desktop-amd64.iso.torrent](http://cdimages.ubuntu.com/lubuntu/releases/trusty/release/lubuntu-14.04-desktop-amd64.iso.torrent)

If you're happy, you could then upgrade your system to 14.04.4 without going the LTS enablement stack route.

---

### Post by mc4man on 2016-02-24
Seems improper for the removal of a meta-package to cause other packages to be marked for autoremove, we'll see - 
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1549310](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1549310)

---

### Post by buzzingrobot on 2016-02-24
> **vasa1 said:**
> ...I'm assuming that OP has the same kernel version...

Yep:  install 14.04.4, reboot, and check for updates.

---

### Post by vasa1 on 2016-02-24
> **mc4man said:**
> Seems improper for the removal of a meta-package to cause other packages to be marked for autoremove, we'll see - 
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1549310](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1549310)
Thanks for filing the bug!
I hope people mark it "affects me too".

Though to reflect the issue here, instead of removing 'lubuntu-desktop', something like 'remove abiword' or 'remove gnumeric' should be reported: according to the posters here, that should trigger removal of 'lubuntu-desktop' as well as a lot of essential packages.

---

### Post by mc4man on 2016-02-24
> **vasa1 said:**
> Thanks for filing the bug!
I hope people mark it "affects me too".

Though to reflect the issue here, instead of removing 'lubuntu-desktop', something like 'remove abiword' or 'remove gnumeric' should be reported: according to the posters here, that should trigger removal of 'lubuntu-desktop' as well as a lot of essential packages.
Really has nothing to do  with the individual packages mentioned, the issue is with the meta package & or how it's removal interacts with apt.

---

### Post by vasa1 on 2016-02-24
> **mc4man said:**
> Really has nothing to do  with the individual packages mentioned, the issue is with the meta package & or how it's removal interacts with apt.
Okay, got it.

Thanks again.

---

### Post by sudodus on 2016-02-24
> **buzzingrobot said:**
> I've never done much with Lubuntu or LXDE, but I gave 14.04.04 Lubuntu a look today in a VM.  I noticed that trying to remove Abiword or Gnumeric or any one of several other packages that are part of the default install would also remove lubuntu-desktop and trigger an autoremove suggestion that would have removed a few dozen core packages and rather definitively broken things.

I checked and both lubuntu-desktop and the lxde meta-packages have dependencies that include standalone apps like Abiword, Leafpad, etc.

I'm not looking for a workaround here, but I am curious how and why those dependencies were established like that.

> **mc4man said:**
> Seems improper for the removal of a meta-package to cause other packages to be marked for autoremove, we'll see - 
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1549310](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1549310)

> **vasa1 said:**
> Thanks for filing the bug!
I hope people mark it "affects me too".

Though to reflect the issue here, instead of removing 'lubuntu-desktop', something like 'remove abiword' or 'remove gnumeric' should be reported: according to the posters here, that should trigger removal of 'lubuntu-desktop' as well as a lot of essential packages.

> **mc4man said:**
> Really has nothing to do  with the individual packages mentioned, the issue is with the meta package & or how it's removal interacts with apt.

Thanks for your efforts to find and explore this issue, and making a bug report about it :-)

---

### Post by mikodo on 2016-02-25
> **vasa1 said:**
> It would be interesting to see if other Lubuntu users (or for that matter Xubuntu users) see what you see or what I see.


Installed Xubuntu 14.04.1 back when ...
Removed abiword a long time ago and I don't know how to that history magic like you, vasa1.
I like to keep some older kernels around and never see the need to remove the Xubuntu-desktop meta-package.
See what I get when I ask apt to purge gnumeric.
*It would interesting if someone who installed Xubuntu 14.04.4 ran through this to see if the same thing happens as did with buzzingrobot with his attempt at purging the metapackage for Lubuntu.
I don't know if you see anything interesting but, here:

```
mikodo@mikodo:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty
mikodo@mikodo:~$  uname -r
3.13.0-79-generic
mikodo@mikodo:~$ sudo apt-get purge xubuntu-desktop
[sudo] password for mikodo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hddtemp linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic
  linux-headers-3.13.0-76 linux-headers-3.13.0-76-generic
  linux-image-3.13.0-74-generic linux-image-3.13.0-76-generic
  linux-image-extra-3.13.0-74-generic linux-image-extra-3.13.0-76-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xubuntu-desktop*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 45.1 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
mikodo@mikodo:~$ sudo apt-get purge gnumeric
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hddtemp linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic
  linux-headers-3.13.0-76 linux-headers-3.13.0-76-generic
  linux-image-3.13.0-74-generic linux-image-3.13.0-76-generic
  linux-image-extra-3.13.0-74-generic linux-image-extra-3.13.0-76-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnumeric*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 7,100 kB disk space will be freed.
Do you want to continue? [Y/n] n

```

---

### Post by vasa1 on 2016-02-25
> This behaviour is perfectly normal and NOT harmful.

** Changed in: lubuntu-meta (Ubuntu)
       Status: Confirmed => Invalid


Wow!

---

### Post by vasa1 on 2016-02-25
> **mikodo said:**
> Installed Xubuntu 14.04.1 back when ...
Removed abiword a long time ago and I don't know how to that history magic like you, vasa1.
I like to keep some older kernels around and never see the need to remove the Xubuntu-desktop meta-package.
See what I get when I ask apt to purge gnumeric.
*It would interesting if someone who installed Xubuntu 14.04.4 ran through this to see if the same thing happens as did with buzzingrobot with his attempt at purging the metapackage for Lubuntu.
I don't know if you see anything interesting but, here:

```
mikodo@mikodo:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty
mikodo@mikodo:~$  uname -r
3.13.0-79-generic
mikodo@mikodo:~$ sudo apt-get purge xubuntu-desktop
[sudo] password for mikodo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hddtemp linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic
  linux-headers-3.13.0-76 linux-headers-3.13.0-76-generic
  linux-image-3.13.0-74-generic linux-image-3.13.0-76-generic
  linux-image-extra-3.13.0-74-generic linux-image-extra-3.13.0-76-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xubuntu-desktop*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 45.1 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
mikodo@mikodo:~$ sudo apt-get purge gnumeric
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hddtemp linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic
  linux-headers-3.13.0-76 linux-headers-3.13.0-76-generic
  linux-image-3.13.0-74-generic linux-image-3.13.0-76-generic
  linux-image-extra-3.13.0-74-generic linux-image-extra-3.13.0-76-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnumeric*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 7,100 kB disk space will be freed.
Do you want to continue? [Y/n] n

```
Hi, thanks for responding! So, you, on Xubuntu with the same kernel, see what I see on Lubuntu.

BTW, I think you can safely *run sudo apt-get autoremove* to get rid of unnecessary kernels if your system is running stably and well. I usually act on all the autoremove prompts I get *but that's only after looking at what being suggested*. If I don't understand something, I ask the people here for guidance :)

As for that history magic, I save all of */var/log/apt/history.log* as soon as the file is compressed for my records so I have every *apt* transaction from the moment I installed Lubuntu just for times like this ;) Plus, I only use apt-get from the dreaded command-line, no software center or synaptic though I do use Synaptic now and then to poke around but never to install/remove software.

---

### Post by mc4man on 2016-02-25
> **vasa1 said:**
> This behaviour is perfectly normal and NOT harmful.

Wow!
Well it seems far from 'normal' to me so have set bug back to new & edit - see someone re-confirmed, good.
After that I don't have a dog in this fight as only use Ubuntu so hopefully it's addressed a bit better.

---

### Post by buzzingrobot on 2016-02-25
> **mc4man said:**
> ...someone re-confirmed, good.
  

Me, most likely.  It seems back on track now.

An autoremove suggestions that says, in effect, "I think we need to remove xorg, please, plus a couple of dozen other packages you probably know nothing about.  Trust me. " is a long way from normal.

Which is why I'm not fond of autoremove.  It relies far too much on user knowledge.

---

### Post by montag dp on 2016-02-25
Seems the real issue here is not autoremove, but how the packages and dependencies are marked in the first place. In theory, autoremove should only remove dependencies of packages that the user has removed from his/her system and are no longer dependencies of any other package that is still present. Which would make it perfectly safe.

---

### Post by mikodo on 2016-02-25
> **vasa1 said:**
>  - Snippet - Hi, thanks for responding! 

Your Welcome!

Thank you, for the response on saving your apt-get hx. It is always nice to learn something new. That said though, I often use the **GUI App **Synaptic too, lol. Sometimes, I use it for installing/deleting still. I also find it useful for information on apps and libraries, and other things I cannot find on cli. I have seen other people like you (very often testers) who, show what and when something was added and removed and their dependencies. I didn't know how one did that and now I know. My long-term interest is to test for Xubuntu-next. I recently started getting the xubuntu-devel daily mailing digest per prompting/request that I do from, one of the devs on irc #xubuntu-devel. I explained that I really don't have much time to devote to any significant contributions to the project now. He suggested reading and maybe making suggestions on the mailing list. He explained that it wouldn't take significant time to devote to that and all input is considered and deemed helpful. I read about him, (Knome), and he has recently been the team leader of the Xubuntu project for a number of years and is known for his exceptional team-building abilities. Hence, even though I was resistant right now with being involved because of my heavy responsibilities, he was able to coerce me well, that may not be the right word but was persuasive enough on irc to suggest something I could do and would like that, wouldn't take a lot of time for me. So, I start there.

For preparing for my preference of testing as my giving back to the community, I will need to start learning some things including I think, the apt-get hx.

Take Care!

---

### Post by buzzingrobot on 2016-02-25
> **montag dp said:**
> Seems the real issue here is not autoremove, but how the packages and dependencies are marked in the first place. In theory, autoremove should only remove dependencies of packages that the user has removed from his/her system and are no longer dependencies of any other package that is still present. Which would make it perfectly safe.

Agreed, but if removing those packages is "perfectly safe" why not just do it, rather than ask the user? Or, perhaps, make it a configuration option that's can be toggled either way.

Posts here that "I used autoremove like apt-get told me and now my system is broken!"  are not rare. I think it's a very unusual user who has the expertise to know if removal of packages per autoremove is safe.

---

### Post by vasa1 on 2016-02-25
> **buzzingrobot said:**
> Agreed, but if removing those packages is "perfectly safe" why not just do it, rather than ask the user? Or, perhaps, make it a configuration option that's can be toggled either way.
That's why the bug was filed. Because removing those packages isn't perfectly safe. Something went wrong somewhere. As montagdp suggests, the mistake has to do with how the packages are marked rather than with autoremove *per se*. 

> **buzzingrobot said:**
> 
Posts here that "I used autoremove like apt-get told me and now my system is broken!"  are not rare. I think it's a very unusual user who has the expertise to know if removal of packages per autoremove is safe.
Totally disagree. Just because posts on something are not rare, doesn't mean autoremove is dangerous. This is a help/support forum primarily. 

I also don't know about "expertise". The more ignorant I am in some things, the more cautious I need to be. I remember my early post (when I was on 11.04 or 11.10) on wanting to remove something and being told that "ubuntu-desktop" would go as well. I asked here and was pointed in the right direction.

---

### Post by buzzingrobot on 2016-02-26
I think that unless it's verified to be *always* right, in all circumstances, autoremove's suggestions should not be displayed by default. Users will assume, as they should, that messages from the OS are correct and that acting on them will have no negative impact.

---

### Post by roni8 on 2016-04-29
To repair:

sudo apt-get install lubuntu-core
sudo apt-get install lubuntu-desktop

Because, i don't know.

---

