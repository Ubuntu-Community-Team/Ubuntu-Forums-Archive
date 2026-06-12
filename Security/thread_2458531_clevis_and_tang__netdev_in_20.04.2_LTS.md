---
title: "clevis and tang _netdev in 20.04.2 LTS"
date: 2021-02-26
forum: Security
---

### Post by galahad70 on 2021-02-26
I am using Ubuntu 20.04.2 LTS with an unencrypted root volume. A secondary volume is encrypted with LUKS and I bound it to a tang server. 
I add these entries to the crypttab:

 plain_sda1 PARTUUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx none luks

After rebooting I am asked for the password, as expected, everything works as it should.

```
Feb 26 14:11:35 test systemd[1]: Dependency failed for /mnt/data.
Feb 26 14:11:35 test systemd[1]: Dependency failed for Remote File Systems.
Feb 26 14:11:35 test systemd[1]: remote-fs.target: Job remote-fs.target/start failed with result 'dependency'.
Feb 26 14:11:35 test systemd[1]: mnt-data.mount: Job mnt-data.mount/start failed with result 'dependency'.
Feb 26 14:11:35 test systemd[1]: [EMAIL="systemd-fsck@dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.servic"]systemd-fsck@dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.servic[/EMAIL]e: Job [EMAIL="systemd-fsck@dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.servic"]systemd-fsck@dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.servic[/EMAIL]e/start failed with result 'dependency'.
Feb 26 14:11:35 test systemd[1]: dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.device: Job dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.device/start failed with result 'timeout'.
[COLOR=#ff0000]Feb 26 14:11:35 test systemd-cryptsetup[638]: Set cipher aes, mode xts-plain64, key size 512 bits for device /dev/disk/by-partuuid/eab8a250-517f-4805-9f20-b813f450b18b.[/COLOR]
Feb 26 14:11:35 test systemd[1]: Starting LVM event activation on device 253:5...
Feb 26 14:11:35 test systemd[1]: Finished Cryptography Setup for plain_sda1.

```
If I change the entry from luks to _netdev in the crypttab, the partition is not automatically unlocked via the tang server after a restart.


```
 Feb 26 11:31:41 test systemd[1]: Dependency failed for /mnt/data.

 Feb 26 11:31:41 test systemd[1]: Dependency failed for Remote File Systems.
 Feb 26 11:31:41 test systemd[1]: remote-fs.target: Job remote-fs.target/start failed with result 'dependency'.
 Feb 26 11:31:41 test systemd[1]: mnt-data.mount: Job mnt-data.mount/start failed with result 'dependency'.
 Feb 26 11:31:41 test systemd[1]: Dependency failed for File System Check on /dev/disk/by-uuid/c7d53999-b7e3-4b75-ab7a-f1da346bcb65.
 Feb 26 11:31:41 test systemd[1]: [EMAIL="systemd-fsck@dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.servic"]systemd-fsck@dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.servic[/EMAIL]e: Job [EMAIL="systemd-fsck@dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.servic"]systemd-fsck@dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.servic[/EMAIL]e/start failed with result 'dependency'.
 Feb 26 11:31:41 test systemd[1]: dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.device: Job dev-disk-by\x2duuid-c7d53999\x2db7e3\x2d4b75\x2dab7a\x2df1da346bcb65.device/start failed with result 'timeout'.
 Feb 26 11:31:41 test systemd[1]: Starting LSB: automatic crash report generation...
 Feb 26 11:31:41 test systemd[1]: Starting Deferred execution scheduler...
 Feb 26 11:31:41 test systemd[1]: Started Regular background program processing daemon.
 Feb 26 11:31:41 test systemd[1]: Starting Permit User Sessions...
```

But if I execute "systemctl start [EMAIL="systemd-cryptsetup@plain_sda1.servic"]systemd-cryptsetup@plain_sda1.servic[/EMAIL]e" after the restart, the partition is unlocked without having to enter the password, the tang server works perfectly.

```
Feb 26 14:38:48 test systemd[1]: Created slice Cryptsetup Units Slice.
Feb 26 14:38:48 test systemd[1]: Starting Cryptography Setup for plain_sda1...
Feb 26 14:38:48 test systemd[1]: Starting Clevis LUKS systemd-ask-password Responder...
Feb 26 14:38:48 test systemd[1]: Started Dispatch Password Requests to Console.
Feb 26 14:38:48 test systemd[1]: Starting Forward Password Requests to Wall...
Feb 26 14:38:48 test systemd[1]: systemd-ask-password-console.path: Succeeded.
Feb 26 14:38:48 test systemd[1]: Stopped Dispatch Password Requests to Console Directory Watch.
Feb 26 14:38:48 test systemd[1]: Stopping Dispatch Password Requests to Console...
Feb 26 14:38:48 test systemd[1]: systemd-ask-password-console.service: Succeeded.
Feb 26 14:38:48 test systemd[1]: Stopped Dispatch Password Requests to Console.
Feb 26 14:38:48 test systemd[1]: Started Forward Password Requests to Wall.
Feb 26 14:38:49 test systemd[1]: clevis-luks-askpass.service: Succeeded.
Feb 26 14:38:49 test systemd[1]: Finished Clevis LUKS systemd-ask-password Responder.
Feb 26 14:38:49 test systemd-cryptsetup[1157]: Set cipher aes, mode xts-plain64, key size 512 bits for device /dev/disk/by-partuuid/eab8a250-517f-4805-9f20-b813f450b18b.
Feb 26 14:38:53 test systemd[1]: Finished Cryptography Setup for plain_sda1.
Feb 26 14:38:53 test systemd[1]: Reached target Block Device Preparation for /dev/mapper/plain_sda1.
Feb 26 14:38:53 test systemd[1]: Starting LVM event activation on device 253:5...
Feb 26 14:38:53 test lvm[1429]:   pvscan[1429] PV /dev/mapper/plain_sda1 online, VG storage is complete.
Feb 26 14:38:53 test lvm[1429]:   pvscan[1429] VG storage run autoactivation.
Feb 26 14:38:53 test kernel: [  604.612598] BTRFS: device label storage::data devid 1 transid 11 /dev/dm-6
Feb 26 14:38:53 test lvm[1429]:   1 logical volume(s) in volume group "storage" now active
Feb 26 14:38:53 test systemd[1]: Finished LVM event activation on device 253:5.

```
It seems as if everything is configured correctly, only if the _netdev option is used in the crypttab is apparently [EMAIL="systemd-cryptsetup@plain_sda1.servic"]systemd-cryptsetup@plain_sda1.servic[/EMAIL]e does anyone know what might be the problem?

---

### Post by annunaki2k2 on 2021-05-10
In case you're still looking for an answer to this, or if someone else hits this issue and is pulling their hair out…

I had the same issue, and after nearly half-a-day spent trawling through tickets, man pages, etc., I eventually hit upon:
```
systemctl enable remote-cryptsetup.target
```

So simple, but after doing that and rebooting, it worked perfectly!

---

