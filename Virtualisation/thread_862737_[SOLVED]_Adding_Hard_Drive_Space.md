---
title: "[SOLVED] Adding Hard Drive Space?"
date: 2008-07-17
forum: Virtualisation
---

### Post by ant2ne on 2008-07-17
Is there a way to add HD space to an already running VM? Or do I need to delete the VM and recreate/re-install one?

---

### Post by dpj23 on 2008-07-17
you can create a second drive and add it to the existing machine... For example a windows machine would have a "C" and "D" drive...

---

### Post by ant2ne on 2008-07-18
yes, but many programs (including MS Visual Studio Suite) does not give you an option of where to install =-(  

Looks like its time for a new VM

---

### Post by Keithel on 2008-07-18
If this is a VMware VM (others too perhaps, as I think the vm hd file format is the same? at least it sounds like it?) then you can use vmware-vdiskmanager to expand the *drive*.  I believe the command line argument you want is the '-x' option.

Note -- this expands the drive and not the partitions on it.  Then, once you've expanded the drive, you can then use GParted from a livecd, or partition magic, or a variety of other tools of the like to expand your partition(s).  Once that's done, you should be all set with more space.

Make sure you have enough space in your host OS for the expansion!

You should be able to find the vvmware-vdiskmanager utility in a VMware workstation install.  I'm pretty sure it's not available with VMware player, and I'm not sure about VMware Server.  There might be other tools out there too to expand the disk -- not sure.

---

### Post by ant2ne on 2008-07-20
Cool tool. How do I find the disk to be modified. Will it have a file extension?

---

### Post by fjgaude on 2008-07-20
I've never tried it before but Keithel is right on.

At the Ubuntu command line simply type **vmware-vdiskmanager** and you get a pretty complete how-to to expand a VM. As stated the -x plus the VM name should do it. Notice example 4 of the program, the -x one.

New understanding, at least for me.

Thanks, Keithel!

---

### Post by ant2ne on 2008-07-20
```
ant2ne@2ne-buntu:~$ vmware-vdiskmanager --help
vmware-vdiskmanager: invalid option -- -
VMware Virtual Disk Manager - build 80187.
Usage: vmware-vdiskmanager OPTIONS diskName 
Offline disk manipulation utility
  Options:
     -c                   : create disk; need to specify other create options
     -d                   : defragment the specified virtual disk
     -n <source-disk>     : rename the specified virtual disk; need to
                            specify destination disk-name
     -q                   : do not log messages
     -r <source-disk>     : convert the specified disk; need to specify
                            destination disk-type
     -x <new-capacity>    : expand the disk to the specified capacity

     Additional options for create and convert:
        -a <adapter>      : (for use with -c only) adapter type (ide, buslogic or lsilogic)
        -s <size>         : capacity of the virtual disk
        -t <disk-type>    : disk type id

     Disk types:
        0                 : single growable virtual disk
        1                 : growable virtual disk split in 2Gb files
        2                 : preallocated virtual disk
        3                 : preallocated virtual disk split in 2Gb files

     The capacity can be specified in sectors, Kb, Mb or Gb.
     The acceptable ranges:
                           ide adapter : [100.0Mb, 950.0Gb]
                           scsi adapter: [100.0Mb, 950.0Gb]
        ex 1: vmware-vdiskmanager -c -s 850Mb -a ide -t 0 myIdeDisk.vmdk
        ex 2: vmware-vdiskmanager -d myDisk.vmdk
        ex 3: vmware-vdiskmanager -r sourceDisk.vmdk -t 0 destinationDisk.vmdk
        ex 4: vmware-vdiskmanager -x 36Gb myDisk.vmdk
        ex 5: vmware-vdiskmanager -n sourceName.vmdk destinationName.vmdk

ant2ne@2ne-buntu:~$ 

```

Oh, I see now I execute it on the vmdk. I don't know why I didn't see that the first time i executed that help command.

Thanks!!

---

### Post by Keithel on 2008-07-21
Yep, you guys have the right idea.

Just remember -- after the vmware-vdiskmanager -x operation is complete, don't expect that when you boot your VM, that it will show the extra space. The VM will show (using proper tools) that the *disk* is biggger, but the partitions remain the same size -- thus, when you do a df, it will show the same free space prior to you expanding.

In order to utilize the space that you have created (the expanded disk), you will need to boot with a livecd like one of the Ubuntu discs, and expand the partition using a tool like GParted (should be accessible from the System->Administration menu (I'm not 100% sure on the menu placement).  Another option is to use a tool like Partition Magic (which does the same thing as GParted, but at a cost, and with prettier visualizations)

---

### Post by fjgaude on 2008-07-22
> **Keithel said:**
> Yep, you guys have the right idea.

Just remember -- after the vmware-vdiskmanager -x operation is complete, don't expect that when you boot your VM, that it will show the extra space. The VM will show (using proper tools) that the *disk* is biggger, but the partitions remain the same size -- thus, when you do a df, it will show the same free space prior to you expanding.

In order to utilize the space that you have created (the expanded disk), you will need to boot with a livecd like one of the Ubuntu discs, and expand the partition using a tool like GParted (should be accessible from the System->Administration menu (I'm not 100% sure on the menu placement).  Another option is to use a tool like Partition Magic (which does the same thing as GParted, but at a cost, and with prettier visualizations)

Gosh, I'm missing something... we are talking about expanding the disk space that is reserved for a VM? Such doesn't show on a parition editor, it's just a big file, this VM.

---

### Post by Dasvinder Singh on 2008-07-22
trying to use outlook but get error messages

---

### Post by Keithel on 2008-07-22
> **fjgaude said:**
> Gosh, I'm missing something... we are talking about expanding the disk space that is reserved for a VM? Such doesn't show on a parition editor, it's just a big file, this VM.

Not quite.  I'm talking about running a partition manager in the guest machine. -- The guest machine knows not that it's disk is really just a file in the host OS.

---

### Post by fjgaude on 2008-07-22
Okay... I never have done such things... live and learn!

What you suggest is I expand my "disk" from say 10G to 20G, and then I have to go in using something like Partion Magic to let the VM know its 20G by using the features of PM? Yes! Okay.

Thanks.

---

### Post by Keithel on 2008-07-22
> **fjgaude said:**
> What you suggest is I expand my "disk" from say 10G to 20G, and then I have to go in using something like Partion Magic to let the VM know its 20G by using the features of PM? Yes! Okay.
Exactly! :)

> **fjgaude said:**
> Okay... I never have done such things... live and learn!
We all have to learn somewhere! I'm glad to be of help.

---

### Post by beaver29 on 2008-08-29
it seems like expanding your existing drive is the best option.  if that doesn't work for some reason, another alternative might be to add a new virtual scsi drive:

[http://www.thoughtpolice.co.uk/vmware/howto/vmware-scsi-disk-add.html]("http://www.thoughtpolice.co.uk/vmware/howto/vmware-scsi-disk-add.html")

---

### Post by ant2ne on 2008-08-31
```
ant2ne@2ne-buntu:/var/lib/vmware/Virtual Machines/XP Pro x64$ vmware-vdiskmanager -x 20Gb "XP Pro x64.vmdk"
Using log file /tmp/vmware-ant2ne/vdiskmanager.log
This disk is part of a snapshot chain in '/var/lib/vmware/Virtual Machines/XP Pro x64/XP Pro x64.vmx'.
The selected operation can only be executed on a disk with no snapshots.
ant2ne@2ne-buntu:/var/lib/vmware/Virtual Machines/XP Pro x64$ 

```how do I remove the snapshot so I can expand the drive?

---

### Post by lazyart on 2008-08-31
I had to do this recently but unfortunately I went a different route:

I installed a second hd into the VM, booted the VM with a clonezilla disk and copied disk 1 into disk 2. Then I deleted disk one and told the vm to boot from disk 2.  Ta-da.

---

### Post by solitaire on 2008-08-31
what OS is in the virtual Machine?

XP and above let's you "Mount" a new NTFS drive to a folder on a NTFS drive. (Like in linux but a bit more awkward to find.) check the "Drive management" in XP.  I've done it a few times years ago to test it but can't remember exactly what to do.

---

### Post by ant2ne on 2008-09-04
> **ant2ne said:**
> ```
ant2ne@2ne-buntu:/var/lib/vmware/Virtual Machines/XP Pro x64$ vmware-vdiskmanager -x 20Gb "XP Pro x64.vmdk"
Using log file /tmp/vmware-ant2ne/vdiskmanager.log
This disk is part of a snapshot chain in '/var/lib/vmware/Virtual Machines/XP Pro x64/XP Pro x64.vmx'.
The selected operation can only be executed on a disk with no snapshots.
ant2ne@2ne-buntu:/var/lib/vmware/Virtual Machines/XP Pro x64$ 

```how do I remove the snapshot so I can expand the drive?Like I said...

---

### Post by TheGameAh on 2008-09-05
Just like above, I went the long way, then got mad about it when I found out it was the long way  :)

I installed a second virtual disk, then used Ghost to clone disk 1 to 2, then deleted disk 1.  

Then I find out a day later that you can use a command line tool to expand the disk.

Bah.

---

### Post by HermanAB on 2008-09-05
It is kinda confoosing...

You need to boot the VM with the Live CD.  Activate the CDROM and reboot the VM, or point the VM CDROM device to an ISO file of the live CD.

Cheers,

Herman

---

### Post by troj on 2008-09-05
> **fjgaude said:**
> Gosh, I'm missing something... we are talking about expanding the disk space that is reserved for a VM? Such doesn't show on a parition editor, it's just a big file, this VM.

From the VMware Server *Host* it is a big file, but from the VMware VM *Guest* it is a disk with a new (expanded) geometry. But the partitions are all the same ones (and same size) that existed before the expansion occurred. So you have to run a partition resizing application on the Guest VM to have the Guest OS recognize the expanded space (or, alternately, create a new partition with the expanded space).

---

### Post by ant2ne on 2008-12-27
I finally got around to playing with this today.

I resized the partition using vmware-vdiskmanager from 10gig to 20gig, and it worked. 

I then resized the partition by booting from a gparted CD. I boot to windows, and I got the same 10gig partition size. 

I reboot into gparted, and it tells me the disk is dirty, so I reboot again into windows, run check disk, reboot back into gparted. Gparted thinks it is resized to 20gigs. I resize it smaller again, just so I can resize it larger again, then reboot back into windows. 

Hoody hoo! Windows sees 19.9 gigs!

---

### Post by darco on 2009-07-03
I know this is an old thread but I wanted to let others know how simple it is to add new hdd space...the original question may have been how to "expand" the hdd but this is the same to me...

Running Linux Mint w/vmware workstation 6.52
My initial hdd was 24 gigs running Win 7....realized later it was a tad too small. All I did was power off the VM. Went to VM/settings. In the Hardware tab, clicked on Add.Chose the hard disk drive option, chose create a new virtual disk. Chose SCSI. Entered the new disk size. Started up the vm. Went to Disk Management in Win 7. Saw the newly created partition, formatted it and that was it! Too easy

darco

---

### Post by ant2ne on 2009-07-06
darco, what you describe is adding another disk, increasing a disk size. Also windows 7 (and windows vista) have more advanced partitioning tools built in. Vista claims to be able to resize a partition without loosing data.

---

### Post by darco on 2009-07-14
ok, my bad. I read the thread to quickly and was thinking "why are they making it so hard for themselves?". Adding a new disk was easy but not the solution you were looking for.
Well today I wanted to upgrade my Win7 to the RTM 7600 and realized my disk was too small!...Now I am in your shoes, adding a new drive wont help.

Ran this command:

```
vmware-vdiskmanager -x 36GB "Windows 7.vmdk"

```

Booted into Win7 and again went right to Disk Management in Win7, saw the unallocated space, right click and chose "expand disk"...didnt even reboot and the extra space was there...now I am upgrading to RTM...

darco

---

