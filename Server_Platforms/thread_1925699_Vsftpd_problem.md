---
title: "Vsftpd problem"
date: 2012-02-15
forum: Server Platforms
---

### Post by coolx on 2012-02-15
Hi,
I have just installed vsftpd(2.3.0~pre2-4ubuntu2.3). I am searching where is "default directory" but I couldnt able to find.

Firstly "etc/vsftpd.conf" file's content is below;
---------------
listen=YES
anonymous_enable=YES
write_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
dirmessage_enable=YES
dirlist_enable=YES
no_anon_password=YES
file_open_mode=777
guest_enable=YES
--------------

When I try connect to ftp server with Filezilla, I can able to connect  anonymously. But I cant create directory or create a file. Its getting  "550 Create directory operation failed." error. How can I create a file?

Secondly, I search everywhere but I cant find default ftp directory.   Some sites are talking about there should be a directory like  "/home/ftp". But its not. Where should I put my files for download?  There is nothing in "etc/vsftpd.conf" file about this.

Regards.

---

