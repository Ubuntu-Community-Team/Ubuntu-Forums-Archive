---
title: "Self Hosting Website and Bind setup worth the trouble?"
date: 2011-11-14
forum: Server Platforms
---

### Post by ptmuldoon on 2011-11-14
I currently subscribe to web hosting via jaguarpc and have a couple of BS websites going for fantasy football, family blog site, and a sub-domain or too.

I have Ubuntu server running 24/7 at home, mainly for file sharing, but do have LAMP already installed and working.  I'm thinking of moving my sites to my home setup and curious to people thoughts on it, and how difficult it may be do set up apache and bind to point to the different websites.

The one good thing I can think of about paying for web services is there backup capabilities, both files and databases.  I do have a RAID 5 setup, but there's always that risk of machine and hardware failure.  And also likely speeds.  Anybody connecting to my home server would likely be restricted to my ISP's upload speeds.

So....... Pro's and Cons on self hosting your website and is it worth the potential savings?

Thanks
PT

---

### Post by lisati on 2011-11-14
I've been running my own publicly accessible LAMP server for about 18 months now. Due to budget constraints, the machine I use is a few years old now, and is not the fastest available. This, together with using a standard domestic ADSL line, can sometimes make web pages slow to load, particularly when there is a need to access a database. 

Apache has a  "virtual hosts" system which can be useful for hosting multiple web sites.

One of the things you might want to read up on is security. Included in the tools I have found useful are fail2ban (configured to help protect both the websites and email) and mod_defensible (help keep out the blog spammers).

The spam filtering setup for the email portion of my setup has, like Topsy, it just "growed". It includes checking a number of DNSBLs, a couple of policy servers (policy-weight or postgrey might be good to check out as part of your standard kit), and some access tables that are populated automatically by a couple of home-grown scripts that analyse my email logs.

---

