---
title: "AuFS read only branch as another read only branch"
date: 2014-02-16
forum: Server Platforms
---

### Post by robin10 on 2014-02-16
[COLOR=#333333][FONT=UbuntuRegular]Hello

My goal is to use an AuFS read only branch as another read only branch:
I've got a directory dir0, then I make :

```
mount -t aufs -o br=dir2=rw:dir0=ro none dir1
```

This gives me

```
- dir0
- dir1  #read only dir0
- dir2  #write layer of dir1
```
I now want to use dir1 this way:

```
mount -t aufs -o br=dir4=rw:dir1=ro none dir3
```

To get

```
- dir0
- dir1  #read only dir0
- dir2  #write layer of dir0
- dir3  #read only dir1 (dir1 + dir2)
- dir4  #write layer of dir3
```

I'm using ubuntu 12.04 and this should work according to aufs-tools man page:[INDENT]Any filesystem can be a branch, But some are not accepted such like sysfs, procfs and unionfs. If you specify such filesystems as an aufs branch, aufs will return an error saying it is unsupported.
[/INDENT]
But I got this error:```
[INDENT]mount: wrong fs type, bad option, bad superblock on none, missing codepage or helper program, or other error (for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount. helper program) In some cases useful info is found in syslog - try dmesg | tail or so
[/INDENT]

```and dmesg gives me```
[INDENT]aufs test_add:231:mount[3346]: unsupported filesystem, (aufs)
[/INDENT]

```Am I missing something here ? 
Regards, Robin[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]

---

### Post by robin10 on 2014-02-16
[COLOR=#333333][FONT=UbuntuRegular]Seems that it is currently not possible.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]However, Overlayfs does it very well and seems to be the union FS of choice in ubuntu and in the future 3.10 Linux kernel.[/FONT][/COLOR]

---

