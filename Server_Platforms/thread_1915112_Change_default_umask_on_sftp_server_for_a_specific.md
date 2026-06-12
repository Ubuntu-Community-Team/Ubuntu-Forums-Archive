---
title: "Change default umask on sftp server for a specific group"
date: 2012-01-25
forum: Server Platforms
---

### Post by Frozen Forest on 2012-01-25
How do you change the default umask in a chroot sftp for the ChrootDirectory? I found this solution [http://serverfault.com/questions/70876/how-to-put-desired-umask-with-sftp](http://serverfault.com/questions/70876/how-to-put-desired-umask-with-sftp) but it seem to change the umask for all users, not only those that belong to a specific group or a specific folder. I would like the umask to be umask 0007, preferably would the owner be root but I think group rights will work. Is there a better solution then have cron run every min or so?

The server uses a chroot for group 'sftponly', the authentication is done by ssh-keys

```

sudo tree -puga /home/
/home/
&#9500;&#9472;&#9472; [drwxr-xr-x root     root    ]  userA
&#9474;   &#9492;&#9472;&#9472; [drwx------ userA sftponly]  .ssh
&#9474;       &#9492;&#9472;&#9472; [-rw-r--r-- userA sftponly]  authorized_keys
&#9500;&#9472;&#9472; [drwxr-xr-x root     root    ]  userB
&#9474;   &#9492;&#9472;&#9472; [drwx------ userB  sftponly]  .ssh
&#9474;       &#9492;&#9472;&#9472; [-rw-r--r-- userB  sftponly]  authorized_keys

``````

Subsystem sftp internal-sftp

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

Match group sftponly
    ChrootDirectory /home/sftp
    X11Forwarding no
    AllowTcpForwarding no
    ForceCommand internal-sftp

```

---

### Post by ruffEdgz on 2012-01-26
From my understanding of umask, its not for folders or groups but for individual or all users on a system:
> 
## From umask man page ##
The  user file-creation mask is set to mode.

If you want a certain user to have the umask '0007' whenever they login, you can set that in their .profile or .bashrc or .bash_profile which will solve it at an individual level.

I updated my .bash_profile with the following line 'umask 0007' and now I have this:
```

usera@testsrv ~$ umask
0007

```
When I created new directories or files I got this:
```

usera@testsrv ~$ ll -d ./new.*
drwxrwx--- 2 usera usera 4096 Jan 26 12:13 ./new.dir
-rw-rw---- 1 usera usera    0 Jan 26 12:13 ./new.file

```

If you want sftp to setup the umask for all users, I found this article that matches the one you found from servefault: [http://jeff.robbins.ws/articles/setting-the-umask-for-sftp-transactions](http://jeff.robbins.ws/articles/setting-the-umask-for-sftp-transactions)

If you want all the directories (only) to be set the way you want (0007) then you will need to complete a small command to make sure /home/user* to be the correct umask (this can NOT be done via sftp or through the umask command since it will change it for both directories and files for users):
```

sudo find /home/ -maxdepth 1 -name <username> -exec chmod 0770 {} \;

```
This will look in the /home dir and find the name <username> going only maxdepth of 1. Once a directory is found, it will execute chmod 0770 for all the found directories with the name "<username>" (that is what the {} part will do).

Hope this helps.

---

