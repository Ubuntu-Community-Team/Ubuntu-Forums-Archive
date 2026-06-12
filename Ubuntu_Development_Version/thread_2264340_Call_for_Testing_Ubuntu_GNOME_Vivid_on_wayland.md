---
title: "Call for Testing Ubuntu GNOME Vivid on wayland"
date: 2015-02-06
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-02-06
[This popped up]("https://lists.launchpad.net/ubuntugnome-qa/msg00702.html") on the Ubuntu GNOME QA mailing list yesterday:

> An experimental GNOME wayland session is now available in vivid. Its not installed by default, however it would still be good to get some
testing, since at some point we will ship this on a standard install.

Some requirements
- You must be using open source drivers (neither AMD or NVIDIA support wayland yet)
- It is probably recommended to be using systemd init [1], although it may work ok with upstart.
- Some features are not quite 100% complete but upstream claim its stable enough for day-to-day use.

To test install gnome-session-wayland package and then select "GNOME on Wayland" from the gdm login menu.

If you file bugs from a wayland session please tag them with "gnome-wayland" so we can easily track them!


There was quickly [an amendment to that]("https://lists.launchpad.net/ubuntugnome-qa/msg00731.html"):

> Actually better to tag with "wayland-session", ubuntu-bug (apport) will soon auto-tag all bugs filed from within wayland sessions with this.


I've not had time to try it yet because I'm swamped with unrelated bug follow-up procedures but **[COLOR="#FF0000"]I think it's best to assume that things could totally go kablooey[/COLOR]** so please test in disposable installations :D

---

### Post by zika on 2015-02-07
It, simply put, works... ;) And it is even fast and clean, for now.
GDM is a must since it does not show in LightDM.
Update&#8321;: Screen tearing. (AMD) If You want to LogOut and change WM You need to have AutoLogin turned off in GDM. Work in progress.
Update&#8322;: It seems that this evening's upgrade already solved much of my complaints. Nice.

---

### Post by xc3RnbFO8P on 2015-02-07
I cant start Gnome Wayland, it only shows in gdm, and it crashes.
I can start Plasma in gdm and lightdm.
Maybe I am missing something so Gnome Wayland shows in lightdm and sddm? 


