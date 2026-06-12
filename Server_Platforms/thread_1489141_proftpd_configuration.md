---
title: "proftpd configuration"
date: 2010-05-20
forum: Server Platforms
---

### Post by PyrexKidd on 2010-05-20
I am trying to set up an ftp server using proftpd and Ubuntu Server 9.10.

I need each ftp user to be able to log in and have access to their directory.
ie:
```

user1 --> /home/user1
user2 --> /some/other/directory
user3 --> /still/another/directory

```

I am able to log in from the command line using
```

$ftp address.to.server

```

but when i attempt to connect using filezilla or any other FTP client I am get the following error
```

Status:	Resolving address of address.toserver
Status:	Connecting to 10.10.10.10:21...
Status:	Connection established, waiting for welcome message...
Response:	220 ProFTPD 1.3.2 Server (Debian) [::ffff:address.to.server]
Command:	USER user1
Response:	331 Password required for user1
Command:	PASS ********
Response:	530 Login incorrect.
Error:	Critical error
Error:	Could not connect to server

```

how do I configure this to enable multiple users?  I have checked the documentation at [http://proftpd.org/localsite/Userguide/linked/userguide.html](http://proftpd.org/localsite/Userguide/linked/userguide.html)

and didn't see a way to do this.  What am I missing?

---

