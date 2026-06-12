---
title: "Karmic's karma"
date: 2009-11-27
forum: The Cafe
---

### Post by PryGuy on 2009-11-27
Well, I used to write about it before and here I go again. First of all, I'm not a Windows fanboy or something. I stick with Ubuntu Desktop and Ubuntu Server, but as I wrote before I just can't use Karmic. The reason - it's unusable for me. You can say, WTF, just stick with Jaunty or something (some actually do here). So I do, but look what problems I've discovered for Karmic:

Samba shares list does not appear sometimes in Nautilus
Empathy conversation logs can't be turned off, that's not suitable
ext4 runs into errors sometimes
gdm has no XDMCP option, some f my clients use it
Wi-Fi chokes on my Atheros AR5001X+ based D-Link DWL-G650 PCMCIA Wireless Network Adapter
mc uses nano as a default editor (has to be mcedit)
mc does not save configuration

So what's going on? I've reported about the Samba shares list problem and launchpad said the bug has low priority. LOW PRIORITY? They must be kidding! Do they want me to start switching my clients on Karmic or not? It's a bloody annoying bug, and it's very serious for me 'cause I can't give my clients a half-working product!

Another thing is ext4. God, it gives me errors! And ext3 is rock stable. Well, in this case I can use ext3, so I do, but they made ext4 a default FS in Karmic!

What's the point of making new releases if they don't care about bugs that appear to be serious for some people? Windows Vista was a failure, that gave Ubuntu benefits among other things. Windows 7 is a solid thing, it can overwhelm Ubuntu as one of the main Ubuntu advantages was stability. Do I really miss something? Tell me if so. Again, I just want to understand what's going on. Thabk you in advance!

---

### Post by the yawner on 2009-11-27
> **PryGuy said:**
> 
Empathy conversation logs can't be turned off, that's not suitable
ext4 runs into errors sometimes
gdm has no XDMCP option, some f my clients use it


- Empathy is still in development. What can't be turned off right now may be possible in the near future. In the meantime, some people continue to just use Pidgin.
- AFAIK, ext3 is still an option during install if you choose manual partitioning. Defaulting to ext4 encourages wider adoption of the new file system and in my opinion, a better way to detect bugs.
- GDM has undergone a re-write. This is an upstream decision, I think.

---

### Post by PryGuy on 2009-11-27
> **the yawner said:**
> 
- AFAIK, ext3 is still an option during install if you choose manual partitioning. Defaulting to ext4 encourages wider adoption of the new file system and in my opinion, a better way to detect bugs.buggy ext4 by default is kinda too serious I think... Canonical should change their Ubuntu slogan to "Ubuntu. Linux for beta-testers" then... Sorry to say that...

---

### Post by dmizer on 2009-11-27
> **PryGuy said:**
> Samba shares list does not appear sometimes in Nautilus
This has been a problem since the beginning. Hence both the CIFS howto in my sig, as well as the 6th link in my sig. Most people can fix their Samba problems by following the 6th link. There are probably hundreds of bugs open on this problem, and I can assure you that the devs are well aware of it and have been actively working on it. I've been following this issue for about 5 years. One of the biggest problems with this particular issue is that even though the symptom is the same, the cause is not. So a fix that works for one person does not necessarily fix everyone.

I highly suggest you start with the 6th link in my sig, and doublecheck for any possibly interference from local firewalls. But to directly answer your problem here ... this is by no means unique to Karmic.


> **PryGuy said:**
> Empathy conversation logs can't be turned off, that's not suitable
Empathy is a new IM client for Karmic. If it's not working for you, install Pidgin instead. If you install pidgin and pidgin-libnotify, it will have most of the features of Empathy.


> **PryGuy said:**
> ext4 runs into errors sometimes
You solved that the same way I did. Just make sure to install ext3 instead. While I agree that ext4 probably isn't ready for the masses, that doesn't mean it's a killer for Karmic because there is indeed an alternative here.


