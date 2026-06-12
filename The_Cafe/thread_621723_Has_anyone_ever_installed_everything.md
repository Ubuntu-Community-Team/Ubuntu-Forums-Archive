---
title: "Has anyone ever installed everything???"
date: 2007-11-24
forum: The Cafe
---

### Post by Ocxic on 2007-11-24
well,, I was just wondering if anyone has ever had the notion to try installing everything in the repositories.

I've made a mirror for myself just for fun and just had the idea..

---

### Post by -grubby on 2007-11-24
I'm thinking that would take a while

---

### Post by dasunst3r on 2007-11-24
I'm sure you might hit a roadblock somewhere, particularly in installing kernel-related stuff.

---

### Post by Polygon on 2007-11-24
there are a couple things (maybe a lot who knows) that cant be intalled when a certain package is installed

the best example i can think of.....if you try to install totem-xine while totem-gstreamer is installed, it will remove totem-gstreamer. so therefore just right there you cant install EVERYTHING in the repos.

---

### Post by Linuxratty on 2007-11-24
No...There are apps i will never use,so I see no reason to install them.

---

### Post by bruce89 on 2007-11-24
> **Polygon said:**
> if you try to install totem-xine while totem-gstreamer is installed, it will remove totem-gstreamer.

>  totem  (2.20.0-3) unstable; urgency=low

   * Complete rework of debian/rules.
   * Split data files in totem-common.
   * Make totem-xine and totem-gstreamer installable together.
     Closes: [#402549]("http://bugs.debian.org/402549").
   * Move debugging symbols to totem-dbg.
   * Move plugins to totem-plugins.
   * Switch to quilt.
   * Refresh patches.
   * Fix menu files and ship them in both packages.
   * 60_gnome-doc-utils.patch: regenerate help/Makefile.in with a newer
     gnome-doc-utils.make that supports out-of-tree builds.
   * Build-depend on libbluetooth-dev and libgalago-dev for the
     corresponding plugins.
   * Remove symbolic links in the firefox directory.
   * Improve long package descriptions.

 -- Josselin Mouette <joss@debian.org>  Wed, 26 Sep 2007 22:36:06 +0200 

Good old Debian does all the work.

---

### Post by BWF89 on 2007-11-24
> **Polygon said:**
> there are a couple things (maybe a lot who knows) that cant be intalled when a certain package is installed

the best example i can think of.....if you try to install totem-xine while totem-gstreamer is installed, it will remove totem-gstreamer. so therefore just right there you cant install EVERYTHING in the repos.
I was thinking more of back when I wasn't sure which video driver to install so I tried installing all of them and it wouldn't let me.

---

