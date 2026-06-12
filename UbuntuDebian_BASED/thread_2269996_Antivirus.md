---
title: "Antivirus"
date: 2015-03-19
forum: Ubuntu/Debian BASED
---

### Post by gordie692 on 2015-03-19
Hey guys I'm writing this post I pitched W7 on my desktop because my paypal account got a couple charges that I didn't make, I changed my password in paypal they refunded me but I went wiped W7 and put Lint Mint 17.1 64 bit I'm trying to make sure I'm secured do I need an antivirus I saw Commando for linux but thought I'd check in here first or is Ubuntu safer. From what I read linux distro are safe its what you like and do.

Thanks guys

---

### Post by kc1di on 2015-03-19
You don't absolutely need an antivirus program , but if it makes you feel better there is no harm either. 
Clamav is in the repositories it's a good antivirus scanner.  also AVG and Avast both have free Linux antivirus programs that can be installed.

Far more important though is a good fire wall system. 
here's a page that explains how to do that [https://wiki.ubuntu.com/BasicSecurity]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by gordie692 on 2015-03-19
how about that comomdo for linux

---

### Post by gordie692 on 2015-03-19
is mint linux 17.1 good or should I go back to Ubuntu I don't think I need an antivirus my desktop only has linux on it I download a bit but not much anyone mostly paying bills surfing just day to day computing

---

### Post by kc1di on 2015-03-19
Hi gordie692, 

Mint is good.  I Use both Ubuntu and mint on different machines.  either one is good.  Mint 17.1 is based on Ubuntu so they are very similar. 
comomdo is also good.  But as the article I quoted before says you don't really need it unless your connecting with a windows machine. 
Good Luck ;)

---

### Post by gordie692 on 2015-03-19
Thank you

---

### Post by kc1di on 2015-03-20
Your Welcome :)

---

### Post by maglin2 on 2015-03-20
Comodo AV for linux isn't officially supported for the Mint 17 kernel (because the open source redirect driver it uses is no longer maintained). You can find an unofficial patch over on the comodo forums (but would you want a patch from an unknown source in a security product that runs as root?).

Mint apparently doesn't apply all the Ubuntu security updates by default. Have a look here if you're concerned [https://sites.google.com/site/easylinuxtipsproject/mint-cinnamon-first#TOC-Enable-security-updates-for-level-4-and-5](https://sites.google.com/site/easylinuxtipsproject/mint-cinnamon-first#TOC-Enable-security-updates-for-level-4-and-5)

---

### Post by buzzingrobot on 2015-03-21
> **gordie692 said:**
> ... do I need an antivirus...

Probably not.

Almost all viruses target Windows, since that's where the most money is to be made. 

But, viruses are not the only thing we need to know about. If someone creates a fake site that looks just like your bank's, and then sends you a fake email that looks just like your bank's email, and then you click on the fake URL in the mail, you'll probably turn your bank account username and password over to the folks running that site.   That can happen using any operating system.

if you are on network with Windows users, running an anti-virus will help stop you from passing along infected Windows mail, etc. to those other folks.

Linux Mint is based on Ubuntu, Almost all the software packages in Mint come directly from Ubuntu servers. Mint does default to using a more conservative approach to updating.

---

### Post by Rob Sayer on 2015-03-21
I know tech support guys who have been using linux on their own machines and at work for 20 years.  Not one of them has *ever* installed an antivirus program on their personal linux machines.  Maybe clamtk on a server ... clam is meant to check emails and is best for mail servers.

As mentioned just because you won't get viruses does not mean you can't get hacked.  For a start you still need a strong password.

There's a saying.  The biggest computer security risk is actually between the keyboard and the chair.  I know too many people whose email addresses/passwords were hacked/phished and they couldn't understand how that could happen because they has norton AV.

---

### Post by sffvba[e0rt on 2015-03-21
Some [good reading]("https://help.ubuntu.com/community/Antivirus") on the subject...

---

### Post by Hard Core Rikki on 2015-03-23
You don't need an antivirus, you only need to make sure your machine isn't infiltrated from your network or your web traffic snooped on.

Make sure your firewall rules are set appropriately, and you're using a secure Wifi connection (wpa2 encrypted, aes, no tkip). And maybe change the router and Wifi connection's passwords too just in case your traffic was being sniffed locally.

---

