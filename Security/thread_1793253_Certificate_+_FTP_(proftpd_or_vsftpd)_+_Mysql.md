---
title: "Certificate + FTP (proftpd or vsftpd) + Mysql"
date: 2011-06-29
forum: Security
---

### Post by danuel on 2011-06-29
Hi Linuxed People!

 I've walked around and around to give and could not find the information I want.
 As you know to be able to access with OpenVPN must be installed (to file) on the client machine to access the certificate server.

 Here comes my question ...

 It's possible configure an FTP server with MySQL authentication (this works 5stars) but with certificate?

 My goal is to have the ftp server with authentication by the database but can only access the FTP server, if I deliver (by hand / by mail...) the certificate file, well, I do not want the user to enter [ftp://server](ftp://server) and which appear to accept the certificate (because it does not interest me to accept any user get the certificate online).

 Thank you for your attention

 PS: Sorry for my English, I hope I have explained correctly

---

### Post by Lars Noodén on 2011-06-29
I would recommend looking into SFTP. FTP is insecure.  SFTP is very secure and you can use your regular login credentials and even lock it down usage to a single directory.  It is part of the package OpenSSH-server.

---

### Post by danuel on 2011-06-30
Lars Noodén Ji!

Thanks for the tip :)

But my question continue, it's possible install certificate in client machine and do not get via online with try access to sftp?

regards :)

---

### Post by Lars Noodén on 2011-06-30
Yes, it's possible to authenticate SFTP using certificates.  It is fairly new.

---

### Post by danuel on 2011-06-30
Thanks!

I will continue search and when I got this functionally I post a mini how to :)

see later :D

---

