---
title: "[SOLVED] redirected to &amp;quot;spyware&amp;quot; site"
date: 2008-12-25
forum: Security
---

### Post by octopusfinley on 2008-12-25
Hey there all. I'm starting to get pretty worried about my laptop security here so I thought I'd make a little post about it. I've been redirected to a site that supposedly detects viruses on my computer and therefore urges me to download their virus detection software for Windows,which I of course am not going to do. I obviously have ubuntu so that is besides the point, but this has happened with the same site in two different locations. I'm minding my own business on the computer and suddenly my page is redirected to this site. I'm wondering if this could indicate a possible virus and if there's a way for me to check for viruses. I'm running ubuntu 7.10--haven't upgraded yet. I also have a partition where I've got Vista rotting away somewhere in my harddrive, don't know if that's a possible in for a virus. Anyway, opinions and advice would be appreciated.
thanks all,
Finley

---

### Post by cariboo on 2008-12-25
If the site wants you to download Antivirus 2009, you have nothing to worry about, except to stay away from web sites that redirect to that site. This has been discussed several times in this forum. You can download the file all you want, but you can't install it. If you had done this in Windows, you'd have been in for sevral hours of work to repair the problem. :)

Jim

---

### Post by octopusfinley on 2008-12-25
hey thanks for the feedback, I know it can be a bit annoying to have the same questions asked over and over again but i am a serious noob so what's there to do? anyhow, that's a relief. 
thanks
finn

---

### Post by octopusfinley on 2008-12-25
though to be truthful, I'm not sure what it was wanting me to download. If it was something else would it affect me?

---

### Post by cdwillis on 2008-12-25
I don't think it's anything you should worry about. What site is redirecting you to this spyware site?

---

### Post by Kinstonian on 2008-12-25
Are you using a popular home router such as Linksys that is using the default password?  If so, you could be a victim of a [drive-by pharming](http://www.symantec.com/avcenter/reference/Driveby_Pharming.pdf) attack, where malicious javascript from a website was used to login to your home router with a default password and reconfigure its DNS settings.

---

### Post by octopusfinley on 2008-12-25
it's happened twice on two completely unrelated sites. The first time was several weeks ago and I don't remember the site, but I was already at it. That is, I was looking around on the website for a good ten minutes and then suddenly I was redirected. Today I was on google doing a search for how to hook up my laptop to a tv and I think it redirected me pretty much as soon as I clicked the link. Again, I am unforunately not quite sure what website it was. i obviously need to pay a bit more attention to these things. another thing, the site seems to know what city I'm in and the IP address, though part of that is covered up so I suspect it doesn't actually know the whole thing.

---

### Post by Sprut1 on 2008-12-25
> **octopusfinley said:**
> though to be truthful, I'm not sure what it was wanting me to download. If it was something else would it affect me?

I am not at all an expert on this, but I found some information about general security for you:

From this link: [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064) (HowTo AVG Antivirus for Ubuntu)

```

Q: Is viruses, trojans and malware a threat to a linux system as in Windows?

A: No, there's a very few viruses to linux and the way a Linux/unix is build up makes it difficult to do any serious damage to the system, in fact I've never heard from people who got their Linux/unix system infected.

Q: So why install a anti-virus application/program?

A: For an ordinary Linux Home user with only one OS system their's no need for Anti-virus, but people who's running network, server or dual booting with win OS this tool can be very handy to scan and delete viruses.

Q: I'm a home user only running Linux do I need it?

A: No, a firewall is way better as protection in that case.
```

Here's a article about security: [http://www.psychocats.net/ubuntu/security#firewallantivirus](http://www.psychocats.net/ubuntu/security#firewallantivirus) (Ubuntu Security)

Article from these forums: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) (There are plent of these, just search around)

I may add that as long as you don't run anything you don't know what is, specially as super user and just be carefull about what you download you'll be fine.

---

### Post by octopusfinley on 2008-12-25
I'm using wireless on both occasions, the first is through my university, so I don't know what router they're using. this time...well...I'm not sure. It says trendnet on the box and there is no mention of linksys. as I said, I'm really very uneducated so I'm basically unsure of what your post said. what's the danger in this drive by pharming deal? and with reconfiguring the DNS settings? what am I looking at here?

---

### Post by octopusfinley on 2008-12-25
thanks for these links. i'm in a paranoid stage of computer security craziness and this is very helpful.

---

### Post by cariboo on 2008-12-26
Have a look [here]("https://forums.symantec.com/t5/Emerging/Drive-By-Pharming-How-Clicking-on-a-Link-Can-Cost-You-Dearly/ba-p/305917;jsessionid=8842B3D4F94BFE85BBFFF5B49D0A9E29#A42"), for an explanation of driveby pharming. If you are a normal user that is aware of what you are doing this shouldn't be a problem. There are occasions where a script can change your DNS, but because you are asking question, it means that you are aware that there are bad things out there on the internet.

Use linux, and be cautious, all the things that affect windows, don't usually have any effect in Linux.

Jim

---

