---
title: "Very short rant about wicd - it continues to be broken - why?"
date: 2011-05-30
forum: The Cafe
---

### Post by leegold on 2011-05-30
Hi,

I posted here because I don't necessarily need tech help but there's something I don't understand. There's a network manager called wicd. It has not worked on any Ubuntu implementation I've tried since 10.04. Totally does not work - broken. Bugs have been cited, no real solutions when searching. Yet this app is still in Synaptic, still touted as a solution. Why? It's broken for many users. Connectivity is important...vital. Why have something around that's broken?

Just my experience and completely personal opinion/question.

Thank you.

---

### Post by Hwæt on 2011-05-30
Wireless managers and connectivity are often touted as Linux's Achilles Heel. Things like this are incredibly iffy and only work on certain builds. Chances are that Wicd works perfectly on the maintainer's hardware, so he's completely oblivious to any problems on yours. It's always best to submit bug reports for this reason, as if no one does, the problem will never get fixed.

---

### Post by boydrice on 2011-05-30
I had read on the Slackware LQ forum that wicd was no longer being actively developed.  Pat Volkerding said that he would be looking at NetworkManager as a replacement.  This might explain why bugs are not getting fixed.

---

### Post by screaminj3sus on 2011-05-30
why not just use network manager?

---

### Post by gutterslob on 2011-05-30
For what little its worth, the CLI front-end, wicd-curses, has worked flawlessly on all my rigs that required wireless connectivity.

Sorry to hear that it's not actively developed any longer. I personally prefer it to NM. Only alternative I'd consider is Aptosid's Ceni.

---

### Post by Hwæt on 2011-05-30
> **gutterslob said:**
> For what little its worth, the CLI front-end, wicd-curses, has worked flawlessly on all my rigs that required wireless connectivity.

Sorry to hear that it's not actively developed any longer. I personally prefer it to NM. Only alternative I'd consider is Aptosid's Ceni.

If you're running Arch I'd really recommend you try Netcfg.

---

### Post by gutterslob on 2011-05-30
> **Hwæt said:**
> If you're running Arch I'd really recommend you try Netcfg. I do have an Arch partition on one of my rigs. I tried Netcfg some time ago, but it kept dropping the connection to my wireless router every few minutes, though I realize newer versions are probably better sorted.. I'm not dissing it, since I only ever tried it on the stock net-auto-wireless setting, but wicd-curses just felt an easier fit at the time.

---

### Post by boydrice on 2011-05-30
> **gutterslob said:**
> For what little its worth, the CLI front-end, wicd-curses, has worked flawlessly on all my rigs that required wireless connectivity.

Sorry to hear that it's not actively developed any longer. I personally prefer it to NM. Only alternative I'd consider is Aptosid's Ceni.

For what it is worth there is nm cli

---

### Post by BrokenKingpin on 2011-05-30
> **screaminj3sus said:**
> why not just use network manager?
Probably because it brings in a bunch of Gnome dependencies that are not wanted on an XFCE install.

---

### Post by SamD42 on 2011-05-30
I've never had a problem getting wicd to connect to a standard network in Ubuntu, provided I also removed network-manager - for some reason installing one does not remove the other anymore.

What is the problem, specifically, that wicd is having on your machine?

That said, I don't know how much wicd development there is going on anymore...

---

### Post by Irihapeti on 2011-05-30
> **BrokenKingpin said:**
> Probably because it brings in a bunch of Gnome dependencies that are not wanted on an XFCE install.

There are only two specifically gnome dependencies: libgnome-bluetooth and libgnome-keyring. Both are fairly small.

I use network manager with Openbox because I was having trouble with wicd not handling a very long WPA2 password.

---

### Post by HoKaze on 2011-05-30
Wicd (the daemon, the gtk interface and the curses interface) has been working well for me for a pretty long time since I started using it as a replacement for network-manager. I found the latter to be unreliable and although I do lose my connection from time to time, this appears to be a fault with my wireless as it occurs regardless of manager, distro and OS.

I'm sad to hear it's not being actively developed any longer, but by now I guess network-manager should be a lot more stable?

---

