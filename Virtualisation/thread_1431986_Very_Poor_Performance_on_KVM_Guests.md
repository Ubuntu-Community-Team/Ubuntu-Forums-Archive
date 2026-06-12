---
title: "Very Poor Performance on KVM Guests"
date: 2010-03-17
forum: Virtualisation
---

### Post by clotterm on 2010-03-17
Hi, I'm currently doing some tests on the KVM performance of the guest system (esp. referring the I/O performance) in order to measure the difference between the expandable disc devices (qcow2), block devices (raw) and the influence of the paravirtualization (virtio) on the guest performance. The difference between the performance of the host machine and the guest systems is really enormous (measured with bonnie++), i.e. factor 10 in-between. The performance lacks especially on writing.

Well, here are my specs:

System: Intel Core2Duo T8300 (with vmx flag), 4GB RAM, quite fast SATA2 HDD OS: Ubuntu 9.04 64bit (Host), Ubuntu 8.10 32bit (Guest)

Regarding the host system: all required modules have been loaded successfully (i.e. kvm and kvm-intel) and all referring packages have been installed (libvirt0, qemu-kvm, aso). When instantiating the guests no error occurs.

Steps how the images have been created and instantiated:
```
kvm-img create -f qcow2 name.img 8G #which creates the image
kvm -m 512 -cdrom blah.iso -drive file=name.img,ifname=virtio -net nic -net user #in order to install the guest system into the image
```

After that the guest has been rebooted and bonnie++ has been started to figure out the performance.

All steps have been performed on two different systems (both had all modules loaded successfully).

Do you have an idea what went wrong during the steps I performed above?

BR clotterm

---

### Post by ibuclaw on 2010-03-17
> **clotterm said:**
> Hi, I'm currently doing some tests on the KVM performance of the guest system (esp. referring the I/O performance) in order to measure the difference between the expandable disc devices (qcow2), block devices (raw) and the influence of the paravirtualization (virtio) on the guest performance. The difference between the performance of the host machine and the guest systems is really enormous (measured with bonnie++), i.e. factor 10 in-between. The performance lacks especially on writing.

Well, here are my specs:

System: Intel Core2Duo T8300 (with vmx flag), 4GB RAM, quite fast SATA2 HDD OS: Ubuntu 9.04 64bit (Host), Ubuntu 8.10 32bit (Guest)

Regarding the host system: all required modules have been loaded successfully (i.e. kvm and kvm-intel) and all referring packages have been installed (libvirt0, qemu-kvm, aso). When instantiating the guests no error occurs.

Steps how the images have been created and instantiated:
```
kvm-img create -f qcow2 name.img 8G #which creates the image
kvm -m 512 -cdrom blah.iso -drive file=name.img,ifname=virtio -net nic -net user #in order to install the guest system into the image
```

After that the guest has been rebooted and bonnie++ has been started to figure out the performance.

All steps have been performed on two different systems (both had all modules loaded successfully).

Do you have an idea what went wrong during the steps I performed above?

BR clotterm

Well, don't expect miracles with a virtual machine. ;)
And yes, I/O performance is not that great, especially if you are writing lots of tiny files to the virtual disk.

Never thought to look into it in a VM, but I usually suggest to people on a host computer to play about with the scheduler of the OS if I/O performance is not up to scratch.

```
echo deadline > /sys/block/sda/queue/scheduler
```
Valid options are: noop, deadline, anticipatory and cfq (which is the default).

Regards
Iain

---

### Post by TheFu on 2010-03-17
I've found qcow2 performance to be very slow too. If you convert to a raw image, the disk performance is substantially better.
You didn't mention where you placed the img file. Is it on a different disk, extern array with striping, SAN or iSCSI storage?

I've never used the virtio under KVM, so I can't help with that.  I did find that the default NIC emulated was just 10BT. By specifying e1000, a GigE NIC is emulated. "User mode" networking is known to have really poor performance too. You need to setup a bridge before trying this on the Dom0/Host.

sudo kvm -m 512 -net nic,model=e1000,macaddr=00:11:22:33:44:70 -net tap -usbdevice tablet -hda Xubuntu.img

Good Luck.

---

