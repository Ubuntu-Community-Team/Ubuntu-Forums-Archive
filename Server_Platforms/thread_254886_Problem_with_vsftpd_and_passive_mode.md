---
title: "Problem with vsftpd and passive mode"
date: 2006-09-10
forum: Server Platforms
---

### Post by 0001001 on 2006-09-10
I've got a problem using vsftpd in passive mode on my server, which is behind a router.
Here's what I've done:

- forwarded the ports 8000-8010 to my server
- compiled and installed vsftpd 2.0.5
- my /etc/vsftpd.conf looks like this:
```
anonymous_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
listen=YES
pasv_enable=YES
pam_service_name=vsftpd
pasv_max_port=8010
pasv_min_port=8000
pasv_address=80.149.130.xxx

```
- started vsftpd manually
- connecting to my server using an ftp client. here's the log file:
```

[R] Connecting to 84.149.130.xxx PORT=21
[R] Connected to 84.149.130.xxx 
[R] 220 (vsFTPd 2.0.5)
[R] USER anonymous
[R] 331 Please specify the password.
[R] PASS (hidden)
[R] 230 Login successful.
[R] SYST
[R] 215 UNIX Type: L8
[R] FEAT
[R] 211-Features:
[R]  EPRT
[R]  EPSV
[R]  MDTM
[R]  PASV
[R]  REST STREAM
[R]  SIZE
[R]  TVFS
[R] 211 End
[R] CWD /
[R] 250 Directory successfully changed.
[R] PWD
[R] 257 "/"
[R] TYPE A
[R] 200 Switching to ASCII mode.
[R] PASV
[R] 227 Entering Passive Mode (84,149,130,xxx,234,238)
[R] Opening data connection IP: 84.149.130.xxx PORT: 60142
[R] Data Socket Error: Connection timed out
[R] List Error

```

As you can see, the client tries to open the data connection on port 60142 instead of using a port between 8000-8010.

Can someone please give me a hint how to get vsftpd to use the ports I've specified?

---

