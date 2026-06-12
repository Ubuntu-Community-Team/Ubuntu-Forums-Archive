---
title: "Login After Suspend/Resume"
date: 2010-02-18
forum: Security
---

### Post by slithymonster on 2010-02-18
I want to require a login after the system resumes from sleep (S3).  So when you open the lid, for instance, the system should require you to enter your password.

That way, if the netbook is stolen, they won't get access to all your info.

Is this possible?

---

### Post by snowpine on 2010-02-18
Welcome to the forums!

System->Preferences->Screensaver
Check the "Lock screen while computer is idle" box.

Please understand however that a screensaver password will not protect your private data if your netbook is stolen. The thief could easily boot into Recovery Mode (or boot with an Ubuntu Live CD) and read all your files. The only solution is to encrypt the data on your hard drive (I think this is an easy option in the current version of the Ubuntu installer).

---

### Post by wojox on 2010-02-18
Go into your Screensaver settings and check Activate and Lock.

---

### Post by wojox on 2010-02-18
> **snowpine said:**
> The thief could easily boot into Recovery Mode (or boot with an Ubuntu Live CD) and read all your files. The only solution is to encrypt the data on your hard drive (I think this is an easy option in the current version of the Ubuntu installer).

Yes very easy. Like snowpine said you should encrypt your home directory.

---

### Post by cariboo on 2010-02-18
On my netbook with 9.10 and the netbook extensions, the screen is locked by default when ever you come out of hibernation.

---

