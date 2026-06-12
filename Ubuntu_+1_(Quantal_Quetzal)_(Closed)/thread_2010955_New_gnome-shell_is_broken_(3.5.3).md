---
title: "New gnome-shell is broken (3.5.3)"
date: 2012-06-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-06-26
The newest gnome-shell 3.5.3 in official repos is broken.
It starts without panels and without functions.
You need to use the 3.4.1 version.

---

### Post by dino99 on 2012-06-26
i'm still curious to know about % users using it ;)

---

### Post by jbicha on 2012-06-26
This will be fixed with the next gnome-shell upload later today; thanks to Rico for the fix. I didn't experience it on my computer because I had a broken GDM 3.4 installed. Since you don't have GDM 3.4 installed, gnome-shell crashes.

By the way, this was in quantal-proposed. If you want quantal to work reliably, you probably don't want to use -proposed.

---

### Post by lonniehenry on 2012-06-26
I'm in the gnome-shell users group.  I usually keep a gnome-shell and a unity testing partition going, but I find gs fits my workflow better.  Waiting for the update.

---

### Post by Harry33 on 2012-06-26
> **jbicha said:**
> This will be fixed with the next gnome-shell upload later today; thanks to Rico for the fix. I didn't experience it on my computer because I had a broken GDM 3.4 installed. Since you don't have GDM 3.4 installed, gnome-shell crashes.

By the way, this was in quantal-proposed. If you want quantal to work reliably, you probably don't want to use -proposed.

Thanks in advance.
Well Quantal is in an early dev phase anyway, so breakages are expected.

---

### Post by kaldor on 2012-06-26
> **dino99 said:**
> i'm still curious to know about % users using it ;)

*raises hand* :KS

---

### Post by ronacc on 2012-06-26
> **dino99 said:**
> i'm still curious to know about % users using it ;)

I am a gnome-shell user exclusively .

---

### Post by jfernyhough on 2012-06-26
I tend to use Rico's PPA for GNOME stuff. gnome-shell is working fine for me :D

I just wish there was a way (I knew of) of putting the system tray in the top bar...

---

### Post by VinDSL on 2012-06-26
Seems like everything is working, for me, except "gnome-tweak-tool".

I'd like to get that back...  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-26-jun-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-26-jun-2012-1.png")[/INDENT]

---

### Post by Harry33 on 2012-06-27
> **VinDSL said:**
> Seems like everything is working, for me, except "gnome-tweak-tool".

I'd like to get that back...  ;)

Tweak-tool not working here either.
Also I noticed I am not able to choose to show seconds in the panel clock.
Then again, we do not need to press "alt" anymore to reboot or shut down.

Perhaps related, nautilus does not show icons any more (pics, pdf).

---

### Post by pressureman on 2012-06-27
VinDSL, you sure do love to show off your desktop... ever thought about taking pictures of your computer to attach to each reply also? ;-)

gnome-tweak-tool is working fine for me here, after I... tweaked it.

Here's a unidiff showing which line you'll need to comment to avoid a Python KeyError exception. I hope you guys can deal with this old fashioned, monochrome, 8-bit ASCII stuff.

```

--- /usr/share/pyshared/gtweak/tweaks/tweak_nautilus.py.bak	2012-06-27 07:25:01.094351723 +0200
+++ /usr/share/pyshared/gtweak/tweaks/tweak_nautilus.py	2012-06-27 07:25:04.386368087 +0200
@@ -45,7 +45,7 @@
 
 TWEAKS = (
     DesktopIconTweak(group_name=TWEAK_GROUP_DESKTOP),
-    GSettingsSwitchTweak("org.gnome.nautilus.desktop", "computer-icon-visible", schema_filename="org.gnome.nautilus.gschema.xml",group_name=TWEAK_GROUP_DESKTOP),
+    #GSettingsSwitchTweak("org.gnome.nautilus.desktop", "computer-icon-visible", schema_filename="org.gnome.nautilus.gschema.xml",group_name=TWEAK_GROUP_DESKTOP),
     GSettingsSwitchTweak("org.gnome.nautilus.desktop", "home-icon-visible", schema_filename="org.gnome.nautilus.gschema.xml",group_name=TWEAK_GROUP_DESKTOP),
     GSettingsSwitchTweak("org.gnome.nautilus.desktop", "network-icon-visible", schema_filename="org.gnome.nautilus.gschema.xml",group_name=TWEAK_GROUP_DESKTOP),
     GSettingsSwitchTweak("org.gnome.nautilus.desktop", "trash-icon-visible", schema_filename="org.gnome.nautilus.gschema.xml",group_name=TWEAK_GROUP_DESKTOP),

```

---

### Post by VinDSL on 2012-06-27
> **pressureman said:**
> VinDSL, you sure do love to show off your desktop... ever thought about taking pictures of your computer to attach to each reply also? ;-)
I've been known to do that too, on hardware sites (like AnandTech).  LoL!

EXAMPLE:  [Cooler Master CoolViva Z1 VGA Heatsink | XFX GeForce 7600 GT AGP]("http://forums.anandtech.com/showthread.php?t=2235595")

I was merely offering the screenie up as "evidence" that gnome-shell 3.5.3 was working fine for me, sans gnome-tweak-tool.

Talk is cheap, you know?  Ppl can claim anything they want.

"DNA doesn't lie".  Heh!  :D

---

### Post by Harry33 on 2012-06-27
Nautilus icons are not OK, after some gnome-desktop upgrades.
So marking this as solved.

BTW I use now Gnome Shell Testing PPA gnome-tweak-tool and that one works.

---

### Post by VinDSL on 2012-06-27
> **Harry33 said:**
> I use now Gnome Shell Testing PPA gnome-tweak-tool and that one works.
That one now works for me.

Thanks!!!  :)

---

### Post by jfernyhough on 2012-06-29
Anyone else noticed that they're starting to implement global menus? I'm hoping there will be an extension that allows the menu to be shown along the top bar rather than hidden behind a click the window title on the top bar...

---

