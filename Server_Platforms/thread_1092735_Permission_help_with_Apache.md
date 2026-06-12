---
title: "Permission help with Apache"
date: 2009-03-10
forum: Server Platforms
---

### Post by MockY on 2009-03-10
Apache is currently driving me nuts.

This is what I want to accomplish:

1. Set up a webserver
2. Set up a FTP account

I have installed apache and vsftpd and they both work.
Here is my problem though:
I told Apache that the www directory is a directory in my home directory. Fair enough, it works - as long as I do a chmod 777 on the directory and everything inside it. As soon as I use FTP to upload to this directory, I don't have permissions to read the file. I assume this is because the files are now owned by the FTP user and can't be read by anyone else. But how on earth can you make that work so that webusers can read it without manually chmodding these files.
How do I properly set up a folder in my home directory to be my webdirectory, and so that all files uploaded via FTP remains readable for web users.

One odd thing I noticed, if I do a chmod 744 on the directory and its content, I get a forbidden error in Firefox when I try to browse to it. When I chmod 777 again, it is still forbidden which is just plain incorrect. However, if I point to the actual file, then I can read it. But after about 3 minutes, it works like it normally does again. What on earth is going on? I am going nuts here. This should really not be that hard at all, but it is.

Could someone please shed some light on this issue?

Thanks

---

### Post by bodhi.zazen on 2009-03-10
That is probably not the best method.

See this for how to configure a directory in you $HOME

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I suggest :

1. put your pages in /var/www

2. Use ssh (scp) rather then vsftp. If you stay with vsftp you will need to configure it to allow ftp access to the directory in question.

3. Make any files server by apache owned by the group www-data.

4. Make them read only, no need for them to be executable, especially if you are uploading files via ftp :)

---

### Post by MockY on 2009-03-11
If this was for just my purpose, I would not have any issues. I would just use ssh and be over with it. However, there are 5 users who needs access that are using Windows, and FTP would probably be the best way of doing this since I don't want them to go out and about in order to do a simple upload to the webserver.

I can't understand why setting up a FTP server should be so hard. I use ServU on my Windows servers, and all I have to do is create a user in ServU, add the folders I want that user to have access to, and then set the permissions I want that user to have on that folder. I wish this would be possible in Linux as well, but I simply have to accept that this is not the case.

So with that in mind, I don't know how to allow FTP users access to the /var/www/ directory so that they can add, alter, and remove files without having to set chmod 777 on the folder, and without the issue where the uploaded files gets separate permissions so that they will not work in a web browser.

---

### Post by MockY on 2009-03-11
I have looked around, tried different FTP servers, and I can't get the FTP user to upload to the /var/www/ directory. If it wasn't for the FTP server I would be fine with staying with Ubuntu, but it simply can't do what I want it to do, at least not somewhat easy. I have to unfortunately put my tail between my legs and resort to Windows 2003. Sad, but painfully true.

EDIT:

Before I completely gave up, I found this post [http://ubuntuforums.org/showthread.php?t=312583](http://ubuntuforums.org/showthread.php?t=312583)
When logging in with the new user, it appears to work. But as soon as I upload a file, the permissions are rw for only the user who uploaded it, hence it can't be viewed via a web browser. How on earth do I set it so that the files I upload are readable for www users?

Here are the permissions after uploading the file other.html
```

drwxrwxr-x 2 user1    www-data 4096 2009-03-10 21:26 css
drwxrwxr-x 2 user1    www-data 4096 2009-03-10 21:26 images
-rwxrwxr-x 1 user1    www-data 2594 2009-03-10 21:26 index.html
-rw------- 1 user2    www-data   38 2009-03-10 22:36 other.html
-rwxrwxr-x 1 user1    www-data   20 2009-03-10 21:26 test.php

```

---

### Post by hyper_ch on 2009-03-11
> **MockY said:**
> I can't understand why setting up a FTP server should be so hard [...]

Well, because thsi is linux and linux is strict on permissions.

Anyway, a simple solution would be

(1) install openssh-server so you get scp/sftp access

(2) install mysecureshell so that you can restrict those 5 users to /var/www only and have them not login with a shell

(3) create those 5 system users, set their shell to /bin/MySecureShell

(4) alter the UID and GID of 4 of those users to the same as the 5th one. Then they will all be able to create/edit/modify the files that others made.

(5) chown the /var/www folder to one of those users or make it so that they can write into.

There are better solutions but that's straight forward. As long as you default files are 0755 they don't need to be owned by www-data in the /var/www folder.

---

### Post by MockY on 2009-03-11
> **bodhi.zazen said:**
> 
I suggest :

1. put your pages in /var/www

2. Use ssh (scp) rather then vsftp. If you stay with vsftp you will need to configure it to allow ftp access to the directory in question.

3. Make any files server by apache owned by the group www-data.

4. Make them read only, no need for them to be executable, especially if you are uploading files via ftp :)

I have, as I mentioned in my other posts, done this. But any uploaded file or folder does not inherit the permissions, hence making it completely worthless since no one can use a browser to read these files.

---

### Post by wibbleypants on 2009-06-12
[QUOTE=MockY;6873557]Apache is currently driving me nuts.

This is what I want to accomplish:

1. Set up a webserver
2. Set up a FTP account

How do I properly set up a folder in my home directory to be my webdirectory, and so that all files uploaded via FTP remains readable for web users.

> I had the same problem. Just changed Filezilla to use sftp instead of ftp and it just worked.

---

