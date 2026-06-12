---
title: "kernel 3.4 vs. NFS"
date: 2012-05-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by 3vi1 on 2012-05-04
Is anyone else using NFS?  I think I found the cause of my hanging when I boot with the 3.4.0-1 kernel.

I think it might have been trying to mount NFS volumes before networking had started.

```
May  4 11:45:14 saturn kernel: [    7.434856] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
May  4 11:45:14 saturn kernel: [    7.438160] BUG: unable to handle kernel NULL pointer dereference at           (null)
May  4 11:45:14 saturn kernel: [    7.438164] IP: [<ffffffffa10d01ae>] rpc_pipefs_event+0xae/0x220 [nfs]
May  4 11:45:14 saturn kernel: [    7.438175] PGD 31b704067 PUD 3101d7067 PMD 0 
May  4 11:45:14 saturn kernel: [    7.438177] Oops: 0000 [#1] SMP 
May  4 11:45:14 saturn kernel: [    7.438179] CPU 8 

...

May  4 11:45:14 saturn kernel: [    7.946858] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  4 11:45:14 saturn kernel: [    7.947030] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  4 11:45:16 saturn kernel: [    9.533966] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
May  4 11:45:16 saturn kernel: [    9.533970] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
May  4 11:45:16 saturn kernel: [    9.534964] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  4 11:45:26 saturn kernel: [   20.208857] eth0: no IPv6 routers present
May  4 11:46:41 saturn kernel: [   96.142650] BUG: soft lockup - CPU#0 stuck for 22s! [mount.nfs:1361]

```

I guess I'm off to see if anyone's reported this on launchpad.

---

### Post by 3vi1 on 2012-05-22
I've continued to see this problem with all three 3.4 kernels so far, but haven't had time to look into it further.

Just now, after 3.4.0-3 failed to boot (in the same manner), I commented my NFS mounts out of my fstab... and it booted fine.  I was even able to re-add them to the fstab and mount them after loging into the system.

So, the problem seems to be with NFS trying to mount them before the network is ready.

Has anyone else seen a problem recently where the system says "Waiting up to 60 more seconds for networking"?  I'm seeing it even with the 3.2 kernels now.  By the time the system boots, everything seems fine.  None of my other systems have a problem, nor do I see any issues when I boot cold to Windows - so I know it's not a network or hardware issue.

This makes me think there's been a change to Network Manager that's exacerbating things, and is the real catalyst for my problems (though the NFS thing really does need to get fixed).

I had a look around launchpad, but didn't see any similar issues reported.  I guess I really should put something there once I have time to ascertain exactly what info I should include.

---

### Post by effenberg0x0 on 2012-05-22
Hi, not sure if this is related, but I had a lot of problems with cifs/smbfs and nfs on 3.4.x. Back then, the modules I had, from repos, were built with a different version of the toolchain, so anything from simply not loading to crashing was expected. When trying to build them with gcc current, I had some missing headers (not too many errors, but annoying). I gave up for lack of time. 

I imagine one should be able to compile them by now, maybe play with apt-build or something. I'm stuck on 3.2.0-24 still, because of specific hardware.

At any rate, before jumping into /usr/src and worrying about headers, I'd advice you lsmod | grep -i nfs, modprobe -r <any-nfs-module-you-find> and check again. apt-get remove --purge nfs-common, nfs-kernel-server (and maybe portmap, idmapd, whatever you have that operates together with nfs). modinfo nfs, nfs_acl, nfsd  to get any remaining modules path and rename them to <previous-name>.backup just to be sure. Then apt-get install the packages (and manually update-grub, initramfs). It *might* solve your problem (happened to me before).

Also: I think I have seen some error like the one you posted here when we changed the /var/run to /run. Check that you have rpcbind/, rpcbind.lock, rpcbind.sock, rpc_pipefs/, rpc.statd.pid in /run (and ownership/modes).

Regards,
Effenberg

---

