---
title: "proftpd and gadmin-proftpd two different configs"
date: 2009-08-12
forum: Server Platforms
---

### Post by Foeburner on 2009-08-12
Hello, 



I have Jaunty and have proftpd and gadmin-proftpd installed thinking that they were linked but when I look at the config file /etc/proftpd.conf, its different from the config tab in gadmin. I have installed gadmin and proftpd before and it worked great on hardy. 

I dont know which is controlling the actual ftp server as I make the changes to both but its almost as if they cancel each other out. I have users log in and everytime they click on a folder it asks them to log back in. 

Which one is the actual config file and how can i get gadmin to control the ftp server? I prefer to have the gui since it makes it faster for me to add users and their permissions for each folder. 

Thank you!

---

### Post by cariboo on 2009-08-12
gadmin-proftpd is you gui frontend to configure proftpd.conf, I've never used it, I took one look at it and ran away screaming :), but check to see if the second config file is a backup. Open a terminal and type:

```
ls -l
```

If one file has a "~' at the end, it is a backup.

---

### Post by Foeburner on 2009-08-12
I dont see a ~ on the folder /etc/proftpd and i've checked the location where gadmin backs up to and the ~ file is there. That location is /etc/gadmin-proftpd/proftpd.conf.old.gadmin-proftpd-0.3.5-admin-backup

---

