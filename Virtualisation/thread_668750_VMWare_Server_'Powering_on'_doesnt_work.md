---
title: "VMWare Server: 'Powering on' doesnt work"
date: 2008-01-15
forum: Virtualisation
---

### Post by jleaker01z on 2008-01-15
Hi!  I've read through some other posts here and havent been able to find my problem so here goes...

1st, Im running Feisty on a Sempron64 3000+ w 1g ram and NV FX6600.

Now, I have the server installed, and created my virtual machine.  But when I go to power on I get the following error:

Unable to change virtual machine power state: The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

POST(no connection): Failed to initialize monitor device.

Failed to initialize VM.

I have also ran the the Any Any patch 115 but that didnt help.  I checked the /dev/ folder and vmmon is not there.  Additionally, vmware-config.pl doesnt exist either.  There is a vmware-network-config.pl but I dont think thats what I need.  

So, where can I get these files?  I have reinstalled vmware-server with the same results...it is looking for things that arent there.

Will vmware-tools help?

Thanks

---

### Post by dcstar on 2008-01-17
> **jleaker01z said:**
> Hi!  I've read through some other posts here and havent been able to find my problem so here goes...

1st, Im running Feisty on a Sempron64 3000+ w 1g ram and NV FX6600.

Now, I have the** server installed**
.......

How?

---

### Post by jleaker01z on 2008-01-18
Using apt-get from the canonical repository.  (sudo apt-get install vmware-server, assuming canonical is in your sources.list)

For the record tho, I tried VirtualBox and it worked right off the bat. So vmware-server has been uninstalled.

---

