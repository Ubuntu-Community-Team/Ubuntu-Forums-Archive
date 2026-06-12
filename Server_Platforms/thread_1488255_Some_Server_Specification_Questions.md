---
title: "Some Server Specification Questions"
date: 2010-05-19
forum: Server Platforms
---

### Post by cusinndzl on 2010-05-19
I have a server which is an old home computer right now. I'm looking to upgrade to something with a higher performance then what I already have. I have some questions below.

Would it be better for me to get all server hardware, or use regular hardware? 

What kind of effect would I get from moving from 4GB of 32-Bit RAM, to 8GB of 64-Bit RAM?

I'm thinking about setting up a RAID array, what are the negatives to a RAID array?

I've seen motherboards with two gigabit Ethernet, and one gigabit Ethernet port. What will come out of having two connected to the network? 

Would DDR3 RAM have a big effect on the server's performance? 

What are the best power supply brands? I really need to get a good long lasting power supply. 

What are some features I should look for when picking parts for my server? 

What is considered good specifications for servers?

Right now the specifications for my server: Intel Pentium 4 2.40 GHz, 512MB of DDR RAM, and an 80GB hard drive. I've had problems with the server overloading sometimes. 

This will be used as a web server. It will host a few websites I currently host about five on my server. Each get about 100 visitors (30-50 unique) each day. I would like a server that would last even if my websites become more popular. I'm looking for a long lasting server. They all use PHP and MySQL to function. I will run things like a VPN, Proxy Server, FTP Server, Samba Server, and possibly a backup server. I might also run a small Windows Server virtual machine so I can use Windows only server applications. I will use Ubuntu Server as the main operating system. The price limit for me is about $800 unless anyone convinces me otherwise. 

I would like as much information I can get about picking parts for a server and what will be best for certain things. You can also send me off to other websites with more information about this.

---

### Post by dudumomo on 2010-05-20
Hi cusinndzl,
I understand that your "Intel Pentium 4 2.40 GHz, 512MB of DDR RAM, and an 80GB hard drive" has reached its limits, but I don't think you will need a big machine to run your websites + others services.
So I don't recommend you to go for a real Server hardware (I mean a XEON or Opteron + SCSI Hardrive, etc...) It will be quite expensive and not very used.
Regular hardware will certainly suit you.

I don't think you will see a different between 32b RAM and 64b RAM (Different architecture anyway). Or may be you mean a 4GB system on a 32b OS // 8GB on a 64b OS ?

I'm not a RAID specialist, so I let other people answer. (But as you want a safe system, I suggest you indeed to do a RAID)

A MB with 2 ethernets, well it can be use for redondant internet connexion, or to get internet from the first eth card and to share it from the others, etc... (Then, you can use your server as a router)

I don't think there will be a significant difference between DDR3 system and DDR2.
For the powersupply, I like Corsair ! Very reliable. But according to your computer spec, you might want to choose a Server powersupply.
In anycase, choose one the 80+

Well, I think you don't need a really big computer. 800$ is more than enough

CPU: A dualcore like a E5200 should be fine for what you want to do.
RAM: Minimum 2GB as you want to do VPN. You can buy 4GB with a 64bit OS to be quiet for a long time.
HDD: 2x500GB (Seagate Barracuda 7200.12 S-ATA)
PSU: Corsair 450W 80+ is enough for this conf
etc...

But what is for you a long lasting server. For me it's about 2-3 years. The HDD might crash, may be the ram, etc...I prefer upgrade my hardware years after years than buying a high end machine will last no longer anyway.

