---
title: "CIFS automount no longer working"
date: 2017-08-31
forum: Server Platforms
---

### Post by yuljk2 on 2017-08-31
Hi guys - I'm running Ubuntu Server 16.04.3, as of this morning my CIFS automounted drive no longer mounts on bootup. Nothing has changed in my fstab.

Syslog shows the following:

```
Aug 31 17:01:38 uranus mount[1163]: mount error(112): Host is downAug 31 17:01:38 uranus mount[1163]: Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
Aug 31 17:01:38 uranus kernel: [   45.127223] CIFS VFS: cifs_mount failed w/return code = -112
Aug 31 17:01:38 uranus systemd[1]: mnt-Music.mount: Mount process exited, code=exited status=32
Aug 31 17:01:38 uranus systemd[1]: Failed to mount /mnt/Music.
Aug 31 17:01:38 uranus systemd[1]: Dependency failed for Remote File Systems.
Aug 31 17:01:38 uranus systemd[1]: remote-fs.target: Job remote-fs.target/start failed with result 'dependency'.
Aug 31 17:01:38 uranus systemd[1]: mnt-Music.mount: Unit entered failed state.

```

etc/fstab:

```
//192.168.50.182/storage/music /mnt/Music cifs credentials=/root/.smbcredentials,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0
```

My .smbcredentials file is present with the correct credentials specified.  Presumably some update has caused this to stop working, as it has been working without a hitch for months.

I should note that the file server (2012 R2) is pingable from Ubuntu and an assortment of Windows clients have no issues accessing the share with the same credentials.

Any help appreciated!

---

### Post by darkod on 2017-08-31
Can you mount it from command line?

Can you telnet 445 from ubuntu to the server? I think cifs uses port 445. Just ping is not very relevant, check if you can open the port you need.

The message host is down seems clear, somehow it think the server is not there...

---

### Post by yuljk2 on 2017-08-31
Hi - Figured out the issue - seems a recent Windows update for Server 2012 R2 now requires you to specify the SMB version when mounting a CIFS share as the SMB version has been updated to 3.02. (I presume this applies to Windows 8 upwards)

I added vers=3.0 to the end of my automount in fstab and mount -a works fine now.

P.S - Clearly port 445 is open, otherwise Windows clients wouldn't be able to connect (as I mentioned in the original post)

Kind Regards

---

