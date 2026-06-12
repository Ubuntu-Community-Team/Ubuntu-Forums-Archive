---
title: "SSH / SFTP Restrict User access"
date: 2009-11-11
forum: Server Platforms
---

### Post by roundhay on 2009-11-11
I would like to share 2 folders on my server with friends / family. One folder contains files which I want them to be able to access and download but not delete, modify or create / add new files to. The second folder is there so that they can upload files but not delete or modify.

Can I create this type of set up using ssh / sftp?

I currently access the server myself using ssh and sftp but when I do this  can see all of the folders and have full access, this is fine for me but I don't want anyone else to have this type of access.

---

### Post by hictio on 2009-11-11
> 
One folder contains files which I want them to be able to access and download but not delete, modify or create / add new files to. 


You can use the sticky bit, for instance.

[Protecting Files with the Sticky Bitt](http://events.oreilly.com/pub/a/linux/lpt/22_06.html)
[Advanced File Permissions in Linux](http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php)

---

### Post by Lars Noodén on 2009-11-12
ssh / sftp only give access to the file system.  The filesystem and its mount options determine what you can do as far as permissions.  

For example, if you're using [AFS](http://www.engin.umich.edu/caen/faqs/Accounts/AFS/permissions/) you get seven.  If you use EXT, you get (AFAIK) three.

---

### Post by roundhay on 2009-11-12
Thanks for the input.

It doesn't look like SSH / SFTP are the right fit for what I'm trying at achieve.

I now plan to look into ftp, I've already done a bit of readind on ftp, would vsftpd be the best option for this? Can it be set up securely?

---

### Post by hictio on 2009-11-12
> **roundhay said:**
> Thanks for the input.

It doesn't look like SSH / SFTP are the right fit for what I'm trying at achieve.

I now plan to look into ftp, I've already done a bit of readind on ftp, would vsftpd be the best option for this? Can it be set up securely?

Actually, FTP will be less secure. Are you planning on having that FTP open to the Internet, or it'll be an internal server (only accessible within your house, for instance)?

---

### Post by roundhay on 2009-11-13
I plan on having the ftp server accessisble over the internet

---

