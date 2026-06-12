---
title: "Locking screen when closing Lid with Darter"
date: 2007-07-09
forum: System76 Support
---

### Post by beuno on 2007-07-09
Since you guys have been so friendly, I'm taking the liberty to ask a few more questions.

I want my Darter to lock my screen when I close the lid (not suspend/hibernate), and it seems everything is set en gnome to do this.
I have traced it to a file being called */etc/acpi/lid.sh*, but it seems to do a lot of things which I don't think I want to break.
It works fine (be default even) in my other laptop.

Any ideas how I can get this laptop to do the same?

---

### Post by thomasaaron on 2007-07-09
This works fine on my Darter.

In System > Preferences > Power Management...

Under both the "AC" and "Battery" tabs, in the pull-down menu beside "When laptop lid is closed:",
select "Blank Screen."

---

### Post by beuno on 2007-07-09
I have both set like that (attaching screenshots).

The screen does go blank, it just doesn't lock the session.

---

### Post by beuno on 2007-07-10
I tested it a few different ways, and when I do a fresh boot, and close my lid, I do get asked for a password.

But from then on, never again.

---

### Post by AusIV4 on 2007-07-11
I have a similar problem on my Gazelle. After I resume from suspend, hotkeys managed by ACPI (including the lid switch) are no longer recognized. This means I can't get my laptop to do anything reliably when I close the lid. I first reported this back in February, so I've pretty much given up hope for a fix.

---

### Post by beuno on 2007-07-11
> **AusIV4 said:**
> I have a similar problem on my Gazelle. After I resume from suspend, hotkeys managed by ACPI (including the lid switch) are no longer recognized. This means I can't get my laptop to do anything reliably when I close the lid. I first reported this back in February, so I've pretty much given up hope for a fix.

You shouldn't loose hope, I'm sure the fine people at System76 will figure it out  :D

---

### Post by beuno on 2007-08-07
Well, I finally figured it out.

The solution (albeit a bit weird), was to have the "lock screen when screensaver is active" option on, in "Screensaver Preferences".

That locks my screen every time I close the lid/leave it alone for a while.

---

