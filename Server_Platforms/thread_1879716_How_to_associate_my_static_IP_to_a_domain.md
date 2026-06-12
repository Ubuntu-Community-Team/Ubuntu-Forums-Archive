---
title: "How to associate my static IP to a domain"
date: 2011-11-12
forum: Server Platforms
---

### Post by aliov_85 on 2011-11-12
I want to host my site on my server. I've already registered the domain. Also I've an static IP and enabled port forwarding for the Web. So my website is reachable through the IP address. How to do so that instead of entering the IP, the user enters the domain name.

Sorry in advance if this is a stupid question as this is my first experience on publishing a website.

Regards

---

### Post by boetzie on 2011-11-12
You have to configure your dns server. This must be done through the dns server of your domain register. hopefully this helps.

---

### Post by aliov_85 on 2011-11-12
Thank you for your reply. So I went to the domain panel, dns settings. In the first line (green brush) I replaced the initial IP address with my IP address. This how I should do it? How much should I wait this to take effect?

[IMG]http://oi41.tinypic.com/2wfogid.jpg[/IMG]

Regards

---

### Post by Jonathan L on 2011-11-12
> **aliov_85 said:**
> I want to host my site on my server. I've already registered the domain. Also I've an static IP and enabled port forwarding for the Web. So my website is reachable through the IP address. How to do so that instead of entering the IP, the user enters the domain name.

Sorry in advance if this is a stupid question as this is my first experience on publishing a website.

Regards

Hi Aliov

You need to add a record which looks like this (but with your IP address):
```
www A 1.2.3.4
```It typically takes 5 minutes with a lot of modern domain hosting firms; sometimes it takes place in seconds, sometimes it can take hours.

You test your DNS entries by looking on any DNS lookup page on the web ([http://www.mxtoolbox.com/DNSLookup.aspx](http://www.mxtoolbox.com/DNSLookup.aspx) is one of many).  Or alternatively from your command line you can check it at one of Google's DNS servers:
```
dig @8.8.8.8 www.yourdomain.com a
```Hope that helps.

Kind regards,
Jonathan.

---

