---
title: "configure Apache to answer for all subdomains requested"
date: 2007-03-27
forum: Server Platforms
---

### Post by patty522 on 2007-03-27
how do i do configure Apache2 to answer for all subdomains requested. as i want to be ble to create sub domains on my server using my main domain name.

---

### Post by Frosty Cold Drink on 2007-03-27
When you set up your VHost block, you can use ServerAlias to add a wildcard.
```
ServerAlias *.domain.tld
```

---

### Post by davidshere on 2007-03-27
Do you want each subdomain to point to a different source folder?  

Do you use webmin?

---

### Post by patty522 on 2007-03-27
> **davidshere said:**
> Do you want each subdomain to point to a different source folder?  

Do you use webmin?

yeas i would like each sub domain to point to different folders eg forum.mydomain.co.uk to point to /var/www/forum

and no i dont use webmin as i was told it was outdated and didnt work with ubuntu anymore

---

### Post by davidshere on 2007-03-27
You'll want this in your /etc/apache2/httpd.conf:

```
<VirtualHost *>
DocumentRoot "/path/to/folder"
ServerName machinename.domainname.com
</VirtualHost>
```

I use webmin with no problems.  Some modules have to manually configured but it's not a big deal.

---

### Post by davidshere on 2007-03-27
With your example:

```
<VirtualHost *>
DocumentRoot "/var/www/forum"
ServerName forum.mydomain.co.uk
</VirtualHost>
```

Remember to restart apache.

---

### Post by patty522 on 2007-03-27
> **davidshere said:**
> You'll want this in your /etc/apache2/httpd.conf:

```
<VirtualHost *>
DocumentRoot "/path/to/folder"
ServerName machinename.domainname.com
</VirtualHost>
```

I use webmin with no problems.  Some modules have to manually configured but it's not a big deal.

cheers i will look into webmin. can you set up virtualhost in that and DNS records?

---

### Post by davidshere on 2007-03-27
Yes, virtualhosts can be setup within webmin's apache module.

I'm not sure what you want to do with DNS.

---

### Post by patty522 on 2007-03-27
dont you need to tell the dns server where the subdomain is pointing to, as i have my own dns server?

mainsite = mydomain.co.uk
subdomain = forum.mydomain.co.uk is just /var/www/forum/
i dont have to buy the subdomain if i own the domain name i can create a record which respons to the subdomain dont i?

---

### Post by davidshere on 2007-03-27
That's not an apache issue.  I've never run a DNS server so I'm not sure how to do it.  

My personal domain is registered through Network Solutions, and they have a control panel where I enter that information.  I used to email my DNS provider every time I wanted a change, but when I realized I could do it myself, I did that instead.

When I want to create a subdomain for our domain here at work, I email our ISP.  They're fast and friendly.

---

