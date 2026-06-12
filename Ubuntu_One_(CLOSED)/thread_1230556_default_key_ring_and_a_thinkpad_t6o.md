---
title: "default key ring and a thinkpad t6o"
date: 2009-08-03
forum: Ubuntu One (CLOSED)
---

### Post by martin saint martin on 2009-08-03
one desktop and one laptop, both running ubuntu one client.  the desktop doesn't tell/ask me to grant ubuntu one access to the default keyring, but on my laptop i'll get this message.  i'm not a fan of this message, so how could i get it to stop asking/telling me about it and just grant ubuntu one privileges to do what it's suppose to do?  i don't have auto log-on on, on both the desktop and laptop.  on my laptop i do use the fingerprint reader to enter my password, could this be the culprit?

---

### Post by martin saint martin on 2009-08-04
anybody out there?

---

### Post by cariboo on 2009-08-04
There's lots of us out here, but so far no one has run into your particular problem, have you tried disabling your fingerprint reader to see if the problem persists?, If you still have a problem, go to the web interface and report a bug.

---

### Post by James Henstridge on 2009-08-04
Could you be a bit more specific about the problem you're seeing?

If the dialog is asking you to grant permission to access to "UbuntuOne token for https://ubuntuone.com" (or something like that), there should be an "always allow" button that will clear up the problem.  Clicking that button gives the client permission to read the token in the future.  It doesn't give the client access to any of your other passwords.

If you are getting a dialog asking you to unlock the default keyring and asking for a password, it is possible that you have a keyring called "default" that was created with an old version of Ubuntu.  With current Ubuntu releases, passwords get stored in a keyring called "login" that is automatically unlocked when you log in.

If you still have the old "default" keyring on your system, some password lookup operations may try to open leading to the password prompt.  If you don't have anything useful in this keyring, it is probably best to just delete it.  You should be able to do this from the "Passwords" tab of the "Passwords and Encryption Keys" application (found under accessories).  Right click on "Passwords: default" and select delete to remove it.  You might want to expand it first to see what is held in the keyring before deleting though.

---

