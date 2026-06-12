---
title: "HOWTO: Ubuntu Server iSCSI for ESXi Server"
date: 2008-09-11
forum: Server Platforms
---

### Post by trmentry on 2008-09-11
This is a very crude how-to on getting the now free [VMWare ESXi](https://www.vmware.com/tryvmware/login.php?eval=esxi&t=1) server working with iSCSI to an Ubuntu Hardy Server.

First, let's setup the ubuntu server.

```

sudo apt-get install iscsitarget

```

Once that's done... edit your /etc/ietd.conf file.  I commented out all that was in there and put in the following 2 lines:

```

TARGET iqn:2006-03.com.example:hoth-esx
      Lun 0 Path=/dev/hoth-vg0/esx,Type=fileio

```

Restart the iscsi server

```

sudo /etc/init.d/iscsitarget restart

```


Once that's done, need to setup the ESXi server.  Open up Virtual Infustructure Client and go to the CONFIGURATION tab of your ESXi host.  Click on STORAGE ADAPTERS on left.  Scroll down to the iSCSI adapter on right and click on PROPERTIES.  

In the window that pops up, click on the GENERAL tab and then CONFIGURE, then tick the ENABLE box.  This will then have your host generate it's iqn.  

Next click on the DYNAMIC DISCOVERY tab.   Add your server in there.  Click ok back to the STORAGE ADAPTERS and rescan.  You should see the Lun0 being presented from your Ubuntu server.  (see attachment 1)

Now click on STORAGE on the left.  Then click on ADD STORAGE in upper right.  Follow the wizard.... you're looking for Disk/LUN to start with.  (see attachment 2)

Once that's complete... your ESXi host will have the iSCSI mounted and you can then create a vm on your host and have it store the vm on your ubuntu server.  

This is handy in case your host fails... you can reinstall it, and repeat this process and then imprt your vm's without having to reinstall them.  (I've not tested this though.)

Enjoy.

---

### Post by Vegan on 2008-09-11
One problem, no GUI on the server. So how about the console methods.

---

### Post by trmentry on 2008-09-11
> **Vegan said:**
> One problem, no GUI on the server. So how about the console methods.

If you need to get the client for esx... point a browser to http://<your esxi host>  and download the client.  Yes, it's windows only unfortunately.  If you're wanting to setup esxi via cli... good luck... esxi doesn't support cli out of the box.  there are work arounds for that, but that is above the scope of this doc.  and highly unrecommended as everything in esxi can be done via the client.

ESXi is a standalone hypervisor OS.  It is not an application/service like vmware server.. You don't install ESXi onto Ubuntu.

 

If you were meaning console methods on the ubuntu server.  my server is headless... and I did it all above via cli.  The screenshots are from the esx client.  The esxi config is from the client.  Everything else is command line in ubuntu

---

### Post by cbreaker on 2008-10-12
Yea, I'm not a big fan of ESXi to tell you the truth.   It's the same as ESX - same kernel, same Linux base.   They just removed everything not absolutely essential to the operation of the server.

It limits what you can do with it; one of the great things about ESX is that you can do a lot within the service console.

However, ESXi is capable of doing everything that ESX can do on the VMware side.  It is capable of Vmotion, DRS, HA, etc.   And, ESXi is free - but only without all the goodies.

VMware ESX Enterprise licenses with Virtual Center is so incredibly expensive that it's a hard sell for many of our customers.   Almost everyone (including a lot of the schools and small businesses we handle) is looking to Virtualize, but the cost..

For instance, to put together a complete VMware system with six sockets (say, three dual-socket hosts) with Virtual Center and Enterprise ESX licenses, it's going to cost you over $25,000.  That's more than the cost of all three hosts combined (at least with HP hardware; probably the same with Dell, etc.)   ESXi saves you no dollars with a complete system.

I really hope that VMware seriously considers lowering prices significantly, because if they don't people will start to really buy into alternatives.   Xen based systems make great alternatives now - with a Xen system you can do a lot of what Enterprise ESX can do - Hot migrations, resource balancing, high availability, and actually has a few additional tricks up it's sleeves.   I still prefer VMware at this point because of things like the Site Recovery Manager.. but we might start offering a low-end solution to some of our really small clients based on Virtual Iron soon.

Anyways, I didn't mean to go off on a tangent =)   iSCSI with VMware works really well, but don't write-off NFS either.   NFS with VMware is actually very high performance and can give you some unique abilities - like being able to access the datastore directly from non-ESX hosts - anything that can access NFS exports.   You can even use the Windows NFS server and get some really decent performance with it; providing you can get through the permissions hell because of the VERY poor Microsoft documentation..  That way you could use any VSS backup tool to back up the VM's directly without VCB or agents on the VM's.

---

### Post by windependence on 2008-10-12
> **trmentry said:**
> If you need to get the client for esx... point a browser to http://<your esxi host>  and download the client.  Yes, it's windows only unfortunately.  If you're wanting to setup esxi via cli... good luck... esxi doesn't support cli out of the box.  there are work arounds for that, but that is above the scope of this doc.  and highly unrecommended as everything in esxi can be done via the client.

ESXi is a standalone hypervisor OS.  It is not an application/service like vmware server.. You don't install ESXi onto Ubuntu.

 

