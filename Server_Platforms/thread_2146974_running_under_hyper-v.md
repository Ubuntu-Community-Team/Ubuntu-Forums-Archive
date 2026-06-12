---
title: "running under hyper-v"
date: 2013-05-20
forum: Server Platforms
---

### Post by Vegan on 2013-05-20
finally have Ubuntu working with > 127 GB worth of storage, now I have it up to 2040 GB. Had to use the old VHD format. Seems to be some problem with VHDX compatibility, hopefully the next version can get around to that.

my current stack is LAMP, SAMBA and DNS which is pretty standard.

I have used Webmin is the past, but with Server 2012 I do not need that any more, I can access the console directly via remote desktop securely

I have some experience PHP and I have some experience with shell scripts

so how to best run this VM as a ISP where each user's home folder is their web site

then Apache can grab content from that directory as per the domain in use

so I guess the ISP needs a database, MySQL seems to still be there


also how about fixing mysql so its visible as a database to the LAN?

also running the DNS server to handle domain transfers etc?

---

### Post by linuxtechguy on 2013-05-21
You should never run so a users home dir is their website. Either use public_html folder in their home folder or create a different directory structure. But /home/username would be extremely insecure.

---

### Post by Vegan on 2013-05-21
I was thinking of jailing users as well to their home folders

all they will get is ftp access

---

### Post by Vegan on 2013-05-22
another few items come to mind, Red Hat is the only distribution Microsoft likes at the moment. I tried to install some integration components but it choked even with RPM installed.

I wonder how much work it would be to port to Ubuntu

Is it possible to disable NUMA easy and also dealing with more and more cores, one issue is using more cores.

---

### Post by rubylaser on 2013-05-22
You don't need to install the Hyper-V integration components on Ubuntu.  They have been built into the the kernel since 12.04.  You can verify this by running.

```
lsmod | grep hv
```
With the newer 3.8 kernels, the [balloon driver is built in as well]("http://askubuntu.com/questions/260589/ubuntu-12-10-guest-on-server-2012-and-hyper-v-integration-components").

---

### Post by CharlesA on 2013-05-22
Wheezy has built in support for Hyper-V too, it seems:

```
lsmod | grep hv
hv_utils               12986  0
hv_storvsc             17423  2
hv_netvsc              18304  0
hv_vmbus               32029  4 hv_netvsc,hv_storvsc,hid_hyperv,hv_utils
scsi_mod              162269  5 libata,sr_mod,sg,hv_storvsc,sd_mod

```

---

### Post by Vegan on 2013-05-25
I created a new VM this AM with 13.04 and I now have better support for dynamic memory which is very helpful when the workload exceeds expectations.

The heartbeat also is working so this leaves only the network which gripes over degraded integration components

I increased the startup RAM from 512MB to 768MB and the virtual machine seem to boot much faster. The minimum dynamic memory can remain at 512MB and Hyper-V is reallocating memory.

---

### Post by rubylaser on 2013-05-25
How have you configured the NIC for your VM? Is is a legacy adapter, etc.?

---

### Post by CharlesA on 2013-05-25
> **rubylaser said:**
> How have you configured the NIC for your VM? Is is a legacy adapter, etc.?

I can only vouch for Debian as I have installed Squeeze and Wheezy on HyperV.

Squeeze needed a legacy adapter but Wheezy was fine with a "regular" network adapter.

---

### Post by Vegan on 2013-05-25
I am using the default virtual adapter that all my virtual machines use

its the only option, as there is only 1 NIC on the host server

should I adjust the defaults for the virtual machine NIC settings? I thought the defaults in Linux were DHCP and automatic.


I tried using the shutdown button instead of su shutdown -h 0, that invoked a BUG alert so it seems that 13.04 is not super stable

---

### Post by rubylaser on 2013-05-26
I was asking how you had it configured in Hyper-V as CharlesA had mentioned above, is it a regular or legacy adapter, not how it's configured in Ubuntu :)

---

### Post by Vegan on 2013-05-27
Its setup with the defaults, only thing I have done is create vast numbers of virtual machines

the hyper-v uses the a 1000BASE-T connection to the router an that NIC is the same on that is virtualized for use by Hyper-V

the VM however thinks I have 10GBASE-T but there is no problem with that virtual adapter either. This is what the virtual instance of Windows Sever sees.

I have many virtual machines running, only was looking at how Linux works with the latest from Redmond

My Linux stack continues to be LAMP+DNS+SAMBA

---

### Post by rubylaser on 2013-05-27
I use Ubuntu 12.04 with LAMP stacks and numerous other setups on our Hyper-V 2012 boxes at work with no issues at all.  I was trying to see if you where trying to do anything out of the ordinary.

---

### Post by Vegan on 2013-05-27
The only thing is that the network adapter IP address is not seen

dynamic memory is working but increasing the startup memory was a big performance boost, more than expected

---

### Post by rubylaser on 2013-05-27
Was this i new install or a migrated VM?  I ask, because you shouldn't have been able to install without internet, and if it was a migration, it's likely that the hardware address of the interface changed, and you just need to remove the contents of /etc/udev/rules.d/70-persistent-net.rules to get it working. The lines that need to be removed look like this.  Remove them, then reboot and see if that gets it working for you.
```

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:21:12:fd:32", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

---

### Post by Vegan on 2013-05-27
It is a clean install and there was no problem installing it

each new version of Ubuntu server is installed in a fresh VM

keep in mind I created a VHD first as the wizard only uses VHDX and for some reason linux does not work

---

### Post by Vegan on 2013-05-28
I have noticed improvements from each update so I am hoping the kinks will be ironed out soon. The VM works well now, uptimes are excellent.

I can determine the IP address of the VM from the console easy

---

