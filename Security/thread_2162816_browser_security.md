---
title: "browser security"
date: 2013-07-16
forum: Security
---

### Post by Tom_ZeCat on 2013-07-16
Okay, it is possible for the criminals to cause harm even to a Linux-based PC via a browser.  They can do it via things like Flash, Java, and Javascript.  However, many sites only show the proper content via these components.  I've therefore set out to have them installed in FireFox, but to block them on sites I don't trust.  I've installed these extensions: 

[LIST=1]
[*]NoScript
[*]Flashblock
[*]Adblock Plus[/LIST]
If it's a site I trust, I can either whitelist it or temporarily disable the plugins.  NoScript and Flashblock contain easy systems for whitelisting sites.  To my annoyance, Adblock Plus does not.  That app is more to avoid annoyance than for security, but I do want to whitelist some sites that I feel do not abuse advertising.  I'm wanting to block the ads of sites that shove a zillion ads into your face.  

Of course I'll need to turn around and do the same to Chrome, which I also occasionally use.  

Does this about cover it?  Or are there other things I should be doing?

---

### Post by tubbygweilo on 2013-07-16
Tom_ZeCat,
You have covered most of your bases but please don't then spoil things by failing prey to a rather well crafted social engineering inspired phishing or spearphishing attack via your in-box. If a link looks too good to be true then it often is. Remember to be up todate with security fixes from Ubuntu.

---

### Post by Tom_ZeCat on 2013-07-16
> **tubbygweilo said:**
> Tom_ZeCat,
You have covered most of your bases but please don't then spoil things by failing prey to a rather well crafted social engineering inspired phishing or spearphishing attack via your in-box. If a link looks too good to be true then it often is. Remember to be up todate with security fixes from Ubuntu.

Well, I'm about to make big money from a Nigerian prince who e-mailed me and I'll use some of that to buy a great hardware firewall.  J/K

But you're right.  They come up with numerous crafty social engineering schemes.  My roommate, who isn't very computer savvy, even received one by telephone.  Someone called up claiming to be from Microsoft saying that our computer was interfering with their network.  The person claimed everything could be fixed if we would go to a particular web page, download, and install some software.  My roommate doesn't know much about computers, but he is security conscious and smelled a rat and hung up.  I later researched it and found out there was a crooked organization in India randomly calling people in every English-language country in the world trying this scam.  If you got fooled into installing their software, it would hijack your PC.  Then, of course, you could pay the criminals money to fix it for you.  Ransomware via telephone.  

I've known other people to get ransomware, aka, a rogue anti-virus via clicking on a page on a web page link that supposedly installes Java, Flash, or some other legitimate application.  Unfortunatelly, it really installs the ransomware.  The moral: If a site claims you need Java, Flash or whatever installed, don't click on their link.  Only install these things from the manufacturer's web page if you're using Windows or Mac.  In Linux do that or use the repositories.

---

### Post by samiux on 2013-07-20
@Tom_ZeCat,

You said you installed the captioned browser add-ons to block the websites that you do not trust.  You whitelist the websites that you trust.  

What about the trust websites have vulnerabilities or infected by malware which can attack the clients?  I am not mention about the social engineering here.

Samiux

---

### Post by Erik1984 on 2013-07-20
> **samiux said:**
> @Tom_ZeCat,

You said you installed the captioned browser add-ons to block the websites that you do not trust.  You whitelist the websites that you trust.  

What about the trust websites have vulnerabilities or infected by malware which can attack the clients?  I am not mention about the social engineering here.

Samiux

Not TS but replying anyway ;) 

That's one of my 'fears' as well, trusted sites can be compromised and host malicious scripts. But what else can you do? Disabling JavaScripts always is no option for me. Modern sites nearly always require JavaScript to 'work'. Maybe enabling Apparmor would be nice as an extra line of defense?

---

### Post by samiux on 2013-07-20
> **Euroman said:**
> Not TS but replying anyway ;) 

That's one of my 'fears' as well, trusted sites can be compromised and host malicious scripts. But what else can you do? Disabling JavaScripts always is no option for me. Modern sites nearly always require JavaScript to 'work'. Maybe enabling Apparmor would be nice as an extra line of defense?

@Euroman,

I think Apparmor can only limited the attackers or malware to access your Linux box.

How about the vulnerable or infected malware trusted websites steal your cookies or tokens in order to access your web applications (may be the trust websites or other sites if possible) and get into your account?  I think Apparmor cannot prevent you from being attacked by this kind of attacks.

Samiux

---

### Post by Hungry Man on 2013-07-20
Samiux, you're describing a 'man in the browser' attack, or, CSRF/XSS. Noscript can prevent against CSRF/XSS attacks. A man in the browser attack can't be protected against, as it means the attacker is controlling the process, and is only interested in that. Your best bet is to try to prevent them from controlling it in the first place.

What apparmor can do is prevent an attacker who controls Firefox from further attacking your system, or gaining persistence through typical means.

---

### Post by samiux on 2013-07-20
In conclusion, if your browser (client) is secured but the website (server) is insecured, you (client) can be compromised in any mean.  In most cases, you (client) lost more than the websites (server).

Samiux

---

