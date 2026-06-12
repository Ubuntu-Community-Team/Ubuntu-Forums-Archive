---
title: "Anyone can recommend the easy way to configure web and ftp server?"
date: 2010-07-12
forum: Server Platforms
---

### Post by plusnplus on 2010-07-12
Hi..,

What is the easy way to make ubuntu as a web and ftp server?
So far i only use ubuntu as development server(LAMP in ubuntu 10.04)

Now, i want try to host the server in my office rather then at service provider company.



thanks for any guide/ reply.

---

### Post by YorYor on 2010-07-12
```
sudo apt-get install apache2 pure-ftpd
``` (or vsftpd depending on which architecture you prefer)

---

### Post by plusnplus on 2010-07-12
after i googling around. maybe what i need is a dns server.
as i mention before. my pc already running ubuntu 10.01 + LAMP.

Now i have a static IP (only IP no domain name) from my internet service provider.
how i configure my ubuntu to use that static IP.
so my server can become live and accessable from internet.

---

### Post by doogy2004 on 2010-07-12
> **plusnplus said:**
> Hi..,

What is the easy way to make ubuntu as a web and ftp server?
So far i only use ubuntu as development server(LAMP in ubuntu 10.04)

Now, i want try to host the server in my office rather then at service provider company.



thanks for any guide/ reply.

```
sudo tasksel
```
select LAMP and OpenSSH, OpenSSH has a built in SFTP (Secure FTP) server.

---

### Post by bigfatgooglefat on 2010-07-13
If you're looking for a great way to configure and monitor your server remotely, I strongly recommend using webmin. You can find it here: [http://www.webmin.com/download.html]("http://www.webmin.com/download.html").
Just FYI, there's a missing dependency in 10.04, so you'll need to find the .deb manually. It only takes a minute and one google search, and it's worth it.

Anyways, hope this helps!

---

