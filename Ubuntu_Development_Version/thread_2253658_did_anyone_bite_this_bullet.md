---
title: "did anyone bite this bullet?"
date: 2014-11-21
forum: Ubuntu Development Version
---

### Post by zika on 2014-11-21
```
:~$ sudo apt-get dist-upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  gir1.2-panelapplet-4.0 indicator-applet-complete libpanel-applet-4-0
The following packages will be upgraded:
  gnome-panel gnome-panel-data
2 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 1331 kB of archives.
After this operation, 860 kB disk space will be freed.
Do you want to continue? [Y/n]
```Frankly, did not have (enough) time to browse through all changelogs but I did not find resolution in those I've looked into. I do not have (too) much to loose since flashback dos not work already... ;)
The only package that I think I need is indicator-applet-complete even though I'm not sure I really do.

---

### Post by muktupavels on 2014-11-21
All applets needs to be updated for new libpanel-applet library as I have made changes that breaks all existing applets.

indicator-applet-complete just needs to be rebuilt for new gnome-panel.

---

### Post by zika on 2014-11-21
> **albertsmuktupavels said:**
> All applets needs to be updated for new libpanel-applet library as I have made changes that breaks all existing applets. indicator-applet-complete just needs to be rebuilt for new gnome-panel.In a nutshell: I should wait... ;)  Makes sense, I though so. Thank You.

---

### Post by xc3RnbFO8P on 2014-11-21
I did, no problem here (yes I took a screenshot  :)

---

### Post by Cavsfan on 2014-11-21
I guess I did too. Since then I've not been able to get into any session but the default on Vivid Gnome.

Anything else and I mean everything else leads to a black screen and a cursor. That is all.

The _only one_ that boots is checked in this screenie and I don't know what System Default is but I'm not real fond of it.

