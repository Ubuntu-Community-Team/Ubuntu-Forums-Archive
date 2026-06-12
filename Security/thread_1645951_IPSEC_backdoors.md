---
title: "IPSEC backdoors"
date: 2010-12-15
forum: Security
---

### Post by dino99 on 2010-12-15
[http://www.osnews.com/story/24136/_FBI_Added_Secret_Backdoors_to_OpenBSD_IPSEC_](http://www.osnews.com/story/24136/_FBI_Added_Secret_Backdoors_to_OpenBSD_IPSEC_)

---

### Post by movieman on 2010-12-15
So is there the slightest evidence of an actual, real backdoor? I could claim that Cthulhu cultists put backdoors in Windows' IPSEC implementation, would that mean that it was true?

IPSEC is a documented standard and the BSD source is open. If there's a real, actual backdoor in the real, actual code it shouldn't be hard to find.

Edit: there is the possibility of something like deliberately slowing code to make timing attacks easier, but everyone should have rewritten their crypto code to eliminate such attacks by now.

---

### Post by dino99 on 2010-12-15
> **movieman said:**
> So is there the slightest evidence of an actual, real backdoor? I could claim that Cthulhu cultists put backdoors in Windows' IPSEC implementation, would that mean that it was true?

IPSEC is a documented standard and the BSD source is open. If there's a real, actual backdoor in the real, actual code it shouldn't be hard to find.

Edit: there is the possibility of something like deliberately slowing code to make timing attacks easier, but everyone should have rewritten their crypto code to eliminate such attacks by now.

By evidence you have not spend too much time to read some usefull comments :(

---

### Post by movieman on 2010-12-15
> **dino99 said:**
> By evidence you have not spend too much time to read some usefull comments :(

Again, where's the back door?

Show me the code or this is just FUD.

---

### Post by MES5464 on 2010-12-16
[FBI accused of planting backdoor in OpenBSD IPSEC stack]("http://arstechnica.com/open-source/news/2010/12/fbi-accused-of-planting-backdoor-in-openbsd-ipsec-stack.ars")

I have one simple question, does Linux have a backdoor (for the FBI or anyone)? If it does I want to know!

---

### Post by CharlesA on 2010-12-16
> **MES5464 said:**
> [FBI accused of planting backdoor in OpenBSD IPSEC stack]("http://arstechnica.com/open-source/news/2010/12/fbi-accused-of-planting-backdoor-in-openbsd-ipsec-stack.ars")

I have one simple question, does Linux have a backdoor (for the FBI or anyone)? If it does I want to know!
Hi. There already another thread on it.

The threads have been merged.

---

### Post by cariboo on 2010-12-16
Here's some updated info on the situation:

[http://www.networkworld.com/news/2010/121610-openbsd-back-door-claim-now.html?hpg1=bn](http://www.networkworld.com/news/2010/121610-openbsd-back-door-claim-now.html?hpg1=bn)

---

### Post by psusi on 2010-12-16
It's a bunch of BS FUD.

---

### Post by KonfuseKitty on 2010-12-18
> **dino99 said:**
> [http://www.osnews.com/story/24136/_FBI_Added_Secret_Backdoors_to_OpenBSD_IPSEC_](http://www.osnews.com/story/24136/_FBI_Added_Secret_Backdoors_to_OpenBSD_IPSEC_)


How interesting, thanks for posting!


I don't think the truth or otherwise of the allegation is the most important point here. Whether true or false, it's been made clear that without a comprehensive audit, no-one can claim that any piece of open source software is secure, not even something as crucial as IPSEC. Apparently, it will now take weeks if not months to conduct the audit. This begs the question of where were the "thousands of eyes looking at open source" that were meant to make it secure?


Another thing that this case makes clear is that if the "Trojan Horse" principle is followed, then the most likely candidates to contain a backdoor would be security applications. In this instance it may or may not be IPSEC, but how about other possibilities? Bringing this to Linux, how can we be sure that SELinux, AppArmor, Iptables, ufw and similar, are not compromised? Has there ever been a thorough audit of these packages? The answer of course is no, there hasn't.


We need an entirely different approach to security, if it is to actually mean anything. A robust, simple way of whitelisting and blacklisting processes that can connect to the net, with equally robust control of how the connection is to be handled. These ideas had been poo-poo'd by the "security experts" on these very forums. In light of the allegation made against OpenBSD, one wonders where people are actually coming from. This issue won't go away.

---

### Post by OpSecShellshock on 2010-12-18
The eyes have always been on it, and there are change logs available for perusal from developers and tinkerers alike. It goes back several years, of course. There's been no evidence to serve as a foundation for any of the speculation and fear. If users of these utilities don't trust the developers, the code is open; they may conduct audits of their own, and join their own eyes to the thousands any time they wish to.

Non-technical users are always going to run up against a point where they have to take someone at their word. That's just the way it goes.

---

### Post by bodhi.zazen on 2010-12-18
> **KonfuseKitty said:**
> no-one can claim that any piece of open source software is secure.

no-one can claim that any piece of software is secure, open or closed source. This is because you can never know what would be crackers will do with the code.

I suggest you read up on the subject:

[http://www.linuxselfhelp.com/HOWTO/Secure-Programs-HOWTO/introduction.html](http://www.linuxselfhelp.com/HOWTO/Secure-Programs-HOWTO/introduction.html)

---

### Post by movieman on 2010-12-18
> **KonfuseKitty said:**
> This begs the question of where were the "thousands of eyes looking at open source" that were meant to make it secure?

First you'd have to show _THAT IT ACTUALLY WAS INSECURE_.

Crypto is particularly hard to get right, and there's precisely no actual, real evidence whatsoever that OpenBSD's IPSEC is insecure. None.

Until this is anything more than a random Internet rumor, please stop spreading FUD.

---

### Post by rookcifer on 2010-12-19
> **movieman said:**
> First you'd have to show _THAT IT ACTUALLY WAS INSECURE_.

Crypto is particularly hard to get right, and there's precisely no actual, real evidence whatsoever that OpenBSD's IPSEC is insecure. None.

Until this is anything more than a random Internet rumor, please stop spreading FUD.

Exactly.  And the guy being accused of being the "agent" has categorically denied it and even pointed out that the accuser was not even working on the project during the dates he said.  In other words, the accuser (Perry) is full of BS.

---

### Post by KonfuseKitty on 2010-12-19
Guys, I appreciate your concern but you're missing the point. Let's say that the allegation is false. That doesn't change the fact that no-one is able to claim that IPSEC is secure, without doing a comprehensive audit. And it seems a "comprehensive audit" is a rare occurrence, given as everyone relies on the "thousands of eyes watching". I just think that the attitude is rather cavalier, particularly when expressed by people who supposedly have security concerns in mind. We need independent auditors of some sort, who could routinely sign off on the most delicate parts of the system as being secure. It must be clear from this IPSEC affair that the present approach isn't enough.


You might ask "who would pay"? All I can say is there are plenty of people who would pay for the knowledge of 100% security. Take it from there.

---

### Post by OpSecShellshock on 2010-12-19
Absolute security is impossible to achieve. This is true with or without a full audit of the code. The fact remains that there is no evidence that IPSEC has been compromised at all, let alone intentionally. If it in fact were compromised, there would be some kind of evidence somewhere, especially if that had been the case for the past seventeen years. If it had been at the behest of law enforcement, then there would have been a prosecution at some point in the intervening years that used evidence gathered in that manner, and it would be on public record. Or a security researcher would have stumbled across it and mentioned something. There are very, very good minds putting security tools to the test all the time in order to see where they need improvement. There are people looking into this supposed issue right now, but it's important to understand that this is not the first time it's been checked. It's not even the second time. The thing is, it's just not a centrally organized project (and that's good).

Mostly though, there's not really any point in worrying about it. Total security and totally trusted computing simply cannot happen. All you can really do is manage specific risks. That, in fact, is what security is. Management of risks. That's the reason why security experts are so dismissive of this particular allegation. The risk is very low.

---

### Post by Objectivity on 2010-12-19
> **KonfuseKitty said:**
> Guys, I appreciate your concern but you're missing the point. Let's say that the allegation is false. That doesn't change the fact that no-one is able to claim that IPSEC is secure, without doing a comprehensive audit. And it seems a "comprehensive audit" is a rare occurrence, given as everyone relies on the "thousands of eyes watching". I just think that the attitude is rather cavalier, particularly when expressed by people who supposedly have security concerns in mind. We need independent auditors of some sort, who could routinely sign off on the most delicate parts of the system as being secure. It must be clear from this IPSEC affair that the present approach isn't enough.


You might ask "who would pay"? All I can say is there are plenty of people who would pay for the knowledge of 100% security. Take it from there.


 I was reading all the comments and thought what you wrote is SO SO SO SO SO important which IS :

 " We need independent auditors of some sort, who could routinely sign off  on the most delicate parts of the system as being secure "

  (((  independent auditors ))) ! not the one who work for ubuntu !!! or any other small or big corporations ! 
 
 Why don't you folks start one ? if you do not have any ?

 By the way, I was about to install ubuntu for the first time in my life and this was my concern too ...

[http://ubuntuforums.org/showthread.php?t=1647491&page=2](http://ubuntuforums.org/showthread.php?t=1647491&page=2)

---

### Post by cariboo on 2010-12-19
> **Objectivity said:**
> I was reading all the comments and thought what you wrote is SO SO SO SO SO important which IS :

 " We need independent auditors of some sort, who could routinely sign off  on the most delicate parts of the system as being secure "

  (((  independent auditors ))) ! not the one who work for ubuntu !!! or any other small or big corporations ! 
 
 Why don't you folks start one ? if you do not have any ?

 By the way, I was about to install ubuntu for the first time in my life and this was my concern too ...

[http://ubuntuforums.org/showthread.php?t=1647491&page=2](http://ubuntuforums.org/showthread.php?t=1647491&page=2)

I think you're a bit confused here, the majority of the software contained in any distribution is not produced by the makers of that distribution. Canonical/Ubuntu produces very little software itself compared to what is available.  Each Ubuntu release is a snapshot of the Debian testing repositories at the start of the release cycle. Debian packages programs from many sources including, the  Gnome Foundation, RedHat, Novell, Intel, AMD, IBM and many independent developers.

All distribution makers, start with the same source code, and package it, adding their own branding and make changes to to suit their needs, by the time the packages arrive on your system the code has already been seen by hundreds if not thousands of pairs of eyes.

You only have to look at the [Ubuntu Security Notices]("http://www.ubuntu.com/usn") page, to see how many security problems have been found and repaired. At the bottom of each notice the people who found the problem and fixed it are given credit for their work, you should note in most cases individuals and not corporations are the ones given the credit.

---

### Post by CharlesA on 2010-12-19
> **OpSecShellshock said:**
> 
Mostly though, there's not really any point in worrying about it. Total security and totally trusted computing simply cannot happen. All you can really do is manage specific risks. That, in fact, is what security is. Management of risks. That's the reason why security experts are so dismissive of this particular allegation. The risk is very low.

Bingo. Nothing is 100% secure. Best you can really do is lock a system down to the best of your ability and keep an eye on it.

I've seen this sort of thing pop up from time to time, and it is all FUD.

---

### Post by rookcifer on 2010-12-19
> **KonfuseKitty said:**
> Guys, I appreciate your concern but you're missing the point. Let's say that the allegation is false. That doesn't change the fact that no-one is able to claim that IPSEC is secure, without doing a comprehensive audit.

And I can't say that Barack Obama is absolutely the president of the US.  There could be a guy who looks like him or perhaps he is really a space alien from planet Zoltar.  I can't prove that he isn't from another planet.  

My point is, you can get yourself into a lot of absurdities by doubting anything and everything and *asking others* to prove a negative.  You can't prove a negative.  The onus of any claim is upon those making the claim to prove it is true, not for others to prove it is not true.  (This is part of the scientific method and is taught in any science 101 class).

Besides, you spoke of code audits.  The OpenBSD team does more routine code audits than any other open source OS out there (more than Linux).  So either they are all working for the Feds or this one guy is full of BS.  This guy making the claim didn't even point out where the flaws were and he was wrong about the dates.  If he is "in the know" why can't he even get simple details right?

>  And it seems a "comprehensive audit" is a rare occurrence, given as everyone relies on the "thousands of eyes watching". I just think that the attitude is rather cavalier, particularly when expressed by people who supposedly have security concerns in mind. 

Again, OpenBSD's entire MO is security.  That's the whole point of it!  Those guys are very anal about doing audits.  They had a record at one time of only having one code exploit found in their default distribution over a several year period.  That's pretty impressive.

> We need independent auditors of some sort, who could routinely sign off on the most delicate parts of the system as being secure. It must be clear from this IPSEC affair that the present approach isn't enough.

IPSEC, and any kind of crypto, is highly specialized.  Not just any old kernel hacker has the expertise to audit it.  The best we can do is ask independent experts in crypto to audit it.  And I am sure OpenBSD is doing just that.

---

### Post by spynappels on 2010-12-20
+1 to Rookcifer

This appears to be part of the normal FUD cycles which comes up every so often.

---

### Post by Objectivity on 2010-12-20
> **cariboo907 said:**
> I think you're a bit confused here, the majority of the software contained in any distribution is not produced by the makers of that distribution. Canonical/Ubuntu produces very little software itself compared to what is available.  Each Ubuntu release is a snapshot of the Debian testing repositories at the start of the release cycle. Debian packages programs from many sources including, the  Gnome Foundation, RedHat, Novell, Intel, AMD, IBM and many independent developers.

All distribution makers, start with the same source code, and package it, adding their own branding and make changes to to suit their needs, by the time the packages arrive on your system the code has already been seen by hundreds if not thousands of pairs of eyes.

You only have to look at the [Ubuntu Security Notices]("http://www.ubuntu.com/usn") page, to see how many security problems have been found and repaired. At the bottom of each notice the people who found the problem and fixed it are given credit for their work, you should note in most cases individuals and not corporations are the ones given the credit.

I think you are right since I am totally new to ubuntu. The more info I get the more I know what is going on. My conclusion was based on another person's thoughts.

  what you are saying is this :

Ubuntu release a snapshot of the Debian testing repositories. THE REST is done by people like me and you - ordinary people ! but the corporations.  If this is the case, even more i give credit to ubuntu as I was under the impression that most of ubuntu comes from ubuntu. 

FANTASTIC news. Tank you for the info :-({|=

---

### Post by dino99 on 2010-12-21
> **spynappels said:**
> +1 to Rookcifer

This appears to be part of the normal FUD cycles which comes up every so often.

AUDIT have come: some on the OpenBSD side have taken this alert seriously, dislike lot of laughs on this forum shotting: "FUD as usual" or/and "show us where are the bugs", ....

patience, they are coming:

[http://www.itwire.com/opinion-and-analysis/open-sauce/43995-openbsd-backdoor-claims-code-audit-begins](http://www.itwire.com/opinion-and-analysis/open-sauce/43995-openbsd-backdoor-claims-code-audit-begins)

---

### Post by rookcifer on 2010-12-21
> **dino99 said:**
> AUDIT have come: some on the OpenBSD side have taken this alert seriously, dislike lot of laughs on this forum shotting: "FUD as usual" or/and "show us where are the bugs", ....

patience, they are coming:

[http://www.itwire.com/opinion-and-analysis/open-sauce/43995-openbsd-backdoor-claims-code-audit-begins](http://www.itwire.com/opinion-and-analysis/open-sauce/43995-openbsd-backdoor-claims-code-audit-begins)

Yeah and one of the guys who found one of those bugs, has said [in his blog]("http://extendedsubset.com/?p=41") that they are not backdoors at all.

---

### Post by dino99 on 2010-12-21
> **rookcifer said:**
> Yeah and one of the guys who found one of those bugs, has said [in his blog]("http://extendedsubset.com/?p=41") that they are not backdoors at all.

of course, stay cool, quiet, no drama around, .... only big buzz ahead :)

---

### Post by spynappels on 2010-12-21
Dino99, have you actually read the link rookcifer provided?

When I referred to FUD, I was not being flippant, but why would a bug probably created by a set of circumstances created by restrictive Government interference automatically be a backdoor? There are people who take delight in spreading Fear, Uncertainty and Doubt and twisting a bug into a backdoor without any evidence is a prime example of this IMHO.

But hey, if you don't trust it, don't use it....

---

