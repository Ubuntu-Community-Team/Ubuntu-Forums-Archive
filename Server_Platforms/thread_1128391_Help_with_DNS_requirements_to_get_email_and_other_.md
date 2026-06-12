---
title: "Help with DNS requirements to get email and other services running on my domain."
date: 2009-04-17
forum: Server Platforms
---

### Post by poundjd on 2009-04-17
Hello all and thanks for your help,

     I have my domain - "mydomain.us",  I want my email server (ebox on Ubuntu) to send and recieve mail sent to "*anyuser*@mydomain.us"

     I want my eBox (Ubuntu 8.04) server to be my Gateway system at home and for the systems in my home to have the domain "home.mydomain.us", with ebox being the only exposed IP and serving as the DNS relay for internal systems.  I want the ebox server will have the FDN of "ebox.home.mydomain.us".  My major problem is that the "home.mydomain.us" does not exist in the public DNS space. 

My external IP is Provided via DHCP and has changed several times this last month.... go figure, so I'll be needing a Dynamic DNS program to update the records at the public DNS servers, as well as the reverse lookup record for my server, other wise many mail servers will not accept mail from my mail server.

What do I have to have the domain registrar enter into the public DNS space?
     I think that I'll need 4 records entered, SOA for "home.mydomain.us", PTR and A record for "ebox.home.mydomain.us" and a MX record to have all mail for "mydomain.us" sent to "ebox.home.mydomain.us".  Or should the ebox server be "mail.mydomain.us" and also have an alias of "ebox.home.mydomain.us"

Or is there some better way with a virtual domain.   
Is this sufficient? Am I totally off base here?  Help and advice requested....
HOWTO's really appreciated.
-jeff

---

### Post by HermanAB on 2009-04-17
If you want to run a mail server, then  you have to get a static IP address from your ISP.  That means signing up for a 'small business server account', which typically costs about $10 a month more than a home user account.

---

### Post by poundjd on 2009-04-20
> **HermanAB said:**
> If you want to run a mail server, then  you have to get a static IP address from your ISP.  That means signing up for a 'small business server account', which typically costs about $10 a month more than a home user account.

Herman,
   Thanks for the time you took to answer, but WHY do you think a static IP address is required to run a mail server? Does this have to do with some of the new mail sender verification systems? 

     I have heard of ton's of people doing it every day on systems with dynamic IP.  Using any one of a number of Dynamic DNS programs to update the DNS cloud with the current IP of the mail server.  Do you know something that I need to know?
-jeff

---

### Post by Dublee on 2009-04-21
Although a static IP address is not required, it is preferred for a number of reasons.  Dynamic IP addresses will work if used in conjunction with a dynamic DNS service, however, if your IP address changes, your previous IP address my still be cached on the sending mail server's DNS servers.  When this happens, 1) incoming email to you may bounce if another mail server is now using your previous IP address, 2) the sending mail server will queue the email until its DNS record updates with your new IP address, or 3) if the email in the sender's queue times out sooner than the DNS record updates, then the email will bounce stating your mail server is unreachable.

Another reason why dynamic IP addresses are not preferred is that many mail servers reject email coming from the dynamic IP address space.  This is because a majority of SPAM originate from infected home systems behind cheaper dynamic IP Internet service.

If you find that your emails are being rejected because it's originating from a dynamic IP address, you can subscribe to a relay service such as DynDNS Mailhop Outbound ([http://www.dyndns.com/services/mailhop/outbound.html](http://www.dyndns.com/services/mailhop/outbound.html)).

---

### Post by Wayne_V on 2009-04-21
Try entering your IP address here:

[http://www.mxtoolbox.com/blacklists.aspx](http://www.mxtoolbox.com/blacklists.aspx)

Remember that unless reverse dns of your IP points backup to mydomain.us a lot of mail hosts will reject you.

---

### Post by BkkBonanza on 2009-04-22
Also a lot of mail servers now like to find an SPF record at your dns. It's easy to set up and tells them which ip/domain is authorized to send may for your domain.

---

