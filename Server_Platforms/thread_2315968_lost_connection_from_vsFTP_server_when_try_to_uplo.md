---
title: "lost connection from vsFTP server when try to upload"
date: 2016-03-04
forum: Server Platforms
---

### Post by michael356 on 2016-03-04
Hi group

i got error info as follow
```
ftp> send policy.txt
227 Entering Passive Mode (10,200,54,194,55,27).
421 Service not available, remote server has closed connection
ftp>
```

the upload file  store 0 KB size on the FTP server. it lost the connection to the server when it start to transmit data.

does any one meet this issue ? 

Ubuntu 14.04

---

### Post by michael356 on 2016-03-04
BTW, the version of vsftpd is 3.0.2

---

### Post by darkod on 2016-03-04
Do you have a firewall and/or port forwarding between the client and the server? In most cases like this, the firewall is blocking the connection as soon as the ftp wants to start using passive mode.

---

### Post by michael356 on 2016-03-05
> **darkod said:**
> Do you have a firewall and/or port forwarding between the client and the server? In most cases like this, the firewall is blocking the connection as soon as the ftp wants to start using passive mode.

no , firewall has been disabled, i can create folders on the ftp server with login account.

---

### Post by darkod on 2016-03-05
With login account, you mean over ssh session? That is not relevant for testing ftp.

You just said above that it fails the ftp connection, and that's the only way you can test ftp. To me it still looks like you are having issues when the connection converts to passive mode. Have you limited the passive mode ports to specific values? If there is port forwarding are you forwarding these ports too?

Otherwise the message you are receiving above doesn't make much sense.

---

### Post by michael356 on 2016-03-05
the issue only happens when i try to upload files.

---

