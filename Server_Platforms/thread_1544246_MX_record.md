---
title: "MX record"
date: 2010-08-02
forum: Server Platforms
---

### Post by jdesai77 on 2010-08-02
Hi,

I have created a ubuntu server. I have hosted around 50 website on it. Its working good. Initially i had only one IPS and one static ip. Now i have purchased one more isp and one more static ip from isp2. All the domains are using WEB & MAILING services. 

Now when i to make sure that the mails and website for those domains never goes down. I am using thrid party DNS. So in the A records and MX records i have entered the ip address respectively. Now the problem is it will not accept the MX records to be the same.

eg: ISP1 ip ---- mail.domainname.com
    ISP2 ip ---- mail1.domainname.com

Now the user is using mail.domainname.com will not rec. email if the first ISP is down coz the incoming n outgoing is pointing to mail.domainname.com

I have taken 2 ips and planning for a router for auto swithing. What i want now is that my server should never go down ( apart from hardware failure).

Please help me.

Regards,
Jitu

---

### Post by epsolon77 on 2010-08-02
This doesn't sound like it should be an issue with your Ubuntu install.  It sounds like either your DNS and MX records are not setup correctly, or your router is not working.

Can you post the actual MX and A settings for a users domain (with the actual domain name vetted for saftey)  I use [http://zoneedit.com/lookup.html](http://zoneedit.com/lookup.html) to lookup records.

---

