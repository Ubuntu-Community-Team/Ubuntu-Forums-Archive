---
title: "Pure-FTPd authentication issue"
date: 2011-03-04
forum: Server Platforms
---

### Post by bulldog5046 on 2011-03-04
Hi Everyone.
 
I've been searching around the net but seem to be so far drawing a blank on trying to find the issue i'm having at the moment. Hopefully someone may be able to offer me a bit of advice!
 
bit of background...
 
I have 2 Ubuntu Servers (10.04) setup in an active/passive cluster format with heartbeat.
 
the active services are: pure-ftpd, telnet, openssh and cron.
 
The problem...
 
I discovered today that Pure-FTPd seems to be allowing unix authentication. both UnixAuthentication & PAMAuthentication are set to 'no' in the conf dir.
 
this is a problem for me as i have both FTP and SFTP running, so whats happening is accounts that should ONLY be SFTP are able to be accessed using FTP, kind of defing the point of it.
 
does anyone know why this may be happening? and how i can go about preventing it?
 
Thanks in advance,
Ry

---

### Post by bulldog5046 on 2011-03-10
bump?

---

### Post by bulldog5046 on 2011-03-11
Managed to find a solution in the end.
 
edited /etc/pam.d/pure-ftpd to use the ftpallow list rather then deny.
 
```

# PAM config for pure-ftpd
# Standard behaviour for ftpd(8).
#auth   required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed
# Uncomment next line to allow non-anonymous ftp access ONLY for users,
# listed in /etc/ftpallow
auth    required        pam_listfile.so item=user sense=allow file=/etc/ftpallow onerr=fail
# Note: pure-ftpd handles anonymous logins on its own. Do not enable pam_ftp.so.
# Standard pam includes
@include common-account
@include common-session
@include common-auth
auth    required        pam_shells.so

```
 
then added the user that all virtual users are associated with to /etc/ftpallow
 
now SFTP users cannot login unsecured and likewise virtual users cant login to SFTP \\:D/

---

