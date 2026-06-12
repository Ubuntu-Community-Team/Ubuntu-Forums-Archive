---
title: "Looking for windows-like firewall."
date: 2009-01-07
forum: Security
---

### Post by kajman on 2009-01-07
I tried to use Firestarter to configure my firewall, but there's a little problem (besides the fact that firestarter uses a lot of my CPU...) - I cannot do it well.

I was wondering if there's a firewall manager that will block everything after it installation, and then ask me for every application that tries to communicate with the internet, just like every firewall which I used on windows did.

I'm looking for something user-friendly but with a little more preferences that firestarter offers.

---

### Post by ugm6hr on 2009-01-07
Firestarter was the only one I knew which fulfilled that level of function.  However, I believe it is no longer being developed.

ufw (or gufw) is very easy to use, but it will not alert you when applications are blocked.

---

### Post by halovivek on 2009-01-07
> **ugm6hr said:**
> Firestarter was the only one I knew which fulfilled that level of function.  However, I believe it is no longer being developed.

ufw (or gufw) is very easy to use, but it will not alert you when applications are blocked.

I am using ubuntu 8.10 64 bit . will firestarter will help me fine in firewall? which alerts like zonefire alarm like windows appication for blocking and warning the internet connecting applications?

---

### Post by mcduck on 2009-01-07
There's rarely any need for application-level firewall control in Linux, since all your software comes from trusted sources so you don't need to be afraid of your programs "calling home" or spying on you in any other way.

I don't know if there's _any_ Linux firewall that would give you popups for every application trying to connect to net. For most users it's enough to allow all outgoing connections and block all incoming ones. (Actually most users don't need a firewall at all, since there is no running services that would listen to incoming connections.)

---

### Post by hyper_ch on 2009-01-07
are you really sure you need such a thing?

---

### Post by scorp123 on 2009-01-07
> **mcduck said:**
> Actually most users don't need a firewall at all, since there is no running services that would listen to incoming connections. +1!

Exactly.

---

### Post by scorp123 on 2009-01-07
> **halovivek said:**
> which alerts like zonefire alarm like windows appication for blocking and warning the internet connecting applications? What would you need that for??? :D

Let go of your Windows-thinking and those rather silly Windows habits. Enjoy your new freedom and peace of mind, OK?

---

### Post by kajman on 2009-01-07
I just feel uncomfortable with that kind of firewall functionality. I felt much safer when I knew what apps are trying to do something with the internet. And also, I think that you can never be sure that all sources are trusted... I do not always install apps through Ubuntu repositories. That is why I am a little bit concerned.

---

### Post by bodhi.zazen on 2009-01-07
> **kajman said:**
> I tried to use Firestarter to configure my firewall, but there's a little problem (besides the fact that firestarter uses a lot of my CPU...) - I cannot do it well.

I was wondering if there's a firewall manager that will block everything after it installation, and then ask me for every application that tries to communicate with the internet, just like every firewall which I used on windows did.

I'm looking for something user-friendly but with a little more preferences that firestarter offers.

Linux is not windows and things work a little different including security.

First it helps if you know a little about firewalls. I do not know your background and please excuse me if what follows is above or below your general knowledge.

Most people use a router as a firewall and if you are not running any private servers you *probably* do not need a firewall on your desktop. This is because, unlike windows, with a default installation of Ubuntu, there are no open ports, so there is nothing to firewall.

The firewall in Linux is iptables and it is quite powerful, but difficult to learn.

The default configuration tool in Ubuntu is ufw. If you want a gui use gufw.

If you want an application level "firewall" the closest thing is apparmor.

If you are new to Ubuntu from windows I suggest you sit back and relax for a minute as Ubuntu is much more secure and take the time to learn how the OS works. I suggest you start with the stickies at the top of this forum.

Edit: Moved to the security section.

---

### Post by kajman on 2009-01-07
Too much time with windows made me paranoid perhaps.
Thank you all for your interest and help.
I'll try to relax and read some more as bodhi.zazen suggests :)

---

### Post by donkyhotay on 2009-01-07
I don't think you're going to find anything like that for linux. First of all it isn't needed. Being notified of every time your firewall blocks something isn't required for a standard desktop because there are no services running. If you were running a server and needed to keep track of that stuff you could configure your custom iptables script to output to a log file. Honestly though that can be very complicated and as I mentioned completely unnecessary unless you're planning on running your own server.

---

### Post by darkchris1991 on 2009-01-08
Black ice I think they used to do a Linux firewall version.

---

