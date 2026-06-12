---
title: "UFW and ProFTPd"
date: 2010-12-27
forum: Security
---

### Post by jaymill on 2010-12-27
I am using ubuntu 10.04 fully updated on a VPS. I have two static IP's both working correctly. My problem is:

I run UFW to make iptables easy, and I enable the following ports, 21 (ftp), 22 (ssh), 80 (http), and 443 (ssl). SSH, apache and ssl all work perfectly, however ftp no longer does. I have tried in both active and passive modes. 

What I get is this; Filezilla connects and authenticates to the server successfully, but times out whenever trying to get the directory listing. Again, in both active and passive modes. I went in and tried to enable port 20 as well in UFW, but no dice. I'm really at a loss. Connective via a web browser fails as well.

If I connect with UFW off, it works perfectly. Any suggestions?

Thanks in Advance.

---

### Post by FuturePilot on 2010-12-27
You also need to open port 20 for FTP.

---

### Post by bodhi.zazen on 2010-12-27
> **jaymill said:**
> Any suggestions?

1. Check your logs to see what packets are being dropped =)

2. If at all possible, use ssh (sftp, scp).

---

