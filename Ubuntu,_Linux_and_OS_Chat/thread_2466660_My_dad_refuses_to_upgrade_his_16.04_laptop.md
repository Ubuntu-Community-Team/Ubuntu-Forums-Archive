---
title: "My dad refuses to upgrade his 16.04 laptop"
date: 2021-09-02
forum: Ubuntu, Linux and OS Chat
---

### Post by salamilimos on 2021-09-02
Back in 2016, the hard drive of my dad's laptop finally gave out after 10 years of usage. The original OS of his laptop was Windows XP and his laptop is a 64-bit Dell Inspiron E1505 with 2GB RAM. So when his hard drive gave out, I installed Lubuntu 16.04 on it because Windows XP was outdated already.

Now, my dad is refusing to upgrade to 20.04 just like he refused to upgrade to 18.04. My dad's reasoning is that his laptop is working fine as is and he doesn't want to change it and also he reasons that he was safe in Windows XP despite it being unsupported, so he thinks he will be safe on Lubuntu 16.04 despite it being unsupported.

Well, I can't force him to upgrade if he doesn't want to, it's his laptop, his property. My dad mainly uses the laptop for Facebook and YouTube video watching and he doesn't do online banking at all on his laptop because he's old fashioned that way.

How safe is he?

---

### Post by hk42 on 2021-09-02
IMHO the main reason to upgrade in Linux is to support new hardware not security.
But it is very easy to have several distributions with Grub allowing you to choose at boot.
When you replace a 10 years old HD you have room to install 5 OS :-)

---

### Post by Dennis N on 2021-09-02
It would be safer if he maintains an up-to-date web browser. For Firefox, download and manually install the latest Firefox version from Mozilla.org - it is self-updating.

---

### Post by grahammechanical on 2021-09-02
I find that web sites are taking longer to load. Yes, my machine is old but It runs Ubuntu 20.04 without any difficulty. Yes, web sites embed advertising. They also link to tracking and analytical sites. It is natural for a web site owner to want to know how many people are visiting the site and what pages or products they are clicking on. Some web sites, in my opinion, take this too far and even go so far as selling data harvested by trackers and analytics.

How safe are the sites that do this? It is safe to stand on the edge of a cliff until we fall off. Then we are no longer safe. This is all part of the complexities of life.

It is a false sense of security to think that the main reason for upgrading is to get hardware drivers for newer hardware. There are security fixes that are applied when we update/upgrade. This will no longer happen with 16.04.

See Ubuntu's Weekly Newsletter for this week. Scroll down to the heading Updates and Security for 18.04, 20.04 and 21.04. Six months ago 16.04 would have been included in that heading.

[https://ubuntuforums.org/showthread.php?t=2466660](https://ubuntuforums.org/showthread.php?t=2466660)

Regards

---

### Post by TheFu on 2021-09-02
Has his home router been properly maintained?  If it hasn't been patched in the last month, that answer is no.
Security is about layered protection.  Email clients and web browsers skip the network-based protections, so that system could be a ticking timebomb.  

Does he have backups? What happens if the HDD fails?  Will he lose everything? If so, what then?
When he goes onto the internet, he can use a live-boot flash drive with a patched release. Probably would want to setup a persistent Lubuntu 20.04 with mkusb for him. Then he can become comfortable using the new OS without risking his current OS.

Does he have a DNS blocker on the network?  Something like a pihole that gets updated lists of "bad" web sites on the internet?
Does he have an updated ad-blocker for his browser?
Is he prone to downloading anything?

Every computer will eventually fail.  There will be software issues, lazy bits on the HDD, and hardware failures.
All kernels have zero-day, full access, bugs.  With a supported release, those get fixed and we are notified a few weeks later. With an unsupported release, those never get fixed.  This is the primary reason why home routers that aren't actively maintained and patched monthly are generally not very secure.  A home router with a remote access bug (they've all had them), will become a launch point to access the rest of the home network.  Nobody is out to get HIM, specifically.  They have scripts that search for weaknesses and get inside all the systems in that way.

You know, he can sign up for ESM for free for 1 system and continue to get patched.  [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)  I think formal ubuntu members can have 50 systems supported for free.  That will get him to 20.04 April.

---

### Post by monkeybrain20122 on 2021-09-02
Well how about installing 20.04 in an external hd and persuade your dad to boot off it once in a while until he is comfortable and then replace 16.04 with that? Don't do "upgrade", always backup data and do a fresh install, otherwise you will be blamed if something goes wrong (or just clone the system in the external drive, wipe the internal drive and then restore system in the external to the internal hd)

---

### Post by GhX6GZMB on 2021-09-02
Leave your dad's machine alone. It works perfectly, and with his use of it, I see no perils.
An upgrade would lead to a major shift to LXQt, which would create further problems/frictions.

I'm worried more about you. You seem to suffer from chronic "upgradeitis", which is not a good thing. There's no need to change a winning team. I run Lubuntu 20.04 LTS and sleep well at night. The "Must upgrade, must upgrade, must upgrade to 21.10" fever has never caught on with me.

Cheers.

---

