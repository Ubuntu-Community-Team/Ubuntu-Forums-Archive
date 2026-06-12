---
title: "cant access my running instance"
date: 2013-01-17
forum: Ubuntu Cloud and Juju
---

### Post by asraa on 2013-01-17
hi everbody

i successfully run my instance and create a key pairs but when i try to connect to it using command     $ ssh -i ~/.ssh/eucakey eucakey@192.168.1.120  ¨ eucakey is the keypair that i used ti run the instance  ¨  

the following output appear :

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
f1:33:79:7a:f1:86:c7:68:96:24:e8:c7:cc:b2:aa:93.
Please contact your system administrator.
Add correct host key in /home/asraa/.ssh/known_hosts to get rid of this message.
Offending RSA key in /home/asraa/.ssh/known_hosts:2
  remove with: ssh-keygen -f "/home/asraa/.ssh/known_hosts" -R 192.168.1.120
RSA host key for 192.168.1.120 has changed and you have requested strict checking.
Host key verification failed.

please help :cry:

---

