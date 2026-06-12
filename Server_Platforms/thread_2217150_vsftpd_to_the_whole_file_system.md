---
title: "vsftpd to the whole file system?"
date: 2014-04-15
forum: Server Platforms
---

### Post by Votlon on 2014-04-15
I'm trying to set up an ubuntu server for local websites. I need to use it to test a single website over a couple computers, but I'm trying to set up my vsftpd to ftp into the computer to change files around but whenever i set it up it only ftp's me into a single directory and won't let me edit the rest. 
So just wondering how i can set up an ftp that allows me to edit all of the computers files or even just all the files in var/www/ 

Please and thank you!

---

### Post by slickymaster on 2014-04-15
Moved to Server Platforms.

---

### Post by nerdtron on 2014-04-15
> **Votlon said:**
> I'm trying to set up an ubuntu server for local websites. I need to use it to test a single website over a couple computers, but I'm trying to set up my vsftpd to ftp into the computer to change files around but whenever i set it up it only ftp's me into a single directory and won't let me edit the rest. 
So just wondering how i can set up an ftp that allows me to edit all of the computers files or even just all the files in var/www/ 

Please and thank you!

Because when you create a user (or even the default user) for the vsftpd, you only have permissions to write on your specified directory. If you want to upload to the /var/www directory you need to edit the permissions of the folder.
I think your /var/www permission looks like this
```
user@server:~$ls -l /var/
drwxr-xr-x  3 www-data www-data 12288 Feb  1 16:20 www
```

Let's say you have "user" as the username. You need to add your user to the www-data group. Note that its a capital G.
```
usermod -a -G www-data user
```

Then have the group write permissions on the /var/www/ folder.
```
chmod -R g+w /var/www
```

Try to login again as "user" and copy files to the /var/www folder.

---

### Post by Votlon on 2014-04-17
my permissions look like this:

```
user@server:~$ls -l /var/
drwxr-xr-x  3 root root     4096 Apr 15 16:34 www
```


when i used your usermod command it tell me this :
 
 ```
user@server:~$ usermod -a -G www-data user
 usermod: cannot lock /etc/passwd; try again later.
```

---

### Post by Votlon on 2014-04-17
Never mind i figured this out! I just changed around the chroot_list and it fixed it but thank you for all the help!

---

