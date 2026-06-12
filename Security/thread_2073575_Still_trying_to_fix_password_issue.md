---
title: "Still trying to fix password issue"
date: 2012-10-19
forum: Security
---

### Post by CampLife on 2012-10-19
I changed my password, and was unable to log on.
I went into root area, and changed password there.
When logging on, it kicks me back to main screen.
I used ecryptfs-rewrap-passphrase /home/.ecryptfs/$USER/.ecryptfs/wrapped-passphrase, 
It asked for old wrapping passphrase, which I assumed was my initial password.
It asked for new wrapping passphrase (twice).
I got an error: Unwrapping passphrase failed (-5).
Info: Check the system log for more inforamtion from libecryptfs.
How do I do that?  
Thanks,

---

### Post by OpSecShellshock on 2012-10-20
My first thought would be to do this:

```
grep libecryptfs /var/log/syslog
```

and see if anything comes up.

The passphrase that it's asking for may actually be the long string of characters that comes up when initially setting up an encrypted disk, the one it tells you to copy down the first time you run it. It's been a while since the last time I set up an encrypted home though.

---

