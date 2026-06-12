---
title: "Boot fails after adding second LUKS encrypted volume to out-of-box encrypted LVM"
date: 2013-05-14
forum: Server Platforms
---

### Post by uschxc on 2013-05-14
I'm trying to figure out what I'm doing wrong in my lab.  I went through the Ubuntu 12 LTS Server install, choosing an encrypted LVM setup.  I added a new drive to the VM and wanted to extend the "ubuntu-root" Volume Group using this disk.  The expansion and partition resize seemed to have gone great.  I updated the /etc/crypttab file to contain the UUID of the new file, and when I restarted I was greated with the following error.  Can someone please help?  I have a production server that has undergone the same routine, and now it is in danger of being inoperable if rebooted.

[IMG]http://i39.tinypic.com/359bcqg.png[/IMG]

After a little while I am dropped to an initramfs prompt, is there anything I can input here that will mount the second LUKS encrypted volume and continue boot as a last resort?

---

