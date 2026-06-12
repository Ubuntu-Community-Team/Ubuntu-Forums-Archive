---
title: "problem with NFS permissions on NAS"
date: 2009-10-21
forum: Security
---

### Post by keevill on 2009-10-21
I have a Network Attached Storage ( Adaptec ) which I can access and read/write files from Windoze clients.
I am trying to migrate most of the clients to Ubuntu 9.0.4.
I can access the files on the NAS and read them but I cannot change or write to the server.
I have just discovered that the NAS does not seem to support Samba but it does support NFS.
Therefore I did the following on the Ubuntu client
 
I installed portmap nfs-common package and made the mount point on the Ubuntu client but the problem remains with one small difference.
This time I can Create a NEW file on my client and save to the server but I still only have read access to the existing files on the server.
Any ideas anyone?

---

### Post by cariboo on 2009-10-21
Is there a way to access the nas using ssh or some other protocol?

---

### Post by keevill on 2009-10-22
> **cariboo907 said:**
> Is there a way to access the nas using ssh or some other protocol?

Well there is the option of snmp or ftp but I don't think that's gonna work.
I can report that I have now resolved the issue with an acceptable caveat.
If I enable the nfs on the server and set permissions on a by user basis, it works but .. 
I have to give the UIN and IP address of each client.
Assuming that the default UIN of 1000 is on each client and if I change my current network settings from DHCP to Fixed IP, then it works.
There doesn't seem to be a way to set the nfs permissions without this direct mapping to each machine.
Bit limiting but just about workable I guess.
Perhaps the way to go is a Linux file server but that's for the future.

---

