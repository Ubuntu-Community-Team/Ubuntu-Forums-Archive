---
title: "Set up SFTP server"
date: 2009-09-28
forum: Server Platforms
---

### Post by mocka on 2009-09-28
After spending some time trying to google my way for an answer to set up a SFTP server, I'm finally asking here in the forums.

My goal is to be able to mount a folder on a client-computer, which is connected to a server through the internet. This requires that the server is hosting a SFTP server. How do I set up this server?

I have tried to install vsftp according to the following tutorial with no success:
[http://wiki.vpslink.com/Configuring_vsftpd_for_secure_connections_%28TLS/SSL/SFTP%29](http://wiki.vpslink.com/Configuring_vsftpd_for_secure_connections_%28TLS/SSL/SFTP%29)

---

### Post by falconindy on 2009-09-28
Install openssh-server. Done. You don't need vsftpd.

---

### Post by Lars Noodén on 2009-09-29
Are you talking about SSHFS?

[http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)

If so, then install the package [openssh-server](http://packages.ubuntu.com/jaunty/openssh-server) SFTP is part of the service.  Also look around a little at some of the options in [/etc/sshd_config](http://linux.die.net/man/5/sshd_config)

Ooops.  After writing that, I read your link and that is talking about FTPS, which is not the same as SFTP.  Given a choice, I'd look at SFTP, which is it's own secure protocol  FTPS is FTP tunnelled over SSL.

---

### Post by mocka on 2009-10-11
Thank you that was very helpful. My sftp-server is now up and running.

---

