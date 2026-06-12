---
title: "Guest Account in Jaunty?"
date: 2009-04-28
forum: Security
---

### Post by stmurray on 2009-04-28
I just upgraded my Desktop to Jaunty and suddenly I see a guest user ID that is logged in from tty9 (Even though it looks as if the authentication for the account is impossible because the password hash is "*"), has a shell (bash) and owns many processes running on the system.  Does anyone know what created this account and how it works?  Is it creating any additional security risks?  (It may have been created before the upgrade, but I have never seen it before and a quick search of the forums and official documentation came up empty)

Thanks!!

---

### Post by cariboo on 2009-04-28
Did you select the Guest account, using switch user? The guest account was added in Intrepid.

---

### Post by stmurray on 2009-04-29
That's what I did.  I kind of wish this was disabled by default on installation.   For those looking to explore this further here is the link ->  [https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount]("https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount")

---