If you were meaning console methods on the ubuntu server.  my server is headless... and I did it all above via cli.  The screenshots are from the esx client.  The esxi config is from the client.  Everything else is command line in ubuntu

Actually, you can run commands in ESXi using RCLI, but why would you want to? Just admin it from a different box like everyone else does. You only need ONE Windoze box for that and almost every PC you  buy today comes with Windoze installed whether you like it or not.

[http://www.virtualizationadmin.com/articles-tutorials/vmware-esx-articles/general/vmware-esxi-server-compare-esx-server.html](http://www.virtualizationadmin.com/articles-tutorials/vmware-esx-articles/general/vmware-esxi-server-compare-esx-server.html)

[http://virtualrw.blogspot.com/2008/07/vmware-rcli-commands-for-esx-i.html](http://virtualrw.blogspot.com/2008/07/vmware-rcli-commands-for-esx-i.html)

[http://www.virtualtroll.com/?p=115](http://www.virtualtroll.com/?p=115)

I do agree that ESX is overpriced but IMHO it's the best you can get right now.

-Tim

---

### Post by lucaspr on 2008-11-06
Almost a great guide ;) Only thing is it gave me an error: /dev/hoth-vg0/esx not found -2

A little research revealed that a file or disk has to be attached at that point.. I followed this([http://www.aspdeveloper.net/tiki-index.php?page=LinuxiSCSITargetOnUbuntu]("http://www.aspdeveloper.net/tiki-index.php?page=LinuxiSCSITargetOnUbuntu")) little guide and was able to restart the service again!

With a file of 2 gigs that was, small but only for testing purposses! 
And a little mistake?
```

TARGET iqn:2006-03.com.example:hoth-esx
      Lun 0 Path=/dev/hoth-vg0/esx,Type=fileio

```
Shouldn't that be:
```

TARGET iqn.2006-03.com.example:hoth-esx
      Lun 0 Path=/dev/hoth-vg0/esx,Type=fileio

```
(notice the : and . difference after the iqn)
Don't know much about iSCSI yet, so it could be fine, I just saw the little difference in the guide and the example in the /etc/eitd.conf file...

---

### Post by chrislouden on 2009-01-29
Trying to get this working with software RAID 5, not having any luck.

Lun 0 Path=/dev/md0,Type=fileio does not work, but if i specific any disk individually it does for example Lun 0 Path=/dev/sdb,Type=fileio

Suggestions?

---

### Post by mwilliamsr on 2009-02-11
> **chrislouden said:**
> Trying to get this working with software RAID 5, not having any luck.

Lun 0 Path=/dev/md0,Type=fileio does not work, but if i specific any disk individually it does for example Lun 0 Path=/dev/sdb,Type=fileio

Suggestions?

Create a LVM volume on the array...  Create single or multiple partions on the array, the create Volume Group(s) (vg)....  This will enable the target to see them....  Some links that may point you in the right direction....

[http://opensourceexperiments.wordpress.com/2008/05/03/a-poor-mans-guide-for-creating-iscsi-targets-without-using-external-usb-hard-disks/]("http://opensourceexperiments.wordpress.com/2008/05/03/a-poor-mans-guide-for-creating-iscsi-targets-without-using-external-usb-hard-disks/")
[http://www.linuxconfig.org/Linux_lvm_-_Logical_Volume_Manager]("http://www.linuxconfig.org/Linux_lvm_-_Logical_Volume_Manager")

---

### Post by netkom on 2009-11-10
Works for me on a Software RAID5.
```

cat /etc/ietd.conf |grep -v '#'

Target iqn.2006-03.com.example:nas.iscsi1
        Lun 0 Path=/dev/md0,Type=blockio

```

---

### Post by zevans on 2009-11-16
[ignore - I had the wrong kernel loaded :-) ]

---

### Post by fosheezy on 2009-11-16
> **cbreaker said:**
> 

VMware ESX Enterprise licenses with Virtual Center is so incredibly expensive that it's a hard sell for many of our customers.   Almost everyone (including a lot of the schools and small businesses we handle) is looking to Virtualize, but the cost..

For instance, to put together a complete VMware system with six sockets (say, three dual-socket hosts) with Virtual Center and Enterprise ESX licenses, it's going to cost you over $25,000.  That's more than the cost of all three hosts combined (at least with HP hardware; probably the same with Dell, etc.)   ESXi saves you no dollars with a complete system.


Why would a small business NEED the enterprise version? you can purchase vmware licenses for 3 servers (2 sockets each) for $5,000 with 3 years of support (link below). A true small business does not need vmotion. You can just as easily power off a VM, and power it back up on another host if you need to. I've been using ESXi at my company for 6 months, running an Exchange server and A terminal server (2008 64bit each). No problems. We're about to P2V our other server and install ESXi on it and setup a central SAN for the two.

[http://store.vmware.com/servlet/ControllerServlet?Action=DisplayPage&Env=BASE&Locale=en_US&SiteID=vmware&id=ProductDetailsPage&productID=126841300&resid=MLLr-goBAkgAAA1fCQcAAAAq&rests=1258433068312](http://store.vmware.com/servlet/ControllerServlet?Action=DisplayPage&Env=BASE&Locale=en_US&SiteID=vmware&id=ProductDetailsPage&productID=126841300&resid=MLLr-goBAkgAAA1fCQcAAAAq&rests=1258433068312)

---

