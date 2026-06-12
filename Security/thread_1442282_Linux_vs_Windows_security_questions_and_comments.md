---
title: "Linux vs Windows security questions and comments"
date: 2010-03-29
forum: Security
---

### Post by jedispork on 2010-03-29
So I've been told no system is hack, or virus proof. However from my understanding linux seems to get you the closest to it with a responsible user. I've been trying to find out why linux is more secure and did some googling about it.  No registry and changes need to be made by root which is password protected thus making it harder for stuff to install itself and propagate through the system.  The other big reason is that linux is not a profitable target because of the lesser user base.

So I was wondering if hackers went all out, like they have done on windows could linux take the heat? Will we eventually need anti virus software and if so will there be enough people still willing to work on everything and keep it free? I've also heard that macs have less problems for similar reasons like the smaller user base but Apple takes even longer than windows  to close holes because they count on them not being exploited. 

I came across a newsgroup discussion about windows security vs linux security and it made me want to ask some questions. In windows the admin account can still be passworded to block changes. Also I would think not hosting internet services (advice from a linux guy) applies to any type of o/s. I also make sure all ports are closed on my router.  The nicer anti virus software for windows is now coming with web guards to check websites for malicious code and I hear it works quite well even with 0 day threats. I combine this with malware domains sub through ad block or a hosts file. 

There are plenty of reasons not to like windows or microsoft but I think many people are misinformed and lay 100% of the blame on windows for being a malware target when part of the reason is simply because it has the largest user base.

Thanks for reading and please correct me where I'm wrong.

---

### Post by Ijan on 2010-03-29
Lol, thoroughly worded post but still the title might be enough to trigger a flame war. ;)

> **jedispork said:**
> So I was wondering if hackers went all out, like they have done on windows could linux take the heat?
Apart from all the safe by design discussion there is by now still nothing as bug free software. So security will AFAIKS stay a find-exploit-and-fix-a-bug race.
So a fictional increase in attack scale would of course make a lot of additional work but projects with the userbase to make such profitable would probably by then have that manpower and maybe even profit from all the outsourced security testing. ;)  
> There are plenty of reasons not to like windows or microsoft but I think many people are misinformed and lay 100% of the blame on windows for being a malware target when part of the reason is simply because it has the largest user base.
Open secret ;) Poor Steve Ballmer, the Linux users can be such a mob ;) But then I would feel maybe even more pity if Microsoft didn't promote their new secure-by-design image by insinuating that that bazar-soft was insecure-by-principle.

The open-internals-structure of Linux makes it extra easy to learn and see about security yourself and forget about the propaganda.

---

### Post by Agent ME on 2010-03-29
I hope this post isn't too all-over-the-place, but I hope it explains the possible security threats to computers.
Windows security threats have often come from exploits in browsers, remote exploits, and trojans.

Browser exploits are when websites have code that when visited, try to trigger a bug in your internet browser to gain access to your machine. All major browsers have had exploits, but usually the exploits have to be tailored to the operating system of the intended victim, and nearly all exploits in the wild have targeted windows.
It is possible that websites could use future exploits to target other systems such as linux, but linux systems vary much more than windows systems (such as where they store settings and user files, and some linux systems don't use x86 processors) making this a bit more difficult in some cases. If linux picks up in popularity much, browser exploits are the thing to watch out for.
It's possible on linux to use AppArmor to prevent your browser from ever able to be tricked into to accessing your user's files outside of what it needs to use, but I'm not too sure how to do this.

Remote exploits are when systems over the internet connect to your computer by themselves, and exploit some bug to gain access. In the past, this used to be common against windows computers, but now most bugs have had fixes delivered in automatic updates. The main problem now is computers with misconfigured or unsecured server programs running: if you enable remote access via SSH or VNC to your computer (windows, linux, mac, doesn't matter) and have a weak password, it's often only a matter of time before the password gets cracked and your system accessed.

Trojans are programs that are advertised to have some wanted function, but act similar to a virus in the background when run. Often web advertisements for "Free screensavers!" lead to windows programs that act as trojans.
On linux, a number of factors prevent this sort of attack from being widespread.
Most programs for linux follow linux's own example, and are open source projects. When all of the source is given, it's much harder for a virus to be snuck in.
Many linux distributions (including Ubuntu) use software repositories, consisting mainly of open source software that is all inspected to be safe, as the main place to go for installing new things, whereas windows users often install programs from random websites that aren't inspected by any trusted authority.

---

### Post by HermanAB on 2010-03-30
Linux being a smaller target or a less interesting target than Windows is a fallacy.  First of all, there are many more Linux systems out there than Windows systems - yes that is correct - there are more than 2 billion Linux devices in use, vs less than 1 billion Windows devices and each year about 350 million Linux devices are produced.

Linux servers are also a very attractive target, since they tend to to be connected to high bandwidth intertubes, so a compromized Linux server can send much more spam than a compromized Windows desktop.

---

### Post by a.walker on 2010-03-30
In general, people's vices (viewing/downloading porn; pirating music, movies, and software; etc.) cause more security problems than their computer's OS.

---

### Post by Nisal on 2010-03-30
at the moment i belive linux is safer than windows because lot of hackers targeting windows because there a ton of ppl who using windows than linux..

but after all it will be a matter of time ..when ppl get in to more and more to linux hackers and crackers also put more attention on linux...

after all NOTHING is secure you are the person who must make it secure from regular updating systems being awake for threats

---

