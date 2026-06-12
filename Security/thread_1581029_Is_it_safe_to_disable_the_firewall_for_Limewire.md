---
title: "Is it safe to disable the firewall for Limewire ?"
date: 2010-09-24
forum: Security
---

### Post by ontherooftop on 2010-09-24
Hi I opened a specific port in my router and manually configured Limewire to use the same port for all traffic, but I notice when I disable and turn off Firestarter when on limewire, my searches go really fast and dowaloads zoom really fast also I am not running as root. Is this ok to temporarly stop the firewall when I am on Limewire and then turn  it back on when finished?

---

### Post by CharlesA on 2010-09-24
You don't really need a firewall on a normal desktop machine since there are no listening services by default.

You can turn off the firewall, but it's up to you.

I'd recommend using ufw or gufw as firestarter is no longer under development.

---

### Post by ontherooftop on 2010-09-24
How about gaurdog, I just need some thing to turn off the default firewall temporarly with a gui. I am currently just using firestarter for that reason , because the router firewall is good enough and I have no access enabled on desktop and good password. My rkhunter also is fine with 1 warning false positive.

---

### Post by CharlesA on 2010-09-24
Never heard of it, so I can't vouch for it.

---

### Post by pricetech on 2010-09-24
<farce>
Yes, disable your firewall and post your IP so everyone will know it and politely leave you be while you limewire.
</farce>

I don't drop my firewall for anybody or anything.  I don't use a software firewall since I have a very solid hardware firewall which keeps out the bad guys.  If you're behind a good hardware firewall, and you haven't "poked holes in it" then you don't even need a software firewall on your computer.

---

### Post by uRock on 2010-09-24
> **CharlesA said:**
> You don't really need a firewall on a normal desktop machine since there are no listening services by default.

You can turn off the firewall, but it's up to you.

I'd recommend using ufw or gufw as firestarter is no longer under development.
+1 I would never recommend out-of-date software, especially for security applications. GUFW will allow you to open the necessary ports and get back to being productive.

---

### Post by Bachstelze on 2010-09-24
> **CharlesA said:**
> You don't really need a firewall on a normal desktop machine since there are no listening services by default.

You can turn off the firewall, but it's up to you.


The point here is that limewire does listen.  Personally, I think it would be a very bad idea to turn off the firewall.  Limewire is closed-source, no one can review its security.  There are a lot of Linux exploits around recently.  What if there's a security hole in limewire and someone uses it to run a root exploit on your machine?

---

### Post by CharlesA on 2010-09-24
> **Bachstelze said:**
> The point here is that limewire does listen.  Personally, I think it would be a very bad idea to turn off the firewall.  Limewire is closed-source, no one can review its security.  There are a lot of Linux exploits around recently.  What if there's a security hole in limewire and someone uses it to run a root exploit on your machine?

I always run firewalls on my machines, since you can never be too careful.

If you are running something that needs other ports open, and you don't open them to protect your machine, you will just have to deal with the slow speed.

If you want full speed, open the ports and open yourself up to the world (so to speak).

It's the same thing with torrents. However, if the firewall is set to accept "established and related" connections, it shouldn't give you that many problems. It'll allow established connections and related connections, but not accept new connections.

---

### Post by Bachstelze on 2010-09-24
> **CharlesA said:**
> I always run firewalls on my machines, since you can never be too careful.

If you are running something that needs other ports open, and you don't open them to protect your machine, you will just have to deal with the slow speed.

If you want full speed, open the ports and open yourself up to the world (so to speak).

It's the same thing with torrents. However, if the firewall is set to accept "established and related" connections, it shouldn't give you that many problems. It'll allow established connections and related connections, but not accept new connections.

The problem is limewire. It's, to say the least, a quite shady program.  BT clients, especially open source ones, should be reasonably safe to use with open ports. I wouldn't say the same of limewire.

---

### Post by CharlesA on 2010-09-24
Agreed. I would not touch limewire with a 10-foot pole.

---

### Post by perspectoff on 2010-09-24
Although it is not under current development, Firestarter is easier to control and more intuitive than ufw (even with the gufw GUI). Further, Firestarter has been stable and rock solid for years. Firestarter is not iptables, anyway, which is the real firewall. It is merely a tool to change, edit, and enforce or temporarily suspend iptables rules on the fly. iptables is continually developed and supervised as part of the Linux kernel, so the strength of security comes from iptables (not from Firestarter).

To assert that no "services" use ports by default is a bit limited in vision. All programs that interact with the Internet use ports. Program updaters use ports (including in Ubuntu) in the background.

Firefox, filetrading services like Limewire and BitTorrent, many games, video and audio streamers (including all multimedia players), social services (IM chat, etc.), and many other apps all use a variety of ports to exchange data. Many of these programs/apps use several ports simultaneously, in fact, and use a rotating selection of ports. This increases the speed of their data exchange, so if the firewall (iptables, using ufw or Firestarter) is turned off, there is a substantial increase in speed while using these apps (Firefox, Limewire, etc.). In fact, you often must do this just to get some of these programs to work properly in the first place.

