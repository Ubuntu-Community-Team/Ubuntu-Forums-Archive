---
title: "Security Softeare"
date: 2010-04-03
forum: Security
---

### Post by sthrnpagan on 2010-04-03
Is there a program that allows me to password lock a single file or folder?

---

### Post by FuturePilot on 2010-04-03
Look into into GPG or Ecryptfs.

---

### Post by rookcifer on 2010-04-03
> **sthrnpagan said:**
> Is there a program that allows me to password lock a single file or folder?

Just change the permissions on the file or folder so that only your user (or root) can view it.  any other user that logs in will be forbidden automatically.  However, this will not be much of a deterrent to someone with physical access to your machine.  Therefore, as the guy above said, the best bet is encryption.

---

### Post by HermanAB on 2010-04-04
And of course if your threat is your little kid sister, then you can simply use Zip with a passsword, which will keep her at bay till she is about 12...

---

### Post by sxmaxchine on 2010-04-04
encrypt a folder for best protection or just put it in a protected folder i put them in the root folder and access it by using terminal sudo nautilus then going to the folder

---

### Post by bodhi.zazen on 2010-04-04
> **sthrnpagan said:**
> Is there a program that allows me to password lock a single file or folder?

You do not need this.

Every user on the system should have a unique account , and so use linux permissions to restrict access.

If you need to restrict access from root or somebody with physical access, then you indeed need to look at encryption.

---

