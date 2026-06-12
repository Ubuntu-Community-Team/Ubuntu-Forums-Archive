---
title: "Ubuntu 14.04 LTS Server Spec"
date: 2015-02-06
forum: Server Platforms
---

### Post by Geoff_Newnham on 2015-02-06
Hi,

as newbie Ubuntu Server user and looking to set a first server up would a server with the following spec run Unbuntu Server 14.04 LTS:

[COLOR=#000000][FONT=Arial]GIGABYTE GA-F2A88XM-DS2 AMD A88X (Socket FM2+) Motherboard
[/FONT][/COLOR][FONT=Helvetica]AMD A10-6800K RICHLAND 4.1GHZ Processor
[/FONT]
[FONT=Helvetica]KINGSTON HXFR 16GB (2X8GB) 1600 Memory

Thanks

Best Regards

Geoff[/FONT]

---

### Post by Bucky Ball on 2015-02-06
Welcome. By the looks of it, that beast could take a fleet of satellites to orbit and track them. I can't see how you would have any issues running a server. Perhaps a mention of your graphics card and a further description of what you want to serve with it may help others. Good luck. 

PS: I used a Raspberry Pi with 1Gb of RAM as a media server for awhile. It had no issue. Now using an Odroid. They are tiny little boxes with ARM processors. ;)

---

### Post by Geoff_Newnham on 2015-02-06
Thanks for your reply.

I was just going to use the motherboard graphics connector, would it be worth sticking a Graphics card in it? I just want to use the server to function as a Vembu BDR Backup Server, [https://www.vembu.com/products/vembu-bdr/](https://www.vembu.com/products/vembu-bdr/).

---

### Post by nerdtron on 2015-02-07
Don't bother installing a new graphics card. Just install Ubuntu server and see if you have display. Then it's good.

---

### Post by Geoff_Newnham on 2015-02-07
Great. Thanks for all your help guys.

---

### Post by mörgæs on 2015-02-07
Is this hardware you are going to buy or something you have already? If the first then I suggest that you wait and test the setup on any random computer you have around.

---

### Post by TheFu on 2015-02-07
Don't know anything about that backup software, but a $150 dual-core atom can easily handle backups for 20+ systems depending on the amount of change data daily and network performance. I do 30 VMs with rdiff-backup nightly. Unless you run ZFS, 16G is 15.5G more than any FLOSS backup server would need.

Just sayin'.  This isn't *that other OS* and in the Linux world, commercial backup tools aren't any better than the F/LOSS solutions for people running fewer than 100 systems.

IMHO.

I was always pissed that ESX/i basically required $1000 software even for basic backups.  When my company did ESX and ESXi stuff, we used Veam stuff. It worked and we passed the cost onto the clients.

---

