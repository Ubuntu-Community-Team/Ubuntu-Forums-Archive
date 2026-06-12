---
title: "how to add security exception in thunderbird?"
date: 2010-05-27
forum: Security
---

### Post by cnkbrown on 2010-05-27
My company uses self signed certificates, and whenever i access the global address book, every time i start typing an address, TB throws up a security warning dialog.  There is no way from that dialog to accept a security exception.

It's getting really tedious.

I tried editing the address book properties to turn off SSL.  This makes the warning go away, but then, every time i start typing an address, TB asks me for my password.   This dialog has a check to store the password, which i always check. Yet, TB keeps asking.

How do i make this stop?

---

### Post by Agent ME on 2010-05-27
Edit -> Preferences -> Advanced -> Certificates -> View Certificates -> Import

I think this may help you.

---

### Post by cnkbrown on 2010-05-28
I was able to download the certificate and import in that dialog, BUT the TB Address Book still throws the dialog.  Apparently, it doesn't check the exceptions list.

Also, when not in SSL mode, it still asks for a password.  Even though, I looked at stored passwords, and the password for that service and port is clearly stored properly.

---

