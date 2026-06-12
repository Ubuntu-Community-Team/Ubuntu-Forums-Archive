---
title: "Lightdm (v. 1.1.1) problems"
date: 2012-01-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-18
Today, I upgraded to the newest lightdm, version 1.1.1-0ubuntu2.
I used to have packages lightdm, liblightdm-gobject-1-0 and lightdm-gtk-greeter installed.

However the greeters were dropped from this source and moved into their own projects.

Well, after the upgrade, my PC did not start lightdm properly, instead it hanged without any greeter.
Obviously the greeter from the older version (1.0.6-0ubuntu4) was not compatible.
So I had to go to tty1 and wget the older packages and downgrade with dpkg.
Now my PC works correctly again.

Have someone else seen this kind of behaviour too?

  > 
* New upstream release:     * Support PAM requesting a change of password (lp: #911597)     * Support for reading users' backgrounds from Accounts Service       (lp: #844081)     * Switching to a user without a password bypasses the greeter       (lp: #861177)     * Move the GTK+ and Qt greeters into their own projects   * Drop the gtk and qt greeters packaging files from this source   * debian/liblightdm-gobject-1-0.symbols:     - list new lightdm_user_get_background symbol   * debian/patches/04_CVE-2011-4105.patch,     debian/patches/05_CVE-2011-3153.patch,     debian/patches/09_show_lang_chooser_option.patch,     debian/patches/10_available_languages.patch,     debian/patches/11_set_language_in_accountsservice.patch:     - dropped, those issues are fixed in the new version or apply to the       gtk greeter which is moved to its own source   * debian/rules:     - install lightdm-set-defaults back to its previous location
 [FONT=Verdana]

[/FONT]

---

### Post by bluexrider on 2012-01-18
There are a bunch of bug reports including "no start" "theme issues" "random problems"

[https://launchpad.net/ubuntu/+source/lightdm/1.1.1-0ubuntu2](https://launchpad.net/ubuntu/+source/lightdm/1.1.1-0ubuntu2)

---

### Post by Harry33 on 2012-01-18
Just to let everybody know, I do not use unity-greeter.
That package has not been dropped and obviously works well.

---

### Post by VinDSL on 2012-01-18
Haven't noticed anything, harry.

There are a couple of EE in the log, but it looks pretty good overall.

```
[+0.00s] DEBUG: unity-greeter.vala:583: Starting unity-greeter 0.1.1 UID=104 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:586: Setting cursor
[+0.00s] DEBUG: unity-greeter.vala:590: Creating background surface
[+0.00s] DEBUG: unity-greeter.vala:593: Loading command line options
[+0.00s] DEBUG: unity-greeter.vala:620: Loading configuration from /etc/lightdm/unity-greeter.conf
[+0.00s] DEBUG: unity-greeter.vala:633: Setting GTK+ settings
[+0.07s] DEBUG: unity-greeter.vala:657: Creating Unity Greeter
[+0.07s] DEBUG: Connecting to display manager...
[+0.07s] DEBUG: Wrote 17 bytes to daemon
[+0.07s] DEBUG: Read 8 bytes from daemon
[+0.07s] DEBUG: Read 90 bytes from daemon
[+0.07s] DEBUG: Connected version=1.0.6 default-session=ubuntu hide-users=false has-guest-account=true
[+0.15s] DEBUG: unity-greeter.vala:187: Monitor is 1280x1024 pixels at 0,0
[+0.26s] DEBUG: user-list.vala:529: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.43s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+0.43s] DEBUG: get entries
[+0.43s] DEBUG: user-list.vala:718: Adding indicator object 0x8365178 at position 0
[+0.43s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.43s] DEBUG: Checking against 2 possible times
[+0.43s] DEBUG: Guessing max time width: 62
[+0.43s] DEBUG: get entries
[+0.43s] DEBUG: user-list.vala:718: Adding indicator object 0x8271abc at position 1
[+0.44s] WARNING: IndicatorObject class does not have an accessible description.
[+0.44s] DEBUG: get entries
[+0.44s] DEBUG: get entries
[+0.44s] DEBUG: user-list.vala:718: Adding indicator object 0x82de20c at position 2
[+0.45s] WARNING: IndicatorObject class does not have an accessible description.
[+0.50s] DEBUG: get entries
[+0.50s] DEBUG: get entries
[+0.50s] DEBUG: get entries
[+0.50s] DEBUG: user-list.vala:718: Adding indicator object 0x8365904 at position 3
[+0.50s] DEBUG: user-list.vala:543: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.50s] DEBUG: user-list.vala:439: Using logo /usr/share/unity-greeter/logo.png
[+0.51s] DEBUG: Loaded session /usr/share/xsessions/gnome-shell.desktop (GNOME, This session logs you into GNOME)
[+0.51s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+0.51s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.51s] DEBUG: Loaded session /usr/share/xsessions/gnome-fallback.desktop (GNOME Classic (No effects), This session logs you into GNOME with the traditional panel without any graphical effect.)
[+0.51s] DEBUG: Loaded session /usr/share/xsessions/gnome-classic.desktop (GNOME Classic, This session logs you into GNOME with the traditional panel)
[+0.51s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0.51s] DEBUG: unity-greeter.vala:130: Adding session gnome-shell (GNOME)
[+0.51s] DEBUG: unity-greeter.vala:130: Adding session gnome-classic (GNOME Classic)
[+0.51s] DEBUG: unity-greeter.vala:130: Adding session gnome-fallback (GNOME Classic (No effects))
[+0.51s] DEBUG: unity-greeter.vala:130: Adding session ubuntu (Ubuntu)
[+0.51s] DEBUG: unity-greeter.vala:130: Adding session ubuntu-2d (Ubuntu 2D)
[+0.51s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.51s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0.53s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.55s] DEBUG: unity-greeter.vala:195: Adding/updating user vindsl (VinDSL)
[+0.55s] DEBUG: unity-greeter.vala:163: Adding guest account entry
[+0.55s] DEBUG: unity-greeter.vala:167: Adding other entry
[+0.66s] DEBUG: unity-greeter.vala:359: Start authentication vindsl
[+0.66s] DEBUG: Starting authentication for user vindsl...
[+0.66s] DEBUG: Wrote 22 bytes to daemon
[+0.66s] DEBUG: unity-greeter.vala:660: Showing greeter
[+0.66s] DEBUG: unity-greeter.vala:211: Showing main window
[+0.66s] DEBUG: user-list.vala:926: Change background
[+0.66s] DEBUG: New style for time label
[+0.66s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.66s] DEBUG: Checking against 2 possible times
[+0.66s] DEBUG: Guessing max time width: 62
[+0.66s] DEBUG: New style for time label
[+0.66s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.66s] DEBUG: Checking against 2 possible times
[+0.66s] DEBUG: Guessing max time width: 62
[+0.67s] DEBUG: unity-greeter.vala:673: Starting main loop
[+0.67s] DEBUG: Read 8 bytes from daemon
[+0.67s] DEBUG: Read 36 bytes from daemon
[+0.67s] DEBUG: Prompt user with 1 message(s)
[+0.78s] DEBUG: user-list.vala:1216: Rendered first frame
[+0.79s] DEBUG: user-list.vala:158: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1280x1024
[+1.04s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.8 seconds (1.231382 fps)
[+1.06s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+1.07s] DEBUG: notify visible signal received
[+1.07s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+1.08s] DEBUG: New calendar item
Error getting devices: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gnome.SettingsDaemon.Power' on object at path /org/gnome/SettingsDaemon/Power
[+1.18s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.929106 fps)
[+1.31s] DEBUG: user-list.vala:174: Render of background /usr/share/backgrounds/warty-final-ubuntu.png at 1280x1024 complete
[+1.31s] DEBUG: user-list.vala:1179: Start background animation
[+1.49s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.2 seconds (5.664310 fps)
[+1.49s] DEBUG: user-list.vala:910: Stop background animation
[+1.63s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (7.188246 fps)
[+1.64s] DEBUG: indicator-sound: new_volume_slider_widget
[+1.65s] DEBUG: indicator-sound: new_voip_slider_widget
[+1.73s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.893252 fps)
[+2.13s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.970885 fps)
[+2.93s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.899324 fps)
[+3.33s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.891001 fps)
[+4.13s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.902657 fps)
[+4.54s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.924869 fps)
[+5.34s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.910606 fps)
[+5.74s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.905109 fps)
[+6.54s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.902559 fps)
[+6.94s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.981036 fps)
[+7.74s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.912964 fps)
[+8.14s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.899324 fps)
[+8.94s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.898344 fps)
[+9.34s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.896973 fps)
[+10.14s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.905600 fps)
[+10.54s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.909624 fps)
[+11.35s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.902559 fps)
[+11.75s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.910213 fps)
[+12.55s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.911982 fps)
[+12.95s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.897364 fps)
[+13.75s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.914242 fps)
[+14.15s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.909428 fps)
[+14.95s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.915323 fps)
[+15.35s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.910803 fps)
[+16.15s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.904422 fps)
[+16.55s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.989711 fps)
[+17.35s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.903049 fps)
[+17.75s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.909330 fps)
[+18.37s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.892273 fps)
[+18.58s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.904030 fps)
[+18.92s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.984524 fps)
[+19.15s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.930585 fps)
[+19.75s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.973570 fps)
[+20.42s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.990110 fps)
[+20.55s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.909330 fps)
[+20.65s] DEBUG: user-list.vala:1204: Drew 1 frames in 0.1 seconds (9.975062 fps)
[+21.22s] DEBUG: Providing response to display manager
[+21.22s] DEBUG: Wrote 24 bytes to daemon
[+21.37s] DEBUG: Read 8 bytes from daemon
[+21.37s] DEBUG: Read 18 bytes from daemon
[+21.37s] DEBUG: Authentication complete for user vindsl with return code 0
[+21.38s] DEBUG: Starting session ubuntu
[+21.38s] DEBUG: Wrote 18 bytes to daemon
```

---

### Post by Harry33 on 2012-01-18
> **VinDSL said:**
> Haven't noticed anything, harry.

There are a couple of EE in the log, but it looks pretty good overall.



That is because you have unity-greeter (0.1.1-0ubuntu1) installed and not lightdm-gtk-greeter or lightdm-qt-greeter (1.0.6-0ubuntu4) installed.

---

### Post by paul_in_london on 2012-01-18
> **Harry33 said:**
> That is because you have unity-greeter (1.1.1-0ubuntu2) installed and not lightdm-gtk-greeter or lightdm-qt-greeter (1.0.6-0ubuntu4) installed.

Yes, I have unity-greeter installed too so lightdm is fortunately working ok for me. :)

---

### Post by OGpmpdog on 2012-01-18
> **Harry33 said:**
> Today, I upgraded to the newest lightdm, version 1.1.1-0ubuntu2.
I used to have packages lightdm, liblightdm-gobject-1-0 and lightdm-gtk-greeter installed.

However the greeters were dropped from this source and moved into their own projects.

Well, after the upgrade, my PC did not start lightdm properly, instead it hanged without any greeter.
Obviously the greeter from the older version (1.0.6-0ubuntu4) was not compatible.
So I had to go to tty1 and wget the older packages and downgrade with dpkg.
Now my PC works correctly again.

Have someone else seen this kind of behaviour too?

   [FONT=Verdana]

[/FONT]

Hi Harry,

Dont know if this is related, but since installing Light DM (from Webup8 PPA), Image Viewer doesnt work; the tab is seen in upper pane but no pic displays.

This is a minor annoyance, as I can still use Shotwell or Gthumb.  But I love Image Viewer for its simplicity...and since I ve been without for almost a day, I realize how underrated Image Viewer is!

---

### Post by Harry33 on 2012-01-19
> **OGpmpdog said:**
> Hi Harry,

Dont know if this is related, but since installing Light DM (from Webup8 PPA), Image Viewer doesnt work; the tab is seen in upper pane but no pic displays.

This is a minor annoyance, as I can still use Shotwell or Gthumb.  But I love Image Viewer for its simplicity...and since I ve been without for almost a day, I realize how underrated Image Viewer is!

LightDM and Image Viewer are not related to each other.
Why did you install webupd8 PPA version of the LightDM?

Try this: purge webupd8 PPA version, then install Precise repo version (assuming you have Precise installed of course).
If you have problems starting LightDM, try removing file /etc/lightdm/lightdm.conf
or better, rename it for example lightdm.old.

---

### Post by Harry33 on 2012-01-19
I solved this issue with the 1.1.1 version by adding the following line into the file /etc/lightdm/lightdm.conf

```
greeter-session=lightdm-gtk-greeter
```

Perhaps new lightdm does not find this theme otherwise.

---

### Post by VinDSL on 2012-01-19
> **Harry33 said:**
> That is because you have unity-greeter (0.1.1-0ubuntu1) installed and not lightdm-gtk-greeter or lightdm-qt-greeter (1.0.6-0ubuntu4) installed.
Heh!  This is a confusing thread, but I'm starting to follow you.

Okay, I reread the thread, and updated my greeter to: 1.1.1-0ubuntu2 (precise).

Then, I restarted.  OMG!!! What a difference!!!

Now, LightDM is automagically using my beautiful desktop wall for the background, instead of the default purple monkey vomit screen -- and the version number is correct. Yeah!

When I came back to this thread (even though it was only a few minutes) you had marked it as [solved].  Hrm...

Rereading the thread, yet again, I see you are adding lightdm-gtk-greeter to the mix.

I'll try that now, even though I'm totally happy with having simply upgraded to 1.1.1-0ubuntu2.

Move over skinny dog, 'cause the fat dog's moving in.  LoL!  :D

Wish me luck!

---

### Post by VinDSL on 2012-01-19
Worked fine, harry!

Installed packages:
[LIST]
[*]lightdm
[*]liblightdm-gobject-1-0
[*]lightdm-gtk-greeter
[/LIST]
lightdm.conf:```
[SeatDefaults]
#greeter-session=unity-greeter
greeter-session=lightdm-gtk-greeter
user-session=ubuntu
```
The only problem is... it's butt fugly!

Heh!  To each his own.  Looks like gnome2, to me.

I'm gonna take a step back...

Just wanted to confirm, it booted fine, using your method. ;)

