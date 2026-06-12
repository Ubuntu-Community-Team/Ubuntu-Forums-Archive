---
title: "Shorewall Issues"
date: 2008-07-27
forum: Security
---

### Post by Kylibar on 2008-07-27
Ok ill make this as quick and detailed as I can.

Im running ubuntu server 6 LTS. I have installed the KDE gui (works very nice with few mods - good for system navigation, you can shut the GUI down when your done tweaking)

aannyywayy...

So I'm doing a two interface setup, later on ill be doing a 3 interface for a DMZ for my DNS, mail, web ect.

this is my current shorewall setup:

"interfaces" files
inet     eth0      detect
enet     eth1      detect

"zones" file
fw       firewall
inet     ipv4
enet     ipv4

"rules" file
Web/accept     enet     fw
Web/accept     fw       inet
Web/reject     inet     fw

"policy" file
enet     inet     accept
inet     all      drop     info
all      all      reject   info

when I try to start shorewall i get "ERROR: Invalid policy accept" within the shorewall-init.log.

any help would be nice :)

oh by the way, should I be able to access MY DSL MODEM from the other side of the firewall, even with shoreline shut off??

what I mean is: (the connection direction im trying to make is indicated by the >>>arrows<<<, the connection im trying to make stops XXXhereXXX :)

[indent](X)MY DSL MODEM<<<
[INDENT]<<<MY FIREWALL
[INDENT]<<<MY HUB
[INDENT]<<<computer im using
[/indent][/INDENT][/INDENT][/INDENT]

I figured it would be better off for me to create the firewall and test it before actually adding it to my network, using a hub and spare dsl modem :) im glad i did, cause.. its not working! lol

yea, any help would be very appriciated!!! thanks!

---

### Post by Kylibar on 2008-07-28
27 views, 0 replies... someone has to know? i know im not the smartest one out there, or... am i? i guess that 160 pays off....   no seriously... someone help me out here.

---

### Post by Biochem on 2008-07-28
I'm gonna take a wild guess here, but in my rules and policy files it's DROP, ACCEPT and REJECT not drop, accept and reject. So it could be something as simple as case sensitivity.

Also it's even though in my firewall is identified in my zones as: 
fw	firewall


In my rules file the firewall is identified as $FW (again might be case sensitive). All other zones remains with the same case and have no $.

As for your second question, I think you need a valid routestopped file.

I hope this help

---

