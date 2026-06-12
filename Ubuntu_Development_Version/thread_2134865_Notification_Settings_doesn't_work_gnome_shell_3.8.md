---
title: "Notification Settings doesn't work gnome shell 3.8"
date: 2013-04-12
forum: Ubuntu Development Version
---

### Post by DisappearingOak on 2013-04-12
I'm using GS 3.8 installed via ppa on Ubuntu 13.04 final beta. Notifications work perfectly but right clicking Notification Settings in system tray does nothing and nothing opens. Any way to fix it?

---

### Post by Frogs Hair on 2013-04-12
Make sure the shell theme is compatible this happens with 3.6 also with incomputable themes .

---

### Post by DisappearingOak on 2013-04-12
I'm using the default shell theme. :)

---

### Post by Frogs Hair on 2013-04-12
Try Alt + F2 ```
r
```

---

### Post by DisappearingOak on 2013-04-12
It restarted the desktop but still nothing. Rebooting doesn't do anything either. I suspect I might be missing some package? Because I'm using the Gnome 3.8 ppa installed on top of the regular Unity beta. Everything is perfect except for the notification settings. I'll try reinstalling the gnome control center maybe that might help.

---

### Post by jbicha on 2013-04-13
Customizing the notifications settings requires Settings 3.8 which needs a fair amount of work before it will be ready for Ubuntu.

---

### Post by sgage on 2013-04-13
> **DisappearingOak said:**
> I'm using GS 3.8 installed via ppa on Ubuntu 13.04 final beta. Notifications work perfectly but right clicking Notification Settings in system tray does nothing and nothing opens. Any way to fix it?

It's working here, with a fully updated system as of this minute (see timestamp on post :-). I'm using both gnome3-team and gnome3-team/staging, for what it's worth.

---

### Post by VinDSL on 2013-04-14
> **sgage said:**
> It's working here, with a fully updated system as of this minute (see timestamp on post :-). I'm using both **gnome3-team** and **gnome3-team/staging**, for what it's worth.
Working here, too.

BTW, I'm using the same PPAs as you, plus **~ricotz/+archive/testing**  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-14-apr-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-14-apr-2013-1.png")[/INDENT]

---

### Post by jbicha on 2013-04-14
> **sgage said:**
> It's working here, with a fully updated system as of this minute (see timestamp on post :-). I'm using both gnome3-team and gnome3-team/staging, for what it's worth.

Yes it will work if you use the GNOME3 Staging PPA but I don't recommend using that PPA (unless you like the bleeding edge) as several of those packages have known bugs.

---

### Post by sgage on 2013-04-14
> **jbicha said:**
> Yes it will work if you use the GNOME3 Staging PPA but I don't recommend using that PPA (unless you like the bleeding edge) as several of those packages have known bugs.

I thought that's what ricotz/testing was for :KS

---

