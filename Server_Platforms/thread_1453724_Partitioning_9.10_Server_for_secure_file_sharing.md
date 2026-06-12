---
title: "Partitioning 9.10 Server for secure file sharing"
date: 2010-04-13
forum: Server Platforms
---

### Post by KaiserBachfeld on 2010-04-13
I have read through many posts and tried different things.  I have  attempted to install the OS several different times as the first few  didn't complete because it couldn't install Grub.  I was trying to get  the right kind of partitioning (appropriate mounting and file systems).   It wouldn't install correctly no matter how many different threads I  followed with various people's opinions on what partitions to have and  what size they should be.  I am not sure if that was because I have a  RAID 1 already setup on the box or not.  Formally, I had Windows Server  2008 standard running and my drives RAID 1 was setup with the Intel  chipset software accessible through the BIOS.  At one point the Ubuntu  installer starting recognizing the two drives as independent instead of  in a RAID  I am not sure if it was because I partitioned and  repartitioned the drives so many times if some how affected the drives.   The setup that finally worked (even though I still had to install the  xstart to get the OS to boot after the first successful installation)  was with the software RAID 1 with 15 GB /swap and everything else on /  however I have no applications or programs or seemingly useful  repository to install anything.  I am not sure what happened when it  went through the install process.  So I am starting over again.

Based on the following information regarding my computer specs and  network components what would be the best partitioning mount choices,  sizes, and filing system for the installations process?
  
Goals for my server:

- File Server with security (encrypted hard drives just encase the  machine is stolen).  This is my primary purpose and if I could get everything to run backups to server I would be very satisfied.
- Security (Firewall, possibly a proxy for my network, I would like to  see all of my traffic pass through the server before it leaves for the  world. I have also recently starting to learn about tor and setting up a  tor rely so this is a possibility too.  It would be important to have  my traffic be more anonymous and if my IP address could be something  from an English speaking country even better so my downloads come in  something that I can read).
- Virtual machines (I would like to have a place to setup virtual  desktops/servers where I can teach myself more).

Current Hardware:
- 8 GB RAM/4-sticks dual channel/800 Mhz
- Core 2 Quad 2.83 GHz/12 MB cache
- Two 1TB 7200 RPM/32 MB/SATA II

Current Network components:
- Modem (WiMax)
- wireless router
- 5-port switch
- Access Point
- Desktop Vista 64-bit Ultimate
- Netbook Windows XP Home
- Laptop Windows 7 Home Premium (my roommates computer)

I would like to add in the future:
- possibly an iPad or some kind of book reader that would have access to  the wi-fi
- Some kind of laptop probably with Windows 7 so I can take the work I  do in Adobe CS4 on my desktop with me with when I travel.

---

### Post by KaiserBachfeld on 2010-04-23
In my searching I have found the following to be a seemingly good layout for partitioning.

/ (10% or 10 GB ext4)
/boot (5 GB)
/swap (12 GB)
/usr (20 GB)
/home (20 GB ext4)