### Post by TheFu on 2021-09-02
> **ml9104 said:**
> Leave your dad's machine alone. It works perfectly, and with his use of it, I see no perils. 

Good advice for a system that **isn't on any network**.

---

### Post by guiverc on 2021-09-02
The oldest Lubuntu system I'd dare to run online with be Lubuntu 18.04 LTS.  Even though the desktop itself is EOL (*the oldest supported release for Lubuntu is currently Lubuntu 20.04 LTS*), at least the `firefox` browser is supported/patched as it's from the 'main' repository being common with Ubuntu 18.04 LTS Desktop - ie. 5 years of support for packages from 'main'.

I in fact still have a thinkpad t43 that uses Lubuntu 18.04 LTS; it however isn't *amd64 (64-bit**) *so the only upgrade I have possible for that is replacing it with Debian (*which runs; I used the box to pre-release QA-test Debian 10/Buster & 11/Bullseye and had no issues*) but I haven't *felt* the need as I don't use it for anything online.

If he wants the LXDE desktop; you can run that on 20.04 too. I've read support issues where users have difficulty (adding LXDE to 20.04 server), but the little testing I did was adding LXDE to a Lubuntu 20.04 LTS system and I encountered no issues.

I wouldn't want to stick on 16.04 if you're online, and my preference would be 20.04 with LXDE if he wants the same desktop (*it won't be supported by Lubuntu; LXDE is supported in general Ubuntu areas though*). At a minimum though I'd use Lubuntu 18.04 LTS (*no longer a Lubuntu supported product so it's generic Ubuntu support anyway*).

---

### Post by vo-nguyen on 2021-10-30
That laptop is probably 32 bit. Ubuntu dropped 32 bit since 18.04. You could try your luck copying Debian testing 32 bit libraries, but I wouldn't recommend it.

---

### Post by lammert-nijhof on 2021-11-11
How to keep 16.04 and 14.04 somewhat longer secure :)

I subscribed to the free Extended Security Maintenance (ESM), which is intended for companies, but is free for everybody for max 3 PCs. Just google and register for the ESM service on the Ubuntu web site. 
I still use Ubuntu 16.04 ESM in a Virtual Machine and I use it exclusively for Banking and PayPal. To keep my applications secure, I replaced LibreOffice and Firefox by the latest snaps. 

I intend to use 16.04 till the end of the ESM in Apr 2026 :)

---

### Post by Tadaen_Sylvermane on 2021-11-11
One thing of note. While "security by obscurity" shouldn't ever be a security model to follow it does have some effect. As such that 16.04 is not nearly as dangerous as say an old version of Windows.

My dad is the same way. He has a Mac that has been out of support for 5+ years. "It's working fine so why change it!" is his view. Can't blame him. But I think the average person regardless of age doesn't realize the danger of that type of thinking.

---

### Post by QIII on 2021-11-11
> **hk42 said:**
> IMHO the main reason to upgrade in Linux is to support new hardware not security.

Remind me never to take security advice from you.  Forgive me, but this is the sort of absolute nonsense that gives us an internet full of bots.

> One thing of note. While "security by obscurity" shouldn't ever be a security model to follow it does have some effect. 

No, it doesn't.  Linux is not obscure.  The fact that it is the infrastructure that runs the internet means that it is not at all obscure to those who are interested in mayhem.

Just some advice for everyone:  If you are not under an ESM program or do not have a current, patched, up-to-date OS -- Linux, Windows, Apple, etc -- do everyone a favor and disconnect from the web.  You're the problem.

For the OP:  I would ask that you discuss with your dad the fact that danger he poses to everyone else far outweighs his desire to not have to trouble himself.

---

### Post by hk42 on 2021-11-12
> **QIII said:**
> 
For the OP:  I would ask that you discuss with your dad the fact that danger he poses to everyone else far outweighs his desire to not have to trouble himself.
So you mean that an old computer with an old OS is a critical risk for all the brand new ones fully up to date with all their bells and whistles.
Do you sell computers or OS's for a living ?

---

### Post by T6&amp;sfpER35% on 2021-11-12
> So you mean that an old computer with an old OS is a critical risk for all the brand new ones fully up to date with all their bells and whistles.
yes... (one doesn't have to have a brand new one with all the bells and whistles, an OLD one , that's up to date , is all good)
> Do you sell computers or OS's for a living ?

what's that got to do with having commom sense?

---

### Post by TheFu on 2021-11-12
Does everyone realize the OP hasn't posted since the initial post #0 2 months ago and hasn't been back since then?

---

### Post by QIII on 2021-11-12
> **hk42 said:**
> So you mean that an old computer with an old OS is a critical risk for all the brand new ones fully up to date with all their bells and whistles.

Yes.  Sometimes obliquely, but yes.  For instance:  10k computers with old, unpatched OSes joined as a bot farm causing a DDoS attack on a critical piece of infrastructure or an important site.  Bots spreading ransomware:  Is your machine updated with all the bells and whistles?  Are you *sure*?  Are you absolutely sure that every move you make on the web is hygienic from a safety and security viewpoint? The "magically bulletproof" myth applied to Linux is just that:  a myth.

