---
title: "Apt-get update not finding servers when host-only adapter is enabled"
date: 2017-12-08
forum: Virtualisation
---

### Post by thibaut123 on 2017-12-08
[COLOR=#111111][FONT=Ubuntu]I have this problem where i cannot update because it's just not finfing the server.. this only happens when i enable host-only adapter.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]With only **Nat**, i can successfully update my server, but not when NAT and **host-only adapter** is enabled.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I'm just so desperate because literally nothing is working.

**apt-get not connecting...:**

[IMG]https://i.imgsafe.org/b6/b69bc231ea.png[/IMG]

[B]ip configuration:
[/B]
[IMG]https://i.imgsafe.org/b6/b69d56f1d4.png[/IMG]
[B]
what i've tried:[/B]
uncommenting line 54 from /etc/gaia.conf
changed nameservers to google in /etc/resolv.conf
disabling anti-virus

Any help is welcome![/FONT][/COLOR]

---

### Post by deadflowr on 2017-12-09
*Thread moved to **Virtualization** *

---

### Post by thibaut123 on 2017-12-09
I have fixed it. when doing the following:

sharing internet connection with the virtualbox host-only adapter on host
manually configure the right ipv4 address so it's on the same subnet as host
use dns of google

Bam it worked!

---

