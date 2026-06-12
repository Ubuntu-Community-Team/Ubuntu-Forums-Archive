---
title: "Installed to iscsi fine, but hangs during boot"
date: 2011-02-13
forum: Server Platforms
---

### Post by aymnme on 2011-02-13
I have a ubuntu 10.10 server that won't complete booting from an iscsi target.

I pxe booted the machine and successfully installed the ubuntu server edition.  The initiator is running ietd 1.4 on a debian box.  Initially it could not login to the target, but I mounted that drive and fixed the problem.  It appears without a password that the script may not be quite correct.  

I chainboot gpxe to startup the client.  Grub comes up ok and then it begins to boot linux.  At some point it just stops and eventually (couple of minutes) many "I/O Errors appear".  It happens right after the system switches video modes thought I don't see why that matters.    The exact messages are and they appear many times.

Buffer I/O error on device sda1, logical block #######
end_request: I/O error, dev sda sector ####### (lots of these)
EXT3-fs (sda1) error in ext3_orphan_add: Journal has aborted
EXT3-fs (sda1) error in ext3_ordered_write_end: IO Failure
ath9k 000:02:00.0: Failed to initialize device

On the target side I don't see any errors, but do see many  connections being opened and closed.  I am at a loss and not sure why this is happening.  I am 99% sure there are no real errors since I can mount and fsck the disk just fine from another running system.  The odd part is that installing to the iscsi target worked fine, so I assumed that everything was OK.  I do see boot messages about eth0, one implying it is ready, but I don't see anything that would change the networking setup during boot.

my ietd.conf, the disk is part of lvm

iSNSServer 192.168.1.10
iSNSAccessControl No


Target iqn.2001-04.com.ayman:storage.lun1
        Lun 0 Path=/dev/vg/ubuntu_lun,Type=fileio
        Alias LUN1
        MaxConnections  1

---

### Post by frankie_guasch on 2011-02-25
hey, it happens exactly the same to me. I installed to the iscsi drive.
Then I build a tftpserver with a custom initrd following the sub.mesa reply here:

  [https://bugs.launchpad.net/ubuntu/+source/partman-iscsi/+bug/447377](https://bugs.launchpad.net/ubuntu/+source/partman-iscsi/+bug/447377)

initrd starts fine and mounts the root partition from the iscsi server.
Then it hangs for a while and starts spitting sda errors.

If I on purpose put wrong the initiator iqn I manage to get a prompt in the initrd. Then I do the iscsistart and mounts de partition right.
So it is working, what fails is the later remount or something. I am not sure.

Any hints would be appreciated. thank you very much

---

### Post by frankie_guasch on 2011-03-01
I found out the problem is when iscsid daemon is executed at boot time. It disconnects the sessions initiated with iscsistart in initrd and the system looses the root drive.

My system now boots since I changed /etc/init.d/open-iscsi adding an exit
at the beginning.

---

### Post by gurpal2000 on 2011-12-02
would either of you mind sharing how you managed to install+boot the os diskless ? thanks!

---

