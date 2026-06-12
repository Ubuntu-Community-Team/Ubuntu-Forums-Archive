---
title: "TFTPD help ???"
date: 2011-09-25
forum: Security
---

### Post by vikkyhacks on 2011-09-25
Hello guys i am actually new to the networking side ....

Last week i able to configure my apache2 server and it worked fine,,,,I also need to configure my FTP server and i was told that TFTPD is a very nice FTP server management tool ... I installed it and i am completely at sea on using it ... Please give me some good tutorials and guides on configuring TFTPD server .... 



...................THANKS IN ADVANCE :-)

---

### Post by Ryan Dwyer on 2011-09-25
According to Wikipedia, TFTP is like limited FTP. It doesn't have authentication. I recommend you don't use it.

Install something like pure-ftpd or vsftpd. They shouldn't need any manual configuration.

---

### Post by Lars Noodén on 2011-09-25
Use SFTP instead of FTP because FTP is insecure. 

SFTP is part of the package OpenSSH-server.  By installing that package will set you up with a working, secure, configured SFTP with no extra packages or configuration needed.

 ([http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP)).

---

### Post by Dangertux on 2011-09-25
Mirroring what someone else said, use SFTP via SSH. It's much more secure. 

TFTP, is something different from regular FTP, it's generally used for installing over a network and other pxe related tasks. It stands for Trivial File Transfer Protocol.

FTP is likely what you were actually recommended and there are some decent FTP servers, however I would still go with SSH it's much more secure.

---

### Post by vikkyhacks on 2011-09-26
K guys I understand about choosing the right software but i need to get a clean tutorial on how it is done from top to bottom ... how to add user, remove them , configure users with write privileges , user with read-only privileges and so on ....

---

### Post by Lars Noodén on 2011-09-26
Here's a good one:  [Stop Using FTP! How to Transfer Files Securely](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)

---