### Post by clotterm on 2010-03-17
Well I tried it that way again. The performance is slightly better, but still really bad. I monitored the CPU load with htop (of the host machine( and during the tests the cpu load of the kvm process toggled from almost 0% up to 90% all the time. Seems like there's something wrong in the host?! Any suggestions what device doesn't run correclty?

---

### Post by benderisgreat on 2010-03-17
if you're looking for i/o performance why don'y you pass a logical volume as a drive to the guest? (instead of an image file on a filesystem)

---

### Post by TheFu on 2010-03-17
I'd like to help, but I can't tell anything about your system from what you've provided. If you could describe your physical and logical disks in relation to where the image is located. That would be a help.

For example, I saw high CPU (50% on 1 CPU) use when I used qcow2 on a VM without much use. Then I converted that file back to raw and CPU use dropped to around 1% on 1 CPU) when the VM wasn't busy. My host OS is on a single SATAII disk with EXT4 formatting and the image file is located on an externally attached RAID5 disk array (JFS format) connected via infiniband (don't get me started) for both of my tests.  No LVM or LVM2 used.  My box also has 4.7GB of RAM that appears is being used for disk cache according to vmstat.

---

### Post by clotterm on 2010-03-18
Thanks for your replies so far;

@benderisgreat: Well the reason why I need images on a filesystem is that I want to use Eucalyptus and that requires images and is unfortunately not able to instantiate images from LVMs.

@ TheFu: Ok, my configuration is not much different to yours. My physical machine has a SATA2 disk also with EXT4 format. The images are located on another system drive (which is also SATA2 and EXT4). I tried it with qcow2 images (formatted in both ext3 and ext4) without any difference -> Very poor performance.
Then I switched to raw block images and the performance improved _a little_ (we're still talking about a I/O performance difference of a factor of 6 between the physical machine and the guests).

---

### Post by TheFu on 2010-03-18
> **clotterm said:**
> 
@ TheFu: Ok, my configuration is not much different to yours. My physical machine has a SATA2 disk also with EXT4 format. The images are located on another system drive (which is also SATA2 and EXT4). I tried it with qcow2 images (formatted in both ext3 and ext4) without any difference -> Very poor performance.
Then I switched to raw block images and the performance improved _a little_ (we're still talking about a I/O performance difference of a factor of 6 between the physical machine and the guests).

Is "another system drive" just another internal disk? 
** How large is your disk cache?**
Can you post the script you used to build the disk image and VM (any strange install options)?
That might help someone see an issue.  

I agree with you that "use LVM" isn't an option.  Using Xen on another machine for 2yrs without LVM on a single disk with "full" images (not sparse) and had no performance issues since switching from sparse. That C2D box runs 6 VMs with CRM, Zimbra, Project Management, Alfresco, LDAP, Web, Wiki, and VPN servers. I expect to get KVM doing the same once 10.04 LTS is out.

---

### Post by ibuclaw on 2010-03-18
> **clotterm said:**
> Thanks for your replies so far;

@benderisgreat: Well the reason why I need images on a filesystem is that I want to use Eucalyptus and that requires images and is unfortunately not able to instantiate images from LVMs.


Why don't you instead use a "Linux-on-Linux" virtualisation without the Virtual Machine, such as OpenVZ or LXC?

If you would prefer future support, LXC will be the one that you'll want to go for. Have a look at this thread for loose documentation, etc. [http://ubuntuforums.org/showthread.php?t=1382823](http://ubuntuforums.org/showthread.php?t=1382823)

Regards
Iain

---

### Post by vkeven on 2010-03-21
Samething here almost 1/6 perfo of host machine , maybe the REAL Redhat version is faster but you need to pay 499$ to know it

---

### Post by uljanow on 2010-03-21
kvm uses writethrough for qcow2 by default which causes some performance issues. Try "-drive file=hda.img,index=0,cache=writeback,media=disk" instead of "-hda hda.img".

---

### Post by ibuclaw on 2010-04-03
> **uljanow said:**
> kvm uses writethrough for qcow2 by default which causes some performance issues. Try "-drive file=hda.img,index=0,cache=writeback,media=disk" instead of "-hda hda.img".

Thanks for this. :)

---

### Post by nutznboltz on 2010-04-05
> **clotterm said:**
> OS: Ubuntu 9.04 64bit (Host), Ubuntu 8.10 32bit (Guest)

Try 9.10 guest with virtio on 9.10 host for better I/O performance.

---

### Post by Spenser_Gilliland on 2011-05-05
Just wanted to post about this.  

I performed the change from write-through to write back and my performance increased from 5 MB/s to 94.3 MB/s.  About 20x difference, there's even an option in Libvirt.  Now just to figure out how to make this the default.

Spenser

---

### Post by agent8131 on 2011-05-07
Anyone reading this should be made aware that using writeback caching can result in a corrupted filesystem on your guest if the virtual machine is ever shutdown uncleanly (which is not uncommon for kvm).  In other words, don't do this for any system where the data is important.

---

### Post by agent8131 on 2011-05-08
I did some research on KVM on the server.  I decided very quickly that KVm was far inferior to Xen with regard to stability and performance.  however, what I did learn about KVm performance I might as well share:

* for stability and performance only run guests with 1 CPU
* pin that 1 CPU to a physical CPU

Believe it or not this helps both CPU and IO performance, which should tell you something is wrong.

---

### Post by Dedoimedo on 2011-05-08
Several options are possible:

Using a separate and fast disk.

Preallocate virtual disk space.

Use a "fast" filesystem for storing virtual machines, but beware data loss due to some of the possible options.

Playing with block size on host and inside guest filesystem might help, but only if you know what specific workloads you will have and if you match them; the same applies to io scheduler.

You may also want to change the readahead size and number of requests, but again, this tweaking could be dangerous and might only work with specific workloads.

Set swappiness ratio in your guess to a low value, but it won't help you if you max. the virtual machine memory resources.

You may want to consider using control groups if you have multiple machines fighting for resources.

Regards,
Dedoimedo

---

### Post by jebus_beler on 2011-12-13
I'm using KVM on ubuntu server 11.10 with a JeOS guest (also ubuntu server 11.10) and a qcow2 disk image and am noticing a similar very strange slow down.  While syncing a large file from another host on the network with the VM I found the latter to slow down a huge amount.  Moreover neither the network not the CPU or ram of the host are being strained so I can only assume its the disk.  Is switching from qcow2 to another format likely to buy me much?

The strange thing is that this review, which admitedly was not disk focused, seems to suggest KVM doing extremely well on disk performance (as compared to other virtualization options):

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1110_xenkvm&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1110_xenkvm&num=1)

