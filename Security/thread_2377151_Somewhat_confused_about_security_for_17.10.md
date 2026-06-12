---
title: "Somewhat confused about security for 17.10"
date: 2017-11-09
forum: Security
---

### Post by ultratamale on 2017-11-09
I am looking to install a security suite for 17.10. I need to be able to scan for all types of malware, and I need a regular firewall and real time scanner. I usually use Kaspersky. I see that they have linux solutions, but they appear to be for businesses. I am not a business. What should I do? I just need it for a desktop.

---

### Post by wildmanne39 on 2017-11-09
*Thread moved to **Security for a more appropriate fit**.*

---

### Post by alwayshacked on 2017-11-10
Individuals are not prohibited from purchasing business products, so unless cost is a factor, why not buy the business product?

If cost is a factor, consider looking for alternatives, pfsense is a nice BSD setup where you can run Snort & Suricata as your realtime scanner. The thing to remember with IDS & IPS systems is the IDS just detects, it doesnt block, and IPS protects so will block. There are other scanners you can also investigate, plus when investigating IPS systems, check out just how quickly they block something. I found some only react after the malicious packets have got to the target device, in other words they shut the barn door after the horse has bolted. 

There are other linux distro's to check out or if you feel competent enough, you could build you own, if you dont mind writing your own scripts to setup the box. 

Alternative, look at AV companies that provide Linux solutions besides Kaspersky. No AV system will ever detect 100% of the viruses according to shadowserver stats so you may want to invest in two different AV systems for piece of mind.


[https://www.shadowserver.org/wiki/pmwiki.php/AV/VirusDailyStats](https://www.shadowserver.org/wiki/pmwiki.php/AV/VirusDailyStats)

---

### Post by DuckHook on 2017-11-11
This is not good advice because it is grossly over-reactive and does nothing but needlessly spread fear, uncertainty and doubt.

@ultratamale

While it is desirable to be prudent, informed and proactive, it is not productive to be paranoid. Our computer systems are not security sieves that constantly leak our private data like nattering rumour-mongers.

When it comes to Linux, there are no known viruses in the wild. Therefore, the use of AV apps are a waste of time, energy, money and resources that could be far better employed elsewhere. Instead of buying an AV app, learn how to configure apparmor. Instead of agonizing over what's in the guts of each browser, install noscript, ghostery and a cookie manager and don't do stupid things on stupid sites. Instead of sifting through each TCP/IP packet getting constantly spooked by false positives, configure UFW properly. Instead of getting mired in rkhunter, stop downloading illegal torrents, don't install non-repo apps and stop adding PPAs to your system like candy. Instead of swearing off WIFI, update religiously, invest in a VPN and learn to use TOR.

A pattern emerges. What's important in security is not tools and apps; but rather, your behaviour. While there are indeed tools that are useful for diagnosis, and while there is a place for penetration testing, there is also a real danger in allowing these tools to take on a life of their own and become the ends in your security rather than just the means. For the vast majority of us, the need to conduct pen testing or packet sniffing (or AV scanning for that matter) is unnecessary and pointless. If you want to do so for curiosity's sake, then by all means, but don't confuse all of the inevitable false positives you will be getting with the sky falling.

I've been on these forums a long time and solved thousands of problems for people in all sorts of trouble. 99% of the real problems we deal with are not about security; they're about people doing foolish things, either out of ignorance or carelessness or thinking of themselves as minor deities who know everything.

If you really want to learn good Linux security practices, then take a look at the link in my sig: ***Security Basics***. That will provide you with a solid launching point on security because it is written by a real security guru who is realistic, knowledgeable and doesn't succumb to the temptation to cry "Wolf!"

---

### Post by bashiergui on 2017-11-22
> **ultratamale said:**
> I am looking to install a security suite for 17.10. I need to be able to scan for all types of malware, and I need a regular firewall and real time scanner. I usually use Kaspersky. I see that they have linux solutions, but they appear to be for businesses. I am not a business. What should I do? I just need it for a desktop.
Why do you need to scan for malware?

---

### Post by ian-weisser on 2017-11-22
> **ultratamale said:**
> I am looking to install a security suite for 17.10.

This gets asked a lot.
So often, in fact, that there is an excellent [set of]("https://ubuntuforums.org/showthread.php?t=1871177") [Stickies]("https://ubuntuforums.org/showthread.php?t=510812") at the top of this Security subforum

Read those first.
Then ask your follow-up questions.

---

