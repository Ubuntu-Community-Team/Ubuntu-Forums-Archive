---
title: "SuperMicro Server Install Woes"
date: 2007-06-26
forum: Server Platforms
---

### Post by Gefunk on 2007-06-26
Hello all,

I am attempting...have been actually to install 7.04 on a SuperMicro server that was given to me.  It has 4 pentium 4's at 3.0, 2 gigs of ram and 3 80 Min SCSI drives with NO internal raid card.  This means that the backpane (sca 742) is running the drives.  I do not really care if there are 3 seperate 40 gig drives but I would like to get server installed.  It makes it to where you can hit enter to install but afterwards it gives me what appears to be hex and a countdown for 30 seconds and it will repeat every 30 seconds.  Any ideaS?  Thanks.

---

### Post by ricrac on 2007-06-26
Was/is it running an operating system already? win, freebsd, linux?
Did you do a memory test?

If you have good online bandwidth, download a few live cd's from various distros. ubuntu, fedora, suse, knoppix, etc.

If no livecd will boot using it's available boot options:

Try LFS until you find the boot problem, physical, driver or kernel. Then try to load driver, add boot option, etc. to install.

Add an IDE drive and unplug scsi until installed, then add driver and use scsi as data partitions.
I always use IDE/SATA/FLASH or cdrom to boot custom driver kernels.  IDE is /boot and has recovery patition, SCSI/raid/san etc. can be entire system or just "data" partitions.

Call or surf supermicro, they have great support.

I support and use many dual and quad supermicro boards, they work great.  I use custom linux, custom freebsd, RHEL, SUSE, Mandriva, haven't tested Ubuntu server on any dual systems yet. All the quad's are custom, usually with that much spent you want more than any distro can provide and it's dedicated to a single task (dbserver often) .  

If it were me, I'd try Centos first and then use to help diagnose/assist your Ubuntu install.

Last ditch efforts, not recommended unless all else fails, these could make things worse.
Modify hardware - unplug scsi and turn off in bios, remove all but one cpu, remove memory to below 3+gig (already there)

---

### Post by Gefunk on 2007-06-27
Wooha, thanks for the great reply...definitely not expecting that.  Anyway, almost all live cds (Fedora 7, Ubuntu, etc) function....and GPart will see the drives on each live cd.  I will try CentOs though, I used them for a while in a college class and was impressed, I will see what happens.  Thanks for the help and I will post back anything for anyone else to use later on.

---

