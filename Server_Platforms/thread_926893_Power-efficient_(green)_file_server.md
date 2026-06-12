---
title: "Power-efficient (green) file server"
date: 2008-09-22
forum: Server Platforms
---

### Post by kpatz on 2008-09-22
I've been tossing around the idea of building a home file server, running Ubuntu of course. :)

Some of the criteria for this server are, at present:[list][*]Minimum 1 TB storage, expandable down the road[*]Minimize power consumption/heat/noise generation, by spinning down unused drives[*]Some sort of redundancy against drive failures[/list]

The first thing that may come to mind is a RAID 5 array, but there are two drawbacks:  (1) drives can't be spun down individually, and (2) expanding storage would involve rebuilding the array.

Right now I'm thinking of something along these lines:  The OS itself would be on a SSD or flash drive.  Then there would be a "primary storage" drive, that would get the majority of use.  To expand storage, additional drives could be added, but the data would be arranged so that frequently used data would stay on the primary drive and infrequently used data would be on the secondary drive(s) that could spend the majority of their time spun down.  A third drive or group of drives could be powered up to back up the data on the primary drives (say, once a day), providing redundancy while still saving power.  Being a home server, it's not mission critical data so real-time redundancy isn't required.

This way, I have a server that is expandable, and runs cool/quiet/low power since a majority of the time most/all of the drives would be spun down.  A nightly cron job could handle backing up to another drive or even an external USB drive.

Thoughts?  Possible issues?

---

### Post by koenn on 2008-09-22
sounds like a plan.
possible issues:
manualy rearranging the data could become a pain, maintenance-wise, and you'd be limited to physical disk/partition sizes, meaning you'd always have some unused/unasable leftover space on each partition

you might consider lvm which allows you to add additional disks easily, and can span disks or partitions, so easier maintenance, but you don't get to chose which disk each file goes to. I also don't know if disks in a lvm logical group would spin down independently of each other.
Of course, you could create several groups ...

