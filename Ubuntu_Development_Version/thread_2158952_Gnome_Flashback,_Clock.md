---
title: "Gnome Flashback, Clock"
date: 2013-07-01
forum: Ubuntu Development Version
---

### Post by muktupavels on 2013-07-01
Is there way to get back clock in top panel?

 [ATTACH=CONFIG]244295[/ATTACH]

---

### Post by dino99 on 2013-07-01
add the widget from extensions.gnome.org

---

### Post by muktupavels on 2013-07-01
Do extensions work in gnome flashback/fallback? I am not using gnome shell.

---

### Post by stinkeye on 2013-07-02
You have 2 clocks to choose from.
One is shown in the "indicator applet complete" as seen in Unity and one is the old style date time.
The "indicator applet complete" and "clock" applets can be added to the panel with alt+Super+Rclick on the panel.
Same shortcut on an applet to move or remove.

You appear to already have the "indicator applet complete" on the panel but not showing date/tlme.

In terminal check the dconf setting
```
gsettings get com.canonical.indicator.datetime show-clock
```

If the value returned is "false", reset the key to the default value of "true"
```
gsettings reset com.canonical.indicator.datetime show-clock
```

Prefer the other clock and don't want to show this one, run...
```
gsettings set com.canonical.indicator.datetime show-clock false
```

---

### Post by Cavsfan on 2013-07-02
I have the same problem as albertsmuktupavels. No clock or calendar displays but, yet the output of this command is true.

```
cavsfan@cavsfan-MS-7529:~$ gsettings get com.canonical.indicator.datetime show-clock
true

```

[ATTACH=CONFIG]244330[/ATTACH]

Any other ideas?

---

### Post by zika on 2013-07-02
Ditto. Using &#8222;other&#8220; clock (see above)...

---

### Post by stinkeye on 2013-07-02
> **Cavsfan said:**
> I have the same problem as albertsmuktupavels. No clock or calendar displays but, yet the output of this command is true.

```
cavsfan@cavsfan-MS-7529:~$ gsettings get com.canonical.indicator.datetime show-clock
true

```

[ATTACH=CONFIG]244330[/ATTACH]

Any other ideas?

May be more to it than I thought.
Just assumed it was disabled in dconf as looked like the "indicator applet complete" was on the panel.
Have you tried removing and re-adding indicator applet complete.

---

### Post by zika on 2013-07-02
> **stinkeye said:**
> May be more to it than I thought.
Just assumed it was disabled in dconf as looked like the "indicator applet complete" was on the panel.
Have you tried removing and re-adding indicator applet complete.Does it count if we (others) tried...?
It is not a simple dconf problem...

---

### Post by stinkeye on 2013-07-02
My fault, didn't realize I was replying to an Ubuntu +1 thread.

---

### Post by muktupavels on 2013-07-02
I don't want "other" clock. I want that one in indicator applet complete...

So now we have two broken things in gnome flashback. First - white panel. Second - no clock in indicator applet complete.

P.S. Clock doesn&#8217;t show only in flashback session. In unity clock is available.

---

### Post by zika on 2013-07-02
> **albertsmuktupavels said:**
> I don't want "other" clock. I what that one in indicator applet complete...

So now we have two broken things in gnome flashback. First - white panel. Second - no clock in indicator applet complete.

P.S. Clock doesn&#8217;t show only in flashback session. In unity clock is available.
Just one at my place... ;) (clock)...
Color of panel is odd in Gnome Classic here...
And I can not change background... In GClassic...

---

### Post by Cavsfan on 2013-07-03
> **albertsmuktupavels said:**
> I don't want "other" clock. I want that one in indicator applet complete...

So now we have two broken things in gnome flashback. First - white panel. Second - no clock in indicator applet complete.

P.S. Clock doesn’t show only in flashback session. In unity clock is available.

I'm with you there. The min, restore and close buttons also do not work after you maximize the window and that began on Raring 13.04 and followed into Saucy 13.10.
I'm not that into Unity although I think it works for the most part. I prefer Gnome. :)
So, there is actually 3 problems.

