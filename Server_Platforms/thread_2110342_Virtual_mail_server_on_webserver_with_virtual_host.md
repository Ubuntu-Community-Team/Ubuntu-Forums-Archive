---
title: "Virtual mail server on webserver with virtual hosts."
date: 2013-01-30
forum: Server Platforms
---

### Post by lourendo on 2013-01-30
Hello all!  I am fairly new to Ubuntu.  I am tired of paying for web hosting so i decided to configure my old poweredge to be my own webserver.  I currently have 2 sites running on it and all was fairly straightforward and simple.  I now would like to configure my device so that i can send and receive site specific emails with roundcube or something similar.  I plan on adding more virtual hosts in the near future so the solution would need to be able to support this.

What is the easiest way I can accomplish this?  I am running 12.04.1 server.  I am not too well versed in ubuntu command prompts so if anyone can point me to a detailed tutorial that would be great.   

I  am really trying to learn this and  i appreciate your help.  Thank you, Louis

---

### Post by volkswagner on 2013-01-30
In reality you are still paying for hosting.  I'm sure that PowerEdge gobbles electric, plus your internet connection is not free. :)

The easiest setup for mail server with multiple domains may just be Citadel.  It includes a web frontend for management and webmail.

You will likely run into issues if you have a dynamic ip address, as many hosts will block incoming mail from dynamic ip's.  Even if you ip does not change, it is listed as dynamic.  This can be worked around by using a relay host such as your isp.

Running the server from home is good for testing and development, but for uptime, reverse DNS, static ip, etc. you will be much happier with an inexpensive VPS provider.  There are providers offering decent sized VPS's for under $10 per month.

---

### Post by SeijiSensei on 2013-01-30
Residential connections often have terms of service which prohibit servers.  You may find that inbound SMTP is blocked.  ISPs often also block outbound SMTP by residential users to keep spambots from blasting out mail.  

I second volkswagner's suggestion of using a VM provider.  I am a very happy [Linode]("http://www.linode.com/") customer, though their basic machine costs $20/month, not $10.  In return you get excellent technical support, essentially unlimited bandwidth, and big honking generators that will keep your services up all the time.  (One of my VMs is in Linode's Newark facility; I saw nary a blip in service during hurricane Sandy.)

---

