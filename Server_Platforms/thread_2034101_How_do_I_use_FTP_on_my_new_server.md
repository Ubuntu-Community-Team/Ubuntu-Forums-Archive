---
title: "How do I use FTP on my new server?"
date: 2012-07-27
forum: Server Platforms
---

### Post by Maheriano on 2012-07-27
I just installed Ubuntu Server and I want to upload files to it through FTP. How can I do this? If I install a FTP program, how do I configure it as a client? Should I get something like XPanel? Thanks.

---

### Post by papibe on 2012-07-27
Hi Maheriano.

I would recommend taking a look at sftp. It is part of the openssh-server package and it needs no configuration. It just works.

If you are really committed to FTP, take a look at this [guide]("https://help.ubuntu.com/12.04/serverguide/ftp-server.html").

Hope that helps, and tell us how it goes.
Regards.

---

### Post by Maheriano on 2012-07-27
Can I connect to that with Filezilla?

---

### Post by papibe on 2012-07-27
> **Maheriano said:**
> Can I connect to that with Filezilla?
Indeed.

Use protocol sftp and port 22.

Regards.

---

### Post by LHammonds on 2012-07-28
From what I have read, vsftpd seems to be the most-recommended FTP server for Ubuntu and most other Linux systems.

I was able to follow the instructions in the [link above](https://help.ubuntu.com/12.04/serverguide/ftp-server.html) to get one setup and secured.

But for my purposes, I was setting up a WordPress site and created a wordpress FTP account rather than using the built-in ftp account.

I am able to use FileZilla ([portable edition for Windows]("http://portableapps.com/apps/internet/filezilla_portable/")) to connect to it via FTP or SFTP.

LHammonds

---

### Post by Maheriano on 2012-08-03
That worked but what about using NetBeans? It looks like it uses port 21 which I have forwarded but my only option for connection in the preferences is via FTP. How can I set up something on the server which would allow me to use NetBeans?

---

### Post by Maheriano on 2012-08-07
So what's the best way to set up an FTP client on Ubuntu Server via command line? I just want something simple that works, nothing too complicated.

---

### Post by papibe on 2012-08-07
I would use vsftpd. Here's a [guide]("https://help.ubuntu.com/12.04/serverguide/ftp-server.html").

Regards.

---

