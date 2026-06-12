---
title: "which antivirus should i used?"
date: 2009-01-12
forum: Security
---

### Post by Paris Heng on 2009-01-12
Which is the best of anti virus in Ubuntu? So long, I am using AVG and Avast! But it seen not much protecting my PC from viruses and Trojan. Please recommend.

---

### Post by bodhi.zazen on 2009-01-12
Most people would advise you not use antivirus as Linux is not vulnerable to any known virus.

Perhaps if you were to explain what you are wanting and what it is you do not like about your current antivirus.

---

### Post by Tubes6al4v on 2009-01-12
If you simply want to lock down your Ubuntu System more, have a look at How-tos and threads in this forum. Play around, see what you can mess with. It is the best way to get to know it. If you haven't already, have a look at the [sticky ]("http://ubuntuforums.org/showthread.php?t=510812")in this forum.

---

### Post by scorp123 on 2009-01-12
> **Paris Heng said:**
> Which is the best of anti virus in Ubuntu? I use Linux since 1996 and I have never ever used anti-virus software here .... Why should I? There are no viruses here to begin with :D

There are a few exotic ones that people in research labs have created but those viruses either have to be installed by the superuser "root" himself in order to do any real Windows-style damage or ... they simply don't do any serious damage :D

There is a far higher risk that you yourself might by accident delete your own files than that a virus might ever do it for you.

> **Paris Heng said:**
>  But it seen not much protecting my PC from viruses and Trojan. Please recommend. My recommendation would be that you let go of your now inadequate Windows-thinking. There is no real risk of viruses or trojans. And the "Bluescreen of Death" only exists as screensaver.

Enjoy your new freedom ;)

---

### Post by listerdl on 2009-01-12
scorp123, amazing post!

I have come from a windows background, (in fact i still use vista at work) and basically spend a lot of time trying to protect and update firewalls and anti viruses etc....

But, what is the point of firestarter?

Would you suggest uninstalling AVG?

Thanks - :)

---

### Post by bodhi.zazen on 2009-01-12
> **listerdl said:**
> I have come from a windows background, (in fact i still use vista at work) and basically spend a lot of time trying to protect and update firewalls and anti viruses etc....

Welcome. Linux security is both similar but there are a number of major differences too.

> But, what is the point of firestarter?

The linux firewall is iptables. iptables is difficult to learn and ther are several gui front ends, of which Firestarter is one.

The default configuration tool is ufw, and if you want a gui install gufw.

> Would you suggest uninstalling AVG?

Thanks - :)

As with firestarter, I suggest you :

1. Stop a minute and take a look at the basics of how your new OS works. May I suggest you start with the stickies at the top of this forum ?

2. Security is a process, not an application. Linux is more modular then windows, so you have to stop a minute and think, what do I want to accomplish and what is the best taks for the job ?

So, to answer your questions,

1. What do you want a firewall to do for you ? Do you have a router ? Are you running a private server ? Do you just want to block ping requests ? Are you running a LAN ? Do you want your firewall to perform NAT ?

2. What do you want an antivirus program to do for you ?

If you want an antivirus program to protect your desktop from known linux viruses, you do not need it, Linux has been pateched to all known viruses. If you want linux antivirus because you are running a linux file or mail server, with windows clients, well that is different.

---

### Post by brian_p on 2009-01-12
> **listerdl said:**
> 

But, what is the point of firestarter?

No part of its function is to detect viruses.

> Would you suggest uninstalling AVG?

As already said

> There is no real risk of viruses or trojans.

What course of action does this suggest to you?

---

### Post by teddks on 2009-01-12
Wait, OP has AVG and Avast! installed... on **Ubuntu**?

---

### Post by scorp123 on 2009-01-12
> **listerdl said:**
> But, what is the point of firestarter? While viruses and trojans and other brainless script-kiddie stuff is far from being a real threat here ... human hackers (with brains ... usually) are absolutely real and might be a threat. Usually they are after servers of "big & evil corporations" and ignore Linux desktops. So the purpose of such a firewall would be to keep unwanted connections and the people behind those connection attempts away from your installation.

But as I said ... hackers (and I really mean those who deserve to be called like that) are usually targetting servers of "big evil corporations" and "big bad governments". Attacking a Linux desktop is totally not interesting in any way to them, there would be nothing to gain. Hacking the Pentagon and retrieving the proofs for super-secreat alien technology or placing undecent pictures on the Vatican's web site, or getting Amazon's database with valid credit card numbers  ... that's where the fun is and this is what they are after ;)

---

### Post by bodhi.zazen on 2009-01-12
The only point to crack a linux, or any other desktop, of those types is to help co-ordinate attacks.

---

### Post by Dr Small on 2009-01-12
> **scorp123 said:**
> But as I said ... hackers (and I really mean those who deserve to be called like that)

There are three types of hackers, not just one. They consist of Whitehat, Greyhat and Blackhat (or, in other words, Cracker). Stereotyping the word "hacker" to mean "criminal activity" is wrong in every sense, seeing how there are many thousands of good hackers who wear Whitehats and "hack" (tweak, modify, edit) their systems. Others also who claim to be hackers are security experts. 