I don't think there is a bug for this yet or if so I haven't seen it.
Here are the other two:

White panel issue: [https://bugs.launchpad.net/compiz-core/+bug/1196177](https://bugs.launchpad.net/compiz-core/+bug/1196177)

Unclickable windows after maximize: [https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)

---

### Post by muktupavels on 2013-07-03
Maybe someone can report this bug?

---

### Post by Cavsfan on 2013-07-04
> **albertsmuktupavels said:**
> Maybe someone can report this bug?

I'm not really sure how to initiate a new bug. I have just encountered something that abends then it reports the bug automatically and it usually already exists.
So I just mark the bug that I am also affected by it.

Perhaps someone else?

---

### Post by muktupavels on 2013-07-04
[https://bugs.launchpad.net/indicator-datetime/+bug/1197957](https://bugs.launchpad.net/indicator-datetime/+bug/1197957)

---

### Post by zika on 2013-07-04
> **albertsmuktupavels said:**
> [https://bugs.launchpad.net/indicator-datetime/+bug/1197957](https://bugs.launchpad.net/indicator-datetime/+bug/1197957)+1ed...

---

### Post by Cavsfan on 2013-07-04
> **albertsmuktupavels said:**
> [https://bugs.launchpad.net/indicator-datetime/+bug/1197957](https://bugs.launchpad.net/indicator-datetime/+bug/1197957)

Good deal! Signed!

---

### Post by Cavsfan on 2013-07-11
> **zika said:**
> Ditto. Using "other“ clock (see above)...

Ditto here also. I could not go any longer with out it. 

[ATTACH=CONFIG]244609[/ATTACH]

---

### Post by muktupavels on 2013-07-11
Soon datetime and power indicators will be back. :) Need to resolve one problem and than we will need to wait until fix will be merged.

I made two other branches with fix for:
1. Restore space in Ambiance between Applications and Places.
2. Fixed gnome-panel creation when using separate x screens.

---

### Post by Cavsfan on 2013-07-16
Not sure why this is marked resolved. Today July 16, 2013 is the first time I have seen the normal clock with date and time if you adjust dconf-settings.

[ATTACH=CONFIG]244793[/ATTACH]

[ATTACH=CONFIG]244794[/ATTACH]

Now it is resolved.
I looked up there a few moments ago and had two dates. I removed the one I had added.

Edit: it even states in the bug 5 hours ago "This bug was fixed in the package indicator-applet - 12.10.2+13.10.20130716-0ubuntu1"

---

### Post by muktupavels on 2013-07-16
I marked solved when my fix was committed. It was only a matter of time when fix will be released to updates.

---

### Post by Cavsfan on 2013-07-16
> **albertsmuktupavels said:**
> I marked solved when my fix was committed. It was only a matter of time when fix will be released to updates.

I was under the impression that once the fix is released to the general population when it is a problem that involves _multiple users_ is when you mark the thread as resolved.
That did not happen until today. ;)

---

### Post by Cavsfan on 2013-07-17
Yesterday it was fixed but today it is broken again. There is no clock, network, logout, etc. icons whatsoever.  If it were not for Cario Dock I couldn't logout, restart etc.

[ATTACH=CONFIG]244825[/ATTACH]

---

### Post by muktupavels on 2013-07-17
Do you have indicators in /usr/share/unity/indicators/? Now they are loaded from this folder. There must be 4 indicator files - datetime, power, session and sound. 

For me after updates indicators where placed in wrong positions. I already submitted fix for that.

---

### Post by Cavsfan on 2013-07-18
> **albertsmuktupavels said:**
> Do you have indicators in /usr/share/unity/indicators/? Now they are loaded from this folder. There must be 4 indicator files - datetime, power, session and sound. 

For me after updates indicators where placed in wrong positions. I already submitted fix for that.

Yes indeed I do:
```
cavsfan@cavsfan-MS-7529:/usr/share/unity/indicators$ ls -l
total 16
-rw-r--r-- 1 root root 245 Jul 15 22:52 com.canonical.indicator.datetime
-rw-r--r-- 1 root root 233 Jul  7 22:07 com.canonical.indicator.power
-rw-r--r-- 1 root root 242 Jul 16 22:01 com.canonical.indicator.session
-rw-r--r-- 1 root root 284 Jul 15 22:24 com.canonical.indicator.sound
```

---

### Post by muktupavels on 2013-07-18
Have you tried reinstall indicator-applet-complete? If you still have problems, can you post your ~/.cache/indicator-applet-complete.log file?

Does anyone else have a problem with indicator-applet-complete?

---

### Post by mc4man on 2013-07-18
> **albertsmuktupavels said:**
> 

Does anyone else have a problem with indicator-applet-complete?
The new package works fine here other than the mentioned ordering.

---

### Post by muktupavels on 2013-07-18
> **mc4man said:**
> The new package works fine here other than the mentioned ordering.

Ordering will be resolved with next update, fix already merged.

P.S. Open file **/usr/share/themes/Ambiance/gtk-3.0/apps/gnome-panel.css** for editing, remove **padding: 0;** and save it. It will restore space between Applications and Places in panel.

---

### Post by mc4man on 2013-07-18
Can now see what Cavsfan reported - logins to flashback show no indicators.
I think it may happen if the applet crashes, after that it doesn't show again (in either a log out/in or full restart.
( ot - as far as log out/ins from gnome* sessions I'm not sure that a user actually fully logs out..
 
Edit: got the indicators back by forcing a new .config/dconf/user file. (saved the bad one first
Switching between the 2 I can get a login with indicators or a login without indicators.

There doesn't seem to be any real diff as far as schemas/keys values though many settings don't have schemas. There is a 4.8 kB diff between the bad & good user files (bad one is larger
Initially this looked promising but made no diff when adding 'indicators' to the bad login, - is good, + is bad

> -org.gnome.gnome-panel.layout object-id-list ['menu-bar', 'indicators', 'show-desktop', 'window-list', 'workspace-switcher']
+org.gnome.gnome-panel.layout object-id-list ['menu-bar', 'show-desktop', 'window-list', 'workspace-switcher']

---

### Post by Cavsfan on 2013-07-19
> **albertsmuktupavels said:**
> Have you tried reinstall indicator-applet-complete? If you still have problems, can you post your ~/.cache/indicator-applet-complete.log file?

Does anyone else have a problem with indicator-applet-complete?

I purged the file with SPM and then re-installed it and no changes.

> **mc4man said:**
> Can now see what Cavsfan reported - logins to flashback show no indicators.
I think it may happen if the applet crashes, after that it doesn't show again (in either a log out/in or full restart.
( ot - as far as log out/ins from gnome* sessions I'm not sure that a user actually fully logs out..
 
Edit: got the indicators back by forcing a new .config/dconf/user file. (saved the bad one first
Switching between the 2 I can get a login with indicators or a login without indicators.

There doesn't seem to be any real diff as far as schemas/keys values though many settings don't have schemas. There is a 4.8 kB diff between the bad & good user files (bad one is larger
Initially this looked promising but made no diff when adding 'indicators' to the bad login, - is good, + is bad

I renamed .config/dconf/user to user.old and rebooted. It rebuilt the file but, nothing changed and they are both the same size - 22.2kb.

The contents of ~/.cache/indicator-applet-complete.log:
```
DEBUG: Indicator-Applet-Complete - Icons directory: /usr/share/libindicator/icons/
WARNING: Indicator-Applet-Complete - Binding '<Super>S' failed!

DEBUG: Indicator-Applet-Complete - Looking at Module: libsyncindicator.so
DEBUG: Indicator-Applet-Complete - Loading Module: libsyncindicator.so
DEBUG: Indicator-Applet-Complete - Looking at Module: libapplication.so
DEBUG: Indicator-Applet-Complete - Loading Module: libapplication.so
DEBUG: Indicator-Applet-Complete - Looking at Module: libmessaging.so
DEBUG: Indicator-Applet-Complete - Loading Module: libmessaging.so
WARNING: libindicator - IndicatorObject class does not have an accessible description.
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from libmessaging.so
DEBUG: Indicator-Applet-Complete - Looking at Module: libprintersmenu.so
DEBUG: Indicator-Applet-Complete - Loading Module: libprintersmenu.so
DEBUG: Indicator-Applet-Complete - Looking at Module: libappmenu.la
DEBUG: Indicator-Applet-Complete - Looking at Module: libbluetooth.so
DEBUG: Indicator-Applet-Complete - Loading Module: libbluetooth.so
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
CRITICAL: Gtk - gtk_distribute_natural_allocation: assertion 'extra_space >= 0' failed
WARNING: Gtk - FIXME: assigning images is not implemented
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.sound
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.session
WARNING: Gtk - FIXME: assigning images is not implemented
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.datetime
DEBUG: Sync-Indicator - indicator-sync.c:249 setting accessible_desc to 'Sync'
DEBUG: Sync-Indicator - indicator-sync.c:217 setting visibility flag to 0
DEBUG: Indicator-Applet-Complete - Signal: Entry Removed
CRITICAL: Indicator-Applet-Complete - entry_removed: assertion 'menuitem != NULL' failed
DEBUG: Indicator-Application - Connected to Application Indicator Service.
CRITICAL: Gtk - gtk_distribute_natural_allocation: assertion 'extra_space >= 0' failed
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
DEBUG: Indicator-Application - Request current apps
WARNING: IDO - Can't load user avatar icon: Error opening file: No such file or directory
DEBUG: Indicator-Application - Building new application entry: :1.18  with icon: nm-device-wired at position 0
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from libapplication.so
CRITICAL: Gtk - gtk_distribute_natural_allocation: assertion 'extra_space >= 0' failed
WARNING: Gtk - FIXME: assigning images is not implemented
DEBUG: Indicator-Applet-Complete - Signal: Entry Removed
WARNING: GLib-GObject - g_object_disconnect: invalid signal spec "signal::show"
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from libmessaging.so
WARNING: Gtk - FIXME: assigning images is not implemented
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from libprintersmenu.so
DEBUG: Indicator-Applet-Complete - Signal: Entry Removed
WARNING: GLib-GObject - g_object_disconnect: invalid signal spec "signal::show"
CRITICAL: Gtk - gtk_distribute_natural_allocation: assertion 'extra_space >= 0' failed
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
WARNING: Gtk - FIXME: assigning images is not implemented
```

I still have no clock or anything in the top right panel in flashback.

---

### Post by mc4man on 2013-07-19
> **Cavsfan said:**
> I purged the file with SPM and then re-installed it and no changes.



I renamed .config/dconf/user to user.old and rebooted. It rebuilt the file but, nothing changed and they are both the same size - 22.2kb..
Getting a new .config/dconf/user file is a little tricky due to some changes in 13.04+. If you do as you did you get the same one again.
2 ways - 
Log in to another user account that can gain root privledges or boot to another install that either uses the same username or can gain root privledge. Then browse to that file & rename or delete, when you log back in to the account in question you'll get a new user file.

Easier - open system settings > keyboard > layout settings > Options > & enable 'key sequence to kill ..' as in screen
Then go to .config/dconf/ & rename user to a bak.  As** soon** as that is done kill X, re-login 
(the point is you want to kill X before anything new is written to dconf

Note: it's possible that with a new user file that you'll get the frickin unity launcher ect. when 1st. logging in to the new user file settings. If that happens go to .local/share & delete the  "session_migration-gnome" file, then log out/in

---

### Post by Cavsfan on 2013-07-19
> **mc4man said:**
> Getting a new .config/dconf/user file is a little tricky due to some changes in 13.04+. If you do as you did you get the same one again.
2 ways - 
Log in to another user account that can gain root privledges or boot to another install that either uses the same username or can gain root privledge. Then browse to that file & rename or delete, when you log back in to the account in question you'll get a new user file.

Easier - open system settings > keyboard > layout settings > Options > & enable 'key sequence to kill ..' as in screen
Then go to .config/dconf/ & rename user to a bak.  As** soon** as that is done kill X, re-login 
(the point is you want to kill X before anything new is written to dconf

Note: it's possible that with a new user file that you'll get the frickin unity launcher ect. when 1st. logging in to the new user file settings. If that happens go to .local/share & delete the  "session_migration-gnome" file, then log out/in

I booted into Raring and deleted the .config/dconf/user file from there and when I booted into Saucy I had the Unity panel. So I deleted the  session_migration-gnome file and logged out and backin but, the Unity panel was still there. I even rebooted and it was still the same.

It had reset everything back to default: the wallpaper, the window buttons are back on the left and the top did not show Applications and Places, but I opened up CCSM and set that back as it was. I unchecked Ubuntu Unity Plugin and I think that may have triggered the change because it looks great now! :D I have the clock, volume, network and logout indicators back at the top right on the panel. :D Just have to move the buttons back to the right as I like them and change my wallpaper back like it was.

Ironically the login screen showed my wallpaper that I had before (that changed a few days ago from the default orangish login screen).
But, I believe with your help **mc4man** It's working pretty well again with the clock and everything.
Thanks a lot! :D

---

### Post by mc4man on 2013-07-19
Not sure then what I did, maybe I deleted all the migration files??
Anyway it seems one needs to beware of when gnome-panel crashes, things could go south from there.

What you could do is once you're setup the way you like is copy .config/dconf/user somewhere. (& replace that copy every once & a while.

Then it something happens you can copy your backup to .config/dconf/ , ect. 
(just remember to do from another user/install or kill X right after copying.

One thing I have noticed is some of the defaults for gnome-panel in dconf seem wrong...

---

### Post by Cavsfan on 2013-07-20
> **mc4man said:**
> Not sure then what I did, maybe I deleted all the migration files??
Anyway it seems one needs to beware of when gnome-panel crashes, things could go south from there.

What you could do is once you're setup the way you like is copy .config/dconf/user somewhere. (& replace that copy every once & a while.

Then it something happens you can copy your backup to .config/dconf/ , ect. 
(just remember to do from another user/install or kill X right after copying.

One thing I have noticed is some of the defaults for gnome-panel in dconf seem wrong...

Thanks again. I made a backup of it on my usb drive. It is messes up again I'll know what to to (maybe :))

---

### Post by Cavsfan on 2013-07-30
You know **mc4man**, while this did restore the clock/date, logout buttons. network icon, etc. at the top right panel of Gnome Flashback.
Everything seems to work well but, when I click on the logout button and then click restart it does absolutely nothing.

I still have to use the logout icon in Cairo Dock to actually reboot (or sudo reboot in terminal).
It's just a phase though I believe. Things will be better towards final release. So, I guess it's nothing to worry about unless you know why it's doing that.
Just thought I'd mention that as I have been wanting to but, the forum was down.

---

### Post by Cavsfan on 2013-08-10
The clock problem was fixed but, the shutdown, resart does not work at the top right in flashback. Thought I would do as you 
suggested mc4man and recreate the user file in .config/dconf/ I even created the shortcut to kill the x server.

So, I renamed the file and immediately stopped the x server, relogged back in and it was all Unity once again with everything set back to default
until I fixed everything back in CCSM. Then I had to get the date and day back, my wallpaper, my icon theme and the windows buttons I had to move back
to the right. 

Yet still the only things that work are lock, which just takes you to the login screen, logout and suspend. 
Restart disappeared again shortly  after purging and re-installing indicator-applet-complete. It did not work and neither does shutdown.
I have to use the logout in Cairo Dock to restart.

Any one else still have this problem?

---

