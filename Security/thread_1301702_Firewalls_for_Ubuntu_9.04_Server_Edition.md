---
title: "Firewalls for Ubuntu 9.04 Server Edition"
date: 2009-10-26
forum: Security
---

### Post by jordanjae on 2009-10-26
I need a firewall for an ubuntu server project I'm doing, my friend is using untangle and I want something similiar, any ideas for firewalls?

---

### Post by ray62 on 2009-10-26
Hi i av Gufw 9.04.2 dont no if i will do for server edition tho ?

---

### Post by piankhi on 2009-10-26
Ubuntu comes with a firewall built into the kernel. Its called iptables. I'd recommend going through the following 3 pages:

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)
[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)
[http://ubuntuforums.org/showthread.php?t=668148](http://ubuntuforums.org/showthread.php?t=668148)


iptables has various GUIs/frontends if you are not comfortable with the command line or bash scripts. Just google iptables GUI or iptables frontend.

---

### Post by ray62 on 2009-10-26
is that no good what i have ?

---

### Post by piankhi on 2009-10-26
Gufw is fine if you're comfortable with it. It is simply a gui for iptables as far as i understand.

---

### Post by gnuisancev3 on 2009-10-26
> **piankhi said:**
> Gufw is fine if you're comfortable with it. It is simply a gui for iptables as far as i understand.

Gufw is a GUI for ufw, which is a simplified command line front end to iptables.

If you want the most control you should really learn how to use iptables.

---

### Post by piankhi on 2009-10-26
> **gnuisancev3 said:**
> Gufw is a GUI for ufw, which is a simplified command line front end to iptables.

If you want the most control you should really learn how to use iptables.

Thanks for putting it better than i could. Wanted to originally say its a gui for iptables by proxy, but thought using the word proxy would confuse him/her. cheers..

---

### Post by ray62 on 2009-10-26
i am a newbie and confused lol

---

### Post by p0rnflake on 2009-10-27
Whats your guys position on using iptables vs securing/patching the system ?

In the Window$ world :evil: there's often alot of debate about the added software in form of the firewall code actually just increases the chance of vulnerabilities - I guess the same could be said for Linux ?

---

### Post by RecNes on 2009-10-28
Is there any console based user interface package for ufw or iptables?

---

### Post by QLee on 2009-10-28
[QUOTE=p0rnflake]Whats your guys position on using iptables vs securing/patching the system ?[/QUOTE]

My position is that it's not an either/or situation. Use sensible iptables rules *and* keep your system patched and optioned securely.

[QUOTE=p0rnflake]In the Window$ world :evil: there's often alot of debate about the added software in form of the firewall code actually just increases the chance of vulnerabilities - I guess the same could be said for Linux ?[/QUOTE]

It could be said but it would be an incorrect statement. It would only be correct if one chose bad software or mis-configured in some way. Iptables is part of the system, the GUI frontends can just make it a bit easier to add and remove rules.

---

