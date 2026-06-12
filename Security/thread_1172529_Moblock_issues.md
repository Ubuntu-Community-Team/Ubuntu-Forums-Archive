---
title: "Moblock issues"
date: 2009-05-28
forum: Security
---

### Post by Thelasko on 2009-05-28
I use moblock with mobloquer and have noticed an issue I feel others should be aware of.  With the newest version of mobloquer, if you don't stop mobloquer before exiting you will have issues with your firewall.  Please be advised.

Symptoms of this problem include problems connecting to email servers and instant messaging servers.

To avoid this problem be sure you click the stop button before exiting the program. 

If this issue is effecting you, simply start mobloquer and click the start button under the manage tab.  Then click the stop button also located under the manage tab.  You may then close mobloquer.

Thanks

---

### Post by lovinglinux on 2009-05-28
This is probably not an issue. This is due to the fact that you have selected the option to load moblock on start. Open Mobloquer, click the settings tab then untick the option to "Start Molock at system boot".

Do you know that you could use moblock to create the firewall rules? It has built in scripts that are loaded and change the iptables on start/stop, so you don't have to use another firewall manager. But you need to know iptables commands to populate the scripts.

---

### Post by Thelasko on 2009-05-29
> **lovinglinux said:**
> This is probably not an issue. This is due to the fact that you have selected the option to load moblock on start. Open Mobloquer, click the settings tab then untick the option to "Start Molock at system boot".
I do not have "Start Moblock at system boot" selected, and never have.

> Do you know that you could use moblock to create the firewall rules? It has built in scripts that are loaded and change the iptables on start/stop, so you don't have to use another firewall manager. But you need to know iptables commands to populate the scripts.

I suspected so, and that is precisely the problem.  If I don't click "stop" before closing moblock, it's settings remain in iptables, and blocks all of my services.  I use GUFW to manage my firewall rules and it is a big hassle.

---

### Post by lovinglinux on 2009-05-29
> **Thelasko said:**
> I do not have "Start Moblock at system boot" selected, and never have.
I suspected so, and that is precisely the problem.  If I don't click "stop" before closing moblock, it's settings remain in iptables, and blocks all of my services.  I use GUFW to manage my firewall rules and it is a big hassle.

Closing mobloquer should not affect the iptables. This is normal behavior, since mobloquer is just a GUI to setup moblock rules and it is the same behavior when you close gufw, which is the GUI to control UFW rules. If closing mobloquer or gufw would remove their corresponding rules from the iptables, then you would have to run them both all the time, which is completely unnecessary. So you need to stop moblock before exiting mobloquer otherwise it will remain active. This is normal behavior.

---

### Post by jre on 2009-05-31
It is the default installation behaviour to run moblock on system start. So if you have never **disabled** that, it is run always.
Since the last version there is a watchdog which restarts moblock if it detects any problems.

From this I conclude (but I don't know for sure), that you always had moblock running but that it was broken most of the times by ufw, without you noticing that.


So you might either disable the automatic start of moblock and only fire it up with full protection, whenever you want. 
Or you might keep it running always and do some whitelisting.
Have a look at [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) to learn how to do these things.

---

