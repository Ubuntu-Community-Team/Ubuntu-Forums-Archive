---
title: "Website hosting issues (with 9.04, apache2, bind9, etc.)"
date: 2009-08-25
forum: Server Platforms
---

### Post by fiveironfrnzy08 on 2009-08-25
Hey,
I'm kinda just starting out with servers and that fun stuff. I've got Ubuntu 9.04 Desktop, Apache, Bind, and a few other things installed and I've been messing around a bit with those. I've got a site up that I'm trying to configure a little bit. I can view from the computer with Ubuntu on it by putting in [www.giuseppesnewbrighton.com](www.giuseppesnewbrighton.com), but can only it from another computer if I put in my external IP address (174.*.*.*). Do I need to do further configuration with Bind9 or Apache to resolve that to [www.giuseppesnewbrighton.com?](www.giuseppesnewbrighton.com?) I just don't really know where to go from here, kinda stuck.

By the way, I'm trying to do all this without using any hosting services online or anything like that. So I want to do it all completely organically, so to speak :). I also chose not to get a static external IP address from qwest in order to save money/challenge myself. For now I'd like to just make the appropriate alterations whenever qwest changes my external IP. 

Thanks in advance :)

---

### Post by cariboo on 2009-08-26
Do you own the domain? Do you portforwarding setup correctly on your router? To check go to [canyouseeme]("http://canyouseeme.org/").

---

### Post by fiveironfrnzy08 on 2009-08-26
My ports are all set up to forward on my router, they're all working (http, ftp, etc). 
Do I NEED to register my domain with someone or is there any way to set up a website without registering, even if it then won't be officially mine (where someone else could register it and take over the domain)?

---

### Post by jocampo on 2009-08-26
> **fiveironfrnzy08 said:**
> Hey,
I'm kinda just starting out with servers and that fun stuff. I've got Ubuntu 9.04 Desktop, Apache, Bind, and a few other things installed and I've been messing around a bit with those. I've got a site up that I'm trying to configure a little bit. I can view from the computer with Ubuntu on it by putting in [www.giuseppesnewbrighton.com](www.giuseppesnewbrighton.com), but can only it from another computer if I put in my external IP address (174.*.*.*). Do I need to do further configuration with Bind9 or Apache to resolve that to [www.giuseppesnewbrighton.com?](www.giuseppesnewbrighton.com?) I just don't really know where to go from here, kinda stuck.

By the way, I'm trying to do all this without using any hosting services online or anything like that. So I want to do it all completely organically, so to speak :). I also chose not to get a static external IP address from qwest in order to save money/challenge myself. For now I'd like to just make the appropriate alterations whenever qwest changes my external IP. 

Thanks in advance :)

I've being doing that for last 2 or 3 days, finally working as expected. Two sites with one IP. They are running and hosted on my Ubuntu headless server.

For your reference, take a look on my thread and see how your apache server configuration files should look like: [http://ubuntuforums.org/showthread.php?t=1249354]("http://ubuntuforums.org/showthread.php?t=1249354") But 1st, you MUST pay for your domain name registration. Choose whatever company you want. Prices per year vary from 10 to 30 bucks. Then, log in into that company site and change the A and CNAME records. Make them point to your public IP address and voila' ... you are hosting your own websites via Apache.

Do not forget to secure Ubuntu and Apache. Here are some tips for Apache: [http://www.petefreitag.com/item/505.cfm]("http://www.petefreitag.com/item/505.cfm") and you should put a firewall in front; open port 80 and the SSH port. Do not make the stupid mistake that I made last week using common 22 port for SSH ;-) ...you can, but be prepare for a Brute Force SSH attach. To avoid that change the port and install deny_host. Tweak your SSH configuration too and avoid root access (just in case, 'cause we do not use root on Ubuntu)

Have fun!

---

### Post by Lori700698 on 2009-08-26
Website has to be registered, only $10 for a year at godaddy if your just playing around.  The reason you must register is that it's like a big phone directory.  You set up your domain name and set up the name servers to point to your IP, then you set bind with your name server information so when somebody types in your [www.yourdomain.com](www.yourdomain.com) the register points them to your name server which bind sends out the signal I have that information and you can get to that site here.  If you don't register any Joe can and then it's not yours.  Get the domain registered and come back for more help with Apache and bind.  There not easy, but awesome after you get it all running!  There as some fantastic tutorials here!

Lori

---

### Post by terazen on 2009-08-26
If you only want to test just put your site in the /etc/hosts file of your client pc.  You'll be able to get to the site by entering the url into a web browser.

This won't test your bind configuration necessarily though.  To do that you'll need port forwarding on your router for dns (udp 53) and set your server's ip as dns server on the client pc.  This won't work well if your isp changes your ip address often.  If that seems like a problem check into free dynamic dns services.

---

### Post by akhilles on 2009-08-27
Get a free account at and set up your domain. Your URL will be like #WHATEVER_YOU_TYPE_&_NOT_TAKEN#.dyndns.com or any of the dozen free domains. Your post inspired me to try it out since I have apache2 up & running & some webpages. It's working perfect with my dynamic IP. To keep the IP up to date, I installed ddclient which updates the IP to dyndns auto.

[https://www.dyndns.com](https://www.dyndns.com)

Even if you pay for a domain name, it mustn't have been taken by someone else.

Most important is secure your server.

---

