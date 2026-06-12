---
title: "Hackers hack The Linux Foundation"
date: 2011-09-11
forum: The Cafe
---

### Post by galacticaboy on 2011-09-11
[http://www.zdnet.com/blog/security/hackers-break-into-linux-foundation/9363](http://www.zdnet.com/blog/security/hackers-break-into-linux-foundation/9363)

Really, I mean come on kernel.org is still recovering. LEAVE LINUX ALONE!

---

### Post by Famicube64 on 2011-09-11
I thought Linux was InherentlySecure™. Maybe this doesn't apply to servers?

---

### Post by sffvba[e0rt on 2011-09-11
> **Famicube64 said:**
> I thought Linux was InherentlySecure™. Maybe this doesn't apply to servers?

As with any system, if a password/account gets compromised the system is compromised.  This is an unfortunate incident but one that happens daily. (We only hear about it when it is high profile sites that are compromised).


404

---

### Post by _d_ on 2011-09-11
> **Famicube64 said:**
> I thought Linux was InherentlySecure™. Maybe this doesn't apply to servers?

No OS is 100% secure, and Linux is no exception to that rule.

---

### Post by undecim on 2011-09-11
> **Famicube64 said:**
> I thought Linux was InherentlySecure™. Maybe this doesn't apply to servers?

It's no more secure than Windows servers.

*ducks*

No OS can be "Inherently Secure", because it all comes down to the admins and the user.

---

### Post by Gremlinzzz on 2011-09-11
If your computer cant be Hacked,then your not using the Internet:popcorn:

---

### Post by Oxwivi on 2011-09-11
> **undecim said:**
> It's no more secure than Windows servers.

*ducks*

No OS can be "Inherently Secure", because it all comes down to the admins and the user.
I can't say if it's more or less secure than Windows Servers, but they are two different operating system, with completely different design - their vulnerabilities can never be equal (except when it comes to social engineering*).

* Though typical Linux and Windows users may possibly pose different levels of difficulty - just sayin'. :P

---

### Post by snip3r8 on 2011-09-11
I say Microsoft did it!

But on a serious note I find this highly disturbing,why is everyone just hacking everything?

---

### Post by Dangertux on 2011-09-11
Honestly, I'm not sure it's a new thing. The "black hat" community has always done this type of thing. Whether for lulz or to make a point.

I honestly think mass media is just spending more time covering it.

---

### Post by snip3r8 on 2011-09-11
But seriously,the Linux Foundation? What did Linux ever do to deserve that? This is going too far! Has anyone claimed responsibility?

---

### Post by themarker0 on 2011-09-11
> **snip3r8 said:**
> But seriously,the Linux Foundation? What did Linux ever do to deserve that? This is going too far! Has anyone claimed responsibility?

Not as of yet, and trust me i've head my head in HF and Twitter since. Well no credible people have claimed it, little skiddies have, but they are just being stupid.

Regardless, I hope MS takes note of this. If someone is going for all the bigwigs, they are certianly a target at some point.

Noteworthy; I remember a server that was colo'd at a datacentre, that refused to install SSH, and the clients walked to the server when they needed to do things :p. Maybe Kernel.org needs to be hosted in someone's basement? :p

---

### Post by Dangertux on 2011-09-11
Personally, I would say it was done to make a statement. 

Maybe the individual involved is tired of hearing people puppet "Linux is secure". How many people in this community constantly repeat that while closing their eyes to reality.

Truth : Nothing is inherently secure. 
Truth : Linux can be compromised in much the same way Windows, BSD, OS X and Unix can.
Truth : Linux is targeted frequently in the corporate world, not so often in the home space.

Most likely, there was some 'low hanging fruit' involved in the attack.

-- Obviously weak password policies
-- Un-patched systems
-- Poorly designed web applications
-- Untrained/undertrained personnel 
-- Poor IDS/NAC/Log Analysis
-- Poorly designed firewalls / network security procedures / applications
-- Improper permissions management (in conjunction with the first point)

Not positive, since they haven't released any details, but most attacks occur because you make yourself a target.

---

### Post by 3Miro on 2011-09-11
Does anyone know what kind of attack was that? What did they attack and how?

---

### Post by snip3r8 on 2011-09-11
>  because you make yourself a target.
How did the Linux foundation make itself a target?

---

### Post by Dangertux on 2011-09-11
> **snip3r8]
How did the Linux foundation make itself a target?
[/QUOTE]

By doing any of these and an assortment of other things that can make themselves look like an "easy target"

