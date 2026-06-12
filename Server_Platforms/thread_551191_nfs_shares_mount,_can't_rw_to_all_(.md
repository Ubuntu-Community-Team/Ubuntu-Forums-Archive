---
title: "nfs shares mount, can't rw to all :("
date: 2007-09-14
forum: Server Platforms
---

### Post by lunaz on 2007-09-14
my user id #s are the same on the server & the clients as far as i can tell. i can mount the shares but the only one i can rw to as luna is /music/. i made a file in luna_bak on the server and the client can't see it.

i thought if i had luna in group luna and bachmanswarbler in group bachmanswarbler on the server, then both users would be able to rw to their shared folders from the clients.

searched around, still not sure what i'm missing.

list of permissions on the server: badassnes_bak isn't shared.
```

luna@oldpos:/media/usbdisk$ ls -la
total 24
drwxr-xr-x  6 root            root            4096 2007-09-13 22:56 .
drwxr-xr-x  6 root            root            4096 2007-09-12 17:49 ..
drwxrwx---  2 bachmanswarbler bachmanswarbler 4096 2007-09-09 16:21 bachmanswarbler_bak
drwxrwx--- 11 root            root            4096 2007-06-18 18:43 badassness_bak
drwxrwx---  2 luna            luna            4096 2007-09-14 18:55 luna_bak
drwxrwx--- 48 luna            music           4096 2007-09-14 18:19 music
luna@oldpos:/media/usbdisk$ 

```

/etc/exports
```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/media/usbdisk/music 192.168.1.1/24(rw,sync)
/media/usbdisk/bachmanswarbler_bak 192.168.1.1/24(rw,sync)
/media/usbdisk/luna_bak 192.168.1.1/24(rw,sync)

```

/etc/fstab on desktop
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=2311721d-c453-4413-af55-ebf78580cc05 /               ext3    defaults,erro$
# /dev/sda1
UUID=34803D5A803D23B0 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/sda4
UUID=3640-45B9  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=9a7a537d-e79c-4f9f-8f43-78ce632357de none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
192.168.1.100:/media/usbdisk/music/ /mnt/music/ nfs rw,hard,intr 0 0

```

---

### Post by peabody on 2007-09-14
I'm no nfs expert but have you checked to make sure the uuids and gids are the same on both the clientside and the server and not just the names?  That's what's truly relevant.

---

### Post by lunaz on 2007-09-14
edit: found the commands...

for the client:
```

luna@badassness:~$ id luna
uid=1000(luna) gid=1000(luna) groups=1000(luna),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin)
luna@badassness:~$ id bachmanswarbler
uid=1001(bachmanswarbler) gid=1001(bachmanswarbler) groups=1001(bachmanswarbler),24(cdrom),25(floppy),29(audio),46(plugdev)
luna@badassness:~$

```

for the server:
```

luna@oldpos:~$ id luna
uid=1000(luna) gid=1000(luna) groups=1000(luna),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),108(lpadmin),109(scanner),110(admin),1001(music)
luna@oldpos:~$ id bachmanswarbler
uid=1001(bachmanswarbler) gid=100(users) groups=100(users),24(cdrom),25(floppy),29(audio),46(plugdev),1001(music),1002(bachmanswarbler)
luna@oldpos:~$ 

```

the only difference i see is that bach is gid 100. would changing it to 1001 help?
i haven't tested stuff with her name yet, i'm still having issues with mine.. :(

---

### Post by peabody on 2007-09-14
> **lunaz said:**
> edit: found the commands...


the only difference i see is that bach is gid 100. would changing it to 1001 help?
i haven't tested stuff with her name yet, i'm still having issues with mine.. :(

Hmm, well, you could try changing it, but if your uids and gids are the same I can't see why you would be having trouble...hmm...

---

### Post by lunaz on 2007-09-15
lol holy crap!!
it'd work alot better if i put luna_bak & bachmanswarbler_bak in my fstab file. :P

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=2311721d-c453-4413-af55-ebf78580cc05 /               ext3    defaults,erro$
# /dev/sda1
UUID=34803D5A803D23B0 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/sda4
UUID=3640-45B9  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=9a7a537d-e79c-4f9f-8f43-78ce632357de none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
192.168.1.100:/media/usbdisk/music/ /mnt/music/ nfs rw,hard,intr 0 0
192.168.1.100:/media/usbdisk/luna_bak/ /mnt/luna_bak/ nfs rw,hard,intr 0 0
192.168.1.100:/media/usbdisk/bachmanswarbler_bak /mnt/bachmanswarbler_bak/ nfs rw,hard,intr 0 0

```

---

