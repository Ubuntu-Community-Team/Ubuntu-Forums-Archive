---
title: "SFTP file edit"
date: 2011-11-24
forum: Server Platforms
---

### Post by LordJebe on 2011-11-24
Hello!

I have installed LAMP and I am hosting a test web site. I uploaded the web page files to the server and everyting works fine, but when I try to edit a file in WinSCP, I get this error:
```
Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 3
```How can I give permissions to edit the files in WinSCP?
Note: I used FTP to upload the files to the server, uninstalled FTP and now I use SFTP. Could this have something to do with my problem?

---

### Post by volkswagner on 2011-11-24
Does the file have write permissions by the user you are logged in as?

```
ls -al /folder/withFile
```

Can you edit it using sudo?

```
sudo nano file.txt
```

---

### Post by LordJebe on 2011-11-24
Yes, the user I am logged in as is admin, and I can edit the files on the server with the text editor.

The files I want to edit on the server are in /var/www/. With WinSCP, I can't do anyting in that folder, I can't even copy a file from my computer into that folder. I need to add permissions to that folder so I can edit the files in WinSCP.

---

### Post by Doug S on 2011-11-24
There was a similar thread just the other day. [http://ubuntuforums.org/showthread.php?t=1882623](http://ubuntuforums.org/showthread.php?t=1882623)

---

### Post by LordJebe on 2011-11-26
> **Doug S said:**
> There was a similar thread just the other day. [http://ubuntuforums.org/showthread.php?t=1882623](http://ubuntuforums.org/showthread.php?t=1882623)
Thanks for the link. Marking thread as solved.

---

