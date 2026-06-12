---
title: "Full Disc Encryption"
date: 2010-02-08
forum: Security
---

### Post by yester64 on 2010-02-08
I just discovered that Truecrypt does not offer on the fly encryption of a whole harddrive, since that is windows only (nooooooooooooo).
Now i wonder what my options are under linux if i want to encrypt the whole harddrive without reformating it.
Or am i out of luck with this issue? :???:

---

### Post by FuturePilot on 2010-02-08
On Linux there is no way to do it without reformatting. You'll have to reinstall with the Alternate installer disc.

---

### Post by yester64 on 2010-02-08
oh wow... that means at the time you install a new linux it has to be installed at the same time?
I have to check the alternate version and see how that works. I wonder why you can't do it like on windows.

Thanks for the info.

---

### Post by ushills on 2010-02-09
You can encrypt your /home and there are lots of guides to do this, this should be suitable as this will protect sensitive information.  You can do this when you create a user or new user and copy your /home across to the new encrypted home and it will be encrypted.

That's what I would do and no reinstall needed.

---

### Post by dogdo on 2010-02-09
Does anyone know if the official ubuntu cd will come with full disk encryption as a option soon?

---

### Post by mkvnmtr on 2010-02-09
The last several releases have asked if I want to encrypt so I guess it comes with full disk encryption now.

---

### Post by FuturePilot on 2010-02-09
> **mkvnmtr said:**
> The last several releases have asked if I want to encrypt so I guess it comes with full disk encryption now.

That will only encrypt your /home, not the whole disk.

---

### Post by ushills on 2010-02-09
tgere can be a significant performance hit with full disk encryption that is not as significant with just encrypted /home and /swap.  Is there a specific reason for full disk encryption.

---

