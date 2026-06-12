---
title: "How do i automatically configure iptables on boot?"
date: 2006-01-29
forum: Server Platforms
---

### Post by sco01 on 2006-01-29
Hi,
I've created a start script for iptables called "iptables", placed it in /etc/init.d and made it executable. It takes three arguments: start, stop and restart. The script works fine as far as i know but i would like the system to execute it when booting so i don't have to do it manually every time. How do i do that? 

Btw, Is this how you normally do this on a server or should i try out an iptables front-end, and in that case which one?

Regards,
Stefan

---

### Post by MartinG on 2006-01-29
[QUOTE=sco01]Hi,
I've created a start script for iptables called "iptables", placed it in /etc/init.d and made it executable. It takes three arguments: start, stop and restart. The script works fine as far as i know but i would like the system to execute it when booting so i don't have to do it manually every time. How do i do that? 

Btw, Is this how you normally do this on a server or should i try out an iptables front-end, and in that case which one?

Regards,
Stefan[/QUOTE]Assuming the system will be operating in runlevel 2, place a link to your script in /etc/rc2.d.  Then rename it by adding a prefix Sxx, where xx is a number between 01 and 99.  The value of xx determines the order of starting of all the services listed in rc2.d, so pick a number with reference to what else is there; probably a fairly low number for a security thing like this.  I'd pick 15 on my system.

If you want a GUI, firestarter is simple and works, but maybe too simple for your needs?

---

### Post by sco01 on 2006-01-30
Thanks alot MartinG. It works as expected, and i learned alot by trying this.

Regards,
Stefan

---

