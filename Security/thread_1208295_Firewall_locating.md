---
title: "Firewall locating"
date: 2009-07-09
forum: Security
---

### Post by Deathvalley122 on 2009-07-09
hi,

where is the firewall located in the gnome environment desktop?

Thanks,

Patrick Voege

---

### Post by lovinglinux on 2009-07-09
The firewall, called iptables, is accessible only by command line. But you can install a firewall manager, like [gufw](apt:gufw) [apt-get], that allows you to create the firewall rules easily. You can access gufw through "System >> Administration >> Firewall Configuration".

Keep in mind that Linux firewalls are not like Windows. For instance there is no such thing as popup alerts. Additionally, once you configure your rules, you can close the firewall manager, because the iptables will be always working on the background.

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

