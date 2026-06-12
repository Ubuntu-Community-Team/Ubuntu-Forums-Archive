---
title: "Running asp.net 2.0 apps with apache2 and mod_mono"
date: 2008-06-11
forum: Server Platforms
---

### Post by rogier.de.groot on 2008-06-11
Hi all,
I've been trying to get the mod_mono package from the standard repos working for serving asp.net 2.0 web apps/services from my home server, but so far no luck.
The best I've gotten so far is the mod-mono-server (asp.net 1.x version) serving up my test application. I can't even figure out why mod_mono would spawn that, since I explicitly configured mod-mono-server2. After I restarted apache (without configuration changes) mod_mono spawned the right server process, but every time I try to access my Default.aspx firefox wants to open it in visual studio instead of it actually running:(
Anyone here know how to get mod_mono working for asp.net 2.0 without resorting to compiling mono from source?

TIA

---

### Post by rogier.de.groot on 2008-06-12
Nobody running ASP.NET 2.0 apps on apache2/mod_mono? Everybody using Java/PHP/Ruby/Python?
I've now discovered the bagderports repo which lets me install a more recent version of mono, but still no luck... The howto on the ubuntu community docs site is no good either, accessing Default.aspx still results in the browser trying to open it rather then it running:(
BTW, is there any similar extra repo for up to date java/glassfish/netbeans packages?

---

