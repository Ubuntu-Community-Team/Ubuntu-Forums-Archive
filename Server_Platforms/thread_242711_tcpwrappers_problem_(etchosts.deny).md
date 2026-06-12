---
title: "tcpwrappers problem (/etc/hosts.deny)"
date: 2006-08-24
forum: Server Platforms
---

### Post by nodrog on 2006-08-24
I am having a problem getting tcpwrappers to work.  Below is what I have in my /etc/hosts.deny file.  I am wanting to block all services from these IPs and IP blocks.  

Does it look like I left something out, did something wrong or is there a service that needs to be started first?

Any help would be appriciated.

Thanks
Nodrog


#
# Below are specific IPs
#
ALL: 206.61.165.140
ALL: 170.40.160.35
ALL: 216.212.110.194
ALL: 147.182.5.50
ALL: 205.142.237.129
ALL: 147.202.14.38
ALL: 65.16.93.171


#
# Below here are entire networks
#
ALL: 218.154.193.
ALL: 212.147.103.
ALL: 217.80.
ALL: 218.90.
ALL: 218.91.
ALL: 218.92.
ALL: 125.240.
ALL: 125.241.
ALL: 125.242.
ALL: 125.243.
ALL: 125.244.
ALL: 125.245.
ALL: 125.246.
ALL: 125.247.
ALL: 85.184.
ALL: 83.16.149.
ALL: 222.184.
ALL: 222.185.
ALL: 222.186.
ALL: 222.187.
ALL: 222.188.
ALL: 222.189.
ALL: 222.190.
ALL: 222.191.
ALL: 195.162.206.
ALL: 203.81.

---

### Post by anindya_m on 2006-08-24
What is the problem exactly? Some hosts can connect despite an entry in hosts.deny or some such thing?

---

### Post by anindya_m on 2006-08-24
sorry posted twice due to network problem.

---

