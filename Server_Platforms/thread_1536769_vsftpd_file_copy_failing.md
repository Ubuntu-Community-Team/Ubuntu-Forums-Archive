---
title: "vsftpd file copy failing"
date: 2010-07-22
forum: Server Platforms
---

### Post by somethingobscure on 2010-07-22
Hello

I've just installed Ubuntu server 10.04 and have set up vsftpd somewhat successfully. I can connect as my root user, and I only have access to my home directory. However, whenever I try to copy a file across a file I receive a 550 Permission denied error. 

I've run the command ls -l /home/directory and the result returned is total 0, when I was expecting details of permissions per user. I've tried running chmod -w /home/directory but this doesn't return any result nor change the result of the above ls command. 

Any pointers to what I should do next will be gratefully received! :)

---

### Post by terazen on 2010-07-22
Edit the /etc/vsftpd.conf file and uncomment the # before the directive that allows uploads.  I forget the exact directive to search for, but if you read the description above each directive it will be easy to spot.

Oh, also `ls -la` is probably the command you are looking for.

---

### Post by richardjh on 2010-07-22
terazen is right. You need to uncomment line 29 of /etc/vsftpd.conf

The line is
```

# Uncomment this to enable any form of FTP write command.
#write_enable=YES
```And you need to make it look like

```
# Uncomment this to enable any form of FTP write command.
write_enable=YES
```

And then restart vsftpd using

```
sudo service vsftpd restart
```

---

### Post by somethingobscure on 2010-07-25
Thanks for all of that guys, it solved the problem perfectly! :)

After using ls -la I found that my user didn't have write permissions to their home directory so used chmod u+w /home/directory to add write permission to the owner. Are there any security issues that this might cause that I should be aware of?

---

### Post by richardjh on 2010-07-27
It sounds good to me. 

Ultimately you have no choice really if you want to allow someone to write there, and the folder is owned by that user, and the permissions allow writing by only that user then that is the tightest you can get the permissions.

---

### Post by somethingobscure on 2010-07-28
Thanks! :)

---

