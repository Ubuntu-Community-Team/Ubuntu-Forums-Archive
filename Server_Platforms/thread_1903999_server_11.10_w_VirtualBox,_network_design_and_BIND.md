---
title: "server 11.10 w/ VirtualBox, network design and BIND quesitons"
date: 2012-01-03
forum: Server Platforms
---

### Post by MyJimmyWeb on 2012-01-03
Alrighty, first I'll start with what I'm trying to do which is run multiple Ubuntu Server VMs on my VirtualBox host machine.  I want each of the VMs main /www/ folder accessible by it's own subdomain under the host machines main domain.  

I understand you can create virtual servers on the host machine to achieve the same thing without the need for VMs, but I'm running other applications that need their own host.  Anyways, the host machine runs BIND, apache, tomact6, etc.  I have everything set up nicely with the VMs and the shared folders in VirtualBox.  Have installed Webmin on host machine as well as read through the Webmin link on the sticky, although I set up most everything through command line so it doesn't scare me.  The VMs pretty much just run apache, tomcat6, and a couple media servers I use.  

Where I'm stuck is getting the subdomains /www/ folder accessible via hostx.example.com  Is this even possible via dyndns?  Is it possible for dyndns to route example.com to my public ip, then have queries for the appropriate subdomains handled by the host machines DNS server?

 I currently have port xxxx external routed to port 80 internal ip of my host server.  I know this isn't at all the preffered setup, but need to get this working on my residential account completely smooth before purchasing a business account for web hosting.  What I've done via Webmin is create master zones for example.com and hostx.example.com.  In master zone example.com I've made A records for ns1, ns2, www, that all point to my external IP.  Then one for hostx.example.com pointing to it's internal IP.  In master zone hostx.example.com I've created A records for hostx.example.com and www pointing to hostx's internal IP.

---

