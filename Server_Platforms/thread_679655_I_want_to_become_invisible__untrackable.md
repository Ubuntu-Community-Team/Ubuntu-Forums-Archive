---
title: "I want to become invisible / untrackable"
date: 2008-01-27
forum: Server Platforms
---

### Post by the8thstar on 2008-01-27
Hello,

Thanks to the many nuts and bolts given in this forum, I think I've achieved a pretty comfortable level of security for my machine.

Maybe I'd like to go up one notch in securing my PC and now I want to know if there is a way to become invisible, i.e. untrackable. Ultimately I don't want to annoy anybody or sneak on anyone's business, I just don't want to be bothered or sniffed - EVER. Yet, I want to surf the web (meaning use cookies, java and flash when needed) and use programs like Skype occasionally.

Does such config exist? Do I need to set specific parameters in my network manager or in my web browser? Are there programs out there that do that?

For the record, I often use VirtualBox with virtual XP Pro SP2 partition. I want to be able to access the web to perform updates and maintenance in that too.

---

### Post by aashay on 2008-01-27
Dunno if it answers the question, but search google for "tor"

---

### Post by amo-ej1 on 2008-01-27
One extremely simple thing you can do is:

```

sudo echo 1 >  /proc/sys/net/ipv4/icmp_echo_ignore_all

```

or edit /etc/sysctl.conf to add this, this will instruct your kernel not to respond to ICMP echo requests. A portscanner (take nmap as an example) will in a default configuration first use an icmp probe to check if a host is alive. This test will fail and if someone is portscanning ranges they will skip your host.

The same can be accomplished using iptables. You could also setup iptables to block all incoming connection. And the easiest 75$ solution is buy a cheap access-point/router which will perform all these tasks for you. (Hence, make sure your pc is not directly accessible from the internet. )

---

### Post by the8thstar on 2008-01-27
Thank you guys for your feedback!

---

### Post by FakeOutdoorsman on 2008-01-27
As for browsing with Firefox here are some good privacy related extensions:

[Adblock Plus]("http://adblockplus.org/"): helps block ads that may track you. It's effectiveness is based on the filters/rules you use.

[Cookie Culler]("http://cookieculler.mozdev.org/"): manage what cookies are kept or removed. Very useful.

[NoScript]("http://noscript.net/"): blocks javascript, etc. Lets you decide which pages can use various scripts.
[URL="http://www.stardrifter.org/refcontrol/"]
RefControl[/URL]: manage what the browser sends as the HTTP referrer.

[SafeCache]("http://www.safecache.com/"): Defends against cache-based tracking.

[SafeHistory]("http://www.safehistory.com/"): Defends against visited-link-based tracking.

[Torbutton]("http://freehaven.net/~squires/torbutton/"): Easily use tor with Firefox.

---