---

### Post by VinDSL on 2012-01-19
Okay, I'm back to the Unity greeter... 

Gawd, that thing is gorgeous!!!

I was looking at the conf file.

Looks like you can turn the grid off now, if you wish.

Some ppl like those little dots, some ppl don't.

I'm neutral on it - don't like 'em, don't hate 'em - so, I'll leave them be.

---

### Post by bmbaker on 2012-01-19
i just upgraded unity-greeter and now when i log in i don't get a choice of unity or gnome it just logs me into the last desktop i used! also it changes my default keyboard so i have to manually change it to be able to type !
tried your suggestions but i still don't get any joy!

might be good to change to not solved :-)
cheers :-)

---

### Post by zika on 2012-01-19
> **VinDSL said:**
> Okay, I'm back to the Unity greeter... 

Gawd, that thing is gorgeous!!!

I was looking at the conf file.

Looks like you can turn the grid off now, if you wish.

Some ppl like those little dots, some ppl don't.

I'm neutral on it - don't like 'em, don't hate 'em - so, I'll leave them be.
Lightdm-gtk is as versatile in conf as unity is... ;)
For as much time I see it in the day it could be the ugliest thing on Planet, I do not care... ;)
Especially since (most of the time) I use startx... ;)

---

### Post by bmbaker on 2012-01-19
just purged lightdm and all its dependencies and rebooted and re-installed and still not wking!

