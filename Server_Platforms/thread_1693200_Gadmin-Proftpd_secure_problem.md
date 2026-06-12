---
title: "Gadmin-Proftpd secure problem"
date: 2011-02-22
forum: Server Platforms
---

### Post by heian on 2011-02-22
Hi,

I'm having problems to secure my FTP server.

Filezilla can login easy using FTP connection and everything works well.

But when trying to login using secure FTP  (SFTP or FTPS) with Filezilla, the message appears: can't connect to server.


I'm running Gadmin-Proftpd on Ubuntu 10.1 (clean install)
Samba is installed, no firewall, testing inside the LAN.
Played around with port 21 and 22, didn't help.

After installing openssh-server, gadmin-proftpd didn't activate at all. After removing openssh-server, it could activate as normal. 

It looks like there is something wrong with the server, but no idea yet what to do about it.

Thanks in advance,

heian

---

### Post by heian on 2011-02-24
Hi,

I just wonder, is it better to use an other server for my needs, as there is not much responce on gadmin-proftpd. I really gave up with Proftpd or Gadmin-Proftpd.

What i need is a secure ftp-server, for about three accounts.
Just for upload and download some personal stuff. Running on Ubuntu 10.04.

What would you guys recommend me to try? And from which server
is enough "up to date" information available on the internet and in forums? 


heian

---

