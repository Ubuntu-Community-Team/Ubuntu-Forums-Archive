---
title: "Ubuntu Server VPS Hosting"
date: 2008-08-02
forum: Server Platforms
---

### Post by SuperMike on 2008-08-02
I'm looking for a starter VPS hosting plan that uses Ubuntu, gives me root (or jailed root), SSH, and lets me install stuff with apt-get. I see that Dreamhost doesn't let me have root or to do apt-get, and that kind of defeats the purpose of using a VPS solution.

In the price range, we want to start in the < $500/year USD ballpark but over time we can scale the site, continue reinvestment in the hosting plan, and move up the VPS plan pyramid and into the dedicated server plan pyramid.

Can anyone recommend someone? Heck, even if you want to start a company and offer this service reliably and in the < $500/year USD ballpark plus have graduated VPS plans after that, we'll consider you.

P.S. Here's what's driving this need. I'm a LAMP developer and my client wants me to build a job seeker starter site that we can grow over time. These job posting/search sites unfortunately require powerful and fast search engines. Integrating Google Site Search is not the best option because it only does keyword searches, not searches by geographic proximity, job type, etc. So, I've been advised to consider a F/OSS solution called Sphinx and connect this to my LAMP site. Unfortunately Sphinx is a custom compile, so we'll need to get a VPS solution. And I don't like working on VPS solutions that are CentOS, Fedora, or RedHat based because the repositories are not as thorough as Debian or Ubuntu, stuff isn't as stable as Debian or Ubuntu, and because I prefer apt-get over yum. We looked at webkeepers.com, but they are CentOS based. We looked at Dreamhost, but they won't let you install stuff or have root access, which kind of defeats the whole purpose of using a VPS solution in the first place.

---

### Post by windependence on 2008-08-02
I have been doing this for a while, and just started offerring this from a new server that is about to go online in the next week or two. I can give you your own private VM for that price. We can also offer backup for a small fee.

The environment would be on a quad core server, with dual UPS protection. I run my own commercial sites on this network and have for over 4 years now. Most of my hosting is FreeBSD machines but I can certainly install Ubuntu in whatever flavor you want. You install the software the way you want it.

PM me if you are interested.

-Tim

---

### Post by SuperMike on 2008-08-02
PM sent. Also something that just popped on my radar is a2hosting.com, which now support Ubuntu Server VPS hosting at a fairly affordable rate (as far as VPS rates):

[http://www.a2hosting.com/services/vps-hosting/](http://www.a2hosting.com/services/vps-hosting/)

However, if someone out there is offering lower rates for Ubuntu Server VPS with good uptime, UPS power, planned outages (scheduled maintenance), and more features (especially regarding average and burstable RAM, plus disk space, plus bandwidth), I'm ready to listen.

---

### Post by windependence on 2008-08-03
PMed you back with my number. Give me call Monday if you are interested.

-Tim

---

### Post by Mouth on 2008-08-03
> **SuperMike said:**
> However, if someone out there is offering lower rates for Ubuntu Server VPS with good uptime, UPS power, planned outages (scheduled maintenance), and more features (especially regarding average and burstable RAM, plus disk space, plus bandwidth), I'm ready to listen.

[http://www.krypt.com/vps/index.php](http://www.krypt.com/vps/index.php)

They offer Debian, but may provide Ubuntu if you ask? I've been with them (dedicated server for 2 years, and they are a great provider). I just purchased a new dedicated server and they installed ubuntu hardy server on it for me, hence why I said you could ask about ubuntu for a VPS.

---

### Post by splatmatic on 2008-08-03
> **SuperMike said:**
> PM sent. Also something that just popped on my radar is a2hosting.com, which now support Ubuntu Server VPS hosting at a fairly affordable rate (as far as VPS rates):

[http://www.a2hosting.com/services/vps-hosting/](http://www.a2hosting.com/services/vps-hosting/)

However, if someone out there is offering lower rates for Ubuntu Server VPS with good uptime, UPS power, planned outages (scheduled maintenance), and more features (especially regarding average and burstable RAM, plus disk space, plus bandwidth), I'm ready to listen.

a2Hosting is managed VPS hosting. a2's parent company also runs cheapvps.co.uk (located in both US & UK) and its unmanaged with cheaper plans but same share and memory quotas.

Ive been running the 384MB plan with Centos (using LXadmin as the control panel, only reason why its not ubuntu) from cheapvps for about 3 months now and so far its been great. I haven't noticed any slowdowns (major) or outages yet and my VPS uptime is 43 days. Would have been longer but I rebooting because I wasn't able to access SSH or FTP, but It was just the firewall blocking me since I guessed to many passwords (Do'h for 20+ character passwords!)

---

### Post by SuperMike on 2008-08-03
> **splatmatic said:**
> a2's parent company also runs cheapvps.co.uk (located in both US & UK) and its unmanaged with cheaper plans but same share and memory quotas.

This is fantastic that I bumped into you. This is excellent news because actually my client is in the UK. When I mentioned to him that I was going to recommend a2hosting.com's hosting for his next project, he complained that it wasn't a UK server and therefore might not be the best SEO/PR with Google. I don't understand what that means -- I would have thought that Google wouldn't care whether the server was UK or USA based when it came to PR. But oh well. So then I find from you here that he can get everything we need from a UK host -- that's going to please him. I've sent him an email and I'm awaiting callback.

---

### Post by windependence on 2008-08-04
Hey SuperMike, this is probably the best option for your client. I didn't realize he was in the UK either.

-Tim

---

### Post by jemmille on 2008-08-04
> **splatmatic said:**
> a2Hosting is managed VPS hosting. a2's parent company also runs cheapvps.co.uk (located in both US & UK) and its unmanaged with cheaper plans but same share and memory quotas.



A2 Hosting does not have a parent company, A2 IS the parent company.  We do not run cheapvps.co.uk.  All of our VPS packages are centrally located in the US in our datacenter in Michigan.  If you have any questions please contact our sales department.  [http://support.a2hosting.com](http://support.a2hosting.com)

---