Could the difference be in the kind of image he was using?  It doesn't seem like he was using the write-through option.  Any suggestions on getting better disk access?

EDIT: my hardware and setup are quite similar to the original posters except I'm using 11.10.

---

### Post by collisionystm on 2011-12-13
> **clotterm said:**
> Hi, I'm currently doing some tests on the KVM performance of the guest system (esp. referring the I/O performance) in order to measure the difference between the expandable disc devices (qcow2), block devices (raw) and the influence of the paravirtualization (virtio) on the guest performance. The difference between the performance of the host machine and the guest systems is really enormous (measured with bonnie++), i.e. factor 10 in-between. The performance lacks especially on writing.

Well, here are my specs:

System: Intel Core2Duo T8300 (with vmx flag), 4GB RAM, quite fast SATA2 HDD OS: Ubuntu 9.04 64bit (Host), Ubuntu 8.10 32bit (Guest)

Regarding the host system: all required modules have been loaded successfully (i.e. kvm and kvm-intel) and all referring packages have been installed (libvirt0, qemu-kvm, aso). When instantiating the guests no error occurs.

Steps how the images have been created and instantiated:
```
kvm-img create -f qcow2 name.img 8G #which creates the image
kvm -m 512 -cdrom blah.iso -drive file=name.img,ifname=virtio -net nic -net user #in order to install the guest system into the image
```After that the guest has been rebooted and bonnie++ has been started to figure out the performance.

All steps have been performed on two different systems (both had all modules loaded successfully).

Do you have an idea what went wrong during the steps I performed above?

BR clotterm

This is why XEN exists....

---

### Post by jebus_beler on 2011-12-13
> **collisionystm said:**
> This is why XEN exists....

Well according to the article I linked to KVM outperforms XEN pretty consistently on Ubuntu 11.10.

An update on my problem.  I think its actually a Unison problem when using large files rather than a KVM problem.  When I switch to manually ssh files I get ~10mb/s over the network so the network is the limiting factor not any disk access on the VM.  Sorry for the confusion.

---

### Post by josir on 2012-03-10
Hi Jebus, 

I have the same problem here. Host network card is 1Gb (overall 30Mb/s) and guest network speed is 10Mb/s at maximum.

Did you find a solution for the slow networking on kvm guest ?

Josir.

---

