---
title: "Can a vmware guest access a physical disk of the host?"
date: 2009-02-25
forum: Virtualisation
---

### Post by samosamo on 2009-02-25
I am running ubuntu-server 8.10 with vmware-server 2.0

I would like the guest to directly access a RAID array.  I'm pretty sure this is possible because Parallels on my Mac does it. I'm just not sure how to go about it.

---

### Post by whoop on 2009-02-25
Running a bridged network guest is about the same as running a real machine. If the raid array is accessible via your local network your vmware guest can reach it.

---

### Post by bodhi.zazen on 2009-02-25
I do not think VMWare Server 2.0 can directly access your hard drive (server 1 on the other hand can).

You only option is to use a network protocol (ftp, Samba, sshfs, etc).

---

### Post by samosamo on 2009-02-26
That's too bad.  My next question is, how can I get better speeds when transferring data from guest to host?  I currently get gigabit speeds which makes sense of course, since the switch is gigabit.

---

### Post by Cybie257 on 2009-02-26
> **samosamo said:**
> That's too bad.  My next question is, how can I get better speeds when transferring data from guest to host?  I currently get gigabit speeds which makes sense of course, since the switch is gigabit.

My experience with VMWare workstation has proven (when windows is the guest OS), that mapping the drives provides better speeds rather than through the network share. Dunno why, but it's usually about 2-3 X's faster. I've even found the same to be true when using VirtualBox. 

-Cybie

---

### Post by samosamo on 2009-02-26
That would be weird because "mapping" the drives is still SMB going through the network.

This happens to be linux guests anyway.

---

### Post by veloce on 2009-02-26
> **samosamo said:**
> That's too bad.  My next question is, how can I get better speeds when transferring data from guest to host?  I currently get gigabit speeds which makes sense of course, since the switch is gigabit.

For the quickest transfers between guest and host, use the "host only" network rather than bridged.

---

### Post by samosamo on 2009-02-27
> **veloce said:**
> For the quickest transfers between guest and host, use the "host only" network rather than bridged.

Perfect.  Bridged tops out at 15MB/s.  Not sure why.  Host-Only tops out at 30, where the CPU causes a bottleneck

---

### Post by dcstar on 2009-02-28
> **samosamo said:**
> Perfect.  Bridged tops out at 15MB/s.  Not sure why.  Host-Only tops out at 30, where the CPU causes a bottleneck

One would assume that Bridged has to use the TCP/IP stack twice because you are using two distinct IP addresses, whereas Host does not and has far less comms overhead.

---

### Post by HermanAB on 2009-02-28
You should try NFS.  It should be much faster than Samba.

Cheers,

Herman

---

### Post by samosamo on 2009-02-28
> **HermanAB said:**
> You should try NFS.  It should be much faster than Samba.

Cheers,

Herman

Read the thread, no one is using samba :)  I'm using NFS

---

### Post by bodhi.zazen on 2009-02-28
> **HermanAB said:**
> You should try NFS.  It should be much faster than Samba.

Cheers,

Herman

I prefer samba to nfs for security reasons. If you are using windows guests, nfs will be more difficult (it is possible to mount a nfs share on windows, but it takes more effort).

nfs has some speed advantages and IMO does a better job with permissions.

---

