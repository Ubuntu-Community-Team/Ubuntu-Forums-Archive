---
title: "Mail Server - cannot receive emails from other domains"
date: 2007-05-02
forum: Server Platforms
---

### Post by earth_walker on 2007-05-02
Hi all,

I have set up an email server, lets call it myserver.com, using [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/). Basically this is a postfix/IMAP/courier/MYSQL/SASL setup. Everything seems to be working ok, and I have remote access working by pop3, imap and squirrelmail. However:

[email]me@myserver.com[/email] can send emails to [email]you@myserver.com[/email]
[email]me@myserver.com[/email] can send emails to everyone else (e.g. [email]you@hotmail.com[/email])
BUT
everyone else (e.g. [email]you@hotmail.com[/email]) cannot send emails to [email]me@myserver.com[/email]

Nothing is recorded in any of the logs, just a server not responding message returned about a day later. I am using our ISP's (bellnet.ca) SMTP for sending emails. 

I have checked the MX records, and they are pointing fine. I can telnet to myserver.com 25 from anywhere on our LAN, so I know it is listening. I cannot telnet to port 25 from home, but I know for sure my home ISP blocks all outgoing port 25 requests, so I don't think that tells me anything.

I have tried several of the mail testing websites, which report that the MX records are correct but the server is not responding.

Since this is a receipt issue rather than a sending issue, could this still be a port 25 blocking problem? I thought that was supposed to stop me from relaying spam, rather than stop me from receiving email!

How can I troubleshoot this? Thanks in advance for any help, hints, troubleshooting tips.

(Edit: I also want to add that my hardware firewall is open and allowing port 25 TCP through. Software firewall is off while I'm testing)

---

### Post by rickyjones on 2007-05-02
If you run dnsreport.com on your domain and it shows the MX record pointing to your IP address, but then displays that it cannot connect to your IP, then that generally means that some sort of port blocking is going on.

Could you post your domain name for testing purposes? Have you tried telneting to port 25 on your domain from another computer on the internet?

Hope that points you in the right direction.

-Richard

---

### Post by earth_walker on 2007-05-03
> **rickyjones said:**
> If you run dnsreport.com on your domain and it shows the MX record pointing to your IP address, but then displays that it cannot connect to your IP, then that generally means that some sort of port blocking is going on.

Could you post your domain name for testing purposes? Have you tried telneting to port 25 on your domain from another computer on the internet?

Hope that points you in the right direction.

-Richard

Yes in both cases with no connection. It looks like it's port blocking. I'll call my isp and see if they will play nice with us, but is there any way to use another port (like 26, for example?). 

The domain is ugmengineering.com.

Thanks, Richard

---

### Post by MrHorus on 2007-05-05
> **earth_walker said:**
> Yes in both cases with no connection. It looks like it's port blocking. I'll call my isp and see if they will play nice with us, but is there any way to use another port (like 26, for example?). 


No because then every other mailserver that might want to connect to you to relay some mail would need to know that you were on port 26 :(

---

### Post by MJN on 2007-05-08
If absolutely necessary you could use a non-standard port and a so-called 'mail reflector' service. These services usually cost (e.g. a quick search points to no-ip.com offering it at $40/yr) and involve them accepting all of your mail and then relaying it on to your mail server running on the non-standard port.
 
Ask your ISP though, I've read at least one post on here from someone who just had to ask for the port to be opened - it was closed by default but could be opened in response to certain conditions being agreed to.
 
Mathew

---

### Post by earth_walker on 2007-05-10
Just a follow-up for everyone. 

I did call my ISP (Bell Canada), and their technician refused to admit that it was even possible to unblock the port, insisting that this was a hardware limitation because of the router included in our service plan, and that the only way around it was to upgrade our service to their premium DSL (for an EXTRA $60 per month plus taxes). 

He went on to say that even if there was a way to get around the router hardware limitation, our IP address wouldn't allow an email server to work, and by the way reflector services would not work either. 

When I suggested that perhaps another ISP may let us use the full internet connection we are paying for without such restrictions, he said that if I changed ISPs the only way I could have a mail server running would be to go for a 5 Meg premium plan similar to the one he was trying to upgrade me to.

So I told him he was wrong, hung up, and went with the $30/year option of using a reflector  service and everything is hunky-dory now. The search is on for a better ISP. Any canadian recommendations would be appreciated!

---

