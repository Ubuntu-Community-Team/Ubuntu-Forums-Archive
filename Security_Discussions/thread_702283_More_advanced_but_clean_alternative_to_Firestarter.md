---
title: "More advanced but clean alternative to Firestarter?"
date: 2008-02-20
forum: Security Discussions
---

### Post by Nesnej Trick on 2008-02-20
I've been trying to get the IPTV we have here at our campus working on my computer, and I think I've discovered why I am not receiving it. The reason seems to be that Firestarter blocks all Multicast traffic and since the programmes are sent as IGMP multicast packets, none of them reach through.

The natural solution would be to switch firewall configurator, but so far I haven't had much luck. KMyFireWall simply has a way to cluttered interface for me and Guarddog just didn't seem to cut it (in fact, it locked everything, including http even though I explicitly told it to allow it). Fwbuilder on the other hand seemed otherwise decent, but it's littered with a gazillion of different option and no tooltips or any other documentation on what each button actually does.

In short, is there any firewall configurator that is advanced enough to have the option to allow multicast traffic but still has an interface so simple that I won't need to learn some obscure programme-specific scripting jargon or how to manually edit iptables?

---

### Post by ajgreeny on 2008-02-20
If you don't run any servers on your computer you really don't need tyo run any "firewall configurator" such as firestarter or guarddog.  So it may be worth removing firestarter and purging your iptables to remove all configuration you have already set, and trying again.

```
sudo /etc/init.d/firestarter stop 
sudo /etc/init.d/guarddog stop 
sudo iptables -F 
sudo dpkg -P firestarter guarddog 
sudo /etc/init.d/networking restart

```
The above was used to get rid of both firestarter and guarddog, so if you only have the one you needn't use the references to guarddog in the above coding.  And if you are running servers on the machine I apologise for wasting your reading time.

---

### Post by Nesnej Trick on 2008-02-20
Well, I might skip setting up a samba server and just leach off the fileshares on the campus network if that saves me work.

---

### Post by euler_fan on 2008-02-21
It doesn't have a gui the way Firestarter does (e.g. all "live" firewall work must be done using another tool/cli) but Firewall Builder is a great tool but requires more knowledge of what you're doing and networking generally.

---

