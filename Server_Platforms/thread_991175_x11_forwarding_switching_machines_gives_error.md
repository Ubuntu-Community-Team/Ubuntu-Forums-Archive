---
title: "x11 forwarding switching machines gives error"
date: 2008-11-23
forum: Server Platforms
---

### Post by Diubidone on 2008-11-23
Hello,

I use x11 forwarding in order to managae two diferent ubuntu servers.
At first I was using one with x11 forwarding and everything was fine. Now i've installed a second server wich I wanted to manage the same way.

I set up the ssh config file and the on my term use

sudo ssh -x user@ipaddress

and i get this response 

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is NUMBER.
Please contact your system administrator.
Add correct host key in /home/USER/.ssh/known_hosts to get rid of this message.
Offending key in /home/USER/.ssh/known_hosts:2
RSA host key for IPNUMBER has changed and you have requested strict checking.
Host key verification failed.

can someone teach me how to solve this problem?

PS: since I will have to use this method to manage two different servers deleting the host file everytime is obviously not a solution.

---

