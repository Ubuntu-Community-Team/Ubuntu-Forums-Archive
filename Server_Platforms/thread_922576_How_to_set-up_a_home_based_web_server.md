---
title: "How to set-up a home based web server"
date: 2008-09-17
forum: Server Platforms
---

### Post by Thievrey Corporation on 2008-09-17
Hello,

I would like to use my computer, running under Ubuntu 8.04, as a server that I could access via Internet when I am away.
The machine would be the server on which I store all my files, and to which I can connect through Internet when I am not home.
Could someone indicate a good tutorial to do so ?
Many thanks,

TC

---

### Post by baudday on 2008-09-17
I just started one over the summer, and Logged pretty much everything I did. Check out the link in my sig. Maybe it helps.

---

### Post by Thievrey Corporation on 2008-09-18
Thanks for your answer; I'll see what I can do with these instructions.

---

### Post by timcredible on 2008-09-18
your main problem will be a static ip address (you'll need to know where your server is, and normal home type isp connections use dhcp).  there's an app you can run that will register your ip address with a known server on the internet and then it will dynamically change a dns entry so you can always access your server.  i don't remember what the app is called though.

---

### Post by XioNoX on 2008-09-18
no-ip.com and there are a package in the repos called noip2 to manage it

---

### Post by Thievrey Corporation on 2008-09-20
Thanks to you.

After setting up **noip** account and installing **noip2**, will I need to do some sort of port forwarding on my router?

---

### Post by Jive Turkey on 2008-09-20
Yes you will need port forwarding, but first you should choose the technology for accessing your computer remotely.  whether you use ftp or ssh or whatever will affect which port is used by default.  

You should also look into changing the default port for the server type for security reasons.  If you leave the default port type open to the 'net, potential intruders will have an easier time hacking your box because they can guess the protocol in use based on the port that is open.

---

### Post by Dr Small on 2008-09-20
> **Jive Turkey said:**
> Yes you will need port forwarding, but first you should choose the technology for accessing your computer remotely.  whether you use ftp or ssh or whatever will affect which port is used by default.  

You should also look into changing the default port for the server type for security reasons.  If you leave the default port type open to the 'net, potential intruders will have an easier time hacking your box because they can guess the protocol in use based on the port that is open.
Potential intruders will not have an easier time hacking a box with a standard port. It meerly allows scriptkiddie bots to flood your logs with unattempted logins (if you are using SSH/FTP).

---

### Post by cariboo on 2008-09-21
I would suggest using denyhosts, this bans an ip address permanently are 5 unsuccesful attempts to log in. Denyhosts is in the repositories, and just plain works. Here is a sample of my hosts.deny file:

```
# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
sshd: 164.41.201.33
sshd: 200.17.53.17
sshd: 193.173.116.194
sshd: 70.32.114.51
sshd: 210.176.26.185
sshd: 202.115.129.8
sshd: 220.227.218.21
sshd: 218.75.172.173
sshd: 200.91.25.233
sshd: 81.196.180.110
sshd: 88.42.172.243
sshd: 59.188.10.20
sshd: 220.231.81.140
sshd: 67.111.251.100
sshd: 82.204.181.164
sshd: 202.71.199.175
sshd: 218.19.140.21
sshd: 196.15.140.145
sshd: 216.107.234.167
sshd: 203.112.151.49
sshd: 210.187.55.30
sshd: 122.224.131.105
sshd: 67.41.255.150
sshd: 79.99.42.78
sshd: 200.111.157.66
sshd: 211.253.236.157
```

Jim

---

