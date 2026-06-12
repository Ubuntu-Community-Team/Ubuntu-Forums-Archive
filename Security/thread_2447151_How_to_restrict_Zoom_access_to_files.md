---
title: "How to restrict Zoom access to files?"
date: 2020-07-13
forum: Security
---

### Post by ari.maidana on 2020-07-13
Hello, I'm using the zoom-client snap. I would like to prevent Zoom being able to access my files, so I disconnected the "home" interface with the following command:

```
snap disconnect zoom-client:desktop :desktop
```

It worked, but the problem was that when I opened Zoom all the text in the UI was missing (does Zoom take the fonts it uses from outside its container?). Does anyone know if it's possible to keep Zoom disconnected from the desktop, so it can't see the files, and have the UI text work correctly at the same time.

Thanks in advance for any help.

---

### Post by TheFu on 2020-07-13
Why not just create a zoom userid then login to that userid for zoom stuff?  That new userid running Zoom wouldn't have access to the files of the other account, unless you go out of the way to allow it.

Always remember, Unix/Linux is a multi-user OS, regardless of how we use it.

If you need access to the files for the other account while in a zoom session, open a terminal, **su - ari** and all the files will be there, available in that terminal. You can launch GUI apps from that terminal too with a little X11 security update to allow it.  I don't use that specific method, but I do run GUI commands on other systems on my LAN and have the window for each displayed in a different system.  Right now, this web browser is running on "regulus", but being displayed on "hadar".  I'm sitting behind hadar.  Those are hostnames.  I run my thick email program the same way - over the LAN.  The account on the other system might have the same name and same HOME directory thanks to NFS, but it is not the same account.  

BTW, snaps don't work with NFS, so when I want to run a snap program, I have to do something else.

---

### Post by EuclideanCoffee on 2020-07-13
You generate an apparmor profile for it.

Generally speaking. I don't use snaps. :)

---

### Post by alexmurray on 2020-07-13
You have disconnected the desktop interface - this is used for integration with the desktop theme etc - so it is no surprise that Zoom then cannot use the correct fonts etc.

Instead you need to disconnect home via:

```

snap disconnect zoom-client:home :home

```

(and so you should reconnect the desktop interface too):

```

snap connect zoom-client:desktop :desktop

```

---

