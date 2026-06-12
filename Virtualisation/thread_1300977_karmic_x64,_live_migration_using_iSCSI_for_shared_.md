---
title: "karmic x64, live migration using iSCSI for shared disks problem"
date: 2009-10-25
forum: Virtualisation
---

### Post by mkutsevol on 2009-10-25
Hi All!
I have such a test environment:
2 almost identical servers with latest karmic x64 server. Let's call them server-virt00 and server-virt01.
On both of them I installed open-iscsi, open-iscsi-utils. 
On server-virt01 I installed iscsitarget. 
Using CHAP auth for discovery and login
ietd.conf
```

IncomingUser * *
OutgoingUser * *
Target iqn.2009-10.lan.server-virt01:mirror.lvm.liga
        Lun 0 Path=/dev/server/liga,Type=blockio
        IncomingUser * *
        OutgoingUser * * 
Target iqn.2009-10.lan.server-virt01:mirror.lvm.kants
        Lun 0 Path=/dev/server/kants,Type=blockio
        IncomingUser * *
        OutgoingUser * * 
Target iqn.2009-10.lan.server-virt01:mirror.lvm.ebox
        Lun 0 Path=/dev/server/ebox,Type=blockio
        IncomingUser * *
        OutgoingUser * * 
Target iqn.2009-10.lan.server-virt01:mirror.lvm.ebox_new
        Lun 0 Path=/dev/server/ebox_new,Type=fileio
        IncomingUser * *
        OutgoingUser * * 
Target iqn.2009-10.lan.server-virt01:mirror.lvm.zimbra
        Lun 0 Path=/dev/server/zimbra,Type=fileio
        IncomingUser * *
        OutgoingUser * * 

```iscsid.conf - not the full config, just what I changed
```

node.startup = automatic
node.session.auth.authmethod = CHAP
node.session.auth.username=*
node.session.auth.password = *
node.session.auth.username_in = *
node.session.auth.password_in = *
discovery.sendtargets.auth.authmethod = CHAP
discovery.sendtargets.auth.username = *
discovery.sendtargets.auth.password = *
discovery.sendtargets.auth.username_in = *
discovery.sendtargets.auth.password_in = *

```iscsid.conf files are identical on both hosts.
When I start VM on any of two hosts it starts and works ok. I can stop it and run on the other one. but when I try to "virsh migrate --live liga qemu+ssh://server-virt00/system" I can see network traffic, it moves memory and starts the VM on the other host, but it is hanging.
And I ran out of ideas what to do. Any help will be appreciated! 
Thanks!

---

