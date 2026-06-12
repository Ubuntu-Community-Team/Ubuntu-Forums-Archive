---
title: "tork vs jap"
date: 2009-09-03
forum: Security
---

### Post by 26venger on 2009-09-03
i was wondering which does a better job of hiding your ip address jap or tork in other words which is more vulnerable?

---

### Post by bodhi.zazen on 2009-09-04
You can not really "hide" your ipaddress and if somebody wishes to find you they can.

Security through obscurity is no security at all.

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by doas777 on 2009-09-04
tork is just a kde frontend for tor, which is medium anonymous. jap looks like it could be cewl, but it is still just a research project, so no guarantees. it does look a bit new and problably offers better features, but the root node appears to be in germany, a country with laws hostile to annominity. [http://anon.inf.tu-dresden.de/dataretention_en.html](http://anon.inf.tu-dresden.de/dataretention_en.html)

I really with I2P would take off. it's the best bet. no one knows who they are talking to.

---

### Post by rookcifer on 2009-09-04
> **26venger said:**
> i was wondering which does a better job of hiding your ip address jap or tork in other words which is more vulnerable?

Tor is what I'd go with.  If you properly set Tor up, it will be practically impossible for someone on the "other end" to discover your originating IP.

---

### Post by NoctisCaelum on 2009-10-09
> **rookcifer said:**
> Tor is what I'd go with.  If you properly set Tor up, it will be practically impossible for someone on the "other end" to discover your originating IP.

how that could be possible ? we can trace it right ?

---

### Post by bodhi.zazen on 2009-10-09
> **NoctisCaelum said:**
> how that could be possible ? we can trace it right ?

No, it is not possible. If you connect to my server I can track you, period, end of discussion.

TOR makes it difficult to impossible for 3rd parities, "man in the middle", or packet sniffers to track.

If you think about it, if you request information from my server, and my server could not find you, how would you see the information you requested ?

It is a two way communication.

---

### Post by auraithx on 2009-10-09
> **bodhi.zazen said:**
> No, it is not possible. If you connect to my server I can track you, period, end of discussion.

TOR makes it difficult to impossible for 3rd parities, "man in the middle", or packet sniffers to track.

If you think about it, if you request information from my server, and my server could not find you, how would you see the information you requested ?

It is a two way communication.

I'm not sure what you mean? You can't track someone connecting to your server - all you get is the IP of the exit node their using for that specific 10min period of time.

---

### Post by ackanao on 2009-10-09
He can if you're leaking your IP and there are few other attacks available for him to expose-decloak you.

---

### Post by rookcifer on 2009-10-09
> **bodhi.zazen said:**
> No, it is not possible. If you connect to my server I can track you, period, end of discussion.

How would you do that if the person is connecting to your site via Tor?  You cannot do a "back track" on Tor.  None of the Tor nodes know which node sent the request.

Visitor ---> Tor node 1 ----> Tor node 2 ----> Tor node 3 ----> Your server

Each node is selected at random and the connection is encrypted from the visitor's machine until it hits your server.  None of the nodes can know from which IP the original request was sent from.  The exception is the exit node -- he can see everything *except* the IP that initiated the original request for the site.  

Essentially with Tor you have no privacy but you do have *anonymity*.  That's why it's not a good idea to use Tor for things like banking, etc..

In order for Tor to be compromised, each of the 3 or more nodes in the above illustration would have to be working in unison (compromised).  This is highly unlikely since each of the 3 nodes are selected at random.

---

### Post by ackanao on 2009-10-09
There are plenty of ways to decloak user of an anonymity network:

RSnake posted PoC with Java which decloaks you very easily:

[[COLOR="DarkOrange"]De-anonymizing Tor and Detecting Proxies[/COLOR]]("http://ha.ckers.org/blog/20070926/de-anonymizing-tor-and-detecting-proxies/")

Giorgio Maone have a working PoC with Flash plugin:

[[COLOR="DarkOrange"]Cross-Browser Proxy Unmasking[/COLOR]]("http://hackademix.net/2007/09/26/cross-browser-proxy-unmasking/")

it needs an update but you can check with versions prior to 9.0.124.0 of Flash plugin - you can download it from here:

[http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

*Keep in mind that there are huge number of users that still use older version of Flash plugin.*

There's a HD Moore's metasploit/decloak and Kyle's Deanonymizer;

And there are even more attack vectors that an attacker can use to decloak you.

But the thing is that all these attacks are exploiting your browser (or browser plugins) vulnerabilities and User surfing habits; We all know that when you use Tor you should disable all browser plugins but that's almost impossible because most users like to watch tube videos online. 

Just torifying your browser will not prevent these leaks - but there's a way to use every browser plugin you want and any application you want with Tor with no risk at all:

Configure Tor as a Transparent proxy - this will route all your traffic through Tor:

[[COLOR="DarkOrange"]Transparently Routing Traffic Through Tor[/COLOR]]("https://wiki.torproject.org/noreply/TheOnionRouter/TransparentProxy")

Even better, use one of the Virtual Machines pre-configured for anonymous Internet communication like JanusVM, Incognito...

[[COLOR="DarkOrange"]The Onion Router Wiki[/COLOR]]("https://wiki.torproject.org/noreply/TheOnionRouter")

This way, most, if not all of these attacks are easilly defeated.

---

### Post by rookcifer on 2009-10-10
As you said yourself, all of these attacks rely on browser "leaks" which are all well known.  They are not a weakness in Tor itself.

---

### Post by Soul-Sing on 2009-10-10
Do not use JAP, its buggy, or not working. I don't know if "Dresden" maintains this project, or another party.
There's a free and nonfree version.

Tor works fine, but gives you no anonymity....

---

### Post by auraithx on 2009-10-10
> **leoquant said:**
> 

Tor works fine, but gives you no anonymity....

[citation needed]

---

### Post by ackanao on 2009-10-10
> **leoquant said:**
> ...Tor works fine, but gives you no anonymity....

Can you elaborate this please? I'm really interested to know why you think that Tor provides no anonymity?

---

### Post by Soul-Sing on 2009-10-10
> **ackanao said:**
> Can you elaborate this please? I'm really interested to know why you think that Tor provides no anonymity?

Quote wikipedia:
The United States government, for example, has the capability to monitor any broadband Internet traffic using devices mandated by the Communications Assistance For Law Enforcement Act (CALEA) and can therefore monitor both ends of a US-based Tor connection. Tor tries to protect against traffic analysis, but Tor does not have the ability to prevent traffic confirmation (also called end-to-end correlation).

---

### Post by Soul-Sing on 2009-10-10
> **auraithx said:**
> [citation needed]

Quote wikipedia:
Steven J. Murdoch and George Danezis from University of Cambridge presented an article at the 2005 IEEE Symposium on Security and Privacy on traffic-analysis techniques that allow adversaries with only a partial view of the network to infer which nodes are being used to relay the anonymous streams. These techniques greatly reduce the anonymity provided by Tor.....

---

### Post by bodhi.zazen on 2009-10-10
Thank you [leoquant]("http://ubuntuforums.org/member.php?u=155157")

---

### Post by auraithx on 2009-10-10
> **leoquant said:**
> The United States government, for example, has the capability to monitor any broadband Internet traffic using devices mandated by the Communications Assistance For Law Enforcement Act (CALEA) and can therefore monitor both ends of a US-based Tor connection. Tor tries to protect against traffic analysis, but Tor does not have the ability to prevent traffic confirmation (also called end-to-end correlation).

Are you talking about NSA logging? If so that has no real relevance to us.

> It is the authors opinion that even though the NSA could likely trace back Tor relatively trivially, that they would not do so. There are multiple reasons for this. Keep in mind that the NSA is an intelligence agency, not a policing agency. Their goal is to gather information, especially information on foreign governments and militarys. Tor is used in embassies around the world for people to communicate information back to their home country. Tor is also likely used by spies, and for military servers. Unless you fall into one of those categories, the NSA is not likely to care about what you are using Tor for. Even if you do fall into one of those categories, the NSA is not likely to directly act on information it gathers about your communication patterns, because to do so would scare people away from Tor. As it is right now, Tor is in a way the ultimate honey pot for the NSA, and unless you are a spy, work at a foreign embassy or use Tor to set up hidden military servers, you are not the fly they are interested in attracting. And they are also not likely to destroy what is undoubtedly an invaluable source of information for them, by showing their ability to compromise Tor.
[http://www.blackopsecurity.net/wiki/index.php/ToR#NSA_logging](http://www.blackopsecurity.net/wiki/index.php/ToR#NSA_logging)

So yeah, if you're a terrorist ToR offers no anonymity (but still can be combined with private 7-node VPNS). But for a hacker trying to avoid the FBI, or a drug dealer trying to avoid the DEA, or a Chinese citizen trying to avoid it's government - ToR provides a lot of anonymity.

> Steven J. Murdoch and George Danezis from University of Cambridge presented an article at the 2005 IEEE Symposium on Security and Privacy on traffic-analysis techniques that allow adversaries with only a partial view of the network to infer which nodes are being used to relay the anonymous streams. These techniques greatly reduce the anonymity provided by Tor.....
I believe that is an entirely different attack (although your post is pretty vague). ToR is aware of this attack and is actively taking steps to stop it. I believe the method they used was by setting their bandwidth to 999999999999GB (or some other insanely high number) so that everyone on ToR would use you as a node until your bandwidth ran out. Now ToR self-checks the bandwidth by using other nodes to test how fast you relay.

---

### Post by rookcifer on 2009-10-10
> **leoquant said:**
> The United States government, for example, has the capability to monitor any broadband Internet traffic using devices mandated by the Communications Assistance For Law Enforcement Act (CALEA) and can therefore monitor both ends of a US-based Tor connection. Tor tries to protect against traffic analysis, but Tor does not have the ability to prevent traffic confirmation (also called end-to-end correlation).

That's only effective if someone is already being targeted by an organization with the technology to do the correlation.  This is not a weakness in Tor itself and Tor was never intended to defend against this sort of thing.

What I am talking about is a website owner being able to "back track" a visitor to a website.  Except for leaky browser plugins, I have seen no success stories of this being done.

---

### Post by ackanao on 2009-10-11
OK. **leoquant** and thanks for response (clarification) but this is nothing new; This is not a part of Tor's threat model - Tor was never designed to protect users from a global adversary.

I think that most of attacks on Tor network are known and well documented since Tor is a very popular "research-network" but the important question is whether these attacks are observed "in wild"? I can't find any information about that and I doubt that even Tor developers know the answer.

My personal guess is that most of these attacks are PoC attacks and that the Tor netwok had never been attacked in such a way; On the other hand, MiTM and "password harvesting" attacks do exists.

> **bodhi.zazen said:**
> You can not really "hide" your ipaddress and if somebody wishes to find you they can.

Security through obscurity is no security at all...



**bodhi.zazen**,
I don't mean to be rude but it looks to me that you really like that quote and I fail to see how that quote applies to Tor since Tor is not a security solution.

---

### Post by Rob_H on 2009-10-11
> **leoquant said:**
> Steven J. Murdoch and George Danezis from University of Cambridge presented an article at the 2005 IEEE Symposium on Security and Privacy on traffic-analysis techniques that allow adversaries with only a partial view of the network to infer which nodes are being used to relay the anonymous streams. These techniques greatly reduce the anonymity provided by Tor.....

If you're gonna quote Wikipedia, at least cite it instead of passing it off as your own. <sigh>

---

### Post by Soul-Sing on 2009-10-11
> **Rob_H said:**
> If you're gonna quote Wikipedia, at least cite it instead of passing it off as your own. <sigh>

Rob_H +1 not my intention. Posts edited.

---

### Post by bodhi.zazen on 2009-10-11
> **ackanao said:**
> OK. **leoquant** and thanks for response (clarification) but this is nothing new; This is not a part of Tor's threat model - Tor was never designed to protect users from a global adversary.

I think that most of attacks on Tor network are known and well documented since Tor is a very popular "research-network" but the important question is whether these attacks are observed "in wild"? I can't find any information about that and I doubt that even Tor developers know the answer.

My personal guess is that most of these attacks are PoC attacks and that the Tor netwok had never been attacked in such a way; On the other hand, MiTM and "password harvesting" attacks do exists.




**bodhi.zazen**,
I don't mean to be rude but it looks to me that you really like that quote and I fail to see how that quote applies to Tor since Tor is not a security solution.

First you are taking that quote out of context.

Second you are putting too much seemingly blind  faith in TOR . This is not a site for hacking and I will not post "proof of concept" scripts here.

Even the tor site cites pitfalls 

[http://www.torproject.org/download.html.en#Warning](http://www.torproject.org/download.html.en#Warning)

---

### Post by ackanao on 2009-10-11
I think that the best thing you could do is to submit your PoC scripts to Tor developers - if they represent new kind of attack, all Tor users will benefit from your report. If you already informed Tor project I think there's no harm to give us a short description of your attack.

That warning is there for reason - to inform new Tor users what Tor is and important steps you need to take if you want to use Tor correctly; These are not actual Tor network attacks but browser attacks; Issues described there are not Tor network vulnerabilities but browser/browser plugins exploits - you can't blame Tor for Flash security vulnerabilities or vulnerabilities in any other browser plugin. 

As described, you need to turn-off all browser plugins, disable cookies, and beware of MiTM attacks - this is not unique to Tor: you are equally vulnerable to these attacks whether you use Tor or not.

There are numerous whitepapers published about attacks on Tor network - I can't submit links to them but I can provide their titles; As I said most of the Tor network vulnerabilites and attacks are well known and well documented and there's nothing that suggests that the Tor network is ever comprimised in that way.

I don't think that my trust in Tor project is unfounded; And if I "really" need to trust someone I will rather believe in Tor and Tor developers than in "hyphotetical" PoC scripts...

---

