---
title: "Kernel panic after oneiric upgrade"
date: 2011-10-27
forum: System76 Support
---

### Post by jtappin on 2011-10-27
I've just done an upgrade for my Pangolin P5 from Natty to Oneiric.
I used "apt-get dist-upgrade" after editing the sources.list and files in sources.list.d rather than the upgrade tool as I've never managed to get that to work properly on any system.

Unfortunately as soon as it tries to boot, there is a kernel panic with a message about not finding the disk (even when I try to select the older kernel). [I don't have the full message, and right now I've got the machine booted into Pardus on an external drive to download the Oneiric install/live image].

Any clues at this stage? I'll try to get the full message and the result with the live image once I'm in a position to reboot.

---

### Post by 2F4U on 2011-10-27
Try the liveCD and see if that boots. That may give an idea if it is the kernel that causes the problem or if something went wrong with the upgrade.

---

### Post by jtappin on 2011-10-27
Update:

1) Yes it does  boot OK from the live media.
2) I do now seem to be able to boot the old (natty) kernel, probably finger trouble the first time.

3) This is the panic message. I've omitted the times and the long hex number before the routines (I was copying by hand onto another machine.
```
Boot from (hd0,0) ext3 <UUID>
Starting up.
[] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[] Pid: 1, comm: swapper Not tainted 3.0.0-13-generic #21-Ubuntu
[] Call Trace:
[] [] panic+0x91/0x194
[] [] mount_block_root+0xdc/0x18e
[] [] mount_root+0x54/0x59
[] [] prepare_namespace+0x16d/0x1a7
[] [] kernel_init+0x140/0x145
[] [] kernel_thread_helper+0x4/0x10
[] [] ? start_kernel+0x3df/0x3df
[] [] ? gs_change+0x13/0x13

```

---

### Post by jtappin on 2011-10-27
I should just add that it looks to me from what I've been able to find on the net that there's a module missing in the initramfs, but which one? all the EXT filesystems are build-in according to the config file, and there are no sata or pata modules loaded with the 2.6.38 kernel.

---

### Post by isantop on 2011-10-28
Could it be that te 3.0 kernel is trying to boot using the .38 initramfs? Try booting the old kernel, backing up, and run this command:

```
sudo update-initramfs -u
```

EDIT: I just conferred with a couple other guys on this issue, and they both think that updating manually was a bad idea. The Upgrade tool uses a lot of scripts to determine exactly how to upgrade the system, and if you use apt to perform an upgrade, those won't get run, and it's unlikely that the upgrade will be successful. Their advise is to back up your files and do a clean installation.

---

### Post by jtappin on 2011-10-30
> **isantop said:**
> Could it be that te 3.0 kernel is trying to boot using the .38 initramfs? Try booting the old kernel, backing up, and run this command:

```
sudo update-initramfs -u
```

That was the first thing I tried after I managed to boot with the old kernel, and it didn't do the trick.

> **isantop said:**
> EDIT: I just conferred with a couple other guys on this issue, and they both think that updating manually was a bad idea. The Upgrade tool uses a lot of scripts to determine exactly how to upgrade the system, and if you use apt to perform an upgrade, those won't get run, and it's unlikely that the upgrade will be successful. Their advise is to back up your files and do a clean installation.

It's always worked in the past, whereas I've had the upgrade tool fail when it kicked X out from under itself (things are probably better now but old habits die hard).

---

### Post by jtappin on 2011-10-31
I managed to fix things without doing a full re-install. It's not pretty but for the record here is what worked for me:
[LIST=1]
[*]Revert /etc/apt/sources.list and the contents of /etc/apt/sources.list.d to natty.
[*]Edit /etc/lsb-release and convert it back to natty and 10.04.
[*]Run do-release-upgrade from the console. Accept most defaults, but let it take the package-maintainers version when it asked for a choice about the grub configuration.
[*]Re-enable extra repositories from adept.
[*]Copy the backup of /etc/lsb-release back to stop it offering to upgrade again.
[/LIST]

This has the advantage of not requiring another overnight download of packages (one reason behind trying to do it manually in the first place was to download the packages overnight and then install them while watching for trouble next morning).

---

### Post by joshrestivo on 2011-11-27
FWIW, I ran into this problem after upgrade and, in my case, I found that the initrd line for the 3.0.0 kernel was missing from /boot/grub/menu.list. Adding the following line (assuming kernel 3.0.0-13) after the 'kernel' lines for the two 3.0.0 entries (main kernel entry and recovery mode) allowed me to boot without issue:

initrd  /boot/initrd.img-3.0.0-13-generic

---

