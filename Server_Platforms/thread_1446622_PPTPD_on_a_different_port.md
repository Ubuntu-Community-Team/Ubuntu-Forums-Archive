---
title: "PPTPD on a different port ?"
date: 2010-04-04
forum: Server Platforms
---

### Post by yesrno on 2010-04-04
Hello,

Some weeks ago I set up a VPN server with the pptpd package and everything was working fine. Now I was wondering if it is possible to connect trough VPN on another port than the default port (1723). 
I was searching for a solution for this but couldn't really figure out how to do it so I was hoping someone here could help me.
Even if I could let pptpd listen on a different port, can I even connect to a different port with the Windows VPN client (or any other client)? Or is this pretty much impossible =;
Thanks in advance.

---

### Post by yesrno on 2010-04-05
Mmm anyone ?

---

### Post by yesrno on 2010-04-06
Or not :-p ?

---

### Post by mbehamin on 2010-04-06
Hi 
im not very familiar with PPTPD you are using. but if there is no option for you in that service to change the Listening port you can easily Redirect it by DNAT option in iptables.

First configure your Server just listen into 127.0.0.1:1723 and then redirect all connection for you vpn into 1723:)

regards

---

