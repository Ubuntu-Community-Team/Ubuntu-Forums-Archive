---
title: "Firefox Fullscreen (F11) Lost with 12.04 ?"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by SemiExpert on 2012-04-22
With 12.04, there is no longer a true Fullscreen (F11) functionality with Firefox.  I'm using Firefox 11, Ubuntu Firefox Modifications 2.0.2, and engaging Fullscreen mode only causes the top Unity panel to disappear.  I'm left with the tabs panel of Firefox - which most definitely isn't a true Fullscreen mode.  Disabling Ubuntu Firefox Modifications 2.0.2 doesn't fix the the issue.  In contrast, Fullscreen (F11) works in Ubuntu 11.10 on Firefox 11, Ubuntu Firefox Modifications 1.0.3?  It lookes like an Ubuntu 12.04 issue?

---

### Post by r-senior on 2012-04-22
Working OK here -- switching to fullscreen makes the tabs and bookmarks bar slide up off the top of the screen after a delay. Same version of Firefox, same version of Ubuntu Firefox modifications and 12.04. Updated this morning.

I tried switching between tabs on top and otherwise and it still works.

EDIT: Are you using Unity or Unity 2D? Or something else?

---

### Post by sammiev on 2012-04-22
Also works here with latest FF and 12.04 with gnome3. Updated today.

---

### Post by SemiExpert on 2012-04-22
> **r-senior said:**
> Working OK here -- switching to fullscreen makes the tabs and bookmarks bar slide up off the top of the screen after a delay. Same version of Firefox, same version of Ubuntu Firefox modifications and 12.04. Updated this morning.

I tried switching between tabs on top and otherwise and it still works.

EDIT: Are you using Unity or Unity 2D? Or something else?

 In both 11.10 and 12.04, Unity.  No matter how long the cursor is inactive, the tabs bar doesn't dissappear.

---

### Post by PaulW2U on 2012-04-22
Works here on my netbook, Ubuntu 12.04 (Unity) and my laptop, Kubuntu 12.04.

---

### Post by r-senior on 2012-04-22
> **SemiExpert said:**
> In both 11.10 and 12.04, Unity.  No matter how long the cursor is inactive, the tabs bar doesn't dissappear.
What happens if you switch to a guest session* and run Firefox. Does it work then?

* Click on your username and select "Guest Session".

---

### Post by SemiExpert on 2012-04-22
> **r-senior said:**
> What happens if you switch to a guest session* and run Firefox. Does it work then?

* Click on your username and select &quot;Guest Session&quot;.

 Fullscreen works in a Guest session, but it doesn't for the default user.  I've attempted to disable all extensions, I've disabled all applets, restored appearance settings to default, tried Unity 2D, Gnome and Gnome without effects - and still no true Fullscreen mode for the default user?  But it works for a Guest Session?

---

### Post by r-senior on 2012-04-22
OK, so it's something in your user account. But where?

How about close Firefox, rename ~/.mozilla, e.g.

```
mv ~/.mozilla ~/.mozilla-backup
```

Then try opening Firefox again. That will tell you if it's something in the Firefox config or elsewhere.

---

### Post by SemiExpert on 2012-04-22
> **r-senior said:**
> OK, so it's something in your user account. But where?

How about close Firefox, rename ~/.mozilla, e.g.

```
mv ~/.mozilla ~/.mozilla-backup
```Then try opening Firefox again. That will tell you if it's something in the Firefox config or elsewhere.

 Okay, so I renamed the .mozilla folder and Fullscreen is functional.  Hmmm....

---

### Post by r-senior on 2012-04-22
Hmmm indeed!

As there doesn't seem to be a "Show Tab Bar in Fullscreen" option ;), it might be easiest to just keep your new .mozilla folder and set up Firefox again. I suspect reverting back to the old folder would allow you to export bookbarks and make a note of your add-ons.

Other than that, I'm out of ideas.

---

### Post by SemiExpert on 2012-04-22
> **r-senior said:**
> Hmmm indeed!

As there doesn't seem to be a &quot;Show Tab Bar in Fullscreen&quot; option ;), it might be easiest to just keep your new .mozilla folder and set up Firefox again. I suspect reverting back to the old folder would allow you to export bookbarks and make a note of your add-ons.

Other than that, I'm out of ideas.

 Fair enough, I'm out of ideas as well.  I did install Seamonkey as a backup browser from the Ubuntuzilla repository, and I can't uninstall it from either the command line or Software Center.  Oh well, with the final release on the 28th, I think I'll just reinstall from scratch.

---

### Post by lovinglinux on 2012-04-23
Most likely that you have assigned F11 key to some Compiz feature. Check Compiz settings and unassign F11.

You can also achieve full screen through "View >>> Full Screen" menu in Firefox.

---

