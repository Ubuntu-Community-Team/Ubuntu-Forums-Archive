---
title: "sbnc: wrong password"
date: 2011-07-08
forum: Server Platforms
---

### Post by cong06 on 2011-07-08
I'm trying to set up and configure sbnc, for ubuntu.
After
```
sudo apt-get install sbnc
```
I set the user to "isaac" and the password to "test"
The only configuration I did, is to make sure that sbnc was starting (/etc/default/sbnc).

Then I opened up irssi, and typed:
```

/server 127.0.0.1 9000 isaac:test

```

However, when I run this, I get the error:
```

20:41 !shroudbnc.info *** shroudBNC 1.2 $Revision: 1080 $ - Copyright © 
          2005-2007 Gunnar Beutner
20:41 !shroudbnc.info *** Doing reverse DNS lookup on 127.0.0.1...
20:41 !shroudbnc.info *** Reverse DNS reply received (localhost).
20:41 !shroudbnc.info *** Doing forward DNS lookup...
20:41 !shroudbnc.info *** Forward DNS reply received. (localhost)
20:41 !shroudbnc.info *** Unknown user or wrong password.
20:41 -!- Irssi: Connection lost to 127.0.0.1

```
And in the file: /var/log/sbnc/sbnc.log
There is an entry:
```

Fri Jul  8 20:38:26 2011: Wrong password for user isaac (from localhost[127.0.0.1])

```

What's going on?

---

