---
title: "Separate storage / VMWare"
date: 2008-09-17
forum: Virtualisation
---

### Post by TheGameAh on 2008-09-17
Are any of you guys out there running your VMs with separated storage?  We're a small business, so a SAN is out of the question, but I see a lot of stories of using NFS as their backend datastore.  I would love to experiment with the use of central storage.

I was thinking about building a simple Linux NFS datastore, and using that as the backend storage.  Right now, everything is DAS (direct attached), with so much wasted storage and resources.

But everything I read about seems to suggest there is no cheap way to go about this.  Everything besides a SAN or expensive NAS is unreliable.

Are there any success stories out there?

---

### Post by SecretCode on 2008-09-22
No replies to this yet?

Separated storage should bring lots of benefits. But I'm not sure whether the benefits (or the issues) are particular to running in VMs. The only hassle with VMs would be making sure that your networking is set up clearly (bridging might be better than NAT ... and if these are busy, production VMs, having a dedicated NIC).

What kind of "unreliable" do you mean? For a small business, an NFS server should work. (Of course SAN is out of the question).

How small a business? How many VMs, on what hosts? How much total storage?
eta: What apps are your VMs running, and how busy are they?

---

### Post by TheGameAh on 2008-09-24
The projects I have in mind might be completely out of the question.  So many things at once.

We have about 170 gigabytes in file sharing, plus some other services (Blackberry, Terminal Server, Solidworks Vault, Exchange, etc.)

I got Blackberry and Terminal Server residing on the same physical box with no problems at all.  (This is not on ESX mind you, just freeware VMWare server on CentOS).  Disaster recovery is a breeze with just worrying about the VMs themselves.  So this got me thinking, how far can I take this?

Well, from everything I've researched, doesn't look like very far.  You need ESX/SAN to go really far.  Apparently Exchange doesn't work very well on freeware VMWare server.  (About 50 gigs of Exchange data at the moment).  And 170 gigs of file sharing?  I've read that file servers aren't a good idea to virtualize because of the I/O.  

But if anyone else has any suggestions, comments, feel free to holler.  I was hoping it would be possible to build a 1 terrabyte or so of an NFS datastore (maybe minimal install of CentOS).  And have everything residing in VMWare on host machines that pointed to the NFS datastore.  But looks like there's just too many nagging issues.  A 300 gigabyte or so VM, mounted over an NFS connection?  Sounds scary.

For now, I'm just running directed attached servers, running the relatively static, low I/O servers as virtual machines.

---

### Post by HermanAB on 2008-09-24
Hmm, well, you are talking of very little storage space.  Nowadays it is very easy to build a 5 terabyte file server by using RAID5 with 6 of 1 TB drives in a single server chassis and accessing that over NFS is no problem at all.

Also, I would not allocate 300GB to a VM.  Most everything you need can be done in a 8GB image (the default VMware VM size).  Then mount the data share over NFS.  in other words, keep your data *outside* the VM.

Cheers,

Herman

---

### Post by TheGameAh on 2008-09-26
I like your suggestions, but my only issue is we use Active Directory, and Windows 2003 NTFS permissions to grant access.  So the file share needs to be on a Windows VM.

---

### Post by trmentry on 2008-09-26
> **TheGameAh said:**
> Are any of you guys out there running your VMs with separated storage?  We're a small business, so a SAN is out of the question, but I see a lot of stories of using NFS as their backend datastore.  I would love to experiment with the use of central storage.

I was thinking about building a simple Linux NFS datastore, and using that as the backend storage.  Right now, everything is DAS (direct attached), with so much wasted storage and resources.

But everything I read about seems to suggest there is no cheap way to go about this.  Everything besides a SAN or expensive NAS is unreliable.

Are there any success stories out there?

I wrote up a down and dirty guide to using iSCSI on esxi.

[http://ubuntuforums.org/showthread.php?t=917155](http://ubuntuforums.org/showthread.php?t=917155)


But if you run vmware 2.0 it does have the ability to use NFS mounts or create other datastores.

so you could put up a server with nfs and export those to the vmware server and create a new datastore using the nfs or mounted nfs. 

i've not tried the nfs thing yet in 2.0.. but I created a new datastore to use a directory under my raid5 array that i have in my fileserver.  (same server vmware is running on).

---

### Post by TheGameAh on 2008-09-29
You can do kinda the same thing on VMware 1.x, right?  Just use an exported NFS share on the VMWare host?

---

