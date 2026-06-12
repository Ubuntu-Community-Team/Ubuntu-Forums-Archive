---
title: "unable to configure ssh"
date: 2011-06-09
forum: Security
---

### Post by new_to_this_stuff on 2011-06-09
[FONT=Arial][SIZE=2]Hi, I am attempting to secure a vps server i got through a cloud hosting company by editing sshd_config.  
To test this method I changed the port from 22 to 2223 and restarted ssh using [/SIZE][/FONT]
```
sudo /etc/init.d/ssh restart
```I then checked to see if ssh was listening on this port with

```
sudo ss -lnp | grep sshd
```which shows

0 128 :::2223 :::* users: (("sshd",1357,4)) 
0 128 *:2223 *:* users: (("sshd",1357,3))

[FONT=Arial][SIZE=2]However when I try to connect from my laptop using port 2223 i get "connection refused"
I can only connect on port 22 using the hosting companies generated console username but I don't want anyone to be able to connect on port 22.

Any insight into what is going on would be much appreciated.

Thank you.[/SIZE][/FONT]

---

### Post by e79 on 2011-06-09
Is it possible your server is behind the company's firewall that would block your requests on port 2223 ? If they/you have a firewall and did not allow the port to be forwarded, that would be the reason.

---

### Post by pricetech on 2011-06-09
Check the documentation from the hosting company.  You may be required to use the default port.

---

### Post by new_to_this_stuff on 2011-06-09
Thank you for your replies, I will check with the hosting company.

---

