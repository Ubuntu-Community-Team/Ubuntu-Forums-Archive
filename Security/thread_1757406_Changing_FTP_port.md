---
title: "Changing FTP port?"
date: 2011-05-13
forum: Security
---

### Post by nbrochu on 2011-05-13
Hello, i am currently using vsftpd for FTP. I know that you can change the port number to connect to something like SSH, but can you change the port number for vsftpd to use?

---

### Post by chippy99 on 2011-05-13
The answer is here [http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

I think ftp_data_port is what you are looking for

---

### Post by Lars Noodén on 2011-05-14
> **nbrochu said:**
> Hello, i am currently using vsftpd for FTP. I know that you can change the port number to connect to something like SSH, but can you change the port number for vsftpd to use?

If you have SSH then you already have SFTP installed, configured and running. So you can use [SFTP](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP) instead and can retire FTP.  FTP just turned 40 years old last month...

---

