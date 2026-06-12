---
title: "Errors with loop device mounted with sshfs"
date: 2012-06-25
forum: Server Platforms
---

### Post by kodiakz on 2012-06-25
Hello,
I am running 12.04 server on a KVM. To extend available storage I mounted a 100GB sftp storage.
Furthermore, to be able to have multi-user support on that drive I created a loop device using dd and made it ext4.

fstab looks like:
```

sshfs#backup-7224@somedomain.com:/ /mnt/hidrive/ fuse comment=sshfs,IdentityFile=/etc/ssh/ssh_host_dsa_key,umask=0113,noauto,exec,reconnect,follow_symlinks,transform_symlinks,idmap=user,gid=fuse,allow_other,rw 0 0

```

In rc.local I have following
```

mount /mnt/container
losetup /dev/loop0 /mnt/container
mount /mnt/container_data

```

well now when transmitting data dmesg shows following a lot:

> 
[ 2623.502322] loop: Write error at byte offset 49526480896, length 4096.
[ 2623.502394] loop: Write error at byte offset 49526484992, length 4096.
[ 2623.502440] Aborting journal on device loop0-8.
.
.
.
[ 2652.888066] loop: Write error at byte offset 30065033216, length 4096.
[ 2652.888812] quiet_error: 313 callbacks suppressed
[ 2652.888815] Buffer I/O error on device loop0, logical block 7340096
[ 2652.889538] lost page write due to I/O error on loop0
[ 2713.818801] EXT4-fs (loop0): previous I/O error to superblock detected
[ 2713.820524] loop: Write error at byte offset 0, length 4096.
[ 2713.821644] Buffer I/O error on device loop0, logical block 0
[ 2713.822846] lost page write due to I/O error on loop0
[ 2713.822860] EXT4-fs error (device loop0): ext4_put_super:818: Couldn't clean up the journal
[ 2726.564376] Buffer I/O error on device loop0, logical block 24999984
[ 2726.565352] Buffer I/O error on device loop0, logical block 24999984
[ 2726.566399] Buffer I/O error on device loop0, logical block 24999998
[ 2726.567278] Buffer I/O error on device loop0, logical block 24999998
[ 2726.568333] Buffer I/O error on device loop0, logical block 1
.
.
.
[ 2726.571601] Buffer I/O error on device loop0, logical block 24999999
[ 2726.572396] Buffer I/O error on device loop0, logical block 24999999
[ 2740.575507] EXT4-fs (loop0): recovery complete
[ 2740.575555] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: errors=continue



I did fsck.ext4 on /dev/loop0, it says fine but did not spend a second for checking.
The storage is most of the time accessible, it contains data.
Sometimes though container_data is not accessible. If I try to access it via terminal it freezes. I can not rely on data consistency. Can anybody point me into a direction?

---

