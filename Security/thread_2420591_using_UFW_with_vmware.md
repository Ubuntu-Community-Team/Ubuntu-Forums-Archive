---
title: "using UFW with vmware"
date: 2019-06-07
forum: Security
---

### Post by marcbo on 2019-06-07
I have vmware installed and I use the guest Ubuntu OS as my primary platform for all work.

This is what I am trying to do.

Outside of the virtual environment of vmware, I want to block all internet traffic incoming and outgoing. However, I still need my interface enp0s25 (to get IP address and for DNS) to connect to my ISP and I want to be able to run apt-get update and apt-get upgrade. Further, I want to allow the network connection within vmware to access the internet (let's call the interface vm0 for now). 

So, there should be no internet activity except manually running apt-get commands outside of my vmware environment.

How do I do this with UFW?

*Note: My base system is Debian Stretch, but there should be a difference between Ubuntu and Debian when configuring UFW.

---

### Post by TheFu on 2019-06-07
```
sudo ufw reset
sudo ufw default deny incoming
sudo ufw enable
```
Might need to modify /etc/default/ufw to enable ufw at boot too.  Different flavors of Linux have different startup/enable methods. Also might need to enable it in **systemctl**.  IDK.  Debian is a little different.

---

### Post by marcbo on 2019-06-09
Hi Thanks for the reply. I'll have to check my settings, because I wasn't notified that you'd replied.

I found out how to do this in a simple manner. If I set ufw in my host OS to deny incoming and outgoing, that blocks all traffic from the host. I simply disable ufw if and when I apt update for security patches, etc.

Within vmware, I set ufw to deny incoming and allow outgoing. I also set the Network Adapter to Bridged instead of NAT, and run a VPN from within the guest OS, but not the host OS. (Also, I run a LAMP stack on the host and guest OS with a Tor service and use a system-wide proxy in both cases to 127.0.0.1:9050)

So now I have a system that can only be compromised within the vmware guest OS, while the host OS remains relatively safe. 

Further, I keep important documents in a share folder named vmshare, and I've changed my ~/.config/user-dirs.dirs file to reflect that vmshare directory location. (Changing $HOME to /mnt/hgfs/vmshare.)

In addition, on the host OS, I've set up a cron job with luckybackup to backup folder vmshare to a 32gb microSD every day.

Lastly, with the guest OS, I also have megasync actively running (on boot) to synchronize the contents of certain folders in ~/marc with /mnt/hgfs/vmshare and to then backup those folders in ~/marc to my end-to-end encrypted cloud storage in New Zealand.

I hope this experiment in redundancy and security helps someone else out there. **If you see any holes in my setup, please let me know!**

---

### Post by TheFu on 2019-06-09
Seems like a good setup, if you can take the inconveniences.  It is more secure than my setups, but a few notes:

Changing the HOME setting will have undesirable side effects. I don't see why this is needed at all. Just use the 

Most SD storage has limited write lifetimes.  I've destroyed name-brand, quality, storage devices in less than a year, by writing to it daily.  I have other SD storage that has been used as the primary storage for other computers which is 3+ yrs old without any signs of failure.  The main difference between these uses - the one that failed was written to nearly fill the storage routinely. The long lasting storage uses less than 25% of the total storage available.  Wear levelling matters to lifespan.

I suspect you mean ~marc/ not ~/marc/  Yes?

Security needs to have multiple layers. Trust no single layer, since there is likely to be a failure - either program failure or human error in the config or a bug.  Bridges are a security issue.  A better solution would be PCI passthru exclusive access of the NIC to the guest.

I don't know about either of those backup tools.  Backups need to be "pulled" by a backup server, so the client doesn't have any direct access. They need to be versioned, with enough versions to give the admins enough time to recognize any issues.  Think about what happens if a crypto-locker malware gains access to the client. If it has access to the backup storage, then that too can be encrypted.  Whereas if the backup server "pulls" the data, just a new, fresh backup, will be made which is huge.  Obviously the backup server cannot be hacked or all is lost.

I'm not a fan of VMware stuff, but that's more about the company management than the software.  VMware made 6 different hypervisor products at 1 point. They are all different and have different limitations.  VMware Workstation is much more trustworthy than the free offerings and has better GPU capabilities.  

KVM with libvirt and SPICE graphics are pretty awesome, BTW.  Why wouldn't you choose that over closed source?

---

### Post by marcbo on 2019-06-10
Hi. Thanks for taking the time.

> Changing the HOME setting will have undesirable side effects. I don't see why this is needed at all. Just use the

Maybe that was overkill. I didn't do it. I'm not sure what you were trying to say at the end of that sentence...

> Most SD storage has limited write lifetimes.  I've destroyed name-brand,  quality, storage devices in less than a year, by writing to it daily.  I  have other SD storage that has been used as the primary storage for  other computers which is 3+ yrs old without any signs of failure.  The  main difference between these uses - the one that failed was written to  nearly fill the storage routinely. The long lasting storage uses less  than 25% of the total storage available.  Wear levelling matters to  lifespan.

This I did not think about and I did not know. So I changed that backup option to another location on my SSD within my Host OS.

I'm not sure about this:
> I suspect you mean ~marc/ not ~/marc/  Yes?

If ~ equals /home, then what I meant by ~/marc is /home/marc.(A little confused about this.)

> I don't know about either of those backup tools.  Backups need to be  "pulled" by a backup server, so the client doesn't have any direct  access. They need to be versioned, with enough versions to give the  admins enough time to recognize any issues.  Think about what happens if  a crypto-locker malware gains access to the client. If it has access to  the backup storage, then that too can be encrypted.  Whereas if the  backup server "pulls" the data, just a new, fresh backup, will be made  which is huge.  Obviously the backup server cannot be hacked or all is  lost.

I'm just a loner over here. I don't have a server, except for my little laptop. I do keep multiple backup copies though. 7 in total. So if something goes wrong on day 5, I still have backups 1 through 4 to fall back on. Luckybackup is basically a copy or sync program. I'm not an expert with backups...

> I'm not a fan of VMware stuff, but that's more about the company management than the software.  

Of course, I don't know your beefs with that company, but I have similar feelings/suspicions. I don't like working with, and usually don't work with, any company that blocks access to it's instructional Wiki simply because you're using Tor. I personally think that's a red flag.

> KVM with libvirt and SPICE graphics are pretty awesome, BTW.  Why wouldn't you choose that over closed source?

To tell you the truth, I don't know. Opensource vs proprietary is usually at the top of my list in considerations. I suppose after going around in circles with Virtualbox, which drove me crazy, VMware just sort of worked. I'm not an expert at Virtualization either. But I will spend some time today looking into KVM. I'm using an older Thinkpad, which I love, and so I don't have to worry too much about graphic performance as it doesn't have a dedicated GPU that I know of.

Thanks for the input.

---

### Post by TheFu on 2019-06-10
> **marcbo said:**
> Hi. Thanks for taking the time.
  People took the time when I was learning. Just paying back.  Please do the same, if you can.

> **marcbo said:**
> 
Maybe that was overkill. I didn't do it. I'm not sure what you were trying to say at the end of that sentence...  I don't remember either. Probably something about using other, available, environment variables or symbolic links.  That's a common solution for having data files outside your HOME - setup symbolic links to the other location.  This is pretty common for those directories like ~/Music/, ~/Videos/ ~/Pictures/, ~/Documents/  that have been forced onto people by DEs.  Or you can stop using a DE completely and just use a window manager. I use fvwm.

> **marcbo said:**
> This I did not think about and I did not know. So I changed that backup option to another location on my SSD within my Host OS.  A backup **must** be on different physical storage to count at all.  SSDs also wear out, especially if they are nearly full.  I've had 2 fail in less than 3 yrs of use.  Now I have some new, well regarded, SSDs, but use less than 50% of the claimed storage. That should provide plenty of wear levelling options for the SSD controller.  I've read that 20% unused is sufficient to drastically extend the SSD life.  OTOH, for backups a $25 spinning USB3 disk is much more cost effective. Better if it has an external power supply so it won't be really slow.

> **marcbo said:**
> I'm not sure about this:

If ~ equals /home, then what I meant by ~/marc is /home/marc.(A little confused about this.)

~/marc/ is a directory inside HOME called "marc".
~marc/ is the home directory for a userid "marc" - that any other userid can use to access in that manner.
~/ is the home directory for the current userid, which might be marc or pete or steve.
The ~ ... asks the shell to use the **getent passwd $USER** command to fill in the correct directory from the password DB.  It doesn't assume /home/{something}, which is only used for non-corporate setups.  Well, if a ~/ is used, it simply fills in the environment variable for $HOME, but effectively that works in the same way because login pulls the data using getent to set HOME correctly.


> **marcbo said:**
> 
I'm just a loner over here. I don't have a server, except for my little laptop. I do keep multiple backup copies though. 7 in total. So if something goes wrong on day 5, I still have backups 1 through 4 to fall back on. Luckybackup is basically a copy or sync program. I'm not an expert with backups...

Anyways, you are doing pretty well having backups and multiple versions of it. If that works for you, FANTASTIC.

A real versioned backup tool can store 30-60-90 days of backups for very little over the storage required to store just 1 backup.  A versioned backup tool will managed the versions for you.  The backup tool I like is rdiff-backup. The last backup appears as a mirror, so getting 1 file back is a cp.  It is only the older "diffs" where using the tool to get files restored is helpful. The diffs are stored as diff.gz files, so we don't need the backup tool for restoring the backup from 17 days ago, though it is really helpful.

Anyways, I've posted so much here about rdiff-backup that interested people can find those threads, see some issues and some great things about it.  Every Sunday morning, I have my backup server make a report about the backups for every system. Here's the report for my main desktop system:```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Jun  9 01:15:06 2019         6.26 GB           6.26 GB   (current mirror)
Sat Jun  8 01:15:05 2019         68.9 MB           6.33 GB
Fri Jun  7 01:15:06 2019         12.0 MB           6.34 GB
Thu Jun  6 01:15:05 2019         10.9 MB           6.35 GB
Wed Jun  5 01:15:05 2019         15.7 MB           6.37 GB
Tue Jun  4 01:15:05 2019         14.0 MB           6.38 GB
Mon Jun  3 01:15:05 2019         63.0 MB           6.44 GB
...
Tue Apr 16 01:15:08 2019         12.6 MB           7.41 GB
Mon Apr 15 01:15:07 2019         17.1 MB           7.42 GB
Sun Apr 14 01:15:09 2019         24.0 MB           7.45 GB
Sat Apr 13 01:15:09 2019         14.3 MB           7.46 GB
Fri Apr 12 01:15:09 2019         11.3 MB           7.47 GB
Thu Apr 11 01:15:07 2019         11.0 MB           7.48 GB
```
So, 60 days of versioned backups for 6.26G of files only needs 7.48G of storage.  I can assure you that this is sufficient for my to restore the computer in about 30-45 minutes with all the data, all the programs, and all the settings on it at the time of the last backup.
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on 
/dev/vda1        20G   16G  2.6G  86% /
```
is the total storage on that machine - OS, my files, my settings, etc.  I keep large files elsewhere. I don't backup the installed OS, just the metadata about the installed OS so I can put it back quickly.  Oh - and my desktop runs inside a KVM virtual machine which is accessible from anywhere (within reason) on the internet through either a VPN (I run a VPN server at home) or ssh connection.

> **marcbo said:**
> 
Of course, I don't know your beefs with that company, but I have similar feelings/suspicions. I don't like working with, and usually don't work with, any company that blocks access to it's instructional Wiki simply because you're using Tor. I personally think that's a red flag.
 Around 2010 they gave all their paying clients whiplash by altering the way license costs were determined and their marketing department claimed it would be "better" for almost all their clients. It was going to cost our clients 2-3x more every year. For a few months we had to freak out our clients about the new pricing. We lost a few clients over it who we'd just finished moving to VMware 1 month prior to the new price announcement.  I'd been using a few other hypervisors for a while, but we preferred the safety of VMware ESX and the old pricing wasn't THAT bad.  Over the next 6 months, we migrated a number of clients to KVM+libvirt and never regretted it.  I still use KVM + libvirt here, just a more advanced setup with more flexible storage, faster systems, and more VMs on more physical systems.

> **marcbo said:**
> 
To tell you the truth, I don't know. Opensource vs proprietary is usually at the top of my list in considerations. I suppose after going around in circles with Virtualbox, which drove me crazy, VMware just sort of worked. I'm not an expert at Virtualization either. But I will spend some time today looking into KVM. I'm using an older Thinkpad, which I love, and so I don't have to worry too much about graphic performance as it doesn't have a dedicated GPU that I know of.
QEMU+kvm can used vmdx files, or whatever storage format the VMware tools you have are using. Just need to make the virtual machine virtual hardware closes enough to what VMware is presenting. For Windows guests, it is complicated. For Linux VMs, it is pretty trivial to move between hypervisors.  **qemu-img** can be used to change from one storage file type to another as you like.  There is much to like about qcow2, though I only have a few VMs using that. Most of my VMs use LVM LVs presented as block devices to the VM.  Probably not something a non-pro would do.  Crazy flexible.
 
Hopefully, this will be helpful too.  Take what is good for you and don't worry if nothing is. That's fine too. We're all in different places.

---

### Post by kevdog on 2019-06-12
Sorry to jump the thread -- but is a block device similar to thin provisioning?

---

