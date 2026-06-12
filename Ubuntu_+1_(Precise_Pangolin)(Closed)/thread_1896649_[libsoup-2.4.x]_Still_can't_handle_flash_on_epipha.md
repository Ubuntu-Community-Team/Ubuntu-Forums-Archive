---
title: "[libsoup-2.4.x] Still can't handle flash on epiphany... :S"
date: 2011-12-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tista on 2011-12-17
Guys,

I've been trying git based epiphany browser on PP.
In past, ver 3.1.91 via nspluginwrapper could playback flash movies like YouTube, but now, 3.3.2 with git based libsoup 2.4 could not do that... XS

When I run ephy from term, I've seen these errors causing with libsoup:
```
libsoup-CRITICAL **: soup_message_io_pause: assertion `io != NULL' failed

libsoup-CRITICAL **: soup_message_io_unpause: assertion `io != NULL' failed
```

On ubuntu repository didn't reach for that 2.4.x yet, but as this results, ephy 3.3.x with libsoup 2.4.x can't playback any flashes for a while??

Or someone already filed this bug onto bugzilla? :)

Regards,
Tista

---

### Post by tista on 2011-12-20
Guys,

OMG... Just now I've found that the latest gnome-shell 3.3.2 on RicotzPPA would need some newer (git based) libsoup to run!! :/

I've noticed that when I update rico's packages today, then gdm-greeter crashed... and also "gnome-shell --replace" would send me some critical messages!

@Ubuntu devs:
Please update libsoup to 2.4.x now!!

---

### Post by Harry33 on 2011-12-20
> **tista said:**
> Guys,

OMG... Just now I've found that the latest gnome-shell 3.3.2 on RicotzPPA would need some newer (git based) libsoup to run!! :/

I've noticed that when I update rico's packages today, then gdm-greeter crashed... and also "gnome-shell --replace" would send me some critical messages!

@Ubuntu devs:
Please update libsoup to 2.4.x now!!

What?
Gnome-shell (from today, Gnome-shell Testing PPA) works here fine with the Precise repo version of libsoup2.4 (2.36.1-1ubuntu1).

---

### Post by jbicha on 2011-12-20
By the way, the latest unstable libsoup is built in the [GNOME 3 PPA]("https://launchpad.net/%7Egnome3-team/+archive/gnome3/+packages?field.series_filter=precise") which will eventually contain the parts of GNOME 3.4 that don't make it into the official precise repositories.

---

### Post by Harry33 on 2011-12-20
> **jbicha said:**
> By the way, the latest unstable libsoup is built in the [GNOME 3 PPA]("https://launchpad.net/%7Egnome3-team/+archive/gnome3/+packages?field.series_filter=precise") which will eventually contain the parts of GNOME 3.4 that don't make it into the official precise repositories.

That is right.
I just installed that version (2.37.3-0ubuntu0~precise1), it works just fine with Gnome-shell Testing PPA contents.
But, like I just said above, it is not necessary for the newest Gnome-shell (3.2.2).

---

### Post by tista on 2011-12-20
> **jbicha said:**
> By the way, the latest unstable libsoup is built in the [GNOME 3 PPA]("https://launchpad.net/%7Egnome3-team/+archive/gnome3/+packages?field.series_filter=precise") which will eventually contain the parts of GNOME 3.4 that don't make it into the official precise repositories.

Hi jbicha! :)

Thanks a lot!!
But  as far as I know I suppose Webkitgtk3 might have some unstable issues with gtk3 based web browsers (ephy, midori, and so..) on libsoup, So I really hope those issues could solve till gnome 3.4 had been released... ;)

Thanks again for your amazing work!!

Cheers.

---

### Post by tista on 2011-12-20
> **Harry33 said:**
> That is right.
I just installed that version (2.37.3-0ubuntu0~precise1), it works just fine with Gnome-shell Testing PPA contents.
But, like I just said above, it is not necessary for the newest Gnome-shell (3.2.2).

Hi Harry33.

Yeah gs 3.2.2 would be OK with libsoup 2.36... 
Or maybe my PP system would be caused by mixing some git sources with Rico's one. If so, please forget about my posts... ;)

Cheers.

---

