---
title: "Explain Threat Please"
date: 2010-03-27
forum: Security
---

### Post by derekeverett on 2010-03-27
Let me begin by saying I understand little about Networking and Computer security.

I work in Ubuntu most nights these days, but I boot into Win7 on occasion as was the case tonight.

I was in Windows no more than 10 minutes when this Norton message popped up. I get these in Windows all the time. What does this mean? Is this just google collecting information?

Regardless, how is Linux "safer" considering Firefox seems to be part of the problem here?

For all I know this is just Norton making a mountain out of a molehill to justify the $75 I throw them every year. But if someone could explain some of this that would be great.

I am really curious. Thanks.

---

### Post by HermanAB on 2010-03-27
Well, I would not classify Google Analytics as an exploit, but it is an annoyance.  You can block it in your \windows\system32\etc\hosts file if you want.

The reason Linux is more secure is complicated.  One reason is that with Linux one always knows what services are active and the listeners are documented.  On Windows, there are multiple undocumented listeners (especially in XP) and these listeners can sometimes be exploited.  That is why you need to hide a Windows box behind a Linux based firewall device.  Linux doesn't need a firewall device (otherwise it will be an unending chain - every firewall will need another firewall).

Firefox does have some security issues, but in order to successfully exploit something, the malicious script would still need to ask for super user permission.  On Windows, it is very easy to craft a script to escalate privileges and do things without asking permission.

One day when Cisco starts to sell firewall boxes that run Windows, that is when Windows will finally be secure - but don't hold your breath.

---

### Post by derekeverett on 2010-03-27
> **HermanAB said:**
> 

Firefox does have some security issues, but in order to successfully exploit something, the malicious script would still need to ask for super user permission.  On Windows, it is very easy to craft a script to escalate privileges and do things without asking permission.


Is this part of what Norton does? Help to prevent such scripts from executing?

---

### Post by unspawn on 2010-03-27
> **HermanAB said:**
> Well, I would not classify Google Analytics as an exploit, but it is an annoyance.  You can block it in your \windows\system32\etc\hosts file if you want.
Read the URI again. Now notice the host name may start with "google.analytics.com." but the domain name ends in .*.info. Contamination of major advertising services, including usage of seemingly innocuous domain names, has been in the news recently.

---

### Post by Kinstonian on 2010-03-27
> **HermanAB said:**
> Well, I would not classify Google Analytics as an exploit, but it is an annoyance.  You can block it in your \windows\system32\etc\hosts file if you want.

Look closer at the domain name, are you sure that's really Google Analytics?

Here are some more examples of Neosploit domain names I found by searching Google...

[COLOR="Red"]Even if you're running Linux, I still would be careful about going to any of them.[/COLOR]

```

google.analytics.com.byuigracdnjj.info
google.analytics.com.cvybexpnqhlx.info
google.analytics.com.dbvvwrkgycfa.info
google.analytics.com.dcghkoixsagu.info
google.analytics.com.dwldxeqavts.info
google.analytics.com.dygpcewrjnw.info
google.analytics.com.eliyisgtkaj.info
google.analytics.com.gopbaqvgprvh.info
google.analytics.com.hzlyaejcvmat.info
google.analytics.com.inxvwrxogrc.info
google.analytics.com.jgvsjnhmvngn.info
google.analytics.com.jklnznqvztu.info
google.analytics.com.jttyhhvcxmbz.info
google.analytics.com.kijksoeohxze.info
google.analytics.com.lsvoenxxyya.info
google.analytics.com.omvdbdcknpct.info
google.analytics.com.prtrkmxkpctw.info
google.analytics.com.pzignbfxspou.info
google.analytics.com.qlgkmytdvyjx.info
google.analytics.com.tklaxlxvedkt.info
google.analytics.com.tluaweyermg.info
google.analytics.com.uuyvsrbtpjhl.info
google.analytics.com.xkduqnxfpnfg.info
google.analytics.com.yfguydudorip.info
google.analytics.com.yggxvnwumcqv.info
google.analytics.com.yhaidebpfltr.info
google.analytics.com.zelhnalbivd.info
google.analytics.com.zugponkeqtzz.info

```

Anyone else think that's an .info TLD?

---

### Post by HermanAB on 2010-03-27
Aaah, google.crud.info 0 neat trick.

I tried a few of those in the list but they are all dead.  Got one that works?

---

### Post by Kinstonian on 2010-03-27
> **HermanAB said:**
> Aaah, google.crud.info 0 neat trick.

I tried a few of those in the list but they are all dead.  Got one that works?

