---
title: "How to determine outgoing port blocks"
date: 2011-11-03
forum: Security
---

### Post by jago25_98 on 2011-11-03
I found this thread and found it interesting:
[http://ubuntuforums.org/showthread.php?t=1870738&highlight=tool+to+scan](http://ubuntuforums.org/showthread.php?t=1870738&highlight=tool+to+scan)

It is entitled "Tool to scan outbound tcp port blockings?"

The response was 

"As has been noted discussion about circumventing your companies policies are not permitted."

I take issue with this because there is no mention of bypassing security. The poster wished to know what ports are allowed and not allowed. The poster was looking for knowledge and information. Looking for knowledge and information is not a crime and should be allowed in a just community. 

I am not in anyway associated with the original poster as we can see from my profile. 

To help the poster I can say that other than asking a sysadmin (which puts your head above the parapit as a trouble maker), there are a few ways. 

The first is to open all ports on a server you control outside the controlled area and script trying to connect to each port. This can be done with netcat but personally I don't know how to do this. 
The other one is to use nmap. You can actually do this from inside the firewalled area. Just ```
#nmap -sP aNonFirewalledAddress
``` I think this works but I think maybe incoming blocks get confused with the outgoing, I'm not sure. 

All this is very useful knowledge if you move around on public wifi, 3G and corporate networks; much quicker than trying t ofind out from an Indian call centre. 

Hope this helps 

 -j

---

### Post by OpSecShellshock on 2011-11-03
The user's explicitly stated intention in that thread is to connect to a home computer from work. If it's been blocked, then it's a safe bet that it's not permitted.

When you connect to other parties' networks, what's allowed or not isn't up to you. Mapping those networks for the purpose of performing unsupported tasks is not responsible, is ethically suspect, and may well be a crime, at least in the US, per the CFAA.

---

### Post by jago25_98 on 2011-11-04
Ok I hope this goes ok. I like to argue but I want it all to be in good faith and if it means irritating someone I'd rather drop this and just let it lie. But I enjoy a good discussion so here we go. 

> **OpSecShellshock said:**
> The user's explicitly stated intention in that thread is to connect to a home computer from work. If it's been blocked, then it's a safe bet that it's not permitted.

The OP was looking for what **is** open and what **is** allowed and what **is** supported. 

Q: Why not just tell users what is and isn't allowed? 
A: Because as with TOS legal spamming this gets abused... better to communicate according to what controls are in place. 

Maybe I need to change attitude and not care. I can't change the world. (planning to emigrate to a more liberal country though!)

[strike]I[/strike] we still have the problem of not knowing why we can't Skype, FTP or use various services when we connect to a new network. When you connect to 3 networks on site through the week at different client networks as a contractor it seems nice to be able to have network permissions laid clear. It is hard work when packets are dropped without giving the decency to say it has happened. I once lost connectivity to a site I was administrating and for a while I thought I had a major issue. It cost me a lot of time. It turned out to be routing but there have been other incidents where packets have been silently dropped like this and turned out it was country level censorship to a site. Was it a hacking site? Was it a threat to national security? No it was a site for people to swap items they own (tax evasion concerns I suppose). 

We have an attitude now where just looking **is** the crime and here I am having to explain and justify why it is innocent to look at something. 

As a sysadmin why do I care about limiting a service. I don't care because they have control of the network. I think if sysadmins actually had to work on a network that isn't under their control things would be very different. I'm willing to bet that anyone in favour of controls are actually working in IT and have never undergone controls.  

When the OP didn't get the answer they needed they would have carried on searching. This likely would have brought them to hacking forums which in turn exposed the work network to cross server scripting vulnerabilities, something a reactive blocking contingency can't fully protect against (like DansGuardian keyword blocks - great, I can't read about rape seed oil on wikipedia...). Unintended consequences like this are the result of our arrogance of thinking we can control everything. 

In my experience port blocks are about are when sysadmins are given the impossible task of securing winbloze machines on a network of a size that is too big for them to manage with users who have no clue. Instead of firewalling correctly and providing a walled garden for browsing such as VMware appliance, separate networks or even dedicated machines it's a case of install a proxy, install a virus scanner. 6 months later the virus scanner lets something through and people are using 3G ipads under their desk. Nice one. Sysadmin says the virus scanner is rubbish and like a bad workman blames the tools without addressing the underlying cause. Cue a round of moaning. Maybe somebody even looses their job. And still the problem is there. 

This has got to stop. 
We've already seen how spyware hides in closed source software and we know that the only way to really know what is going on is opensource like Ubuntu. Openness applies right here too. It has a real impact - i.e. are your corporate phones using Dolphin Browser on Android and passing everything to the developers? 

Do we use Ubuntu as a mark of integrity or do we use it as a mark of cheapskatedness? 

This is academic in a way now that we have 3G coverage but I still implore for reconsideration for all the reasons above and more that we fail to recognise. 

It's also true that if the UbuntuForum has to operate within laws that are antagonistic to what Ubuntu is (the CFAA for USA hosting), then I guess it's tough cheese for me. But at least if that's out in the open everybody from all over the world visiting here is on the same page - surely got to be much better than self enforced thought crime emanating first from the USA then through the anglophone world. 

Replies please! 
Mods what are your thoughts?
(other than move to offtopic now ) 

 -j

---

### Post by haqking on 2011-11-04
The poster was at work, using scanning tools such as NMAP usually contravenes AUP of company networks.

as for telling them what is and isnt allowed it is in the forum guidelines.

---

### Post by CharlesA on 2011-11-04
If this thread is about the reason why the thread linked in the OP is closed, then create a thread in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123").

This one is closed.

---

