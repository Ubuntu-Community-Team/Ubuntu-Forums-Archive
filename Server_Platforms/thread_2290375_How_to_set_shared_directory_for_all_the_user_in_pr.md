---
title: "How to set shared directory for all the user in proftpd?"
date: 2015-08-11
forum: Server Platforms
---

### Post by luofeiyu2011 on 2015-08-11
I have created two users in proftpd  this way:
adduser  user1
passwd user1
mkdir /home/ftp/user1
usermod -d /home/ftp/user1  user1

The same way for user2.

Now all the users can login into their accounts with ftp,they can  download and upload the their own files  into their own direcotories.
Now i want to create a shared directory  /home/ftp/share ,how to make  all the users can just download the files in the /home/ftp/share?z
How to write the configuration file?

---

### Post by nerdtron on 2015-08-12
You can make it like the /tmp folder, writable to all users, but only the owner of the files inside can delete/modify their own files.
```

$ ll -d /tmp
drwxrwxrwt. 8 root root 4096 Aug 12 06:39 /tmp
```

to make other folders like this:
```
 chmod 777 /shared/folder
chmod +t /shared/folder

```

more info here: [http://computernetworkingnotes.com/managing-file-system-security/sticky-bit.html](http://computernetworkingnotes.com/managing-file-system-security/sticky-bit.html)

---

### Post by TheFu on 2015-08-12
Plain ftp is a security risk.  Please strongly consider using sftp which doesn't have the same issues as plain FTP or FTPS.  Then normal Unix security permissions will be used. Nothing special here.

---

### Post by bab1 on 2015-08-12
> **luofeiyu2011 said:**
> I have created two users in proftpd  this way:
adduser  user1
passwd user1
mkdir /home/ftp/user1
usermod -d /home/ftp/user1  user1

The same way for user2.

Now all the users can login into their accounts with ftp,they can  download and upload the their own files  into their own direcotories.
Now i want to create a shared directory  /home/ftp/share ,how to make  all the users can just download the files in the /home/ftp/share?z
How to write the configuration file?
Regardless of others concerns about whether to use FTP, FTPS or SFTP, this is a directory/file permissions issue.  The sticky bit example (/tmp) that @nerdtron mentions is typically used to store data in a single place by multiple users, but not for collaboration such as editing or updating by multiple users.  If you want to have a directory that multiple users use in collaboration then you need to use a common user group and set the sgid bit (setgid).  I would setup a directory with a user common user group.  You can use the group ***users*** for this purpose.  The ownership could be* root:users* with permissions of 2775.  The leading 2 is the sgid bit set.  All files created in the directory would have the ownership of <creator>:users and permissions of 664.  All directories created would have ownership as <creator>:users and permissions of 775.  The inheritance is always preserved by the sgid bit set on the root or the file store.  

FWIW, I always use SFTP (OpenSSH) myself.  I haven't setup a FTP server in years.

---

