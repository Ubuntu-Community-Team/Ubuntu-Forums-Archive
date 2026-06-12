---
title: "&quot;Upload as binary&quot;?"
date: 2010-08-04
forum: Server Platforms
---

### Post by fred2028 on 2010-08-04
I am trying to install PHPMotion and it says that some files need to be uploaded as BINARY and not ASCII. The thing is, I don't use FTP to upload files, I have physical access to the servers and I use a USB stick to transfer files over. I download them as .zip or .tar.gz on Windows and then move them to the Ubuntu 10.04 LTS x64 server and put them directly into my /var/www/ folder. How do I make them binary?

---

### Post by Nextraztus on 2010-08-04
When you copy directly from a device like a thumbdrive you don't have to worry about it.

The "upload as binary" thing is specific to FTP only. If you did use FTP, you have to setup your ftp client to binary mode otherwise it will corrupt the files. Most web software install guides are written assuming you don't have physical access to the server.

---

