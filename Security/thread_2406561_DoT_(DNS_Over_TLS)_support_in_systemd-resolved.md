---
title: "DoT (DNS Over TLS) support in systemd-resolved"
date: 2018-11-22
forum: Security
---

### Post by fgont on 2018-11-22
[COLOR=#242729][FONT=Arial]Folks,[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm running a fresh install of 18.10. I configured as:[/FONT][/COLOR]
[Resolve]
DNS=1.1.1.1
#FallbackDNS=
Domains=~.
#LLMNR=no
#MulticastDNS=no
#DNSSEC=no
DNSOverTLS=opportunistic
#Cache=yes
#DNSStubListener=yes
[COLOR=#242729][FONT=Arial]Still, when running tcpdump it seems systemd-resolved still tries to use (in parallel with 1.1.1.1) the DNS advertised by the DHCP server.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My assumption was that setting:[/FONT][/COLOR]
Domains=~.
[COLOR=#242729][FONT=Arial]would prevent that.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any clues?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks!
Fernando[/FONT][/COLOR]

---

### Post by jeremy31 on 2018-11-22
Duplicate of [https://ubuntuforums.org/showthread.php?t=2406560](https://ubuntuforums.org/showthread.php?t=2406560)
Thread closed

---

