---
title: "Backing up KVM/libvirt virtual machines automatically"
date: 2009-02-09
forum: Virtualisation
---

### Post by stephanhughson on 2009-02-09
Hi,

I was wondering what is the (best) way everyone out there has found to back up their virtual machines? I'm using KVM with the virtual machines controlled through libvirt.

libvirt has a couple of features that might help, but what I'd really like is to avoid suspending or rebooting the virtual machine. The aim is to have a complete snapshot of the drive (memory if possible) that can be used in case of a disaster recovery.

Losing stuff in memory / requiring an fsck on restore isn't the end of the world for me... I would probably back up the personal data / user files separately anyway. In fact, it would be great if the image could *not* include the data!

Mondorescue actually ticks most of the boxes in regards to what I want, but although I have messed about with it quite a bit, I haven't got it working yet.

What does everyone out there do? I'm interested to know, even if it's something basic.

Thanks

---

### Post by Blinkiz on 2009-04-04
Hi there
All my virtual machines disc storage are in separated logical volumes.
So for example, my file server has the path /dev/vg/fileserver and mail server /dev/vg/mail.

You can easily do LVM snapshots. In fact, it's the only way I know it's possible to do a live snapshot of a running machine. When you have done the snapshot, you can mount the new volume in any way you want. I for example, mount this snapshots in my virtual machine responsible for backups. Bacula.

The above solution is not automated in any good way. So you have to create bash scripts and so on to get this automated.

God luck!

---

### Post by stephanhughson on 2009-04-23
Thanks. I think that's the best way. I spoke to someone who runs a KVM virtual machine hosting service and also someone who has a build/test system running Xen virtual servers. That's how they both recommend doing it as well.

For me just now, I have made a script that suspends each virtual machine, then simply copies the disk image file. It takes about 20 seconds per machine. I have split up my .qcow2 images so that there is a small one (about 4 gigs) for the operating system, then a larger one mounted for the data (e.g. home directories etc). It's basic, but will do for the moment. :P

---

### Post by yngens on 2012-04-15
> **stephanhughson said:**
> Thanks. I think that's the best way. I spoke to someone who runs a KVM virtual machine hosting service and also someone who has a build/test system running Xen virtual servers. That's how they both recommend doing it as well.

For me just now, I have made a script that suspends each virtual machine, then simply copies the disk image file. It takes about 20 seconds per machine. I have split up my .qcow2 images so that there is a small one (about 4 gigs) for the operating system, then a larger one mounted for the data (e.g. home directories etc). It's basic, but will do for the moment. :P

Hi Stephan,

Could you please share your script since I also don't want to go into complications of turning my setup into separate LVMs. I am doing what your script does manually for now.

---

### Post by stephanhughson on 2012-04-15
Yeah, no problem, although I do it differently now.

I'm taking snapshots of the disk using r1soft hotcopy which is available from here: [http://www.r1soft.com/tools/linux-hot-copy/](http://www.r1soft.com/tools/linux-hot-copy/) , then copying the files, then deleting the snapshot.

r1soft have an apt repository, you'll need to dig around on their website to find the details. I would post them here, but they'll want you to register etc, even though it's free.

Anyway, here's the code, which I just run manually from time to time.

```

# Check to see if the r1soft hotcopy module is loaded. If it isn't, then install it.
lsmod | grep hcpdriver || hcp-setup --get-module

# Take a snapshot of the RAID 1 array.
hcp --mount-point /mnt/hotcopy/ /dev/md0

# Mount the extra hard disk.
mount /dev/sdc1 /mnt/extradrive/

# Check that the hard disk and snapshot are actually mounted. Exit if they are not.
mount | grep hotcopy || exit
mount | grep extradrive || exit

# Copy the xml that defines the virtual machines.
rsync /etc/libvirt/qemu/*.xml /mnt/extradrive/xml/

# Copy the disk images that the virtual machines use.
rsync -a --progress --verbose --human-readable /mnt/hotcopy/vservers/ /mnt/extradrive/vservers/

# Remove the snapshot.
hcp --remove /dev/hcp1

# Unmount the extra hard disk
umount /mnt/extradrive

```



My old script was called using rsnapshot, so rsnapshot would pause the VMs, then copy the files, then resume them. You could combine the two scripts to make something quite nice as the "hotcopy" command won't require pausing of the VMs.

Here's the old script:

```

# This script takes backups of paused virtual machines and saves them locally, to be be saved later with rsnapshot by the backup server.

# Get a list of the virtual machines that are running on the server.
virtualserverlist=`virsh list --all | grep running | awk {'print $2'}`

# For each virtual machine on the virtual host server, get the list of disk images that are in use.
for virtualserver in $virtualserverlist
	do
	# Exclude files with "dataimage" in the name, as those are large and get backed up with normal rsnapshot while the virtual machine is running.
	diskimagelist=`ls /vservers/$virtualserver | grep -v dataimage`

	# Suspend the virtual server
	virsh suspend $virtualserver
	echo "$virtualserver suspended at" `date`
		
	# For each disk, copy it to the temporary rsnapshot directory
	for disk in $diskimagelist
	do
		echo "Backing up $disk from $virtualserver"
		time rsync --inplace /vservers/$virtualserver/$disk /root/virtual_machine_backups/$virtualserver-$disk
	done

	# Resume the virtual server
	virsh resume $virtualserver
	echo "$virtualserver resumed at" `date`
done

```


I can't give you what's in my rsnapshot configuration file, as that server is currently down (I just emigrated so it's in a box), but in the configuration file, you would look for the "backup_script" part, then just have it call the script you've written.

If you end up making something good, please share it back as I really should improve the way I'm doing it, just don't have much time.

Hope that helps. Good luck.

---

### Post by yngens on 2012-04-15
> **stephanhughson said:**
> 

```

# This script takes backups of paused virtual machines and saves them locally, to be be saved later with rsnapshot by the backup server.

# Get a list of the virtual machines that are running on the server.
virtualserverlist=`virsh list --all | grep running | awk {'print $2'}`

# For each virtual machine on the virtual host server, get the list of disk images that are in use.
for virtualserver in $virtualserverlist
	do
	# Exclude files with "dataimage" in the name, as those are large and get backed up with normal rsnapshot while the virtual machine is running.
	diskimagelist=`ls /vservers/$virtualserver | grep -v dataimage`

	# Suspend the virtual server
	virsh suspend $virtualserver
	echo "$virtualserver suspended at" `date`
		
	# For each disk, copy it to the temporary rsnapshot directory
	for disk in $diskimagelist
	do
		echo "Backing up $disk from $virtualserver"
		time rsync --inplace /vservers/$virtualserver/$disk /root/virtual_machine_backups/$virtualserver-$disk
	done

	# Resume the virtual server
	virsh resume $virtualserver
	echo "$virtualserver resumed at" `date`
done

```

If you end up making something good, please share it back as I really should improve the way I'm doing it, just don't have much time.

The first variant is too much complicated for me, so I prefer to keep things simple for now. Thanks for sharing the second script, I am going to adapt it to my environment for some custom paths. I'd like to also give a try to 'virt-clone' function ([https://help.ubuntu.com/community/KVM/CreateGuests](https://help.ubuntu.com/community/KVM/CreateGuests)) instead of 'rsync' to reduce the downtime if it is really shorter and if it makes sense.

When I have little more experience with KVM I'd like to dig little dipper to using KVM's capability of taking snapshots like described here [http://serverfault.com/a/22905](http://serverfault.com/a/22905), but for now I am happy I can simply take copies or to clone VM images.

---

