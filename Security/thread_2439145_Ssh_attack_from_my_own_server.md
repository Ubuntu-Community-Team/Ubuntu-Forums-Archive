---
title: "Ssh attack from my own server"
date: 2020-03-23
forum: Security
---

### Post by nathan042 on 2020-03-23
Hi everyone,
I'm sorry if a similar post already exists, i can't find it.

I've just recieved a mail from OVH because someone complain about my personal VPS :

> IP is continually attempting to hack ssh passwords on a server of mine. It is being done to such an extent that it should be caught by your internal detection system. Please disable whatever you have using that IP. The IP is reported as abusive on multiple sites and is considered malicious with 100% confidence. Please disable it immediately

They send me this log :
> Mar 23 16:17:43 server sshd[29480]: Invalid user kirinuki from XX.XXX.XX.XX
Mar 23 16:17:43 server sshd[29480]: Failed password for invalid user kirinuki from XX.XXX.XX.XX port 49984 ssh2  
Mar 23 16:17:43 server sshd[29480]: Received disconnect from XX.XXX.XX.XX port 49984:11: Bye Bye [preauth]  
Mar 23 16:17:43 server sshd[29480]: Disconnected from XX.XXX.XX.XX port 49984 [preauth]  

I don't know what to do. I checked a lot of things, i've installed clamscan and rkhunter, but i dont know what i'm looking for...

Thanks in advance!

---

### Post by EuclideanCoffee on 2020-03-23
You must act quickly. Turn off your server.

When you've done so, I can provide next steps. I recommend hiring someone to assist you today. I don't provide services from this account, so I won't give you explicit details on to solve your problem.

Repeat, please seek professional help _today_.

---

### Post by nathan042 on 2020-03-23
Thanks for your answer!
I finally have found a solution here : [https://askubuntu.com/questions/1115770/crond64-tsm-virus-in-ubuntu?newreg=fb490b98fc694c90b9fac73b1332ff08](https://askubuntu.com/questions/1115770/crond64-tsm-virus-in-ubuntu?newreg=fb490b98fc694c90b9fac73b1332ff08)

The virus used the user "gogs" so maybe there is an old breach in this service. For now i've disabled this service and block outgoing requests on 22. I'll check for the next days if there is suspicious activities on the server.

I dont use this server for profesional activities so i will not hire somebody. But thanks for your advices!
Good night

---

### Post by EuclideanCoffee on 2020-03-23
This is on your home NAT? That's troubling. Close up your router while working on this. Thanks.

---

### Post by CharlesA on 2020-03-25
> **EuclideanCoffee said:**
> This is on your home NAT? That's troubling. Close up your router while working on this. Thanks.

Nah, it looks like it's a hosted box since they mentioned VPS and OVH, which is a hosting company.

> **nathan042 said:**
> Thanks for your answer!
I finally have found a solution here : [https://askubuntu.com/questions/1115770/crond64-tsm-virus-in-ubuntu?newreg=fb490b98fc694c90b9fac73b1332ff08](https://askubuntu.com/questions/1115770/crond64-tsm-virus-in-ubuntu?newreg=fb490b98fc694c90b9fac73b1332ff08)

The virus used the user "gogs" so maybe there is an old breach in this service. For now i've disabled this service and block outgoing requests on 22. I'll check for the next days if there is suspicious activities on the server.

I dont use this server for profesional activities so i will not hire somebody. But thanks for your advices!
Good night

Honestly, once a machine is compromised it's usually best to nuke it and reinstall from backups since you don't know what was done to it after it was compromised.

Blocking outgoing traffic is only a stop-gap at best.

---

### Post by nathan042 on 2020-03-26
I don't wanted to do it but i think you'r right. I'm going to nuke

Thanks guys!

---

