---
title: "Trojan infects 20,000 os x using computers"
date: 2009-01-23
forum: The Cafe
---

### Post by EnGorDiaz on 2009-01-23
this seems to be a huge numbers for the unix hackers out there this is a huge accomplishment
[http://www.engadget.com/tag/TrojanHorse/](http://www.engadget.com/tag/TrojanHorse/)

---

### Post by Eisenwinter on 2009-01-23
Interesting, yet I don't care.

---

### Post by sydbat on 2009-01-23
My favourite bit...> According to a white paper released by Intego, at least 20,000 people may have downloaded the infected software -- which they'll get around to installing as soon as they finish those episodes of Celebrity Rehab they grabbed at the same time.

More seriously, of course a Trojan or other malware can infect a Unix or Unix-like OS, for EXACTLY the reason stated in the article> downloading a pirated version of iWork '09 have gotten more than they'd bargained forUnsafe Internet habits.

---

### Post by Skripka on 2009-01-23
Teeeeheeeee.


PS-It is a TROJAN, not a "virus".

---

### Post by EnGorDiaz on 2009-01-23
> **Skripka said:**
> Teeeeheeeee.


PS-It is a TROJAN, not a "virus".

sorry im tired put a misleading title up i will change it 


but seriously i think them mac fanboys and other mac users wont be under there shell for much longer as this seems like a huge archievement

---

### Post by Skripka on 2009-01-23
> **EnGorDiaz said:**
> sorry im tired put a misleading title up i will change it 


but seriously i think them mac fanboys and other mac users wont be under there shell for much longer as this seems like a huge archievement


It is impressive, but this infection ought to be common-sense avoidance -_as ANYONE with BRAINS_ knows that illegal copies of software on torrents are almost always infected with something or other-if not the app itself then it is the keygen/crack....although statistically speaking-at least 20,000 people evidently are not born with common sense over a certain period.

---

### Post by Paqman on 2009-01-23
> **EnGorDiaz said:**
> this seems like a huge archievement

Not really. If you download and install cracked versions of proprietary software or games you're pretty much asking to be infected. It's exactly how i'd spread malware if I was going to. Pick a popular app or game, insert your payload, and watch as people download and install it.

This would work perfectly well on Linux, btw. Just another reason why the repos rule.

---

### Post by stchman on 2009-01-23
I have never used OSX, but since it is based on FreeBSD it should have similar security features on Linux.

The people in question downloaded an illegal copy of iWorks and then installed it on their machines.  They obviously granted administrator privileges to the illegal iWorks software.  When you do that you let the dirty software do all the deeds it wants.

They should have downloaded Openoffice.org 3 for OSX instead.

---

### Post by earthpigg on 2009-01-23
> **Paqman said:**
> This would work perfectly well on Linux, btw. Just another reason why the repos rule.

yes it would... we are vulnerable to trojans in random internet software because we grant root access when installing programs.

what about a self-replicating virus?

---

### Post by Grant A. on 2009-01-23
Chances are that this virus/trojan uses the Cocoa API. I see no imminent danger for any Linux user who obeys copyright laws.

---

### Post by daverich on 2009-01-23
beautiful.

I despise software piracy, especially when linux is available for free.

Serves them right.

Kind regards

Dave Rich

---

### Post by KiwiNZ on 2009-01-23
Thread title changed

Also

So simple to avoid, DON'T use pirated software

---

### Post by AlphaMack on 2009-01-23
> **Grant A. said:**
> Chances are that this virus/trojan uses the Cocoa API. I see no imminent danger for any Linux user who obeys copyright laws.

The trojan is an extra package added to the iWork metapackage which uses Apple's Installer.app.  The only way to know beforehand that something is amiss is to run Pacifist, a shareware front-end to Apple's pax utility.

It installs to /usr/bin/, /System/Library/StartupItems, and a hidden file (most likely config) in /private/tmp/.  Of course a package receipt is left behind in /Library/Receipts.

Once the program is launched (through the script in StartupItems) it connects to a remote server where according to Intego it downloads more software.

It uses a PHP script to perform a DoS on web sites.

The removal instructions given by some sites are quite silly as they instruct you to run 'sudo su' before a bunch of rm commands.

My suggestion would be a full reinstall as you don't know what else has been compromised.

---

### Post by Frak on 2009-01-23
> **Skripka said:**
> Teeeeheeeee.


PS-It is a TROJAN, not a "virus".
FYI, Trojan is a type of computer virus. Just as much as a worm is a type of computer virus. There is no generic "virus", they fall under a subclass.

---

### Post by swoll1980 on 2009-01-23
I don't think it's impressive at all. These idiots are installing the **** on there own computers. What would be impressive, is if they(the hackers) found a way to install the **** on your computer for you with out your knowledge. Any idiot that downloads and installs pirated software from a torrent deserves everything they get. No OS can keep a user from installing viri on there own computer no matter how secure it is.

---

### Post by swoll1980 on 2009-01-23
> **Frak said:**
> FYI, Trojan is a type of computer virus. Just as much as a worm is a type of computer virus. There is no generic "virus", they fall under a subclass.

I think he was just trying to emphasize the fact that it wasn't self installing

---

### Post by domokunrox on 2009-01-23
What was the point or payload to the infection?

Most of the time its to zombify a computer. I would love to know how a zombified Mac works.

---

### Post by calvinps on 2009-01-23
> **Skripka said:**
> Teeeeheeeee.


PS-It is a TROJAN, not a "virus".

A "Trojan Horse" **IS** a type of virus.

---

### Post by shadylookin on 2009-01-23
well when you give an app root permissions you're pretty much at it's mercy. When you give an app that contains pirated software that you got from a torrent site root permission don't be surprised when it's a virus.

---

### Post by Sealbhach on 2009-01-23
So in Uubntu, when we install things from Synaptic, do we give them root permission (after we've typed in our password)?


.

---

### Post by TBOL3 on 2009-01-23
Yup, this is why linux security is not all it's cracked up to be (even if I don't give an app root permission, it can still wipe out my /home/<user> directory.  And I can do a re-install in 20 min, with another hour or two to completely reconfigure my system.  But I can't replace my docs.

Also, I agree, those idiots got what they deserved.

And finally, I still think viri is not correct, it's viruses.

---

### Post by dnRoyston on 2009-01-23
This can't be possible, because, as we all know, Macs don't get malware ;)

---

### Post by Dev'olution on 2009-01-23
It is by living in that cocoon dnRoyston, that you will only end up getting something one day!

---

### Post by ratmandall on 2009-01-23
> **Sealbhach said:**
> So in Uubntu, when we install things from Synaptic, do we give them root permission (after we've typed in our password)?


.

Yep, but all the software in the default repositories are clean.

---

### Post by Flying caveman on 2009-01-23
But how did they know I also downloaded 'Celebrity Rehab'?:p

---

### Post by .arean on 2009-01-23
> **Paqman said:**
> Just another reason why private trackers rule.

Fixed.

---

### Post by Frak on 2009-01-23
> **Grant A. said:**
> Chances are that this virus/trojan uses the Cocoa API. I see no imminent danger for any Linux user who obeys copyright laws.
I doubt it. It would seem more effective to go for the BSD core using ObjC.

---

### Post by EnGorDiaz on 2009-01-24
> **ratmandall said:**
> Yep, but all the software in the default repositories are clean.

no the app runs on normal user level after you install them they usaly have a hidden set of config files in the home directory its complex to explain

---

### Post by Frak on 2009-01-24
> **EnGorDiaz said:**
> no the app runs on normal user level after you install them they usaly have a hidden set of config files in the home directory its complex to explain
I don't even know what you're trying to explain...

---

### Post by EnGorDiaz on 2009-01-24
> **Frak said:**
> I don't even know what you're trying to explain...

*shuts up and walks away*

---

### Post by Frak on 2009-01-24
> **EnGorDiaz said:**
> *shuts up and walks away*
*bakes a cake*

---

### Post by -grubby on 2009-01-24
> **Frak said:**
> *bakes a cake*

*NOMs it*

---

### Post by Frak on 2009-01-24
> **nathangrubb said:**
> *NOMs it*
*shrieks*

---

### Post by ade234uk on 2009-01-24
Serves them right really. I don't see any reason why someone would want to do this on Linux, since all the software is free. There would be no point, would there?

---

### Post by Procuro on 2009-01-24
> **ade234uk said:**
> Serves them right really. I don't see any reason why someone would want to do this on Linux, since all the software is free. There would be no point, would there?
Well the motive would probably be to get into a specific machine or just access someone's private data in general. It wouldn't be to get back at Steve Jobs or try to prove a point on piracy or something.

---

### Post by billgoldberg on 2009-01-24
The same thing can just as easily happen on a Linux box.

If you give something root access, all bets are off.

So be sure it's safe.

Stick to the repos or other trusted sources.

---

### Post by billgoldberg on 2009-01-24
> **Frak said:**
> FYI, Trojan is a type of computer virus. Just as much as a worm is a type of computer virus. There is no generic "virus", they fall under a subclass.

While that is true, most people consider a virus something that can install itself without any action being made by the user.

---

### Post by eragon100 on 2009-01-24
Most files I have downloaded from the net are not infected with any kind of virus.

Plus, if you run under wine, then a virus will not be able to infect your linux installation. If the movies/music had been infected it would more then likely have been a windows virus, which means it can't do a thing if you run it in a linux media player. The file usually plays fine, so no problem. It only becomes a problem when you want to share that file with a windows user. I usually scan for infections, then. If it is infected, I tell them so and say that they obviously can't play it. Unless they install the great Ubuntu Linux, offcourse! :KS

---

### Post by Paqman on 2009-01-24
> **eragon100 said:**
> Most files I have downloaded from the net are not infected with any kind of virus.


So some of them have been?

Simple rule: never install *anything* from an untrusted source unless you have the MD5 for a clean version of it. P2P is, by the way, always an untrusted source, whether it's private tracker or public.

---

### Post by 3rdalbum on 2009-01-24
1. I'd be surprised if it was really 20,000 computers.

2. Why would you pirate iWork? Surely there's a cracked version of Microsoft Office on the trackers?

3. Unsafe behaviour is unsafe behaviour, on any platform.

---

### Post by BigSilly on 2009-01-24
So just how safe are repositories like Medibuntu and PLF for Linux users? Not wishing to cause any offence, but at the end of the day many of us rely on these repositories, and if they got hacked or had a malicious contributor, we'd be screwed really wouldn't we? :confused:

I have used these software sources for a while now, and trust they are safe. Is someone here going to prove otherwise?

---

### Post by -grubby on 2009-01-24
> **3rdalbum said:**
> 
2. Why would you pirate iWork? Surely there's a cracked version of Microsoft Office on the trackers?


Maybe some people prefer iWork over Microsoft Office.

---

### Post by Frak on 2009-01-24
> **nathangrubb said:**
> Maybe some people prefer iWork over Microsoft Office.
Bleh, no. Last time I used it, it felt like an unfinished version of office. There are many usability bugs, such as listing, and the formatting feels incomplete, especially since the formatting is easily undone when selecting something else.

I prefer OO.o over iWork, and I'd still use MSO over OO.o

---

### Post by ratmandall on 2009-01-25
> **EnGorDiaz said:**
> no the app runs on normal user level after you install them they usaly have a hidden set of config files in the home directory its complex to explain
The key word here is "AFTER".

---

### Post by hanzomon4 on 2009-01-25
Same thing could happen on any nix system, only a matter of time.

---

### Post by Skripka on 2009-01-25
Here's an interesting addition to the question of, "Why?"


It seems for boxed discs of iWork, Apple no longer needs/requires a reg code.

[http://arstechnica.com/journals/apple.ars/2009/01/20/apple-stops-requiring-licenses-for-boxed-iwork-09](http://arstechnica.com/journals/apple.ars/2009/01/20/apple-stops-requiring-licenses-for-boxed-iwork-09)

---

