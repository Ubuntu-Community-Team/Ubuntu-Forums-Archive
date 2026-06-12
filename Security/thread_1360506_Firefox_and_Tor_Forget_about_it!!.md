---
title: "Firefox and Tor? Forget about it!!"
date: 2009-12-21
forum: Security
---

### Post by njiii on 2009-12-21
With mounting security problems I'm finally saying, &quot;Firefox and Tor? Forget about it!!  &quot;  [http://secunia.com/advisories/37699/](http://secunia.com/advisories/37699/)  I want something less bloated like Dillo:  [http://www.dillo.org](http://www.dillo.org).  I haven't tried the old & outdated distro called ELE:  [http://northernsecurity.net/download/ele/](http://northernsecurity.net/download/ele/)  &quot;What is ELE? ELE is a bootable Live CD Linux distribution with focus on privacy related software. It is based on Damn Small Linux and aims to be (obviously) as small as possible. The first release was 65M, the current one 61M.  What does it include? Irssi, Gaim, Dillo, Firefox, SSH, VNCviewer, Xpdf, most of the standard Linux apps like wget and vi. It uses the Fluxbox window manager. Everything, except VNCviewer at the moment, passes thrugh Tor. When using Dillo or Firefox scrubbing is done by Privoxy and the Google search engine has been replaced by Scroogle.&quot;  but it sounds sweet. I've decided to go in this direction, using Dillo and Privoxy on a personally rolled together Linux LiveCD or USB. I'll try basing it off of Damn Small Linux  [http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)  first to see how well it works.  When using Firefox and Torbutton* along with Noscript* and Privoxy* (or other extensions), It feels like I'm riding on an elephant or whale of a creature who is open to anything with its seedy downtown brothel breath fogging up my glasses. Firefox doesn't feel safe to use anymore, especially in a tor environment where hostile injections are a growing concern. (* No offense to Torbutton, Noscript and Privoxy developers you make fine software and I'll continue to use Privoxy with another browser, but how many more combinations will we continue to need to plug Firefox's issues with tor usage and how many soft spots could be considered possible or future vectors in each piece we plaster on top?)  Please tell me what you think of all of this and whether or not this is a proper direction to go on or if Dillo's audience is limited and doesn't receive enough testing to warrant switching to Dillo.  Attention: The ELE distro mentioned is old and the tor version probably won't work, I mentioned it as a motivational tool towards where I am headed in my tor usage, away from Firefox and extensions!  Why are the paragraphs missing from my post? It shouldn't appear jumbled like that, sorry.

---

### Post by bodhi.zazen on 2009-12-21
What is it you are trying to accomplish ?

Normally I do not think of TOR as a part of security, normally I think of it as privacy.

I do not think TOR helps with the security problem you linked.

---

### Post by lovinglinux on 2009-12-21
I'm not a security expert, but here are my thoughts...

> **njiii said:**
> With mounting security problems I'm finally saying, &quot;Firefox and Tor? Forget about it!!  &quot;  [http://secunia.com/advisories/37699/](http://secunia.com/advisories/37699/)  

Don't fool yourself thinking that switching browsers will solve all security problems. Vulnerability reports like that are part of the game and Mozilla should probably fix those soon. If you are worried about such reports, you should use Apparmor to limit what Firefox can do on your system. As far as I know, this is the only way to avoid zero-day attacks. There is [very good Apparmor tutorial](http://ubuntuforums.org/showthread.php?t=1008906) from bodhi.zazen in the forums. 

> **njiii said:**
> I want something less bloated like Dillo:

I personally don't think Firefox is bloated. Besides, there are several features, tweaks and extensions to enhance the interface to your liking. I never used Dillo.

> **njiii said:**
> Everything, except VNCviewer at the moment, passes thrugh Tor.

I never really used TOR. I tried it once, but there are several things you cannot do, to avoid the problems you described, and TOR has it's own security/privacy issues. So it's a NO GO for me. BTW, stay away form VNC, unless you tunnel it through a secure ssh connection.

NOTE: "at the moment" means 2005!

> **njiii said:**
> When using Firefox and Torbutton* along with Noscript* and Privoxy* (or other extensions), It feels like I'm riding on an elephant or whale of a creature who is open to anything with its seedy downtown brothel breath fogging up my glasses. Firefox doesn't feel safe to use anymore, especially in a tor environment where hostile injections are a growing concern.

Sorry, but that sounds like FUD to me. As bodhi.zazen already said, TOR is for privacy, not security. If you are so worried about Firefox security issues, than don't install any third-party add-ons, except for NoScript or other security related extensions and use Apparmor as already explained. If privacy is what's bothering you, then perhaps you should consider using a reliable and paid VPN service instead of TOR. See [TOR weknesses](http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29#Weaknesses).

> **njiii said:**
> (* No offense to Torbutton, Noscript and Privoxy developers you make fine software and I'll continue to use Privoxy with another browser, but how many more combinations will we continue to need to plug Firefox's issues with tor usage and how many soft spots could be considered possible or future vectors in each piece we plaster on top?)

Again...Apparmor. You will never be free of zero-day attacks, no matter which browser or distro you use.

> **njiii said:**
> Attention: The ELE distro mentioned is old and the tor version probably won't work, I mentioned it as a motivational tool towards where I am headed in my tor usage, away from Firefox and extensions! 

As far as I can check, the last update was in 2005. So basically you are backing up your "Armageddon" thread, by copying and pasting the home page of a distro that is out-dated by 5 years and is not even included in the DistroWatch database? Are you serious?

Sorry if I'm being rude, but you have created a thread with a title and information that basically tells other users to stay away from Firefox and TOR, basing it on information that is outdated and unreliable. Your post is alarmist, it's FUD. Perhaps if you weren't so categoric about how bad Firefox is in terms of security I wouldn't be so blunt. But I couldn't let those pass. Sorry.

---

### Post by sliketymo on 2009-12-21
Sounds like a little paranoidification has set in on the poor OP.Might be best to just stay away from that un-safe internet thang.

---

### Post by BkkBonanza on 2009-12-21
paranoidification? You mean paranoia. 
Yep. I have several friends who caught that bug until it wore them down.

---

### Post by lovinglinux on 2009-12-21
> **sliketymo said:**
> Sounds like a little paranoidification has set in on the poor OP.Might be best to just stay away from that un-safe internet thang.

Sounds like a bot. Take a look at the other threads from the same user.

---

### Post by njiii on 2009-12-21
"As far as I can check, the last update was in 2005. So basically you are backing up your "Armageddon" thread, by copying and pasting the home page of a distro that is out-dated by 5 years and is not even included in the DistroWatch database? Are you serious?" 

I posted knowing most people don't read entire posts. My 1st post ended:

** "Attention: The ELE distro mentioned is old and the tor version probably won't work, I mentioned it as a motivational tool towards where I am headed in my tor usage, away from Firefox and extensions! Why are the paragraphs missing from my post? It shouldn't appear jumbled like that, sorry." Try reading it again if you need to. **

"Sounds like a bot. Take a look at the other threads from the same user." 

Nice try at censorship or slander, I'm not a bot.

---

### Post by lovinglinux on 2009-12-22
> **njiii said:**
> Nice try at censorship or slander, I'm not a bot.

At least we know now that you are not a bot. You would be surprised with what they can do. Anyway, I wasn't trying to censorship or slender you, but your posts have a pattern that are at least suspicious. You are a new user that don't request support, don't post on other threads and create more than one thread with the same line of subject. The subject is always security related and sort of catastrophic, with references that are not the most reliable ones and with titles and passages that are sensationalist:

> Xtremely Evil Linux Virus/Trojan?

> Every computer hackable by Radio Freq?

> Firefox and Tor? Forget about it!!

> It feels like I'm riding on an elephant or whale of a creature who is open to anything with its seedy downtown brothel breath fogging up my glasses. Firefox doesn't feel safe to use anymore, especially in a tor environment where hostile injections are a growing concern.

Anyway, I'm sorry if I offended you. That wasn't my intention. Welcome to the community and good luck with your security experiments.

---

