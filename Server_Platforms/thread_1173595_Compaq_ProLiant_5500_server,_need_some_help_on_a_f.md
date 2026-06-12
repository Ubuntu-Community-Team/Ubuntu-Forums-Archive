---
title: "Compaq ProLiant 5500 server, need some help on a few things..."
date: 2009-05-29
forum: Server Platforms
---

### Post by zetsumei on 2009-05-29
I got a Compaq ProLiant 5500 server and I'm looking to get a working web, mail, ftp, dns, dhcp, etc server going on it.  It's got 4 processors at 550mhz each, 768mb of RAM and 10 18gb scsi drives in RAID.

I had Ubuntu 8.04 LTS on it and didn't much like it as I wanted to go with something I knew more so I went with Arch.  Everything went fine until I get to the GRUB install.  I go in and check all my paths and then tell it to install GRUB to the c0d0 and c0d1 since their in RAID and then it tells me there's a missing or invalid root: device.

And if anyone could help me get this working on Arch, I'd be really happy.  If not, would Ubuntu Server 9.04 be a good choice for something like this?

---

### Post by cariboo on 2009-05-30
I would suggest you have a look at dnsmasq if you are only running a small network. Setting up Bind9 properly can be a large hassle. 

This is the Ubuntu forums, of course we are going to recommend Ubuntu over Arch.

---

### Post by windependence on 2009-05-31
Personally, I would run VMware ESXi (not server) directly on the hardware and then you could run Ubuntu and Arch on the same box depending on what app you are running on it. You should not be running all that stuff on one box anyway.

ESXi should run fine on your SCSI drives, but you probably will need more RAM. One tip, you do not normally want to give your VM as much RAM as you would a physical machine because the hypervisor does a good job at managing shared memory, especially on similar or identical operating systems. With a little more memory, you could easily run 10 VMs on that box.

-Tim

---

### Post by Wim Sturkenboom on 2009-05-31
I'm not familiar with grub, so can not really help you.

Maybe [http://www.megalinux.net/?s=dl380](http://www.megalinux.net/?s=dl380) (slackware on DL380) might point you in the direction; it contains a small piece about a 'modification' to the lilo configuration (steps 45 and 46) that probably is applicable (after translation to grub)
Else install Ubuntu, check the grub afterwards, install arch and apply the changes.

WimS

---

