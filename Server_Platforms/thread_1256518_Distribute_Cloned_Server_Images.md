---
title: "Distribute Cloned Server Images"
date: 2009-09-02
forum: Server Platforms
---

### Post by Lambchopper on 2009-09-02
I've got a working Ubuntu 9.04 server and I'm looking to image it to distribute it to other offices.  I'm new to imaging on the Ubuntu plateform.

To start here's what I'm working with starting with the df output:

```
...@CHI-CAPPORTAL:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/CHI--CAPPORTAL-root
                       71G  701M   67G   2% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M   76K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  136K  497M   1% /dev
tmpfs                 497M     0  497M   0% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-server/volatile
/dev/sda5             228M   14M  203M   7% /boot

```

And here's the partitions:

```
...@CHI-CAPPORTAL:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b7cf071

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9695    77875056   8e  Linux LVM
/dev/sda2            9696        9726      249007+   5  Extended
/dev/sda5            9696        9726      248976   83  Linux

```

If I use the dd if=/dev/sda of=<Some Image File> will that capture all the partions?  Also will the target HDD need to be the exact same size?

I won't know the destination HDD size because the remote offices are providing their own gear.  So my drive image needs to work regardless of the destination HDD size.  So any suggestions are welcome.

Thanks!

---

### Post by HermanAB on 2009-09-02
Howdy,

Yes, you can do that, but it is not really a good way to replicate servers anymore - it is a 20th century solution and we are already almost a whole decade into the 21st century.

Your first problem is that your sever file systems should be encrypted and if they are encrypted, then the images won't compress, so the images will be enormous.  The second problem is that Udev notes the MAC address of the serial port in the rules and that is unique to each server.  So images do not work so hot.

If however, you install VMware Workstation or VMware ESX on each machine and install the server as a VM, then you can easily replicate them by simply making a tar ball of the VM directory.  The trick with VMs is to keep the data OUTSIDE the VM on a NFS share.  That way, you can keep the VM itself small.

---

### Post by bear24rw on 2009-09-02
I have no idea about imaging but maybe it would be easier to make a script to remove/install needed packages and then you can sync the config files?

---

### Post by HermanAB on 2009-09-03
Automated installs are done with Redhat Kickstart.  There is a version available for Ubuntu as well.  Some Googling will find it.

---

### Post by Lambchopper on 2009-09-03
> **HermanAB said:**
> Howdy,

Yes, you can do that, but it is not really a good way to replicate servers anymore - it is a 20th century solution and we are already almost a whole decade into the 21st century.

Your first problem is that your sever file systems should be encrypted and if they are encrypted, then the images won't compress, so the images will be enormous.  The second problem is that Udev notes the MAC address of the serial port in the rules and that is unique to each server.  So images do not work so hot.

If however, you install VMware Workstation or VMware ESX on each machine and install the server as a VM, then you can easily replicate them by simply making a tar ball of the VM directory.  The trick with VMs is to keep the data OUTSIDE the VM on a NFS share.  That way, you can keep the VM itself small.


Thanks.  However, imaging will be the best solution in this case.  The servers I'm deploying are Gateway devices for a Captive portal solution.  They act as Routers and will be used in a corporate environmnet.  VMWare isn't a solution because of a number of reasons, one of which is cost.  

Encryption is also not an issue as I'm not encrypting the file system since proprietary data will not reside on these units.  They are a low security risk.  So compression shouldn't be an issue.

How can I go about getting Udev to redetect the MAC addresses that you mention?

For me to design scripts and Kickstart installations for what is essentially 7 Servers would take more time than to just install them manually.

---

