---
title: "Problem with AWS EC2 c3.large with Ubuntu 14 HVM virtualization"
date: 2014-09-10
forum: Virtualisation
---

### Post by coewar on 2014-09-10
There is a problem with the combination of Ubuntu14 HVM and c3.large. In /var/log/syslog this type of error outputs every minute:

```
kernel: [ 1152.732091] xen:balloon: reserve_additional_memory: add_memory() failed: -17
```


I tested Ubuntu14 HVM c1.medium, t2.micro and have not seen this.
I also tested with Ubuntu14 PV c3.large and have not seen this.

To duplicate this I installed no software or did anything at all other than launch an instance with 1 NIC. It makes no different if it's in VPC or not.

I also see that on the problem instance, I do not see the following in the log which I do see on the instances that do not have the failure:

```

ec2: #############################################################
ec2: -----BEGIN SSH HOST KEY FINGERPRINTS-----
ec2: 1024 7f:53:xxx5b:03:03:d4:2d  root@xxx (DSA)
ec2: 256 1a:51xxxb9:6d:d1:ca:f0:ed:b0  root@xxx  (ECDSA)
ec2: 2048 1e:b3:c2xxxcb:83:32:bf:46:a6:dd  root@xxx  (RSA)
ec2: -----END SSH HOST KEY FINGERPRINTS-----
ec2: #############################################################
```

---

