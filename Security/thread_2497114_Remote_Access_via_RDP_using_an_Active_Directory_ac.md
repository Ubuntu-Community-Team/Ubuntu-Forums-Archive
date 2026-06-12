---
title: "Remote Access via RDP using an Active Directory account"
date: 2024-04-23
forum: Security
---

### Post by jtrout2 on 2024-04-23
I have an Ubuntu desktop workstation and I would like it to be remotely accessible over the network via RDP using an AD account. The system is already joined to AD and locally logins are working well. 

I see the sharing option and can successfully access it using RDP; however, it is requiring a unique local account name and password to start the RDP session and it is requiring me to have already logged in to the workstation.

If I try to RDP to the workstation when it is locked my RDP session closes right away. If I try to RDP to the workstation when nobody is logged in the connection is refused.

I've tried to do some searching online to get this set up and have not found any good tutorials and most people are saying to install xrdp. I am trying to avoid any extra software if I can.

Is it possible to get this set up?

Ubuntu version is 22.04 LTS

---

### Post by TheFu on 2024-04-23
RDP has lots of restrictions.  If you are stuck with RDP, someone else will need to help.  I've been in places like that where installing alternate software wasn't allowed.

This is why I use x2go plus it is faster and has better security via ssh and ssh-keys/-certs built-in, but those are different issues.  x2go sessions are separate from local sessions, but there are times that I have to clean up certain programs that only allow 1 instance per userid for their own reasons.  Also, x2go doesn't work with heavy GUIs, so it is best to use XFCE/LXQt/Mate, or some other lite-DE, if you aren't comfortable running with just a WM alone.  Of course, this all doesn't matter if you aren't allowed to install other software on the server or the client. Then you are stuck.

---

### Post by jtrout2 on 2024-05-01
Thanks for the reply. Our security team is trying to minimize additional programs so we won't be able to consider those. 

If I can't get this sorted out otherwise I might be able to push them to consider a 3rd party program; but, with the climate of things I think they would push back wanting to minimize our software footprint.

I'm going to check to x2go so I can become familiar with it.

---

### Post by TheFu on 2024-05-01
If they care about security, then they wouldn't use RDP.

---

