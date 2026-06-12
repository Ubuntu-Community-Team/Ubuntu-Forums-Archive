---
title: "No permission issue after creating new partition"
date: 2014-07-18
forum: Virtualisation
---

### Post by deme2 on 2014-07-18
My 15G partition inside VMWare is full, so I booted from DVD and try to increase using GParted. My intentio were to extend from 15 to 17GB and then create one extra partition.
1 - is it possible to extand my main partition without deleting the files from there? I guess not.
2 - while creating second partition, why I can't use it even I do see it in my devices?
Because I am very new in Ubuntu I uploaded two images to show what I am doing.

---

### Post by TheFu on 2014-07-18
Which VMware? They make many different hypervisors.

How is the storage provided by the hostOS to the client?  file, partition passthru, iSCSI, disk controller passthru, something else?

Generally, for virtual machine storage, there are 3 main steps to making more storage available inside the VM. 
* Shutdown the VM
* make the virtual HDD larger (multiple ways to do this) - this is done at the hostOS level
* boot up the VM off any live-CD (not the clientOS), and use a partitioning tool to increase the size of the partition (gparted can do this); cannot boot into the VM using the normal boot method because that makes the partition you want to resize "in-use", so it cannot be modified.
* inside the VM, use resize2fs to resize a running file system as needed.

Of course, you could have used LVM inside the VM - so those steps are more complicated, but if you selected LVM, then I'd think RTFM would work.  For virtual machines, I don't use LVM **inside** the VM.  Definitely use LVM on the hostOS, but the added complexity hasn't been useful inside for me.

I hope this all makes sense.  Without more specifics about YOUR situation, can't provide any more specific steps, sorry.

Oh ... and existing files shouldn't be harmed in anyway doing this, but when messing with partitions, bad things can/and do happen. Make a backup first and hope you don't need it.

Or ....
You could create a new larger partition and move files into it using whatever liveCD you like.  dd, tar, fsarchive, rsync and a number of other tools can be used to accomplish this.  Oh ... and almost any competent backup software too.

Or ....
You could add another new partition to the VM and move some of the files from key locations into in, being certain to mount the new partition over the directory that you migrated the files from.  Probably not too safe for someone new to Linux, but relatively easy. I've done this a few times.

So .... from your description, I think you missed the 1st step to make the virtual-HDD larger first.  You were close, which is great.

---

### Post by deme2 on 2014-07-18
Firstly, thank so much! I can see you spent energy trying to help me.
I have no idea what you mean by:
1 - "resize2fs". Is this a tool or partition format like NTFS? 
2 - LVM inside the VM 
3 - RTFM 


I am not very good in Linux, so let's tell each step I took:
0 -My VM is shutted down and my virtual HDD was done larger
1 - First I downloaded Ubuntu Iso
2 - Second I pointed DVD from my VMware Player (6.0.3 build-1895310) to such ISO file
3 - I entered an option to delay the boot in order to see Esc/F2 options
4 - I clicked in Play Virtual machine (I just have one VM)
5 - Click ESC and choose DVD boot
6 - I clicked in Try without installing
7 - starts Gparted
8 - if you look at the image you will see that I can't increase the size (red circled)
9 - and when I start the VM I don't have access to the second partition I created.


I do want to do this: "You could add another new partition to the VM and move some of the files from key locations into in". Obviously I will not do this with folders I don't know the purpose. Imagining I was doing the same thing in Windows with only one physical HD: I would have a C drive and a D drive partition. I am a Java Developers, so some sample codes, MP3 and photos I could paste in D drive for instance and don't worry much about this if one day I need to reformat D.
[IMG]D:\Temp\details.png[/IMG]

---

### Post by deme2 on 2014-07-18
I think that the image I try to upload is not being showed. What I would trying to show in the image is, I clicked in /dev/sda1, clicked in Resize/Move, and I try to increase New Size (MIB) but it is not allowed. 
Do you know if this might be caused because I m not running as root? If so, how can I run Gparted as root. If I type sudo Gparted I can't open it. Last possibility: should I have to run Gparted from DVD ([https://help.ubuntu.com/community/GParted)?](https://help.ubuntu.com/community/GParted)?)

---

### Post by TheFu on 2014-07-18
Create a new virtual-HDD ... that is another hard disk, not a new partition in the existing vHDD.  Then inside that NEW vHDD, create a new partition to be used for whatever purpose.  I'd move my /home into it using the live-CD.  Having /home on a dedicated partition is a "best practice".  Be certain to update the /etc/fstab so this happens at boot and goes to the correct place.  

The issue is that you are using extended partitions inside the client with swap and some other partition inside it.   Don't do that, it just makes life harder for zero gain. While any partitions are being used, the extended partition can't be corrected.  In Linux, swap partitions are automatically used.  Clear out those 2 partitions inside the extended partition (backup any data first) and then delete them and the extended partition too. It isn't helping you. Use primary partitions, if that is your need, but I'd just extend the existing one into the space that the current primary partition is using.

Linux is NOT Windows.  Especially when it comes to hard disk management, they have very different philosophies. D: means nothing.  Any directory can be used as a mount point under Linux at any level. PC BIOS may have a limit of physical HDDs, but not the OS.  I've seen UNIX systems with hundreds of physical HDDs mounted.  

The answers to your other questions are google-able. You'll learn much more that way than me providing a snippet of info.

---

