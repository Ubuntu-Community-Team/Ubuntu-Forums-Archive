---
title: "Lightdm background doesn't change?"
date: 2013-02-11
forum: Ubuntu Development Version
---

### Post by screaminj3sus on 2013-02-11
I did a clean install from today's iso, and noticed the lightdm background now refuses to change. If I change the backgroung either via one of the default backgrounds in control center or via eog lightdm keeps using the purple background. Does this happen to anyone else?

---

### Post by VinDSL on 2013-02-11
> **screaminj3sus said:**
> Does this happen to anyone else?

LightDM does all sorts of nasty stuff, on this rig.

Yes, sometimes the background refuses to change, then it starts changing again, for no apparent reason, e.g. it seems to have a mind of its own.

The icons in the upper-right corner always look like grunt (no background at all) ever since I upgraded to RR.  This has never changed.

Et cetera, et cetera, blah, blah, blah.  Don't get me going!  LoL!  :D

Personally, I prefer using GDM these days.  I switch back and forth between LightDM and GDM. 

IMO, GDM rules and LightDM drools.

Anyway, what you are experiencing with LightDM is (unfortunately) normal these days...  ;)

---

### Post by mc4man on 2013-02-11
On a 2 week old or so install all is well in this regard, on a new install from the other day see the same. The greeter does not use anything but the default background (purple whatever

May be able to find out why later, may not..

---

### Post by mc4man on 2013-02-11
Can see in /var/log/lightdm/x-0-greeter.log where it 'skips' over setting a custom background vs. the log from older install where it does.

You actually don't need a new install to see - 
On my slightly older install where it works fine created a new user, that user will not get a custom greeter screen while my orig user will.
(haven't tried switching backgrounds on my working user & likely won't.

You should file a bug on if there isn't one already - didn't see one.

---

### Post by mc4man on 2013-02-11
Seems  to be caused by the new ubuntu-settings package  - 
> ubuntu-settings (12.10.7) raring; urgency=low

  * Disable gnome-settings-daemon plugins:
    - print-notifications: We use indicator-printer
    - updates: That uses PackageKit, we use update-notifier/update-manager.
    - background: Nautilus renders the background, this imposes an unnecessary
      check at startup.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Fri, 01 Feb 2013 09:33:44 +0100

downgrading to previous allows custom greeter, maybe they've something in mind
(to test a downgrade may be a little convoluted - 
Edit: No need to downgrade - just run this, restart, login, change background, ect.
```
gsettings set org.gnome.settings-daemon.plugins.background active true

```

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1122619](https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1122619)

---

### Post by unheeding on 2013-02-11
My background stopped changing because I enabled encryption on my /home/ directory, so attempting to load a file from there before I log in is a no go.

---

### Post by screaminj3sus on 2013-02-12
> **mc4man said:**
> Seems  to be caused by the new ubuntu-settings package  - 

downgrading to previous allows custom greeter, maybe they've something in mind
(to test a downgrade may be a little convoluted - 
Edit: No need to downgrade - just run this, restart, login, change background, ect.
```
gsettings set org.gnome.settings-daemon.plugins.background active true

```

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1122619](https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1122619)

thanks :)

---

### Post by grahammechanical on 2013-02-12
This is happening on my daily updated Raring install. I did not notice as I use the rotating wallpapers and that setting always gives warty-final-ubuntu.png as the LightDM background image.

But setting a static wallpaper no longer gives that wallpaper as the background to LightDM.

Regards.

---

### Post by ventrical on 2013-02-12
Ditto .. I thought it was only me.

---

### Post by Baldrick_NZ on 2013-02-15
> **VinDSL said:**
> I switch back and forth between LightDM and GDM...

Sorry to crash the thread, but how do you do this?

Cheers.

EDIT: Sorted. Google really is my friend! lol

---

### Post by mc4man on 2013-03-21
This has been fixed in nautilus (1:3.6.3-0ubuntu11)
So should be ok on new installs that contain the ^ or higher, older may need to change background once then back to get current in greeter.  (assuming the g-s-d plugin is set to inactive

---

### Post by ManamiVixen on 2013-03-22
I actually preferred the wallpaper to be static on LightDM. That way other users can't peek at what you have as a background on your desktop by selecting your account name in the selection box.

---

### Post by mc4man on 2013-03-22
> **ManamiVixen said:**
> I actually preferred the wallpaper to be static on LightDM. That way other users can't peek at what you have as a background on your desktop by selecting your account name in the selection box.

Well then unfortunately the easy way to adjust on or off thru gsetting the g-s-d plugin is gone. Can't see it being user addressable thru nautilus.

If one wanted the plugin setting back in 13.04 the it would be pretty simple to just rebuild nautilus & revert the patch.
( patch -R -Np1 < ./debian/patches/10_sync_background_to_accountsservice.patch

unless someone's got time on their hands don't see the schema being removed in 13.04 so it would again be usable

---

### Post by bmwerks on 2013-04-30
> **mc4man said:**
> Seems  to be caused by the new ubuntu-settings package  - 

downgrading to previous allows custom greeter, maybe they've something in mind
(to test a downgrade may be a little convoluted - 
Edit: No need to downgrade - just run this, restart, login, change background, ect.
```
gsettings set org.gnome.settings-daemon.plugins.background active true

```

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1122619](https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1122619)

i just upgraded to 13.04 and my background disappeared i only saw a blue screen(except when the screen was locked, then i saw the background)
i followed these steps and it worked for me.... though i did it differently i went into 'dconf editor' followed org.gnome.settings-daemon.plugins.background then ticked the option to active and my background came back immediately no restart or anything

THANKS FOR THE GUIDANCE

---

