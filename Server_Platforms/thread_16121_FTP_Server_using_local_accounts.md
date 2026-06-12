---
title: "FTP Server using local accounts"
date: 2005-02-19
forum: Server Platforms
---

### Post by thorN on 2005-02-19
I am planning to set up a web/ftp server which uses local system accounts for each site hosted.

I've set up apache to fetch sites from the /home/*user*/public_html/ directories without a problem, and set up virtual hosts.

However, I can't manage to make VSFTPD work with local accounts. (Using local log in details to access FTP?)
In /etc/vsftpd.conf, I've set:
```
anonymous_enable=NO
local_enable=YES
chroot_local_user=YES
```

The users in question were all created with this command:
```
useradd -m -k /etc/skel -d /home/  *user* &&
passwd <password>
```

When I attempt to log in (using gFTP 2.0.17 on a seperate machine) I get this error:
```
Looking up 192.168.1.111
Trying 192.168.1.111:21
Connected to 192.168.1.111:21
220 Welcome to tR | Clan FTP service.
USER *user*
331 Please specify the password.
PASS xxxx
530 Login incorrect.
Disconnecting from site 192.168.1.111
```

I don't know where else to look to fix this, so could anyone help me?

Thanks

---

### Post by thorN on 2005-02-19
Oh wait, nevermind. I've fixed it now.

I had to set the shell for each user, or it wouldn't allow them to log into FTP.

My useradd command should've been:
```
useradd -m -k /etc/skel -d /home/ -s /bin/bash  *user* &&
passwd *user* <password>
```

I've figured out that I can set defaults for new users though, like this:
```
useradd -D -b /home/ -s /bin/bash
```

---

