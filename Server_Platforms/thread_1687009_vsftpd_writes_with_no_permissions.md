---
title: "vsftpd writes with no permissions"
date: 2011-02-13
forum: Server Platforms
---

### Post by hirohitosan on 2011-02-13
Hi there. I have on my Ubuntu10.10 server vsftpd. I enabled in /etc/vsftpd.conf to upload files ```
write_enable=YES
```but the files are uploaded without any permissions for group or others. For example, if I create a file test.txt on my computer ```
ls -al test.txt 
-rw-r--r--  1 user  staff  5 Feb 13 14:46 test.txt
```and upload to my U10.10 server, I'll have```
ls -al test.txt
rw------- 1 horatiu horatiu       6 2011-02-13 14:48 test.txt
```
How can I told to vsftpd to keep the file permissions?

thanks!

---

