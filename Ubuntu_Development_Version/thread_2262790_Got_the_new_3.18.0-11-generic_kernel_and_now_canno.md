---
title: "Got the new 3.18.0-11-generic kernel and now cannot enter password"
date: 2015-01-27
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-01-27
Anyone else have this problem? I updated to the 3.18.0-11-generic kernel and rebooted and there was no place to enter password so I could not login.

I believe I could have logged in as guest but I'm not interested in that.

I even tried the 3.18.0-9-generic but got the same results.

All I could get to was tty to reboot and am now in Precise writing this.

---

### Post by ventrical on 2015-01-27
+1 for Unity login after recent update/upgrade.

If you just click on the login area and then type your password blindly it will log in and you will see a flash display of the login dialoge feild.

Regards..

---

### Post by Cavsfan on 2015-01-27
> **ventrical said:**
> +1 for Unity login after recent update/upgrade.

If you just click on the login area and then type your password blindly it will log in and you will see a flash display of the login dialoge feild.

Regards..

Thanks! I'll try that.

---

### Post by Cavsfan on 2015-01-27
Yes, that did indeed work. Blind enter password - whoda thunk? :p

This has to be a bug doesn't it? Maybe there is one I don't know.

---

### Post by ventrical on 2015-01-27
> **Cavsfan said:**
> Yes, that did indeed work. Blind enter password - whoda thunk? :p

This has to be a bug doesn't it? Maybe there is one I don't know.


Unity greeter? Lightdm?   It's the dead of winter up here and things must be slow :)

Regards..

---

### Post by Elfy on 2015-01-27
glad to see this is at least ok in Xubuntu - didn't see this thread before I logged out :p

---

### Post by Elfy on 2015-01-27
> **ventrical said:**
> Unity greeter? Lightdm?   It's the dead of winter up here and things must be slow :)

Regards..

Perhaps unity greeter - the one we use is ok and lightdm seems fine here too.

---

### Post by ventrical on 2015-01-27
> **Elfy said:**
> Perhaps unity greeter - the one we use is ok and lightdm seems fine here too.

I'll try my other distros.

Thanks..

---

### Post by ventrical on 2015-01-27
gnome-session fine ..

---

### Post by Cavsfan on 2015-01-27
Unity greeter? I thought I login via Lightdm, which has the password problem, and from there select Default (Unity) or Gnome Flashback (with compiz), etc.

I don't see no stinking Unity greeter! :p

---

### Post by Cavsfan on 2015-01-27
> **ventrical said:**
> gnome-session fine ..

Gnome Shell?

---

### Post by ventrical on 2015-01-27
@cavsfan

You can mee too this bug if you like.

 [URL="https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1415168"]https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1415168


[/URL]

---

### Post by ventrical on 2015-01-27
> **Cavsfan said:**
> Gnome Shell?

:) .. yea .. Shell ... :)
  me    zzzzzzzzzz...

---

### Post by Cavsfan on 2015-01-27
> **ventrical said:**
> @cavsfan

You can mee too this bug if you like.

 [URL="https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1415168"]https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1415168

[/URL]

I me tooed that baby! Thanks for pointing it out!

> **Cavsfan said:**
> Gnome Shell?

> **ventrical said:**
> :) .. yea .. Shell ... :)
  me    zzzzzzzzzz...

:lol: Yeah there's Gnome shell and Gnome Flashback so I was cornfused. :lol:

---

### Post by Doug S on 2015-01-27
So glad I had seen this thread earlier today, and therefore wasn't surprised and knew exactly what to do after updates and re-boot just now.

---

### Post by ventrical on 2015-01-27
hey guys .. thanks for the mee toos ! :)

---

### Post by ventrical on 2015-01-27
> **Elfy said:**
> Perhaps unity greeter - the one we use is ok and lightdm seems fine here too.

+1

---

### Post by buzzingrobot on 2015-01-28
Fixed here with the latests updates, which included unity-greeter.

---

### Post by Cavsfan on 2015-01-28
> **Doug S said:**
> So glad I had seen this thread earlier today, and therefore wasn't surprised and knew exactly what to do after updates and re-boot just now.

I at first looked to see if there was anything about this and posted it. Luckily Ventrical is a wizard and knew just to type it in like normal.
I thought I could not get in until I seen his post.

> **buzzingrobot said:**
> Fixed here with the latests updates, which included unity-greeter.

Indeed it was and that didn't take long.  I don't understand what is in the changelog that fixed it but it is fixed.

```
unity-greeter (15.04.2-0ubuntu2) vivid; urgency=medium

  [ Iain Lane ]
  * Set GSETTINGS_SCHEMA_DIR and install an icon theme.

  [ Lars Uebernickel ]
  * Remove old code for drawing DashEntry that is no longer needed.

 -- Dmitry Shachnev <mitya57@ubuntu.com>  Wed, 28 Jan 2015 13:48:58 +0300
```

---

### Post by Doug S on 2015-01-28
> **Cavsfan said:**
> Indeed it was and that didn't take long.  I don't understand what is in the changelog that fixed it but it is fixed.

```
unity-greeter (15.04.2-0ubuntu2) vivid; urgency=medium

  [ Iain Lane ]
  * Set GSETTINGS_SCHEMA_DIR and install an icon theme.

  [ Lars Uebernickel ]
  * Remove old code for drawing DashEntry that is no longer needed.

 -- Dmitry Shachnev <mitya57@ubuntu.com>  Wed, 28 Jan 2015 13:48:58 +0300
```Hmmm... The chanelog at that level seems incomplete to me. As I understand it from the bug report the issue was this:```
 [ Lars Uebernickel ]
     DashEntry: remove .spinner class
 Spinners are drawn differently now, which caused the entry to be not drawn at all.
 This depends on the theme setting (and animating) the -gtk-icon-source of thisentry.
```Anyway, things are back to normal, after applying this mornings updates.

---