[[IMG]http://en.zimagez.com/miniature/20141121134931.jpg[/IMG]]("http://en.zimagez.com/zimage/20141121134931.php")

Guess like zika said, we just wait...
Thanks Alberts!

---

### Post by zika on 2014-11-21
> **Ringi said:**
> I did, no problem here (yes I took a screenshot  :)

> **Cavsfan said:**
> I guess I did too. Since then I've not been able to get into any session but the default on Vivid Gnome.

Anything else and I mean everything else leads to a black screen and a cursor. That is all.

The _only one_ that boots is checked in this screenie and I don't know what System Default is but I'm not real fond of it.

[[IMG]http://en.zimagez.com/miniature/20141121134931.jpg[/IMG]]("http://en.zimagez.com/zimage/20141121134931.php")

Guess like zika said, we just wait...
Thanks Alberts!```
:~$ sudo aptitude upgrade --full-resolver[sudo] password for zika:
The following packages will be upgraded:
  gnome-panel{b} gnome-panel-data xdiagnose{b}
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1395 kB of archives. After unpacking 116 kB will be freed.
The following packages have unmet dependencies:
 gnome-panel : Breaks: libpanel-applet-4-0 (< 1:3.14.0) but 1:3.8.1-2ubuntu5 is installed.
 xdiagnose : Depends: python3-pygtk which is a virtual package.
The following actions will resolve these dependencies:


     Remove the following packages:
1)     gir1.2-panelapplet-4.0
2)     indicator-applet-complete
3)     libpanel-applet-4-0
4)     ubuntu-desktop
5)     xdiagnose


     Leave the following dependencies unresolved:
6)     gnome-panel recommends indicator-applet-complete




Accept this solution? [Y/n/q/?]
```

---

### Post by Cavsfan on 2014-11-21
> **zika said:**
> ```
:~$ sudo aptitude upgrade --full-resolver[sudo] password for zika:
The following packages will be upgraded:
  gnome-panel{b} gnome-panel-data xdiagnose{b}
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1395 kB of archives. After unpacking 116 kB will be freed.
The following packages have unmet dependencies:
 gnome-panel : Breaks: libpanel-applet-4-0 (< 1:3.14.0) but 1:3.8.1-2ubuntu5 is installed.
 xdiagnose : Depends: python3-pygtk which is a virtual package.
The following actions will resolve these dependencies:


     Remove the following packages:
1)     gir1.2-panelapplet-4.0
2)     indicator-applet-complete
3)     libpanel-applet-4-0
4)     ubuntu-desktop
5)     xdiagnose


     Leave the following dependencies unresolved:
6)     gnome-panel recommends indicator-applet-complete




Accept this solution? [Y/n/q/?]
```

Was that before or after you bit the bullet?
All I get is this:
```
cavsfan@cavsfan-MS-7529:~$ sudo aptitude upgrade --full-resolver
The following packages will be upgraded: 
  libreoffice-help-en-us 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,434 kB of archives. After unpacking 1,024 B will be used.
Do you want to continue? [Y/n/?] 
```

---

### Post by xc3RnbFO8P on 2014-11-21
Only thing that isnt working is Plasma, My fault

[[img]https://farm8.staticflickr.com/7558/15660801199_ab70cbd7de_c.jpg[/img]](https://flic.kr/p/pRTGzM)

---

### Post by xc3RnbFO8P on 2014-11-21
@Cavsfan

Have you tried to change to Lightdm?

---

### Post by zika on 2014-11-21
> **Cavsfan said:**
> Was that before or after you bit the bullet?
All I get is this:
```
cavsfan@cavsfan-MS-7529:~$ sudo aptitude upgrade --full-resolver
The following packages will be upgraded: 
  libreoffice-help-en-us 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,434 kB of archives. After unpacking 1,024 B will be used.
Do you want to continue? [Y/n/?] 
```As I wrote, I did not taste the bullet. We, obviously, do not have same situation, due to almost sure difference in PPAs etc. As I can see You have GDM and...
> **albertsmuktupavels said:**
> All applets needs to be updated for new libpanel-applet library as I have made changes that breaks all existing applets. indicator-applet-complete just needs to be rebuilt for new gnome-panel.This a very clear explanation and guidance for me.

---

### Post by Hazzabin on 2014-11-21
Yup I got bitten badly, actually 3 times as I was just setting up another puter with Gnome 15.04 with flashback (only cos I thought I had done something wrong) :)

OK so do 'WE" have to do this "[COLOR=#000000][I]indicator-applet-complete just needs to be rebuilt for new gnome-panel." or is this eventually coming down via updates??


[/I][/COLOR]

---

### Post by muktupavels on 2014-11-21
@Hazzabin
Just wait until new version of indicator-applet-complete will be available in updates.

@Cavsfan
What DM are you using? Display Manager should set XDG_CURRENT_DESKTOP from DesktopNames in /usr/share/xsession/*.desktop file. If DM does not support this then this is at least one reason why session does not work.

---

### Post by Cavsfan on 2014-11-22
> **albertsmuktupavels said:**
> @Hazzabin
Just wait until new version of indicator-applet-complete will be available in updates.

@Cavsfan
What DM are you using? Display Manager should set XDG_CURRENT_DESKTOP from DesktopNames in /usr/share/xsession/*.desktop file. If DM does not support this then this is at least one reason why session does not work.

I installed Vivid Gnome [http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/) 
and it came with GDM as the default:

```
cavsfan@cavsfan-MS-7529:~$ aptitude show gdm
Package: gdm                             
State: installed
Automatically installed: no
Version: 3.14.0-0ubuntu1
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Uncompressed Size: 5,290 k
Depends: libaccountsservice0 (>= 0.6.8), libaudit1 (>= 1:2.2.1), libc6 (>= 2.14), libcanberra-gtk3-0 (>= 0.25), libcanberra0 (>= 0.2), libgdk-pixbuf2.0-0 (>= 2.22.0), libgdm1 (= 3.14.0-0ubuntu1), libglib2.0-0
         (>= 2.37.3), libgtk-3-0 (>= 3.0.0), libpam0g (>= 0.99.7.1), libselinux1 (>= 1.32), libsystemd0, libwrap0 (>= 7.6-4~), libx11-6, libxau6, libxdmcp6, libxrandr2 (>= 2:1.2.99.3), debconf (>= 0.5) |
         debconf-2.0, init-system-helpers (>= 1.18~), lsb-base (>= 4.1+Debian11ubuntu7), gir1.2-gdm-1.0 (= 3.14.0-0ubuntu1), adduser, libpam-modules (>= 0.72-1), libpam-runtime (>= 0.76-13.1), libpam-systemd,
         gnome-session-bin (>= 3.12.1), gnome-settings-daemon (>= 3.2), gnome-shell, plymouth (>= 0.8.8-0ubuntu6.1), gnome-session | x-session-manager | x-window-manager | x-terminal-emulator, librsvg2-common,
         accountsservice (>= 0.6.12), gsettings-desktop-schemas, libglib2.0-bin (>= 2.36.0), dconf-cli (>= 0.12.1-2), dconf-gsettings-backend (>= 0.12.1-2), x11-common (>= 1:7.6+11), x11-xserver-utils
Recommends: zenity, xserver-xephyr, x11-xkb-utils, xserver-xorg, at-spi2-core, gnome-icon-theme, gnome-icon-theme-symbolic
Suggests: libpam-gnome-keyring, gnome-orca
Conflicts: gdm
Breaks: gnome-control-center (< 3.0), gnome-control-center (< 3.0), gnome-orca (< 2.30.0-2), gnome-orca (< 2.30.0-2), gnome-panel (< 3.0), gnome-panel (< 3.0), gnome-screensaver (< 2.17.7), gnome-screensaver (<
        2.17.7), gnome-shell (< 3.5), gnome-shell (< 3.5)
Provides: x-display-manager
Description: Next generation GNOME Display Manager
 GDM provides the equivalent of a "login:" prompt for X displays: it asks for a login and starts X sessions. 
 
 It provides all the functionality of XDM, including XDMCP support for managing remote displays, and extends it with the ability to start X servers on demand. 
 
 The greeter is written using the GNOME libraries and hence looks like a GNOME application - even to the extent of supporting themes! 
 
 This package contains the next generation GDM, which was developed using the technologies on which GNOME 3 is based.
```

Changing the DM will not fix this correct? We wait on indicator-applet-complete to be updated as you stated right?

---

### Post by muktupavels on 2014-11-22
Yes, changing DM will not fix problem with empty screen. There is something wrong with upstart (?)... If gnome-flashaback-* is removed from /etc/upstart-xsessions then it will work.

If you want you can upgrade to gnome-panel in proposed, but that will remove indicator-applet-completate or any other applet that is not updated for new libpanel-applet version. I would suggest to wait until gnome-panel is moved from proposed to release.

---

### Post by ventrical on 2014-11-22
This thread should be marked with a prefix. ie; [all variants].

 On my ubuntu-desktop install I already knew gnome-flashback-compiz was bust but now gnome-flashback-metacity only shows background screen.

edit:  razorqt working like a champ:)

---

### Post by zika on 2014-11-22
> **albertsmuktupavels said:**
> Yes, changing DM will not fix problem with empty screen. There is something wrong with upstart (?)... If gnome-flashaback-* is removed from /etc/upstart-xsessions then it will work.
If you want you can upgrade to gnome-panel in proposed, but that will remove indicator-applet-completate or any other applet that is not updated for new libpanel-applet version. I would suggest to wait until gnome-panel is moved from proposed to release.[SIZE=1]Off-topic:
```
:~$ ls /etc/upstart-xsessions
/etc/upstart-xsessions
```
1. flashback sessions do not work
2. this folder is empty from the time UpStart was removed on this machine and systemd-sysv was installed.[/SIZE]
Apart from some off-topic (growing) wait is the only cure with a good explanation (of Yours) given on the very beginning of the thread. I' waiting for upgrade of packages mentioned to mark it solved.

---

### Post by Cavsfan on 2014-11-22
I too will wait.
```
cavsfan@cavsfan-MS-7529:~$ ls /etc/upstart-xsessions
/etc/upstart-xsessions
```

It is a file.
```
cavsfan@cavsfan-MS-7529:~$ cat /etc/upstart-xsessions 
# xsessions listed below are run inside an Upstart user session.
gnome
gnome-classic
gnome-fallback
gnome-flashback-metacity
gnome-flashback-compiz
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
unity8-x11
unity8-mir
```

But still I will wait until I see indicator-applet-complete in the updates.

---

### Post by zika on 2014-11-22
> **Cavsfan said:**
> It is a file.Old and tired (weekend (Saturday) that became harder than mid-week day)... :)```
:~$ cat /etc/upstart-xsessions
# xsessions listed below are run inside an Upstart user session.
gnome
gnome-classic
gnome-fallback
gnome-flashback-metacity
gnome-flashback-compiz
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
unity8-x11
unity8-mir
```

Update&#8321;: Now that I see it is a file, I've fixed FlashBack sessios:
```
sudo mv /etc/upstart-xsessions /etc/upstart-xsessions.original
sudo touch /etc/upstart-xsessions
```Only Unity seems to loose indicators, I'll see to that next time I do log-out... ;)
What's most important: my para-trick is reversible so no caveats... ;)
I did not know if that file is necessary do I played safe and made empty one, just in case not to have to log-in again. ;)
I love having my FlshBack back so thank You Cavsfan.

---

### Post by Cavsfan on 2014-11-22
> **zika said:**
> Old and tired (weekend (Saturday) that became harder than mid-week day)... :)```
:~$ cat /etc/upstart-xsessions
# xsessions listed below are run inside an Upstart user session.
gnome
gnome-classic
gnome-fallback
gnome-flashback-metacity
gnome-flashback-compiz
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
unity8-x11
unity8-mir
```

Update&#8321;: Now that I see it is a file, I've fixed FlashBack sessios:
```
sudo mv /etc/upstart-xsessions /etc/upstart-xsessions.original
sudo touch /etc/upstart-xsessions
```Only Unity seems to loose indicators, I'll see to that next time I do log-out... ;)
What's most important: my para-trick is reversible so no caveats... ;)
I did not know if that file is necessary do I played safe and made empty one, just in case not to have to log-in again. ;)
I love having my FlshBack back so thank You Cavsfan.

Thank *you* Zika! I did what you posted and I have flashback too! :D Happy camper here. :D
That file is now empty.

---

### Post by muktupavels on 2014-11-22
> **zika said:**
> 
Update&#8321;: Now that I see it is a file, I've fixed FlashBack sessios:
```
sudo mv /etc/upstart-xsessions /etc/upstart-xsessions.original
sudo touch /etc/upstart-xsessions
```Only Unity seems to loose indicators, I'll see to that next time I do log-out... ;)
What's most important: my para-trick is reversible so no caveats... ;)
I did not know if that file is necessary do I played safe and made empty one, just in case not to have to log-in again. ;)
I love having my FlshBack back so thank You Cavsfan.

No need to create empty file. Just comment out flashback and fallback lines by adding #. Unity will still use upstart and indicators will work.

---

### Post by Hazzabin on 2014-11-22
Thanks guys I too a very happy camper, after doing that code all back to normal Gnome 15.04 with flashback   :guitar:

---

### Post by zika on 2014-11-23
> **albertsmuktupavels said:**
> No need to create empty file. Just comment out flashback and fallback lines by adding #. Unity will still use upstart and indicators will work.Yes, just like that. That is why I've kept original file. Thank You for leading me to that file.

---

### Post by Cavsfan on 2014-11-23
> **albertsmuktupavels said:**
> No need to create empty file. Just comment out flashback and fallback lines by adding #. Unity will still use upstart and indicators will work.

Thanks for that! I was not able to restart or logout until I did as you stated. :D
> **Hazzabin said:**
> Thanks guys I too a very happy camper, after doing that code all back to normal Gnome 15.04 with flashback   :guitar:

Sweet! I guess even though we're old and stuff we can still learn new things. I love learning and am glad this works again!
And I learned 2 things - that you can **sudo mv** a file to rename it and **sudo touch** a file to create a blank file.

> **zika said:**
> Yes, just like that. That is why I've kept original file. Thank You for leading me to that file.

I am glad you suggested backing up that file. I just reversed the commands.

```
sudo rm /etc/upstart-xsessions
sudo mv /etc/upstart-xsessions.original /etc/upstart-xsessions
```

Then edited it and logout works again. Whoot! :guitar:

I noticed gnome-session-flashback is in the update queue. I came here to see if there was anything about it. I guess I'll update it.
I noticed this and was hoping that gnome-screensaver would be changed from depends to suggests also, but I am confident that it will be done. :)

```
gnome-flashback (3.14.0-3ubuntu5) vivid; urgency=medium

  * Depend on unity-settings-daemon instead of gnome-settings-daemon.
  * Make gnome-session-flashback suggest compiz.

 -- Dmitry Shachnev <mitya57@ubuntu.com>  Sun, 23 Nov 2014 13:06:44 +0300gnome-flashback (3.14.0-3ubuntu5) vivid; urgency=medium
```

---

### Post by zika on 2014-11-27
I've installed indicator-applet-complete today, concluding this thread, I presume. Before I've installed new packages consciously loosing that package.
Update&#8321;: Marking this thread solved.

---

### Post by Cavsfan on 2014-11-27
I was able to logout and back in with it but my indicator-applet-complete hasn't been updated since November 11th by Alberts. 

I was under the impression the fix was still in the works but I could be wrong.

```
indicator-applet (12.10.2+15.04.20141111-0ubuntu1) vivid; urgency=low

  [ Alberts Muktup&#257;vels ]
  * Update for new libpanel-applet version.

 -- Ubuntu daily release <ps-jenkins@lists.canonical.com>  Tue, 11 Nov 2014 17:53:08 +0000
```

Thanks

---

### Post by zika on 2014-11-28
One caveat: LightDM does not allow now change of session (type).

---

### Post by xc3RnbFO8P on 2014-11-28
Happend here to, I reconfigure it to gdm, no problem there

---

### Post by zika on 2014-11-28
> **Ringi said:**
> Happend here to, I reconfigure it to gdm, no problem thereMy solution is even simpler: Go to xinit/startx and use FlashBack or even use light(er) WM... ;)
Not to mention real solution:```
:~$ cat /usr/share/lightdm/lightdm.conf.d/50-zika.conf[SeatDefaults]
user-session=gnome-session-flashback-metacity
#user-session=gnome-session-flashback-compiz
#user-session=unity
#user-session=openbox
```... ;)
Paired with```
sudo systemctl stop lightdm.service
sudo systemctl start lightdm.service
```it works like magic...

---

### Post by xc3RnbFO8P on 2014-11-28
I cant find this 50-zika.conf  :)
but I got this:
[[img]https://farm8.staticflickr.com/7565/15276393004_91e19d49b2_o.png[/img]](https://flic.kr/p/pgVvqh)

---

### Post by zika on 2014-11-28
There is no zika on Your computer? That must be odd... ;)
Of course there is no file such the one I've mentioned. I've created it so could You, using another name, I presume.
On of helpful resources is: [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by xc3RnbFO8P on 2014-11-28
> **zika said:**
> There is no zika on Your computer? That must be odd... ;)
Of course there is no file such the one I've mentioned. I've created it so could You, using another name, I presume.
On of helpful resources is: [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

Ha ha, maybe  I need some Zika in my computer it is total mess at the moment, it is darn Plasma 5, Kubuntu is going the same way as Gnome 2!

---

### Post by zika on 2014-11-28
> **Ringi said:**
> Ha ha, maybe  I need some Zika in my computer **it is total mess at the moment**, it is darn Plasma 5, Kubuntu is going the same way as Gnome 2!Trust me, any zika near/in computer is just adding to the mess. I know that the best... ;)

---

### Post by Cavsfan on 2014-11-28
:lol: Ha!
Isn't this the indicator-applet-complete that we had been waiting on?

```
indicator-applet (12.10.2+15.04.20141127.2-0ubuntu1) vivid; urgency=low

  [ Dmitry Shachnev ]
  * Build against gnome-panel 3.14.

 -- Ubuntu daily release <ps-jenkins@lists.canonical.com>  Thu, 27 Nov 2014 11:45:58 +0000
```

```
gnome-panel (1:3.14.0-1~ubuntu1) vivid; urgency=medium

  * Merge with Debian NEW queue, remaining changes:
    - Use an epoch in version number.
    - Recommend indicator-applet-complete.
    - Use unity-control-center instead of gnome-control-center.
    - Adjust Breaks for Ubuntu versioning.
    - Add patches:
      + 40_unset_menuproxy.patch
      + 41_classic_layout.patch
  * Recommend gnome-session-flashback 1:3.14.0, as that is the first
    version providing GNOME-Flashback desktop name.

 -- Dmitry Shachnev <mitya57@ubuntu.com>  Tue, 18 Nov 2014 18:14:19 +0300
```

---

### Post by zika on 2014-11-28
> **Cavsfan said:**
> :lol: Ha!
Isn't this the indicator-applet-complete that we had been waiting on?

```
indicator-applet (12.10.2+15.04.20141127.2-0ubuntu1) vivid; urgency=low

  [ Dmitry Shachnev ]
  * Build against gnome-panel 3.14.

 -- Ubuntu daily release <ps-jenkins@lists.canonical.com>  Thu, 27 Nov 2014 11:45:58 +0000
```

```
gnome-panel (1:3.14.0-1~ubuntu1) vivid; urgency=medium

  * Merge with Debian NEW queue, remaining changes:
    - Use an epoch in version number.
    - Recommend indicator-applet-complete.
    - Use unity-control-center instead of gnome-control-center.
    - Adjust Breaks for Ubuntu versioning.
    - Add patches:
      + 40_unset_menuproxy.patch
      + 41_classic_layout.patch
  * Recommend gnome-session-flashback 1:3.14.0, as that is the first
    version providing GNOME-Flashback desktop name.

 -- Dmitry Shachnev <mitya57@ubuntu.com>  Tue, 18 Nov 2014 18:14:19 +0300
```I think that is the one due to which I did mark thread solved. I do have it on my machine already and... Look at the time-stamp.

---

### Post by Cavsfan on 2014-11-28
> **zika said:**
> I think that is the one due to which I did mark thread solved. I do have it on my machine already and... Look at the time-stamp.

It was not available to me at the time you marked this thread solved. But that is probably because I'm on the other side of the world. I was with family all day yesterday.
So it was probably just a time zone difference. :)

---

### Post by zika on 2014-11-28
> **Cavsfan said:**
> It was not available to me at the time you marked this thread solved. But that is probably because I'm on the other side of the world. I was with family all day yesterday.
So it was probably just a time zone difference. :)Or the fact that I have proposed repository turned on... ;) It is definitely better to spend time with family than to sit in front of computer. Nevertheless I was at work most of the day.

---

### Post by muktupavels on 2014-11-29
> **zika said:**
> One caveat: LightDM does not allow now change of session (type).

It is bug in unity-greeter. Clicking on buttons does nothing.

---

