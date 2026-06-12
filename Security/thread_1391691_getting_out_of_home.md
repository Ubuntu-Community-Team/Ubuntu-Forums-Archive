---
title: "getting out of /home?"
date: 2010-01-27
forum: Security
---

### Post by razzer on 2010-01-27
i se this as a security question. Currently on my server system users can back out of their home folder. for example for me /home/razzera i can back out into /home/ and then i can bacout once more into root /. my question is, how can i stop users so they cannot back out into /home/ or go to any folder that is not in their home folder trough SSH or FTP?

---

### Post by Lars Noodén on 2010-01-27
You can put something like this in your ssh server's configuration file to chroot sftp users to their own home directories.  

At the end of /etc/ssh/sshd_config :

```

Subsystem sftp **internal-sftp**

Match Group sftp-only
	ChrootDirectory **%h**
	AllowTCPForwarding no
	X11Forwarding 
	ForceCommand **internal-sftp**

```

The members of the group **sftp-only** can then only connect with sftp and even then only to their own home directory.  If you want to allow access to all of /home, then replace **%h** above with **/home** or whatever target you wish.

For sftp clients, there is the regular text client sftp, and GUI clients Filezilla, Konqueror, Dolphin, Nautilus, Fugu, and Cyberduck.  There are some others, too, that's just a sample.

---

