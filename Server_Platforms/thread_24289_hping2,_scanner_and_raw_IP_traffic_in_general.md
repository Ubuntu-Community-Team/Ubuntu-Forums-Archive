---
title: "hping2, scanner and raw IP traffic in general"
date: 2005-04-06
forum: Server Platforms
---

### Post by tomdeb on 2005-04-06
hi,

I get an error :

```
[send_ip] sendto: Operation not permitted
``` 

each time I am using an application that sends raw IP traffic, such as nmap or hping2

I am obviously sudo-ing the command but i still get the same error.

any idea or suggestion would be great.

Thanks

Tom

---

### Post by GoblinCity on 2006-05-31
Hi, I am having the same problem with hping2. I can send SYN and ACK packets OK, but not RST, SYN/ACK or FIN packets. (I have no problems with nessus, nmap or Ethereal)

Same error message: [send_ip] sendto:operation not permitted

even when sudoing and even when manually logged in as root.

Can anyone explain why this is happening? Do I need to change permissons on something?

I am running Breezy Badger

Thanks

Goblin Queen

---

### Post by GoblinCity on 2006-05-31
Solved it - my firewall (Firestarter) was blocking the packets (and so it should!) Suspend the firewall and they get through fine.

Goblin Queen

---

