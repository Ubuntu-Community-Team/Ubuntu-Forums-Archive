---
title: "NFS problem mount.nfs: Connection timed out  on 14.04.2 (via VM Machine)"
date: 2015-04-19
forum: Server Platforms
---

### Post by Bundit on 2015-04-19
I use the NFS configuration from this website :: [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-12-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-12-04)

Once I reach the step two mount the directories (of client) i got the message "mount.nfs: Connection timed out"

what should I do? I use 2 VM player (runs Ubuntu 14.04.2) for both of client and server on single machine and use NAT connection (I try to use Bridge connection but still not work)

Thanks everyone

---

### Post by nerdtron on 2015-04-20
Is your nfs-server service running? is the firewall up on each server?

Post your /etc/exports file here and the IP address of each of the VM. Also it's better to use bridge mode on both VMs.

---

