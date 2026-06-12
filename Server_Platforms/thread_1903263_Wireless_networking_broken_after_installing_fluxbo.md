---
title: "Wireless networking broken after installing fluxbox"
date: 2012-01-02
forum: Server Platforms
---

### Post by jeliocranch on 2012-01-02
Building a server(11.10) to centralize files, & provide VM hosting.
I only have wireless internet available.  During installation, the wireless card was recognized, and after first boot I had connectivity.  Thinking I might want an easier interface than CLI, I installed xorg and fluxbox.  Shortly after, I decided against a gui, and --purge remove'd the two packages.
Now, when it boots, it cannot configure the network.  There are several guides to cli wireless, but most reference:
/etc/wpa_supplicant.conf
which doesn't exist in my install.  Was it wiped out by xorg or fluxbox? Has it been moved in 11.10?  Is there a new method?

---

### Post by jeliocranch on 2012-01-02
After sleeping on it for a few hours, I had the solution.  It was right in front of me the whole time: Rescue Mode):P!
First thing that happens is you setup networking.  You get a chance to reboot after selecting the partition for /.

So while I didn't solve my issue from the command line, I did fix the issue.

---

### Post by jeliocranch on 2012-01-02
interestingly, still no /etc/wpa_supplicant.conf.
I wish I could read fast enough to pickup the packages and utilities being installed.
If anyone knows how 11.10 server does configure wireless, I'd appreciate the reply.

---

