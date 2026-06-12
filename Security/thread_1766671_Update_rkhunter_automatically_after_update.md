---
title: "Update rkhunter automatically after update"
date: 2011-05-24
forum: Security
---

### Post by ianc1 on 2011-05-24
Following a recent post by leoquant in another rkhunter thread, [http://ubuntuforums.org/showthread.php?t=1762615&highlight=rkhunter](http://ubuntuforums.org/showthread.php?t=1762615&highlight=rkhunter), I was drawn to the Ubuntu Community rkhunter page, [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter).

This outlines how to run **rkhunter --propupd**, automatically after software updates, by putting
```

DPkg::Post-Invoke { "if [ -x /usr/bin/rkhunter ]; then /usr/bin/rkhunter --propupd; fi"; };
```in */etc/apt/apt.conf.d/90rkhunter*.

I appear to already have this file with similar contents:
```

// Makes sure that rkhunter file properties database is updated after each remove or install only if hashes test is enabled
DPkg::Post-Invoke { "if [ -x /usr/bin/rkhunter ] && ( grep -qiE '^APT_AUTOGEN=.?(true|yes)' /etc/default/rkhunter && ! grep -qE '^DISABLE_TESTS=.*(hashes.*attributes|attributes.*hashes|properties)' /etc/rkhunter.conf | grep -qE '^ENABLE_TESTS=.*(hashes|attributes|properties)' /etc/rkhunter.conf ); then /usr/bin/rkhunter --propupd --nolog; fi" }
```Could someone please tell me why this doesn't work.  For example a recent update to binutils changed the files /usr/bin/size and /usr/bin/strings and today rkhunter should these as warnings.  So clearly no --propupd had been done.

Any ideas would be much appreciated.

Thanks

---

### Post by Soul-Sing on 2011-05-25
I'll take a look  at it with a small testgroup.

---

### Post by douglasbagnall on 2011-07-13
> **ianc1 said:**
> 
I appear to already have this file with similar contents:
```

// Makes sure that rkhunter file properties database is updated after each remove or install only if hashes test is enabled
DPkg::Post-Invoke { "if [ -x /usr/bin/rkhunter ] && ( grep -qiE '^APT_AUTOGEN=.?(true|yes)' /etc/default/rkhunter && ! grep -qE '^DISABLE_TESTS=.*(hashes.*attributes|attributes.*hashes|properties)' /etc/rkhunter.conf | grep -qE '^ENABLE_TESTS=.*(hashes|attributes|properties)' /etc/rkhunter.conf ); then /usr/bin/rkhunter --propupd --nolog; fi" }
```Could someone please tell me why this doesn't work. 

This part:
```
 grep -qiE '^APT_AUTOGEN=.?(true|yes)' /etc/default/rkhunter 
```

is checking whether /etc/default/rkhunter contains a line like ```
APT_AUTOGEN="yes"
```By default it doesn't.

---

### Post by ianc1 on 2011-07-13
Ah well spotted, thanks.  I should look at the actual text a bit more in future.

Has anyone ever tried adding that line to */etc/apt/apt.conf.d/90rkhunter* and changing the /etc/default/rkhunter file accordingly?

Are there any cons to doing this?

Thanks

---

### Post by unspawn on 2011-07-13
> **ianc1 said:**
> Are there any cons to doing this?
Using this method as a panacea to get rid of those "pesky warnings" deprives you of the opportunity to verify changes when they occur. But let's try a simple analogy: let's say you crashed your car and it got structurally damaged. Would just painting it over a few times restore structural integrity of the car or not?..

* Since 1.3.4 RKH allows you to add a single or list of file, directory or package names to the "--propupd" switch. This will limit updating the rkhunter.dat file to only the given items.
** Also see rkhunter.conf for the descriptions wrt WARN_ON_OS_CHANGE and UPDT_ON_OS_CHANGE.

---

