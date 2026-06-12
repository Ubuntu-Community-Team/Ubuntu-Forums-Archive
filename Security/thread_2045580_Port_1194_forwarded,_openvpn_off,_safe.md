---
title: "Port 1194 forwarded, openvpn off, safe?"
date: 2012-08-21
forum: Security
---

### Post by JohnnyQuest69 on 2012-08-21
Hey,

I'm pretty new to ubuntu and Linux in general so please forgive me of I'm asking a foolish question. 

I successfully setup openvpn on my Ubuntu server 12.04.  I have the service turned off for the moment but the port on my wireless router that the server is connected to is still forwarded to the server.  My question is: is this safe or does the service need to be on?

I'm paranoid about security because the second I set up ssh and fail2ban I started getting about 10 bans a week and I'm afraid that in my ignorance, I may inadvertently leave my server open to attack. 


It's just a file server but I'd rather not have it hijacked or otherwise compromised. 

Thanks!

---

### Post by Ms. Daisy on 2012-08-22
You forwarded port 1194 from your router to the server, (if I understand correctly). If you turn off the server, yes the router will still try to forward all incoming traffic on port 1194, but the service won't respond because it's off.  Therefore the connections will time out or be refused. 

If you're concerned about security of your servers, I recommend you read the stickies in the security forum. Those would give you a good start.

---

### Post by JohnnyQuest69 on 2012-08-23
Ok will do. You did understand correctly. I'll read those stickies. Thanks.

---

