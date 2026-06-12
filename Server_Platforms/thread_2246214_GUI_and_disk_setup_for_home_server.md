---
title: "GUI and disk setup for home server"
date: 2014-09-29
forum: Server Platforms
---

### Post by mastablasta on 2014-09-29
Well, the micro server arrived. Disks will arrive soon. it's an HP micro with Turion Neo II, 2,4Ghz dual core and 4Gb ECC ram (basically like best atom only worse power consumption).

Server will be installed to and run from 8GB USB stick (btw I just found out how one can not install it to USB on one computer and then boot that USB on another - IP wasn't assigned to it internet wasn't working  what's up with that ?!?!). if the stick will fail (which I doubt) we will get an SSD.

For start it will be a backup server that will also be used as VPN (backups will run only on weekly basis) and we might add virtual hosts on (still deliberating on that...). we also though to be able to serve the files by using some kind of GUI like maybe owncloud. so all this stuff has to be easy to setup. 

I did plenty of GUI tests. and I would like to hear if there is any advice from more seasoned server users that might be using a web gui for administering the server.

Znetyal - nice, easy, but might be too bloated for my needs.
ClearOS (centOS based) - good, simple to use, but plenty plugins need payment
Webmin - didn't like it too many things and not too easy to find or immediately see unless you know where to look and what for.
Nethserver (centOS based) - good, clear, but perhaps a bit too clear. found one or two minor issues. I am not sure it has all things included that I need. it is light on resources.
Ajenti - clean, nice, fast, but documentation is not as good. and some things are done a bit strange. e.g for service it is showing what package is missing for it to work but doesn't always offer download button net to it.
Openmediavault - nice and all but doesn't support USB stick install
FreeNAS (FreeBSD based) - good, has jails, but I do not have enough RAM to run it. also the CPU is not really something stellar
NAS4Free (FreeBSD based) - could maybe pool it off with 8 GB ram but it would mean I need to buy a 4GB stick. so I will pass.

ISP config and zPanel - too complex or too bloated (too many stuff I do not need or ever plan to use).

I realise I could use CLI only but some things to setup need so many commands that they are off putting. I do not want to go through 84 simple steps just to setup openvpn server and then when it's not working troubleshoot each of the steps.



Now as for disks
First I am still not sure what way to use to transmit data that needs backup to server. There are a couple of windows PC and a couple of Ubuntu with one Android in the net. Own cloud seemed like a good choice but it syncs immediately, while I would like it to do sync only at a certain time in week. also there is no history. just sync. so while we might make a part of disk dedicated to owncloud it might not be a good idea to use it for backup. or am I missing something? owncloud does have deleted files recycling bin bit does it have snapshots?

Ok so for starters we will have 2x 2TB hard disks that will be connected (mirrored). What I am not sure here is it better to have Raid 1 (hardware / software?!) or to just use rsync,snapRAID or similar between the two?

---

### Post by mastablasta on 2014-10-01
bump and to add what I need to interact with server and move the data:

1. it should have a linux and windows (XP) client (i.e. GUI) - Android optional, but not necessary
2. it should have file versioning but not too space consuming, so we can easily retrieve the old file version. 
3. it should have user management - multiple users each with their own directory (currently max 10 users/clients)
4. it should have such a sync that it doesn't overload the network. In other words to include an option where you can delay syncing for certain 
files/folders until a more appropriate time (e.g. late at night)
5. it should have a way to restore the file sync upon interruption (e.g. loss of power supply, loss of network connection). Kind of like torrent where 
it checks the hash and continues with download - resulting in perfect file image.

---

### Post by lukeiamyourfather on 2014-10-01
FreeNAS will do all of those things and 8 GB of memory is enough for that. If you use ZFS it can be configured to take automatic snapshots which will allow you to go back to older files.

---

### Post by mastablasta on 2014-10-02
I know but it needs a stronger PC which would cost me quite a bit more in my part of the world. for now we have what we have and have to work with this. I am sure it should (in a way) be enough.

---

### Post by johnathan3 on 2014-10-02
DO NOT BOOT AND RUN from a USB stick. i tried this running Ubuntu server and went through 4 USB sticks and 1 USB controller on my board within 1.5 years , the read and write cycles on Ubuntu are to much for a USB stick to handle all the time (think logs always running for system and disks) you will burn out the USB for sure. if you NEED to run from USB port because you are out of Sata ports, atleast plug in a USB disk drive, like 64GB SSD or something.

After having 4 16GB USB stick burn out (and not cheap ones, they were USB 3 and good quality Corsair ones) i switched to a Sata 120gb laptop drive 5400rpm, have for 2 years now have had 0 issues.

---

### Post by QIII on 2014-10-02
OTOH, I have a cheap 16GB Lexar USB with a full-on ext4 installation in my pocket.  I've used it for a couple of years and even upgraded from Precise to Trusty.  Granted, I don't keep anything important on it and it doesn't have a swap partition.

---

### Post by mastablasta on 2014-10-03
> **johnathan3 said:**
> DO NOT BOOT AND RUN from a USB stick. i tried this running Ubuntu server and went through 4 USB sticks and 1 USB controller on my board within 1.5 years , the read and write cycles on Ubuntu are to much for a USB stick to handle all the time (think logs always running for system and disks) you will burn out the USB for sure. if you NEED to run from USB port because you are out of Sata ports, atleast plug in a USB disk drive, like 64GB SSD or something.

After having 4 16GB USB stick burn out (and not cheap ones, they were USB 3 and good quality Corsair ones) i switched to a Sata 120gb laptop drive 5400rpm, have for 2 years now have had 0 issues.

> **QIII said:**
> OTOH, I have a cheap 16GB Lexar USB with a full-on ext4 installation in my pocket.  I've used it for a couple of years and even upgraded from Precise to Trusty.  Granted, I don't keep anything important on it and it doesn't have a swap partition.

that's the thing. read on corsair forums where they said that if any USB failed within 10 years they would replace it and also said they can not say what kind of controler is used in different batches (static wear levelling or dynamic wear level one). what I was thinking is sticking the /logs and /swap on data disk. or maybe not even that. we got a 8GB Kingston USB with 5 year warranty and Linux support :)

so we will see how this goes. if not there is the warranty... ha, ha!

no, if it doesn't work we plan to get a 32GB SSD install Debian on it and add openmediavault or Nethserver or similar. just looking for something with GUI and some modules so I don't have to mess around too much with install. although SSD have same issue with swap as I know. and with 4GB I hope swap won't get touched much if ever. at the moment I am running Ubuntu on the stick and I reduced swapiness, and it was never used yet.

---