It's been a while since I've been there, but you should be able to find some interesting domains [here](http://www.malwaredomainlist.com/update.php).  Have fun :)

---

### Post by ronnielsen1 on 2010-03-27
Um, didn't stay there long. I've got 2 computers hooked up to a kvm switch. I was upgrading in Ubuntu and things stopped working because of certain upgrades. So I clicked on my sons computer (Windows - I know - some of his sites don't work in linux) and I was browsing in Windows when I saw all those :-#

> It's been a while since I've been there, but you should be able to find  some interesting domains [here]("http://www.malwaredomainlist.com/update.php").   Have fun

---

### Post by OpSecShellshock on 2010-03-27
I notice your machine is the source, while the scammyscam.info page is the destination. This probably indicates one of two things:

1. This is post-infection activity and your (now-compromised) computer is checking in with the remote host, but the attempt was blocked by Symantec.

2. Your Symantec software, in addition to reactive scanning of your drives, also provides protection from known malicious web scripts before you even access the page.

I'd say 2 is most likely.

---

### Post by Kinstonian on 2010-03-27
> **ronnielsen1 said:**
> Um, didn't stay there long. I've got 2 computers hooked up to a kvm switch. I was upgrading in Ubuntu and things stopped working because of certain upgrades. So I clicked on my sons computer (Windows - I know - some of his sites don't work in linux) and I was browsing in Windows when I saw all those :-#

I don't know why someone would intentionally go to sites they know are malicious using Windows, but it doesn't matter...

I suggest you find a security forum like [Malwarebytes](http://forums.malwarebytes.org) and ask for a review.   You could check for suspicious processes (e.g. that were started at the time you browsed the site, unusual or random names, etc.), check for programs set to run when Windows loads with Autoruns, check for files that were recently created, check Windows logs for events that happened around that time, look for suspicious network connections, etc. etc.  AND use anti-malware software.  As you can see from what I listed, there is a lot more to detecting security problems than AV software.

> **OpSecShellshock said:**
> I notice your machine is the source, while the scammyscam.info page is the destination. This probably indicates one of two things:

1. This is post-infection activity and your (now-compromised) computer is checking in with the remote host, but the attempt was blocked by Symantec.

2. Your Symantec software, in addition to reactive scanning of your drives, also provides protection from known malicious web scripts before you even access the page.

I'd say 2 is most likely.

Maybe, but I'd say the first one shouldn't be ruled out just yet because he says he's getting those alerts a lot so it sounds like the malware is trying to contact that domain.

---

### Post by OpSecShellshock on 2010-03-27
Yeah, good call. I missed that the first time. Although according to a [post last month on the Avast blog]("http://blog.avast.com/2010/02/18/ads-poisoning-%E2%80%93-jsprontexi/"), the advertising platforms of Yahoo, Google, and News Corp (which make up > half of the web advertising market) have been regularly serving malicious scripts for a while now. And reading through the list of domains on that post, I see some of the ones listed above in this thread.

Special note for the sake of not freaking all of you out: these exploits won't affect those who exclusively use Linux/Firefox/ABP/NoScript. Mostly what they do is redirect to Adobe Acrobat/Reader exploits (which most Linux users probably don't have) and IE exploits. Following that, it just loads fake anti-virus, which generally imitates Windows folders and drive naming conventions (so it's more obviously fraudulent in the event of hitting a Linux desktop). However, those of you who also use Windows, or have members in your household/workplace who use Windows, should take note and pass this along.

---

### Post by CharlesA on 2010-03-27
Good catch. There's another article [here]("http://www.digitaltrends.com/computing/yahoo-fox-and-google-inadvertently-spread-malware-through-ads/"), that links to the one from Avast.

In any case: Adblock Plus ftw(with a few sites whitelisted)!

---

### Post by ronnielsen1 on 2010-03-28
> I don't know why someone would intentionally go to sites they know are  malicious using Windows, but it doesn't matter...

Technically, I didn't. It was an index of sites and since I'm not used to being in Windows, I didn't even think of it.

---

### Post by HermanAB on 2010-03-28
Cool, I tried a few of those in the malware domain list, but they don't do much in the links browser!

---

### Post by OpSecShellshock on 2010-03-28
Nah, a lot of them are probably inactive by now. Also, I'd expect that they've been set up to throw 404s or to redirect somewhere else if the referrer and/or user-agent in the headers don't give them what they're looking for. That's kind of "industry" standard at this point. Fortunately the good folks at ISecLabs have modified Wepawet to allow custom referrers to be added to queries, so if you know how people are getting there you can appear to be arriving in the same way.

(on the unfortunate side, the time it takes me to de-obfuscate the scripts is generally long enough that the thing I'm trying to find is no longer active. I've really got to stop doing that manually)

---

