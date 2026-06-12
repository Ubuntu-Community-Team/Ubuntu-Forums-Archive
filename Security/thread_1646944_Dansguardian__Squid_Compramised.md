---
title: "Dansguardian / Squid Compramised?"
date: 2010-12-16
forum: Security
---

### Post by crashed111 on 2010-12-16
Hi

I was just alerted to the fact that my connection was going mad however no computers were browsing the net or performing any kind of update etc. 

I quickly did a tcpdump and I was sending a lot of web traffic upstream to a IP I have never seen before. 

I logged onto my server and stopped dansguardian and the traffic instantly stopped. I also tailed the access log during this and found no evidence of anything being accessed in dansguardian. Started it up again and it worked fine. 

This must have at least been going on for 10 mins. 

Is it possible dansguardian has been compromised? I am using a fully patched version of the latest LTS, I know sometimes flash videos can be held back to be scanned even once the web browser on the client has been closed but I could find no evidence of this either.

As an update I have just run rkhunter and shkrootkit and have had no issues found.

---

### Post by bodhi.zazen on 2010-12-16
Hard to tell from what little information you posted.

---

### Post by crashed111 on 2010-12-16
> **bodhi.zazen said:**
> Hard to tell from what little information you posted.

Hi

Thats the problem I am having I am finding it hard to get some information on it. Access log does not really give anything away as strange and when it happened there was nothing coming into it anyway ( using tail -f) ........

Looking at the tcp stream all I was sending upstream were ACK`s and it was just HTTP data coming downstream. 

All other system logs look fine. 

Is there anything I can check as I have quite little experience with managing dansguardian and squid. 

I am probably being over paranoid but any help will be appreciated :)

Thanks!

---

### Post by bodhi.zazen on 2010-12-16
How are you using Dansguardian and squid ? What kind of firewall are you running ? Why does anyone outside your LAN have access to either Dansguardian or Squid ? What makes you think you have any any way been compromised ? Have system files been altered ?

I suggest you read the security stickies and learn about snort and OSSEC.

Unless the problem recurs I would not worry about it, could have need any number of things. If the problem recurs we need more information.

---

### Post by crashed111 on 2010-12-16
Hi

Thanks for your reply 

I agree the issue for now probably should be left all traffic now seems fine and it was probably a one off. Examining TCP traces whilst browsing through the proxy show nothing abnormal now.

---

### Post by nitrogensixteen on 2011-01-03
Do you have payload caps or just headers?

Just because there were only ACK packets present in the stream does not mean data egress was not in progress. An attacker could have used a an ACK tunnel out of your machine by encapsulating a connectionless transport in an encrypted data stream in the ACK packet payloads.

---

### Post by HermanAB on 2011-01-03
Howdy,

A misconfigured Squid-cache can be used as a proxy by a hacker to anonimize his traffic and make it look like it is you.  You have to add some firewall rules to your machine if you are using Squid, so install UFW.

---

