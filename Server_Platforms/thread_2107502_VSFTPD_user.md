---
title: "VSFTPD user"
date: 2013-01-22
forum: Server Platforms
---

### Post by Basurci on 2013-01-22
Hello new small explanation how to add new user to vsftpd and set that he would be able to open folder that is in ./ folder.
Tried online guides but they didn't help me much , I was getting 500 OPS error or 530 permission denied.
Is it possible to use root user that I use to login through putty to vps?

---

### Post by ragtag on 2013-01-22
You can set up normal users that are in the ftp group using "adduser", and then make sure they are not listed in /etc/ftpusers. If you don't want those users available over ssh, make sure they are not members of the sshers group.

You should not use 'root' to login over ftp (don't know if this is even possible). Ftp traffic is not encrypted, and not very secure, and the root user has full access to mess up your server.

---

### Post by Basurci on 2013-01-24
Could you write me what i need to enter to terminal? Because i tried and it didn't work maybe i did something wrong?

---

