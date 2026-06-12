---
title: "Ubuntu DNS server redirect"
date: 2007-11-15
forum: Server Platforms
---

### Post by fry15 on 2007-11-15
Hi,

I have an ubuntu server and I want to add a dns server service to it. But I want to do something a bit unusual, I want it to redirect, or return all requests to one ip address, so if someone types eg 'www.google.com' it will take them to the wrong ip, which i would like to set. 

Now im not an overally technical person when it comes to this kind of specifics, but if someone could point me in the right direction of config files to change, or perhaps the correct technical name of what I want to do, it would be a great help.

Thanks in advance!

---

### Post by scrooge_74 on 2007-11-15
Would not be easier to put a proxy server and firewall those sites you dont want users to see? Maybe using Dansguardian to block and filter content? I use it for my kids.

And you can easily make all PCs on your lan to go throught your proxy server and block those sites you dont want them to see.

You can also use OpenDNS service and block sites from there is an easy first step

---

### Post by fry15 on 2007-11-16
i see how that could work! it makes sense. i'll try it that way.

thanks for your help!!

---

### Post by scrooge_74 on 2007-11-16
Check the forum there is a good tutorial for Dansguardian and proxy servers

Good luck,  post if you dont understand something

---

