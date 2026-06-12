---
title: "NBDE (clevis and tang) support in 18.04"
date: 2018-06-25
forum: Security
---

### Post by rkramer1 on 2018-06-25
[COLOR=#111111][FONT=Ubuntu][FONT=inherit][COLOR=#6A737C][FONT=inherit][COLOR=#111111][FONT=inherit]Running Ubuntu 18.04 with an unencrypted root volume. For what I need this to do, that's fine. But I need to mount and decrypt secondary disks. Following Red Hat's directions [/FONT][/COLOR][here]("https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/sec-using_network-bound_disk_encryption")[COLOR=#111111][FONT=inherit] since every google search for Ubuntu and NBDE/Clevis&Tang takes me there.[/FONT][/COLOR][/FONT][/COLOR][/FONT]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][FONT=inherit][FONT=inherit]**This procedure works flawlessly on RHEL 7.x and CentOS 7.x.*
[/FONT]
[FONT=inherit]I've gotten as far as partitioning (not using LVM here), encrypting, binding it to a tang server.[/FONT]
[FONT=inherit]First I install the packages:
[/FONT]
```
apt-get install clevis clevis-systemd clevis-dracut clevis-luks
```

[FONT=inherit]Then I set up the disk
[/FONT]
```
echo '<TEMPPASS>'| cryptsetup --verbose luksFormat /dev/xvdc1
```

```
clevis bind luks -f -k- -d /dev/xvdc1 tang '{"url":"http://<IP>:<PORT>","thp":"<KEY>"}' <<< "<TEMPPASS>"
```

Get rid of the temporary passkey

```
echo "<TEMPPASS>" | cryptsetup luksRemoveKey /dev/xvdc1
```

Unlock the device

```
clevis luks unlock -d /dev/xvdc1 -n testluksvol
```

[FONT=inherit]And Bob's your Auntie. Then I format it and verify it can mount.
[/FONT]
```
mkfs.ext4 /dev/mapper/testluksvol
```

```
mount /dev/mapper/testluksvol /testluksvol
```

[FONT=inherit]So far so good. I add the entries to /etc/fstab using _netdev as the directions said:
[/FONT]
```
/dev/mapper/testluksvol /testluksvol    ext4    defaults,_netdev 0 2
```

[FONT=inherit]Add the entry to /etc/crypttab, also with _netdev, though I didn't think Ubuntu crypttab supported that since it isn't in the crypttab manpage, but whatevs. We're making Chef Boy'R'D here, not world class bolognese:
[/FONT]
```
testluksvol     UUID=<DEVICE UUID>       none    _netdev
```

[FONT=inherit]And finally, enable clevis-luks-askpass.path
[/FONT]
```
systemctl enable clevis-luks-askpass.path
```

[FONT=inherit]Then we reboot... and it doesn't work. No auto decrypt, no auto mount. It sits for a bit running a job for the device before finally giving up and finishing the boot. So we go look in /var/log/syslog and see this:
[/FONT]
```
Jun 22 23:06:22 ubuntu03 systemd[1]: dev-disk-by\x2duuid-72ebf50e\x2dc3de\x2d468a\x2d89c3\x2defc869757a51.device: Job dev-disk-by\x2duuid-72ebf50e\x2dc3de\x2d468a\x2d89c3\x2defc86975
7a51.device/start timed out.
Jun 22 23:06:22 ubuntu03 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-72ebf50e\x2dc3de\x2d468a\x2d89c3\x2defc869757a51.device.
Jun 22 23:06:22 ubuntu03 systemd[1]: Dependency failed for Cryptography Setup for testluksvol.
Jun 22 23:06:22 ubuntu03 systemd[1]: Dependency failed for dev-mapper-testluksvol.device.
Jun 22 23:06:22 ubuntu03 systemd[1]: Dependency failed for /testluksvol.
Jun 22 23:06:22 ubuntu03 systemd[1]: Dependency failed for Remote File Systems.
Jun 22 23:06:22 ubuntu03 systemd[1]: remote-fs.target: Job remote-fs.target/start failed with result 'dependency'.
Jun 22 23:06:22 ubuntu03 systemd[1]: testluksvol.mount: Job testluksvol.mount/start failed with result 'dependency'.
Jun 22 23:06:22 ubuntu03 systemd[1]: Dependency failed for File System Check on /dev/mapper/testluksvol.
Jun 22 23:06:22 ubuntu03 systemd[1]: [EMAIL="systemd-fsck@dev-mapper-testluksvol.servic"]systemd-fsck@dev-mapper-testluksvol.servic[/EMAIL]e: Job [EMAIL="systemd-fsck@dev-mapper-testluksvol.servic"]systemd-fsck@dev-mapper-testluksvol.servic[/EMAIL]e/start failed with result 'dependency'.
Jun 22 23:06:22 ubuntu03 systemd[1]: dev-mapper-testluksvol.device: Job dev-mapper-testluksvol.device/start failed with result 'dependency'.
Jun 22 23:06:22 ubuntu03 systemd[1]: Dependency failed for Local Encrypted Volumes.
Jun 22 23:06:22 ubuntu03 systemd[1]: cryptsetup.target: Job cryptsetup.target/start failed with result 'dependency'.
Jun 22 23:06:22 ubuntu03 systemd[1]: [EMAIL="systemd-cryptsetup@testluksvol.servic"]systemd-cryptsetup@testluksvol.servic[/EMAIL]e: Job [EMAIL="systemd-cryptsetup@testluksvol.servic"]systemd-cryptsetup@testluksvol.servic[/EMAIL]e/start failed with result 'dependency'.
Jun 22 23:06:22 ubuntu03 systemd[1]: dev-disk-by\x2duuid-72ebf50e\x2dc3de\x2d468a\x2d89c3\x2defc869757a51.device: Job dev-disk-by\x2duuid-72ebf50e\x2dc3de\x2d468a\x2d89c3\x2defc86975
7a51.device/start failed with result 'timeout'.
```

[FONT=inherit]This is a bit beyond frustrating. I got 18.04 specifically because it was supposed to have support for clevis & tang. I wanted to integrate it into an existing env that is running tang servers.[/FONT]
[FONT=inherit]Can anyone, for the love of Linus Torvalds, tell me what I'm doing wrong?

[/FONT]*Update: I discovered that my disk UUID was wrong. Hence broken. Once I updated that, things worked correctly. I'm embarrassingly closing this help request.
[/FONT]
[/FONT][/COLOR]

---

### Post by apalacheno on 2018-12-30
Thanks for sharing your setup!

Did you manage to get Clevis to work with an encrypted root volume?

I'm trying but it seems that dracut won't bring up the network at initramfs stage; at least I can't see the client requesting a DHCP lease and I can't ping it at the root password prompt. Once root is decrypted everything works fine.

How can I enable networking in dracut? I already ran

```
dracut -f --kernel-cmdline "ip=dhcp"
```

and during dracut initialization it tells me that the networking module is enabled:
```
*** Including module: network ***
```

but still no network at the LUKS password prompt.

---

### Post by drlamb on 2019-01-25
Re Dracut and Networking in 18.04: I've actually just ran into this same problem. Doesn't happen in KVM of course. Did you find a solution?

---

### Post by apalacheno on 2019-02-11
Unfortunately not. Is it working on KVM for you? Maybe a required driver or module is missing in the initramfs.

---

### Post by drlamb on 2019-02-13
Yes, I've gotten it working with KVM. As virtual machines aren't a target of this project that's rather meaningless. I was hoping to find a solution to this quickly but as all projects go my attention got diverted. I'd really like to avoid pulling in an un-merged patch just to get NBDE working in my enterprise environment. [https://github.com/latchset/clevis/pull/35](https://github.com/latchset/clevis/pull/35)

---

### Post by tdussa2 on 2019-05-14
For the record, I believe the problem is that out of the box, at least bionic runs update-initramfs to update, well, the initramfs, not dracut.

Unfortunately, update-initramfs creates/updates a file called `/boot/initrd.img-$KERNELVERSION` (despite its name).  `dracut -f`, on the other hand, creates `/boot/initramfs-$KERNELVERSION.img`.

This means that after installing `clevis` as above, everything is set up properly in `/boot/initramfs-...`, but NOT in `/boot/initrd.img...`.

Now, since `/boot/initrd.img...` is the default, `grub` is configured to use that, not `/boot/initramfs-...`.

A workaround is to remove (or, more smartly, rename) `/boot/initrd.img...`, and then (after having run `dracut -f`) reconfigure `grub` with `update-grub`.

After that, unlocking with `clevis` at boot time should work (well, it did for me).

Beware, though, that this is just a workaround.  `apt` will still call `update-initramfs` if it feels it needs to update the initrd, so automatic updates will not work then (`grub` will still continue to use `/boot/initramfs...`).  I bet there is a way to convince `apt` to use `dracut` instead, will have to figure out how next.

---

