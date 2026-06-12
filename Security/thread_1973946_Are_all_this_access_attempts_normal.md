---
title: "Are all this access attempts normal?"
date: 2012-05-05
forum: Security
---

### Post by sowdust on 2012-05-05
Hello everyone,

I set up my ubuntu server some months ago (around november); it is publicly online, reachable, of course, by anyone through the web.

I have noticed in my auth.log file many many login attempts from different locations, most of them trying with a root login, others trying with some popular user names (both of humans and services - eg "oracle").
Also, regular visitors of the web server are "Morpheus ******* scanner", "ZmEu" and other popular attackers.

Being it the first time I own a server, I don't know if this is normal and safe or if I should do something to limit this attempts.
So far I don't think there was any real attack nor have I found any successful login attempt, but I don't want to risk to be a brute force attack victim.
Any suggestion?

Thanks in advance,

---

### Post by CharlesA on 2012-05-05
Normal, yes. There are tons of bots. As long as you are using a strong password you should be fine.

Might want to look into rate-limiting with iptables to slow down the log noise.

---

### Post by sowdust on 2012-05-06
thank you! :)

---

### Post by unspawn on 2012-05-06
Couple of comments here if I may.

> **sowdust said:**
> Being it the first time I own a server
I can't infer from that if you are new to Linux as well. If you are not then you know where to find server administrators documentation. 
If you are new to Linux you should know what you run, why and how to manage it. Please read some basic Linux tutorials like [Rute Tutorial & Exposition]("http://rute.2038bug.com/index.html.gz"), the [Linux Newbie Administrator Guide]("http://linux.about.com/od/embedded/l/blnewbie_toc.htm"), [The Linux System Administrator's Guide]("http://tldp.org/LDP/sag/html/index.html") and the documentation your distribution provides.


> **sowdust said:**
> it is publicly online, reachable, of course, by anyone through the web. (..) So far I don't think there was any real attack nor have I found any successful login attempt, but I don't want to risk to be a brute force attack victim.
There is no reason to "worry", "think" or "guess": accounts can be checked, log files can be filtered for anomalies, settings can be verified and conditions can be tested to unambiguously conclude something is safe or not (Samhain, Logwatch, GNU/Tiger, OpenVAS). Using strong passwords should be a given anyway and brute force attacks are not all that Linux is susceptible to. See for instance the information disclosure vuln in PHP (CVE-2012-1823), TimThumb (OSVDB 7187[noparse]8)[/noparse] *which was disclosed on 2010-09-08, fixed on 2010-09-08 but still hits careless users to this day* or the CVE-2012-1190 which is a cross-site scripting (XSS) vulnerability in a long line of cross-site scripting vulnerabilities affecting PhpMyAdmin or the Apt-specific InRelease file vulnerability (USN-1385-1). So in the case of web stack application and other service vulnerabilities having strong passwords is not what prevents unwanted malicious activity. 


> **sowdust said:**
> I set up my ubuntu server some months ago (around november); 
The better approach would have been to have gone over securing and hardening before exposing the server. I'll point you to the security sticky [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812), the wiki [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) and one of the oldest security manuals around that still give you a good overview of things: [http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html). Please note 0) hardening a machine also means *testing applied measures* (using say OpenVAS or Nessus) and 1) learn applying measures isn't a one-off: you'll have to audit the machine regularly and adjust when necessary. 

*Linux may be available free of cost but running Linux is not free of responsibilities*

---

### Post by CharlesA on 2012-05-06
> **unspawn said:**
> 
I can't infer from that if you are new to Linux as well. If you are not then you know where to find server administrators documentation. 
If you are new to Linux you should know what you run, why and how to manage it. Please read some basic Linux tutorials like [Rute Tutorial & Exposition]("http://rute.2038bug.com/index.html.gz"), the [Linux Newbie Administrator Guide]("http://linux.about.com/od/embedded/l/blnewbie_toc.htm"), [The Linux System Administrator's Guide]("http://tldp.org/LDP/sag/html/index.html") and the documentation your distribution provides.

+1.


> There is no reason to "worry", "think" or "guess": accounts can be checked, log files can be filtered for anomalies, settings can be verified and conditions can be tested to unambiguously conclude something is safe or not (Samhain, Logwatch, GNU/Tiger, OpenVAS). Using strong passwords should be a given anyway and brute force attacks are not all that Linux is susceptible to. See for instance the information disclosure vuln in PHP (CVE-2012-1823), TimThumb (OSVDB 7187[noparse]8)[/noparse] *which was disclosed on 2010-09-08, fixed on 2010-09-08 but still hits careless users to this day* or the CVE-2012-1190 which is a cross-site scripting (XSS) vulnerability in a long line of cross-site scripting vulnerabilities affecting PhpMyAdmin or the Apt-specific InRelease file vulnerability (USN-1385-1). So in the case of web stack application and other service vulnerabilities having strong passwords is not what prevents unwanted malicious activity. 



The better approach would have been to have gone over securing and hardening before exposing the server. I'll point you to the security sticky [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812), the wiki [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) and one of the oldest security manuals around that still give you a good overview of things: [http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html). Please note 0) hardening a machine also means *testing applied measures* (using say OpenVAS or Nessus) and 1) learn applying measures isn't a one-off: you'll have to audit the machine regularly and adjust when necessary. 

I was going to post those links, but you beat me to it. ;)

I also like this one: [https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

> *Linux may be available free of cost but running Linux is not free of responsibilities*

Indeed.

---

### Post by sowdust on 2012-05-06
> There is no reason to "worry", "think" or "guess": accounts can be checked, log files can be filtered for anomalies, settings can be verified and conditions can be tested to unambiguously conclude something is safe or not 

very true and logical, the thing is that not being used to these issues I did not know how to judge the access attempts I noticed, nor I knew whether they could possibly turn out into something successful (for them) and "bad" (for me).

I want to thank both of you, both for reassuring me a little about what already happened, but overall for giving me very good advice on what to do for better guard my little server and be more responsible ; )

---

