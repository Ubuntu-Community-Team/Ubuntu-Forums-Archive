---
title: "vmware server 1.0.10 and ubuntu 10.04 i386"
date: 2010-09-12
forum: Virtualisation
---

### Post by Patrick Frank on 2010-09-12
There is a lot of forum postings floating around regarding vmware, but none of them brought a solution to my problem, maybe because the patches are not for my version.

vmware server 1.0.10
ubuntu 10.04 lts for i386

---

### Post by dcstar on 2010-09-13
> **Patrick Frank said:**
> There is a lot of forum postings floating around regarding vmware, but none of them brought a solution to my problem, maybe because the patches are not for my version.

vmware server 1.0.10
ubuntu 10.04 lts for i386

Do you **really** need Server?, Player 3.11 is a lot easier to install (and use) in 10.04.

---

### Post by FliesLikeABrick on 2010-11-29
Are there any solutions floating around for this?  I've tried working the existing patches for workstation 7 and server 2.0.2 in, but [unsurprisingly] haven't made any progress.

---

### Post by ExTruckie on 2010-11-30
Try what i did. See the following. Just posted it!!
[http://ubuntuforums.org/showthread.php?t=1634028](http://ubuntuforums.org/showthread.php?t=1634028)

---

### Post by dcstar on 2010-12-01
> **ExTruckie said:**
> Try what i did. See the following. Just posted it!!
[http://ubuntuforums.org/showthread.php?t=1634028](http://ubuntuforums.org/showthread.php?t=1634028)

Which has absolutely **nothing** to do with VMware** Server**.

---

### Post by JeremyA on 2010-12-07
I've been relying on my ubuntu 8.10 LTS server running vmware server 1.0.6 for years.  This beast has had a mix of vmware server and VirtualBox (PEULA version) guests running on it w/o incident for a very long time.

I upgraded to 10.04, because I figured it was time to start looking into kvm.

After the upgrade, I was entirely unable to get vmware-server 1.0 running.  I found that heavy virtualbox usage crashed my server entirely.  So I've been converting to kvm.

You can convert the flat vmware images to kvm/qcow2 format, and I've had good luck converting my vmware machines to kvm so far -- they're using a LOT less memory, and for the most part, they're equivalent with CPU usage (Though the rhel4.6 box is taking a bit more than it used to)

The bridging setup isn't that hard to get going, either.  It may be time for you to look into kvm -- vmware-server 1.0.x appears to be pretty much abandoned.

---

