---
title: "Changing hostname question"
date: 2010-05-28
forum: Server Platforms
---

### Post by osx on 2010-05-28
I installed Ubuntu 10.04 64-bit on a server and then changed the hostname (e.g., from smtp to smtp02). On boot it displays the old name in the dev path /dev/mapper/smtp-root.

In my head it seems like this is fine and won't cause a problem since it has to do with the partitions that were created during install, but the side of me that desires consistency is nagging me and wondering if it could cause problems some where down the road.

I changed the hostname by manually editing /etc/hostname (also updated /etc/hosts). This is the way I have done it in the past.

Am I good to go? Should I be changing the hostname some other way? Are there some additional files I should be changing? Do I have OCD? :)

---

### Post by Irregular Joe on 2010-05-28
The naming will not cause any issues for you.

You can rename the volume groups and logical volumes, but this adds some additional risk (which can be overcome), and you will need to be able to boot the LiveCD (desktop) or from another OS that supports LVM2.

Before you do that, however, run the 'vgcfgbackup' command to save a copy of the LVM configuration as it exists now.  Store this on a thumb drive or other non-LVM partition.  Also save a copy of your /etc/fstab file to the thumb drive.

Boot from the LiveCD (I am assuming Lucid desktop).  Select the option to 'Try Ubuntu'.  Open a terminal window.
1) Desktop does not automatically include LVM, so install it with 'sudo apt-get install lvm2'
2) Issue the command 'sudo lvscan' to view the LVM groups and volumes, for reference.
3) To change the volume group name, use 'vgrename'
4) To change the logical volume name, use 'lvrename'
5) We will need to edit the configuration files on the unmounted volume, so create a mount point with 'sudo mkdir /media/oldfs' and mount the file system 'sudo mount /dev/mapper/xxx-yyy /media/oldfs'
6) Use sudo to edit the /media/oldfs/etc/fstab file to reference the new volume group and logical volume names.
7) Reboot (be sure to remove the LiveCD when prompted during shutdown).

With every bit of luck, this should be working just fine.  If there are problems, use the LiveCD, install lvm2 again, and use the vgcfgrestore command to get the volume groups back to where they started and restore the /etc/fstab file (remember to mount the file system).


With all those steps, you might decide to leave the volume names as they are.  Using the host name is a convention some people use, but there is nothing that mandates it.

---

### Post by osx on 2010-05-28
> **Irregular Joe said:**
> The naming will not cause any issues for you.

You can rename the volume groups and logical volumes, but this adds some additional risk (which can be overcome), and you will need to be able to boot the LiveCD (desktop) or from another OS that supports LVM2.

Before you do that, however, run the 'vgcfgbackup' command to save a copy of the LVM configuration as it exists now.  Store this on a thumb drive or other non-LVM partition.  Also save a copy of your /etc/fstab file to the thumb drive.

Boot from the LiveCD (I am assuming Lucid desktop).  Select the option to 'Try Ubuntu'.  Open a terminal window.
1) Desktop does not automatically include LVM, so install it with 'sudo apt-get install lvm2'
2) Issue the command 'sudo lvscan' to view the LVM groups and volumes, for reference.
3) To change the volume group name, use 'vgrename'
4) To change the logical volume name, use 'lvrename'
5) We will need to edit the configuration files on the unmounted volume, so create a mount point with 'sudo mkdir /media/oldfs' and mount the file system 'sudo mount /dev/mapper/xxx-yyy /media/oldfs'
6) Use sudo to edit the /media/oldfs/etc/fstab file to reference the new volume group and logical volume names.
7) Reboot (be sure to remove the LiveCD when prompted during shutdown).

With every bit of luck, this should be working just fine.  If there are problems, use the LiveCD, install lvm2 again, and use the vgcfgrestore command to get the volume groups back to where they started and restore the /etc/fstab file (remember to mount the file system).


With all those steps, you might decide to leave the volume names as they are.  Using the host name is a convention some people use, but there is nothing that mandates it.

Thanks for the detailed response. If it is not going to cause any problems then I may just leave it alone (as long as I can resist the urge anyway). However, I may try what you say on another machine as what you describe is very interesting to me. Thanks again.

---

