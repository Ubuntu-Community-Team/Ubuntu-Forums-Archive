---
title: "Xscreensaver unlocks with any string not just password"
date: 2007-01-11
forum: Server Platforms
---

### Post by Seirios on 2007-01-11
Hi.

Mmm, I don't know if this is the right forum to post this, but I have the following security-related issue:

When i put xscreensaver 5.01 to lock my screen, it works all fine. But when it asks for the password, i can just type any string in the Password field, and it unlocks.

I know this is an xscreensaver issue, but I use Ubuntu and it's a security issue, so I'm posting it here.

I've compiled it (xscreensaver) with PAM support and KRB5 support.

here is xscreensaver -verbose output:

```
xscreensaver 5.01, copyright (c) 1991-2006 by Jamie Zawinski <jwz@jwz.org>.
xscreensaver: initial effective uid/gid was root/sirius (0/1000).
xscreensaver: changed uid/gid to sirius/sirius (1000/1000).
xscreensaver: in process 20456.
libGL warning: 3D driver claims to not support visual 0x4b
xscreensaver: 23:06:53: 0: xscreensaver-gl-helper: GL visual is 0x23 (default).
xscreensaver: 23:06:53: initialization of Kerberos passwords failed.
xscreensaver: 23:06:53: running on display ":0.0" (1 screen).
xscreensaver: 23:06:53: vendor is The X.Org Foundation, 70101000.
xscreensaver: 23:06:53: useful extensions:
xscreensaver: 23:06:53:   MIT Screen-Saver  <-- not supported at compile time!
xscreensaver: 23:06:53:   Shared Memory
xscreensaver: 23:06:53:   Power Management
xscreensaver: 23:06:53:   GLX
xscreensaver: 23:06:53:   XF86 Video-Mode
xscreensaver: 23:06:53:   Resize-and-Rotate
xscreensaver: 23:06:53: screen 0 non-colormapped depths: 24.
xscreensaver: 23:06:53: selecting RANDR events
xscreensaver: 23:06:53: 0: visual 0x23 (TrueColor,   depth: 24, cmap: default)
xscreensaver: 23:06:53: 0: saver window is 0x2000001.
xscreensaver: 23:06:53: selecting events on extant windows... done.
xscreensaver: 23:06:53: awaiting idleness.
xscreensaver: 23:07:30: LOCK ClientMessage received; activating and locking.
xscreensaver: 23:07:30: 0: locked mode switching.
xscreensaver: 23:07:30: blanking screen at Wed Jan 10 23:07:30 2007.
xscreensaver: 23:07:30: 0: grabbing keyboard on 0x4d... GrabSuccess.
xscreensaver: 23:07:30: 0: grabbing mouse on 0x4d... GrabSuccess.
xscreensaver: 23:07:30: fading...
xscreensaver: 23:07:31: fading done.
xscreensaver: 23:07:31: 0: visual 0x23 (TrueColor,   depth: 24, cmap: 256)
xscreensaver: 23:07:31: 0: saver window is 0x2000006.
xscreensaver: 23:07:31: 0: destroyed old saver window 0x2000001.
xscreensaver: 23:07:31: 0: spawning "glmatrix -root -density 29 -delay 30147" in pid 20553.
libGL warning: 3D driver claims to not support visual 0x4b
xscreensaver: 23:07:35: 0: suspending pid 20553 (glmatrix)
xscreensaver: 23:07:35: prompting for password.
xscreensaver: 23:07:35: 0: creating password dialog.
xscreensaver: 23:07:35: 0: mouse is at 135,225.
xscreensaver: 23:07:35: grabbing server...
xscreensaver: 23:07:35: 0: ungrabbing mouse (was 0x4d).
xscreensaver: 23:07:35: 0: grabbing mouse on 0x200000e... GrabSuccess.
xscreensaver: 23:07:35: ungrabbing server.
xscreensaver: 23:07:35: 0: child pid 0553 (glmatrix) stopped with signal 19.
xscreensaver: 23:07:37: pam_start ("xscreensaver", "sirius", ...) ==> 0 (Success)
xscreensaver: 23:07:37:   pam_set_item (p, PAM_TTY, ":0.0") ==> 0 (Success)
xscreensaver: 23:07:37:   pam_authenticate (...) ==> 0 (Success)
xscreensaver: 23:07:37:   pam_acct_mgmt (...) ==> 9 (Authentication service cannot retrieve authentication info.)
xscreensaver: 23:07:37:   pam_setcred (...) ==> 0 (Success)
xscreensaver: 23:07:37: pam_end (...) ==> 0 (Success)
xscreensaver: 23:07:37: authentication via PAM passwords succeeded.
xscreensaver: 23:07:37: password correct.
xscreensaver: 23:07:37: grabbing server...
xscreensaver: 23:07:37: 0: ungrabbing mouse (was 0x200000e).
xscreensaver: 23:07:37: 0: grabbing mouse on 0x4d... GrabSuccess.
xscreensaver: 23:07:37: ungrabbing server.
xscreensaver: 23:07:37: 0: moving mouse back to 135,225.
xscreensaver: 23:07:37: 0: resuming pid 20553 (glmatrix)
xscreensaver: 23:07:37: unblanking screen at Wed Jan 10 23:07:37 2007.
xscreensaver: 23:07:37: 0: killing pid 20553 (glmatrix)
xscreensaver: 23:07:37: 0: ungrabbing mouse (was 0x4d).
xscreensaver: 23:07:37: 0: ungrabbing keyboard (was 0x4d).
xscreensaver: 23:07:37: 0: unlocked mode switching.
xscreensaver: 23:07:37: starting de-race timer (10 seconds.)
xscreensaver: 23:07:37: awaiting idleness.
xscreensaver: 23:07:37: 0: child pid 0553 (glmatrix) terminated with signal 15.
xscreensaver: 23:07:47: de-race completed.

```

i just pressed the escape key at password field entry and it unlocked

by the way, if it helps, i use Ubuntu 6.10 in a PPC G4 machine.

hope somebody can help me or tell me where to find a solution

thanks in advance

Sirius.

---

### Post by scrooge_74 on 2007-01-11
you should make a formal bug report

---