[QUOTE=Dangertux said:**
> 
-- Obviously weak password policies
-- Un-patched systems
-- Poorly designed web applications
-- Untrained/undertrained personnel 
-- Poor IDS/NAC/Log Analysis
-- Poorly designed firewalls / network security procedures / applications
-- Improper permissions management (in conjunction with the first point)
.



[QUOTE=3Miro]
Does anyone know what kind of attack was that? What did they attack and how?
[/QUOTE]

I don't think that information has been released yet. My guess would be a combination of unpatched software and weak passwords or compromised keys.

---

### Post by snip3r8 on 2011-09-11
> Maybe the individual involved is tired of hearing people puppet "Linux  is secure". How many people in this community constantly repeat that  while closing their eyes to reality.

How do you know it was an individual?

---

### Post by Dangertux on 2011-09-11
I don't... feel free to make it plural if it makes more sense to you.

---

### Post by snip3r8 on 2011-09-11
Which one makes more sense to you? Could it just be a lone skiddie who got lucky with Linux.org and found the same vulnerabilities in the linux foundation site?

---

### Post by Gone fishing on 2011-09-11
> Truth : Nothing is inherently secure.

Not sure this is true - certainly no system is invulnerable, but I don't think we need to fall over-ourselves to say Windows servers are great. You can - make a a secure server using Linux, FreeBSD, OpenBSD etc.

It also might be easier - if you know what your doing to make a secure open-source server than a propitiatory server. I don't think the reason that Linux dominates the Web server market is because it is insecure crap.

---

### Post by Dangertux on 2011-09-11
[QUOTE=snip3r8]
Which one makes more sense to you? Could it just be a lone skiddie who  got lucky with Linux.org and found the same vulnerabilities in the linux  foundation site
[/QUOTE]

Truth of the matter is it could have been anything. I think you are underestimating the ability of an average technician or system administrator to introduce a vulnerability into even the most secure environment.

[QUOTE=Gone fishing]
Not sure this is true - certainly no system is invulnerable, but I don't  think we need to fall over-ourselves to say Windows servers are great.  You can - make a a secure server using Linux, FreeBSD, OpenBSD etc.

It also might be easier - if you know what your doing to make a secure  open-source server than a propitiatory server. I don't think the reason  that Linux dominates the Web server market is because it is insecure  crap.
[/QUOTE]

I never said it was more or less insecure than Windows or any other platform, but security is not a black and white thing. ANY "secure" system must go through a VERY rigorous process. My point is everything can be vulnerable. The truth of the matter is quite simply this. People are creative creatures by design. If you build a better can, someone is going to build a better can opener.

---

### Post by snip3r8 on 2011-09-11
If none of the usual groups have claimed responsibility yet then it could just be a lone wolf with no purpose just testing the waters.

---

### Post by 3Miro on 2011-09-11
> **Dangertux said:**
> 
Maybe the individual involved is tired of hearing people puppet "Linux is secure". How many people in this community constantly repeat that while closing their eyes to reality.


Sorry, but I don't see how a fan-boy from another OS would be annoyed enough at the Linux fan-boys and then learn enough about Linux to attack a huge server.

This is different from someone posting a "rm" command in a .deb on Gnome-looks. For the Linux Foundation to be affected they either have to drop the ball big time or someone has to be a pretty good hacker. Neither of those makes sense and thus I want more information on the type of attack before I speculate.

---

### Post by Dangertux on 2011-09-11
> **3Miro said:**
> Sorry, but I don't see how a fan-boy from another OS would be annoyed enough at the Linux fan-boys and then learn enough about Linux to attack a huge server.

This is different from someone posting a "rm" command in a .deb on Gnome-looks. For the Linux Foundation to be affected they either have to drop the ball big time or someone has to be a pretty good hacker. Neither of those makes sense and thus I want more information on the type of attack before I speculate.

It was just a spitball idea. It's likely not the case. I'm not the person who did it and I am not clairvoyant so their intentions will remain a mystery at least until they explain them.

I agree that someone dropped the ball.

---

### Post by hatalar205 on 2011-09-11
The more Linux grows, the more it becomes target.
We are growing!:)

---

### Post by snip3r8 on 2011-09-11
> **hatalar205 said:**
> The more Linux grows, the more it becomes target.
We are growing!:)
Interesting positivity there

---

### Post by cgroza on 2011-09-11
> **hatalar205 said:**
> The more Linux grows, the more it becomes target.
We are growing!:)
Linux is already big on the domain where it was targeted.

