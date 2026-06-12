---
title: "no hibernate with gnome-session-fallback in 12.04 (precise)"
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by James Paige on 2012-03-21
Up until yesterday I was using 11.04, and hibernate always worked well for me.

Last night I installed 12.04. I know it is not officially released yet, but I know it is getting close, so I figured I would try it.

I didn't like Unity, so I switched to gnome, and I didn't like gnome-shell so I switched to gnome-session-fallback. I hated that until I realized that I could alt-right-click to make my panels stop sucking, so now I am pretty happy with it.

The only problem I can't figure out is why hibernate support has vanished. Hibernate is no longer in the meny by shutdown (and for that matter, "restart" appears to be missing too)

I went to system settings, and into "Power", and there is an option to hibernate when the lid is closed (which I used in 11.04) but it is greyed out, and I cannot select it. Does anybody know what is up with that?

My current workaround is to install the powermanagement-interface package and run
```
sudo pm-hibernate
```

But I was wondering if anybody knew a more elegant workaround for this problem?

---

### Post by wildmanne39 on 2012-03-21
Hi, I am going to ask a mod to move this to development since the release is not out yet and all questions with 12.04 should be posted there.
Thanks

---

### Post by overdrank on 2012-03-21
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by James Paige on 2012-03-21
Ah! Thank you for moving the thread :)

---

### Post by Whoopie on 2012-03-22
You have to comment out the following lines in /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla:

```

[Disable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=no

```

Do a restart or logout/login after modifying the file.

---

### Post by James Paige on 2012-03-22
Awesome! Thanks, Whoopie! I wasn't sure what comment char to use, so instead I just changed ResultActive=yes and it worked

```

[Disable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

```

The hibernate option is no longer greyed out in the power config screen.

Any idea why it defaults to disabled? That seems like a pretty strange default (or maybe I am just spoiled by having hardware that has been hibernating reliably for years ;)

---

### Post by Whoopie on 2012-03-23
I read somewhere that hibernate is broken on too many laptops. That's why the devs disabled it.

---

