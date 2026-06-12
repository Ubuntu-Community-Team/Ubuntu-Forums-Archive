---
title: "Help With SFTP Configuration"
date: 2024-03-08
forum: Server Platforms
---

### Post by flashc5 on 2024-03-08
[COLOR=#111111][FONT=-apple-system]hello,

I am having problems getting a sftp user to be able to log into a directory that is (and should be) owned by ubuntu.

I have ran the following commands

```

sudo addgroup sftpgroup
sudo adduser sftpuser_docs
```[/FONT][/COLOR]```
[COLOR=#111111][FONT=-apple-system]
sudo usermod -G sftpgroup sftpuser_docs[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]
sudo usermod -G sftpgroup ubuntu
/var/www/wwwroot$ sudo chown -R ubuntu:sftpgroup docs[/FONT][/COLOR]

```[COLOR=#111111][FONT=-apple-system]
[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]

for this file 
sudo vi /etc/ssh/sshd_config

I have tried this
[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]```
[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]
Match Group sftpgroup
    ChrootDirectory [/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]/var/www/wwwroot/docs[/FONT][/COLOR]
[COLOR=#111111][FONT=-apple-system]    PasswordAuthentication yes
    AllowTcpForwarding no
    X11Forwarding no
    ForceCommand internal-sftp
[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]
```[/FONT][/COLOR]
[COLOR=#111111][FONT=-apple-system]
and this
```

Match User sftpuser_docs
    ChrootDirectory /var/www/wwwroot/docs
    ForceCommand internal-sftp
    AllowTcpForwarding no
    X11Forwarding no
    PermitTunnel no
    PasswordAuthentication yes

```[/FONT][/COLOR]
[COLOR=#111111][FONT=-apple-system]
And of course restart the service...
```

 sudo systemctl restart ssh

```

unless the [/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]/var/www/wwwroot/docs is owned by root the user [/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]sftpuser_docs cannot log in.

here is what the log says
[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]tail /var/log/auth.log[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]
```

Mar  8 10:33:29 sshd[4990]: pam_unix(sshd:session): session closed for user sftpuser_docs
Mar  8 10:33:29 systemd-logind[631]: Session 64 logged out. Waiting for processes to exit.
Mar  8 10:33:29 systemd-logind[631]: Removed session 64.
Mar  8 10:33:35 sshd[5047]: Accepted password for sftpuser_docs from [myip] port 50567 ssh2
Mar  8 10:33:35 sshd[5047]: pam_unix(sshd:session): session opened for user sftpuser_docs(uid=1002) by (uid=0)
Mar  8 10:33:35 systemd-logind[631]: New session 65 of user sftpuser_docs.
Mar  8 10:33:35 sshd[5094]: fatal: bad ownership or modes for chroot directory "/var/www/wwwroot/docs"
Mar  8 10:33:35 sshd[5047]: pam_unix(sshd:session): session closed for user sftpuser_docs
Mar  8 10:33:35 systemd-logind[631]: Session 65 logged out. Waiting for processes to exit.
Mar  8 10:33:35 systemd-logind[631]: Removed session 65.


```[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]

[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system] ls -l /var/www/wwwroot/docs[/FONT][/COLOR]
```
[COLOR=#111111][FONT=-apple-system]
drwxr-xr-x 2 ubuntu sftpgroup 4096 Mar  8 10:03 member
[/FONT][/COLOR]
```[COLOR=#111111][FONT=-apple-system]

```
[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]/var/www/wwwroot$ ls -l[/FONT][/COLOR]
[COLOR=#111111][FONT=-apple-system]
drwxrwxr-x 4 ubuntu ubuntu    4096 Jan 22 14:49 css
drwxr-xr-x 5 ubuntu sftpgroup 4096 Mar  7 22:00 docs
-rw-rw-r-- 1 ubuntu ubuntu    5430 Jan 22 14:42 favicon.ico
-rw-rw-r-- 1 ubuntu ubuntu    1148 Jan 22 14:51 favicon.png
drwxr-xr-x 3 [/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]ubuntu ubuntu[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]      4096 Feb 21 23:54 imgs
drwxrwxr-x 2 ubuntu ubuntu    4096 Jan 22 14:31 js
drwxrwxr-x 6 ubuntu ubuntu    4096 Jan 22 14:31 lib
[/FONT][/COLOR][COLOR=#111111][FONT=-apple-system]
[/FONT][/COLOR]
[COLOR=#111111][FONT=-apple-system]
```
Sorry for the noob question but I am stuck figuring this out.  Thanks in advance
[/FONT][/COLOR]

---

### Post by TheFu on 2024-03-08
Please use forum code tags whenever posting terminal output.  Columns don't line up correctly otherwise.  Don't make it hard to help you.

ssh/scp/sftp all honor standard Unix permissions.

Basically, you need to learn Unix file and directory permissions.  Find a tutorial. Work it.  Then spend 30-60 minutes actually testing what you learned with 3 new userids under /tmp/foo/ creating new directories and files. Try every possible Linux permission and group and owner setting available from 000 - 777.  Spend extra time on 664, 775,. 750,  640, and 711.  It would also be helpful if you learned about the setgid flag.  Spend the time now to avoid hours, days, weeks, months of frustration.

```
drwx[COLOR="#FF0000"]r-xr[/COLOR]-x 2 ubuntu sftpgroup 4096 Mar  8 10:03 member
```

Red is the issue with that directory. fix that.  Forget sftp for now. When the local permissions are working correctly, then sftp will work as you want too.

BTW, you probably want the top directory for the files to be ```
drwxrw[COLOR="#FF0000"]s[/COLOR]r-x
``` and you'll need to ensure every subdirectory has the same and then chgrp -R to your sftpgroup for all files and directories you want the group to have write access into.  There are some caveats for the setgid flag, so be certain you understand those.

---

### Post by flashc5 on 2024-03-08
Thank you for the reply.

So should the member directory be 750?

Do I need to create the sftpgroup or can I just add the user sftpuser_docs as the owner?  Its really just that sftp user and ubuntu user(web server daemon) that needs to be able to read write to that directory

---

### Post by TheFu on 2024-03-08
As I said before,  make the directory permissions:
```
drwxrwsr-x
```

> **TheFu said:**
>  
Basically, you need to learn Unix file and directory permissions.  Find a tutorial. Work it.  Then spend 3060 minutes actually testing what you learned with 3 new userids under /tmp/foo/ creating new directories and files. Try every possible Linux permission and group and owner setting availble from 000 - 777.  Spend extra time on 664, 775,. 750,  640, and 711.  It would also be helpful if you learned about the setgid flag.  Spend the time now to avoid hours, days, weeks, months of frustration.
 .

Until you do that, you'll screw up any instructions I might provide, since I'm not on the system to check for 50 other issues too.
> 
So should the member directory be 750?
No.
> 
Do I need to create the sftpgroup or can I just add the user sftpuser_docs as the owner? Its really just that sftp user and ubuntu user(web server daemon) that needs to be able to read write to that directory 
No. 

There are 50 possible solutions. Until you learn the basics, you cannot make good choices.  File and directory permissions are the first layer of security for any server. Get those wrong and your server will be pwnd, quickly.

---

### Post by flashc5 on 2024-03-08
Hello again.

I did take a tutorial and I believe I have the basics.  For simplification purposes lets consider this example (1 user, no groups, with full 777 permissions)


```

ls -l /
lrwxrwxrwx   1 root root     7 Apr 20  2022 bin -> usr/bin
drwxr-xr-x   4 root root  4096 Mar  9 00:25 boot
drwxrwxrwx   4 root root  4096 Mar  9 03:10 data
.......

ls -l /data
drwxrwxrwx 3 sftpuser_backups sftpuser_backups 4096 Mar  9 03:18 backups

ls -l /data/backups/
drwxrwxrwx 2 sftpuser_backups sftpuser_backups 4096 Mar  9 03:18 2024-03-08

```


```

sudo vi /etc/ssh/sshd_config
....
Match User sftpuser_backups
    ChrootDirectory /data/backups
    ForceCommand internal-sftp
    AllowTcpForwarding no
    X11Forwarding no
    PermitTunnel no
    PasswordAuthentication yes
.....
sudo systemctl restart ssh

```

```

sshd[1781]: Accepted password for sftpuser_backups from [MYIP] port 60243 ssh2
sshd[1781]: pam_unix(sshd:session): session opened for user sftpuser_backups(uid=1003) by (uid=0)
systemd-logind[624]: New session 21 of user sftpuser_backups.
**sshd[1827]: fatal: bad ownership or modes for chroot directory component "/data/"**
sshd[1781]: pam_unix(sshd:session): session closed for user sftpuser_backups
systemd-logind[624]: Session 21 logged out. Waiting for processes to exit.
systemd-logind[624]: Removed session 21.

```

I have sftpuser_backups as the owner with full 777 permissions.  Why doesnt it work?

Edit:
I even took it a step further and set the entire dir to be owned by sftpuser_backups
```

sudo chown sftpuser_backups:sftpuser_backups /data
ubuntu:/data$ ls -l /
lrwxrwxrwx   1 root             root                 7 Apr 20  2022 bin -> usr/bin
drwxr-xr-x   4 root             root              4096 Mar  9 00:25 boot
drwxrwxrwx   4 sftpuser_backups sftpuser_backups  4096 Mar  9 03:10 data

```

still doesnt work...same error (sshd[2441]: fatal: bad ownership or modes for chroot directory component "/data/")

---

### Post by TheFu on 2024-03-09
The manpage for sshd_config explains the requirements to setup a ChrootDirectory, so I won't repeat all of them all here, but the first paragraph is pretty clear:

```
     ChrootDirectory
             Specifies the pathname of a directory to chroot(2) to after authen&#8208;
             tication.  At session startup sshd(8) checks that all components of
             the pathname are root-owned directories which are not writable by
             any other user or group.  After the chroot, sshd(8) changes the
             working directory to the user's home directory.  Arguments to
             ChrootDirectory accept the tokens described in the TOKENS section.
...
```
Using 777 permissions is also a problem.  ssh isn't dumb so it wouldn't work if you do that ... among other things.  It goes into the "For safety ..." explanation too, which you appear to be violating.

But it appears to me that you have bad file permissions, the wrong owner, and don't really understand how groups work.

---

### Post by flashc5 on 2024-03-09
> **TheFu said:**
> The manpage for sshd_config explains the requirements to setup a ChrootDirectory, so I won't repeat all of them all here, but the first paragraph is pretty clear:

```
     ChrootDirectory
             Specifies the pathname of a directory to chroot(2) to after authen&#8208;
             tication.  At session startup sshd(8) checks that all components of
             the pathname are root-owned directories which are not writable by
             any other user or group.  After the chroot, sshd(8) changes the
             working directory to the user's home directory.  Arguments to
             ChrootDirectory accept the tokens described in the TOKENS section.
...
```
Using 777 permissions is also a problem.  ssh isn't dumb so it wouldn't work if you do that ... among other things.  It goes into the "For safety ..." explanation too, which you appear to be violating.

But it appears to me that you have bad file permissions, the wrong owner, and don't really understand how groups work.

well from the start of this thread you have been saying its permissions related so in a toubleshooting effort i give it full ownership and full permissions.  Still doesnt work.

Changing the parent directory to root does work.

I find that 700 seems to work for my needs since that is the only user that will be accessing that directory.

What is not clear to me is why 600 doesnt work but 700 does.  600 is rw which is all I am doing, why does it need execute when nothing is being executed?

I am by no means an expert on this so that is why I am reaching out asking for help.

---

### Post by flashc5 on 2024-03-09
So setting the directory to drwxrwsr-x should be 2775 
The setgid bit makes it so that everything is execute by the owner sftpuser_docs?  Can I ask why this is a good/desirable thing?  I guess I dont understand why that matters.

---

### Post by deadflowr on 2024-03-09
> What is not clear to me is why 600 doesnt work but 700 does. 600 is rw which is all I am doing, why does it need execute when nothing is being executed?
Probably as good as explanation as any:
[https://superuser.com/a/169418](https://superuser.com/a/169418)

---

### Post by TheFu on 2024-03-09
> **flashc5 said:**
> So setting the directory to drwxrwsr-x should be 2775 
The setgid bit makes it so that everything is execute by the owner sftpuser_docs?  Can I ask why this is a good/desirable thing?  I guess I dont understand why that matters.

In post #2, I suggested a method to learn Unix file and directory permissions.  If you'd done that, it should be clear.  I even provided specific permissions to be understood.  Maybe some other people can better explain.

This is my failure. So sorry to have wasted your time.

---

### Post by jansalleine on 2024-03-13
> **flashc5 said:**
> So setting the directory to drwxrwsr-x should be 2775 
The setgid bit makes it so that everything is execute by the owner sftpuser_docs?  Can I ask why this is a good/desirable thing?  I guess I dont understand why that matters.

I'll give it a try to explain:
You want both Users "ubuntu" and "sftpuser_docs" to have read/write access in that directory. Because they both share the same group "sftgroup" you want to make sure that every new file files created in that directory gets owned by the group "sftgroup" and not by i.e. another group that "ubuntu" or "sftpuser" are in. That is what the setgid bit does.

For example:
I set my apache directory (/var/www) to 2775 and added my normal user to the www-data group. When I log in and write a file to /var/www (*touch testfile*) it will end up like this:

```

drwxrwsr-x  6 www-data www-data 4096 Mär 13 14:12 .
-rw-rw-r--  1 spider   www-data    0 Mär 13 14:12 testfile

```

If I do the same in my home directory (*touch testfile*) the file will have my users main group:

```

drwxr-x--- 7 spider spider     4096 Mär 13 14:17 .
-rw-rw-r-- 1 spider spider        0 Mär 13 14:17 testfile

```

---

### Post by flashc5 on 2024-03-18
> **jansalleine said:**
> I'll give it a try to explain:
You want both Users "ubuntu" and "sftpuser_docs" to have read/write access in that directory. Because they both share the same group "sftgroup" you want to make sure that every new file files created in that directory gets owned by the group "sftgroup" and not by i.e. another group that "ubuntu" or "sftpuser" are in. That is what the setgid bit does.

For example:
I set my apache directory (/var/www) to 2775 and added my normal user to the www-data group. When I log in and write a file to /var/www (*touch testfile*) it will end up like this:

```

drwxrwsr-x  6 www-data www-data 4096 Mär 13 14:12 .
-rw-rw-r--  1 spider   www-data    0 Mär 13 14:12 testfile

```

If I do the same in my home directory (*touch testfile*) the file will have my users main group:

```

drwxr-x--- 7 spider spider     4096 Mär 13 14:17 .
-rw-rw-r-- 1 spider spider        0 Mär 13 14:17 testfile

```

Thank you, this is very helpful.

---

