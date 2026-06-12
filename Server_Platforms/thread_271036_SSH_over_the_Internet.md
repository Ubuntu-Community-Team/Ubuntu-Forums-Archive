---
title: "SSH over the Internet"
date: 2006-10-04
forum: Server Platforms
---

### Post by den_elze on 2006-10-04
Hi,

I installed openssh on my ubuntu 6.06 server @ home. This server is connected behind my router, just like 2 other machines. (winxp and ubuntu 6.06)

I configured my router to forward my public ip address on port 2222 to my private ip address 192.168.100.2 on port 22. This is because my provider (Telenet Belgium) blocks ports lower then 1024.

When I do ssh (public address) -p 2222 on my private domain, it works great. But when I do the same from any other location, for example from my pc @ work, I always gets a timeout.

I do not have a dns name, and my public ip address is not static, but this doesn't really make a difference does it.

Can someone give me some ideas what to check next?

Thx a lot

---

### Post by murraymints on 2006-10-04
if your ip address is not static then it is probably changing between when you last looked and when you try to access it (if your cannection has an idle time-out then your ip address will change very regulary).

I heard of a great website yesterday call [www.dyndns.org](www.dyndns.org) which will let you assiang a domain name such as example.dyndns.org for your ubuntu server. Try giving it a go.

---

### Post by den_elze on 2006-10-04
mno the IP hasn't changed yet. But I will take a look at that website

---

### Post by doogy2004 on 2006-10-04
I usea no-ip for my dynamic dns.  it has an easy to install update client that runs right from your server at an interval that you can choose.

---

### Post by inthewayboy on 2006-10-04
Sounds like you are forwarding 2222 to 192.168.100.2:22, yet you say you connect internally to port 2222. Makes me think that the ssh server is setup to listen on 2222, which means you would want to forward 2222 to 192.168.100.2:2222. Unless it way a typo...

---

### Post by doogy2004 on 2006-10-04
> **inthewayboy said:**
> Sounds like you are forwarding 2222 to 192.168.100.2:22, yet you say you connect internally to port 2222. Makes me think that the ssh server is setup to listen on 2222, which means you would want to forward 2222 to 192.168.100.2:2222. Unless it way a typo...

Thats true, because I test my external connections as follows:

let the server = 192.168.1.100
let the port = 22

let dynamic dns address = home.dynamic.com

1 connect via 192.168.1.100:22
2 configure my router to forward the correct port
3 connect via home.dynamic.com:22

if that connects that is a good indication that everything is working.

---

### Post by den_elze on 2006-10-05
thx a lot for all the replies! (I learned a lot from them)

I was able to fix the problem by changing the port in the sshd_config file.

---

