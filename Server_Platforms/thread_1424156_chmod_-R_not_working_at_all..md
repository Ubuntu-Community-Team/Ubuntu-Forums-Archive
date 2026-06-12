---
title: "chmod -R not working at all."
date: 2010-03-07
forum: Server Platforms
---

### Post by Juliano Dasilva on 2010-03-07
Geeks,

I just finished setting up my home ubuntu home server. Installed LAMP and it works beautifully. The problem is everytime I upload a file through FTP into the server, the file changes permission even though I did chmod -R 755 www. Si everytime I upload a file to my server i need to run the command chmod -R 755 /var/www Any ideas? 

Thank you!

---

### Post by km0r3 on 2010-03-08
Show us your **FTP Server Software **and **your permissions set on folder /var/www.** 
```
stat /var/www
```If set to 777, try setting to 755 without the -R argument. *Then* try uploading some files and check permissions.

---

