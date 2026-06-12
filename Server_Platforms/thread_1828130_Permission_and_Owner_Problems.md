---
title: "Permission and Owner Problems"
date: 2011-08-18
forum: Server Platforms
---

### Post by steelraptor on 2011-08-18
So I am running Apache on Ubuntu 10.04 64bit with virtual hosting.  Everything works swimmingly except for this one head scratching problem.

I have vsftpd enabled and configured for users to be able to log in and create folders quickly and easily in their public_html folders.  But when any user creates a folder with any FTP client it gives the folder 7 0 0 permissions.   But if I create a folder through a terminal sessions with the same user it gives the folder 7 5 5 permissions, which are the correct permissions for this setup.  I have the users in the www-data group and but none of the users that log in have sudo access.  I know you can quickly change the permissions of a created folder with Filezilla after upload but that is just a workaround.  Also the owner and group are reported as 1001 where as the files that were created with the terminal are 33.

So basically I need the users to create folders with 7 5 5 permissions and owner/group 33 through FTP.

I've been a full time linux user for a year now but still I haven't learned nearly enough as many others out there.  So hopefully someone out there can point me in the right direction.

Thanks for any help ^-^

---

### Post by dinu90 on 2011-08-18
This is done using the local_umask= setting in vsftpd.conf
You can set it to whatever you want

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

### Post by steelraptor on 2011-08-18
> **dinu90 said:**
> This is done using the local_umask= setting in vsftpd.conf
You can set it to whatever you want

Ahh!  So that's where I had to look!  I read about umask but didn't fully understand how it worked.

So I uncommented the ```
local_umask=022
``` and changed it too ```
local_umask=022 
```

Problem solved!

Thanks ^-^

---

