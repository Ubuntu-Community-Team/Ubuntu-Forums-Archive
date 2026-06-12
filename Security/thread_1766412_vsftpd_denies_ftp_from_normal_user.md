---
title: "vsftpd denies ftp from normal user"
date: 2011-05-24
forum: Security
---

### Post by Lotarogg on 2011-05-24
Hi, Ive got an ftp server which allows me to connect as the root user but won't allow connections from any other users I create. I have placed the new users (shell disabled) in the vsftpd.chroot_list file. When I try to connect I get "the server actively refused the connection". I can connect with the root user I used to install the vsftpd app. 
 
Thanks
 
edit - basically I can't ftp to the server with any other account than the one that installed it. Have made a new admin user and that can't do it either. Feel I'm missing something obvious...

---

