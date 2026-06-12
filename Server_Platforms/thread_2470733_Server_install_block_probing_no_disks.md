---
title: "Server install block probing no disks"
date: 2022-01-09
forum: Server Platforms
---

### Post by tsmithmuskegon on 2022-01-09
Ubuntu-20.04.3-live-server-amd64.iso on a USB.
Media check comes back OK

I cannot get past the "Block probing did not discover any disks" message when trying to install.

A non-profit gave me their old server of around 2014 vintage:

HP Proliant ML 350P Gen8
(1) Intel 2.50 GHz, 10MB L3 cache
(2) 450 GB model: EF0450FARMV

Controllers are HP AHCI SATA v0.90 (one says v0.84)

Both storage disks are bad? flash orange and turn to solid orange when booted. I do NOT need any data saved.
In the config for arrays:
View logical drive - (1) RAID1 450GB Failed
If I delete this logical drive and try to create a new one " there are no physical drives"

In the BIOS I have tried a boot with PCI Device Enable/Disable->HP Smart Array P420i controller disabled - same result

Whatever I try I still come up against "Block probing did not discover any disks"
Is it possible to install the the OS without the storage disks working?

PS: very much a Linux server newbie

---

### Post by TheFu on 2022-01-09
I vaguely remember that HP 3xx series servers became incompatible with Ubuntu a few releases later. Don't trust my memory. I have no special knowledge about this model and haven't loaded Ubuntu onto any physical server hardware in over a decade.

Here's where it was supported: [https://ubuntu.com/certified/201309-14183](https://ubuntu.com/certified/201309-14183) - 2014.
Here's the HPE answer (no answer): [https://community.hpe.com/t5/ProLiant-Servers-ML-DL-SL/Ubuntu-Server-16-04-on-HP-Proliant-ML350P-Gen-8/td-p/6994846](https://community.hpe.com/t5/ProLiant-Servers-ML-DL-SL/Ubuntu-Server-16-04-on-HP-Proliant-ML350P-Gen-8/td-p/6994846)

This has specific settings [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=783066](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=783066)
> Disable Dynamic Smart Array BS320i and enable SATA AHCI in BIOS. Non non-free firmware required!

Not anything you haven't already tried.

If you are new to Linux, attempting to run on difficult hardware isn't what I'd recommend.  Setup an OS that you know well on the hardware, then put the "Ubuntu Server 20.04" into a virtual machine, which will hide all the complexities of the hardware from you. Not having to deal with hardware issues is good to avoid whenever possible.  Of course, this assumes you are familiar with running a hypervisor. That is a base skill these days.

Old servers are often like old boats.  Full of rot and just eating money (usually electricity and heating a room) and very noisy. In winter, the heat isn't an issue.  I've seen people get huge servers for home that cost $5/day to run in electricity.  They have this crazy powerful system, but only use it a few hours a month due to the extra costs involved.  A $300 Ryzen system is usually faster.

---

### Post by MAFoElffen on 2022-01-10
Here's what i know about Installing Ubuntu on Dell PowerEdge and HP Proliant Servers... If it comes up that an Ubuntu Install ISO (whether Desktop or Server Edition) cannot find any disks... If it has a Hard RAID card, which they did...

I have been doing server hardware for decades,and am still a certified HP, Dell, and Lenovo Service Tech. So I do know a bit about them. LOL

The disks on those servers are physically connected to the RAID card, not as SATA members connected through SATA connections from the system board. So you have to set them up on the RAID card first, for the physical system to be able to see them... For the Linux system to them on that system. The connections have to be made, even if some of those connections end up being 'logical'. Does that make sense now?

On startup, hit the hot-keys to get into the RAID card setup... If you do not want to setup RAID... Then setup the disks on the card as either JBOD or single disk RAIDO. (Some cards do not have JBOD, so you can get around that by tricking the card, by setting those single disks as single-disk RAID0 arrays...)

I like old metal... Though using old server hardware uses a lot of power, are very slow to boot up (all the hardware and redundancy checks), and are very noisy!!!

EDIT:
I just remembered that on some old HP and IBM Servers, on some specific models, I had to use their branded bootable setup disks to be able to setup their integral RAID cards. I am sorry if I don't remember which models those were. But be aware of the messages coming up during POST, and if you do not see a message with hot-keys to get into the RAID card setup, then that is another option.

---

