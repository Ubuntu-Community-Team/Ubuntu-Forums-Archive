---
title: "VMWare Tools Installation in Ubuntu 10.10"
date: 2016-05-24
forum: Virtualisation
---

### Post by Brij_Raj_Kishore on 2016-05-24
[COLOR=#111111][FONT=Ubuntu] I am Unable To Install VmWare Tools For My Linux Distro 10.10. I tried the following guide from the official [vmware site]("http://pubs.vmware.com/workstation-12/index.jsp?lang=en&topic=/com.vmware.ws.using.doc/GUID-08BB9465-D40A-4E16-9E15-8C016CC8166F.html"). I Am Currently Running -:[/FONT][/COLOR]

[LIST=1]
[*]Windows 10 - Host OS.
[*]Ubuntu 10.10 - Guest OS In Vmware 12 workstation
[*][IMG]http://i.stack.imgur.com/RwPzl.png[/IMG]
[*]I am getting this error
[/LIST]

---

### Post by TheFu on 2016-05-24
Support for 10.10 ended, er ... in 2011.  Move to a supported release - probably 14.04 today and 16.04 in July (after the .1 release).  You definitely need to be on LTS releases.

This won't help with your issue.  Check that the VM has a fake-CDROM and that something (like an ISO) has been connected to it. This is a common missed step - and not just for you, but for everyone.  I've done it at least 10 times - maybe 50  - over the years.

If there isn't a Fake-CDROM deviced added to the VM, you'll never mount it.  It can be either IDE or SATA, but IDE is more common in the other VM hypervisors.  I stopped using all VMware products around 2011, so haven't seen anything from then since.  Ubuntu Server doesn't automatically mount any storage, IME.  

Definitely check the device name - could be /dev/sr? or /dev/sd? or /dev/hd? - depends on the fake-interface seen.

People here will be more familiar with VirtualBox or KVM.

---

### Post by deadflowr on 2016-05-24
Well two things (aside from the EOL of 10.10)

1) Perhaps the device is /dev/sr0, instead of /dev/cdrom.

2) And it is more likely that the cd is already mounted.
Ubuntu does that, did that even back in 2010.

Look in the /media directory (this is where Ubuntu designates placing external storage devices such as cd's or external hard drives, etc, etc)

Or simply run command: **mount**
That will show all that's mounted on the system. As well as where it is mounted.

---

### Post by slickymaster on 2016-05-24
*Thread moved to **Virtualisation**.*

---

### Post by TheFu on 2016-05-24
> **deadflowr said:**
> 
Look in the /media directory (this is where Ubuntu designates placing external storage devices such as cd's or external hard drives, etc, etc)

Ubuntu Server doesn't automatically mount anything, IME.

---

### Post by Brij_Raj_Kishore on 2016-05-28
The Out put Of ```
mount
``` command is ```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mrinmoy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mrinmoy)


```

---

### Post by TheFu on 2016-05-28
Please verify that there is a fake CDROM/DVD device added to the VM inventory.  As I said above, if that isn't there, you cannot mount a CD.  Well, that isn't actually true - there are ways using an ISO file and the **mount -o loop**.

Also, it would be much more readable if "code tags" were used, not quotes.

---

