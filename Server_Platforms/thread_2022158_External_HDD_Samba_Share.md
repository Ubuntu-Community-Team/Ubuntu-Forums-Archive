---
title: "External HDD Samba Share"
date: 2012-07-10
forum: Server Platforms
---

### Post by jwsicomputing on 2012-07-10
Hi there,

I am trying to use my external hdd to create another samba share from my ubuntu server, it worked for a day and then when i restarted the machine all i get when i try to connect from a remote machine is 'access denied'

Please help, i have tried changing the smb.conf file to force user = jwsiadmin (my username) but still no luck

Thanks
James

---

### Post by RyanRahl on 2012-07-10
It's probably a file permissions problem. you should post the directive describing the share from your smb.conf, and an ls -l of the path the share points to.

---

### Post by HermanAB on 2012-07-10
Howdy,

It is possible that the external drive was only mounted after the Samba server was already up and running, so Samba failed on the unavailable drive.  Ensure that the drive is mounted then restart samba.

---

