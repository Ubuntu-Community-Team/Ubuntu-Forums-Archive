---
title: "FTP &amp; mounted samba share - read only"
date: 2016-06-08
forum: Ubuntu/Debian BASED
---

### Post by alex548 on 2016-06-08
[COLOR=#000000]Hello guys,[/COLOR]

[COLOR=#000000]I have vsftpd installed which works ok. However, the space is very limited therefore in order to extend size I decided to mount a samba share which is located on another server. It is mounted using cifs to a folder within the ftp tree. From server which hosts samba I provided full read/write permission (777). Ftp user on vsftpd setup also has full read/write permission on ftp. But, this user has read/write permission only to a directories which resides on vsftpd host, write is not permited on mounted share - only read and directory creation allowed, can't write files into it.[/COLOR]
[COLOR=#000000]When doing ls -la on vsftpd host to check mounted share permission it has 777 permission, but when writing file through ftp - permission denied... Can you advise, please?
Thanks.[/COLOR]

---

### Post by stevolus on 2016-07-28
Please, if you managed to sort this out let me know what you did. I have the exact same issue and I have a user that I constantly have to upload data for via ftp into a mounted samba share. I can do it just fine with the root account and I have even tried adding her to the root group which didnt work, which is weird. Havnt found any help on google.

Any feedback, or push in the right direction at least would be immensely appreciated. Thanks

---

### Post by stevolus on 2016-07-28
Basically got 2 ubuntu 14 VMs, one with samba one with proFTPD. The proFTPD has a mounted share from the ubuntu VM with samba on. Ive made the share recursively 777. Cant right to the sahre with standard user on the proFTPD server via ftp. Thats my situation

---

### Post by stevolus on 2016-07-29
Anyone?

---

