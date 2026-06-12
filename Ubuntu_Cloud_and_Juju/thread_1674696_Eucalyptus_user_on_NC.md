---
title: "Eucalyptus user on NC"
date: 2011-01-24
forum: Ubuntu Cloud and Juju
---

### Post by mcanonic on 2011-01-24
Hi,
I followed the instruction here:
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)
and everything was fine until "euca-describe-availability-zones verbose" command, where I got:
```

mcanonic@minicloud02:~$ euca-describe-availability-zones verbose
AVAILABILITYZONE        cluster1        193.206.55.172
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0000 / 0000   1    192     2
AVAILABILITYZONE        |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0000   2    512    10
AVAILABILITYZONE        |- m1.xlarge    0000 / 0000   2   1024    20
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    20

```

That means there is no NC. So I tried to discover one and I found it:
```

mcanonic@minicloud02:~$ euca_conf --discover-nodes
New node found on 193.206.55.173; add it? [Yn] 
New node found on fe80::221:9bff:fefd:ccb; add it? [Yn] 

INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.
Warning: cannot file file node-cert.pem in //var/lib/eucalyptus/keys/
Warning: cannot file file cluster-cert.pem in //var/lib/eucalyptus/keys/
Warning: cannot file file node-pk.pem in //var/lib/eucalyptus/keys/
Warning: cannot file file cloud-cert.pem in //var/lib/eucalyptus/keys/

Trying rsync to sync keys with "193.206.55.173"...Warning: Permanently added '193.206.55.173' (RSA) to the list of known hosts.
eucalyptus@193.206.55.173's password:

```

The problem is: must I create a eucalyptus user on NC? Why this is not documents in [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall) ?

Thanks,
  Massimo

---

### Post by kim0 on 2011-01-24
AFAIK, it should have worked, however it seems to have failed this time ? Feel free to contribute to improving the documentation. A section on debugging such UEC problems would be great!

---

### Post by mcanonic on 2011-01-25
> **kim0 said:**
> AFAIK, it should have worked, however it seems to have failed this time ? Feel free to contribute to improving the documentation. A section on debugging such UEC problems would be great!

Hi,
thanks for replying. First of all, does eucalyptus user must be created in NC?

What do you exactly mean with "debug session"?

Thanks,
 Massimo

---

### Post by mcanonic on 2011-01-25
> **mcanonic said:**
> Hi,
thanks for replying. First of all, does eucalyptus user must be created in NC?


Ops, I just tried to create an eucalyptus user on my NC and I got:
```

mcanonic@minicloud03:~$ sudo adduser eucalyptus 
adduser: The user `eucalyptus' already exists.

mcanonic@minicloud03:~$ ls /home/
mcanonic


```

I'm not an expert on Ubuntu, but it seems strange to have a user without a directory in /home. But I did not set it, and I have no idea which password he has.

M

---

### Post by mcanonic on 2011-01-25
I have re-installed the two systems, using DHCP and now the NC is registered (as I can see in the avalability-zone output)

Last time, the NC did not find the Walrsu storage during the installation.

I'm not sure if this is related to DHCP, but this is what happened.


Hope this helps.
 M

---

### Post by s7upify on 2011-02-02
When you install UEC it installs a Eucalyptus user for you.

I think you are getting the password prompt because you did not set up shared keys between the Eucalyptus users.

See section 2.2.3 in the Ecalyptus Beginner's Guide: UEC Edition v2.0

---

