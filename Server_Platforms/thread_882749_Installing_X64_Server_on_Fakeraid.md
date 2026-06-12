---
title: "Installing X64 Server on Fakeraid"
date: 2008-08-07
forum: Server Platforms
---

### Post by CyberCowboy on 2008-08-07
I've been trying to get an answer to this for a couple days now and not having much luck, so hopefully I can get it here.

I am building an x64 "server" on an Optiplex 755 work station

Specs are
Quad Core 2.6 Ghz
8 GB RAM
2 500 GB Drives to be used in RAID 1

the system has an onboard fakeraid that I would like to utilize, however all of the instructions I'm finding for using fakeraid seem to want you to boot from the LIVE CD, which is desktops.  Where can I find a reasonable walk-through for setting up the server (or alternate cd which I can modify the instructions to work with the server) using the fakeraid system?

In case it matters the server is going to be used at home for personal web pages, file, backup and e-mail for myself and my wife.

---

### Post by windependence on 2008-08-07
Are you sure it's fakeraid? Have you tried setting up an array and installing on it? Sometimes it will actually be fine for you.

-Tim

---

### Post by CyberCowboy on 2008-08-07
> **windependence said:**
> Are you sure it's fakeraid? Have you tried setting up an array and installing on it? Sometimes it will actually be fine for you.

-Tim

Yes, I did a full set up, saw both drives even though I had created an array in the controllers setup.  Went through the setup anyway (only partitioned and installed on one of the drives)

Upon the subsequent reboot it hung at the raid screen (where you press ctrl+i to go in and configure the raid) so I left it over-night since I was getting HD activity I figured it was mirror, but it's now been 2 days and I figure it's just failed (I am at work at the moment so don't have access to the box, but will try any suggestions tonight)

---

### Post by Krupski on 2008-08-07
> **CyberCowboy said:**
> I've been trying to get an answer to this for a couple days now and not having much luck, so hopefully I can get it here.

I am building an x64 "server" on an Optiplex 755 work station

Specs are
Quad Core 2.6 Ghz
8 GB RAM
2 500 GB Drives to be used in RAID 1

the system has an onboard fakeraid that I would like to utilize, however all of the instructions I'm finding for using fakeraid seem to want you to boot from the LIVE CD, which is desktops.  Where can I find a reasonable walk-through for setting up the server (or alternate cd which I can modify the instructions to work with the server) using the fakeraid system?

In case it matters the server is going to be used at home for personal web pages, file, backup and e-mail for myself and my wife.

I built a very similar setup for my own use. It's an Intel DG33BU motherboard, 8GB of ram, two 1TB drives as RAID-1 and gigabit Ethernet.

I am not using any raid controller card or motherboard raid... I'm using Linux MDADM alone.

One thing you may wish to do to make your life a LOT simpler is to install Server on a compact flash card and use the hard drives SOLELY for storage (i.e. no Linux on them at all).

That way, if the array fails, you can still boot. You can also use 'dd' to make image backups of the CF card so that you can always "go back" to a known good install in case the latest "experiment" goes awry!  :)

By the way, if you're interested, check out this item:

[http://www.addonics.com/products/flash_memory_reader/adebidecf.asp](http://www.addonics.com/products/flash_memory_reader/adebidecf.asp)

It's a nice little card with a 40 pin female IDE connector on it and a Compact Flash socket on the other end.

You just stick the card into an IDE/ATAPI connector on your motherboard, plug in the CF card and you can install to and boot from the CF card.

Ubuntu Server 8.04.1 runs just fine on a 4GB CF card... 2G for Linux and 2G for swap space.

Here's a 'df -H' from my file server:

```

root@storage:/# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdc1              2.1G   612M   1.4G  32% /
varrun                 4.2G   893k   4.2G   1% /var/run
varlock                4.2G      0   4.2G   0% /var/lock
udev                   4.2G    37k   4.2G   1% /dev
devshm                 4.2G      0   4.2G   0% /dev/shm
/dev/md0               993G   330G   663G  34% /home/shared

``` 

As you can see, the OS fits very comfortably in 2 GB.

Good luck!

-- Roger

---

