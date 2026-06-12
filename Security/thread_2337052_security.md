---
title: "security"
date: 2016-09-14
forum: Security
---

### Post by sunil16 on 2016-09-14
how to secure my new ubuntu system? any suggestion is appreciated.

---

### Post by wildmanne39 on 2016-09-14
*Thread moved to **Security**.*

---

### Post by Habitual on 2016-09-14
[Sound Advice.]("https://ubuntuforums.org/showthread.php?t=510812")

---

### Post by HermanAB on 2016-09-16
Ubuntu is secure by default.

All you have to do is use looooooooong passwords of at least 12 characters to keep it so and not install any crapware off random sites on the internet.

---

### Post by ltrtiger2 on 2016-09-16
> **HermanAB said:**
> Ubuntu is secure by default.

All you have to do is use looooooooong passwords of at least 12 characters to keep it so and not install any crapware off random sites on the internet.

I get what you're saying, but even so, would not a firewall and....gasp....antivirus not be good ideas....even in ubuntu??  Guess my question is what harm could it do?

---

### Post by &amp;KyT$0P# on 2016-09-17
> **ltrtiger2 said:**
> would not a firewall and....gasp....antivirus not be good ideas....even in ubuntu??
Firewall is **critical** ESPECIALLY in Ubuntu.  I personally use iptables/ip6tables, which is part of the core Linux system.  Others here have recommended other firewall programs and various simplified front-ends to iptables.

Antivirus is un-necessary as there are no Linux "viruses".  Anti-malware is not required for typical users who have taken the other steps to protect themselves.

> Guess my question is what harm could it do?
A properly-set firewall does not do any harm to the user.

As for anti-malware software, that has been discussed in [this thread]("https://ubuntuforums.org/showthread.php?t=2332576").  The harm anti-malware software does lies in how people misunderstand it.
First things first, make sure you know its capability, know what kinds of malware it'll scan for.  As noted in the other thread, most anti-malware programs on Linux are designed to scan for Windows malware but not Linux malware.  Furthermore, no anti-malware scan from a compromised system can ever be considered trustworthy.

Once you've understood that, if you treat the anti-malware scanner as only a "second opinion" - nothing more than that - you should be good there.  Treat an anti-malware scanner like a [magic egg sorter]("https://www.youtube.com/watch?v=kpgRdVBf5Qk") and it's worse than useless as you're left with a false sense of security.

---

### Post by HermanAB on 2016-09-17
A firewall is mostly a Windows thing.  It is not a magical security blanket.  It is just a packet filter which you can use to prevent packets from reaching servers.

On Linux, you have everything under your own control.  You know which services you are running.  You don't need to guard against unknown services started behind your back by Microsoft during the last update which did gawd knows what.

So, if you install the Ubuntu desktop system and you don't experiment with various servers, then you don't need a firewall - and if you know what you are doing and running one or two well controlled servers, then you also don't need a firewall.

---

### Post by &amp;KyT$0P# on 2016-09-17
> **HermanAB said:**
> A firewall ... is just a packet filter which you can use to prevent packets from reaching ...
... your computer.  Some packet types, such as IGMP, aren't needed for typical computer use, but will be used anyway unless blocked.
Reduced attack surface and all that.

> On Linux, you have everything under your own control. You know which services you are running. You don't need to guard against unknown services started behind your back by Microsoft during the last update which did gawd knows what.
More like, on Linux you know what services you installed and you *can* control pretty much everything.  You don't need to guard against new services being installed behind your back during the package updates, because, well, that simply doesn't happen to a clean Ubuntu system.

You don't know what services came default unless you're somewhat "techie" looking at system monitor and netstat, or perhaps using something like nmap.  You also don't know how those services are configured out-of-the-box unless you're somewhat techie looking at config files, man pages, and manual tests.

I've seen new Ubuntu installs come default with services such as avahi and cups installed and listening to the larger network, and un-installing them would have uninstalled a lot of the desktop.  The solution is clear.

---

### Post by HermanAB on 2016-09-19
You don't need to uninstall servers you don't like.  Just stop them.

---

