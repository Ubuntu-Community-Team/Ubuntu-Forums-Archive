---
title: "sftp users, setting umask"
date: 2009-03-19
forum: Server Platforms
---

### Post by nerrud on 2009-03-19
Hi,

I have a "dropbox" for some users on my ssh/sftp server, but I'd like to force all uploaded files to have certain permissions.

Does anyone have experience using the patch for sftpfilecontrol on hardy? I noticed that a .deb is available at tienhuis.nl as well.

What I'd like to do is simply to have a Match <user> section in my sshd_config, and add the apporpriate SftpUmask, but I do not know if this will work with OpenSSH_4.7p1

thanks for your help! :)

---

