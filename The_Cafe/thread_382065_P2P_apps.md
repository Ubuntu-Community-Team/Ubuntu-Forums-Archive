---
title: "P2P apps"
date: 2007-03-11
forum: The Cafe
---

### Post by ubageek on 2007-03-11
the other day I did "sudo apt-get install gtk-gnutella" to get some P2P software and it works fine, well I mean it will load up, the only problem is that I cannot connect to other hosts or the servers, or whatever you connect to, I can't connect to it. I had this installed on my system before and it connected then but I have to get a new hard drive because my first one crashed, and I just feel that I haven't installed something, can any one help.

---

### Post by lloyd_b on 2007-03-11
First off, how long did you wait after starting GtkG?  With a fresh install, it can sometimes take 5-10 minutes before you start getting connections.

Second issue - because of some issues involving the host cache, Bearshare nodes are no longer likely to appear (the same is true for fresh Limewire installs - it's a problem with how Bearshare operates).

Third - are you behind a firewall (or a router that does NAT)?  With a fresh install of GtkG, it will have randomly generated a new port number, so even if you opened a hole in the firewall (or forwarded a port from the NAT) on the previous install, that may not take effect for the new install.  This should *not* prevent you from connecting, but it could limit the type of connections you get.

Finally - A last resort.  Try manually entering the following nodes:
195.8.0.38:7073
88.84.144.195:37755
83.102.105.146:15561
201.23.141.42:55633
166.70.81.17:63666

These are all high-uptime GtkG "ultras".  Hopefully, at least one of these will respond for you, at which point it will provide you with additional valid hosts.

Lloyd B.

---

