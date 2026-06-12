---
title: "Setting locale failed"
date: 2008-09-30
forum: Server Platforms
---

### Post by spikeh on 2008-09-30
Fresh Ubuntu Server 8.04 install on an OVH server. Perl and subversion complains about locale. This is the error message:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

apt-get install locales tells me I already have the latest version.

dpkg-reconfigure locales throws some additional errors:

```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

Here's the output from "locale"
```
root@xxxxxx:~# locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=
```

/etc/locale.gen does not exist. Could this be the source of the problem?

---

### Post by Wardazo on 2008-10-28
Hi

Just contracted a server off OVH (ubuntu 8.04 English) and have encountered exactly the same problem as soon as I ran apt-get upgrade.

Did you or anyone else find a solution?

Thanks

---

### Post by Wardazo on 2008-10-29
Just in case anyone else has this problem

Solution:

```
apt-get install language-pack-en
```

---

### Post by jimmyxx on 2008-11-23
> **Wardazo said:**
> Just in case anyone else has this problem

Solution:

```
apt-get install language-pack-en
```



Thanks Wardazo - fixed it for me :)

---

