---
title: "Mount partition as VirtualBox virtual hard disk"
date: 2013-02-19
forum: Virtualisation
---

### Post by huzefa_from_kuwait on 2013-02-19
I have a same issue with a slight change in taste

Mine is Pentium M laptop and the cd isn't working at all.

Ubuntu is installed and working fine.

I need to install Windows server 2003 in one of the empty partitions and my "old" laptop doesn't support booting from USB.


What I thought i will install virtualbox and use one of my partitions as a virtual disk.

I created the virtual disk of my partition with

```

VBoxManage internalcommands createrawvmdk -filename WinXP.vmdk  -rawdisk /dev/sda -partitions 1

```


Now however once I boot from Win2K3 CD all things work fine till I select the partition where I have to install win2k3 (in that blue screen). After which it asks to format and doesn't format because of SCSI adapter issue (according to google).

So is there some other way to inject Win2k3 into one of my partitions without USB boot and a working CD.

I cant buy a USB CD-Rom because I am poor (no wonder why would I be using Pentium M still if i wasn't poor)

I have tried changing LSIlogic and Buslogic and played around with no success 

Please help me,

Thanks.

---

### Post by codemaniac on 2013-02-19
Moved to its own thread. 

cheers!!

---

### Post by huzefa_from_kuwait on 2013-02-19
I did however get to work by 
```

VBoxManage internalcommands createrawvmdk -filename WinXP.vmdk  -rawdisk /dev/sda -partitions 1,2,3,5,6,7

```

4 was extended partition so there was no need to add it.

However because of hardware differences between virtual and 'real' machine Win2k3 never booted.

Now still thinking what to do ;)

---

### Post by huzefa_from_kuwait on 2013-02-19
I did however get to work by 
```

VBoxManage internalcommands createrawvmdk -filename WinXP.vmdk  -rawdisk /dev/sda -partitions 1,2,3,5,6,7

```

4 was extended partition so there was no need to add it.

However because of hardware differences between virtual and 'real' machine Win2k3 never booted.

Now still thinking what to do ;)

---

### Post by lmarmisa on 2013-02-20
I think that you should use the option -mbr in the command createrawvmdk ([http://www.virtualbox.org/manual/ch09.html#rawdisk](http://www.virtualbox.org/manual/ch09.html#rawdisk)).

You can create a file named zero.mbr typing this command:

```

dd bs=446 count=1 if=/dev/zero of=zero.mbr

```Then you can create the virtual disk:

```

VBoxManage internalcommands createrawvmdk -filename WinXP.vmdk  -rawdisk /dev/sda -partitions 1 -mbr zero.mbr

```Define a virtual machine with that virtual disk attached as IDE device and boot that VM from a Ubuntu Live CD (really use the iso file).

Open gparted and try to format to ntfs the partition /dev/sda1.

Shutdown the VM. 

Then start the VM from the Win2k3 installation iso file and try to install Windows in the partition /dev/sda1 (really Windows will assign a different name to this partition; select only one partition for installation).

Once Win2k3 is installed, shutdown the VM and close VirtualBox.

Finally, open a terminal and type this Ubuntu command:

```

sudo update-grub

```If the VM installation was correct, the command update-grub should detect Win2k3 and add it to GRUB2 menu at startup.

**NOTE**: I suppose you are trying to install Win2k3 in partition /dev/sda1.

---

