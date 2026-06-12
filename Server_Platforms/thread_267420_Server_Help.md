---
title: "Server Help"
date: 2006-09-28
forum: Server Platforms
---

### Post by obe1kenobi on 2006-09-28
I haven't done much with servers and I'd like to learn. So I used the HowToForge walkthrough to install a LAMP server.  I was wondering what I needed as far as a website to host my server.  Do I need to buy a domain?  Can I just use a free subdomain? Who should I go through for hosting the site? 

Also does a mail server actually allow you to do?  Does it mean you can set up your own email addresses?

I don't really know much about the topic so any help would be much appreciated.

Please post any recommended reading (books or sites) as well.

---

### Post by pppetter on 2006-09-30
when you have a website(homepage etc) that you want to put on the internet, start with using a free subdomain. It's free :) You will actually be the one hosting your website, since it's your server.

I got my subdomain via [www.no-ip.org](www.no-ip.org), since I don't have a static IP-adress, but a dynamic. In my router(D-link) I configured so that my server got a static internal ip, I forwarded the http port to my server, and just added my username and password for my no-ip.com account so that it will report my new dynamic ip when it changes.

If you would set up a mailserver and you have a domain or like me, a subdomain, then yes, you can set up your own email adresses(as in [email]example@yourdomain.com[/email] or [email]example@your.subdomain.com[/email]).

I hope that my examples gave you something :)

---

### Post by obe1kenobi on 2006-10-01
Thanks for the info, I'll try that.  \\:D/

---

### Post by Iowan on 2006-10-01
It might be worth checking your ISP's guidelines concerning webservers.  At least a couple of the ISP's I've considered changing to (my dial-up is getting painfully slow for updating Ubuntu) expressly forbid "a server directly or indirectly (hidden behind a router) attached to their network through a subscriber account.

---

