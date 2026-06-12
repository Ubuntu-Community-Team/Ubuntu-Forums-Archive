---
title: "What's your preferred Internet Security software?"
date: 2008-03-23
forum: Windows
---

### Post by twin_57103 on 2008-03-23
I'm building a new machine and debating on which internet security software to use.  This will be a fast computer, despite running Vista (AMD Phenom quad core 2.2GHz, 4 Gb RAM).

Hence, my question: what do you prefer as a (comprehensive) internet security option for Windows with high-speed internet?

---

### Post by seanc7 on 2008-03-23
For free antivirus I recommend AVG or Avast.

For pay-for antivirus I recommend Kaspersky.

For software firewall: Comodo personal firewall

For antispyware: Spybot S&D, Adaware and might as well run Windows Defender too, it comes with Windows so why not.

For rootkit scanner: Rootkit revealer - it's owned by MS but I think they left it alone though (ie: they didn't "Microsoft" it). I don't know any other ones for Windows but I know there are a few others.

I also recommend making sure your box is behind a hardware router/firewall as well.

---

### Post by Kernel Sanders on 2008-03-24
With Vista you really don't need antivirus unless your planning on turning UAC off.

After all, with UAC on you have to manually allow something mallicious to run.

---

### Post by LaRoza on 2008-03-24
Use a restricted account and be smart.

Anti virus for home users is pointless, and a bad security model.

---

### Post by LookTJ on 2008-03-24
I use Avast(free antivirus) and Spybot S&D(antispyware). For user accounts, type in the Run prompt "control userpasswords2" and either use power users(standard users group) or restricted user groups. Don't use administrator power on daily account basics. Only on installation of trusted software and drivers, as well as Windows Update. 

Good Luck!

EDIT: also I don't use software firewall because I'm behind a router, which is my firewall.

---

### Post by Shazaam on 2008-03-24
WinXP programs (installed before I found linux).......
AV= Avast
Anti-spyware= Spybot S&D
Firewall= Zone Alarm Pro (ver.4.5)
NoScript and AdBlock for Firefox
Forensics= HijackThis, CProcess, AutoRuns, AccessEnums, CwShredder and RootkitRevealer.
Net stuff= nmap, SamSpade

Ubuntu apps=
Noscript and AdBlock for Firefox
FireStarter
iptraf

---

### Post by jesusfreak107 on 2008-03-24
Free: AVG
Paid: PcCillin 2007 ( I think the Vista version is "PcCillin 15")

---

### Post by rsarvi on 2008-03-25
NOD32 is small and sexy

---

### Post by Calash on 2008-03-25
AVG, it is light weight and does a good job.

IMHO firewall software is a bit overrated and does not do a good job for the performance price you pay.  The built in Windows firewall is what I would use, if any at all.

Limited user accounts are best, but it can be difficult to support if not in your own house.  However I do recommend them wherever possible.

---

### Post by LaRoza on 2008-03-25
> **Calash said:**
> 
IMHO firewall software is a bit overrated and does not do a good job for the performance price you pay.  The built in Windows firewall is what I would use, if any at all.

Limited user accounts are best, but it can be difficult to support if not in your own house.  However I do recommend them wherever possible.

What? Comodo firewall is better at protecting computers than any antivirus that I have seen. It is very powerful, and doesn't waste RAM. It is also better than Windows firewall.

Antivirus is like a minesweeper, very useful for finding nasties. However, a home computer is like your backyard. There shouldn't be mines in there! File/Mail/Web servers need AV, but home computers don't.

If you have to be looking for malware, your security model is poorly designed. It shouldn't be there.

---

### Post by Kernel Sanders on 2008-03-25
> **LaRoza said:**
> Use a restricted account and be smart.

Anti virus for home users is pointless, and a bad security model.

Indeed, although Vista comes with a restricted account by default.

I'm finally glad to use a Windows machine with a similar security model to Linux and OSX!

IE7 sandboxed? Check.
Having to manually allow something malicious to get into your system? Check.

Still prefer my Ubuntu though :guitar:

---

### Post by Calash on 2008-03-25
When running a firewall software, it is only as secure as the OS it is working on.  If the OS is flawed, your firewall is flawed.

If it is important enough that you need a security model for your supported systems, then you should be looking at a hardware based firewall solution.

Again, this is my opinion based on my experiences.

---

### Post by sub2007 on 2008-03-25
I do agree with you LaRoza, in my opinion a firewall is your first and last defence and if you only have one piece of security software it should be a firewall. I would never allow a PC on the Internet without a firewall, thankfully I have a hardware firewall but I would still use something like Comodo. The Windows XP firewall is only one way, so it will stealth the ports but won't stop anything getting out. Comodo firewall will block both incoming attacks and outgoing ones, including all the leaks that malware can exploit and so if you did happen to get a keylogger or a dropper then you would know straight away (even if your antivirus didn't detect it) and be able to block it's access with the Internet.

I used to Avira AntiVir antivirus (free) on Windows but it never caught anything and so a lot of the time I did question why I was running it. It's just one of those things that you feel like you have to run and I would still recommend everyone runs one as it least it will catch something if something manages to get in. People will still continue to fall victim to social engineering and so I think on Windows you should run it just because you have a high chance of catching something. And yes, it's probably too late if your a/v does catch it but it's better caught than not caught, in my opinion.

