---
title: "Need help with file server"
date: 2011-01-22
forum: Server Platforms
---

### Post by Red Rebel on 2011-01-22
I am looking to set up a file server for the company I work for, running Ubuntu Server, 10.04 LTS 64 bit. The requirements are as follows. Users must be able to drag and drop files to and from server, from their Windows based laptops, via gui. Access must be available locally and through the internet. Users must only have access to sftp. Users must not be able to access the command line, or any other service or protocol. User access must be easily configurable to only a few predefined directories. Users must not be able to roam around important system files and directories, even within their own home directory. Solution must be free and open source. 

     Based on the information that I have gathered so far, VanDyke's VShell Server, and client software, SecureCRT or SecureFX, **APPEAR** to be the best solution for us. They support the requirements that we are looking for, however, their software is not free. A license must be purchased annually. We want to steer away from licensing fees, and instead, embrace free open source software. 

     OpenSSH, available through the Ubuntu repositories, seems to lack some features that we are looking for. For one, operating system file level security is required. This would make restricting user access to only a few directories a cumbersome process, since the software itself doesn't have the capability to restrict directory access like VShell does, directory access would have to be predefined through the os file permissions. Secondly, access cannot be limited to sftp only. Users will have access to the command line, and this is something that we want to prevent. Please feel free to correct me about my assumptions in respect to OpenSSH as I am a new to Ubuntu. We are looking for a free open source solution that meets our requirements. Any input would be greatly appreciated. 


thanks in advance 
rj

---

### Post by amra.sonntag on 2011-01-22
I have been thinking about this problem too.

I came up with this: [http://ubuntuforums.org/showthread.php?p=10381354#post1038135](http://ubuntuforums.org/showthread.php?p=10381354#post1038135)

That way your users are contained to home directories and have no shell acces.

---

### Post by Red Rebel on 2011-01-22
I took a look at your post, and it appears to be very interesting. Basically, it appears, that you have modified the sshd_config file, from OpenSSH server, to prevent shell access, and only give the user access to their home directory. This brings me one step closer to what I need, but I am not sure that it takes me quite where I need to be. I need users to be able to share folders. Is this possible with your method? Thanks again for your valuable input. 

rj

---

### Post by Red Rebel on 2011-01-22
Also, I found these two links posted by another user on launchpad.net. I think you may find them very interesting.

[http://www.sublimation.org/scponly/wiki/index.php/Main_Page](http://www.sublimation.org/scponly/wiki/index.php/Main_Page)

[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

tell me what you think.

thanks again...

rj

---

### Post by amra.sonntag on 2011-01-23
Hello hello,

the 2nd link you posted is more or less where I got my information from.

If you want to modify it to what you want to do - you would probably have to play around with permission rights. Example:

I suppose you could create a user Share with group Share. Add group Share to all your Users and place a link to the Share's homefolder inside the User's homefolder. It might work with the right permissions set. (Can User B have his home inside User As home? It would help alot - but i'm not sure)

scponly looks nice - and it is even in the repos - i might try it someday. Thx

I'll test playing around with permissions later today and tell you, how it went.

;)

Edit: Ha - playtime is over. I believe, that i managed to solve this puzzle. My solution is to add all the users to one group (we do this more or less anyway for sshd_config) and create the Home dirs inside one another. But it might help more, when you take a look at it yourself:
```
[FONT=monospace]# this is not intended to be run - it is just an example

# First create a user for the sftp/share group
# we specify user the user ID, because we want to use it later on

adduser --uid 1111 --home /yourpath/NAMEOFSHARE sftpshare
# we don't intend to let anybody really use this user so:
usermod -s /bin/false sftpshare

# Now we create our User - we specify his Home and the GroupID
# this way he will be part of the sftpshare group by default
adduser --gid 1111 --home /yourpath/NAMEOFSHARE/USERNAME USERNAME
# our SFTP users aren't allowed to log in
usermod -s /bin/false USERNAME

# Now we need to get the permissions for read and write access in the right places

# 1. Only our user should be able to enter his HOME
chmod 700 /yourpath/NAMEOFSHARE/USERNAME

# 2. We need to give NAMEOFSHARE to root and set the right permissions
# so we can ChrootDirectory /yourpath/NAMEOFSHARE for your Users in sshd_config
chown root:sftpshare /yourpath/NAMEOFSHARE
chmod 750 /yourpath/NAMEOFSHARE

# 3. Since our Users cannot write into NAMEOFSHARE, we create a SHARE folder
mkdir /yourpath/NAMEOFSHARE/SHARE
chown sftpshare:sftpshare /yourpath/NAMEOFSHARE/SHARE
chmod 770 /yourpath/NAMEOFSHARE/SHARE[/FONT]

```

Don't forget to edit your sshd_config to the new group and give everyone there the same Root dir.

I tested this method - and have now a safe account inside a share folder when connecting to my little server sandbox.

---

### Post by Red Rebel on 2011-01-23
I will attempt to replicate that today, report back. Seems like it may just work out for me. 

thanks again,

rj

---

