---
title: "NFS Client, not mounting server after failure at boot, with bg setting"
date: 2011-02-23
forum: Server Platforms
---

### Post by sibaz on 2011-02-23
I've got a few servers, and recently had cause to reboot all of them at once.  Unfortunately at that time, one of our NFS client machines failed to come up, because the NFS server hadn't booted yet.  

I've now changed the settings in fstab from default to rsize=8192,wsize=8192,timeo=14,intr,bg,retry=1,nobootwait

so now (with nobootwait) it doesn't halt the bootup waiting for me to continue.  

However, the bg setting, in the manual says it'll fork to the background and with retry=1, wait 1 minute then try to connect again.  

That doesn't seem to work.  I stop the NFS service, reboot the NFS client, it comes up, and df shows the NFS mount isn't mounted, I start the NFS service on the NFS server and the NFS client never picks up on it.  

How do I use the bg setting?

Also I saw a comment regarding another issue on hardy, where the commenter said they could see that mount had spawned a background process.  How can I see that this background process is running?  How can I see if it has attempted to connect to the server?

---