---

### Post by newbie2 on 2011-09-11
> The Linux Foundation has mailed users of the Linux.com and LinuxFoundation.org sites informing them that they discovered a security breach on 8 September which "may have compromised your username, password, email address and other information". The Foundation says that it believes the breach is connected to the security breach at kernel.org at the start of September.
[http://www.h-online.com/security/news/item/Security-breach-at-Linux-Foundation-1340733.html](http://www.h-online.com/security/news/item/Security-breach-at-Linux-Foundation-1340733.html)

---

### Post by dmoconnell on 2011-09-11
I don't think that the Linux Foundation (or kernel.org) itself is a lone target. the PlayStation Network, Citibank, as well as LastPass where all hacked recently and that's just the ones I can name of the top of my head. (and that's just the ones that are common knowledge). I've heard on the news that there is a group of hackers that are targeting well know companies merely to antagonise them. 

it could be a weak or vulnerable passkey, but I think its more likely that it was an exceptionally good hacker. 
"Never underestimate your opponent, for then you shall surely lose"

That's my conspiracy theory of the week. 
Dm

---

### Post by fdrake on 2011-09-11
people do not do such a time consuming work without gaining something... also i do not really get it why kernel.org?? isn't that an open source code? so they could not really steal any info out of it. why then? maybe they had another objective.

---

### Post by Dangertux on 2011-09-11
> **fdrake said:**
> people do not do such a time consuming work without gaining something... also i do not really get it why kernel.org?? isn't that an open source code? so they could not really steal any info out of it. why then? maybe they had another objective.

Noteriety?

---

### Post by alphacrucis2 on 2011-09-11
The article suggests that this incident was related to the kernel.org attack. I'm reading between the lines but I suspect that the same user credentials were involved. Someone with access to both sites had their password or SSH keys compromised by social engineering or other.

---

### Post by fdrake on 2011-09-11
from inside? well that's pretty big. maybe they wanted to compromise the kernel's code by bypassing the authentications certificates? that would have been a big deal.

---

### Post by oldos2er on 2011-09-11
Not a support question, moved to Community Cafe.

---

### Post by IWantFroyo on 2011-09-11
I got this email, too.

I use different passwords for all my websites, so I'm okay in that perspective. If I get a bunch of spam email, I'll just apply a few filters.

---

### Post by uRock on 2011-09-11
Threads merged.

---

### Post by alegomaster on 2011-09-11
I use the same password for each site so I have to change around 40 passwords today. :icon_frown::icon_frown:

It is somewhat good that linux got hacked. It proves that Linux is not any small fish. Plus they could probably learn from this hack so that in the future this will have a lower chance of happening.;)

---

### Post by dmoconnell on 2011-09-12
I stand by what I said earlier, that Linux is not the sole target. It very well could be linked to the many other hacks that have happened recently, or it might not be. But its to coincidental that major networks are being hacked. (and may i add that it has been in the news that a group of hacker have been behind some major hacks of major networks (like Playstation)) and it just happens that 2 huge Linux networks get hacked. I personally don't believe in coincidences.
But in any case the FBI will (who undoubtedly have been contacted) find out who's behind these two hacks
Dm

---

### Post by Nisal on 2011-09-12
hope these sites will be back online soon.

---

### Post by kagz on 2011-09-12
> **snip3r8 said:**
> But seriously,the Linux Foundation? What did Linux ever do to deserve that? This is going too far! Has anyone claimed responsibility?
why should any1 do this to our open community....what point is he/she trying 2 prove..?

---

### Post by SharkMonster on 2011-09-12
> **kagz said:**
> why should any1 do this to our open community....what point is he/she trying 2 prove..?

Maybe they hate Linux? Or they were bored?

---

### Post by whiskeylover on 2011-09-12
> **snip3r8 said:**
> But seriously,the Linux Foundation? What did Linux ever do to deserve that? This is going too far! Has anyone claimed responsibility?

What has *anyone* ever done to deserve that? No one deserves to be hacked, irrespective of what OS they use.

---

### Post by conundrumx on 2011-09-12
> **dmoconnell said:**
> ...but I think its more likely that it was an exceptionally good hacker. 
"Never underestimate your opponent, for then you shall surely lose"

That's my conspiracy theory of the week. 
Dm

Exceptionally good "hackers" don't get caught until they do something more public than the initial breach of security.  There are much more significant breaches occurring regularly at more important organizations.

Little stuff like this, when the company spots the breach in short order are compromised passwords or other blatant things that can be spotted by vigilant admins.

---

### Post by clanky on 2011-09-12
This could actually be a good thing for Linux in the end, the idea that linux is somehow magically immune to any kind of attack is incredibly harmful.

Maybe now people will start taking security seriously and not just assume that because they are using Linux they will be OK.

---

### Post by josephmills on 2011-09-13
security of ones computer/server (toaster)  is hard work it seems I keep on seeing all these websites that have lots and lots of exploits and vulnerability. With all the sites out there that promote this kinda acts then there are going to be people that try to stand out. I could be 100% wrong. but just take a look 

[http://www.exploit-db.com/](http://www.exploit-db.com/)
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)
[http://www.securityfocus.com/bid/48259](http://www.securityfocus.com/bid/48259)
[http://www.rapid7.com/products/vulnerability-management.jsp](http://www.rapid7.com/products/vulnerability-management.jsp)
[http://www.openvas.org/sources-for-security-issues-information.html](http://www.openvas.org/sources-for-security-issues-information.html)
[http://www.tenable.com/products/nessus/documentation/scanning-with-credentials](http://www.tenable.com/products/nessus/documentation/scanning-with-credentials)
[http://www.seepurity.com/?p=250](http://www.seepurity.com/?p=250)
[http://www.devquotes.com/2011/06/15/php-cve-2011-2202/](http://www.devquotes.com/2011/06/15/php-cve-2011-2202/)
[http://jon.oberheide.org/](http://jon.oberheide.org/)
[https://lkml.org/](https://lkml.org/)
[http://pastebin.com/i4LFsQPW](http://pastebin.com/i4LFsQPW)
[http://www.exploit-db.com/exploits/17787/](http://www.exploit-db.com/exploits/17787/)

---

### Post by Eiji Takanaka on 2011-09-13
Maybe the much loved 'trusted repository' isn't so trustworthy after all.

---

### Post by uRock on 2011-09-13
> **Eiji Takanaka said:**
> Maybe the much loved 'trusted repository' isn't so trustworthy after all.
Why wouldn't it be?

---

### Post by Dangertux on 2011-09-13
> **uRock said:**
> Why wouldn't it be?

Well the argument could be made that the private key was compromised, however I'm sure that will be regenerated before anything is brought back online. 

So I would say it's still ok :-/

---

### Post by the kernel on 2011-09-14
I think this should be a wake-up call. Security is something the Linux community as a whole needs to increase their focus on. I think alot of people take security on Linux for granted, and when you drop your guard you can become more vulnerable. Remember, the Linux source code is out there for all to see, including hackers that have chosen the dark side. So it's important to increase threat detection, find and eliminate vulnerabilities and create software that alerts a user to a possible intrusion.

---

### Post by 3Miro on 2011-09-14
> **the kernel said:**
> I think this should be a wake-up call. Security is something the Linux community as a whole needs to increase their focus on. I think alot of people take security on Linux for granted, and when you drop your guard you can become more vulnerable. Remember, the Linux source code is out there for all to see, including hackers that have chosen the dark side. So it's important to increase threat detection, find and eliminate vulnerabilities and create software that alerts a user to a possible intrusion.

Considering how Linux is the system of choice of servers, I don't think people in the community have gotten "sloppy".

The Linux community has a much faster threat response time than any commercial software.

There is already "alert" software in the face of SELinux and AppArmor.

The Linux Foundation has not reported a security whole or issues a patch. This is not a flaw in Linux itself, the problem is that that somebody dropped the ball on the server team at the Linux Foundation.

---

### Post by Dangertux on 2011-09-14
> **the kernel said:**
> So it's important to increase threat detection, find and eliminate vulnerabilities and create software that alerts a user to a possible intrusion.

This is already available. Unfortunately all of these solutions require two things. 

1 - Someone competent to write definitions, signatures, rules or whatever the software uses to identify a threat.

2 - Someone knowledgeable to monitor the output of said solutions. In order to determine a few things. 

       - False positives
       - Automated scanners
       - APT's 

If you don't have all of these factors in place the only thing those solutions will prevent are script kiddies that don't know better and automated scanning tools. An actual attacker is an intelligent adaptive creature and requires a counterpart that is equally intelligent and adaptive on the other side.

Obviously this is both costly and largely (based on the security requirement) ignored.

---

### Post by Eiji Takanaka on 2011-09-14
I agree dangertux, it could be somewhat compared to the sniping games of  Vasily Grigoryevich Zaitsev and Major Erwin König.   Then again it could be a simple application of powdered rouge,   when analysing such things discerning ones motive and who is to gain by such actions is usually/but not always ;) a sure-fire way of whittling down potential suspects.   Then again i could just be talking **** ;)   I would suspect corporate politics to be the order of the day.  Open source will win the day though ;) p.s bloody no-script removing my paragraphing is annoying =P

---

### Post by Eiji Takanaka on 2011-09-14
P.s in response to urock, if they are doing things by the book (the penetration testers open source toolkit book) then the probability of compromise of the trusted repositories i would imagine would at the very least increase substantially being that they managed to transit and compromise 2 connected domains of the target in question. If they managed to do this it would be reasonable to speculate that their target may be the trusted repositories would it not? Just a thought anyways. I don't doubt such things have been anticipated/ and precursory measures have been put in place to prevent such actions from occuring though.

---

### Post by Eiji Takanaka on 2011-09-14
to undermine trust and confidence in a person/product is a basic tactic that has been used for time immemorial - by unscrupulous individuals/factions.

---

### Post by NMFTM on 2011-09-14
> **_d_ said:**
> No OS is 100% secure, and Linux is no exception to that rule.
Yes, but OpenBSD is [helluva good](http://en.wikipedia.org/wiki/OpenBSD#Security_and_code_auditing).
> **snip3r8 said:**
> But seriously,the Linux Foundation? What did Linux ever do to deserve that? This is going too far! Has anyone claimed responsibility?
A lot of Linux users (including many on this forum) are pretty arrogant and elitist about how great their OS of choice is and who crappy "Micro$$$oft Winblow$" is. Maybe they decided that Linux needed taken down a notch to show they're not so high and mighty.

---

### Post by Dangertux on 2011-09-14
> **Eiji Takanaka said:**
> P.s in response to urock, if they are doing things by the book (the penetration testers open source toolkit book) then the probability of compromise of the trusted repositories i would imagine would at the very least increase substantially being that they managed to transit and compromise 2 connected domains of the target in question. If they managed to do this it would be reasonable to speculate that their target may be the trusted repositories would it not? Just a thought anyways. I don't doubt such things have been anticipated/ and precursory measures have been put in place to prevent such actions from occuring though.

That book and other documentation like it is more like a set of guidelines then rules. I wouldn't count on anything.

---

### Post by xtjacob on 2011-09-22
So I'm wondering, since kernel.org is down, where can I get the latest kernel source?

---

### Post by Dangertux on 2011-09-22
> **xtjacob said:**
> So I'm wondering, since kernel.org is down, where can I get the latest kernel source?

[https://github.com/torvalds/linux](https://github.com/torvalds/linux)

---

### Post by j814wong on 2011-09-22
Someone is trying to discredit Linux with this.

---

### Post by Dangertux on 2011-09-22
> **j814wong said:**
> Someone is trying to discredit Linux with this.

I probably should just let this thread die, however who are they discrediting? The only people discredited will be those who blindly assume Linux is impenetrable. Which is and has been a false statement for a very long time (a little over 20 years).

Corporate systems get cracked all the time, most of them are NOT running Windows.

---

### Post by Eiji Takanaka on 2011-09-22
+1 j814wong

---

### Post by ClientAlive on 2011-09-25
So what really is the bottom line here? Because I need the 2.6.39 kernel source (with all the patches and up to date). Is there no other place/ way to obtain the Linux kernel?? What if they never recover? Linux dies?? C'mon now! This is nuts!!

Seriously though. Is there some other reliable source of the kernel for me?

---

### Post by ClientAlive on 2011-09-25
> **Dangertux said:**
> [https://github.com/torvalds/linux](https://github.com/torvalds/linux)


Thanks Dangertux but that site is this massive maze of stuff. I've been around and around and around on there looking for what I need. For the life of me I can't seem to find this one simple thing. Can you help?

I'll keep searching on there in the meantime.

Thx.

---

### Post by ClientAlive on 2011-09-25
I think I found it - maybe.

[https://github.com/torvalds/linux/downloads](https://github.com/torvalds/linux/downloads)

What I don't understand though is that there is all the release candidates ("-rc" whatever) and then you trace it on down the list and you see what seems like it should be the stable release, but there's no fourth number on the end. Does that mean it's the bare kernel without any patches? I've been trying to get the latest, patched, 2.6.39 kernel for over a week.

---

### Post by Dangertux on 2011-09-25
> **ClientAlive said:**
> I think I found it - maybe.

[https://github.com/torvalds/linux/downloads](https://github.com/torvalds/linux/downloads)

What I don't understand though is that there is all the release candidates ("-rc" whatever) and then you trace it on down the list and you see what seems like it should be the stable release, but there's no fourth number on the end. Does that mean it's the bare kernel without any patches? I've been trying to get the latest, patched, 2.6.39 kernel for over a week.

Because it's 2.6.39-0, what patches are you referring to? The Ubuntu patches? This kernel is not going to be a patched Ubuntu kernel , this is just the Linux kernel. The version that WAS in repos for Natty was actually 2.6.39-rc5 which still won't be the same if you download it from github.

---

### Post by ClientAlive on 2011-09-25
> **Dangertux said:**
> Because it's 2.6.39-0, what patches are you referring to? The Ubuntu patches? This kernel is not going to be a patched Ubuntu kernel , this is just the Linux kernel. The version that WAS in repos for Natty was actually 2.6.39-rc5 which still won't be the same if you download it from github.


Thanks so much for your help.

I just barely know a little bit about a lot of topics in Linux right now. I'm still learning. I know the naming/version numbering (at github site) looks different than what I've seen at kernel.org. I have read articles about the version numbering; and, I though, they say "rc" stands for "release candidtate" which is not a stable version (not something one would typically want). These articles also mention four numbers in the versioning scheme. The last two being the ones to focus on, and the fourth number being the patches that are included. If I am not mistaken, I should be looking for something like 2.6.39.xx not 2.6.39 right? I don't want to have to hunt down 40 patches and apply them myself. I thought I could get the up to date thing and just go from there. I'm I understanding this right?

FWIW, I'm building a system from the ground up and it's not any regular Linux distro per se. It's Xen with Gentoo as it's dom0. I haven't even gotten a chance to get started yet. I've been learning how for everything under the sun until recently - now I feel confident in beginning the build and I'm having difficulty getting the 'right' kernel.

---

### Post by Dangertux on 2011-09-25
> **ClientAlive said:**
> Thanks so much for your help.

I just barely know a little bit about a lot of topics in Linux right now. I'm still learning. I know the naming/version numbering (at github site) looks different than what I've seen at kernel.org. I have read articles about the version numbering; and, I though, they say "rc" stands for "release candidtate" which is not a stable version (not something one would typically want). These articles also mention four numbers in the versioning scheme. The last two being the ones to focus on, and the fourth number being the patches that are included. If I am not mistaken, I should be looking for something like 2.6.39.xx not 2.6.39 right? I don't want to have to hunt down 40 patches and apply them myself. I thought I could get the up to date thing and just go from there. I'm I understanding this right?

FWIW, I'm building a system from the ground up and it's not any regular Linux distro per se. It's Xen with Gentoo as it's dom0. I haven't even gotten a chance to get started yet. I've been learning how for everything under the sun until recently - now I feel confident in beginning the build and I'm having difficulty getting the 'right' kernel.

Right but 2.6.39 JUST came out, so there haven't really been any patches to it yet, as you can see it was just RC. So you'd be fine to use that kernel, it IS the full kernel source.

So let's say there was a security fix applied the NEXT version would be 2.6.39-1, or whatever number. Does that make more sense?

---

### Post by ClientAlive on 2011-09-25
> **Dangertux said:**
> Right but 2.6.39 JUST came out, so there haven't really been any patches to it yet, as you can see it was just RC. So you'd be fine to use that kernel, it IS the full kernel source.

So let's say there was a security fix applied the NEXT version would be 2.6.39-1, or whatever number. Does that make more sense?


Ahhh. I see. But it's not 'bleeding edge' then is it?
-------------------

Edit:

I know this thread wasn't about this but I'm trying to take a couple things into account here and I'm a little unsure of my own understanding sometimes. I read on the Xen wiki that kernels after 2.6.32 (I think) are pv-ops kernels. Meaning they have the Xen extensions right in the kernel, right out of the box. Based on that I assumed that since 2.6.39 is a later release than 2.6.32 it would also be pv-ops - but I have not seen this explicitly-stated. Then, another consideration/ factor, is I want to have the latest kernel goodies but yet very stable and not even close to bleeding edge. Picking 2.6.39 was just a guess for me.
--------------

Edit:

I guess the way I've been thinking of it is that no patches = a too early of a release to really be counted on. That if a person wanted something really stable, secure, and reliable they would look straight to the patch number. If it's been around long enough to work out the bugs, it would have patches. Do you think this is a reasonable way to look at it?

---

