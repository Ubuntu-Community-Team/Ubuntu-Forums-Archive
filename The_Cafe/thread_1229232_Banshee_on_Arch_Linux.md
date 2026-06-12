---
title: "Banshee on Arch Linux?"
date: 2009-08-01
forum: The Cafe
---

### Post by Jimleko211 on 2009-08-01
I downloaded banshee using pacman, and it tells me that it downloaded and installed it correctly.  I try to launch it with the command "banshee", and it doesn't work.  I then try "banshee-1" and I get the following error message:
```

Unhandled Exception: System.Exception: Unable to open the session message bus.
--> System.ArgumentNullException: Argument cannot be null
parameter name: address
   at NDesk.DBus.Bus.Open (System.String address) [0x00000]
   at NDesk.DBus.get_Session() [0x00000]
   === End of inner exception stack trace ---
   at NDesk.DBus.get_Session () [0x00000]
   at Banshee.ServiceStack.DBusCennection.get_ApplicationInstanceAlreadyRunning() [0x00000]
   at Booter.Booter.Main () [0x00000]

```

I checked the Arch Wiki but I couldn't find an entry on Banshee...any help?

---

### Post by FuturePilot on 2009-08-01
Just a stab in the dark, but is dbus running?

---

### Post by Jimleko211 on 2009-08-01
> **FuturePilot said:**
> Just a stab in the dark, but is dbus running?
HAL is running, and the arch wiki says that dbus starts with HAL.

---

### Post by Jimleko211 on 2009-08-01
Solved the problem.  Thanks for making me look up the d-bus page!

---

### Post by kevdog on 2009-08-01
Um -- could you provide a better explanation please.

---

### Post by Jimleko211 on 2009-08-01
> **kevdog said:**
> Um -- could you provide a better explanation please.
The problem is solved, if that's what you meant.  If not, look at the final section of the D-Bus page on the Arch Wiki.  That's how I solved the problem.

---

