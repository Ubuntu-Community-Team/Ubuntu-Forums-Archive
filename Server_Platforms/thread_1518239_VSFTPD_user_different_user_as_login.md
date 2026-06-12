---
title: "VSFTPD user different user as login"
date: 2010-06-26
forum: Server Platforms
---

### Post by Leppie on 2010-06-26
is it possible to set up vsftpd to use a different user from the one used to log on?
for example, if i use uploader as the account to log onto the ftp service, can it be changed to siteowner during the logon phase so that all uploaded files will be owned by siteowner?

---

### Post by WinstonChurchill on 2010-06-27
> **Leppie said:**
> is it possible to set up vsftpd to use a different user from the one used to log on?
for example, if i use uploader as the account to log onto the ftp service, can it be changed to siteowner during the logon phase so that all uploaded files will be owned by siteowner?The vsftpd daemon runs as root - it can be configured to allow you to authenticate as a real local user, which would get you what you're looking for. 

Remember that FTP passwords are sent in the clear, and can easily be sniffed off the network - you'll want to use TLS/SSL for logins if your FTP client supports it. Read the man page for more information on how to configure the /etc/vsftpd.conf file:```
user@host:~$ man vsftpd.conf
```

---

### Post by Javich on 2010-06-28
Don't mean to be rude, but the vsftpd config file has everything you asked documented in it. Just open it and set it up according to your needs

```
sudo gedit /etc/vsftpd.conf
```

---

