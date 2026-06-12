---
title: "Dns Issues Very Very Strange!!"
date: 2008-05-20
forum: Server Platforms
---

### Post by ade234uk on 2008-05-20
I set the nameservers for a domain name about 5 days and everything propogated as it should do. I have been viewing the site for 4 days.

Tonight I accessed the site, and suddenly I was back at the registrar holding page. What the *** I thought.

I pinged the domain name and it gave me the IP address of the registrar.

I phoned up a couple of people and they where still seeing the site and I was not. 

I asked one of them to flushdns and then ping the domain name and they got the site ok.

I walked away for about 10mins and came back. I pinged the domain name again and it was back on the correct IP. I visited the site and everything seems to back to normal.

Has anyone ever seen this before?

---

### Post by HermanAB on 2008-05-20
Your system is pointing to a bad DNS.  You can change it in /etc/resolv.conf.

Cheers,

Herman

---

### Post by MJN on 2008-05-20
Without knowing the domain name it is impossible to say whether the issue is down to bad DNS configuration or a problem at your end. Of course now that it appears to be fixed we'll probably never know!

Mathew

---

