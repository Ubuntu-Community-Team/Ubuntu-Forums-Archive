---
title: "sftp fails for LDAP users (ssh works)"
date: 2011-05-24
forum: Server Platforms
---

### Post by hewbert on 2011-05-24
Hello,

I've recently migrated our web server to authenticate against a different LDAP service.  Since then, users in LDAP trying to use SFTP have authentication failures.  However, they are able to use SSH and plain ol' FTP.  Local system users are also able to use SFTP.

I didn't change any of my PAM configs, so it's a bit perplexing.  Here's what /var/log/auth.log looks like when an attempt is made:
```

May 24 11:24:51 web1 sshd[8633]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=24.xxx.x.xxx  user=user
May 24 11:24:51 web1 sshd[8633]: Accepted password for user from 24.xxx.x.xxx port 57296 ssh2
May 24 11:24:51 web1 sshd[8633]: pam_unix(sshd:session): session opened for user user by (uid=0)
May 24 11:24:51 web1 sshd[8704]: subsystem request for sftp
May 24 11:24:51 web1 sshd[8633]: pam_unix(sshd:session): session closed for user user

```

Notice that it does accept the credentials.

I can provide any configs or PAM configurations as needed.

In /etc/ssh/sshd_config, I have:

Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes

---

### Post by hewbert on 2011-05-25
What a silly issue...  After testing with 'sftp -v user@remotehost', I was getting an error of "Received message too long ...."  From reading, this appears to be caused by receiving data that wasn't expected (e.g. a .bash_profile or .profile echoing something).  None of mine had anything that I could tell that would print any text.  I moved all of my .bash* and .profile in /etc/ to a backup anyway and was able to login.

I'll have to dig through my system-wide bashrc and see what the culprit might be, but good to know anyway.

---

