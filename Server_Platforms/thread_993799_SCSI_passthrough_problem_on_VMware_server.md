---
title: "SCSI passthrough problem on VMware server"
date: 2008-11-26
forum: Server Platforms
---

### Post by newenden on 2008-11-26
Hi,

I've just spotted that SCSI passthrough to an LTO-2 tape drive has stopped working on an Ubuntu 8.04 Server running VMware server 1.07. Guest OS on the VM is Windows SBS 2003 R2.

It was working fine, both under VMware server 1.06 and 1.07. It stopped working on 24 October when the Ubuntu host was updated, through Aptitude, with Security patches and Updates as at that date. We had previously updated Ubuntu on 6 Sept 2008 so whatever has changed was released between 6 Sept and 24 Oct. The Ubuntu update was the only change that happened on 24 Oct, Windows updates on the guest OS are done regularly but none on that date, which was when the tape backup problem started.

The tape device is still showing as /dev/sg0 (lsscsi -g) and shows as connected in the VM in VMware Tools. However, it doesn't show up in Windows Device Manager and isn't available within Backup Exec on the guest. The tape drive is only associated with the one VM, so there isn't any reason for access conflicts between VMs. 

Anybody else seen this? Any thoughts?

Thanks,

Chris

---

### Post by newenden on 2008-11-26
Problem solved. After trying various things yesterday, I fixed it by:

- shutting down the VM

- deleting the virtual SCSI device from the VM config

- adding the virtual SCSI device back to the VM config from scratch

- restarting the VM, after which the tape drive appeared in Windows Devices

- reconfigured the tape drive in Backup Exec.

The difference between yesterday and today was that I deleted and added the virtual SCSI device (using the VMware Windows client), yesterday I just checked its config. Strange.

Regards,

Chris

---

