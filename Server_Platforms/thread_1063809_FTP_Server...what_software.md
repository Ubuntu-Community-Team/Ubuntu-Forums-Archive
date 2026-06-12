---
title: "FTP Server...what software?"
date: 2009-02-08
forum: Server Platforms
---

### Post by Lion06 on 2009-02-08
Hi to all!

I'm going to install a new Server FTP in my office; i would use only opensource software, but i don't find what i need :(

Primary FTP Server Feature:
- FTPS
- Event Handling (example: If USER-A upload file --> send mail to [email]test@test.it[/email])
- Write log to file

Secondary Feature:
- Read FTPS file through WebSite HTTP/S

	
I found only one program with this feature but it's for Windows and too expensive :(
[http://www.southrivertech.com/products/titanftp/index.html](http://www.southrivertech.com/products/titanftp/index.html)

Any ideas?

---

### Post by inphektion on 2009-02-08
you can setup vsftpd to do all this.  the event handling isn't built into it but i did it with incron

---

### Post by linux_tech on 2009-02-08
vsftpd works very good
```

aptitude install vsftpd

```


[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

---