> Do you sell computers or OS's for a living ?

No.  Appropriate security practices do not require new machines.  Furthermore, selling Ubuntu at $0 per unit would require a lot of effort to make up for by volume.

Please do not use the Ubuntu Forums to spread unwise and misguided security advice.  


And TheFu's observation is a good one, but this is in a chat area so it's fair game.

---

### Post by Tadaen_Sylvermane on 2021-11-12
> [COLOR=#000000]No, it doesn't. Linux is not obscure. The fact that it is the infrastructure that runs the internet means that it is not at all obscure to those who are interested in mayhem.

I guess I assumed that services would be targeted, not Linux in general. As such the main targets would be things that the average home user doesn't have or even know about therefore the vulnerabilities are less targeted. Any malware I'd assume would also be targeted at services that again the average user does not have the majority of the time? I wasn't claiming it's a good idea, but not as bad as it could be. Am I incorrect in this line of thought?[/COLOR]

---

### Post by DuckHook on 2021-11-12
As an extension of QIII's comments:

The main reason that Linux experiences less malware has little to do with its inherent robustness as an OS; it has far more to do with the fact that Linux users tend to be geeks and therefore are more security conscious to start with. The median Linux user is simply safer and better informed.

This advantage has traditionally kept the Linux ecosystem tighter and cleaner than proprietary ones. The benefits are: fewer bot farms, smaller attack surfaces, less demand for dangerous fluffware, better code auditing… the list is as long as my arm. These benefits are significant and far reaching.

But they are also fragile in the sense that they are dependent on Linux users continuing to practice good computing hygiene. When newbies or the misinformed drag their bad Windows habits into Linux, then say hello to Linux botfarms, c&c servers, ransomware nodes and the army of assorted nasties that have turned Windows into a malware cesspool.

I'm at the point where I no longer want foolish newbies or no&#8209;rules&#8209;for&#8209;me types piling into Linux if they insist on ignoring good practice and security hygiene. They pollute our entire ecosystem. And the two most important rules of good practice/hygiene are: never run anything EoL and update fast and furiously.

It's not that hard. Disputing this is like insisting that the earth is flat.

---

### Post by DuckHook on 2021-11-12
> **Tadaen_Sylvermane said:**
> I guess I assumed that services would be targeted, not Linux in general. As such the main targets would be things that the average home user doesn't have or even know about therefore the vulnerabilities are less targeted. Any malware I'd assume would also be targeted at services that again the average user does not have the majority of the time? I wasn't claiming it's a good idea, but not as bad as it could be. Am I incorrect in this line of thought?[/COLOR]
There are many ways to attack Linux. Services is a big one, but not the only one. The most severe threats are zero&#8209;day flaws in structural components. Thankfully, they are rare. However, not rare enough. Here's a recent one:

[https://www.theregister.com/2021/11/01/trojan_source_language_reversal_unicode/](https://www.theregister.com/2021/11/01/trojan_source_language_reversal_unicode/)

This one is especially nasty because, well, who doesn't have Unicode? It's ubiquitous. *The only thing that will solve a problem like this is an update.* Any OS built before the update will be vulnerable. Anything after the update will no longer be vulnerable. *And we still have people questioning the value of updates*???

But, in the final analysis, it's still older proven tools like supply chain poisoning, spoofing, spear phishing, etc that compromise most systems. These are not strictly services related either. Instead, they tend to have a component of socio-psychological engineering. The weakest link in most exploits is the entity between the chair and the keyboard.

---

### Post by Tadaen_Sylvermane on 2021-11-13
Thank you for that clarification. Always something to learn.

---

### Post by night_sky2 on 2021-12-02
> **ml9104 said:**
> 
I'm worried more about you. You seem to suffer from chronic "upgradeitis", which is not a good thing. There's no need to change a winning team. I run Lubuntu 20.04 LTS and sleep well at night. The "Must upgrade, must upgrade, must upgrade to 21.10" fever has never caught on with me.

The average joe should only install a LTS release anyway.

---

### Post by Shibblet on 2021-12-02
> **Dennis N said:**
> It would be safer if he maintains an up-to-date web browser. For Firefox, download and manually install the latest Firefox version from Mozilla.org - it is self-updating.

This actually presents an interesting question.  If 16.04 is no longer supported, does that mean the software center no longer gets updates?  Can you maintain a current browser with an older OS?

---

### Post by DuckHook on 2021-12-03
> **Shibblet said:**
> …If 16.04 is no longer supported, does that mean the software center no longer gets updates?
Yes, that is exactly what it means. The repository actually gets retired, is moved to archives and no longer receives updates. There is a grace period of a few days but, once missed, one cannot even upgrade from an expired version because dpkg cannot locate the repo. If you examine the details of each kernel update, there is almost always one and usually multiple CVE fixes included. That's why falling behind on updates is so dangerous: a few months of accumulated CVEs make for an installation so full of holes that a script kiddie could compromise the system.
> Can you maintain a current browser with an older OS?
Technically, yes. But since a distro like Ubuntu is a hundred times more than just a browser, then maintaining just the browser imparts one of the worst false senses of security imaginable.

Important to note that one *can* extend the life of a LTS by purchasing paid EMS support. I believe that EMS for 16.04 extends its lifetime to 2024, but I'm not sure of the details since I have never availed myself of this option.

---

### Post by Dennis N on 2021-12-03
I recommend you get the Entended Security Maintenance (ESM) offer. It is simple to enroll in. I have done it myself. There is no cost for up to 3 computers for any one user. Then the 16.04 Software Updater will continue to function normally. It gives you security updates for "5 additional years". Go to:
[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

---

### Post by night_sky2 on 2021-12-05
> **Dennis N said:**
> I recommend you get the Entended Security  Maintenance (ESM) offer. It is simple to enroll in. I have done it  myself. There is no cost for up to 3 computers for any one user. Then  the 16.04 Software Updater will continue to function normally. It gives  you security updates for "5 additional years". Go to:
[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

Yep. Ubuntu 16.04 has extended support up to 2026. That OS is pretty much safe from major vulnerabilities as it receives security patches through updates. I don't see any problem in using a system that is still actively maintained. You only have to allow Extended Security Maintenance (ESM) and  it's free for individual users. 

All the people who claim his dad ''absolutely'' needs to upgrade to a newer version are dead wrong.

---

### Post by Shibblet on 2021-12-06
> **DuckHook said:**
> Technically, yes. But since a distro like Ubuntu is a hundred times more than just a browser, then maintaining just the browser imparts one of the worst false senses of security imaginable.

It would also seem more difficult to maintain that browser without having regular updates in the repositories.  Downloading .DEB's and installing "sh" in the terminal, doesn't seem conducive to just letting the package manager take care of it.

> **DuckHook said:**
> Important to note that one *can* extend the life of a LTS by purchasing paid EMS support. I believe that EMS for 16.04 extends its lifetime to 2024, but I'm not sure of the details since I have never availed myself of this option.

I've heard you can do that... but it seems that's more of an issue for places that have a LOT of computers that need to be updated properly.  It just seems more simple to upgrade the OS for a personal computer.

If your dad is anything like mine, he doesn't want to upgrade, because he thinks he'll have to learn it all over again.  He's got it where he likes it, so leave it alone.  ;-)

In our current area, all of the cable companies are no longer supporting television.  The only way to get Cable TV is to use one of the satellite providers, such as Dish or Direct.  All of the other options are now gone.  The other two companies only support internet now.  [URL="https://www.adn.com/business-economy/2021/12/02/gci-says-to-get-with-the-times-it-needs-to-drop-its-cable-tv-platform-in-favor-of-streaming-some-customers-arent-pleased/"]https://www.adn.com/business-economy/2021/12/02/gci-says-to-get-with-the-times-it-needs-to-drop-its-cable-tv-platform-in-favor-of-streaming-some-customers-arent-pleased/
[/URL]
My father cannot wrap his head around this concept.  He doesn't want Hulu Live or Youtube TV, because he doesn't want to learn anything new.  He also doesn't want anyone to come hook up a satellite dish on his house...  He's about to learn a hard lesson...

---

### Post by night_sky2 on 2021-12-06
> **Shibblet said:**
> It would also seem more difficult to maintain that browser without having regular updates in the repositories.  Downloading .DEB's and installing "sh" in the terminal, doesn't seem conducive to just letting the package manager take care of it.

The easiest thing to do would be to switch to Firefox Extended Support Release (ESR). The Mozilla Team has a PPA you can add that supports Ubuntu 16.04.

[https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)

Alternatively, you can install a browser such as Vivaldi (not open-source but based on Chromium) that still supports Ubuntu 14.04 and 16.04.


> **Shibblet said:**
> I've heard you can do that... but it seems that's more of an issue for places that have a LOT of computers that need to be updated properly.  It just seems more simple to upgrade the OS for a personal computer.


You only have to enter a command line in the terminal to allow extended security maintenance (ESM). It's very easy.

---

### Post by monkeybrain20122 on 2021-12-07
> **night_sky2 said:**
> The easiest thing to do would be to switch to Firefox Extended Support Release (ESR). The Mozilla Team has a PPA you can add that supports Ubuntu 16.04.

[https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)

Alternatively, you can install a browser such as Vivaldi (not open-source but based on Chromium) that still supports Ubuntu 14.04 and 16.04.





You only have to enter a command line in the terminal to allow extended security maintenance (ESM). It's very easy.

Just download the distro agnostic tarball from Mozilla, make a .desktop file to launch it. To update, click Help > About Firefox, it will update automatically if update is available. OP can set it up for his dad.

---

### Post by Daveski17 on 2021-12-16
I used 16.04 LTS (Ubuntu) for a long time. I used 14.04 for even longer. I only upgraded in April this year. I brought my laptop right up to date to 20.04 LTS. It didn't take long to familiarise myself with 20.04. I should have done it sooner! In April next year I'll upgrade with everyone else. Overall it's safer to use a supported OS.

---

### Post by DuckHook on 2021-12-17
> **Daveski17 said:**
> …I should have done it sooner!
Good on you that you got there.
> Overall it's safer to use a supported OS.
Understatement of the year. It's more accurate to say that anyone not on a supported release is a not only a danger to themselves, but a menace to the whole computing community.

The [current log4j disaster]("https://www.theregister.com/2021/12/13/log4j_rce_latest/") is a case in point. This one is really nasty. But while most typical users won't have this library installed, it isn't hard to unwittingly stumble into it with the installation of a Java app (Minecraft anyone? Apache?).

Supported versions of Ubuntu were patched within hours (anything =+v2.16 is fixed):```
duckhook@Zeus:~$  apt show liblog4j2-java
Package: liblog4j2-java
Version: 2.16.0-0.20.04.1
Priority: optional
Section: universe/java
Source: apache-log4j2
…
```
…but unsupported versions? Outta luck. [You will be pwned.]("https://www.theregister.com/2021/12/15/log4j_latest_cisa/")

---

### Post by Daveski17 on 2021-12-18
> **DuckHook said:**
> Good on you that you got there.

Unfortunately I listened to the advice of Linux 'experts' that assured me that all LTS Ubuntu releases after *Trusty* were inherently unstable. I missed out on 18.04, which was a bit of a change from 16.04. 

[ATTACH=CONFIG]289647[/ATTACH]

20.04 LTS not only performs better but looks better IMO.

> **DuckHook said:**
> Understatement of the year. It's more accurate to say that anyone not on a supported release is a not only a danger to themselves, but a menace to the whole computing community.

The [current log4j disaster]("https://www.theregister.com/2021/12/13/log4j_rce_latest/") is a case in point. This one is really nasty. But while most typical users won't have this library installed, it isn't hard to unwittingly stumble into it with the installation of a Java app (Minecraft anyone? Apache?).

Supported versions of Ubuntu were patched within hours (anything =+v2.16 is fixed):```
duckhook@Zeus:~$  apt show liblog4j2-java
Package: liblog4j2-java
Version: 2.16.0-0.20.04.1
Priority: optional
Section: universe/java
Source: apache-log4j2
…
```
…but unsupported versions? Outta luck. [You will be pwned.]("https://www.theregister.com/2021/12/15/log4j_latest_cisa/")

Scary.

---

### Post by night_sky2 on 2021-12-19
> **Daveski17 said:**
> I used 16.04 LTS (Ubuntu) for a long time. I used 14.04 for even longer. I only upgraded in April this year. I brought my laptop right up to date to 20.04 LTS. It didn't take long to familiarise myself with 20.04. I should have done it sooner! In April next year I'll upgrade with everyone else. Overall it's safer to use a supported OS.

A lot of people don't care about the ''latest and greatest''. They just want a OS that is stable, rock solid and that meets their all of their needs. If you find one, I don't see why there is a ''need'', an ''urge'' to upgrade. Also, when using Ubuntu 16.04 (as mentioned by the OP) and their derivatives, it's a mistake to believe that they are necesserely unsupported or any less safer. They can still receive *Extended* Security Maintenance (ESM).

---

### Post by DuckHook on 2021-12-19
> **night_sky2 said:**
> A lot of people don't care about the ''latest and greatest''. They just want a OS that is stable, rock solid and that meets their all of their needs. If you find one, I don't see why there is a ''need'', an ''urge'' to upgrade. Also, when using Ubuntu 16.04 (as mentioned by the OP) and their derivatives, it's a mistake to believe that they are necesserely unsupported or any less safer. They can still receive *Extended* Security Maintenance (ESM).
What you say has some merit, but we are posting a bit at cross purposes.

I'm generally not interested in the latest and the greatest either. The fact that I stick to LTSes already puts me, on average, a year behind the curve, and because computing years are somewhat akin to dog years, this translates into something like 8 years in the virtual universe. Indeed, were it not for the fact that I help out on these forums, I might not even upgrade to even the latest LTSes.

However, the important operative in your observation is your conditional: the reference to ESM. Reading through all of the prior posts, it is clear that the old&#8209;timers who have chimed in have all taken pains to mention the ESM option as the only acceptable way to run an old version that would otherwise be out of support.

But here's the real problem:

People who can't be bothered to stay current also all too often can't be bothered to run ESM. Doing so requires a degree of technical acumen. In my experience, the people who run five years behind the curve (=40 dog/computing years) aren't the sort to seek out archival repos or understand concepts like ESM. They are more like the sort who still connect to the Internet using Windows XP because that too is an OS that is "…stable, rock solids and that meets their needs."

The whole point of all the cautions raised is that, as stable, solid and need&#8209;fulfilling as it is, ***it isn't safe***.

If the OP's father can be convinced into adding ESM to his setup, then great. My bet is the old man will refuse to allow his computer to be touched in any way, shape or form because it's running "stable, rock solid and meets his needs."

---

### Post by Daveski17 on 2021-12-19
> **night_sky2 said:**
> A lot of people don't care about the ''latest and greatest''. They just want a OS that is stable, rock solid and that meets their all of their needs. If you find one, I don't see why there is a ''need'', an ''urge'' to upgrade. Also, when using Ubuntu 16.04 (as mentioned by the OP) and their derivatives, it's a mistake to believe that they are necesserely unsupported or any less safer. They can still receive *Extended* Security Maintenance (ESM).

I think it's just simpler and safer to stay supported. This is why I have only ever used LTS releases anyway. The *latest* *and* *greatest* isn't a requirement for me either. But I think being supported and with an up to date software centre is better than just using an unsupported OS version because you feel comfortable with it. 

One of the principle reasons I ditched Windows for Ubuntu was security. Well, that and I just prefer Linux as it's a better system IMO. 

Things change. Admittedly not always for the better. But they change. I honestly wish I'd have upgraded sooner.

---

### Post by Dennis N on 2021-12-19
> I think it's just simpler and safer to stay supported. This is why I have only ever used LTS releases anyway.
In Ubuntu 20.04, it appears not all packages are supported with security updates as you might think:
```
dmn@Sydney:~$ ubuntu-security-status
2092 packages installed, of which:
1820 receive package updates with LTS until 4/2025
 270 could receive security updates with ESM Apps until 4/2030
   2 packages are no longer available for download

Packages that are not available for download may be left over from a
previous release of Ubuntu, may have been installed directly from a
.deb file, or are from a source which has been disabled.
For more information on the packages, run 'ubuntu-security-status
--unavailable'.

[U][U]Enable Extended Security Maintenance (ESM Apps) to get 10 security
updates (so far) and enable coverage of 270 packages.
[/U]
```[/U]
As I read it, you don't get the 10 available security updates mentioned without ESM enabled. So you are vulnerable to those now.

---

### Post by DuckHook on 2021-12-19
> **Dennis N said:**
> In Ubuntu 20.04, it appears not all packages are supported with security updates as you might think:
…
As I read it, you don't get the 10 available security updates mentioned without ESM enabled. So you are vulnerable to those now.
:-k
I never knew about that command until now, but I got similar results. I wonder why they would do this? Know of any way to tell what pkgs those are?

---

### Post by Daveski17 on 2021-12-20
> **Dennis N said:**
> In Ubuntu 20.04, it appears not all packages are supported with security updates as you might think:
```
dmn@Sydney:~$ ubuntu-security-status
2092 packages installed, of which:
1820 receive package updates with LTS until 4/2025
 270 could receive security updates with ESM Apps until 4/2030
   2 packages are no longer available for download

Packages that are not available for download may be left over from a
previous release of Ubuntu, may have been installed directly from a
.deb file, or are from a source which has been disabled.
For more information on the packages, run 'ubuntu-security-status
--unavailable'.

[U][U]Enable Extended Security Maintenance (ESM Apps) to get 10 security
updates (so far) and enable coverage of 270 packages.
[/U]
```[/U]
As I read it, you don't get the 10 available security updates mentioned without ESM enabled. So you are vulnerable to those now.

Oh crap! I'll have to take my chances I think.

---

### Post by sudodus on 2021-12-20
> **DuckHook said:**
> :-k
I never knew about that command until now, but I got similar results. I wonder why they would do this? Know of any way to tell what pkgs those are?

Maybe to make us sign up for Ubuntu Advantage (which is free for max 3 computers for personal use, but more for Ubuntu members)

[https://ubuntu.com/advantage](https://ubuntu.com/advantage)

I don't know which are those 10 packages. Maybe we can get an answer at [https://discourse.ubuntu.com/](https://discourse.ubuntu.com/), so I [asked now](https://discourse.ubuntu.com/t/why-is-extended-security-maintenance-needed-for-apps-in-ubuntu-20-04-x-lts-in-2021/25871/2) ...

---

### Post by night_sky2 on 2021-12-20
> **Daveski17 said:**
> I think it's just simpler and safer to stay supported. This is why I have only ever used LTS releases anyway. The *latest* *and* *greatest* isn't a requirement for me either. But I think being supported and with an up to date software centre is better than just using an unsupported OS version because you feel comfortable with it. 

But there are reasons *why* Canonical offers Extended Security Maintenance (ESM). Sometimes you have machines you just don't want to upgrade. Everything works perfectly fine as it is. Upgrades require change, bring novelties that are not always desirable and may result in instability. This is especially true in large enterprises when you just don't want to go through the hassle of upgrading  every few years for various reasons. I don't see why this couldn't also be true for individual users.


> **Daveski17 said:**
> One of the principle reasons I ditched Windows for Ubuntu was security. Well, that and I just prefer Linux as it's a better system IMO.

I switched to Linux for the freedom of choice.

> **Daveski17 said:**
> Things change. Admittedly not always for the better. But they change. I honestly wish I'd have upgraded sooner.

In terms of computer OS, I think we are actually devolving. Microsoft Windows is a classic example of this. Windows XP and Windows 7 were pretty good but after that things went downhill. Their OS became fatter, more ressource hungry, intrusive and with all the bells and whistles. No wonder why millions of people worldwide still run XP and 7, as their perfectly working hardware can't keep up with the demands of ''change'' and consumerism. Linux users don't have to fall into that trap.

---

### Post by DuckHook on 2021-12-20
> **sudodus said:**
> …I don't know which are those 10 packages. Maybe we can get an answer at [https://discourse.ubuntu.com/](https://discourse.ubuntu.com/), so I [asked now](https://discourse.ubuntu.com/t/why-is-extended-security-maintenance-needed-for-apps-in-ubuntu-20-04-x-lts-in-2021/25871/2) ...
Thx for looking into this sudodus.

Will you post your findings back to this thread?

---

### Post by Daveski17 on 2021-12-20
> **night_sky2 said:**
> But there are reasons *why* Canonical offers Extended Security Maintenance (ESM). Sometimes you have machines you just don't want to upgrade. Everything works perfectly fine as it is. Upgrades require change, bring novelties that are not always desirable and may result in instability. This is especially true in large enterprises when you just don't want to go through the hassle of upgrading  every few years for various reasons. I don't see why this couldn't also be true for individual users.

Fair point. I just think it's easier to upgrade every five years. Eventually I'll have to buy new hardware anyway. 

> **night_sky2 said:**
> I switched to Linux for the freedom of choice.

Freedom of limited choice? I am not going to fetishise 'freedom' even though it's popular with some. Let's face it, Linux has limitations. There's a lot of software I can't run on it (easily). However; MS update cycles were always a borkfest, and with Win 7 I was so sure a patch or update would bork the system, I made regular Macrium images. MS even stopped me switching off auto updating. Notwithstanding the disaster that was Win 8/8.1 (which I never used) and them consistently pushing Win 10. Eventually I couldn't even get MSE to update signatures. Third party AV's are just as bad and I've never used an anti-malware program that hasn't tried to remove system drivers or eviscerate any Widows computer I owned. So, I'm free of that fandango. 

> **night_sky2 said:**
> In terms of computer OS, I think we are actually devolving. Microsoft Windows is a classic example of this. Windows XP and Windows 7 were pretty good but after that things went downhill. Their OS became fatter, more ressource hungry, intrusive and with all the bells and whistles. No wonder why millions of people worldwide still run XP and 7, as their perfectly working hardware can't keep up with the demands of ''change'' and consumerism. Linux users don't have to fall into that trap.

Yes, that was another prime reason I switched to Ubuntu. Not only is it free, it's light. Vista eventually crashed irretrievably on my old Belnea notebook. So I converted it to Ubuntu. The difference in performance was stunning. It only had 1Gb of RAM. I'm surprised it handled Vista at all. It positively flew with Ubuntu. *I* was converted to Ubuntu from then on.

---

### Post by sudodus on 2021-12-21
> **DuckHook said:**
> Thx for looking into this sudodus.

Will you post your findings back to this thread?

At [discourse.ubuntu.com/](https://discourse.ubuntu.com/t/why-is-extended-security-maintenance-needed-for-apps-in-ubuntu-20-04-x-lts-in-2021/25871/2) I was asked to write a bug report.

Here it is: [Why is Extended Security Maintenance needed for apps in Ubuntu 20.04.x LTS in 2021?](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1955471).

Please add heat by clicking on the bug report's  'Affects me too' button :-P

Edit: The bug report was declared invalid, so we are back to where we started.

Edit2: Olivier Tilloy (I think he works at Canonical) is giving us a hopeful message: After the holiday season, they may start looking at this issue.

---

### Post by DuckHook on 2021-12-21
> **sudodus said:**
> At [discourse.ubuntu.com/](https://discourse.ubuntu.com/t/why-is-extended-security-maintenance-needed-for-apps-in-ubuntu-20-04-x-lts-in-2021/25871/2) I was asked to write a bug report.
…Edit: The bug report was declared invalid, so we are back to where we started.
Edit2: Olivier Tilloy (I think he works at Canonical) is giving us a hopeful message: After the holiday season, they may start looking at this issue.
Thanks for the followup sudodus.
> **Dennis N said:**
> In Ubuntu 20.04, it appears not all packages are supported with security updates as you might think:
```
dmn@Sydney:~$ ubuntu-security-status
2092 packages installed, of which:
1820 receive package updates with LTS until 4/2025
 270 could receive security updates with ESM Apps until 4/2030
   2 packages are no longer available for download

Packages that are not available for download may be left over from a
previous release of Ubuntu, may have been installed directly from a
.deb file, or are from a source which has been disabled.
For more information on the packages, run 'ubuntu-security-status
--unavailable'.

[U][U]Enable Extended Security Maintenance (ESM Apps) to get 10 security
updates (so far) and enable coverage of 270 packages.
[/U]
```[/U]
As I read it, you don't get the 10 available security updates mentioned without ESM enabled. So you are vulnerable to those now.
It looks like this report is bugged (or at least misleading). "Supported" still means all-inclusive and the "ESM Apps" reference is meant to be a future feature (as far as I can make out from the short and somewhat murky Launchpad posts).

---

### Post by Shibblet on 2021-12-21
This is very interesting that all of this can be done.  But it kinda seems like a lot more effort and technical skill is required to do this... wouldn't upgrading be easier?

---

### Post by VMC on 2021-12-21
> **TheFu said:**
> Does everyone realize the OP hasn't posted since the initial post #0 2 months ago and hasn't been back since then?

I have been seeing this post grow for quite a while now. I never bothered to view it until today. Couldn't help myself or understand why a simple question could contain 5 pages of comments.
TheFu is right. The OP has never come back!

The discussion after the OP's disappearance has some valuable information. The Title though wouldn't have brought me here, but noticing 5 pages did.

On topic, I would never have my PC's unprotected or not up to date. I don't update or upgrade to have the latest software, but to keep my software and computer secure.

---

### Post by night_sky2 on 2021-12-23
> **Shibblet said:**
> This is very interesting that all of this can be done.  But it kinda seems like a lot more effort and technical skill is required to do this... wouldn't upgrading be easier?


There is nothing technical about copy/past a command line in a terminal. That's all it takes to activate *Extended* Security Maintenance (ESM).

As long as you still receive security updates, there is no urge whatsoever to upgrade.

---

### Post by Daveski17 on 2021-12-23
I'm just going to upgrade. Doing it every five years isn't really a biggie.

---

### Post by sudodus on 2022-01-04
> **DuckHook said:**
> Thanks for the followup sudodus.

It looks like this report [the report written by the command **[FONT=Courier New]ubuntu-security-status[/FONT]**] is bugged (or at least misleading). "Supported" still means all-inclusive and the "ESM Apps" reference is meant to be a future feature (as far as I can make out from the short and somewhat murky Launchpad posts).

There is a new reply at [discourse.ubuntu.com](https://discourse.ubuntu.com/t/why-is-extended-security-maintenance-needed-for-apps-in-ubuntu-20-04-x-lts-in-2021/25871/9) by Julian Andres Klode stating that this output, (that we fail to understand) is nothing new to worry about. The packages in the main repo are supported with security updates but we should not expect Canonical to provide security updates for packages in the universe and multiverse repos.

I will not continue to push this issue.

---

### Post by grahammechanical on 2022-01-04
Here is my guess

esm-infra = what is presently available with Extended Security Maintenance. esm-apps = a new idea to provide extended security maintenance to certain default applications in Ubuntu. The ins and outs of this extended ESM (will it be called EESM? (joke) have yet to be worked out, costed and approved. The connection to 20.04 LTS? It would be the first release to have both the base Ubuntu software infrastructure and 10 default applications (or less) included in the ESM offer.

Does this mean that ESM does not at present cover Firefox?

Regards

---

### Post by DuckHook on 2022-01-04
> **sudodus said:**
> I will not continue to push this issue.
I agree sudodus.
> **grahammechanical said:**
> ...will it be called EESM? (joke)
I propose **E**xtra **E**xtended **E**sm **W**ork-in-progress or: EEEW :tongue:
> Does this mean that ESM does not at present cover Firefox?
Good question. Perhaps some of the people already on ESM can fill us in. 16.04 users should now be on ESM I believe.

---

### Post by sudodus on 2022-01-14
> **sudodus said:**
> At [discourse.ubuntu.com/](https://discourse.ubuntu.com/t/why-is-extended-security-maintenance-needed-for-apps-in-ubuntu-20-04-x-lts-in-2021/25871/2) I was asked to write a bug report.

Here it is: [Why is Extended Security Maintenance needed for apps in Ubuntu 20.04.x LTS in 2021?](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1955471).

Please add heat by clicking on the bug report's  'Affects me too' button :-P

Edit: The bug report was declared invalid, so we are back to where we started.

Edit2: Olivier Tilloy (I think he works at Canonical) is giving us a hopeful message: After the holiday season, they may start looking at this issue.

> **sudodus said:**
> There is a new reply at [discourse.ubuntu.com](https://discourse.ubuntu.com/t/why-is-extended-security-maintenance-needed-for-apps-in-ubuntu-20-04-x-lts-in-2021/25871/9) by Julian Andres Klode stating that this output, (that we fail to understand) is nothing new to worry about. The packages in the main repo are supported with security updates but we should not expect Canonical to provide security updates for packages in the universe and multiverse repos.

I will not continue to push this issue.

There is progress at the [bug report](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1955471) - a suggested patch to make the information to us end users easier to understand:

> In Ubuntu Advantage Client, as of now, `ua security-status` is showing ESM-Apps information only if it is enabled on the machine while the service is beta.

This patch does the same for `ubuntu-security-status`: it will only show ESM-Apps related information if:
- The user has enabled esm-apps through UA, or
- ESM Apps gets released and we remove the `beta` flag on the UA side.

Please let me know if this suffices and/or if there is anything else we could help with.

Please add your own comment at the bug report.

---

### Post by DuckHook on 2022-01-15
> **sudodus said:**
> Please add your own comment at the bug report.
Thanks for keeping us in the loop sudodus.

For my part, I can't think of anything to add. The unfortunate thing is the label: "ESM Apps" is so easily conflated with ESM in its totality. I was never aware of the distinction between ESM Apps and ESM Infra—pretty obscure—though it makes sense once it is explained.

But I can't think of a clearer label than "ESM Apps" either, so it will just have to do. I think the devs have clarified this as far is such things can be. I don't think it will lead to too much confusion if for no other reason than so few users ever invoke: *ubuntu-security-status*

---

