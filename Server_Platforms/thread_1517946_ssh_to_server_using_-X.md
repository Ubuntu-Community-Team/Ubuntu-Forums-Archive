---
title: "ssh to server using -X"
date: 2010-06-25
forum: Server Platforms
---

### Post by jmsgz on 2010-06-25
hi folks
  i can ssh into server by command line without -X opt.
also able to use remote desktop using gui.

when attempting to ssh with -X opt i get the following message



xxx@xxx-desktop:~$ ssh -X [email]xxx@xxx-lserver.local[/email].
The authenticity of host 'xxx-lserver.local. (192.168.0.102)' can't be established.
RSA key fingerprint is 52:e9:e6:1c:c2:aa:34:8e:46:ac:50:94:a1:95:79:61.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'xxx-lserver.local.' (RSA) to the list of known hosts.
[email]xxx@xxx-lserver.local[/email].'s password: 
Linux xxx-lserver 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

Last login: Fri Jun 25 17:50:06 2010 from xxx-desktop.local
/usr/bin/X11/xauth:  error in locking authority file /home/xxx/.Xauthority
xxx@xxxlserver:~$ nautilus
X11 connection rejected because of wrong authentication.
Could not parse arguments: Cannot open display


can you help?

thanks in advance
jsg

---

