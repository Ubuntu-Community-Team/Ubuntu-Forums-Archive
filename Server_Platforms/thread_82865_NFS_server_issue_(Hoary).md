---
title: "NFS server issue (Hoary)"
date: 2005-10-27
forum: Server Platforms
---

### Post by Goriknak on 2005-10-27
Okay so have been using ubuntu at home for over a year and i have resently stated using it on my webservers.. Just love setting the whole thing up with apt-get, makes my life so much easier. 

however i have run into a little snag. 

I want to restart my NFS/portmap/whateverels deamons with out having to reboot the server since it halts on reboots (old pc).

right now i cant mount my nfs from the client pc.. allthough the daemon is running

when i do  rpcinfo -p 83.149.***.***  from the client i get 

   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32768  status
    100024    1   tcp  32768  status
    391002    2   tcp  32769  sgi_fam
 

It would seem i am missing some services..  probably being blocked by rpc


my hosts.allow is as follows 

portmap: 84.104.***.***
lockd: 84.104.***.***
mountd: 84.***.***
rquotad: 84.104.***.***
statd: 84.104.***.***
nfsd: 84.104.***.***

hosts.deny is blank 

etc/exports 

/www 84.104.***.***(rw,no_root_squash)

I have setup a nfs server at home before on ubuntu and ran into the same problem... i configured it correctly but i needed to reboot before i worked. 


Any help would be much apreciated. 

~Gori

---

