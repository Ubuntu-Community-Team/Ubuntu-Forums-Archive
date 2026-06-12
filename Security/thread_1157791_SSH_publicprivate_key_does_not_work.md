---
title: "SSH public/private key does not work"
date: 2009-05-13
forum: Security
---

### Post by Shungo73 on 2009-05-13
Hi guys,

i have now changed from UbuntuStudio 8.04 to 9.04 and some things are great, no crashes anymore like Pidgin.

But for some reason i do have some issues with using SSH.

SSH with passphrase:
works fine

SSH with public/private key:
does not work.

when changing my key to 600 and the folder to 700 and trying to connect to one of our server following will happen:

ddietz@ws46:~$ ssh worker
The authenticity of host 'worker (x.x.x.x)' can't be established.
DSA key fingerprint is bd:d3:03:59:be:a3:ea:d3:52:d7:e8:42:3f:7f:10:9a.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'worker,x.x.x.x' (DSA) to the list of known hosts.
Permission denied (publickey).

the server is reachable via ping so there is no network issue.

my key is correct as it works on UbuntuStudio 8.04 and default Ubuntu Desktop. It also works fine when using it on windows with SecureCRT.


Does anybody know what is wrong with UbuntuStudio 9.04 i386 and AMD64 and SSH???


Thanks
Shungo

---

### Post by Shungo73 on 2009-05-13
strange...now it's working without changing anything... :-(

---

### Post by Bark on 2009-05-13
Use the -v option to debug ssh connections.

You can add more and more of them to get more and more verbose output.

ssh -v -v -v

etc.

This usually gives enough hints to solve the problem. :popcorn:

---

### Post by Shungo73 on 2009-05-20
ok, found out that Ubuntustudio 8.10 works pretty fine untill updating to 9.04 via the automatic upgrade option.
 
Could see following upgraded packets:
 
openssh-client
openssl
openssl-blacklist
 
ssh-askpass-gnome
 
 
Are they related to the issue???
 
Hope someone can help me. 
 
Thanks

---

### Post by freddyflintstone on 2009-05-20
Hi,

(1)  Use ssh -vv as suggested.
(2) Have a look at the log on the server side, e.g. sudo tail -100 /var/log/secure. This should give you an indication of the problem if the issue is server-side.

---

