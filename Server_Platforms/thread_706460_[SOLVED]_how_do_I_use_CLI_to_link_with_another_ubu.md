---
title: "[SOLVED] how do I use CLI to link with another ubuntu share"
date: 2008-02-24
forum: Server Platforms
---

### Post by ttallos on 2008-02-24
How do I link to the ubuntu share (already set up) from a freshly loaded server I have CLI. I want to pull some files on to the server to set up samba shares. Thanks for any help.

---

### Post by k_grdn on 2008-02-24
Hi,

If the share is NFS use:

mount -t nfs -o options remote_ip:/path/to/file mount_point

man mount.

Regards,

k_grdn

---

### Post by astrotech226 on 2008-02-24
If this is a one time copy and you are running ssh, scp is pretty easy.

```
scp -r username@the_other_host:/path/to/directory/to/be/copied /path/where/copy/should/go
```

---

