---
title: "What can vmware do?"
date: 2006-10-20
forum: The Cafe
---

### Post by The Soundophiliac on 2006-10-20
I've been wondering, what are the real capabilities of vmware? How slow is it? What works, what doesn't? Would it be a plausible tool in a demanding environment such as audio production?

Thanks

---

### Post by .t. on 2006-10-20
VMWare is like XEN. It is a virtualisation tool, sending commands from the programs run in its "sandbox" to the host CPU. It doesn't do any emulating, so is almost native speed, but it has to translate hardware accesses, which slows it down. It doesn't do 3D acceleration, but apart from that, it's like having another of your PC on at the same time.

---

### Post by AndyCooll on 2006-10-20
Well VMware can run full OS's. I use it to look at the various alternatives out there: Debian, Fedora, SUSE, ReactOS, FreeBSD etc.

I also have an XP image which I use to play Football Manager ...and the game plays great, hardly any noticeable lag at all. FM is a number crunching game so that's ok. Where you might struggle with VMware is if the app requires a powerful graphics card. VMware doesn't use your own card capabilties but rather its own "virtual graphics card". And this is the equivalent to a bog standard card.

:cool:

---

### Post by bdb on 2006-10-20
I use vmplayer, which is the equivalent to adobe acrobat.  It lets you use virtual pcs but not make them.  

I use it for windows xp development. It runs fast enough to use Visual Studio 2005 with asp.net and sql server. Of course you need alot of ram to do that. I just upgraded to 2GB.

---

### Post by maniacmusician on 2006-10-21
> **The Soundophiliac said:**
> I've been wondering, what are the real capabilities of vmware? How slow is it? What works, what doesn't? Would it be a plausible tool in a demanding environment such as audio production?

Thanks
No, it cannot be used for audio production. at least not on linux. it's because the kernel isn't patched to give apps realtime access (or something like that). if your computer isn't set up and configured for audio on normal plain linux, you wont be able to do it with vmware either. it's really mostly just for testing unstable OS's or trying out an OS just for fun.

---

### Post by ngms27 on 2006-10-21
It not just for trying out. It's totally viable for real world apps.

I have done the following:

Designed and created an IT Service Desk case logging system including measuring against SLAs full accoutability etc using Apache, PHP5, Mysql, PhpMyAdmin, Openssl, Active Directory authentication.

This has a web front end, uses SSL etc and runs in 256MB on a Windows 2003 Server on top of its existing apps. You wouldn't now the Virtual Appliance was there and you have to see it to realise how fast tis works. Click a button on a web page, and bang its there including MySql having to do some complex queries.

I have also created a fully featured Email Server with Virus Scanning, Spam filtering, POP3, SMTP, Webmail etc and it just has to be seen to be beleived.

So VMWare is the way of the future. Virtual Appliances will run on beefy servers thus reducing hardware costs.

You can probably get away with four Appliances on a single Windows / Linux server now as long as it has enough RAM. Of course the real beauty is that the appliances can simply be stopped and pasted over to another Server if performance becomes a problem.

Business is now going down this route big time using VSX where you can host many Appliances on one box.

THIS IS THE FUTURE

JonnyT

---

### Post by djsroknrol on 2006-10-21
VMware saves me from rebooting into MS just to run the few programs that I need and can't run in Ubuntu...

---

### Post by deepwave on 2006-10-21
VMWare lets me play around with new linux distros without borking my system.  It also lets me run Windows 98 (hate it but some legacy progs need it)... mostly safely too.  And I use it for my security course, so I can have sandboxed insecure Linux system that I can trash... without trashing my primary desktop.

---

### Post by hanzomon4 on 2006-10-21
You may be able to use it for audio, but you need to get vmplayer or vmware workstation as vmware server doesn't support audio. I wouldn't use it for audio work and I think the latency would be hell even with a patched kernel.

I only use vmware server for playing around with the opensolaris ubuntu clone [Nexenta]("http://www.gnusolaris.org/gswiki"). I might start using vmplayer for the sound support.

---

### Post by djsroknrol on 2006-10-22
> **hanzomon4 said:**
> You may be able to use it for audio, but you need to get vmplayer or vmware workstation as vmware server doesn't support audio.

That's not entirely true...I'm running VMware server on Dapper with full sound and USB support.

It depends on if your hardware is supported by your host system...

---

### Post by hanzomon4 on 2006-10-22
How did you set it up, I got sound in edgy

---

