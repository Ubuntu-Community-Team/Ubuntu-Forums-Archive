---
title: "Power cut - lost files in NFS folder"
date: 2021-05-19
forum: Server Platforms
---

### Post by quizzicalpony on 2021-05-19
We had the technician round to fix the dishwasher. For some reason, he took it upon himself to cut the power to the entire house... (needless to say I will be investing in a UPS shortly!)

Upon rebooting all my computers, i realised the NFS server was down. It's hosted on a VM.

```
$ systemctl list-dependencies nfs-kernel-server
nfs-kernel-server.service
[COLOR=#26A269]**&#9679;**[/COLOR] &#9500;&#9472;-.mount
&#9679; &#9500;&#9472;auth-rpcgss-module.service
&#9679; &#9500;&#9472;nfs-config.service
&#9679; &#9500;&#9472;nfs-idmapd.service
&#9679; &#9500;&#9472;nfs-mountd.service
[COLOR=#26A269]**&#9679;**[/COLOR] &#9500;&#9472;proc-fs-nfsd.mount
&#9679; &#9500;&#9472;rpc-svcgssd.service
[COLOR=#26A269]**&#9679;**[/COLOR] &#9500;&#9472;rpcbind.socket
[COLOR=#C01C28]**&#9679;**[/COLOR] &#9500;&#9472;srv-nfs4-temp\x2dplots.mount
[COLOR=#26A269]**&#9679;**[/COLOR] &#9500;&#9472;system.slice
[COLOR=#26A269]**&#9679;**[/COLOR] &#9492;&#9472;network.target

```

```
$ systemctl status nfs-server.service 
&#9679; nfs-server.service - NFS server and services
     Loaded: loaded (/lib/systemd/system/nfs-server.service; enabled; vendor preset: enabled)
    Drop-In: /run/systemd/generator/nfs-server.service.d
             &#9492;&#9472;order-with-mounts.conf
     Active: inactive (dead)

May 19 17:38:58 docker systemd[1]: [COLOR=#D7D75F]**Dependency failed for NFS server and services.**[/COLOR]
May 19 17:38:58 docker systemd[1]: **nfs-server.service: Job nfs-server.service/start failed with result 'dependency'.**

```

These are the two relevant errors I've managed to identify. But most importanly, when I go to my NFS folder on the server /srv/nfs4/temp - it's now empty. There are zero files. Is there any way to (1) restart the NFS service and (2) recover the files?

---

### Post by slickymaster on 2021-05-19
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2021-05-19
Try:
```
sudo systemctl restart nfs-client.target
sudo mount -a
```

This assumes the NAS device is up, not corrupted, and the /etc/fstab was used to specify NFS mounts. If the NFS server hasn't mounted the storage, then you'll need to work on that system.

If you use autofs for all temporary mounts, which is what I do, just restart the autofs service, then try to access the storage location using any tool.

Oh ... and you'll need to shutdown any VMs the system is trying to run off the NFS storage.  Any local programs shouldn't be trying to access any files/directories on the NFS when the restart happens.

A reboot of the nfs client system would have done these things already, so if that didn't work, the problem is on the nfs-server side and will need to be addressed there.

---

