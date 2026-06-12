---
title: "Enabling user_xattr in default LVM installation"
date: 2018-09-02
forum: Server Platforms
---

### Post by crognlie on 2018-09-02
Is it possible to enable user_xattr in logical volumes?  I've got a brand new 18.04.1 LTS server installation, all defaults through the LVM configuration during install.  I'm attempting to enable extended attributes in the filesystem.

Extended attributes currently not supported {tried as root just for completeness}:
```
$ sudo setfattr -n testattr -v blah tst
setfattr: tst: Operation not supported
```

Tried adding to root mount in fstab, no apparent help:
```
$ cat /etc/fstabUUID=0c688e8b-ade4-11e8-abab-0026b0e77b64 / ext4 defaults,user_xattr 0 0
UUID=0c688e8a-ade4-11e8-abab-0026b0e77b64 /boot ext4 defaults 0 0
UUID=8757-B065 /boot/efi vfat defaults 0 0
```

mtab, which would hopefully show if xattr got enabled? :
```
$ cat /etc/mtab | grep " \/ "
/dev/mapper/ubuntu--vg-ubuntu--lv / ext4 rw,relatime,data=ordered 0 0
```

---

### Post by TheFu on 2018-09-02
First, user_xattr is enabled by default on almost all file systems these days.  I think only ReiserFS doesn't. Ext4 does.
In the command, does the tst file/directory exist?

When I run 
```
$ sudo tune2fs -l /dev/mapper/ubuntu--vg-root
```

This is returned:
...
```
 Default mount options:    user_xattr acl
```

So it is enabled by default.

Checking the way you did doesn't work, at least not here..```

$ mount |grep root
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,noatime,nodiratime,discard,errors=remount-ro,data=ordered)
```

There's a section in the mount manpage just about ext4 options. I didn't see anything related there, but perhaps I missed something?

Let's see ....  
```
cd /tmp; touch tst
$ setfattr -n user.name1 -v val1 tst
$ getfattr -d tst
# file: tst
user.name1="val1"

```
Seems to work here.

---

### Post by crognlie on 2018-09-02
Thanks for the response, it pointed me to learning that the problem I thought I had wasn't actually the problem I had.
XATTR(7) says attributes have to start with security, system, trusted, or user, in the 'namespace.attribute' form.  Hence my problem:

```
$ setfattr -n userattr1 -v val1 tst
setfattr: tst: Operation not supported
$ setfattr -n user.attr1 -v val2 tst
$ getfattr -d tst
# file: tst
user.attr1="val2"[FONT=Verdana]
```[/FONT]

---

### Post by TheFu on 2018-09-02
Yep.  I hadn't used xattr before either, so this was 100% learning for me as well. Thanks for the question.
I did the google on the error, then read the man pages, then decided to google for example usage ... which solved it.  ;)

I didn't even have the attr package on my laptop before this question.  I can see all sorts of uses for this if location will include these attributes in the DB or at least if 'find' will allow them.  Sorta like having exif data with image files, but for all files on a system. Very cool, provided they are included in backups and restores and don't get lost moving across systems.  Hummmm.

---

