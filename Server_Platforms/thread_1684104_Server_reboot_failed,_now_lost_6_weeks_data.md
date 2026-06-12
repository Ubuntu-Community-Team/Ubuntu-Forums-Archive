---
title: "Server reboot failed, now lost 6 weeks data"
date: 2011-02-08
forum: Server Platforms
---

### Post by dvalphen on 2011-02-08
I am running Ubuntu Server 9.10 x86_64 on a HP Proliant ML115 server. Server has 8gb ram, 2x 500gb drives in Raid1 using the motherboard fake raid.

The system is running KVM with a few ubuntu and 1 windows guest. Most of the vm's are running in disk images, however one partition is lvm, and is mounted as is in a guest vm that exports it on the network using nfs/samba - this is the one I am hoping to be able to recover some data from.

I logged in to install updates, and the system informed me that it needed a restart, which I did. When the machine failed to come back up, I pressed the off button - acpi is configured to shut down the system when I press this. Incidently it switched off immediately, so I knew there was a problem.

Booted up with a screen and keyboard and discovered the default grub entry gives an error. Havent got it written down, but I can reboot to take a look if needed.

All the changes to both host and all vms since december 26 are not present. Almost as if I reverted to a previous snapshot, only I've not used those on this system at all. Log files on any of the affected systems show things like:

Dec 26 23:54:01 host kernel: Kernel logging (proc) stopped.
Feb  8 09:07:59 host kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.

Dec 26 23:35:28 vm1 -- MARK --
Feb  8 09:10:24 vm1 syslogd 1.5.0#5ubuntu3: restart.

Unfortunately discovered that there is a problem with the backups I've got, no restore options from that :(

Has anyone got any ideas on what may have happened, if there may be a way to check the journals etc? Any suggestions are appreciated.

---

### Post by dtfinch on 2011-02-08
I have no experience with KVM or Qemu but I think if you're using a differential disk format (like qcow2), if you've ever taken a snapshot, the original file would hold the old data, and any changes since then would be in a new file that references it.

If it's forgotten that it had switched to a new differential image after a snapshot, it may be using the base image instead. This is quite dangerous if it actually makes changes to the base image, which could make the differential image appear corrupt. Though this situation is out of my league, I'd suggest stopping the VMs until you know for sure whether or not there's a separate differential disk image it should be using.

I have no idea why the host would experience a similar revert though.

---

### Post by dvalphen on 2011-02-08
Thanks for the response dtfinch.

I haven't used any snapshot tools on this server so nothing to revert to. Also the data partition isnt a disk image but an lvm partition.

I've shut down the VMs, and instead tried mounting the data partition on the host in a temporary space. This works okay though with the same data that the VM was showing, so it seems that it wasn't a VM loading issue.

I've checked the boot logs, and the partition was clean on initial boot after the update failure.

The raid array is also healthy.

Any thoughts?

---

