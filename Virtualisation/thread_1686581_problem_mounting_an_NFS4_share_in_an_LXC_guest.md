---
title: "problem mounting an NFS4 share in an LXC guest"
date: 2011-02-12
forum: Virtualisation
---

### Post by Nighthog on 2011-02-12
Hi folks,

I am trying to share a directory from my 10.04.1 (desktop) host with a Centos guest in an LXC container.  I understand that I mount it using the fstab file pointed to from the container's config file, but I can't get syntax right.  Getting it wrong prevents the container starting and I can't find any log output to help me correct it.

The host and guest talk via a bridge.  Here's the defs on the host's /etc/exports:

/export            192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/library    192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)

On the host I have installed nfs-common, nfs-kernel-server & portmap, and I mount via the host's fstab:

  	 	 	 	p { margin-bottom: 0.21cm; }/library	/export/library	none	bind		0	0 

On the container's fstab file I have tried every combination of localhost, 192.168.1.6 (the host's address), 192.168.1.10 (the bridge's address), /export/library and /library all with no luck.  Here's the fstab file:

none /var/lxc/rootfs/ve101/dev/pts devpts defaults 0 0
none /var/lxc/rootfs/ve101/proc proc defaults 0 0
none /var/lxc/rootfs/ve101/sys sysfs defaults 0 0
localhost:/library /var/lxc/rootfs/ve101/library nfs4 soft,intr,noacl,nosuid 0 0

The container only starts if I comment out the bottom line.  I'm at a loss - can anybody please help?

TIA

---

### Post by Nighthog on 2011-02-13
Well I've now spent numerous hours trying everything I can find from Mr Google and still no luck.  I can't believe I'm alone in trying this - surely someone out there can give me a lead?  Pretty please?

I'll buy a large ice cream for anyone who can help me fix this.  Just meet me in Corsham town centre at a mutually convenient time and we'll take it from there ....

---

### Post by MajorNelson on 2011-04-14
Not sure if you are still having issues since this was posted back in February, but I recently started learning lxc and stumbled across this thread.

In my environment the NFS server is not running on the lxc host. So I mount NFS shares from inside the container normally.  Install nfs-common and add the appropriate fstab entry. 

But from your post it seems that your NFS server and container are the same physical machine so I'm wondering if this would be a better approach and just bind the host directory to the guest. 
In the config file for the guest add:
lxc.mount.entry=/export/library /var/lxc/rootfs/ve101/library none bind 0 0

Hope this helps.
I found this entry helpful:
[http://ubuntuforums.org/showthread.php?t=1476832](http://ubuntuforums.org/showthread.php?t=1476832)

---

### Post by zefram12 on 2012-08-08
I also experience this "problem" of mounting nfs exports that was exported from the host running the lxc containers.

I haven't figured out exactly what is going on, but I have a clue: Exporting the nfs share with * wildcard, works, e.g:

/mnt/myexport *(rw,sync,no_subtree_check,no_root_squash)

My nfs server isn't showing anything useful in the logs. I would think that the nfs server could log the access denied reason, but I cannot find it.

I was thinking somewhere in the lxc backend some form of mangle is going on with the packets, causing the address to be changed. I tried to confirm this by seeing what ip address is requesting a website from my host, but unfortunately received the expected lxc ip address.

My reason for wanting nfs instead of lxc bind: I have found that the lxc bind method do not always work for me. For my purposes nfs will be fine.

---

