---
title: "File Server hardware specs?"
date: 2011-04-24
forum: Server Platforms
---

### Post by cphuntington97 on 2011-04-24
Samba server for small office. 15 users typical; provisioning for growth to 25. Mostly word and excel docs but some large images. Total data around 40GB and growing slowly. Gigabit switch but most clients 100Mbps.

Happy to pay more for better performance but don't want to waste money. Uptime important but not mission critical.

Hardware specs to shoot for?

---

### Post by kgatan on 2011-04-25
Performance wise i think pretty much anything can handle that kind of usage.
Often its either the hard drives or the power supply that gives in so id put my money there.


However, id recommend to buy a NAS device like Qnap or Readynas.

Remember to consider an offiste backup sollution as well!

---

### Post by JackRabid on 2011-04-26
One of my server machines is a 700mhz with 256m of system memory that seems to perform just fine. I'm sure you can probably find people who are running systems with less, but considering that systems better than the above are both plentiful and inexpensive, why bother with less?

As far as hard drive capacity- Currently I am running the system using LVM which allows many separate IDE drives to be seen by the system as one drive. Think Raid-JBoD. I'm using 3 HDD's I pulled off my 'shelf'o'obsolete hardware'- two 15g's and a 20g giving me a final working 'logical volume' of ~45g. If needed I can attach a fourth drive and seamlessly merge it to the existing volume group to allow me to swap in higher capacity drives if need be down the road. Periodic off-system data backup is vital when using this setup because if one of the drives in the VG go all the data is lost... I really need to look into reconfiging that machine with drive redundancy in mind...

Anyhow- anything better than 700mhz w\ 256m memory... pretty much whatever machine you have sitting around that you feel comfortable sticking in the back of some closet somewhere :)

---

### Post by headvampyre@hotmail.co.uk on 2011-04-26
if your looking to save money, you could always just buy an old server :)

i found a 1998 Dell PowerEdge 2400/733 on ebay for about £30/49.37USD :)

It works perfectly:
 - I had to find an SCSI HDD for it, but other than that
 - I added 512MB of RAM

It now works perfectly :) and a total of around £60 for:

Server
HDD(SCSI)
512MB of RAM
64MB onboard RAID
Backplanes
CPU power(Both CPU's) of 1.466GHZ :)

I cant complain, and its pretty damn fast aswell :D

---

### Post by elico on 2011-04-26
i would go on a new machine.
not server class hardware.
you can buy a good MotherBoard of asus or gigabyte or another more branded one that has 
built in raid 5 support, vga.
buy 3 of let say WD Black drives of 320 GB 
2 GB ram
simple CORE2DUE E5500 intel cpu.
some nice case of thermaltek or any other good case.
most likely the OnBoard LAN card will not be compatible with linux or will be less then a good intel CARD!!!
so buy a 1GB intel Ethernet card.

i got one of these(quad core+8 TB +4 GB ram + INTEL 2XLAN PCIX card) on a very fair price.
it will give you a peace of mind on the hardware and also very good performance.

---

### Post by dtfinch on 2011-04-26
I would want a semi-decent cpu, dual core or better. But we run a lot of scripts against folders with thousands of files in them. Because Samba emulates a case-insensitive filesystem on top of a case-sensitive filesystem, it often has to scan a full directory just to find a single file. If something's querying every file in a large directory, samba's cpu usage can easily reach 100%.

On our now-retired single-core file servers this was a big issue. Just leaving Adobe Dreamweaver running idle on a client with default settings and a large project open (Dreamweaver by default constantly rescans for updated files) was enough to bog down a server. But now, with quad cores, nobody would ever notice if one client maxed out one core.

Our file server usage might be atypical though.

---

### Post by AllGamer on 2011-04-26
any old computer will do, seriously.

I always recycle old computers that people no longer wants, and then i convert them into decent RAID file servers, which are great for file sharing, backup, and redundancy backup.

So you can have your main file server, and another backup file server to mirror the file server, and a back server to backup the backup server.

it might sound like overkill to some, but customers really appreciate this when they lost important files, and you can easily recover it by going to the older or oldest set of backup recycled from their old discarded hardware ;)

it's green & environmentally friendly, and it's partially free, except for the electricity used of course :D

most 2000 onward PCs are decent candidates for file server conversion.
just throw in a low cost PCI SATA controller, and fill up all the slots that you can afford with the largest HDD, then use mdadm to setup a nice RAID5

and then use the original old IDE HDD to install a clean lean Ubuntu Server + Samba, and optionally + OpenLDAP, and even more optional install CUP server to manage printing.

install in webmin and you can run it all headless mode

and optionally attach it to an UPS, and both things can be hidden in a storage closed somewhere in the office.

---

### Post by TheFu on 2011-04-26
> **cphuntington97 said:**
> Samba server for small office. 15 users typical; provisioning for growth to 25. Mostly word and excel docs but some large images. Total data around 40GB and growing slowly. Gigabit switch but most clients 100Mbps.

Happy to pay more for better performance but don't want to waste money. Uptime important but not mission critical.

Hardware specs to shoot for?

Any desktop with a GigE connection is fine.  I'd use RAID1 or RAID10 storage and take hourly snapshots to protect the data to an external HDD (NAS, desktop, just some disk that isn't the same as the RAID disks). For a small office, just use a spare desktop with a RAID controller. You can do RAID with mdadm for greater flexibility, but performance will be a little less than you'd see with a good quality RAID controller. SW-RAID is still very acceptable on modern processors.

If the network performance is less than 600Mbps, add an Intel PRO/1000 ethernet card for $30 and then you'll know it isn't the NIC as the bottleneck.

For disk, don't use Green drives.  I prefer the SAS drives in servers for higher performance and greater warranty support, but that means a server-class SAS controller is necessary. A little cheaper are SATA drives, but be certain to get those with 5 yr warranties.

You didn't mention whether you were running AD or some sort of LDAP for user authentication or what the client machines are running. I'd rather not assume. Whatever you use can matter for single-sign-on and password management.  We use OpenLDAP here and have samba, machines and lots of web services authenticate to that. 1 password to be managed, which your users will like.

Finally, rather than using straight samba, consider the free/FLOSS version of Alfresco for your deployment. This will notch you up to a DMS, not just file server. Alfresco CAN look like a regular CIFS file server, but brings sooooo many more capabilities. Like all DMS, it can be a hassle, but may be appreciated in the long run.  Alfresco will need a little stronger server with more RAM. Think at least a 1.5Ghz CPU and 512 MB of RAM.

---

