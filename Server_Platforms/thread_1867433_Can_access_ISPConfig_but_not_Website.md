---
title: "Can access ISPConfig but not Website??"
date: 2011-10-22
forum: Server Platforms
---

### Post by Gladhus on 2011-10-22
Helle everyone!

I am kind of new to Ubuntu Server and I have followed the "Perfect Server" Tutorial to set up a Ubuntu Server 11.10 and everything seemed to work as I wanted, so I setted up everything from my LAN and everything is working, I can access everything...

So I try to access my ISPConfig login page ( [public IP]:8080 )  externally and everything works, I try to connect by sftp and everything works... Now I try to access my web page (at my public IP without any precised port) and I can't access it. I just can't figure out what won't work... Is it because of ISPConfig 3? ...

I repeat that on my LAN, everything works fine, I can access the web page correctly...

---

### Post by volkswagner on 2011-10-22
Does your site work on LAN?

Likely port 80 is blocked by your ISP, a firewall is blocking, or it is not opened correctly on the Router.

To see if port 80 is the issue go to canyouseeme.org (from a PC browser on your LAN) and check port 80.  It will tell you if it is blocked.  If you are confident no firewall and router setting is correct, you likely have port 80 blocked by isp.

---

### Post by Gladhus on 2011-10-22
I have forwarded the port on my router and have desactivated the firewall of Ubuntu Server... The webpage does work on my LAN. 

How do I make sure ISP isn't blocking port 80 and if it is, how do I unblock it?

---

### Post by volkswagner on 2011-10-23
You can call them, but I think the steps in my first response are adequate. 


You may need a commercial/business plan or some sort of upgrade.  Most residential plans have an agreement which forbid you from running services such as web server/mail server from a residential line.  This is the reason for the isp blocking such ports.

So you can run Apache2 on an alternate port, or call your isp for a solution.

---

