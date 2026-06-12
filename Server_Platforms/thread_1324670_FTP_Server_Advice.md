---
title: "FTP Server Advice"
date: 2009-11-12
forum: Server Platforms
---

### Post by hambone79 on 2009-11-12
I just setup a Ubuntu 8.04 server machine to use as a dedicate FTP server, but I'm having a little trouble picking which FTP server software to use (I haven't setup an FTP server in 3 years). I have some requirements that I need to meet, so I wanted to see if there is anyone that can advise me on a server to do the following:

1. Must have TLS for security reasons.
2. Must be able to disable system users from using FTP (also for security).
3. Must be able to use virtual users, preferably with a MySQL backend.
4. Must have a means to monitor the server in real time.
5. Must be able to allow or restrict users/groups by directory.

I am creating this server so that clients can upload CAD models directly to me. Since these models are important proprietary information and I have signed non-disclosure agreements, I need to make sure that my clients can upload over an encrypted connection. I also need to make sure that my clients can not browse into other directories and steal information.

Thanks!

---

### Post by ibutho on 2009-11-12
Proftpd can be configured to use a mysql backend. I am not sure if it has all the features your require, but it worth taking a look at it.

---

### Post by hambone79 on 2009-11-12
I gave ProFTPd a shot but I still can't make TLS working and it's acting weird behind my firewall. 

Since I couldn't get ProFTPd working, I gave vsftpd a shot and it works beautifully. I now have a MySQL database handling logins, TLS encryption, and everyone is jailed in their own directories. It also works perfectly behind my router/firewall from the outside world so now I'm good to go!

---

