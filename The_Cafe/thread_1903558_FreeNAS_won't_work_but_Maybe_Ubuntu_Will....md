---
title: "FreeNAS won't work but Maybe Ubuntu Will..."
date: 2012-01-02
forum: The Cafe
---

### Post by Mattaus on 2012-01-02
Hi all,

I turned an old PC into a FreeNAS based home NAS the other day. For reasons that remain a complete mystery to me the NAS decided to not function after 3 days despite nothing having being changed.

I searched my butt off to no avail, but the problem is definitely a software issue with FreeNAS simply just not liking my gear - why it worked for a few days then bit the dust is beyond me. The hardware is fine and I am still determined to use it for my home NAS. I figured I could just put Ubuntu or Lubuntu on the machine, set up SAMBA file sharing and away I go - not ideal but it'll work.

HOWEVER, I wish to install the OS to the same thumb drive that FreeNAS was installed on - this frees up all the internal HDD's for content. 

I'm a bit of a noob so I'm going to try  and create a persistent Live USB stick for the job. All the machine will do is hold data and share it over my network. I won't even have a screen plugged in. I'll just be treating it's shared folders as folders on my Windows desktop.

Will this work or if not can someone suggest a better idea? I am most certainly all ears!!!

Cheers.

- Matt

---

### Post by mbarland on 2012-01-03
It'll work, just run through the Ubuntu installer and tell it to install to the flash drive. I did the same recently, but my flash drive died after running the server for a few months. It was kind of a pain to reset everything up, so I put it on a HD partition. I would recommend the same, a small installation of Ubuntu wont take up that much space.

---

### Post by Mattaus on 2012-01-03
I ended up using the universal USB installer because I only had a spare 4GB flash drive, and Ubuntu wanted 4.3GB. How the Universal Installer goes about fitting it on I'm not sure, but it has worked.

A bigger issue has arisen however in that my hard drives from the NAS are UFS formatted. While I can mount and read them, getting them to be writable is more effort than it's worth in my opinion. I'm busy moving everything to my Windows box so I can reformat the drives to something friendlier.

