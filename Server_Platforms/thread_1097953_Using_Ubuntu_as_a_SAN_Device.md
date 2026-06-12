---
title: "Using Ubuntu as a SAN Device"
date: 2009-03-16
forum: Server Platforms
---

### Post by Pattonj on 2009-03-16
I am trying to set up a ISCSI SAN using UBUNTU 8.10. I have it set up and had many issues along the way.  When I first installed it would not boot so I had to run Grub and that got it to boot then but I am continuing to have problems with the Network Bonding as I am unsure exactly how to set it up.  Then every time I am testing and disconnect all network interfaces it crashes and I can not reconnect back to the VM WARE server. I was able to reboot both the Ubuntu SAN and VMWare and it worked but tryed it again and it lost all of my config files on the Windows server. not sure if it is a issue with my setup or just windows. Any assistance or information would be extremely helpful?

 We are currently Running Ubuntu on a Dell 2650 Raid5 then have a ESXI set up on a Dell 2950 and wanting to create servers on it to run Exchange and SQL.  Also would be interested if any one is running UBUNTU as SAN in a production environment.

Thank you for any information you can provide.

---

### Post by bitbud on 2009-03-18
I use Ubuntu regularly as an iSCSI SAN and find it to be quite stable and performs well.  I'd recommend using the 8.04 LTS 64-bit version, as the 8.10 version is a little cutting-edge for server use (my opinion), and will only be supported for 18 months.

I use LVM to manage the target volumes, and use the iSCSI Enterprise Target package to share targets.  I am also using network bonding for redundancy and increased bandwidth.  Fairly standard hardware with Intel Gigabit NICs and a mix of 3Ware RAID controllers and LSI.  I've blogged about some of it at bitbud.com , which may or may not be helpful.

---

### Post by basketcase on 2009-03-18
> **bitbud said:**
> I use Ubuntu regularly as an iSCSI SAN and find it to be quite stable and performs well.  I'd recommend using the 8.04 LTS 64-bit version, as the 8.10 version is a little cutting-edge for server use (my opinion), and will only be supported for 18 months.

I use LVM to manage the target volumes, and use the iSCSI Enterprise Target package to share targets.  I am also using network bonding for redundancy and increased bandwidth.  Fairly standard hardware with Intel Gigabit NICs and a mix of 3Ware RAID controllers and LSI.  I've blogged about some of it at bitbud.com , which may or may not be helpful.

Great article!  I've been itching to do something like this.  I though I would use Open Solaris and ZFS but I might have to give Ubuntu a shot.

---

### Post by windependence on 2009-03-18
Much easier to just use FreeNAS. 

[http://www.freenas.org/](http://www.freenas.org/)

Open source. GUI web interface. They even have a zfs version. Does NFS, SAMBA, iSCSI, and others.

Even better, runs on FreeBSD. Stable as hell.

-Tim

---