Blackhat hackers (or Crackers, as we hackers like to call them) are the criminal bunch. Hackers have a natural distaste for Blackhat Hackers, seeing how they set out to destroy the infrastructure that the real hackers create and secure.

So please, do not associate the word "hacker" with "criminal activity", as it gives hackers a bad name and most take it as an insult, who claim to be hackers.

Dr Small

---

### Post by Paris Heng on 2009-01-14
> **scorp123 said:**
> I use Linux since 1996 and I have never ever used anti-virus software here .... Why should I? There are no viruses here to begin with :D

There are a few exotic ones that people in research labs have created but those viruses either have to be installed by the superuser "root" himself in order to do any real Windows-style damage or ... they simply don't do any serious damage :D

There is a far higher risk that you yourself might by accident delete your own files than that a virus might ever do it for you.

 My recommendation would be that you let go of your now inadequate Windows-thinking. There is no real risk of viruses or trojans. And the "Bluescreen of Death" only exists as screensaver.

Enjoy your new freedom ;)

Danke!

---

### Post by Paris Heng on 2009-01-14
But if come to a Linux server which used for a data storage "top secret information", e.g. a Suse SLE server, did we really no need the anitivirus and the firewall for the server?

---

### Post by scorp123 on 2009-01-14
> **Dr Small said:**
> Stereotyping the word "hacker" to mean "criminal activity" is wrong in every sense I agree, but you see: you and me do understand the term "white hat", "black hat", and so on. You and me understand the important difference between a "hacker" and a "cracker". A noob does not. Neither does the general public (e.g. non-IT people). So that's why I stick to the term "hacker" that everyone understands even though it's not really correct.

---

### Post by ratmandall on 2009-01-14
> **Paris Heng said:**
> But if come to a Linux server which used for a data storage "top secret information", e.g. a Suse SLE server, did we really no need the anitivirus and the firewall for the server?

You won't need an anti-virus.
You will need to configure a firewall so it's harder for crackers to get in.

---

### Post by Vantrax on 2009-01-14
> **ratmandall said:**
> You won't need an anti-virus.
You will need to configure a firewall so it's harder for crackers to get in.

Not to rain on the no AV get a firewall parade, but Ubuntu blocks all ports by default. So no need to have a firewall unless you are installing server apps which have vulnerabilities or are being misconfigured.

---

### Post by hyper_ch on 2009-01-14
ubuntu does not block any port by default. By default there is nothing listening on any port but if you install a daemon then the port is not "blocked".

---

### Post by bodhi.zazen on 2009-01-14
> **Paris Heng said:**
> But if come to a Linux server which used for a data storage "top secret information", e.g. a Suse SLE server, did we really no need the anitivirus and the firewall for the server?

Those questions are very broad, what do you want to use antivirus for ? What do you want a firewall for ? What kind of a server ?

If you are running a samba or mail server with Windows clients, antivirus may make some sense. If you want to build a box to act as a router a firewall may make sense.

If you do not know why you are installing antivirus or a firewall how can we tell you if you need one ?

---

### Post by hyper_ch on 2009-01-14
if he does not know why he wants to install AV or firewall then he very likely doesn't need it...

---

### Post by oldsoundguy on 2009-01-14
Many answers, all leading to the same conclusion.  Hope the OP now understands that, as long as there is nothing Windows involved on their computer. no need for AV or spyware or general malware protection.  ONLY when there is something MS functioning in an MS background is there a need for such.
(be it separate computers using the Linux machine as a head end server, a separate partition on the drive running Windows,  Virtual Machine running Windows or running Windows in a Linux add on such as Wine or Cedega or whatever else is now out there.)

The only protection you need IS a firewall, but it can be a basic one. (this stops port scanning and using your machine for such as DOS attacks.  Those things still can NOT get past the general nature of the Linux system, but they can, in some cases, use your computer to RELAY.)

The best firewall is a hardware firewall, furnished by any GOOD (and kept up to date) router.

Personally, I have never used the Linux firewall as I AM behind a router.

You DO, however, need to keep whatever browser you chose up to date with the protection programs available for IT from the home site of that browser.  You do want to stop redirects, malicious web sites and phishing attempts, etc.  The reason I chose Firefox, as it has a boatload of nice add ons to make surfing more safe and faster.  But, that may not be the one you choose.  Whichever one you did choose. keep it updated often as the malware script kiddies and the crooks are all over and just waiting for someone to make a mistake!

---

### Post by scorp123 on 2009-01-16
> **Paris Heng said:**
> ... a Linux server which used for a data storage "top secret information"...  did we really no need the anitivirus and the firewall for the server? Please explain to me what "top secret data" has to do with anti-virus software? :confused:

Anti-virus software does nothing whatsoever to protect the secrecy of any data on a Linux server. I fail to understand what you want to say.

If you have "top secret data" on a Linux server then it would be better to invest time, money and resources into e.g. strong authentication mechanisms (e.g. Secure-ID, Crypto-Tokens, Challenge+Response schemes, etc.) and access control. And maybe you could do a full-disk encryption of the harddisks where this data is stored? This could be very useful in case somebody gains physical access and decides to steal the harddisk where the "top secret data" is stored.

But anti-virus software? Nope, I don't see what it would do here and how your "top secret data" might benefit from that.

---