As an example, I'm running a Server@home, one main website with 100 unique visitors/day, and several others services (Seedbox, Mail, forums, gallery, FTP, Jabber, AjaXplorer, Image hosting). I got a HTPC case with a E5300, 2GB or RAM, 250HDD 2.5 7200tr, Intel ITX MB. I can tell you, I'm not using quite much of these config.
My CPU is never used more than 10% (Thanks to BOINC, I'm helping the science with my spare clock time, ie 90% :))
My RAM, well, I'm glad of having more than 1GB. But 2GB is too much (Anyway it's not very expensive and can be still used. But I don't have any GUI, VPN as you want to, so in your case, 2GB has to be the minimum)
My HDD, well 250GB is quite a lot for me and my connection, but I'm glad of having taken a 2.5 format but 7200tr/m, I'm sure it helps.

Here was my 2 cents.

---

### Post by jbrown96 on 2010-05-20
You don't need to buy any hardware to serve that kind of load. 

Don't buy server hardware, unless you need the warranties that come with it.

RAID might not be a bad idea, but you probably won't see any benefit from it. It's also extremely easy to setup. See ```
man mdadm
```

You don't need more RAM for that light of load. 

You really don't need to upgrade. Perhaps if you provided some better statistics on the server load, then we might be able to recommend some stuff, but you are so vague that there's nothing to recommend. With basic static pages you could use a PII to serve 100 guests a day.

---

### Post by Joe of loath on 2010-05-20
I have a box of exactly the same spec as yours, except it has a Celeron 2.4ghz. As above, what load issues are you having? I run out of CPU while updating, and out of memory when running a GUI with web browsing, IM and music. This should change now that I've switched from fedora to a headless debian system though.

---

### Post by cusinndzl on 2010-05-20
> **Joe of loath said:**
> I have a box of exactly the same spec as yours, except it has a Celeron 2.4ghz. As above, what load issues are you having? I run out of CPU while updating, and out of memory when running a GUI with web browsing, IM and music. This should change now that I've switched from fedora to a headless debian system though.

Mainly RAM overload, but I have an occasional CPU overload.

---

### Post by cusinndzl on 2010-05-20
> **dudumomo said:**
> Hi cusinndzl,
I understand that your "Intel Pentium 4 2.40 GHz, 512MB of DDR RAM, and an 80GB hard drive" has reached its limits, but I don't think you will need a big machine to run your websites + others services.
So I don't recommend you to go for a real Server hardware (I mean a XEON or Opteron + SCSI Hardrive, etc...) It will be quite expensive and not very used.
Regular hardware will certainly suit you.

I don't think you will see a different between 32b RAM and 64b RAM (Different architecture anyway). Or may be you mean a 4GB system on a 32b OS // 8GB on a 64b OS ?

I'm not a RAID specialist, so I let other people answer. (But as you want a safe system, I suggest you indeed to do a RAID)

A MB with 2 ethernets, well it can be use for redondant internet connexion, or to get internet from the first eth card and to share it from the others, etc... (Then, you can use your server as a router)

I don't think there will be a significant difference between DDR3 system and DDR2.
For the powersupply, I like Corsair ! Very reliable. But according to your computer spec, you might want to choose a Server powersupply.
In anycase, choose one the 80+

Well, I think you don't need a really big computer. 800$ is more than enough

CPU: A dualcore like a E5200 should be fine for what you want to do.
RAM: Minimum 2GB as you want to do VPN. You can buy 4GB with a 64bit OS to be quiet for a long time.
HDD: 2x500GB (Seagate Barracuda 7200.12 S-ATA)
PSU: Corsair 450W 80+ is enough for this conf
etc...

But what is for you a long lasting server. For me it's about 2-3 years. The HDD might crash, may be the ram, etc...I prefer upgrade my hardware years after years than buying a high end machine will last no longer anyway.

As an example, I'm running a Server@home, one main website with 100 unique visitors/day, and several others services (Seedbox, Mail, forums, gallery, FTP, Jabber, AjaXplorer, Image hosting). I got a HTPC case with a E5300, 2GB or RAM, 250HDD 2.5 7200tr, Intel ITX MB. I can tell you, I'm not using quite much of these config.
My CPU is never used more than 10% (Thanks to BOINC, I'm helping the science with my spare clock time, ie 90% :))
My RAM, well, I'm glad of having more than 1GB. But 2GB is too much (Anyway it's not very expensive and can be still used. But I don't have any GUI, VPN as you want to, so in your case, 2GB has to be the minimum)
My HDD, well 250GB is quite a lot for me and my connection, but I'm glad of having taken a 2.5 format but 7200tr/m, I'm sure it helps.

Here was my 2 cents.

Thank you very much. That answers my questions. 

I'll probably get a Core i3 because it is the newer socket LGA 1156 which will make later upgrades better. . I'll probably get one 4GB stick of RAM and I will later on get another 4GB stick. I'll probably get a smaller RAID array and then some more hard drives for storage that is not quite as important.

---

### Post by cusinndzl on 2010-05-20
> **jbrown96 said:**
> You don't need to buy any hardware to serve that kind of load. 

Don't buy server hardware, unless you need the warranties that come with it.

RAID might not be a bad idea, but you probably won't see any benefit from it. It's also extremely easy to setup. See ```
man mdadm
```

You don't need more RAM for that light of load. 

You really don't need to upgrade. Perhaps if you provided some better statistics on the server load, then we might be able to recommend some stuff, but you are so vague that there's nothing to recommend. With basic static pages you could use a PII to serve 100 guests a day.

I have dynamic content on all of my websites it hosts. Each uses MySQL and PHP.

---

### Post by Joe of loath on 2010-05-20
> **cusinndzl said:**
> Mainly RAM overload, but I have an occasional CPU overload.

Then that's easy. Stick some more RAM in (peanuts on ebay) and a slightly faster CPU. You can get P4's up to 3.4ghz.

---

### Post by cusinndzl on 2010-05-20
> **Joe of loath said:**
> Then that's easy. Stick some more RAM in (peanuts on ebay) and a slightly faster CPU. You can get P4's up to 3.4ghz.

I think it is time for an upgrade for me.

---

### Post by Joe of loath on 2010-05-20
Personally I don't see the logic, but it's your money...

---

### Post by cusinndzl on 2010-05-20
> **Joe of loath said:**
> Personally I don't see the logic, but it's your money...

The machine is 7 years old, eventually I will need to get a new machine. Part of why I don't upgrade the RAM is because it uses DDR RAM which is pretty old and I would not be able to use that RAM in a new machine if I ever get one.

---

### Post by tgalati4 on 2010-05-20
I bought two Dell poweredge 1750's for $300 each.  Dual Xeon (4 cores) 2.8 GHz, 3x36 GB scsi RAID drives with a real RAID controller, 4 GB of RAM, dual NICs.  They run Hardy server just fine.  I'm building one of them with Xen and multiple OS's.  With your workload, it only makes sense to get real server hardware.

Dual NICs will only help if you have faster than Cable/DSL bandwidth.

RAID0 will double your disk write/read speed but cut your drive reliability in half (no parity or backup provision).
RAID5 will give you roughly double speeds with parity and drive rebuild capability.

---

### Post by cusinndzl on 2010-05-20
> **tgalati4 said:**
> I bought two Dell poweredge 1750's for $300 each.  Dual Xeon (4 cores) 2.8 GHz, 3x36 GB scsi RAID drives with a real RAID controller, 4 GB of RAM, dual NICs.  They run Hardy server just fine.  I'm building one of them with Xen and multiple OS's.  With your workload, it only makes sense to get real server hardware.

Dual NICs will only help if you have faster than Cable/DSL bandwidth.

RAID0 will double your disk write/read speed but cut your drive reliability in half (no parity or backup provision).
RAID5 will give you roughly double speeds with parity and drive rebuild capability.

Thank you for the information on Dual NICs, I'm running my stuff off of a cable modem so that will have no use to me. I will probably setup RAID 1 because I will be using it for more of a backup in case of failure.

---

