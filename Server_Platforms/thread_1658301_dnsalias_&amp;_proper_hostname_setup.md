---
title: "dnsalias &amp; proper hostname setup"
date: 2011-01-02
forum: Server Platforms
---

### Post by greenrubberducky on 2011-01-02
Hello everyone!

First, let me say do love the forums. 99% of the time I can find straightforward answers to my Ubuntu server issues. This one, well, not so much.

I have a simple LAMP server running in my basement. 10.10 server. My complication comes from how I face the internet. 

I own my URL, call it "mysite.com". I have a free DynDNS.com account. That URL is "mysite.dnsalias.com", and it gets my home IP address constantly updated from my home router. I bought "mysite.com" from 1&1 Internet, and have "www.mysite.com" forwarded to "mysite.dnsalias.com" through 1&1. My home router then has an open port (80, of course) to the internal network IP address of my LAMP server. This setup works great. When I go to [http://www.mysite.com/](http://www.mysite.com/), it does indeed land me on the homepage of my home LAMP server (which happens to run Drupal). All very nice and serviceable.

My problem now comes when trying to set up postfix to allow my Drupal site (or indeed any mail program) to send mail from my home server. It simply doesn't work. I can set up the server, connect to it, send mail locally, etc. However, I cannot connect via mysite.com, or the dnsalias.com URL. 

My question is around how I should set up my hostname locally, and how should I set up the string of accounts and URLs that allow the world to connect to me? Does anyone have experience with a similar setup? I'd like to run all mail for mysite.com right from my home server if possible. 

Let me know if I'm leaving out critical information. Thanks for the help!

---

### Post by jgedeon on 2011-01-02
Look what you did to serve web pages.  You need to do the same thing for mail.  You may need to use your ISP's email server to send out from your server to the internet.  You can set up a relay host with postfix to accomplish this.

---

### Post by greenrubberducky on 2011-01-02
Right, makes sense. I do believe I need a few more specifics. My web server gets the forward via a simple http redirect. That doesn't require any intervention on my server. The mail setup does, I believe. I could use some more details there.

---