There's software that manages stuff like this. It's called tiered storage (or also hierarchical storage management - [http://en.wikipedia.org/wiki/Tiered_storage](http://en.wikipedia.org/wiki/Tiered_storage) ) but that's probably out of yout league, it's data center stuff really.


and of course you realize that a once a day backup means you can lose a full day's work/data

---

### Post by TomB19 on 2008-09-22
First, if you only have 2 drives, there's no need for RAID 5.  RAID 1 will provide the same benefits.

Also, I'm pretty confident drives can spin down when configured in a software array.  They key is to configure the machine up with enough RAM that frequent hits to the same files are cached, allowing the drives to spin down.

I can confirm the drive spin down when configured with mdadm.

By the way, I'd go with software RAID.  For years, we've been brainwashed into thinking hardware RAID is better than software RAID but this has turned out to only be the case in certain circumstances.  With a low use home server, software RAID is the way to go.

I would suggest a machine with built in Video.  They have the lowest over all power use and integrated graphics are fine for server use.


As far as the idea goes, I think it's a great one.  It costs a couple of hundred dollars per year to leave a machine on.  If you could get the power consumption down to 60~80 watts average, which I think is well possible, you could cut your cost down to $100 per year.

Individual machines can vary widely in their power usage.  Not long ago, it was common to have systems drawing 300 watts of hydro.  These days, 150~200 watts is more common.  With a little work and perhaps a light underclock/undervolt, systems can comfortably achieve sub 100 watt levels.


Personally, I save a bit of energy by replacing two systems with a single one running an ATX v2 PSU and compute enough compute power to easily replace two machines with one.  Unfortunately, ATX v2 PSUs come at a premium price.

Don't forget you can run a server in a virtual session and save having a second box.


Saving energy is a good idea.  I would suggest it's only worth it during scheduled upgrades.  A system would have to be a real dog to merit replacement outside it's normal refresh cycle.

Another benefit is having a cooler running system.  At 73*F ambient, I have a three year old, dual core system that emits 92*F air from the PSU.  A similarly equipped system right beside it emits 81*F air.  It doesn't seem unreasonable to expect the components inside to last longer on the cooler running system.


Good luck,

Tom

---

### Post by kpatz on 2008-09-22
I'm sure disks in a RAID5 array can spin down when idle, but as soon as you need to access something in the array, all the disks in the array have to spin up.

LVM is a possibility, but if one drive fails, wouldn't you lose everything on all the drives (like RAID 0)?

Tiered storage was basically the idea I had.  I could achieve it with a cron job that moves infrequently accessed files to the secondary drive(s) and then symlinks them to the original locations.  Thus, rarely accessed files could be on a drive that spends most of its time sleeping.> and of course you realize that a once a day backup means you can lose a full day's work/dataWell, since this server would be mainly housing backups of my other systems, I don't think that will be much of a problem.  That plus, anything created within that day is likely something I can re-create easily (e.g. recopy from another system, or reload pictures from a camera).

---

### Post by cariboo on 2008-09-22
You also may want to have a look at these drives:

[http://www.wdc.com/en/products/products.asp?driveid=385](http://www.wdc.com/en/products/products.asp?driveid=385)

They are touted to be power saving.

Jim

---

### Post by windependence on 2008-09-23
Using power saving drives and low wattage processors is the way to go. Most all hardware is "green" compliant now. It's a fallacy that servers take more power to run than spin down drives, turn off LAN cards etc. I run mine 24/7/365 and it doesn't cost hundreds to run each server or I would be bankrupt. 

Also, you are wearing your hard dries out twice as fast spinning them down all the time. Spinning them up takes 100's of hours off their life. The temperature change is also hard on components.

IMHO, you are wasting your time trying to do more than the hardware manufacturers already have for the "savings" you will get if any, in the end.

-Tim

---

### Post by kpatz on 2008-09-26
Any other thoughts?  I'm trying to weigh the benefits of RAID5 vs. separate drives that can stay spun down most of the time.

It seems that hard drives aren't all that power hungry; some only draw 10 watts when running, so just letting them spin won't make for a much higher electric bill/heat generation.

RAID5 Pros:
1.  Better performance via striping
2.  Easier recovery from a failed drive
RAID5 Cons:  All drives have to be spinning at once, so if the array goes to sleep, all drives have to spin up when the array is accessed after a long period of inactivity.

Separate Drives Pros:  Provided I keep frequently-accessed files on one drive and rarely-accessed files on a 2nd drive, the 2nd drive can spend most of its time sleeping, saving power, heat, and drive wear.

Separate Drives Cons:  More complex file organization, and a failed drive would cause loss of data.

Of course there are combination options as well... the separate drives scheme using pairs of mirrored drives, for example, or two RAID5 arrays, but then I'm using a lot more drives than I would have to otherwise.

I've been trying to find a fairly definitive list of PC components and their average power draws.  I know the biggest power draws are the CPU and video card, but I don't know how much power DDR2 RAM draws (I've heard figures as high as 10-20 watts for RAM, but that seems awfully high).  I'm thinking if the machine has a ton of RAM for caching, it would reduce hard drive activity, saving power, but not if RAM draws that much juice. :)

Thoughts?

---

### Post by koenn on 2008-09-26
> **kpatz said:**
> 
Separate Drives Pros:  Provided I keep frequently-accessed files on one drive and rarely-accessed files on a 2nd drive, the 2nd drive can spend most of its time sleeping, saving power, heat, and drive wear.
As Windependence said, spinning your drive up again when they're needed causes the most wear, possibly more than keeping them running.

---

### Post by Krupski on 2008-09-26
> **koenn said:**
> As Windependence said, spinning your drive up again when they're needed causes the most wear, possibly more than keeping them running.

Here's another way to save power... use CPU throttling.

It's easy to do. For most newer motherboards that support ACPI, simply add the line "acpi-cpufreq" to the "/etc/modules" file and then add this (below) to the "/etc/rc.local" file:

```

/usr/bin/test -e /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
/usr/bin/test -e /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
/usr/bin/test -e /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
/usr/bin/test -e /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor

```

If you want "on demand" cpu throttling (i.e. either min or max as needed), then replace "conservative" with "ondemand".

Likewise to always save power and never throttle up, replace "conservative" with "powersave".

Lastly, change it to "performance" to lock the cpu at max clock.

-- Roger

(edit): there is no need to remove the lines for CPU2 and CPU3 if you only have a dual core. Each line tests for the presence of the "scaling_governor" file and only runs if the file is present.

---

### Post by lazyart on 2008-09-26
The surge of current it takes to spin the drive back up is more damaging than leaving it running.  

Ever notice that a light bulb is most likely to blow out when you turn it on?  Same concept here.

If you're going to be green, that's fine.  Just be sure your redundancy/backup plan is working.  
If you're running CRTs, ditch them.  If you can't, make sure they are off when not in use.  
Buy a KVM or administer your servers remotely.  
Virtualize what you can.  Keeping a single CPU busy is a lot less power than a 2nd box and it's power supply/fans/monitor....

---

### Post by kpatz on 2008-09-27
I guess RAID5 is the way to go then... one question though, is it possible to add drives to a software RAID5 array in the future to expand the capacity?  Or would the entire array need to be backed up and rebuilt? **EDIT:** Looks like RAID5 arrays can be "grown": [http://scotgate.org/?p=107](http://scotgate.org/?p=107)

The idea behind the "green" server is more to minimize fan/drive noise and heat generation (we have no A/C and the room gets hot in the summer).  I already use an LCD monitor and KVM and hope to set up virtual machines on this box down the road.

---

### Post by fjgaude on 2008-09-27
Yes, you can add drives to software raid, add then grow by changing the number of drives in the assemble. Lots of things to learn before one can successfully do all the things that we can run across with drive failures, etc.

These were my study guides:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
 /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
 [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Have fun!

---

### Post by tgalati4 on 2008-09-27
You can also use ethernet drives.  There are several Network Attach Storage (NAS) solutions out there.  Newer designs use less power.

---

### Post by Krupski on 2008-09-28
> **tgalati4 said:**
> You can also use ethernet drives.  There are several Network Attach Storage (NAS) solutions out there.  Newer designs use less power.

Do you know if anyone makes an "AOE" (ata over ethernet) adapter board?

What I picture is a little circuit board that has a power connector, a hard drive (SATA or PATA) connector and an RJ-45 ethernet jack.

Is there something like this? I searched Google and didn't come up with much. I found all sorts of USB to HDD boards and Firewire to HDD, but no Ethernet to HDD.

It would be awesome to be able to add hard drives to a Linux box simply by connecting them to the local Intranet.

-- Roger

---

### Post by dgray_from_dc on 2008-09-28
They do exist.  You'd be better of looking for an NAS.  However, stay away from the Netgear SC101.  I bought one on the cheap only to find out that they only work with windows.  But this is likely to be just like what you're looking for.  It's a dual drive enclosure with power and Ethernet plugs, that's it.

---

### Post by michaelzap on 2008-09-28
> **Krupski said:**
> Do you know if anyone makes an "AOE" (ata over ethernet) adapter board?

What I picture is a little circuit board that has a power connector, a hard drive (SATA or PATA) connector and an RJ-45 ethernet jack.

Is there something like this? I searched Google and didn't come up with much. I found all sorts of USB to HDD boards and Firewire to HDD, but no Ethernet to HDD.

It would be awesome to be able to add hard drives to a Linux box simply by connecting them to the local Intranet.

-- Roger
Why would you do that instead of just mounting the drive via ethernet?

I second tgalati4's suggestion of using a NAS drive instead of building a server machine. If you're really concerned about power usage, these will blow away any complete CPU in that respect. If all you need is a file server, then a NAS is ideal.

---

### Post by windependence on 2008-09-28
If you can find a device that supports iSCSI, that would be the way to go, and you could use the NAS for VMs or for storage on your Linux boxes.

-Tim

---

### Post by Krupski on 2008-09-28
> **michaelzap said:**
> Why would you do that instead of just mounting the drive via ethernet?


I'm confused. I thought the AOE adapter would allow that?

How do I "mount a [hard] drive via ethernet"?

What I mean is, I want to put hard drives into a box with a power supply and an ethernet cable... no computer used. I want to mount these drives OVER ethernet on a computer in another room.

Can I do this? If so, how?

---

### Post by dgray_from_dc on 2008-09-29
> **Krupski said:**
> I'm confused. I thought the AOE adapter would allow that?

How do I "mount a [hard] drive via ethernet"?

What I mean is, I want to put hard drives into a box with a power supply and an ethernet cable... no computer used. I want to mount these drives OVER ethernet on a computer in another room.

Can I do this? If so, how?

NAS!  It's a type of disk enclosure which simply allows you to access files via an Ethernet connection.  A lot of NAS's come with drives built in.  However, some don't.  Just look up NAS (Network Attached Storage), I've seen them on TigerDirect.com, Geeks.com, even on Google Shopping.  This is _**[SIZE="6"]EXACTLY[/SIZE]**_ what you are talking about. A number of them are supported by Linux with standard protocols.  Just be careful in your selection and avoid the models like the one mentioned in my previous post as it uses proprietary drivers and software only compatible with Windows.

---

### Post by Krupski on 2008-09-29
> **dgray_from_dc said:**
> NAS!  It's a type of disk enclosure which simply allows you to access files via an Ethernet connection.  A lot of NAS's come with drives built in.  However, some don't.  Just look up NAS (Network Attached Storage), I've seen them on TigerDirect.com, Geeks.com, even on Google Shopping.  This is _**[SIZE="6"]EXACTLY[/SIZE]**_ what you are talking about. A number of them are supported by Linux with standard protocols.  Just be careful in your selection and avoid the models like the one mentioned in my previous post as it uses proprietary drivers and software only compatible with Windows.

Thanks! I'll check it out.

-- Roger

---

### Post by koenn on 2008-09-30
> **dgray_from_dc said:**
> NAS!  It's a type of disk enclosure which simply allows you to access files via an Ethernet connection.  A lot of NAS's come with drives built in.  However, some don't.  Just look up NAS (Network Attached Storage), I've seen them on TigerDirect.com, Geeks.com, even on Google Shopping.  This is _**EXACTLY**_ what you are talking about. A number of them are supported by Linux with standard protocols.  Just be careful in your selection and avoid the models like the one mentioned in my previous post as it uses proprietary drivers and software only compatible with Windows.

that's not exactly true.
NAS is a file sharing appliance : it does file sharing, commonly through smb/cifs (samba, windows) or NFS.

with file sharing, you're obviously working on file level. the device Kropski describes -"ATA over Ethernet"- suggests access on block level - below the filesystem. As Windependence said, this technology exists for SCSI in the form of iSCSI. 
[http://en.wikipedia.org/wiki/Iscsi#Storage_Area_Network_.28SAN.29](http://en.wikipedia.org/wiki/Iscsi#Storage_Area_Network_.28SAN.29)
It's actualy SAN (_not_ NAS) technology over ethernet in stead of the classic fiberchannel.

according to wikipedia, a similar technology exists for SATA drives :
[http://en.wikipedia.org/wiki/ATA_over_Ethernet](http://en.wikipedia.org/wiki/ATA_over_Ethernet)

---

### Post by michaelzap on 2008-09-30
> **koenn said:**
> that's not exactly true...

It does seem to be exactly what he wants to do. He asked about a specific hardware method for doing it that is what you describe, but his end goal doesn't seem to require block-level access to the drive at all. I still don't understand why a person wouldn't just connect the drive via SATA if they want block-level access, so ATA over Ethernet seems like a rather esoteric and cumbersome way to achieve what appears to be a common and straightforward purpose.

---

### Post by koenn on 2008-09-30
> **michaelzap said:**
>  I still don't understand why a person wouldn't just connect the drive via SATA if they want block-level access, so ATA over Ethernet seems like a rather esoteric and cumbersome way to achieve what appears to be a common and straightforward purpose.

It may be cumbersome and esotheric overkill if you use it to attach just one disk, but if you have a storage device that can take multiple disks in RAID configurations and where you can add additional drives quasi at will,  things change. Plus you could attach more than one server to the same storage, allowing for clusters or other fail-over configurations. And you lose the overhead of a client/server fils sharing application.

granted, all of this doesn't make much sense for a home server :)

---

### Post by kpatz on 2008-10-02
All this SAN talk is drifting off the original topic... we're talking major overkill for a home file server.

Also I don't want to use a dedicated NAS box since I'll be using this box for development and running virtual machines as well.  Maybe even as a Myth slave backend.

Plus, I like to DIY and have more control over everything if I build a box than if I use someone's proprietary NAS unit.

---

### Post by michaelzap on 2008-10-02
> **kpatz said:**
> All this SAN talk is drifting off the original topic... we're talking major overkill for a home file server.

Also I don't want to use a dedicated NAS box since I'll be using this box for development and running virtual machines as well.  Maybe even as a Myth slave backend.

Plus, I like to DIY and have more control over everything if I build a box than if I use someone's proprietary NAS unit.

Well that's a horse of a different color. NAS servers are definitely the "greenest" file servers that you're going to find (by far), but you can't run virtual machines on them. You can use them to stream media, and many have hacked firmware available (the Buffalo firmware is awesome) that would allow you to do a lot more, but they're not intended to be a complete system for all uses.

Flash drives are extremely energy-efficient and fast, but they're also hella expensive. Low-temperature CPUs (like the Core 2 Duo) use less power, and you wouldn't want a fancy high-power video card or huge monitor either. I think that higher-quality power supplies waste less electricity in the conversions, so that might be worth investigating.

But again if green is your goal, you could get a NAS and additionally build yourself a system for virtual machines and whatnot that would be turned off whenever you're not using it.

---

### Post by windependence on 2008-10-02
On the contrary, if your NAS device supports iSCSI protocol, you can most certainly (at least with VMware) use the device just like a SAN, including booting from the device and creating LUNs for your VMs. This is why I mentioned FreeBSD with a bunch of storage because you can then make that whole box an iSCSI target and cut it up into LUNs for each of your VMs, even when hosted on different machines.

-Tim

---

### Post by michaelzap on 2008-10-02
> **windependence said:**
> On the contrary, if your NAS device supports iSCSI protocol, you can most certainly (at least with VMware) use the device just like a SAN, including booting from the device and creating LUNs for your VMs. This is why I mentioned FreeBSD with a bunch of storage because you can then make that whole box an iSCSI target and cut it up into LUNs for each of your VMs, even when hosted on different machines.

-Tim

Er...right. but if I understand you correctly, we're saying the same thing. you can use the drive in the NAS as your boot drive for a virtual machine, etc., but you still need another CPU to actually run the machine (as well as the other little things like a mouse, keyboard, and monitor).

---

### Post by kpatz on 2008-10-06
Let me outline my current network setup and how I envision this box being used:

Right now, I have, in my office, two machines.  One is an old Pentium 3 Dell Optiplex which serves firewall/email/DHCP/DNS server duties, and a home-built Athlon64 based box running XP (my main desktop).  I also have a MythTV box in my theater cabinet.

The new box I'm planning will initially act primarily as a file server and development box (I write C++ apps in Ubuntu such as a spam filter which I run on the Optiplex).  The "file serving" duties will primarily be for primary backups of the other machines, archival of infrequently used files, and archival/overflow storage for the Myth box.  I also have a few gigs of MP3s on the myth box which I may move to the file server as well.  Both of my current Ubuntu boxes have MySQL running as well, and when I build the new box, I hope to move my databases to it as well.

I also plan on running virtual machines on this box.  Depending on how well it works out, I may eventually replace my XP desktop with it (running XP in a virtual machine for apps that don't work in Wine).

The reason I want some "green" in it is because I'll likely have it running 24/7, and with no A/C it gets hot in the summer so minimizing heat generation is important.  On hot summer days I'll usually leave the XP box off and use my laptop.  Also, when the box is idle, I'd like it to be able to use less power, by reducing CPU speed, powering off drives, etc., since there may be times when the box isn't accessed much, but I like to have it on so I don't have to wait for it to boot up/shut down, and so any files stored on it are available.

---

### Post by CCCCCC on 2008-10-06
Give you the best recommendation
Serving over 225,000 customers,  AAA PharmacyOnline is your trusted source for the lowest possible prices for all of your prescription needs. At AAA PharmacyOnline your health is our number one concern. Our trained team of doctors and pharmacists make sure your purchasing experience is stress free and enjoyable.  We make sure that you receive the highest quality medications. When it comes to excellent customer service, low prices and fast shipping, we set the industry standards. 
 
We offer a wide range of brand name and generic drugs at economical prices for all your prescription needs. If you find your medication priced lower, we will match that price for you.  
 
If you do not already have a prescription then our medical doctors can work with you to provide you with your prescription. 
 
Visit us: [http://www.aaa-pharmacyonline.com](http://www.aaa-pharmacyonline.com)

---

### Post by michaelzap on 2008-10-06
We have two NAS drives (one for work files and one for media), an Ubuntu desktop and a couple of laptops (plus others when we have guests). The NAS drives hold all of our shared files and any of the networked machines can access them. I backup the desktop and laptops to the media NAS and I also do offsite backups to a USB hard drive (plugs right into either NAS) and Amazon S3 via JungleDisk.

It's a relatively green setup, since the NAS drives use very little power and spin down when not in use. It's also simple and reliable, since NAS drives don't require constant updates and maintenance (they just work). I'm also getting a D-Link DSM-520 media streaming device to be able to play videos and mp3s without a laptop or desktop machine, but that's more luxury than necessity since the media NAS streams these files.

Personally I like that the NAS drives aren't full computers. I want reliable file storage, not another machine to deal with. They also make upgrading our work machines a lot easier, since we have practically no files on them to backup before formatting.

Probably the greenest thing that you could do is to trade your Athlon64 in for a Core2Duo or some other speedy but low-power CPU.

---

