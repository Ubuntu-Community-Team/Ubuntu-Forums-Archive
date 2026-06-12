---
title: "SFTP Chroot"
date: 2012-01-29
forum: Server Platforms
---

### Post by cowfish on 2012-01-29
I've been trying to set up a secure ftp server so I can transfer my files to /var/www without risk of anyone hacking in and seeing the rest of the server. Basically I have it set up so user x owns /var/www and in sshd_config he is chrooted to /var/www. In theory it would work but apparently the chroot directories have to be owned by root, however, that ruins the security element since I don't want to chroot my root user. Does anyone have any suggestions about setting this up?

---

### Post by shumifan50 on 2012-01-29
I would rather set ftp up for another directory and then use putty to copy the files to /var/www, so I can check them before I put them in place.

---

### Post by kevinthecomputerguy on 2012-01-29
Have a look at this, leave user root out of the match-group, and he can write anywhere.
[http://woodel.com/domore/sftp/woodel_sftp.pdf](http://woodel.com/domore/sftp/woodel_sftp.pdf)

And or make a "/var/www/uploads" folder

---

