---
title: "VMware server re-install issue (vmware player 3.0.1)"
date: 2010-03-10
forum: Virtualisation
---

### Post by fake_punk on 2010-03-10
Hello all,

I hope i posted this in the right section.  I am a bit of a noob, and I am having issues with my VMware server installation.

I originally installed Vmware server 2.0.2 using the instructions here:
[https://help.ubuntu.com/community/VMware/Server]("https://help.ubuntu.com/community/VMware/Server")

All worked well, until a reboot.  It didn't start up properly and told me to rerun the config.  So I did.  Everything then worked well.  I used the script there to open up the VMware player to view the VM's etc.

Well, I decided that since everything was running so well, I had to screw it up :(.  I wanted to run unity so I tried to install Vmware player 3.0.1, and it seemed to install fine.  However, when I tried to run it, it failed at stopping the services.  Also, my VMware server no longer worked.  I tried to reinstall using that script and it didn't work, it detected an older install.  So, I purged everything and removed the vmware folder as per that website, and with a reinstall I got:

make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config1/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config1/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config1/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config1/vmnet-only/smac.o
  CC [M]  /tmp/vmware-config1/vmnet-only/vnetEvent.o
  CC [M]  /tmp/vmware-config1/vmnet-only/vnetUserListener.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config1/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

So now I have no working VMWare server or player.  Ideally I would like to have both VMware server 2.0.2 and VMware Player 3.0.1 working.  Any help would be greatly appreciated.

Thanks.
Rees

---

### Post by Exca on 2010-03-10
Good evening,

2 things to check for your installation. I've encountered similar problem during my VMWare Server 2 installation.

- Did you installed your linux headers ? => sudo apt-get install linux-headers-$(uname -r)
- Run the script as root, not by doing a simple sudo. => sudo su

Good luck !

---

### Post by fjgaude on 2010-03-10
First off, I don't think on the same host you can have Server and Player installed. Remove one and see what happens.

---

### Post by fake_punk on 2010-03-11
I checked and the headers were installed.  Also, running as root gave me the same result.  I thought that when I ran these commands:

Solution: First of all, ensure that you "Completely Removed" vmware-player/vmware-server and all its modules. To ensure that, run the following command:

    sudo aptitude purge vmware-server vmware-player vmware-tools-kernel-modules

If you still keep getting the above error, run the following command:

    sudo rm -r /etc/vmware*

That would essentially uninstall all VMWare related products from my machine right?

---

### Post by fjgaude on 2010-03-11
Did you try this:

```
vmware-installer -u vmware-player
```

The later versions of vmware installer is required to easily remove a previous version of VMware.

---

