---
title: "LTSP fat-client/thin-client User Profile Editor"
date: 2010-08-07
forum: Server Platforms
---

### Post by jeight on 2010-08-07
[SIZE=2]I've installed Edubuntu 10.04 with LTSP running fat-clients and thin-clients. The problem is the fat-clients don't use the settings from the User Profile Editor but the thin-clients do. The Itsp is a fat-client server by default, but I put LTSP_FATCLIENT=false in the lts.conf file for specific mac addresses that I want to run as thin-clients. The only thing I can think of would be to install sabayon in the chroot directory.

My guess is that the thin-clients are running on the root directory and that the fat-clients are running on the chroot directory, but I want some input before I do. The other option would be to add additional information into the lts.conf file but I don't know what that would entail. [/SIZE]

---

### Post by jeight on 2010-08-07
**[https://help.ubuntu.com/community/UbuntuLTSP/FatClients](https://help.ubuntu.com/community/UbuntuLTSP/FatClients)** (under troubleshoot)

SSH_FOLLOW_SYMLINKS=False is required in lts.conf. 

 

[LIST]
[*]Install nfs-client in the chroot, 
[*]Install nfs-kernel-server on your server, 
[*]Add /home   *(rw,sync,no_subtree_check) to your /etc/exports on your server, 
[*]Run sudo exportfs -ra for the previous change to take effect, 
[*]And finally, add NFS_HOME=/home on your lts.conf. 
[/LIST]
That solved the problem.

---

