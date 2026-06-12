---
title: "Safe to change root username"
date: 2009-09-08
forum: Server Platforms
---

### Post by Cardale on 2009-09-08
Is it safe to change root username under ubuntu?  For added security?

```
sudo usermod -l <new name> root 
```

---

### Post by gombadi on 2009-09-08
Never done it, would not recommend it and make sure you have full backups before you try it. Let us know how you get on.

Lets avoid the whole security by obscurity discussion :-)

---

### Post by Cardale on 2009-09-08
It's always nice being a ginny pig hahah....

---

### Post by ainsworth_t on 2009-09-09
Since there are a lot of system and application configuration files, and processes owned by root (just run *ps -ef | grep root* and you'll see what I mean), I don't think it would be a good idea to change the root user name. Either make an extremely strong password for root, or disable root logins.

---

### Post by grantemsley on 2009-09-09
My guess it that it will severely break things.  Possibly to the point where the system wont boot.

File permissions will be fine, they are actually stored by uid.  But I'll bet there are plenty of startup scripts and such that reference the root account by name.

By default, you can't log in as root anyways.  You can only get access to its account through sudo.

---

### Post by Iowan on 2009-09-09
I've done it on other systems - not renaming root, exactly, but making an alias user and disabling root login (something Ubuntu does out-of-the-box).

---

### Post by cariboo on 2009-09-09
If you do have a root password, locking it by using:

```
sudo passwd -l root
```

see man passwd, will go a long way in securing your system.

---

### Post by dcstar on 2009-09-10
> **Iowan said:**
> I've done it on other systems - not renaming root, exactly, but making an alias user and disabling root login (something Ubuntu does out-of-the-box).

Which is probably the most effective way of protecting the UID 0 account.

Even if you rename root people who have any level of access could probably find the new name easily by looking at /etc/passwd or at the owner name of any system file you know has to be owned by root - so essentially it is pointless if you use the security step outlined above.

Unlike Windows you do not have to have the "Administrator" account (which is the only account on that O/S that cannot be disabled by failed login attempts!) available for login to have a usable system.

---

