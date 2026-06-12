---
title: "Boot-Repair Pastebin"
date: 2019-02-05
forum: Virtualisation
---

### Post by pdiego.silva on 2019-02-05
**Hello everyone!**

I'm having a problem with a virtual machine running **Server 18.04 LTS**. After an unexpected shutdown of the host machine (**Windows Server 2008 R2 running Hyper-V**) this VM with Ubuntu 18.04 wont boot anymore, claiming a "boot partition" issue ("**uuid does not exist dropping to a shell**"). The host machine have other VMs that are running fine, this was the only one affected.

After some research, I've found instructions about **Boot-Repair** tool and put it to test, but still no luck on booting the system. After the Boot-Repair, the machine at least seems to boot, it hangs a lot on the "**Running: /scripts/init-botoom...**" message, then it goes to "**Welcome to Ubuntu 18.04.1 LTS!**", "**Set hostname to <hostname>**" and freezes there, giving no logon options. Pinging to the machine's IP also doesnt return anything.

Here is my Boot-Repair Pastebin: [http://paste.ubuntu.com/p/V7T89xWyvr/](http://paste.ubuntu.com/p/V7T89xWyvr/)

And here some visual of whats going on:

[ATTACH=CONFIG]282408[/ATTACH]

What can I do about it? Some advanced option on Boot Repair or some manual editing of a boot file / config?

Thanks in advance for any help!

---

### Post by howefield on 2019-02-05
Thread moved to the "*Virtualisation*" forum for a better fit.

---

### Post by oldfred on 2019-02-06
Do not know VM, but something does not look correct with fstab.

```
UUID=23cb5036-b5e5-11e8-9a33-00155d003403 none swap sw 0 0
UUID=2b022f5a-b5e5-11e8-9a33-00155d003403 / ext4 defaults 0 0
#UUID=1c61c71c-b5e5-11e8-9a33-00155d003403 /boot ext4 defaults 0 0

```

You show a /boot partition, but have it commented out in fstab.
And you do not show a swap partition but still have an entry in fstab. ( or is server also now using a swap file?)
And then grub.cfg not shown?

If you changed from using /boot partition to a /boot folder in / (root), you need to totally reinstall grub and a kernel. 
You can use Boot-Repair's advanced options and choose to add a new kernel and total reinstall of grub.

---

### Post by pdiego.silva on 2019-02-06
> **oldfred said:**
> Do not know VM, but something does not look correct with fstab.

```
UUID=23cb5036-b5e5-11e8-9a33-00155d003403 none swap sw 0 0
UUID=2b022f5a-b5e5-11e8-9a33-00155d003403 / ext4 defaults 0 0
#UUID=1c61c71c-b5e5-11e8-9a33-00155d003403 /boot ext4 defaults 0 0

```

You show a /boot partition, but have it commented out in fstab.
And you do not show a swap partition but still have an entry in fstab. ( or is server also now using a swap file?)
And then grub.cfg not shown?

If you changed from using /boot partition to a /boot folder in / (root), you need to totally reinstall grub and a kernel. 
You can use Boot-Repair's advanced options and choose to add a new kernel and total reinstall of grub.

Hi! Thanks for the help

So, I only executed the Boot-Reapir, I suppose he changed those lines on fstab. Just checked here and the fstab indeed have a line commented and the exactly same line at the end of the file. On sda4 partition there is a /boot folder but it is empty, and the sda2 partition is purely a /boot folder with the following contents:

config-4.15.0-X-generic
initrd.img-4.15.0-X-generic
System.map-4.15.0-X-generic
vmlinuz-4-15.0-X-generic

One of each file above for the versions (X) 43, 44 and 45. Algo a grub folder and a grub.bak folder.

Could the problem be related to the fact that I used a LiveCD of Desktop 18.04 LTS to repair Server 18.04 LTS? For what I read that was ok to do it.

As of the swap partition, it is the first one on the .vhd, **UUID=23cb5036-b5e5-11e8-9a33-00155d003403 none swap sw 0 0**, no?

I'll try to rerun the Boot-Repair choosing to purge and reinstall grub and kernel to see the results in the meantime.

---

### Post by pdiego.silva on 2019-02-07
Well, after several tries with Boot-Repair I couldnt solve the problem. After every attempt the boot froze after the "Set hostname" message, without actually loading the system.

As i was dealing with a VM, with backups of the VHD, I've decided to restore a backup from a few days ago and recover specific files from the ruined VHD that dont boot anymore. Here is what I've done:

- Booted from a Live CD into the ruined VHD, mounted the partitions and backuped the data I'd want to a network drive.
- Restored the backup of a VHD from a few days ago.
- Once I booted into the restored VHD, it seem'd to had some bug with my AD logon, so I had to log with a local user.
- That swap partition that appears on fstab was slowing down the boot, because she didn't existed. Along with this, the UUID on the fstab was wrong. I've ended up commenting the partition and moving on.
- Restored the data I needed from the network drive where it was backuped.
- Rejoined my AD.
- Rebooted the machine several times to make sure that no boot problem was left.

All working fine until now, 14 hours after the above procedures were done.

Thanks for the help anyway, I hope it helps someone in the future.

---