[[img]https://farm8.staticflickr.com/7293/15841150034_3d3261f166_z.jpg[/img]](https://flic.kr/p/q8Q31s)

[[img]https://farm8.staticflickr.com/7378/16437672576_f152aa220e_z.jpg[/img]](https://flic.kr/p/r3xnnS)

[[img]https://farm8.staticflickr.com/7334/16463655075_85ed03bf22_z.jpg[/img]](https://flic.kr/p/r5Qx4Z)

[[img]https://farm9.staticflickr.com/8593/15843583543_5bee6d941d_z.jpg[/img]](https://flic.kr/p/q93vpv)

[[img]https://farm8.staticflickr.com/7406/16463655215_35a64316c2_z.jpg[/img]](https://flic.kr/p/r5Qx7p)


xsession-errors
```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
I: Script for ibus started at run_im.
I: Script for auto started at run_im.
I: Script for default started at run_im.
upstart: gpg-agent post-stop process (4258) killed by TERM signal
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd respawning too fast, stopped
upstart: hud main process (4317) terminated with status 1
upstart: unity-settings-daemon main process (4324) terminated with status 1
upstart: unity-panel-service main process (4351) terminated with status 1
upstart: indicator-keyboard main process (4490) terminated with status 1
upstart: indicator-printers main process (4497) terminated with status 1
upstart: indicator-transfer main process (4468) killed by TERM signal
upstart: indicator-bluetooth main process (4472) killed by TERM signal
upstart: indicator-power main process (4476) killed by TERM signal
upstart: indicator-datetime main process (4480) killed by TERM signal
upstart: indicator-session main process (4503) killed by TERM signal
upstart: indicator-application main process (4573) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
```

---

### Post by grahammechanical on 2015-02-07
I have just run two tests.

Ubuntu Gnome Vivid + nouveau + core3.14 ppa 

_Test #1_

Systemd option = loading to login screen takes a very long time. Required to press Esc to move on to the login screen. Loads to a desktop. The opening of windows is quick but the rendering to text strings is messed up. Imagine a heavily redacted report on a government's security agency. It affects the text string in application menus, the labels of files and folders in File manager and the text in Writer documents.

[U]Test#2

[/U]Upstart option. Loads to log in screen without any pause and then loads to a desktop but the same messed up text strings issue is there.

I noticed that this is actually xwayland. Remember xmir? The challenge for both the Gnome and Ubuntu developers is to get the default applications which are written to run on X running on their respective new compositors.

The other year I tested xmir and the only problem I had running any of the Ubuntu family on xmir was with Ubuntu Gnome. And the cause of that problem was GDM not being modified. There were not any problems when using LightDM. But the challenge is to get these distributions running on the full or the pure or whatever you want to call it, new compositors.

Interesting times ahead for U+1 testers.

Regards.

---

### Post by wolterh on 2015-02-11
Well I didn't test on a disposable installation. My results are very similar to the previous ones reported. 

Text sometimes misrenders, and usually hovering or selecting it fixes parts of the text. It also appears that when an application is graphically updating periodically, each time there are different bits of text misrendered.

As for other things, sometimes black borders appear around windows, and after they're replaced by their respective shadowing. Dragging windows around works OK, performance seems a little reduced. Resizing them is sometimes next to chaotic; a lot of artifacts decorated with visual cache residues appear and blink with screen updates.

---

### Post by zika on 2015-03-13
With recent upgrades (X.org and Mesa...) Wayland is very nice and fast. Great work.

---

### Post by xc3RnbFO8P on 2015-03-13
> **zika said:**
> With recent upgrades (X.org and Mesa...) Wayland is very nice and fast. Great work.

No problem with mouse? 
Here double clic do not work and there is no option in settings.
Yes it is fast and smooth.
Works only with GDM.

---

### Post by zika on 2015-03-13
I love Friday afternoon like this... ;)
Simple```
gnome-session --session=gnome-wayland
```on command-line in tty1 gives me everything I need from Wayland. Shortcuts, everything... Just as if I started GDM and... Cool.
To enter in SystemD to clean tty1 (&#8222;text&#8220; kernel boot-line switch before) use &#8222;systemd.unit=runlevel3.target&#8220;.
Very nice.
```
:~$ ps -e|grep way 
7166 tty6     00:00:25 Xwayland
```

---

### Post by xc3RnbFO8P on 2015-03-13
Yes that looks simple, but...
I moved Gnome-Wayland.desktop from Wayland Session to Xsessions, now I see Gnome-Wayland in SDDm and Lightdm, but it wont start.
> ps -e|grep way gives zero output.

---

### Post by zika on 2015-03-13
Not only that it looks simple, it is.
It can not start if You do not make it discard (or do not start) X  and start Xwayland.
That is the reason it works only in GDM because it allows it to do that. To choose between X and Xwayland.
That is why I was trying to use it from tty1 and not from X. X is not a place it likes_to/can live. Like fish... ;)
```
:~$ cat /usr/share/**xsessions**/gnome-flashback-metacity.desktop
[Desktop Entry]
Name=GNOME Flashback (Metacity)
Comment=This session logs you into GNOME Flashback with Metacity
Exec=/usr/lib/gnome-flashback/gnome-flashback-metacity
TryExec=metacity
Icon=
Type=Application
DesktopNames=GNOME-Flashback;Unity;
X-Ubuntu-Gettext-Domain=gnome-flashback
``````
:~$ cat /usr/share/**wayland-sessions**/gnome-wayland.desktop
[Desktop Entry]
Name=GNOME on Wayland
Comment=This session logs you into GNOME, using Wayland
Exec=gnome-session --session=gnome-wayland
TryExec=gnome-session
Icon=
Type=Application
DesktopNames=GNOME
X-Ubuntu-Gettext-Domain=gnome-session-3.0
``````
:~$ cat /usr/share/**xsessions**/gnome-flashback-metacity.desktop
[Desktop Entry]
Name=GNOME Flashback (Metacity)
Comment=This session logs you into GNOME Flashback with Metacity
Exec=/usr/lib/gnome-flashback/gnome-flashback-metacity
TryExec=metacity
Icon=
Type=Application
DesktopNames=GNOME-Flashback;Unity;
X-Ubuntu-Gettext-Domain=gnome-flashback
``````
:/usr/lib$ cat /usr/share/applications/mutter-wayland.desktop
[Desktop Entry]
Type=Application
Name=Mutter (wayland compositor)
**Exec=mutter --wayland --display-server**
NoDisplay=true
# name of loadable control center module
X-GNOME-WMSettingsModule=metacity
# name we put on the WM spec check window
X-GNOME-WMName=Mutter
# back compat only 
X-GnomeWMSettingsLibrary=metacity
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=mutter
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-Phase=WindowManager
X-GNOME-Provides=windowmanager
X-GNOME-Autostart-Notify=true
X-Ubuntu-Gettext-Domain=mutter
```If I gain some spare time I will try to use mutter to compose appropriate .desktop file but the above gives (as I beleive) enough stuff to do that.


Update&#8321;: Just to note that #8 does not work if You're using UpStart. It depends on SystemD. To clarify: GDM is not a factor in this since I did disable and stop it in SystemD to check that. Note: GDM will start due to SystemD even though it is disabled (as a service), even with &#8222;text&#8220; boot-line option or &#8222;systemd.unit=runlevel3.target&#8220;, whatever.

---

