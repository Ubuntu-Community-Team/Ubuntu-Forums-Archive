---
title: "OpenSSH and SFTP"
date: 2010-02-05
forum: Server Platforms
---

### Post by lewisforlife on 2010-02-05
I currently have OpenSSH-Server installed on an Ubuntu 9.10 Server install.  I currently have PasswordAuthentication turned off and authenticate remote connections with RSA PublicKeyAuthentication.

I want to create a user that has access to /var/www and its contents, and is chrooted in that directory.  I would like this user to be able to authenticate with a password.  Every other user would have to use PublicKeyAuth.  Is this possible?  If so how can I accomplish this?

---

### Post by lykwydchykyn on 2010-02-05
Regarding authentication, I don't know exactly how to do this, but you want to look into using PAM with SSH.  It's set up by default on Ubuntu, you need to edit /etc/pam.d/sshd.

For chroot, I think this can be set in /etc/security/limits.conf.  You may have to enable that file in /etc/pam.d/sshd.

---

