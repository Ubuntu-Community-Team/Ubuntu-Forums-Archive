---
title: "nfs-kernel-server dropping out..."
date: 2005-07-18
forum: Server Platforms
---

### Post by Caspa on 2005-07-18
Hi All,

I have a nfs-kernel-server running on 5.04, and it seems to work perfectly for uploading anything to the nfs share. However, when downloading from the nfs share (to the client computer) the server will stop responding after about 30 seconds and disconnect. The client is running Mac OS 10.4, but this client has never had any problems connecting to non-ubuntu nfs servers.

Any ideas?

Thanks!

---

### Post by LordHunter317 on 2005-07-18
Did you enable a firewall?

Is lockd running?  Is portmap running?  What NFS protocol level?  TCP or UDP?  Is it local LAN?  What speed?

Any messages in the system logs?

---

### Post by Caspa on 2005-07-18
My syslog has this in it

```

Jul 18 23:17:07 localhost kernel: nfsd: request from insecure port (192.168.0.5:54788)!
Jul 18 23:17:22 localhost kernel: nfsd: request from insecure port (192.168.0.5:54798)!
Jul 18 23:17:32 localhost kernel: nfsd: last server has exited
Jul 18 23:17:32 localhost kernel: nfsd: unexporting all filesystems
Jul 18 23:17:51 localhost kernel: nfsd: request from insecure port (192.168.0.5:54858)!
Jul 18 23:18:06 localhost rpc.statd[8719]: statd running as root. chown /var/lib/nfs/sm to choose different user


``` 

Very new to this, don't know much about it, but its just a generic kernel-nfs-server installation from apt, on a local lan... Getting bout 3MB/sec when uploading, cannot download without it hanging. The request from insecure port is because I'm connecting from mac os x (i have insecure option in /etc/exports so not a problem connecting).

---

