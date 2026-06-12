---
title: "Ubuntu 14.04 LTS server disable the use of the TLSv1.0 protocol"
date: 2015-07-27
forum: Server Platforms
---

### Post by paul212 on 2015-07-27
I am running a Unbuntu 14.04 LTS server. It is my SFTP server.  I cannot find where or how to disable the use of the TLSv1.0 protocol.  I have searched the net for days but nothing I read is helping to disable this protocol.  No Apache installed.  VSFTPD is installed.  OPENSSH installed. Latest version. I need to disable this protocol so that I can pass my PCI network scan. 
Any help would be great!   Thank you

---

### Post by PaulW2U on 2015-07-27
*Thread moved to **Server Platforms**.*

---

### Post by nerdtron on 2015-07-28
I think sftp uses the /etc/ssh/sshd_config file so you'll need to declare your supported ciphers on the file. Either declare all, then remove TLSv1 or just declare which ones you want to use.
Some info on this link: [URL="http://security.stackexchange.com/questions/39756/secure-configuration-of-ciphers-macs-kex-available-in-ssh"]http://security.stackexchange.com/questions/39756/secure-configuration-of-ciphers-macs-kex-available-in-ssh

[/URL][http://www.reddit.com/r/linuxadmin/comments/14bo0g/hardening_sshd_config/](http://www.reddit.com/r/linuxadmin/comments/14bo0g/hardening_sshd_config/)

---

