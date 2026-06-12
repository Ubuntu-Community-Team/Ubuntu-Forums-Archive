---
title: "mount.nfs4: access denied by server while mounting"
date: 2018-05-18
forum: Server Platforms
---

### Post by ucharlie on 2018-05-18
I didn't manage to mount a NFS4 share :

mount -t nfs4 -o rw,sec=krb5 charlie.dom.local:/data /mnt/
mount.nfs4: access denied by server while mounting charlie.dom.local:/data

Can you help me to debug ?

---

### Post by TheFu on 2018-05-18
What have you done?  Exactly.  Show all the work. All commands and important outputs.  Please use "code tags" so things line up.

First question, did you setup Kerberos?  Did you run the mount as root?

---

