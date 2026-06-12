---
title: "Apache Virtual Servers"
date: 2010-04-29
forum: Server Platforms
---

### Post by jaymattlin on 2010-04-29
I apologize if this is in the wrong place but I wasn't sure where to really post this.

I am currently running Ubuntu Server 9.10 and have installed the needed apps to run a web server. I am using Webmin to administer my sites.

I have setup all of my sites in DNS Bind and added Virtual Hosts in Apache.

When I redirect all HTTP traffic to the Ubuntu box, all traffic is pointed to one domain and not to the domains they are intended for.

For example:

I have jaymattlin.me setup.
I also have nanasheroes.org setup.

If I redirect traffic on port 80 to the Linux box, the only site that will open is jaymattlin.me. If I type in nanasheroes.org, I get to jaymattlin.me.

Does this make sense? Any help would be appreciated.

Thanks.

---

### Post by gyzer on 2010-04-29
I've had the same problem, and I wasn't able to fix it. I just created a virtual interface to separate the sites out in apache, thats been working fine for me.

---

### Post by jaymattlin on 2010-04-29
I'm not sure how to do that. Do you have any instructions? Or someplace to find a how-to?

I'm pretty good with Windows but I want to be able to do Joomla on my sites and this is the only thing standing in my way right now.

---

### Post by cdenley on 2010-04-29
Why are you redirecting? What are you redirecting to? If you redirect to your IP address, then your web server won't be given a hostname to match to your site, and the default site will be served. You need your domains to resolve to your server's IP, not redirect.

---

### Post by jaymattlin on 2010-04-29
I'm currently hosting several websites on a Windows Server 2003 machine. 

It is running IIS and doing all of the DNS and routing of the Internet for my network.

In Routing and Remote Access, instead of having HTTP port 80 pointing to my Windows Server for IIS to pickup the sites, I will be redirecting port 80 to the Ubuntu box.

Once I port all port 80 traffic to the Ubuntu box, only the website contained in /var/www is displaying.

---

### Post by cdenley on 2010-04-29
> **jaymattlin said:**
> In Routing and Remote Access, instead of having HTTP port 80 pointing to my Windows Server for IIS to pickup the sites, I will be **redirecting** port 80 to the Ubuntu box.

Once I **port** all port 80 traffic to the Ubuntu box, only the website contained in /var/www is displaying.

By "redirect" and "port", do you mean route?

---

### Post by jaymattlin on 2010-04-29
> **cdenley said:**
> By "redirect" and "port", do you mean route?

Yes. Sorry. Route.

---

