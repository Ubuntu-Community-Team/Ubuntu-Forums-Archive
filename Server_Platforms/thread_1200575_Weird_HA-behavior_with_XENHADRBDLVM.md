---
title: "Weird HA-behavior with XEN/HA/DRBD/LVM"
date: 2009-06-30
forum: Server Platforms
---

### Post by sussox on 2009-06-30
I have a HA-setup with Xen heartbeat lvm and DRBD. According to this howto: [http://www.asplund.nu/xencluster/xen-cluster-howto.html](http://www.asplund.nu/xencluster/xen-cluster-howto.html)

Im using 2 Poweredge R710. ha1 & ha2 with Ubuntu 8.04

I can do a manual live migration of the domU's without any problems. Also if i shutdown heartbeat on ha1 with init.d/heartbeat the domU's are migrated to ha2 sucessfully. 

Also, if i pull the plug on ha1, after a while the domU's start on ha2 (as they should).

However! When doing a "reboot" on ha1, domU's begin to migrate but then crashes on ha2. pasting ha-debug and xend.log below. 

Any ides why it keeps doing this? All i can think of is that some process is being killed to fast (when the domU's are beeing migrated, but i don't know what to look for.) Also, i ran a test couple of weeks ago with the same setup but on one R710 and a older shuttle and then there was no problem. Tried to redo the howto twice but with the same problem :(

Cheers! /Sussox

**ha-debug:**
```

heartbeat[28295]: 2009/06/30_13:46:12 info: Received shutdown notice from 'ha1.vbm.se'.
heartbeat[28295]: 2009/06/30_13:46:12 info: Resources being acquired from ha1.vbm.se.
heartbeat[28295]: 2009/06/30_13:46:12 debug: StartNextRemoteRscReq(): child count 1
heartbeat[29445]: 2009/06/30_13:46:12 info: acquire local HA resources (standby).
ResourceManager[29472]:	2009/06/30_13:46:12 info: Acquiring resource group: ha2.vbm.se xendomainsHA2
heartbeat[29446]: 2009/06/30_13:46:13 info: Local Resource acquisition completed.
heartbeat[28295]: 2009/06/30_13:46:13 debug: StartNextRemoteRscReq(): child count 2
heartbeat[28295]: 2009/06/30_13:46:13 debug: StartNextRemoteRscReq(): child count 1
ResourceManager[29472]:	2009/06/30_13:46:13 info: Running /etc/ha.d/resource.d/xendomainsHA2  start
ResourceManager[29472]:	2009/06/30_13:46:13 debug: Starting /etc/ha.d/resource.d/xendomainsHA2  start
ResourceManager[29472]:	2009/06/30_13:46:13 debug: /etc/ha.d/resource.d/xendomainsHA2  start done. RC=0
heartbeat[29445]: 2009/06/30_13:46:13 info: local HA resource acquisition completed (standby).
heartbeat[28295]: 2009/06/30_13:46:13 info: Standby resource acquisition done [foreign].
heartbeat[29559]: 2009/06/30_13:46:13 debug: notify_world: setting SIGCHLD Handler to SIG_DFL
harc[29559]:	2009/06/30_13:46:13 info: Running /etc/ha.d/rc.d/status status
mach_down[29573]:	2009/06/30_13:46:13 info: Taking over resource group xendomainsHA1
ResourceManager[29597]:	2009/06/30_13:46:13 info: Acquiring resource group: ha1.vbm.se xendomainsHA1
ResourceManager[29597]:	2009/06/30_13:46:13 info: Running /etc/ha.d/resource.d/xendomainsHA1  start
ResourceManager[29597]:	2009/06/30_13:46:13 debug: Starting /etc/ha.d/resource.d/xendomainsHA1  start
Starting auto Xen domains: hejsan(skip) *   [done] 
ResourceManager[29597]:	2009/06/30_13:46:13 debug: /etc/ha.d/resource.d/xendomainsHA1  start done. RC=0
mach_down[29573]:	2009/06/30_13:46:13 info: /usr/share/heartbeat/mach_down: nice_failback: foreign resources acquired
mach_down[29573]:	2009/06/30_13:46:13 info: mach_down takeover complete for node ha1.vbm.se.
heartbeat[28295]: 2009/06/30_13:46:13 info: mach_down takeover complete.
heartbeat[29696]: 2009/06/30_13:46:13 debug: notify_world: setting SIGCHLD Handler to SIG_DFL
harc[29696]:	2009/06/30_13:46:13 info: Running /etc/ha.d/rc.d/ip-request-resp ip-request-resp
ip-request-resp[29696]:	2009/06/30_13:46:13 received ip-request-resp xendomainsHA2 OK yes
ResourceManager[29715]:	2009/06/30_13:46:13 info: Acquiring resource group: ha2.vbm.se xendomainsHA2
ResourceManager[29715]:	2009/06/30_13:46:13 info: Running /etc/ha.d/resource.d/xendomainsHA2  start
ResourceManager[29715]:	2009/06/30_13:46:13 debug: Starting /etc/ha.d/resource.d/xendomainsHA2  start
ResourceManager[29715]:	2009/06/30_13:46:13 debug: /etc/ha.d/resource.d/xendomainsHA2  start done. RC=0
heartbeat[28295]: 2009/06/30_13:46:24 WARN: node ha1.vbm.se: is dead
heartbeat[28295]: 2009/06/30_13:46:24 info: Dead node ha1.vbm.se gave up resources.
heartbeat[28295]: 2009/06/30_13:46:24 info: Link ha1.vbm.se:eth0 dead.

```

**xend.log**

```
[2009-06-30 13:46:11 5499] DEBUG (XendCheckpoint:210) restore:shadow=0x0, _static_max=0x18000000, _static_min=0x0, 
[2009-06-30 13:46:11 5499] DEBUG (balloon:151) Balloon: 398436 KiB free; need 393216; done.
[2009-06-30 13:46:11 5499] DEBUG (XendCheckpoint:227) [xc_restore]: /usr/lib/xen/bin/xc_restore 4 7 1 2 0 0 0
[2009-06-30 13:46:11 5499] INFO (XendCheckpoint:365) xc_domain_restore start: p2m_size = 18800
[2009-06-30 13:46:11 5499] INFO (XendCheckpoint:365) Reloading memory pages:   0%
[2009-06-30 13:46:14 5499] INFO (XendCheckpoint:365) ERROR Internal error: Error when reading page (type was 0)
[2009-06-30 13:46:14 5499] INFO (XendCheckpoint:365) Restore exit with rc=1
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:1913) XendDomainInfo.destroy: domid=7
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:1930) XendDomainInfo.destroyDomain(7)
[2009-06-30 13:46:14 5499] ERROR (XendDomainInfo:1942) XendDomainInfo.destroy: xc.domain_destroy failed.
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/xen/xend/XendDomainInfo.py", line 1937, in destroyDomain
    xc.domain_destroy(self.domid)
Error: (3, 'No such process')
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:1553) No device model
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:1555) Releasing devices
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:1561) Removing vif/0
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:590) XendDomainInfo.destroyDevice: deviceClass = vif, device = vif/0
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:1561) Removing vbd/51713
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:590) XendDomainInfo.destroyDevice: deviceClass = vbd, device = vbd/51713
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:1561) Removing vbd/51714
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:590) XendDomainInfo.destroyDevice: deviceClass = vbd, device = vbd/51714
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:1561) Removing console/0
[2009-06-30 13:46:14 5499] DEBUG (XendDomainInfo:590) XendDomainInfo.destroyDevice: deviceClass = console, device = console/0
[2009-06-30 13:46:14 5499] ERROR (XendDomain:1136) Restore failed
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/xen/xend/XendDomain.py", line 1134, in domain_restore_fd
    return XendCheckpoint.restore(self, fd, paused=paused)
  File "/usr/lib/python2.5/site-packages/xen/xend/XendCheckpoint.py", line 231, in restore
    forkHelper(cmd, fd, handler.handler, True)
  File "/usr/lib/python2.5/site-packages/xen/xend/XendCheckpoint.py", line 353, in forkHelper
    raise XendError("%s failed" % string.join(cmd))
XendError: /usr/lib/xen/bin/xc_restore 4 7 1 2 0 0 0 failed

```

---

