---
title: "FTP Server?"
date: 2010-07-10
forum: Server Platforms
---

### Post by wh33t on 2010-07-10
Hello Community, I install the LAMP option of the Ubuntu Server, I can't remember the version at the moment, but I know it's currently the latest LTS version.

I want to be able to FTP into my Apache's webroot directory with full write privledges. How can I see this up? I am certainly struggling to make this happen. 

I would like to create an FTP user for this purpose.
Any tips in the right direction would be great.

---

### Post by jbrown96 on 2010-07-10
[https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)

---

### Post by wh33t on 2010-08-12
Thanks for replying.

Unfortunately for me that webpage you suggested doesn't give me enough information. 

Unfortunately it doesn't give me enough information to set a password for the user I have created. I'm not even aware which FTP server software that guide is written for.

---

### Post by CharlesA on 2010-08-12
You'd be better off to use sftp, as it is more secure.

As long as you secure ssh properly, you won't have any problems with unauthorized access.

You can use something like filezilla if you want to connect.

---

### Post by wh33t on 2010-08-12
> **CharlesA said:**
> You'd be better off use sftp, as it is more secure.

The FTP server isn't accessible outside of my router. The machine literally sits next to my computer and it's just a way for me to write Php/mysql applications with out relying on a webhost.

Also, the program I am using does not support Sftp, otherwise I'd just be using ssh/scp to do this.

---

### Post by CharlesA on 2010-08-12
What program are you using?

---

### Post by wh33t on 2010-08-12
> **CharlesA said:**
> What program are you using?

This old version of the Zend PHP Editor, but I was just reading up and it says the updated version will do SFTP, I am downloading it now, so I guess that solves my problem for now.

I appreciate everyone taking the time to reply.

---

### Post by aeiah on 2010-08-13
incase you still do want FTP (and the only reason for it really is to transfer large files on a LAN, since its insecure but has less overhead than ssh), i use vsftpd

on my lan i get about twice the transfer rate of sftp, but this is only useful if you're transferring lots of stuff. id never open it to the outside world, although the vs in vsftpd does stand for 'very secure'

---

