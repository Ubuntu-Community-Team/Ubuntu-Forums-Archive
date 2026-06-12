---
title: "samba question ???"
date: 2008-09-18
forum: Server Platforms
---

### Post by fouadk on 2008-09-18
hi everyone,,,,

i have an ubuntu server that acts as a samba server for windows active directory users....

my question is: is there is a way to add more samba server and make them act as one...think of it as load balancing, you can also think of it as more space separated....

is this possible ???

please help...

thanks in advance

---

### Post by Krupski on 2008-09-18
> **fouadk said:**
> hi everyone,,,,

i have an ubuntu server that acts as a samba server for windows active directory users....

my question is: is there is a way to add more samba server and make them act as one...think of it as load balancing, you can also think of it as more space separated....

is this possible ???

please help...

thanks in advance

You mean run additional Samba servers on the SAME machine?

There's absolutely no point in doing so.

---

### Post by fouadk on 2008-09-18
of course thats not what i mean....

i mean , have different machines, each one of them running samba...and in the end, make all these machines appear as one samba share for load balancing and to extend space

---

### Post by jamesrfla on 2008-09-18
> **fouadk said:**
> of course thats not what i mean....

i mean , have different machines, each one of them running samba...and in the end, make all these machines appear as one samba share for load balancing and to extend space

I think you can do that but I am not sure how. How many computers are going to be accessing this Samba server?

---

### Post by HermanAB on 2008-09-18
Coda and NFS can do Distributed File Systems.  I don't think Samba can.  You'll have to check on the Samba web site in the Official Howto guide.

Maybe you can run Coda on each server to do the DFS and run Samba on each physical machine.  That way you can point different users at the various Samba servers to distribute the load, while Coda takes care of the data replication between the servers.

Cheers,

Herman

---

### Post by fouadk on 2008-09-18
i have around 100 computers accessing that samba server....
the computers are active directory clients and the users are also active directory users so i cannot use NFS

---

