---
title: "Problem with kernel modules, mount of cloud drive fails with every protocol"
date: 2018-11-24
forum: Server Platforms
---

### Post by fidoro on 2018-11-24
Hello community,

this is a problem that hunts me since a few months now. I can't get it to work.

[B]What I try to achieve
[/B]I want to mount a Strato HiDrive (cloud drive of 1TB) on my Ubuntu virtual server to have my nextcloud file server set it's data directory into the mount.
I want all the data to be stored into the HiDrive as soon as it is created, no active syncing solution or something.
I already managed it once, but I can't remember all the hundret things that I had to do to make it work.
The file transfer protocol shall be not transferring in clear text and shall be as fast as possible.
Since the HiDrive offers some protocols I chose to work with cifs (preferred) or davfs.

**What my problem is**
I am fairly skilled with Linux servers, but I already have problems with mounting the drive. Others in the internet seem to have the same problem, only their solutions don't work for me.

Lets say I try to mount the drive using cifs, the following happens:
(Usernames, passwords and hostnames are censored. Important error messages are bold, the others weren't there before I tried to fix it by installing fuse an stuff.)
```

root@<HOST>:~# sudo mount -t cifs -o username=<USERNAME> //cifs.hidrive.strato.com/users/<USERNAME> /kezlynDrive
Password for <USERNAME>@//cifs.hidrive.strato.com/users/<USERNAME>:  ********
[B]mount error: cifs filesystem not supported by the system
mount error(19): No such device[/B]
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

When I try to do the same with davfs (credentials are in a external file, system finds them by itself):
```

root@<HOST>:~# sudo mount -t davfs -o defaults,rw,nosuid,nodev,_netdev,auto https://webdav.hidrive.strato.com/users/<USERNAME> /kezlynDrive
/sbin/mount.davfs: lade das Kernel_Modul fuse
**modprobe: ERROR: ../libkmod/libkmod.c:514 lookup_builtin_file() could not open builtin file '/lib/modules/4.15.0/modules.builtin.bin'**
modprobe: FATAL: Module fuse not found in directory /lib/modules/4.15.0
/sbin/mount.davfs: das Laden des Kernel-Moduls fuse schlug fehl
/sbin/mount.davfs: warte auf des Einrichten von /dev/fuse
/sbin/mount.davfs: kann die fuse-Gerätedatei nicht öffnen
/sbin/mount.davfs: ich versuche es mit dem Kernel-Dateisystem coda
/sbin/mount.davfs: keine freie coda-Gerätedatei gefunden

```
[LIST]
[*]The "modules.builtin.file" is there by default and is readable for everyone.
[/LIST]

Same when I try to use the "/etc/fstab" file:
```
https://webdav.hidrive.strato.com/users/<USERNAME> /kezlynDrive davfs defaults,rw,nosuid,nodev,_netdev,auto,conf=/root/.credentials 0 0
```
```

root@<HOST>:~# sudo mount -a
mount: /dev/pts: none already mounted on /sys.
/sbin/mount.davfs: lade das Kernel_Modul fuse
**modprobe: ERROR: ../libkmod/libkmod.c:514 lookup_builtin_file() could not open builtin file '/lib/modules/4.15.0/modules.builtin.bin'**
modprobe: FATAL: Module fuse not found in directory /lib/modules/4.15.0
/sbin/mount.davfs: das Laden des Kernel-Moduls fuse schlug fehl
/sbin/mount.davfs: warte auf des Einrichten von /dev/fuse
/sbin/mount.davfs: kann die fuse-Gerätedatei nicht öffnen
/sbin/mount.davfs: ich versuche es mit dem Kernel-Dateisystem coda
/sbin/mount.davfs: keine freie coda-Gerätedatei gefunden

```

**What I tried already**
[LIST]
[*]Re-installing the system.
[*]Installing a newer ubuntu server (from 14.xx to 18.01).
[*]Installing "cifs-utils" / purging and reinstalling it.
[*]Rebooting (a hundret times already)
[*]Module versions and kernel version are matching (4.15.0)!
[*]Driver files are there! (Pastebin of driver file locations: [https://pastebin.com/Rb06ecGW](https://pastebin.com/Rb06ecGW))
[*]There was no recent kernel update that could have caused non-matching version numbers.
[/LIST]
To be honest, I have the feeling that somehow the system doesn't recognise the modules, even thought they are there.
Is it possible that it has something to do with the myriad of folders that are in my "/lib/modules/4.15.00/" folder? Maybe the referenced links aren't as obvious to every program?
I would rather not have to build my own modules, that's kinda complicated.

I don't know and that's what I am here for, I hope someone can help me!
I can give you all the console outputs and information about the server that you need.

Thanks, Fidoro.

---

### Post by Doug S on 2018-11-24
Disclaimer: I know almost nothing about this stuff.

Your code mentions looking for '/lib/modules/4.15.0/modules.builtin.bin' and not finding it. However, and I have looked on 4 Ubuntu computers, some servers, some desktops, and they never have a 4.15.0 modules directory. There is always more at that level.

Example (the best one):
```
doug@cyd-hp2:~$[COLOR="#FF0000"] locate modules.builtin.bin[/COLOR]
/lib/modules/4.13.0-31-generic/modules.builtin.bin
/lib/modules/4.15.0-29-generic/modules.builtin.bin
/lib/modules/4.15.0-30-generic/modules.builtin.bin
/lib/modules/4.15.0-32-generic/modules.builtin.bin
/lib/modules/4.15.0-33-generic/modules.builtin.bin
/lib/modules/4.15.0-34-generic/modules.builtin.bin
/lib/modules/4.15.0-36-generic/modules.builtin.bin
/lib/modules/4.15.0-39-generic/modules.builtin.bin
```

---

### Post by fidoro on 2018-11-25
Yes, I also have a lot of folders in there. But there is one named only "4.15.0" and I think it is right like that.
If I understand you right.
Your directories only seem to be versionated, from updating consequently. My system is freshly installed and thus doesn't seem to have these.

What I do have are some more 'spices' than only "generic", I seem to have "aws", "gcp", "lowlatency" as well as some others.
I don't quite now what that means for my problem, though.

But thanks for the input :)

---

