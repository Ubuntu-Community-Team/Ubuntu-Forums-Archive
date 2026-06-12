---
title: "Zimbra server"
date: 2014-09-29
forum: Server Platforms
---

### Post by shamz_71 on 2014-09-29
Hello geeks,

Im trying to install Zimbra server on Ubuntu 14.04.1 LTS in my Vmware for testing. 
I have installed the Ubuntu on my VM and its running fine (Y).

Zimbra installation pre-requisites ares

[COLOR=#333333][FONT=Source Sans Pro]For install properly Zimbra you will need the next:[/FONT][/COLOR]

[LIST]
[*]A valid public domain (example: domain.com)
[*]A valid IP Public address
[*]A internal DNS for create the following:
[LIST]
[*]An A entry for internal domain (example: mail.domain.local)
[*]An MX entry for your domain, you can use the example before (mail.domain.local)
[/LIST]

[*]A valid public DNS por create the following:
[LIST]
[*]An A entry for the domain (example: mail.domain.com) that points to your Public IP ADDRESS
[*]An MX entry for your domain, you can use the example before (mail.domain.com
[/LIST]
[/LIST]
Can some one help me in achieving the pre-requestites. I have just instaleld a fresh Ubuntu. NO DNS yet.

---

### Post by shamz_71 on 2014-10-10
[ATTACH=CONFIG]257107[/ATTACH]

Im trying to install few lib packages. few of them get installed perfeectly while few give me this error.
Can someone help.

---

### Post by nerdtron on 2014-10-10
> **shamz_71 said:**
> [ATTACH=CONFIG]257107[/ATTACH]

Im trying to install few lib packages. few of them get installed perfeectly while few give me this error.
Can someone help.

What guide are you following in installing a zimbra email server?

> [COLOR=#333333][FONT=Source Sans Pro]For install properly Zimbra you will need the next:[/FONT][/COLOR]


[LIST]
[*]A valid public domain (example: domain.com) 
[*]A valid IP Public address 
[*]A internal DNS for create the following:
[LIST]
[*]An A entry for internal domain (example: mail.domain.local) 
[*]An MX entry for your domain, you can use the example before (mail.domain.local) 
[/LIST]
 
[*]A valid public DNS por create the following:
[LIST]
[*]An A entry for the domain (example: mail.domain.com) that points to your Public IP ADDRESS 
[*]An MX entry for your domain, you can use the example before (mail.domain.com 
[/LIST]
  
[/LIST]


First, did you already bought your domain name? You can use your Registrar's DNS server for configuring the A and MX records.
Then, should have a public IP address. You can ask the network team or ISP for a public IP for your server.
you can either assign this to your router and configure port forwarding or assign it directly to your server. This part is more of a network related concern rather than Ubuntu related concern.

Anyway, zimbra is a bit harder to configure and heavy on resources. If you like to have a complete email server, try installing iRedMail on a fresh install of ubuntu Server. It just takes a ~15-30mins for the whole installation. It's worth trying on VM and very easy to install.
Link with screenshots: [http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)

---

### Post by shamz_71 on 2014-10-10
im trying to install it on a VM first. but my library packages dont get updated.
Any guide i follow, they tell to download few packages. And im stuck at this point.

Im following this guide: [http://ubuntuserverguide.com/2013/01/how-to-setup-zimbra-collaboration-suite-open-source-edition-8-0-2-in-ubuntu-server-12-04.html](http://ubuntuserverguide.com/2013/01/how-to-setup-zimbra-collaboration-suite-open-source-edition-8-0-2-in-ubuntu-server-12-04.html)

---

### Post by nerdtron on 2014-10-11
Your guide is for 12.04 and you are using 14.04. There are differences.

---

### Post by TheFu on 2014-10-11
I've been running Zimbra since ... 2007-ish.
From what I remember, here are the tricks.

* At least 1.5G of RAM, 2 CPUs.  This is the starting point.
* Ubuntu Server (ensure it is formally supported by the zimbra version you are installing)
* openssh-server - nothing else. NOTHING ELSE!!!!!!!!!!!!  Unless the Zimbra install guide says to put something else in.
* Trivial /etc/hosts file - This is necessary during upgrades too.  3 lines - not 4.
* Do not let the base OS have any other MTA - no postfix, no exim, no qmail, no other MTA.

I'm still on 10.04 for Zimbra, but plan to move to 12.04 shortly. Just need to run a few test migrations first to ensure all the minor tweaks I've done are working or can be fixed quickly.

Carefully read the ZIMBRA guides.  I've never trusted any of the others out there. When your job is making email work, that is critical to read all their release notes, any problems someone else had, forum posts for migrations, etc. 

I wouldn't run Zimbra if we weren't completely addicted to enterprise calendaring.  Ran postfix+dovecot for 10 yrs before - I won't go back.  Absolutely LOVE the server-side filters, so all my devices see exactly the same view.

DNS stuff is something you need to pay a provider for ... unless this is for a company and they run DNS already.  DNS is highly hackable-  best left to pros.  

of course, there are other opinions.  hope these help.

---