---

### Post by Harry33 on 2012-01-19
There is an update to lightdm again: v. 1.1.1-0ubuntu3

Here:
[https://launchpad.net/ubuntu/precise/+source/lightdm/1.1.1-0ubuntu3](https://launchpad.net/ubuntu/precise/+source/lightdm/1.1.1-0ubuntu3)

> lightdm (1.1.1-0ubuntu3) precise; urgency=low    [ Aurélien Gâteau ]   * debian/control, liblightdm-qt*.install:     - Rename liblightdm-qt packages to match upstream changes     - Conflicts, Replaces with the buggy version  -- Sebastien Bacher <email address hidden>   Thu, 19 Jan 2012 11:34:41 +0100I do not have unity installed at all. So there might be some differencies how LightDM and greeters work for me.
I have these lines in /etc/lightdm/lightdm.conf
```

[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=gnome
allow-guest=false

```

LightDM does not offer any guest session (like I ordered it not to). That is OK.
LightDM uses Gnome as default session. I can change it if I like. That is OK.
LigthDM uses lightdm-gtk-greeter. Also OK.

So I do not have any more issues with it. That is why I marked it as "solved".

---

### Post by bmbaker on 2012-01-19
ah i still have unity installed i try un-installing it and see what happens :-)

---

### Post by bmbaker on 2012-01-19
welll i tried everything i can think off but i guess something got broken somewhere !

