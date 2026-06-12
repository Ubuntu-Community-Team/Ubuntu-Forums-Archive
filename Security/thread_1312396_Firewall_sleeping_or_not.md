---
title: "Firewall sleeping or not?"
date: 2009-11-03
forum: Security
---

### Post by OldGrantonian on 2009-11-03
I've just created a dual-boot Ubuntu partition after my Windows partition.   I installed a &quot;Firestarter&quot; firewall, until I manage to read through the sticky posts in this forum.   The icon shows &quot;Firewall running&quot; in the tooltip. The dialog shows that events are occurring.   I click System > Administration > System Monitor > Processes tab. The &quot;Firestarter&quot; status is listed as &quot;Sleeping&quot;.  Can anyone explain why these messages seem to be contradictory?  :)  New question: can anyone recommend a site (or sites) that claim to test firewalls?

---

### Post by yeleek on 2009-11-03
Just because a process is sleeping - doesn't mean its not functioning....

Firewall test sites - remember though that you most likely have a firewall already turned on at a router level!

[Google results]("http://www.google.co.uk/#hl=en&source=hp&q=test+firewall&btnG=Google+Search&meta=&aq=f&oq=test+firewall&fp=9cff3232a59d5ab3")

---

### Post by Lars Noodén on 2009-11-03
You can see what rules are active this way:

[INDENT][FONT="Courier New"]sudo iptables -vL[/FONT][/INDENT]

---

### Post by OldGrantonian on 2009-11-03
> **Lars Noodén said:**
> You can see what rules are active this way:[INDENT][FONT=Courier New]sudo iptables -vL[/FONT][/INDENT]

Very useful info.  Thanks for that :)

---

### Post by TheForumTroll on 2009-11-03
> **OldGrantonian said:**
>  can anyone recommend a site (or sites) that claim to test firewalls?

[GRC Shields up]("https://www.grc.com/x/ne.dll?bh0bkyd2").

---

### Post by Soul-Sing on 2009-11-04
> **TheForumTroll said:**
> [GRC Shields up]("https://www.grc.com/x/ne.dll?bh0bkyd2").

Shields-up test your router/modem-router.
```
sudo iptables -vL
``` test if your linux firewall iptables is up and running.

---

### Post by QLee on 2009-11-04
> **leoquant said:**
> Shields-up test your router/modem-router.

This is true with a caveat, many gateways have the ability to option the included firewall off. The default is usually on, so as long as the admin hasn't turned it off this statement is correct in that the GRC check for open ports only test to the first (Internet facing) firewall in your network topology.

A minor distinction, but I am picky about such things.

---

### Post by lensman3 on 2009-11-04
If you have any kind of logging turned on in the iptables rules, the log can be reviewed using "dmesg".  Run "dmesg" from a text screen.  You will probably have to pipe it through "more".

---

### Post by QLee on 2009-11-04
[QUOTE=lensman3]If you have any kind of logging turned on in the iptables rules, the log can be reviewed using "dmesg".  Run "dmesg" from a text screen.  You will probably have to pipe it through "more".[/QUOTE]

Those "hits" you're talking about might be more easily found and read in kern.log or messages but the "hits" only show you what has been blocked.

The advice from leoquant "sudo iptables -vL" will show you the rules being used.

Edit: Oh, and if the gateway has a firewall turned on with sensible rules, the "hits" won't get to your box, that is leoquant's other point, which people often overlook.

---

