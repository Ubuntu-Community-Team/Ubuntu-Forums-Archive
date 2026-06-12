---
title: "configuring my droplet’s DNS"
date: 2014-04-27
forum: Server Platforms
---

### Post by Drone4four on 2014-04-27
I purchased my Domain Name from NameCheap a while ago. I installed LAMP on my freshly created Digital Ocean droplet.  The ip is accessible in my web browser.  I’m now trying to configure my DNS for the droplet.  I am following a guide called, [How To Set Up a Host Name with DigitalOcean]("https://www.digitalocean.com/community/articles/how-to-set-up-a-host-name-with-digitalocean").

By default in my control panel, there is an A record which indicates ‘@’ and is associated with the ip 162.243.112.67.   What is that address pointing to?  It fails to load in my browser and doesn’t respond when I ping it from a console.  My droplet’s ip is completely different.  I associated my droplet ip as an A record too, along with my domain name that I registered with NameCheap some time ago.  The most important question here that I’d like to know is: Is it safe for me to remove the default ‘@’ ‘162.243.112.67’ A record? 

I pointed my name servers to the ones given to me by NameCheap (produced with my whois command) and filled them in in five NS fields in my DigitalOcean control panel.  Do I have to wait 24-72 hours to discover if what I am doing is right or wrong? 

How do I update my Zone File? Or does it update automatically?

How do I save? The guide says: “Save by clicking Add new A record”.  There is no such button to click.  Is the guide outdated?

I decided to post my questions here on the Ubuntu forums because I think DigitalOcean’s forums are a chaotic madhouse and cluster fsck.

---

### Post by Habitual on 2014-04-28
Seen these:
[http://support.launchrock.co/knowledgebase/articles/36670-namecheap-a-record-instructions](http://support.launchrock.co/knowledgebase/articles/36670-namecheap-a-record-instructions)
[https://www.namecheap.com/support/knowledgebase/article.aspx/319/78/how-can-i-set-up-an-a-address-record-for-my-domain](https://www.namecheap.com/support/knowledgebase/article.aspx/319/78/how-can-i-set-up-an-a-address-record-for-my-domain)

Your A Record should point to the publicly available IP that DigitalOcean has assigned you.

---

