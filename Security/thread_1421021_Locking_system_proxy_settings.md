---
title: "Locking system proxy settings"
date: 2010-03-03
forum: Security
---

### Post by deadlockedgamer on 2010-03-03
I installed DansGuardian. In order for it to work I set the system wide proxy. However it is really easy to get around DansGuardian by going to preference proxy setting. How do I password protect this setting so it requires a password to change proxy setting? Preferably a different password than the normal sudo password if possible. If not I at least want the sudo password protecting it! I run multiple browsers so doing it via the system rather than the browser made the most since.

---

### Post by bodhi.zazen on 2010-03-03
The easiest way on a LAN is to use a proxy server for the entire lan.

See squid, transparent proxy

[http://www.debian-administration.org/articles/71](http://www.debian-administration.org/articles/71)

---

### Post by deadlockedgamer on 2010-03-03
I am currently on wifi and have the proxy installed on the machine that is using the internet. The problem is You can go top system preference network proxy and change to direct connection which bypasses the program that blocks pages. At one point I will make the only way to connect to the internet in the house is through a server with the block. However for no I would like to use the solution which works fine other than the explained work around I found!

---

### Post by deadlockedgamer on 2010-03-03
bump

---

### Post by Agent ME on 2010-03-03
> **deadlockedgamer said:**
> However for now I would like to use the solution which works fine other than the explained work around I found!
Locking the system proxy settings wouldn't stop someone from changing the proxy settings directly in Firefox or any other browser. bodhi.zazen's solution is the correct one.

---

### Post by NiGhtMarEs0nWax on 2010-03-04
> **deadlockedgamer said:**
> I installed DansGuardian. In order for it to work I set the system wide proxy. However it is really easy to get around DansGuardian by going to preference proxy setting. How do I password protect this setting so it requires a password to change proxy setting? Preferably a different password than the normal sudo password if possible. If not I at least want the sudo password protecting it! I run multiple browsers so doing it via the system rather than the browser made the most since.

it depends on the skill of the person you are attempting to keep out.

publicfox is a good addon for firefox, it will lock preferences and about:config. however since the firefox profile folder is in a directory every user should have write access to, it is easily bypassed. you can take root ownership of the profile folder in question and allow write access only to the following files:

places.sqlite  // bookmarks
cookies.sqlite  // cookie data
key3.db  // stored password hashes (master password)
signons.<somethinglol>  // list of websites for stored passwords.
permissions.sqlite  // cookie permissions.


there is also a document for the google search toolbar, cant remember the name of it though.
also there is nothing stopping a person from downloading a new firefox binary and creating a new profile. totally bypassing the proxy settings.

in that case you will need squid to listen on port 80, and or use ip tables to forward ports.

good luck. :)

---