However you should be aware that **antiviruses can't catch everything** and many people are shocked. You suggest their PC may be infected and they say "oh no it can't be, I have Norton" even though it's 2002 version and their subscription has lapsed... even if you are up to date today then you're A/V will still miss most of the newer viruses because, short of using it's heuristics, it will only catch things that it has signatures for. 

Antivirus is, in my opinion, insurance - you probably will never need it but when you do need it you'd be glad you had it. But I see no reason in spending money on one when the free ones do just as good a job. And if you are catching lots of things with your antivirus then it really is time to reassess your surfing habits.

---

### Post by LaRoza on 2008-03-25
> **Kernel Sanders said:**
> Indeed, although Vista comes with a restricted account by default.

I'm finally glad to use a Windows machine with a similar security model to Linux and OSX!

IE7 sandboxed? Check.
Having to manually allow something malicious to get into your system? Check.

Still prefer my Ubuntu though :guitar:

No, it is the admin account and it does everything it can to annoy you into turning UAC off. It tries, but doesn't quite get there.

Comodo is better IMO, as it has such security features that restrict access to certain parts and programs and is a firewall.

> **sub2007 said:**
> I do agree with you LaRoza, in my opinion a firewall is your first and last defence and if you only have one piece of security software it should be a firewall. I would never allow a PC on the Internet without a firewall, thankfully I have a hardware firewall but I would still use something like Comodo. The Windows XP firewall is only one way, so it will stealth the ports but won't stop anything getting out. Comodo firewall will block both incoming attacks and outgoing ones, including all the leaks that malware can exploit and so if you did happen to get a keylogger or a dropper then you would know straight away (even if your antivirus didn't detect it) and be able to block it's access with the Internet.

However you should be aware that **antiviruses can't catch everything** and many people are shocked. You suggest their PC may be infected and they say "oh no it can't be, I have Norton" even though it's 2002 version and their subscription has lapsed... even if you are up to date today then you're A/V will still miss most of the newer viruses because, short of using it's heuristics, it will only catch things that it has signatures for. 


Yes, that is one reason they are flawed.

---

### Post by rickyjones on 2008-03-25
I use AVG for my antivirus. If I need a software firewall I just use the Windows Firewall. It blocks all incoming connections by default which is what I want/need.

I'm usually behind a NAT router anyways, so an extra third party firewall is more clutter than I need.

-Richard

---

### Post by ax1m on 2008-03-25
I agree with sub2007.

I always have a firewall enabled and do not use any antivirus software. There's nothing wrong with AVG, but I don't believe it is necessary. 

The golden rules as far as I see it are: 

> Do not use Internet Explorer: use Firefox, Opera or similar.

>Do not visit the darker, murky corners of the internet and download dirty things or click "yes" to anything random.

>Do not download "free trial" offers for unheard-of antivirus programs.

>Do not use Limewire. (If you must pirate stuff use torrents from a reputable server [e.g. thepiratebay]).

>Use a mail server with good filters and firewall

All the infections of XP I have ever come across have been smitfraud infections for which there are a number of fixes, the best being smitfraudfix by s!ri. 

I have fixed at least 10 different XP boxes for people using this software and nothing else.

---

### Post by blane2 on 2008-03-26
Kevin Mitnick was one described by the Department of justice as  "the most wanted computer criminal in United States history."
He's since become a computer security consultant, and what follows is a list of his security advice taken from wired.com

You can run a search on Kevin Mitnick if you'd like to know just what makes him an expert on such matters if you'd like. here is his advice.

    * Back up everything! You are not invulnerable. Catastrophic data loss can happen to you -- one worm or Trojan is all it takes.

    * Choose passwords that are reasonably hard to guess -- don't just append a few numbers to a no-brainer. Always change default passwords.

    * Use an antivirus product like AVG or Norton, and set it to update daily.

    * Update your OS religiously and be vigilant in applying all security patches released by the software manufacturer.

    * Avoid hacker-bait apps like Internet Explorer and disable automatic scripting on your e-mail client.

    * Use encryption software like PGP (pretty good privacy) when sending sensitive e-mail. You can also use it to protect your entire hard drive.

    * Install a spyware detection app -- or even several. Programs that can be set to run frequently, like SpyCop, are ideal.

    * Use a personal firewall. Configure it to prevent other computers, networks and sites from connecting to you, and specify which programs are allowed to connect to the net automatically.

    * Disable any system services you're not using, especially apps that could give others remote access to your computer (like Remote Desktop, RealVNC and NetBIOS).

    * Secure your wireless networks. At home, enable WPA (Wi-Fi protected access) with a password of at least 20 characters. Configure your laptop to connect in Infrastructure mode only, and don't add networks unless they use WPA. 

--------------------------------------------------------------------------

aside from that, any determined hacker will still find a way in. The whole idea is to make it as hard as you can, most hackers won't jump through hoops to get at you if all the doors are locked. Since there are plenty of people who leave their doors wide open.

---

