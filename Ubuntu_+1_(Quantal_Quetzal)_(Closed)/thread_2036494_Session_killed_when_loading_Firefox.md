---
title: "Session killed when loading Firefox"
date: 2012-08-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by dino99 on 2012-08-02
Since the latest gcc 4.7.1-6 installation today, the session is killed by loading Firefox here on i386.
But nothing logged to know what happened :confused:

Other browser like Midori does not have that issue.

---

### Post by jfernyhough on 2012-08-02
I take it you've tried launching Firefox in safe mode? (e.g. $ firefox -safe-mode )

Maybe the hardware acceleration feature? Is it the same for Aurora/Nightly?

---

### Post by dino99 on 2012-08-02
safe mode also kill the session  ](*,)](*,)

have not installed the non genuine FF yet.

---

### Post by paul_in_london on 2012-08-02
> **dino99 said:**
> Since the latest gcc 4.7.1-6 installation today, the session is killed by loading Firefox here on i386.
But nothing logged to know what happened :confused:

Other browser like Midori does not have that issue.

+1 (64 bit, gnome-classic). Was seeing this last night. FF nightly build (and other versions of FF) dump me back to the login screen and I didn't find anything in the logs either. Didn't get round to trying safe mode. Are you using xorg-edgers?

Will check my gcc version when I get home, but for me this problem only started after the upgrade to Xserver_1.13. Midori/Chrome/Chromium/Iron all worked ok though. :confused:

---

### Post by dino99 on 2012-08-02
> **paul_in_london said:**
> +1 (64 bit, gnome-classic). Was seeing this last night. FF nightly build (and other versions of FF) dump me back to the login screen and I didn't find anything in the logs either. Didn't get round to trying safe mode. Are you using xorg-edgers?

Will check my gcc version when I get home, but for me this problem only started after the upgrade to Xserver_1.13. Midori/Chrome/Chromium/Iron all worked ok though. :confused:

Same here : gnome-classic but i386, with edgers xorg (maybe its the faulty reason ?)

---

