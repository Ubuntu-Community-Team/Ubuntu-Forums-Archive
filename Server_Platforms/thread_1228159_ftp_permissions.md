---
title: "ftp permissions"
date: 2009-07-31
forum: Server Platforms
---

### Post by Delta62 on 2009-07-31
I've recently set up an FTP server onto my ubuntu 9.04 box.

I am able to use FTP normally, but I need some way to change the default permissions of uploaded files.

This is a LAMP testing server, so files are uploaded and need to be accessible immediately. However, when a file is uploaded, it has a permission value of 600, so uploaded webpages cannot be viewed by anyone.

I need to find some way to change the permissions of uploaded files to be 644 by default. Is there a way to do this?

---

### Post by ibutho on 2009-07-31
Which ftp server are you using?

---

### Post by Delta62 on 2009-07-31
I am using vsftpd.

---

### Post by ibutho on 2009-07-31
Is your umask for local users set to 022?

---

### Post by Delta62 on 2009-07-31
I haven't tried that. Let me take a look at that here...

---

### Post by Delta62 on 2009-07-31
That has done it. Thanks so much! :guitar:

---

### Post by ibutho on 2009-08-01
> **Delta62 said:**
> That has done it. Thanks so much! :guitar:

Ok. I'm glad that managed to resolve the problem. :)

---

