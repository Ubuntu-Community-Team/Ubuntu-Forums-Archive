---
title: "OpenSSH authentication error: Algorithm negotiation fail"
date: 2016-10-27
forum: Server Platforms
---

### Post by bfordz on 2016-10-27
"newbie" I installed a Ubuntu Server 16.04 with the OpenSSH 7.2 package.
I need to backup our phone system files to a SFTP server; I'm switching from freeSSHd on WinXP to Linux.

When I try to send the file I get the following error:
An error occurred while trying to connect to the sftp server xxx.xxx.xxx.45

My system event log shows this error:
An error occurred while trying to connect to xxx.xxx.xxx.45 with s8800:Algorithm negotiation fail

My SSH System logs show this error:
Unable to negotiate with xxx.xxx.xxx.56 port 47027: no matching key exchange method found.  Their offer: diffie-hellman-group1-sha1,diffie-hellman-group-exchange-sha1 [preauth]

My question being new to Linux and SSH, what do I change and how do I change it to make this work?

---

### Post by bfordz on 2016-10-27
I tried adding this line to my sshd config files and I still get the same message.

KexAlgorithms +diffie-hellman-group1-sha1

any suggestions?

---

### Post by bfordz on 2016-10-28
After some more trial and error I got it to work.

I needed to add both diffie-hellman keys separately to my sshd_config file;
"KexAlgorithms +diffie-hellman-group1-sha1"
"KexAlgorithms +diffie-hellman-group-exchange-sha1"
Both line had to be added separately.

I still got the "Algorithm negotiation fail" message when trying to upload a file, but I got a different error message in my ssh log file.
"no matching cipher found. Their offer: aes128-cbc,3des-cbc,blowfish-cbc [preauth]"

I found I had to add another line to my sshd_config file;
"Ciphers   aes128-cbc,3des-cbc,blowfish-cbc"

I can now upload my backup files via SFTP to my Ubuntu Server.

---

### Post by Habitual on 2016-10-28
Good job and well done!

---

