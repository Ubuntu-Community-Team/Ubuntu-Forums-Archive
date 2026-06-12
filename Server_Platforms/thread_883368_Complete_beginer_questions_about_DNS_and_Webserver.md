---
title: "Complete beginer questions about DNS and Webservers"
date: 2008-08-07
forum: Server Platforms
---

### Post by njschwartz on 2008-08-07
In the past I have hosted my website, [www.nateandstephie.com](www.nateandstephie.com), using IIS on Windows server 2003 and 2008.  I decided I wanted to switch to linux mostly just to learn something new.  I used the guides at Zaphu.com to setup my LAMP server.  I own the domain nateandstephie.com which I bought from Godaddy.  I never asked my ISP for a static IP, but in the year I have lived in my current location my IP has never changed so I am going to assume that its static. Prior to that I had a dynamic IP so I used Zonedit for my nameservers and even though my ip appears to be static I am still using zonedits nameservers.  I realize this is a completely noob questions, but I really don't know what I need when it comes to DNS.  Do I need my own DNS running on the network?  I have setup bind9 on the same server that I am running the webserver on, but I don't understand if I even need it.  Basically, I just would like someone to explain to me, if possible, what I need to host my own web and mail servers on my ubuntu box.  Any advice would be greatly appreciated since despite my best efforts I am still failing to understand how it all ties together.  Thanks for the info and you patience with a linux beginner.

---

### Post by windependence on 2008-08-08
Since your domain is registered with Godaddy, you definitley do not need your own DNS servers. they have a compete DNS control panel and you can use their name servers with better results than running your own. In fact, I would say most people just don't need to be running bind9. Why all the tutorials tell you to do this is a mystery to me.

If you get stuck, call Godaddy and have them walk you through setting up your DNS. They are very good at this.

-Tim

---

### Post by njschwartz on 2008-08-08
So you recommend I diable bind and use goddady's DNS servers?  Is that setup then to make a A record with @ pointing to my external IP? And then perhaps and A record with www also pointing to the external IP?  Is there anything else I would need to do on this?  Thanks for the reply btw!! :KS

---

### Post by windependence on 2008-08-08
Yep, you got it. you can go into your control panel and create your A record, MX and whatever else you need right there. It's really nice and like I said, if you get stuck they are very good at helping you.

Although i don't host with them, I really like their domain services.


-Tim

---

