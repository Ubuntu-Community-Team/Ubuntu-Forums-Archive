---
title: "&quot;Hybrid Cloud&quot; - OpenNebula/Eucalyptus/etc."
date: 2010-03-17
forum: Virtualisation
---

### Post by binwiederweg on 2010-03-17
Hello everyone,

I'm having a hard time in understanding some parts of cloud computing, esp. what the exact definition of a "Hybrid Cloud" is. If you guys could help me with the following questions, that would be great. Thanks.

                                 
[LIST]
[*]Both OpenNebula and Eucalyptus have so called cloud controllers. Why     is there a dedicated machine to handle the cloud? Can it be     on the same host as a node?
[*]OpenNebula     supports 'hybrid clouds'. What exactly is the definition of a hybrid     cloud?
[LIST]
[*]Is         it only a common interface for completely different clouds?
[*]Or is it possible in a hybrid cloud to move images between different clouds? For example, move a KVM/QEMU image to Amazon EC2 with OpenNebula?
[*]If it is the former one (just a common interface), how is it possible to "scale out" if the images are incompatible?
[/LIST]
     
[*]Eucalyptus     says it is EC2 compatible, but it seems to me it it only API-compatible, not image-compatible.
[LIST]
[*]Can         one move a Amazon image AMI to a eucalyptus cloud?
[/LIST]
 
[/LIST]
 Thanks! 

Regards,
Philipp

---

