---
title: "General Security (VPN + Mail Server)"
date: 2011-06-07
forum: Security
---

### Post by ikartz on 2011-06-07
Hi, first of all hello and thanks, I'm a old-new user I always wandered around here and always found answer to all just by reading others posts.


I have an email Server at my home and I would like to implement a VPN server in the same server, but I wanted to know at what poing I'm protected since I hold the ubuntu server 10.04 server installed with normal config (haven't changed more than ssh config)


[SIZE=3]**My 'Problem'**[/SIZE]
    Since I'm 90% of my time using wireless and I exchange info with my server (projects) and with my friends-projects I wanted to create a way that me and my friends could encrypt/secure our data as it leaves our laptops.


[SIZE=3]**What's my plan:**[/SIZE]
    Creating a VPN server (which would be laptop <> home-server) and send email (which is in the same server, and the recipient is there too), so the info never leaves that server, but I want to know if that leads my server compromised and what can I do to secure it.

..I want to be sure of being secure.



**PS:** right now I'm searching for articles in google but I wanted advice from wiser and experienced people than me. If someones know about any other secure 

way of changing ideas with my friends-project I would be extra thankfull.

---

### Post by ikartz on 2011-06-08
74 views and no reply, well thanks anyway =|

---

### Post by Lexus45 on 2011-06-09
> **ikartz said:**
> 
[SIZE=3]**What's my plan:**[/SIZE]
    Creating a VPN server (which would be laptop <> home-server) and send email (which is in the same server, and the recipient is there too), so the info never leaves that server, but I want to know if that leads my server compromised and what can I do to secure it.

..I want to be sure of being secure.


Hello.

I'm not a security expert, though I want to say that's there's no absolute securty.

But you may use OpenVPN as a tool for creating a VPN between yourself, your friends and a server, which all of you will use.

Yoy may even not configure SMTP-auth on your mail-server, if you and your people will send mail only via VPN-connection, and the mail server will be a member of that VPN.
Say, your VPN uses 10.1.1.0/24 network. Your PC receives 10.1.1.5 after activating the connection with the VPN-server, your friends receive 10.1.1.6, 10.1.1.7, 10.1.1.8. The mail server will be 10.1.1.4. And you'll have to allow sending mail through it only from your 10.1.1.0/24 network. And configure it to listen on the VPN-interface, for OpenVPN it'll be named as tun0 or tap0, depending on either you use TCP or UDP tunneling.

Something like this...

---

### Post by ikartz on 2011-06-12
> **Lexus45 said:**
> Hello.

I'm not a security expert, though I want to say that's there's no absolute securty.

But you may use OpenVPN as a tool for creating a VPN between yourself, your friends and a server, which all of you will use.

Yoy may even not configure SMTP-auth on your mail-server, if you and your people will send mail only via VPN-connection, and the mail server will be a member of that VPN.
Say, your VPN uses 10.1.1.0/24 network. Your PC receives 10.1.1.5 after activating the connection with the VPN-server, your friends receive 10.1.1.6, 10.1.1.7, 10.1.1.8. The mail server will be 10.1.1.4. And you'll have to allow sending mail through it only from your 10.1.1.0/24 network. And configure it to listen on the VPN-interface, for OpenVPN it'll be named as tun0 or tap0, depending on either you use TCP or UDP tunneling.

Something like this...

thank you for the reply,
best regards,
Ikartz =)

---