> **PryGuy said:**
> gdm has no XDMCP option, some f my clients use it
First search results in google for: karmic xdmcp -> [http://ubuntuforums.org/showthread.php?t=1239268](http://ubuntuforums.org/showthread.php?t=1239268)


> **PryGuy said:**
> Wi-Fi chokes on my Atheros AR5001X+ based D-Link DWL-G650 PCMCIA Wireless Network Adapter
Admitedly, I couldn't find a quick fix for this, but if it's a PCMCIA adapter, surely you can spring for a $15 replacement if it's that big of an issue?


> **PryGuy said:**
> mc uses nano as a default editor (has to be mcedit)
This is an upstream problem and also existed in Jaunty here's your bug with links upstream. Doesn't look like there are any workarounds posted, but you can be well assured that this one is being actively worked on as well -> [https://bugs.launchpad.net/ubuntu/+source/mc/+bug/263442](https://bugs.launchpad.net/ubuntu/+source/mc/+bug/263442)


> **PryGuy said:**
> mc does not save configuration
Bug report with fix turned up on a google search for: karmic mc save configuration -> [https://bugs.launchpad.net/ubuntu/+source/mc/+bug/397497](https://bugs.launchpad.net/ubuntu/+source/mc/+bug/397497)

---

### Post by PryGuy on 2009-11-27
Thanks for the answer, dmizer! I was expecting that people start saying post is rubbish... What do you generally think of the quality of this release?

P.S. Ang wow! Your guide is wonderful!

---

### Post by dmizer on 2009-11-27
> **PryGuy said:**
> Thanks for the answer, dmizer! I was expecting that people start saying post is rubbish... What do you generally think of the quality of this release?

I've actually installed it on one of my machines and have been using it. That's a first for me. I generally wait several months before installing a new release on a production machine.

---

### Post by SR_ELPIRATA on 2009-11-27
@PryGuy: If I remember well, with 9.10 they brought again the ability for you to make your own LiveCD. Far as I understood it...you could eliminate packages that you didnt wanted/needed and have others be there. Therefore, some stuff that you mention you probably can make into an ISO and distribute to your clients.

To me, if aint broke... why change? If their Jaunty's are working well, why the need to change/upgrade it?

I moved to 9.10 when it got out, found a huge problem with the audio and after a week or so in Launchpad and tried every solution they gave me... it didnt work, so I'm back to 9.04. Its not perfect either, but I require 'perfect' audio and 9.04 has it.

I've noticed the problems with shares also with 9.04. I used to be able to share data between my host (8.10) and Virtualbox VM's (xp or whatever) and now I cant. I'm sure this is not the same problem that you are having, but they are somewhat related.

Still, I wouldnt return to XP when Ubuntu works so great for me. If my hard drive hadn´t died, I can tell you I would still be in 8.10 happily.

BTW, whats the 'mc' thingie? Media Center? I'm using xbmc :) works great!

ELP

---

### Post by PryGuy on 2009-11-27
> **SR_ELPIRATA said:**
> BTW, whats the 'mc' thingie? Media Center? I'm using xbmc :) works great!

ELP
It's Midnight Commander, Linux Norton Commander analogue. It's vital if you work with CLI, and I work with CLI mostly.

---

### Post by ZankerH on 2009-11-27
> **PryGuy said:**
> buggy ext4 by default is kinda too serious I think... Canonical should change their Ubuntu slogan to "Ubuntu. Linux for beta-testers" then... Sorry to say that...


Everyone who uses a non-LTS release of Ubuntu is essentially an unpaid betatester. If you don't like that, stick to LTS or the last version that worked for you.

---

### Post by Kazade on 2009-11-27
> **ZankerH said:**
> Everyone who uses a non-LTS release of Ubuntu is essentially an unpaid betatester. If you don't like that, stick to LTS or the last version that worked for you.

I hear this a lot, but that's not true. Go to [http://www.ubuntu.com/](http://www.ubuntu.com/) and tell me what download you are given by default. 

Releases between LTS's are just as much full releases, they just don't have as much focus on stability. I think pretending that they are "beta" versions is just a bad excuse for breakage.

---

### Post by Psumi on 2009-11-27
> **ZankerH said:**
> Everyone who uses a non-LTS release of Ubuntu is essentially an unpaid betatester. If you don't like that, stick to LTS or the last version that worked for you.

Sadly, 9.10 is the last one that works for me. So I must use 9.10.

What about us?

---

### Post by vexorian on 2009-11-27
karmic is the last release before the LTS. All of these changes were bound to happen and introduce regressions. It is annoying, but even though I had issues with karmic I think  it is best to have the regressions in this release rather than in the next one. If you have costumers and want something more stable wait for the next release. Jaunty is perfectly fine right now and still getting package updates.

Did not experience any big problem in karmic besides grub2, I fixed it by just installing legacy grub.

---

### Post by dmizer on 2009-11-27
> **ZankerH said:**
> Everyone who uses a non-LTS release of Ubuntu is essentially an unpaid betatester.

This suggests that there are paid beta testers.

Bugs and bug reporting is simply part of being a member of the Linux community. That doesn't make non-LTS releases any more or less usable, it just means that users sometimes encounter bugs as a result of new software releases. However, this is not unique to Linux. Beta test all you want, but you'll never be able to test all the potential situations your software will subjected to in a production environment.

---

### Post by PryGuy on 2009-12-01
Have to add: I've fixed the PCMCIA Atheros Wi-Fi card bug. It was the ath5k driver. Disabling it and istalling madwifi manually solves the problem. Back in the good old days when we had to compile drivers manually. ;)
Sorry, I'm sarcastic...

---

