---
title: "Adding rules in gufw"
date: 2011-09-29
forum: Security
---

### Post by arroy_0209 on 2011-09-29
1. My gufw preferences are as follows: firewall enabled, incoming denied, outgoing allowed. However I further tried to add rules to be more specific with certain options. My doubt is, in preconfigured option to add rule, if I click "show extended actions" then an option for numbers (0,1,2,....) appear at the leftmost position. I do not understand what it means. Can anybody please explain? What value should I set? should it be different for different actions like ftp, ssh, samba, http etc?

2. I have opted for "denied incoming" and "denied outgoing" for all services and programs except for http, for which I allow outgoing. (otherwise I can not access internet). Please comment on this configuration. How can it be improved?

---

### Post by SparTacux on 2011-09-30
> **arroy_0209 said:**
> 1. My gufw preferences are as follows: firewall enabled, incoming denied, outgoing allowed. However I further tried to add rules to be more specific with certain options. My doubt is, in preconfigured option to add rule, if I click &quot;show extended actions&quot; then an option for numbers (0,1,2,....) appear at the leftmost position. I do not understand what it means. Can anybody please explain? What value should I set? should it be different for different actions like ftp, ssh, samba, http etc?

2. I have opted for &quot;denied incoming&quot; and &quot;denied outgoing&quot; for all services and programs except for http, for which I allow outgoing. (otherwise I can not access internet). Please comment on this configuration. How can it be improved?

 I THINK the numbers 0,1,2 means that the top rule ( 1 in this case ) is executed first then rule 2 then rule 3 and so on. The order of the rules is important. Rule zero is probably used to write the current rule you are making at the bottom of the list of current rules? - not too sure about this so you might want to check it out ) If you have denied all outgoing traffic and have a rule 1 that says allow all http traffic then all http traffic will be allowed. If you then add another rule ( rule 2) that says block traffic to a particular web site then it won't work because rule 1 says allow all http traffic. If you wanted it to work then you would have to block that website using rule 1 and allow all http traffic using rule 2.  Denying all outgoing traffic is quite restrictive and you will need to allow out HTTP, HTTPS, DNS, NTP, POP AND SMTP ( if using this mail ). If using printers then also maybe MDNS and IPP. Enable UFW logging and you will be able to see if this causes any problems.

---

