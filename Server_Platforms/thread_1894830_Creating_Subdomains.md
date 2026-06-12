---
title: "Creating Subdomains"
date: 2011-12-13
forum: Server Platforms
---

### Post by anuvnu387 on 2011-12-13
Hello all,

I have a Ubuntu 10.04 server running several websites. I would like to combine them into one domain under different subdomains. Here is my situation:

Domain Registrar: Godaddy
DNS Management: Zoneedit (since I have a dynamic IP)
Apache Server running on a non-standard port (ISP blocks 80)

How do I create subdomains? 

1. I see I can create subdomains on Godaddy (I think they are subdomain forwards). 
2. I believe I can create subdomains on Zoneedit.
3. I believe I can create subdomains (virtualhosts?) on Apache.

But I am clueless where to start or whichone to use. Any help/advise will be greatly appreciated. If you need further information please let me know. 

Thanks,

---

### Post by djmikepic on 2011-12-13
Hi,

A subdomain is nothing more than individual hostnames under the primary, but you will need static IPs in order to correlate any domain to specific IP's. You can create multiple A records with weight/cost routes, but you still need to be able to predict which IPs you'll be using. But anyway, here is the procedure for A records:

1) log into your Godaddy Account
2) Under My-Domains, click your primary domain
3) Locate and click on DNS Manager
4) Click Edit Zone
5) You will add each record under the first table (A HOST)

Just click on quick-add and input your information in the fields (first field is for hostname and second field is for the IP address. 

For example if your subdomain is server.godaddy.com, then you will enter **server **in first field, and the IP address in second. 

Also, you will need to add the hostname to your server under /etc/hosts. For example

-------------------------------------
# sudo vi /etc/hosts

127.0.0.1 localhost
50.73.x.x server server.godaddy.com
-------------------------------------

In the example above, your hostname "server" will correlate to new subdomain server.vert-serve.com

Hope that helps,
Cheers

---

