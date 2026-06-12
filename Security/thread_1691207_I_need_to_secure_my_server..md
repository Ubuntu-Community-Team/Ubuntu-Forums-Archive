---
title: "I need to secure my server."
date: 2011-02-19
forum: Security
---

### Post by whosherox on 2011-02-19
Ok im new, i know apparmor is running. i was looking for firestarter but their isnt one.....how do i secure this server? i want a good firewall and some virus protection!. also do i need this?

---

### Post by metalf8801 on 2011-02-19
> **whosherox said:**
> Ok im new, i know apparmor is running. i was looking for firestarter but their isnt one.....how do i secure this server? i want a good firewall and some virus protection!. also do i need this?

What's the sever going to be used for?

---

### Post by whosherox on 2011-02-19
> **metalf8801 said:**
> What's the sever going to be used for?

i plan to host someones website. a business, so its important it is secure it will most likely be a dedicated server with a lot of space.

---

### Post by cariboo on 2011-02-19
Have a look at the [Sever Administration and Security]("http://ubuntuforums.org/showthread.php?t=1046738") sticky in [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339").

---

### Post by metalf8801 on 2011-02-19
Well first you need to make sure you only have what you need on it. You also need to make sure only the ports you need are open. For example if your not going to be using it as a Samba server then make sure your not running Samba. 

have you looked at [https://help.ubuntu.com/10.04/serverguide/C/security.html](https://help.ubuntu.com/10.04/serverguide/C/security.html)

Oh are you using 10.04 or 10.10? 

Also since your doing this for a business I strong recommenced working with Conical for support and/or training. 
[http://www.canonical.com/enterprise-services](http://www.canonical.com/enterprise-services)

---

### Post by lisati on 2011-02-19
There are options, a couple of which have already been mentioned.

Worthy of mention is mod_defensible, which is a DNSBL-based add-on for apache, that can help keep out the blog spammers. Others might mention fail2ban (which I've never used)

Some more ideas can be found at [http://www.petefreitag.com/item/505.cfm](http://www.petefreitag.com/item/505.cfm)

---

### Post by whosherox on 2011-02-19
Thanks for the advice. So if i ran a server with just ubuntu in its default self, would it be making a mistake? is ubuntu highly secure within itself?

---

### Post by whosherox on 2011-02-19
> **metalf8801 said:**
> Well first you need to make sure you only have what you need on it. You also need to make sure only the ports you need are open. For example if your not going to be using it as a Samba server then make sure your not running Samba. 

have you looked at [https://help.ubuntu.com/10.04/serverguide/C/security.html](https://help.ubuntu.com/10.04/serverguide/C/security.html)

Oh are you using 10.04 or 10.10? 

Also since your doing this for a business I strong recommenced working with Conical for support and/or training. 
[http://www.canonical.com/enterprise-services](http://www.canonical.com/enterprise-services)

Once i finish these trainings do i get a certification? a certificate or something hard copy?

---

### Post by cariboo on 2011-02-19
> Once i finish these trainings do i get a certification? a certificate or something hard copy?

You get the satisfaction of knowing you can secure a Debian based server, and you also get phone calls in the middle of the night when the server isn't working. :)

---

### Post by synapsys on 2011-02-19
> **whosherox said:**
> Thanks for the advice. So if i ran a server with just ubuntu in its default self, would it be making a mistake? is ubuntu highly secure within itself?

Yes! that would be a mistake. No matter how good an OS is, it's default installation will never be secure. The main things to remember are; disable unnecessary services, change default settings, use ridiculously strong passwords, use protection (anti-virus/firewall), etc. It's a good idea to "lock-down" or "harden" any computer that is directly connected to the internet (like your server.) Here is a good hardening guide to get you started:

[http://www.securenetwork.it/ricerca/whitepaper/download/Debian-Ubuntu_hardening_guide.pdf](http://www.securenetwork.it/ricerca/whitepaper/download/Debian-Ubuntu_hardening_guide.pdf)

---

### Post by HermanAB on 2011-02-19
Well, unlike the general practise on that other OS, the less stuff you run on your server, the more secure it is.  So, you generally do not need to layer on 'security' software.

I run my servers with a single iptables rule to protect them against most exploits:
```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

You only need a virus filter is you are serving Email, in which case you need to add spam filtration and RBLs too, but the purpose of that is not so much to improve the security of the server, but to improve the security of all the Windows mail clients and to enable users to find their legitimate mail in a sea of crud.

My mail server gets about 1 million spams a day, while I only get a handful of viruses and legitimate messages per day, so my signal to noise ratio (and the virus to noise ratio) is literally one in a million.  So, spam is a million times bigger problem than viruses.

---

