---
title: "Server load history"
date: 2007-04-24
forum: Server Platforms
---

### Post by byenary on 2007-04-24
Hello,

Im looking for easy way, maybe a gui app for watching the cpu load history, i've got a bunch of cronjobs running in the night and would like to see how much this takes from my lightweight server...

Thx

---

### Post by strixy on 2007-04-24
That's an easy one. Right click on a panel, select add new, and add a system monitor. Right click on the new monitor icon to configure. You can monitor the processor, memory, and the network graphically.

If you need more specific numbers, the "top" command is unbeatable (IMHO) as are the rest of the commands found on this page,

[http://tldp.org/LDP/sag/html/system-resources.html](http://tldp.org/LDP/sag/html/system-resources.html)

Something that will help overnight is "sar"

[http://www.die.net/doc/linux/man/man1/sar.1.html](http://www.die.net/doc/linux/man/man1/sar.1.html)

---

### Post by MJN on 2007-04-24
> **strixy said:**
> If you need more specific numbers, the "top" command is unbeatable (IMHO)
Have you tried **h**top? Even better! (IMO!) :)

Mathew

---

### Post by byenary on 2007-04-27
htop is very nice thx a lot !

---

### Post by huygens on 2007-04-27
Like it was suggested, sar is a really good solution to monitor any kind of resources. It is in the sysstat package (as far as I remember).
I do not know any GUI for it though... but I found the command line rather easy after you do a 'man sar'...

Though a quick search on the internet returned: [http://freshmeat.net/projects/ksar/](http://freshmeat.net/projects/ksar/)
more to search I guess ;-)

---

