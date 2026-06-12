---
title: "unable to mount nfs directories on client"
date: 2011-12-27
forum: Server Platforms
---

### Post by bryan.sailer on 2011-12-27
I have resently upgraded my server to ubuntu 11.10. I have setup NFS on the server and I have followed this walkthrough: [https://help.ubuntu.com/community/SettingUpNFSHowTo#NFSv4_server](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFSv4_server) 

When I go to mount the directories on the client I keep get mount.nfs4: Connection timed out

I have Webmin setup to configure the server and when I apply the changes to the NFS exports I get the following:

rpc.nfsd: no process found
 * Stopping NFS kernel daemon
   ...done.
 * Unexporting directories for NFS kernel daemon...
   ...done.
 * Exporting directories for NFS kernel daemon...
exportfs: No options for o NFS: suggest NFS(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "NFS:o".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Failed to resolve NFS
exportfs: Failed to resolve NFS
exportfs: No options for o clients.: suggest clients.(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "clients.:o".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Failed to resolve clients.
exportfs: Failed to resolve clients.
exportfs: No options for o See: suggest See(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "See:o".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Failed to resolve See
exportfs: Failed to resolve See
exportfs: /etc/exports:1: syntax error: bad option list
exportfs: scandir /etc/exports.d: No such file or directory

I have had NFS running before but the only change is the upgrade to Ubuntu 11.10. My client is still running Ubuntu 10.10.

Any suggestions would be helpful.

---

### Post by bryan.sailer on 2011-12-29
After troubleshooting more into this problem. I am unable to get NFS to start on my server. I have gone over and over the walkthrough listed above and the service does not start. What could I be missing? How do I find it?


Ubuntu 11.10 Server
Ubuntu 10.10 client

---

### Post by 2F4U on 2011-12-30
Do you get errors on starting the NFS service? They would usually show up in the system log file on the server.

---

### Post by bryan.sailer on 2011-12-31
syntax,syntax,syantax. The whole problem was staring mr in the face th whole time. In my /etc/exports file I had removed a couple of examples and I deleted a # and there was a o in its place. This was causing nfs to think that o was a client and not continue down to the actual directories to be exported. Pay attention to every line of code. Lesson learned for me.

Ubuntu 10.10 and 11.10

---

