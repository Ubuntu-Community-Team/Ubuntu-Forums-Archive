---
title: "Editing sudoers file ?"
date: 2010-01-03
forum: Security
---

### Post by Barriehie on 2010-01-03
So about 7 months ago I changed my sudo timeout but in the process was freaked out by VI and generated these files:
```

/etc # >ls ./.sud*
./.sudoers.tmp.swo  ./.sudoers.tmp.swp
/etc # >ls -l ./.sud*
-rw------- 1 root root 12288 2009-06-18 14:48 ./.sudoers.tmp.swo
-rw------- 1 root root 12288 2009-06-18 14:42 ./.sudoers.tmp.swp
/etc # >

```
Can they be deleted???

TIA,
Barrie

---

### Post by jediborger on 2010-01-03
Assuming sudo still works fine for you.

```
sudo rm ./.sudoers.tmp.sw*
```

If sudo is messed up so you can't run that, try switching to root.

```
su root
```

---

### Post by Barriehie on 2010-01-03
> **jediborger said:**
> Assuming sudo still works fine for you.

```
sudo rm ./.sudoers.tmp.sw*
```

If sudo is messed up so you can't run that, try switching to root.

```
su root
```

Thank you! sudo still works, I rebooted to make sure! :)

---

