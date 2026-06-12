---
title: "Apache wont remove completely"
date: 2009-12-24
forum: Server Platforms
---

### Post by IZWicky on 2009-12-24
Hello all,


I did:
```
sudo apt-get remove --purge apache2
```but when I check /etc/apache2 the files are still there, so I tried again the command above and says nothing needs to be removed but I keep seeing Apache's files.

What can I do?

I'm using Ubuntu Server 9.10 via SSH, so I can do what say using shell.

Thanks in advance!

---

### Post by Vegan on 2009-12-24
```
sudo apt-get autoremove
```

will get ride of all excess packages

be aware that config files in the /etc are not all removed as modified files are better manually removed so an opportunity to save files is preserved.

---

### Post by IZWicky on 2009-12-28
Just did that and it showed no files needed to be deleted because they were deleted when I did "*sudo apt-get remove apache2*" command.

So I deleted files manually and tried to install apache2 again, I did:
```
sudo apt-get install apache2
```

but when I check for /var/www or /etc/apache2 directories, they don't exist!

What can I do here?

---

### Post by taliksik on 2009-12-29
Try
```
#sudo apt-get purge apache2
```This will completely remove the package

---

### Post by wojox on 2009-12-29
Try a reinstall:

```
sudo apt-get install --reinstall apache2
```

---

