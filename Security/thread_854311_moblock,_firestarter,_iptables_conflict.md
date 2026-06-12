---
title: "moblock, firestarter, iptables conflict"
date: 2008-07-09
forum: Security
---

### Post by mdsharp24 on 2008-07-09
[B]I've been doing some research on moblock and have concluded that moblock and firestarter (a GUI for iptables) do NOT play nicely and could accidentially lead a user into a false sense of security when using moblock. 

First, in the default install of firestarter and moblock (both starting at system boot), firestarter is run AFTER moblock (rcS.d) which removes all moblock iptable setting.

Secondly, if firestarter is started at boot (with all custom rulesets) and moblock is not, and a user manually starts moblock after firestarter all is good. HOWEVER, if a user adds or deletes a ruleset in firestarter with firestarter and moblock running then moblock's iptables rulesets get deleted.

Thirdly, if firestarter is started at boot and moblock is manually started after firestarter, then all is well. BUT, if a user decides to STOP the firewall in the firestarter GUI then all moblock's rules are borked. A restart of the firewall via the GUI will not replace the moblock iptable rulesets.

[COLOR="DarkRed"]_POSSIBLE WORKAROUNDS_[/COLOR]

[COLOR="Red"]1. Do not use firestarter (or seemingly any other IPTABLES configuration tool) and use a hardware router to port forward needed services such as http, DNS, etc and just use moblock.

2. If using both firestarter and moblock, turn firestarter off so that there are NO IPTABLE rulesets and then start moblock when needed. When not needed, stop moblock and start the IPTABLES rulesets in firestarter.

3. Write your own IPTABLES scripts that integrate IPTABLES and moblock and start it effectively at system boot. Just remember, moblock must be started after all other IPTABLE rulesets[/COLOR][/B]

---

### Post by jre on 2008-07-10
Another possibility might be to restart MoBlock automatically whenever firestarter does an iptables operation. But I don't know if this is possible.

Of course it is important to know that you have to use MoBlock 0.9 (not 0.8 ) with the marking feature for nonblocked packets on. (This is the case if you install the "moblock" package). Otherwise no integration at all is possible!

But with the above conditions met, you will always be fine as long as there are no accept iptables rules before MoBlock's rules.

jre

---

### Post by Trevorius on 2009-08-23
And how would it work if people just loaded blocklists into a program like KTorrent while using Firestarter, rather than using a separate program like Moblock?

---

### Post by jre on 2009-08-24
I´m quite sure that KTorrent filters IP directly (inside KTorrent), but does not use iptables. Therefore you have no conflicts between KTorrent and any other firewall (in regard to the IP filtering).
The drawback of this solution is, that only KTorrent filters its traffic. There´s no system wide security, and no stealth mode.

Again: I´m just assuming this, I haven´t tested it.

---

