---
title: "Installing no add on GUI locks up server after install."
date: 2012-04-09
forum: Server Platforms
---

### Post by Timster4life on 2012-04-09
[SIZE=2]Title is pretty much self explanatory, When I install the no frills GUI for my Ubuntu Server 11.10 using..[/SIZE]
[COLOR=red]
[/COLOR][CENTER]> sudo apt-get install --no-install-recommends ubuntu-desktop
[COLOR=red][/COLOR][/CENTER]
[COLOR=red][SIZE=2][COLOR=black]
The installations seems to go fine, then once upon reboot.. the unit just locks up within seconds and dose not make it past what appears to be some basic self tests..

Any ideas/suggestions?...

Thank you all for your help in advance!


[/COLOR][/SIZE][/COLOR]

---

### Post by arrrghhh on 2012-04-09
Why are you installing the ubuntu-desktop package on a server?!?

Even with --no-install-recommends, you're going to get a ton of stuff.  If you want a full blown UI, install Ubuntu Desktop.  No headache, no fuss... You want a DE, you get a DE.

Server edition, you don't get a DE.  Trying to shove one onto it is possible, but usually not a good idea - not recommended.  I know some people do LXDE or some lighter DE, but still - if you want a full DE, install Ubuntu Desktop!!  Thank you!

---

