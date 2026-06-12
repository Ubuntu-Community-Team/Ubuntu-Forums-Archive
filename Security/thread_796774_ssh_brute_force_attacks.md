---
title: "ssh brute force attacks"
date: 2008-05-16
forum: Security
---

### Post by jeff.sadowski on 2008-05-16
Reading
[http://www.securityfocus.com/comments/articles/11518/35098/threaded#35098](http://www.securityfocus.com/comments/articles/11518/35098/threaded#35098)
Reminded me of an issue I had at work a year ago I implemented shellter and more or less forgot about it. Before I implemented it I was getting hit 1000 times a day or more with ssh attempts now I am down to 20 a day. 

I would expect to find before too long that something along the lines of shellter [http://shellter.sourceforge.net/](http://shellter.sourceforge.net/) or Brute Force Detection [http://www.rfxnetworks.com/bfd.php](http://www.rfxnetworks.com/bfd.php) will be installed by default with open-ssh
with all distros. Is this in the plans for ubuntu? Could we have someone take a look into it please? Thank you.

---

### Post by Oldsoldier2003 on 2008-05-16
DenyHosts is in the repos but isnt installed by default. It works real well for blocking bruteforcers.

---

### Post by HalPomeranz on 2008-05-17
I'll also note that simply running your SSH servers on an alternate port number works extremely well for avoiding the brute force bots.  Eventually the attackers will get smart enough to use Nmap to find the SSH daemons on alternate ports, but for now I'm not bothered by them.

---

### Post by Oldsoldier2003 on 2008-05-17
Personally i never bother to change the ports I just disallow password logins and restrict public key logins to only certain accounts. the script kiddies cant defeat that even with brute force lol. you can throttle connections using iptables rules to stop the "knocking at the door" :)

---

### Post by hyper_ch on 2008-05-18
changing SSH port is about as secure as using WEP on your wifi

---

### Post by kevdog on 2008-05-18
I dont think anyone stated changing ports was secure, only that it definitely cuts down on the number of random hits your daemon is experiencing -- which may be beneficial for other reasons beyond security.

---

### Post by HalPomeranz on 2008-05-18
> **hyper_ch said:**
> changing SSH port is about as secure as using WEP on your wifi

It's like they say, "Security through obscurity doesn't work... but obscurity is a layer."  If you rely entirely on obscurity for your system defenses, then you're not going to get security.  But making things less straightforward for an attacker is at least an incremental improvement in your overall security posture.

In this case, changing the port doesn't help with the overall security of the box, but it least it stops me from being bothered by all of the annoyance of the brute force bots.  That means I can spend my time/resources doing more useful security configuration.

Of course you have to balance this against the cost of the configuration change-- teaching users to use the alternate port number (or configuring /etc/ssh/ssh_config to use the correct port number automatically), etc.  Your mileage, as always, may vary...

---

### Post by brian_p on 2008-05-18
> **HalPomeranz said:**
> It's like they say, "Security through obscurity doesn't work... but obscurity is a layer."

I wasn't familiar with that quote so, wondering who "they" are, did a quick search and wasn't convinced.

> If you rely entirely on obscurity for your system defenses, then you're not going to get security.  But making things less straightforward for an attacker is at least an incremental improvement in your overall security posture.

If there is no security with obscurity alone how does using it add any?

> In this case, changing the port doesn't help with the overall security of the box, but it least it stops me from being bothered by all of the annoyance of the brute force bots.  That means I can spend my time/resources doing more useful security configuration.

Failed attempts are failed attempts. If you didn't look at them they are less bothersome.

---

### Post by HermanAB on 2008-05-18
The iptables rate limiting filter can be used to stop any and all brute force and DOS attacks.  Add the following to the bottom of /etc/rc.d/rc.local:
 
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

---

### Post by brian_p on 2008-05-19
> **HermanAB said:**
> The iptables rate limiting filter can be used to stop any and all brute force and DOS attacks.  Add the following to the bottom of /etc/rc.d/rc.local:


From the number of times it is mentioned one would think serious brute force and DOS attacks were very common and yet this corner of the internet hasn't noticed any directed at it. True, there have been 305 attempted logins via ssh since May 3 but they are going nowhere and consume far, far fewer resources and an insignificant proportion of my time than the 500,000+ per year spam emails which arrive in one of my POP3 accounts.

---

### Post by HermanAB on 2008-05-19
I got SSH attacks on my servers - very annoying.  However, using a non-std port made it go away.  I still do the new connection rate limiting too though.

---

