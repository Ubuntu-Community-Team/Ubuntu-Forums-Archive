---
title: "FTP to Apache?"
date: 2009-03-30
forum: Server Platforms
---

### Post by m3bik on 2009-03-30
I seem to be facing an issue that is annoying me... I've got VSFTPD and Apache2 installed in Ubuntu 8.10.

I've created a folder /home/sites/mysite/ for my website files. I set the apache config for my domain to point to this document root too...

I log in to ftp (with my personal account) and upload the files to this folder... Yet, when I try to access them in my browser, I get the error that I don't have permission to access the file. I've created basic HTML files through SSH (using sudo so the files are created as root user) in the same directory, and can view them with no problem through apache. I can't login as root into FTP... Is there anything I can do to allow me to mass upload files into this folder through FTP and actually have them accessable over apache (without chown'ing each file)?

---

### Post by doogy2004 on 2009-03-30
check for read permissions for Other:
```
ls -all /home/sites/mysite/
```

Add the read permission to other:
```
chmod o+r -R /home/sites/mysite
```

---

### Post by m3bik on 2009-03-30
Thanks, got it working.

---

