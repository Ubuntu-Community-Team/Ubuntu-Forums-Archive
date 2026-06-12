---
title: "Ubuntu Server 16.04.03 LTS - PPA issue / error"
date: 2017-09-30
forum: Server Platforms
---

### Post by gomo.dd on 2017-09-30
Hello there! I've been trying add a repository on my Ubuntu Server 16.04.03 LTS but I keep getting these errors:
[URL="https://i.imgur.com/RCO9V42.png"]https://i.imgur.com/RCO9V42.png
[/URL]Server is not running behind a proxy, nor does go it through a VPN. It's directly connected to an external Ipv4 address & I have a Apache webserver running off of it. Also, I'm not using any additional firewalls. I tried following this guide [https://itsfoss.com/fix-add-ppa-error-ubuntu-1404-linux-mint]("https://itsfoss.com/fix-add-ppa-error-ubuntu-1404-linux-mint/") and after running first command I received following message: [https://i.imgur.com/UB4eDbr.png](https://i.imgur.com/UB4eDbr.png) 

I'd appreciate your help! Thanks in advance!
-kind regards-
Gomo

---

### Post by gomo.dd on 2017-10-01
Anyone?? (iptables are pretty much empty, so it's not firewall blocking anything ..)

---

### Post by slickymaster on 2017-10-01
*Thread moved to **Server Platforms**.*

---

### Post by ajgreeny on 2017-10-01
That add-apt-repository command worked here in the UK for me even though I do not want it and immediately removed it.

Try again; perhaps this is more a temporary network problem specifically related to that ppa, ie, it was just down at that moment.

---

### Post by slickymaster on 2017-10-01
> **ajgreeny said:**
> That add-apt-repository command worked here in the UK for me even though I do not want it and immediately removed it.

Try again; perhaps this is more a temporary network problem specifically related to that ppa, ie, it was just down at that moment.
It worked for me also, which makes me believe that ajgreeny is right and must have been a temporary network glitch.

---

### Post by gomo.dd on 2017-10-01
I wish that was the case .. I've been trying since yday and keep getting same error.

---

### Post by gomo.dd on 2017-10-01
Fixed the issue. For some reason my "resolv.conf" didn't have the right DNS entries. Basically,

nameserver 8.8.8.8
nameserver 8.8.4.4

were missing. No idea how, or why. Thanks for the help tho!

---

### Post by slickymaster on 2017-10-01
Glad you got it fixed. Will you please [mark the thread as SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

