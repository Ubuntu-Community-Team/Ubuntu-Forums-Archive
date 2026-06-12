---
title: "Basic user security apps / settings"
date: 2011-12-21
forum: Security
---

### Post by toolmania1 on 2011-12-21
I am a basic, home Ubuntu user.  I want to secure my system, but I don't have a huge network of users to be in charge of.  This is what I was thinking of having set up security wise for Ubuntu 11.  Is this a good set up? ( Not sure if anything changed from Ubuntu 10.10 to Ubuntu 11.10 )

1. Firefox browser with Noscript, Browser protect, Adblock plus, WOT, and Better Privacy add ons
2. UFW ( not sure what to allow / deny ) with gufw installed
3. Chkrootkit
4. AppArmor

Anything else?
Should I block every port except 80 for internet usage? in ufw also?

---

### Post by Ms. Daisy on 2011-12-21
Have a look at the wiki in my signature. All the things you list are in there except for chkrootkit.

---

### Post by toolmania1 on 2011-12-29
Perfect!

Thanks

---

### Post by d3v1150m471c on 2011-12-29
firewalls are like throwing a dirty rug on a pile of dirt. good security starts with knowledge, the right software, and the right configurations. btw, blocking everything except port 80 will eliminate your dns, as well as 443. 443 == ssl == [https://.](https://.) for anonymity i would recommend using JonDoNym's JonDoFox. I will argue it could be more secure but that's no trivial configuring. You can always use lynx + tor if you're feeling brave enough to use a terminal.

---

