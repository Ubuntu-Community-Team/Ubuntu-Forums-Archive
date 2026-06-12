---
title: "Struggling with FTP"
date: 2008-02-03
forum: Server Platforms
---

### Post by jonbey on 2008-02-03
I have Ubuntu Fiesty, and installed ProFTPd.

I can upload and download via FTP from my home directory, and also upload to the subdirectories in home, but I cannot download from the some subdirectories - well, I can download, but the file loses its content, and is always 0Kb.

e.g. using FTP on my other computer, I can upload to
/home/user/websites/domain1 but if I attempt to download a file, it is always 0KB

I can download anything from /home/user/ though.

Permissions for websites is drwxr-xr-x which is the same as Desktop, which I can download compelte files from.

So, what is the problem? The permissions and iownership all look OK, so what could be preventing downloads from working?

Cheers

Jon.

---

### Post by Dr Small on 2008-02-03
How are you attempting to download the files? via FTP?

---

### Post by jonbey on 2008-02-05
Yes, CoffeeCup. I have no problems with my professional hosting, so it somthing wrong with the configuration on my own server.

---

### Post by ellis rowell on 2008-02-05
I use Gftp and have no problems. If i occasionally upload a file with the permissions set wrong, my professional host allows me to do a "chmod" and change the permissions (not all do). My host is 1and1.co.uk (server based in Germany)

---