So much more mucking around than I envisaged a few weeks ago :(

---

### Post by arguson on 2012-01-04
you could use Gparted Live to reformat the disks for server use 

I installed ubuntu server instead of freenas 3 years ago and never regretted the decision, works great to date without any breakage. only hitch is that you have to use command line to setup everything

---

### Post by Mattaus on 2012-01-04
Yeah I've transferred all my media and I am in the process of formatting everything to a friendlier to use format. No UFS for me thanks!

---

### Post by jjex22 on 2012-01-04
> **Mattaus said:**
> Yeah I've transferred all my media and I am in the process of formatting everything to a friendlier to use format. No UFS for me thanks!
 
I use NTFS for mine, have done for years - ever since I started using more than just MacOS! I still feel a little dirty every time I do it, and I don't even use Windows - only one machine has Windows 7 on it (and 8 preview... not a fan) and I swear I just use it to update itself these days! But I've not found a better supported (R/W) file system able to handle large files - obviously as a Mac user HFS+ was out! I also format my data drives with GPT instead of MBR... okay I format all my drives this way, but I did start with my Data machine!


> I ended up using the universal USB installer because I only had a spare  4GB flash drive, and Ubuntu wanted 4.3GB. How the Universal Installer  goes about fitting it on I'm not sure, but it has worked.


The live CD's/USB's use a file system called SquashFS instead of the more usual EXT3/4 or UFS - it's a compressed file system, so takes up less space, but it is a read only file system - you can't write to it, this is why you created a "persistance" file - this is where all the data is writen to that you download this, plus the usb nature of the device and compression mean that it will not run as fast as an internal HDD formatted in EXT4. This however shouldn't be a problem for such a simple set up.

If you wanted to get Ubuntu installed internally, I'd recommend using a minimal image such as [this]("https://help.ubuntu.com/community/Installation/MinimalCD") to build on, or just install the server [image]("http://www.ubuntu.com/business/server/overview") - you would be able to install a base system plus the extras you need for well under 2GB of hard drive space - Ubuntu server only requires a minimum of 1GB and you wouldn't be using more than this. 

Whatever you do I do recommend using the server image of 10.04 or atleast the desktop 10.04 for NAS use - I would leave it  until the support for 10.04 desktop runs out in 2013 before upgrading to 12.04, ofcourse if you used the server you would recieve updates until 2015 anyway!

---

### Post by Mattaus on 2012-01-04
Oddly enough I'm formatting the drives to NTFS already - however it's because I've decided I should just let go of the hardware I was using for my NAS and just use my Windows box as the NAS for the time being. It stays on 24/7 *cough* doing things *cough* so I may as well use it instead of having 2 full desktop machines running.

At some point in the future I will buy a dedicated NAS and then migrate everything into that. NTFS will make that relatively easier than what I've been going through the last couple of days!

---

### Post by jjex22 on 2012-01-04
> **Mattaus said:**
> Oddly enough I'm formatting the drives to NTFS already - however it's because I've decided I should just let go of the hardware I was using for my NAS and just use my Windows box as the NAS for the time being. It stays on 24/7 *cough* doing things *cough* so I may as well use it instead of having 2 full desktop machines running.

At some point in the future I will buy a dedicated NAS and then migrate everything into that. NTFS will make that relatively easier than what I've been going through the last couple of days!

I can see the sense in that - it often occurs to me how much energy my home server wastes - it's an old G4 PowerMac that became out dated when Apple went Intel only, and I couldn't bring myself to chuck it out. I've been thinking that once my 3 year old netbook goes sometime in the next 18 months I'll strip it down and use the motherboard to replace the server - at 9.5 hours battery life with it's atom cpu, it's got to be better suited than the powermac - I'll probably still use the old mac for the legacy mac stuff and retire my emac that's REALLY unefficient with it's massive crt monitor!

who know's maybe the powermac will go first! it's been running near 24/7 for about 4 years-ish basically only getting turned off to move - it doesn't even get shut down for short breaks so we can access things remotely! it doesn't even get a break for updates as it runs tiger  - so there's been no updates! I did try different distro's but the PowerPC CPU varients were (at the time) less stable, and the tiger ran natively!

---

### Post by Mattaus on 2012-01-04
That's it - my main concern is power consumption. 

My desktop is a power hungry beast (quad core, AMD video card, lots of RAM and 4 HDD's as it is without the inclusion of the 2 from the NAS) plus the plasma TV, AppleTV (running XBMC) a bazillion ceiling fans (welcome to Australia!) - I just can't justify yet another running PC nor can I afford a dedicated NAS at the moment either.

---

### Post by cariboo on 2012-01-04
I'd suggest you use the server version without a gui. If all you plan on doing is serving files, and streaming media, the server version automagically throttles the cpu speed, you don't need a lot of resources.

My server is powered by an Intel E5400 dual core cpu@2.7Ghz with 2GiB of ram. I've only tried streaming 3 different media files to 3 different systems, and the server does it easily without even breaking a sweat.

I'm currently connected to the server via ssh, transferring a couple of large files, 5Gib+ each via sftp and streaming a movie (ripped dvd) to my stereo/blu-ray player, and cpu usage is under 1%, it was running at .7%, but has since dropped to .3% since the file transfer finished.

---

### Post by mips on 2012-01-05
> **Mattaus said:**
> 

At some point in the future I will buy a dedicated NAS...

[http://mybroadband.co.za/vb/showthread.php/333460-HP-ProLiant-MicroServer](http://mybroadband.co.za/vb/showthread.php/333460-HP-ProLiant-MicroServer)



.

---

### Post by Mattaus on 2012-01-05
Performance throttled or not I'd imagine (and I've got no facts on hand to back this up so please don't take it as being rude) a full blown desktop PC would still run more power intensive than a dedicated NAS.

> 
Originally Posted by Mattaus  

At some point in the future I will buy a dedicated NAS...
[http://mybroadband.co.za/vb/showthre...nt-MicroServer](http://mybroadband.co.za/vb/showthre...nt-MicroServer)

Again am yet to check full specs but even that micro server would pull more power than a dedicated NAS surely? Remember I already have  XBMC running off an Apple TV2 (8Watts!!!) so no need for anything grunty enough to actually display the media as well.

All in all I'm probably a while off getting the NAS so no point looking now because the landscape will likely change in the coming months/year.

---

### Post by jjex22 on 2012-01-05
Whilst on the subject of being power efficient and good natured to the environment and what not, thought I'd mention PC Recyling as an option for your old PC if it's becomming surplus? The first PC I ever made was for my step sister when we were students - then she got a job and got a mac, so the old box came back to me - I had no use for it and would probably only get $60 on ebay for it - it sat in my garage for a bit awaiting a trip to the tip when someone at work mentioned Computer Aid International - I think they're only a UK charity, but there seems to be a organisation like them everywhere; the refit and repair old PC's then give them to people who need them local and global - better than going to the tip!

Of course if you can get something on ebay for it go fot it - that's like paid recycling!

---

### Post by Mattaus on 2012-01-05
I told my girlfriend I'd use the old NAS to build a desktop machine for her (mine is 'sacred' lol). I'm going to try and sneak Ubuntu on it, pretty it up of course, and see how she likes it. All she does is web browsing so it shouldn't be an issue!

---

