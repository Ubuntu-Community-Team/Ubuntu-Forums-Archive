---
title: "Virtualized file server best practices?"
date: 2013-11-09
forum: Server Platforms
---

### Post by junk.here on 2013-11-09
I would like to set up a virtual file server, but I have no idea where to even start. Everything I can find on Google involving a SAN, whereas in my case the disks will be directly attached to the host.

---

### Post by tgalati4 on 2013-11-09
What is the Use Case?  Personal or Small Business?  Do 100 PC's need access to the files or 10,000?  What other services do you need to run on the server?  Typically serving files requires little CPU load, so any virtual machine that is running mail or print services could also act as a file server by simply running SAMBA and setting up your shared file mounts.

---

### Post by TheFu on 2013-11-09
File server best practices depend on many things.  Running a server in a home is very different from running in a small biz or for an enterprise.  Is the data just recorded TV shows or is it regulated health care data or regulated financial data?  What sort of permissions management is needed - are userIDs enough, groups or do you need ACLs?  Which clients will access the files?  The wider that list is, the more likely that least-common-denominator solutions will be wanted. There are major drawbacks ... heck ... just having non-UNIX clients is a huge drawback.

So - try to list all the needs, users, bandwidth, sensitivity, file sizes, location of users, network limitations, and clients you can.

I can say that a best practice is to have great backups, regardless of everything else.  Backups are more important than RAID.

---

### Post by junk.here on 2013-11-10
I'll try to answer the questions to the best of my ability:

This server will reside in a primarily Windows home environment. Users will be accessing their files via a combination of 802.11n and gigabit ethernet. As for what kinds of files will be stored on there, I guess it'll just be the kinds of files a typical family would have - everything from text documents and PDFs to videos. As far as permissions management is concerned, I've always used ACLs on Windows, but then again that's about all NTFS supports - perhaps Linux has something better?

---

### Post by TheFu on 2013-11-10
> **junk.here said:**
> I'll try to answer the questions to the best of my ability:

This server will reside in a primarily Windows home environment. Users will be accessing their files via a combination of 802.11n and gigabit ethernet. As for what kinds of files will be stored on there, I guess it'll just be the kinds of files a typical family would have - everything from text documents and PDFs to videos. As far as permissions management is concerned, I've always used ACLs on Windows, but then again that's about all NTFS supports - perhaps Linux has something better?

Do not put the storage for the files "inside" the VM OS. The VM image needs to have just enough OS storage to do those "file server" things you need, but storage for all the data should be external - probably on the same physical host - definitely in a different partition. You can use multiple NAS devices for the storage too. Look for iSCSI or AoE NAS devices, but NFS can be fine for smaller budgets.  The VM / partition can be 6G or so. Here is my partition for the OS:
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1       6.4G  3.3G  2.8G  54% /
```

You can either setup LVM2 partitions at the hostOS to be mounted in the guest VM or use NFS. LVM has their own "best practices" to be followed.  Do not use LVM **inside** the guestOS ... others might have a different opinion. I've been burned, so I am gun shy.

Samba is THE server to make CIFS shares available to Windows and other clients.[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide) is a good start. Always use per-user access. It is very well understood and works with great performance. Most end-users from Windows don't notice the permissions. You can setup remote mounts for clients based on IP, login, groups, or open to everyone.  Read-only or read-write by use is the normal method.  There are special setups for UNIX-HOME directories with it good if the users are familiar with networked storage. 

I have NEVER used any GUI tools to setup Samba.  Adding 15 lines to a samba config file seems easier than P-n-C on 5 tabs and hoping the GUI translates my intentions correctly.

Samba4 includes AD-type features. It can be a domain controller, never used it myself.  Looked at using it a few weeks ago for a simple home-share requirement. Setup seemed very complex to me. I'm a simpleton. I have used Samba3 and older for 20+ yrs in shared environments.  The performance is fantastic.  Anyway, after looking at Samba4 about 20 minutes, removed it, installed samba v3.x and had my shares working 3 minutes later.

UNIX clients should use NFS, not samba/cifs/smb access. Even if the same storage areas are available over CIFS, NFS can be provided too. NFS lets almost all native file permissions to be honored by remote clients. Avoid NFS over wifi the wavy nature of wifi connections does not support the guaranteed bandwidth necessary.

For some-times connected clients, sftp might be an easier connection. WinSCP is a good client.  It is based on ssh, so key-based authentication from anywhere in the world is considered secure. sftp comes for free with ssh, which is how you will administer the servers anyway.

Don't know if I've answered the questions at the appropriate level or not. Hope so.

---

### Post by Vegan on 2013-11-10
You would probably be better off simply buying one of those NAS boxes I see more and more. I like them for backup targets etc

---

### Post by TheFu on 2013-11-10
> **Vegan said:**
> You would probably be better off simply buying one of those NAS boxes I see more and more. I like them for backup targets etc

SmallNetBuilder.com has comparisons if you need more storage than a $99 dual-HDD low-end device provides.
Storage selection can become very complex and costly.  It is really amazing what a $100 Atom box can accomplish with a GigE NIC and 4 SATA ports, in comparison to those $600+ single-purpose devices.

---

### Post by tgalati4 on 2013-11-10
Not to mention that the operating systems for most NAS boxes are atrocious.  You want a Synology box or Netgear, since they run some flavor of linux and have better management control.  If you want to learn some new skills, find an old PC and install *freenas* on it or simply Ubuntu 12.04 and set up your file shares.  Put in a SATA card so you can expand the number of disks that you can add as your file needs expand.  Most PC's have 2 to 6 SATA ports.  So add a card if you need more than that.

---

### Post by junk.here on 2013-11-10
I've never come across a remotely decent consumer-grade NAS box. All of the ones I've tried have slower than USB 2.0 transfer rates, despite offering "gigabit connections".

The entry-level SMB-grade NAS boxes are pretty good, but for the price of one of those I could get an entire PC.

I already looked into FreeNAS - unfortunately, it doesn't work with just any old PC since ECC RAM is a requirement. Unfortunately, the only box I have that has ECC RAM is the one my VMs are currently running on so I would have to get another one (~$400) if I were to go that route.

---

### Post by tgalati4 on 2013-11-10
You can run the older freenas which is called [http://www.nas4free.org/](http://www.nas4free.org/) and I have it running on a Pentium 1, 166MHz PC overclocked to 233MHz with a SATA card and several terabytes of storage using ZFS.  Works just fine for a home network.

---

