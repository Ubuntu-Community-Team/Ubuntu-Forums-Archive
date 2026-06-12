---
title: "Is Internet Surfing Safe? - Losing Grip"
date: 2014-09-27
forum: The Cafe
---

### Post by Quarkrad on 2014-09-27
I've been trying to keep up with the Shellshock issue mainly on this forum and others but admit I'm starting to lose grip on my personal risk; i.e. a layperson who uses 14.04 as a Desktop mainly for Surfing and email.  I get the impression the main worry is in the SERVER environment with remote SSH use but I'm probably wrong.  I have read on an Apple site a recommendation to stop all internet Banking activity (and general 'buying' on the internet) - I assume this is because some web sites use security protocols during the transaction stage.  I am updating all the time and am up to date - following one of the Security threads, my Bash is  4.3-7ubuntu1.3.  However, as a Desktop user, am I safe to do internet Banking and financial transactions (e.g. buying things using credit cards/paypal)?

---

### Post by TheFu on 2014-09-27
Your question is similar to whether it is safe to cross a busy street or not.

I will say that using Ubuntu is safer than doing it in an alternative way, but I still boot into a liveCD, as recommended by Brian Krebbs, to do any financial banking/broker logins. I don't use paypal - too many flaws in that system for me.  Buying stuff online I use 1 credit card just for that purpose and only from reputable sites - almost always.  About once a year, I'll take a chance on an unheard company purchase online.

The recent bash issue doesn't matter to users who don't have any servers running or don't allow other people access to their systems.  OTOH, it isn't like patching is hard.

Being paranoid is good. "THEY" aren't out to get YOU, but "THEY" are out to get everyone online who makes it easy to get. Stay patched and stay on supported releases.

BTW, you know that HTTPS is a house of cards and that DNS is the foundation. People screw with their DNS without understanding how important it is to all secure connections online. An untrustworthy DNS can break all HTTPS security 100%.  In many parts of the world, the local dictator runs the internet, DNS, and certificate signing authority. That means they pown almost every 'secured' connection online.

---

### Post by Quarkrad on 2014-09-27
Thank you - my ISP is TalkTalk (DNS wise) although I have recently switched to OpenDNS.  However, re your comment about DNS understanding (mine is very little) would you say OpenDNS is a resonable service to port through?

---

### Post by TheFu on 2014-09-27
[http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/](http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/) explains the liveCD for banking.
Brian Krebs was at the Washington Post for many years, but has gone out on his own to do the sorts of in depth stories that makes my skin crawl. Interesting AND accurate reading.  
Also this week on NOVA, they did a story about hackers enough to scare an average person into never connecting their computers to a network again.  Frontline has done something like that previously.  pbs.org has those videos. Should be available worldwide.

---

### Post by buzzingrobot on 2014-09-27
We have to trust/assume that those with the most to lose will be quick to patch their systems. Mainstream media are jumping on this because Bash is so widely used.  It's that angle that makes it mainstream news. Exploitable bugs are found and patched all the time and most of us don't know it. 

Increased media attention, though, does not necessarily equate to increased risk.

At least all the attention means corporate managers will probably think to ping IT to make sure they're doing their job.

---

### Post by 3rdalbum on 2014-10-01
The threat has been massively overstated - early media reports said that all Android phones were vulnerable (they don't use Bash so of course they are not vulnerable).

If you continued to use the internet during Heartbleed, then you should be continuing to use the internet during Shellshock. It's mostly patched now, and the risk is to servers, not desktop users. Heartbleed was worse than Shellshock.

---

### Post by Bucky Ball on 2014-10-01
```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

That should do it. And this:

> **3rdalbum said:**
> The threat has been massively overstated - early media reports said that all Android phones were vulnerable (they don't use Bash so of course they are not vulnerable).

If you continued to use the internet during Heartbleed, then you should be continuing to use the internet during Shellshock. It's mostly patched now, and the risk is to servers, not desktop users. Heartbleed was worse than Shellshock.

---

### Post by help_me2 on 2014-10-02
The threat is more theoretical than practical. No worries, keep surfing.

---

### Post by bashiergui on 2014-10-05
[FONT=UICTFontTextStyleBody]Yes with the media running around yelling "doomsday" it would be nice to have a reality check. As an end user of a desktop distro, all you need to do is apply updates as they're released. It's really that simple.
[/FONT][FONT=UICTFontTextStyleBody]
The very real high risk is to web servers using cgi web applications. But since you said you don't have one, then you can ignore this risk. The only way it affects you as an end user is you can never know whether the web page you're using is patched. All you can do is use a credit card instead of a debit card so that you're not liable for fraud (in the US anyway). You can use different passwords on all sites. Perhaps cycle your passwords every 90 days as a preemptive measure. But beyond that, you have no control over external websites, so there's no point in worrying
[/FONT][FONT=UICTFontTextStyleBody]
This is a nice hyperbole-free discussion of the risk
[/FONT][FONT=UICTFontTextStyleBody][http://www.citon.com/shellshock-vulnerability-real-risks-with-a-side-of-hyperbole/](http://www.citon.com/shellshock-vulnerability-real-risks-with-a-side-of-hyperbole/)[/FONT]
[FONT=UICTFontTextStyleBody]
> the threat is more theoretical than practical It is both theoretical and practical. It is a very real threat *to web servers with cgi apps.* There are malicious bots actively scanning the internet owning servers they find vulnerable. *Theoretically* you could find a way to exploit everything that calls bash at some level. That amounts to a large theoretical risk that affects developers/ maintainers of apps and servers using bash. Again, you're not doing that so *you* don't have to worry. [/FONT]
[FONT=UICTFontTextStyleBody]
This is a nice discussion of the theoretical issues that should worry app and sever owners, but not you as a desktop user:[/FONT]
[FONT=UICTFontTextStyleBody][URL="http://blog.erratasec.com/2014/09/bash-bug-as-big-as-heartbleed.html"]
http://blog.erratasec.com/2014/09/bash-bug-as-big-as-heartbleed.html[/URL][/FONT]

---

### Post by Linuxratty on 2014-10-05
> **3rdalbum said:**
> The threat has been massively overstated - 

As is always the case..People are still going on and on about it in the media flaunting their ignorance and/or vying for click bait. Over at Linux Internationals,we fixed it on our machines **the day after** the announcement was made. ):P

---

### Post by irv on 2014-10-06
Remember Target and now Home Depot? This was in store hacking. Just before this happen at Home Depot I made a purchase using my card but nothing happen. Now last week I made a large purchase from them again (new carpet) and went to pay for it at one of their stores. Not only did they fix there problem, but they replaced all there card reader. But to be on the safe side, I had my bank on line while we did the transaction. I was over my limit so I had the back raise it, and then lower it back down again.
Any time I make a purchase online or off, if it is going to be a large one I call my bank. Keep your limits low on any card you can always call them and let them know when you are going to need to up it.
I also recommend using an online bank like Paypal, it reduces the chance of you losing money.
By the way I have been doing this for years and do online banking and pay all my bills online and have never had one problem.
My son had his card number stolen over the telephone while ordering a news paper.

---

