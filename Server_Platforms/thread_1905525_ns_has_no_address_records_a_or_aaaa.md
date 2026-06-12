---
title: "ns has no address records a or aaaa"
date: 2012-01-07
forum: Server Platforms
---

### Post by fedjaa on 2012-01-07
[FONT=Calibri][SIZE=3]Hi,[/SIZE]
[SIZE=3]I need some help with DNS server configuration. When I test my Reverse Zone file[/SIZE]
[SIZE=3]Sudo named-checkzone densel.ee /etc/bind/zones/db.192[/SIZE]
[SIZE=3], the output gives me following message:[/SIZE]
[SIZE=3]Zone densel.ee/IN: NS ‘igor.densel.ee’ has no address record <A or AAAA>[/SIZE]
[SIZE=3]Zone densel.ee/IN: not loaded due to errors.[/SIZE]
[SIZE=3]However the Forward Zone file test is OK![/SIZE]
[SIZE=3]My Reverse Zone file:[/SIZE]
[SIZE=3]$TTL 3D[/SIZE]
[SIZE=3]@                           IN                           SOA                       igor.densel.ee. root.densel.ee. ([/SIZE]
[SIZE=3]                                                                                              3;[/SIZE]
[SIZE=3]                                                                                              604800;[/SIZE]
[SIZE=3]                                                                                              86400;[/SIZE]
[SIZE=3]                                                                                              2419200;[/SIZE]
[SIZE=3]                                                                                              604800);[/SIZE]
[SIZE=3];[/SIZE]
[SIZE=3]@                           IN                           NS                          igor.densel.ee.[/SIZE]
[SIZE=3]1                             IN                           PTR                        igor.densel.ee.[/SIZE]
[SIZE=3]10                           IN                           PTR                        Igor-PC.densel.ee[/SIZE]
[SIZE=3]254                        IN                           PTR                        gw.densel.ee[/SIZE]
[SIZE=3]Does anyone have an idea what is a reason of that?[/SIZE]
[SIZE=3]Thanks in advance![/SIZE]
[/FONT]

---

### Post by Doug S on 2012-01-07
Hi,
I believe the Ubuntu server guide (if that is your reference) is incorrect with the instructions for this test.
Instead of:```
sudo named-checkzone densel.ee /etc/bind/zones/db.192

```the command should be (for example only, I don't know your actual sub-net):```
named-checkzone 1.168.192.in-addr.arpa /etc/bind/db.192
```See also [the lauchpad bug ]("https://bugs.launchpad.net/serverguide/+bug/864259")

---

