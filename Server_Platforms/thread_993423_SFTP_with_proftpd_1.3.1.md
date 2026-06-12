---
title: "SFTP with proftpd 1.3.1"
date: 2008-11-25
forum: Server Platforms
---

### Post by the-bna on 2008-11-25
Hello, I decided to make a new thread, since the old one contains information that is no longer relavant, and it would be misleading if the old thread contained the info that this thread will contain.

The story is I'm setting up proftpd with SFTP on ubuntu, and I'm not very familiar with linux.

So I need to **(1)**: disable SFTP access for the ssh user.

Then I need to **(2)**: enable SFTP access for a number of ftp users, who must _not_ have shell access via ssh.

So how do I go about that? Also, could I have SSH on one port and SFTP on another port?

---

### Post by Philio on 2008-11-25
To change the SSH port edit:

/etc/ssh/sshd_config

And change the line near the top Port to the new port of your choice. Restart ssh to apply the change.

No experience with proftp so afraid I can't help you further with that one!

---

### Post by the-bna on 2008-11-25
> **Philio said:**
> To change the SSH port edit:

/etc/ssh/sshd_config

And change the line near the top Port to the new port of your choice. Restart ssh to apply the change.

No experience with proftp so afraid I can't help you further with that one!

I've already got the SSH port changed, but that's all I've done so far. It doesn't have to be proftpd, it could be anything. I just want solid security.

---

### Post by Philio on 2008-11-25
Probably the quickest way to setup the users would be to use standard accounts but set them up as follows:

useradd -ms /bin/false username

(Setting their shell to /bin/false disables shell logins)

You could setup vsftpd as the ftp server with a couple of config changes:

local_enable=YES
write_enable=YES
chroot_local_user=YES

---

### Post by the-bna on 2008-11-25
I found this:

[http://ubuntuforums.org/showthread.php?t=451510](http://ubuntuforums.org/showthread.php?t=451510), that's probably as easy as it gets :)

---