/? (the rest of the space I want to be a shared partition for the network while everything else is secured, however, I don't know what the best mount for this would be yet.

When I had fake RAID 1 setup these partition setup just fine however, the install would never complete because it wasn't able to install Grub or Lilo.  When I removed the fake RAID and did software RAID by the time I get to /home it says that the rest of the space on the drive is not accessible.  So I have around 953 GB not accessible.  Why is this?  Is this something that I can overlook and then mount later after the OS install?

---

### Post by KaiserBachfeld on 2010-04-23
I am attempting to follow this guide

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

On the first step there is a screen shot showing to drives with nothing listed under them.  However, on my screen there under both drives there is a partition listed that says,

> pri/log 1.0 TB  Free Space

Is this a problem? If I select the actual drive if it will ask if I really want to partition the whole disk.  I have to select the partition instead.  Will I will still be able to get the desired results if I do this or is this the reason why I run out of usable space to make partitions after 47 GB of partitioning?  :confused:

---

### Post by flatline on 2010-04-23
It's a little hard for me to understand your posts, but I'll give it a shot.  I have a server (specs in my sig) setup similar to yours - all my computers (4) backup across the network to it.  One suggestion there - try to stick with wired lines.  Backing my Macbook Pro up wirelessly is a huge pain.  I took the time to wire my house with Cat6, so that provides a much better option (took ~19hrs to transfer 80GB wirelessly, took 28 minutes over the hard lines).

[LIST]
[*]As far as partitioning the server, I'm not a true expert, but my advice would be to pick up another hard drive, something smallish (I use a 320GB, but even an 80GB would suffice).  This way you don't have to fight with the SoftRAID to get your OS installed - unplug your other HDs and just install Ubuntu onto the primary drive.  I didn't even bother to manually create partitions, I let the installer do it for me.  
[*]After the system was installed and running, I plugged my 4x1TB drives back in and formatted them, [_using mdadm to create a RAID5 array_]("http://www.jamierf.co.uk/2009/11/04/software-raid-5-using-mdadm-in-ubuntu-9-10/").  You could use you 2x1TB drives and create a RAID1, which will give you redundancy but only 1TB of usable space.  I prefer RAID5 because it allows for redundancy but also can be grown by adding more drives.
[*]I then used [_these instructions_]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") to move /home to my RAID5 array.
[*]Lastly, I [_edited /etc/samba/smb.conf_]("https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html") to create the necessary shares (using security=user).  
[/LIST]

Now, a machine on my local network can login to the server (with a valid user account, guest access is disabled) to gain access to /home.  The only downside to this setup is that I haven't found a way to use Samba (or other software) to put a limit on the size of a directory.  So if you're worried about one of the backups growing rapidly and eating up all your space, you might need to create several RAID devices, one for each backup, to put a hard cap on the disk space it can use.

EDIT: Note that I previously had this server installed very similar to you - it had 2x1TB drives in RAID1, running Ubuntu 8.04.  However, when I decided to upgrade to RAID5 and move to 9.10, I could not for the life of me get the system to install while the old drives were plugged in.  The installer kept recognizing that the 1TB drives were part of a RAID array and for some reason couldn't handle installation while they were hooked up.  So that's why I installed 9.10 with ONLY the 320GB plugged in, then from the terminal manually configured my RAID5.

---

### Post by Vegan on 2010-04-23
I let LVM do the partitioning, I then setup the server as needed. I have one web appliance and one file server.

---

### Post by KaiserBachfeld on 2010-04-23
flatline that does sound close to what I would like to do.  Yes backup on the wired connection is best and if I need to backup a laptop I think I will do that but for general security I would still like the server to monitor traffic coming across the wireless.

Since the price of technology is crazy in my country I will buy the drives in the US and ship them here (my mom is sending my some other things soon anyway).  I think I will add a 160 GB for the OS and then another 1 TB to create a RAID 5 since that is a better idea all around.  Recently the firmware on my 500 GB data drive in my desktop stopped working (couldn't find or access the drive anymore).  I sent it back to the US for repair and I will be replacing it with two 750 GB drives to RAID 0 in my desktop (don't want that problem to happen again, I have been without my data for almost a month now).  But I will need more space on the server to backup 750 GB (plus I would still like to image the OS and programs) than it did with the 500 GB hard drive.  My netbook won't take up a lot of space since it only has a 16 GB SSD.

Also, I love that your house is wired with Cat6.  If I ever own a house I would love to do something like that.

---

### Post by KaiserBachfeld on 2010-04-23
> **Vegan said:**
> I let LVM do the partitioning, I then setup the server as needed. I have one web appliance and one file server.

Yeah I couldn't seem to figure out how to get through the install with LVM.  It was like there was no place for the boot files to install.  Maybe I would have to do that manually but I definitely wasn't able to get through the GUI install with Grub or Lilo boot loaders being able to install.

I was able to go through the install process successfully until I did just one /swap 24 GB and everything else on on /.  However, that wasn't really the configuration I was looking for.  Also, it didn't boot automatically.  I still had to install xstart (or something like that).  Then when I got into the OS there were no applications (which I thought I had selected in the installation process) and the repository didn't seem to work correctly.

---

### Post by Vegan on 2010-04-24
The only time you need manual is to delete existing partitions, I perfer to let the OS figure out what it wants.

As for security, how much do you need?

I do security professionally at my shop.

---

### Post by KaiserBachfeld on 2010-04-29
> **flatline said:**
> 
EDIT: Note that I previously had this server installed very similar to you - it had 2x1TB drives in RAID1, running Ubuntu 8.04.  However, when I decided to upgrade to RAID5 and move to 9.10, I could not for the life of me get the system to install while the old drives were plugged in.  The installer kept recognizing that the 1TB drives were part of a RAID array and for some reason couldn't handle installation while they were hooked up.  So that's why I installed 9.10 with ONLY the 320GB plugged in, then from the terminal manually configured my RAID5.


Flatline I would like to take your suggestion and go with a smaller drive (probably a 320 since it's only $5 more than a 160 with twice the cache).  And then add a 1TB drive to my two to make a RAID 5 array.  I have question though regarding the type of drives to use in an array. Is it necessary for the drives to be identical.  My two drives are 1 TB with 32 MB cache which I can add a third one that is the same or for the same price get a 1 TB with 64 MB cache.  What do you think?

[QUOTE=Vegan]
The only time you need manual is to delete existing partitions, I perfer  to let the OS figure out what it wants.

As for security, how much do you need?

I do security professionally at my shop.
[/QUOTE]

I was wanting to do a manual setup for partitioning because I was trying to set up enough space for the /home or /usr partitions to setup various server administration applications and/or run other virtual servers to dedicate to various network applications that perform well in a virtual environment. Then to make another partition separate from all the admin apps for backups/restore/boot from LAN (something like WDS via PXE)/etc. operations to keep the various computers on my network up and running in case of failure.  I don't know if it is possible but I would like to setup Adobe Version Cue CS4 Server but I don't know if that would run on Linux (I can just keep that on my workstation).  So I have lots of things I would like to do with the server so I was thinking if I had the various partitions that would let me have the most scalability because when the OS just sets everything up it gives me a /boot and a / partition.

In regards to security it is important to me.

I would like to get to the place where all my drives (on all my computers) are encrypted in case of physical theft.  I was trying to figure out how to setup encrypted drives from the 9.1 install GUI but once I selected encrypted drives nothing else would install properly after that.  But that could be because I didn't have my partitions setup properly (i.e. no boot partition flagged bootable and formatted to the correct type of file system, etc.).

My server should also have network security so that only authenticated computers can access it remotely for either server administration or for file sharing/backups.

Then in regards to internet security I do want to put up a firewall on my server (though my router is probably decent enough) along with a proxy or VPN to the US and possibly setup a tor relay (this is just my thinking through all the possibilities with no place to start at this point because I don't have a running server).  I would rather not have my IP address attached to my current country.  That also would make it easier for me when downloading something because it wouldn't automatically give me the Arabic version of the software.  Even the nationals here prefer their software in English because technical Arabic is too difficult to read which leaves me with little hope of learning it but I am working on it.

---

