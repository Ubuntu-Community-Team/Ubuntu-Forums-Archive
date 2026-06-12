---
title: "no internet on 9.10 VM on 8.04 host"
date: 2009-11-03
forum: Virtualisation
---

### Post by muteXe on 2009-11-03
Hi,
Running virtualbox 3.0.8. Since updating to this version both my ubuntu 9.10 and slackware 13 VMs no longer have internet access. The host system is ubuntu 8.04, on a wireless internet connection.

I keep reading that I have to do some port forwarding. Is this true? They both worked ok with my last version of virtualbox.

Cheers in advance,

mute

---

### Post by Cypher on 2009-11-03
In VB you need to setup a NAT between the virtual Ethernet adapter created in VB with your real physical connection..

Regards

---

### Post by muteXe on 2009-11-03
Thanks for the reply.
I've never needed to this with any VM in any other version of VB before.... Can you point me where and how to do this please?  Do i just have to mess with settings in VB or mess with settings on the host or the guest or all of the above?
Thanks again,

mute

---

