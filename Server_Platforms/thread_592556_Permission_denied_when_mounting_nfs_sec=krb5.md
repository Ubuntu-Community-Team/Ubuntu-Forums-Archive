---
title: "Permission denied when mounting nfs sec=krb5"
date: 2007-10-26
forum: Server Platforms
---

### Post by jbardin on 2007-10-26
Hi

Running a new gutsy server, and trying to get krb5 nfs working.

Clients can mount sec=sys, but when sec=krb5, they report 
"mount.nfs: Permission denied"

On the server, the only message I see is:
 mountd[13330]: authenticated mount request from client.fqdn:938 for /export (/export)

The clients can mount krb5 from other servers, so I know kerberos is working.

I have RPCSVCGSSDOPTS="-vvv -rrr -iii", and nothing in  the logs, so it seems it's not getting that far.

I also put ALL:ALL in the hosts.allow just to bu sure.

How can I get more information from the server daemons to help troubleshoot?

---

### Post by kwcoffman on 2007-10-26
What does your /etc/exports file look like on the server?  What does the output of "exportfs -v" on the server show?

Are you using nfsv3 or nfsv4?   If it is v3, then rpc.svcgssd is not involved in the mount.

If none of that gives a clue, it may be necessary to look at a packet trace to see exactly what is failing.

---

### Post by jbardin on 2007-10-27
`exportfs -v` yields
/export      10.0.0.0/24(ro,wdelay,root_squash,no_subtree_check)
/export      gss/krb5(rw,wdelay,root_squash,no_subtree_check)


I'm trying to test this with nfs3, because I don't have nfs principal keytabs for my dev clients yet. 

I've tried using the usual exports format of:
/export    10.0.0.0/24(ro)
/export    gss/krb5(rw)

I've also tried the new syntax, which the man pages say is supported, and it doesn't give any errors on the server
/export    10.0.0.0/24(sec=krb5,rw)

Thanks
-jim

---

