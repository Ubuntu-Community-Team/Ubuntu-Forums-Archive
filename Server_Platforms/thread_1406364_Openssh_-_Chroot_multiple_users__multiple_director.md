---
title: "Openssh - Chroot: multiple users / multiple directories"
date: 2010-02-13
forum: Server Platforms
---

### Post by Zidaps on 2010-02-13
Hi,

I was successfully able to confine userS to A PARTICULAR directory withing my computer using "ChrootDirectory" Now, I am trying to fine tune access.

Apparently, my user name was also Chrooted into the same directory. This is because I belonged to the same group that was Chrooted (sambashare). Upon noticing that, I changed my group. Yet the problem persists and I am confined to the same folder everyone else is.

Here is the relevant bit of my sshd_config file.
> Subsystem sftp internal-sftp

Match group sambashare

    ChrootDirectory /media/Media/Public
    X11Forwarding no
    AllowTcpForwarding no
    ForceCommand internal-sftpI am interested in doing the following things:

1. Can anyone tell me how to regain full access. 
2. Can anyone tell me how to confine different users to different directories.

In regard to objective (2), Lets say there are 3 users, a, b, c. and I want to limit them to different directories: like this.

a = /media/Media/a
b = /media/Media/b
c = /media.Media/c

Limiting each user to their own root, and not a common shared root. Keeping in mind that neither a, b, nor c should be able to go back passed "/media/Media" so they are jailed but jailed to different directories within a common shared "prison"

Also, if someone can explain why I get locked into the Chroot jail when my user name is no longer in the group "sambashare" specified to be Chrooted above in the "sshd_config" file ?

Thanks.

---

