---
title: "Can I set up a domain name server?"
date: 2009-07-29
forum: The Cafe
---

### Post by dragos240 on 2009-07-29
Hi,
Is it at all possible to create a domain name server, and avoid paying for a domain? I want to try this for 2 reasons.

One is because I want a free domain for my website, and I am planning on self-hosting also.

Two is because I am very curious to see if it's possible.

---

### Post by ghindo on 2009-07-29
**EDIT:**  Never mind.

---

### Post by cariboo on 2009-07-29
First of setting up your own dns server is not for the faint of heart, check out all the problems people are having  [here]("http://ubuntuforums.org/forumdisplay.php?f=339").

You can buy a domain name [here]("http://www.active-domain.com/") for less than $10.00 a year.

---

### Post by MaxIBoy on 2009-07-29
[Nevermind, misunderstood the question]
[]("http://www.dyndns.com/services/dns/dyndns/")

---

### Post by dragos240 on 2009-07-29
> **cariboo907 said:**
> First of setting up your own dns server is not for the faint of heart, check out all the problems people are having  [here]("http://ubuntuforums.org/forumdisplay.php?f=339").

You can buy a domain name [here]("http://www.active-domain.com/") for less than $10.00 a year.

If it exists, I want to try it.

---

### Post by MaxIBoy on 2009-07-29
You can register a domain name for free if you're willing to take care of the actual hosting (i.e. on a home server.)
[http://www.dyndns.com/](http://www.dyndns.com/)

---

### Post by doas777 on 2009-07-29
you can set up bind for an internal dns server if you want. i use one for my interior domain. 

unfortunately, if you want your domain to be registered with the dns root network, so that the public may resolve your name, then you have to register via an ICANA certified registrar: [http://www.icann.org/en/registrars/accredited-list.html](http://www.icann.org/en/registrars/accredited-list.html)

setting up bind is as easy as installing bind9 and configuring zones. here is a tutorial on bind setup:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

Edit: I should say, a publicly accessible second level domain. as maxiboy pointed out, you can register a subdomain (third level and lower) off a service like dydns.

---

### Post by dragos240 on 2009-07-29
I used to use no-ip for that. But, they since, have added a subdomain limit.

---

### Post by virusiidx on 2009-07-29
If you're on a regular consumer line, it's most likely a dynamic IP. So running your own DNS may not be the best thing to do. However, if you want to run your own webserver, you can use dynamic dns services such as dyndns or no-ip to keep your domain name updated with the right IP address that points to your server. You will probably run into some problems such as emails getting blocked by most email services, such as gmail, yahoo, hotmail, etc... since they block dynamic IP address due to spammers. 

I've been running a web server at home myself hosting multiple sites of my own and friends using a dynamic dns service (no-ip.com). Only problems I usually have is with outgoing emails due to what I mentioned above, so instead I use gmail's smtp server, but it's still a problem when a script such as php's mail() function tries to send out emais, they get blocked. Other than that, it's been working fine for me.

 I've been running the server for the last 7-8 years using that dynamic dns service. So I basically only pay for the domain name itself ($7-10/year) and the dns service ($25/year/domain). Still better than paying a monthly hosting fee. :)

Eventually, I'm hoping to get FIOS business line with a static IP so I can just configure my own DNS. However, I'm not too savvy in setting up DNS, so it might be a challenge, but I'm sure I can eventually figure it out.

---

### Post by Sublime Porte on 2009-07-29
> You can register a domain name for free if you're willing to take care of the actual hosting (i.e. on a home server.)

Regostering a standard domain name is not free, even if you're going to host the DNS yourself.

---

### Post by philcamlin on 2009-07-29
dyndns has some free ones :popcorn:

---

