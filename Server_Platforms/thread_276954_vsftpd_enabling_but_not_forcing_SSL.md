---
title: "vsftpd: enabling but not forcing SSL?"
date: 2006-10-13
forum: Server Platforms
---

### Post by Futile on 2006-10-13
I would like to enforce encryption on all log ins from the internet (not anonymous browsing), but having it be optional within the LAN; I'm hoping you guys can help me out.

Connecting from within my LAN gets me 8-9MB/s to the FTP, with SSL off. With encryption on however, it drops to a measly 160-170Kbit/s. I want the extra security of SSL whenever I log in from the internet, but within the LAN it's much more important with speed.

How do I (for internet connections only) enforce SSL for local users, while still allowing unencrypted anonymous browsing?

---

### Post by _AA_ on 2006-10-17
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES


This should cause authenticated users to use SSL and anonymous users to not use SSL.

My question is how the hell did you get SSL working in the first place?


root@elvira:/etc/courier# 
root@elvira:/etc/courier# /usr/sbin/vsftpd 
**500 OOPS: SSL: cannot load RSA certificate**
root@elvira:/etc/courier# 
root@elvira:/etc/courier# 
root@elvira:/etc/courier# 
root@elvira:/etc/courier# cat /etc/vsftpd.conf | grep rsa
**rsa_cert_file=/etc/vsftpd/vsftpd.pem**
root@elvira:/etc/courier# 
root@elvira:/etc/courier# ls -l /etc/vsftpd/vsftpd.pem
**-rw-r--r-- 1 root root 2111 2006-10-17 15:15 **
root@elvira:/etc/courier#

---

### Post by Futile on 2006-10-20
There were pre-set certs already configured for use in the default vsftpd.conf 

I simply let it use those defaults, and connected with filezilla from windows - worked like a charm. I've since created my own certs and keys, I wasn't sure if it was a good idea to use default keys. 

Anyhow, your suggestion doesn't solve my problem. I want SSL from the internet but not in the LAN. Anonymous users should always browser without encryption.

---

