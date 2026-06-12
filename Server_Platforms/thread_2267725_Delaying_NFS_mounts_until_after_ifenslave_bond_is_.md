---
title: "Delaying NFS mounts until after ifenslave bond is operational?"
date: 2015-03-03
forum: Server Platforms
---

### Post by spyd4r on 2015-03-03
Ubuntu Server
Precise 12.04.5

Our NFS server mounts appear to get mounted too early and as a result system hangs indefinitely during boot as the NFS server name does not resolve. A half-baked workaround is to list the nfs server in /etc/hosts and enable statd in /etc/default/nfs-common. This results in the system no longer hanging during boot, but results in no route to host during the attempted NFS mount during boot. So you still need to manually mount the NFS server once you can log into the server.

I assume this is all due to NFS being mounted before the bond is fully operational. I have tried numerous things to try and delay the nfs mount, but alas I am out of ideas.

Any help appreciated, I've spent far too much time on this issue as it is.

---

### Post by MAFoElffen on 2015-03-03
I had this problem with a few Snap Servers if configured as NFS shares. If they were SMB, no issues. But NFS and it would hang while trying to make the connect. But after the boot, then would connect no problem.

On those, I took out of the fstab and ran from a script, kicked off as a startup script in /etc/init.d/... Which reminds me that I should probably take another look at those to update them to systemd spec's.

---

### Post by darkod on 2015-03-04
How about adding the noauto option for the nfs entries in fstab and then mounting them by simple bash script in rc.local?

That should do the trick since the script will be run at the very end of the boot process.

---

### Post by nerdtron on 2015-03-04
rc.local is an option.

If the auto-mounting is on fstab, you need to wait for the network. just add the _netdev on the mount options column to wait for network before mounting the nfs.

sample:
```
192.168.10.15:/mnt/share    /mnt/share1     nfs    _netdev,rw,sync    0     0  
```

---