---

### Post by VinDSL on 2012-01-21
> **zika said:**
> Lightdm-gtk is as versatile in conf as unity is... ;)
For as much time I see it in the day it could be the ugliest thing on Planet, I do not care... ;)
Especially since (most of the time) I use startx... ;)
No offense intended, zika!

I *guess* my expection was... lightdm-gtk would offer some sort of visual enhancement.  And, maybe it does, if one is of the mind that less is more.

Sorry, if that came out wrong -- it was just a shock reaction...  :)

---

### Post by zika on 2012-01-21
> **VinDSL said:**
> No offense intended, zika!

I *guess* my expection was... lightdm-gtk would offer some sort of visual enhancement.  And, maybe it does, if one is of the mind that less is more.

Sorry, if that came out wrong -- it was just a shock reaction...  :)None taken. I (even) do not see what could have offended me...
Just relax, as far as I'm concerned...
As far as I can remember I was (mostly) joking... ;)

---

### Post by VinDSL on 2012-01-21
I just ran across a screenie of GDM3 (on UbuOO)


[INDENT][IMG]https://lh3.googleusercontent.com/-sP03tOYz4v8/TjEX-mNrMvI/AAAAAAAAFi0/PLS0VUtgMIQ/gdm3_ubuntu_11.10_oneiric_ocelot.png[/IMG][/INDENT]


Greeter looks pretty similar to lightdm-gtk, no?!?!?

---

