---
title: "user accounts"
date: 2011-10-17
forum: Server Platforms
---

### Post by Mistertuxedopants on 2011-10-17
So i am setting up a home server. My bother lives in the house with me and wants to access the files via sftp which is fine, i have it working. What i don't want is when he using winscp is for him to be able to see all the root files. I just want him to only be able to specific folders, like music or movies. Is this possible?

thanks
MTP

---

### Post by HermanAB on 2011-10-18
Yes, you can chroot users with sshd.  Read the man page or the snailbook.  It is a good one.

---

### Post by Mistertuxedopants on 2011-10-18
so, i took your advice and looked for chroot and found some information

I added this
Match Group users     
ChrootDirectory /Music 
    AllowTCPForwarding no     
X11Forwarding no     
ForceCommand /usr/lib/openssh/sftp-server

to this /etc/ssh/sshd_config

But when i connect to my server with WinSCP using SFTP the user can still see everything and not just /Music

---

### Post by Mistertuxedopants on 2011-10-19
nobody can help me out with this.


thanks!

---

