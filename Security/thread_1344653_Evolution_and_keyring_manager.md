---
title: "Evolution and keyring manager"
date: 2009-12-03
forum: Security
---

### Post by martinrandau on 2009-12-03
a) If you launch Evolution under the following circumstances:
1. Automatic login
2. Deny when asked to enter the keyring password the first time (for your wireless for example)

b) and then launch Evolution and deny when it asks you to enter your keyring password

c) then you will get a loop where Evolution first asks you to enter your keyring password and then asks you to manually enter the email account password.

The only way I could get out of it was to use force application quit and then quickly press the 'Force quit' button before the 'Enter keyring password' or 'Enter email account password' window came up.

**The reason is that the 'Enter keyring password' window is placed above all other windows (including the 'Force quit' window).**

It's not really a bug but it's annoying if you for example accidentally open Evolution and want to shut it down quick without entering your keyring password. 

There might have been some other circumstances present as well so it might not be repeatable.

I just thought I should mention it! :P

---

