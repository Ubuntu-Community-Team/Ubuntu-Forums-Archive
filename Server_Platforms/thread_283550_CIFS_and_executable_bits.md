---
title: "CIFS and executable bits"
date: 2006-10-24
forum: Server Platforms
---

### Post by lutzky on 2006-10-24
I'm using winbind, pam_mount and cifs to get my Single Sign-On. Now, the server is Linux, and some of the clients are Linux, so I'd like permission bits to work correctly. They mostly do - however, some applications activate the executable bit by default. This includes svn and wget (for example, wgetting google.com creates an index.html chmodded 0744). It does not include touch and vim (for example, touching or vimming and saving a file called 'test' sets it at 0644). Now, the executable bit is REALLY annoying, especially with svn. Some files, however, do need to be executable...

I've tried getting pam_mount to work with sshfs, but no dice (which is a shame, I really like sshfs). So is there any way to get CIFS to work here?

(NFS is too insecure to be considered)

---

