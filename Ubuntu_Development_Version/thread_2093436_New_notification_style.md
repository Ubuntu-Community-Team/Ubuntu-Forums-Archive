---
title: "New notification style?"
date: 2012-12-10
forum: Ubuntu Development Version
---

### Post by pressureman on 2012-12-10
I'm not sure if this is a GNOME Shell only thing, or also affects Unity. I noticed a new style of notification popups yesterday, and don't recall doing anything in particular to get them... is this the new style?

See attached screenshot.

---

### Post by d.atanasov on 2012-12-10
Hi, 

I don`t see any change in the style, but the color. And here I don`t know if it is your preferred or it has changed ? 

cheers

---

### Post by kostkon on 2012-12-10
These are the ubuntu ones (since 10.04 [or 9.10]). Gnome Shell's notifications appear at the bottom of the screen and look differently.

---

### Post by ventrical on 2012-12-10
Nothing here in Unity 3D  running:

Linux dale-desktop 3.7.0-030700rc8-generic #201212031649 SMP Mon Dec 3 22:00:46 UTC 2012 i686 i686 i686 GNU/Linux

---

### Post by pressureman on 2012-12-10
> **kostkon said:**
> These are the ubuntu ones (since 10.04 [or 9.10]). Gnome Shell's notifications appear at the bottom of the screen and look differently.

Exactly... that's why I was kind surprised to see these again. I'm running GNOME Shell 3.6.2.

Did I break something?? In all honesty, I prefer these ones. I never liked the GNOME Shell notifications... you kinda had to chase them, as they liked to hide from the mouse ;-)

---

### Post by screaminj3sus on 2012-12-10
> **pressureman said:**
> Exactly... that's why I was kind surprised to see these again. I'm running GNOME Shell 3.6.2.

Did I break something?? In all honesty, I prefer these ones. I never liked the GNOME Shell notifications... you kinda had to chase them, as they liked to hide from the mouse ;-)

It just means you have notify-osd running under gnome-shell

---

### Post by VinDSL on 2012-12-10
> **pressureman said:**
> Exactly... that's why I was kind surprised to see these again. I'm running GNOME Shell 3.6.2 [...]

I'm running GS 3.7.2 and the notifier is still at the bottom...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-10-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-dec-2012-1.png")[/INDENT]


> **screaminj3sus said:**
> It just means you have notify-osd running under gnome-shell
I might try that. I hate having notifications pop-up at the bottom.

Er...

How would one go about it?!?!?

---

### Post by pressureman on 2012-12-10
> **VinDSL said:**
> I might try that. I hate having notifications pop-up at the bottom.

Er...

How would one go about it?!?!?

Since I didn't intentionally enable this, I really have no idea... but once I find out, I'll be adding this to my list of "Things To Do After Installing Ubuntu"... along with disabling overlay scrollbars and modal dialogs :-|

Edit: After a bit of searching, I suspect this might be the cuplrit:

```

$ cat /usr/share/dbus-1/services/org.freedesktop.Notifications.service
[D-BUS Service]
Name=org.freedesktop.Notifications
Exec=/usr/lib/x86_64-linux-gnu/notify-osd

```

I'm not 100% sure, but I think the Exec line usually refers to notification-daemon instead of notify-osd... can any GS-user confirm?

---

### Post by pqwoerituytrueiwoq on 2012-12-10
looks like just the color to me, i noticed it seemed to change with the wallpaper
i don't use unity often, i use xfce (in a gnome2 layout with compiz) mainly

---

### Post by mc4man on 2012-12-10
> **pressureman said:**
> Since I didn't intentionally enable this, I really have no idea... but once I find out, I'll be adding this to my list of "Things To Do After Installing Ubuntu"... along with disabling overlay scrollbars and modal dialogs :-|

Edit: After a bit of searching, I suspect this might be the cuplrit:

```

$ cat /usr/share/dbus-1/services/org.freedesktop.Notifications.service
[D-BUS Service]
Name=org.freedesktop.Notifications
Exec=/usr/lib/x86_64-linux-gnu/notify-osd

```

I'm not 100% sure, but I think the Exec line usually refers to notification-daemon instead of notify-osd... can any GS-user confirm?

On an Ubuntu install the above is normal, what session logged into doesn't matter.
Are you using Ubuntu > GS or the GS only image?

(I don't have any issue with notifications showing at the bottom of the screen, the latest Ubuntu GS displays them off the bottom of the screen, only see half of the close button. The opposite of what a recent commit meant to fix which never was broken here.

---

### Post by serdotlinecho on 2012-12-11
Notication still at the bottom. Gnome-shell 3.6.2 with latest raring updates.

[IMG]http://i.imgur.com/E8pB2.jpg[/IMG]

---

### Post by pressureman on 2012-12-11
rofl.... the notifications are back to the GS-style, bottom-of-the-screen type.

And I have no idea how that happened. Gotta love beta testing ;-)

---

### Post by pqwoerituytrueiwoq on 2012-12-11
> **pressureman said:**
> rofl.... the notifications are back to the GS-style, bottom-of-the-screen type.

And I have no idea how that happened. Gotta love beta testing ;-)
you mean alpha testing
[https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule](https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule)

---

### Post by pressureman on 2012-12-12
> **pqwoerituytrueiwoq said:**
> you mean alpha testing
[https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule](https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule)

Nitpick much? Raring doesn't yet have any official alpha releases (not for the Ubuntu flavour anyway), so technically it's not even alpha testing :p

---

