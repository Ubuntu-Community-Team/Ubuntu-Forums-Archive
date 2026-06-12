---
title: "DNS..domain name stuff, help"
date: 2009-10-25
forum: Server Platforms
---

### Post by noblerabbit on 2009-10-25
Hello,

I am trying to run a web server from my home computer. I am just using normal desktop, as the web thing is really just for testing, making web pages, so that they are robust before I move them to an actual host.

I have installed apache2, php5, etc. and have it running on my IP (forwarded port 80 traffic to my machine behind the NAT) so that when I type the IP to our connection here, it finds my web pages.

Problem is, some of the stuff I am trying to do mean I need a domain name. I still own a domain name with 123reg from a site I was running a year or so ago, that is no longer hosted.

I cannot seem to figure out how to "link" that domain name to the IP of our house here.

(sorry for the use of incorrect terminology here and there, I'm still learning).

Thanks for any help you can provide :P

---

### Post by volkswagner on 2009-10-25
> **noblerabbit said:**
> ...

I cannot seem to figure out how to "link" that domain name to the IP of our house here.


You will need to log into your reg123 account and edit your DNS settings.  I am not familiar with their control panel, but you will want to point your domain name to your external ip address (set your a record).  You may need to set your domain to your ip and set your www subdomain to your top level domain, so you can use it with our without the www prefix.

As long as your router has port 80 open to your server than you should be good to go.

If you don't have a static ip address from your ISP, you may need to keep track and periodically update your account at 123reg.  To avoid such a task, you can sign up for dynamic DNS service at such a place like DynDns or noip.com.

---

### Post by noblerabbit on 2009-10-26
Thanks for your reply! :P

I get the feeling I need to change nameserver too, is that correct? At the moment the nameserver information points to the hosting company I used to use, but 123reg has their own too. What do I do about that.

---

### Post by volkswagner on 2009-10-26
Yes you will need to reset DNS servers to 123reg's name servers.

---

### Post by noblerabbit on 2009-10-27
Thank you very much for your help :D

---

