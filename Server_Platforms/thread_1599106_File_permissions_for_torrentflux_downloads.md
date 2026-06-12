---
title: "File permissions for torrentflux downloads"
date: 2010-10-17
forum: Server Platforms
---

### Post by oshunluvr on 2010-10-17
I have a new home media server install, 10.04.1 - 64 bit, up and running fine. Apache2, ssl, openssh, samba, cups, sane, nfs, and last but not least torrentflux.

My question is regarding files I receive using torrentflux. They are downloaded to a directory that has to be world "rw" but then it put the d/l's files into a subdirectory that is my torrentflux username. 

This would be fine except I want to be able to move the files from that directory to another from any user account and the target directory is group "r" but not "w". This is a family server so there's no need for that much security.

Basically - is there a setting to change the default create permissions for downloaded files? I just need to add "w" to the group permissions.

---