Now, Firefox has a fallback mode to use only ports 80/443 (the traditional ports for web browsing) if all the other ports are closed by the firewall. This noticeably slows down Firefox since all traffic must then generally squeeze through these two ports.

Many program/app updaters also "listen" in the background (or at least constantly connect to a home location on the Internet), including those for Firefox and (K)Ubuntu itself. Many apps also put in "homing beacon" code (heck, Ubuntu was even in the news for planning this, recently), and it is theoretically not very difficult to open a backchannel. (Many antivirus programs in the Windows world do this, and Windows itself does this as part of its .NET structure).

A user must therefore choose speed and ease of connectivity over control and monitoring. Some users throw caution to the wind and open up all their ports and trust in their applications not to infiltrate his system. For many users this probably is ok.

But when surfing the web, malicious websites can and will scan for open ports on your computer and some malicious sites will then attempt to run Java, Javascript, or other applet code through these open ports. They may attempt to store code (and data) by piggybacking onto other programs you might happen to be running (like IRC, Torrent traders, IM chat, and others), so they usually concentrate on open ports commonly used by these programs.

Malicous code hackers have concentrated on the Windows platform for many years (and there is a reason 75% of Windows computers have some malware on them, of major or minor significance). While the Linux operating system has been intrinsically more secure (due to a stricter permission paradigm for critical systems modules), the apps themselves do not always necessarily share the same level of security. These apps may have the same intrinsic weaknesses as their Windows counterparts.

How would it be if you had Limewire running while surfing the net, and you encountered a website that recognized your open Limewire ports and then started downloading packets through your open ports onto some unprotected folder on your system, without your knowledge? Code could then be stored in these folders that could be accessed the next time you were to visit another malicious website searching for that same stored snippet of code. Can't happen in Linux? Righttt....

(Look, I was also assured when I was young that the banks were safe, there can't be oil spills, and that global warming isn't happening. It didn't stop me from losing tens of thousands of dollars in wall street scams, my bank's investment portfolios, and in real estate. I am also watching glaciers disappear and my local summertime temperature increase 10 degrees over the past few years.)

Backdoors can be installed on any system. Perhaps not as part of the intrinsic operating system (where root privileges are usually needed to install or change modules), but they can be there nevertheless.

Do I trust Ubuntu and all the open source applications that I use not to do this? No I don't. Ubuntu tried to recently install homing code in its distro. While I like Debian and Ubuntu and trust the developers for the most part, development is a diffuse process and there's a lot of code in aggregate, all of which can't be checked by the Debian/Ubuntu teams. It doesn't take much to slip in a few lines of malicious code somewhere.

(It is often said in the Linux world that code is open and many people are always looking for this, but in reality there are at best only a few thousand people conversant with all the code who can really find it easily, and they are pretty busy people. The concept of a zero-day attack means code is inserted and used before people ever find it.)

Perhaps these are remote possibilities, but the nature of hacking is to exploit remote possibilities. Malicious intruders try to use already-running programs to attempt intrusion, despite some users' blithe assurances. (That's how it is now done in Windows, where .DLL files are a major location of malware.)

Does using a Firewall prevent this? No. To use any Internet program the ports relevant to that program must be open. All that a firewall does is allow you to choose when to open the ports and when to close them so that data exchange from your computer to the Internet doesn't occur without your vigilant permission (or knowledge).

I prefer this level of control on my computer (and in general), and if you read today's news, there are many articles on the need to control your data in these days of insecure cloud computing services (of which Limewire is a type).

I use (K)Ubuntu for a variety of purposes. I use it on some computers for business. I use it on some computers for games. I use it on some computers for servers. I use it on some computers for exchanging data through Torrents. Each of these uses entails a different security paradigm and different risks.

My servers, for example, are the most locked down and do not connect to any other part of the LAN. This is enforced by iptables' firewall rules (using Firestarter or ufw to manipulate iptables).

I never, ever keep any personal or sensitive information on any computer that can trade files (such as Limewire, IM chat, IRC, etc.) or on which all the ports are flung wide open <snip>. In fact, my computers/hard drives that have really sensitive data don't connect to the Internet at all, except occasionally through secure proxies (and then only under very specific firewall-controlled conditions).

What I do instead is install a separate instance of (K)Ubuntu in a quarantined partition. I use this quarantined instance of (K)Ubuntu to run Torrent programs or online games, or any other Internet program in which file exchange is possible.

I don't run these types of apps from my primary (K)Ubuntu installation, and certainly not on the (K)Ubuntu installations that have servers or anything with private data on them.

The quarantined instance of (K)Ubuntu can be installed within a virtual machine, as well, but this is intrinsically slower and somewhat more complicated. It is a good solution, though, if you are familiar with virtual machines.


------------------------------------------

"Ostriches don't make good security advisors. You don't always have to wear a Kevlar vest, but it is worthwhile to recognize the situations in which one might be needed."

---

