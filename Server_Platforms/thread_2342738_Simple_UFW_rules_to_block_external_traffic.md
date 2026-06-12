---
title: "Simple UFW rules to block external traffic"
date: 2016-11-09
forum: Server Platforms
---

### Post by aeronutt on 2016-11-09
Note I'm a ufw / iptables rookie.
I've done some simple testing and so far, I think I have a set of simple rules to block/allow my local file server from external addresses, and allow local access.

after enabling ufw:
for local access, apply the following rule
```
sudo ufw allow from 192.168.0.100/24
```

Then, use the following to turn off and on access to external connections via allow/deny ethernet port:

deny internet access
```
sudo ufw deny in on enp2s0
sudo ufw deny out on enp2s0

```

allow internet access
```
sudo ufw allow in on enp2s0
sudo ufw allow out on enp2s0
```


This allows me to write a simple script to allow/deny external access.

I was a bit surprised, but happy, that the "allow from <ip address>" seems to create an exception to the "deny ethernet" command.
Does order matter?

Thoughts?

---

### Post by darkod on 2016-11-09
Probably a redundant question: Is the server connected directly to the internet with a public IP?

---

### Post by aeronutt on 2016-11-09
Nope, it's attached to a home router. And the server IP is a private one (192.168.xxx)

---

### Post by aeronutt on 2016-11-09
Ok, with the above rules, I can sftp to the server (from local client), but can't ftp. 
I added "sudo ufw allow ftp", but still can't ftp from client.
Current ufw rules on server look like:

```
[ 1] Anywhere                   ALLOW IN    192.168.0.0/24            
[ 2] Anywhere on enp2s0         DENY IN     Anywhere                  
[ 3] Anywhere                   DENY OUT    Anywhere on enp2s0         (out)
[ 4] 21/tcp                     ALLOW IN    Anywhere                  
[ 5] Anywhere (v6) on enp2s0    DENY IN     Anywhere (v6)             
[ 6] Anywhere (v6)              DENY OUT    Anywhere (v6) on enp2s0    (out)
[ 7] 21/tcp (v6)                ALLOW IN    Anywhere (v6)          
```

---

### Post by darkod on 2016-11-09
Then there is no external traffic on it. Disable ufw and don't worry about it.

Your home router has a firewall, and no one can access your server on a private IP over the internet. Which external traffic you are referring to?

The only way traffic goes directly to your server on a private LAN, is if you have some ports forwarded on the router to it. But in such case you are doing it for a purpose, and blocking those ports with a firewall on the server beats the point.

---

