---
title: "iptables logging dropped packets"
date: 2014-07-24
forum: Security
---

### Post by bob40 on 2014-07-24
I have been reading a lot about the subject of logging dropped packets.  I see several pages that give the following basic instructions:

```
iptables -N LOGGING
iptables -A INPUT -j LOGGING
iptables -A OUTPUT -j LOGGING
iptables -A LOGGING -m limit --limit 2/min -j LOG --log-prefix "IPTables-Dropped: " --log-level 4
iptables -A LOGGING -j DROP
```

Now if I understand correctly, line 1 creates a new chain called LOGGING.  Line 2 puts AT THE END a command to the "input" chain to send any remaining packets to the new "LOGGING" chain.  Line 3 same for "OUTPUT" chain.

First question; As I understand the packet is processed in order of the chain ceasing when it matches and going no further.  So if I put the LOGGING command at the end of the chain, I will only get packets logged that have not already been delt with.  In other words, if there is a DROP command, it won't make it to the logging command.

Second; I want to save these rules but I have shorewall and fail2ban that dynamicaly add rules.  I seem to have several rules that I don't recal setting.  As I understand I can save iptables and have it load on startup but then I get all the dynamic stuff stuck in there, correct?

Bob

---

### Post by JKyleOKC on 2014-07-25
> **bob40 said:**
> First question; As I understand the packet is processed in order of the chain ceasing when it matches and going no further.  So if I put the LOGGING command at the end of the chain, I will only get packets logged that have not already been delt with.  In other words, if there is a DROP command, it won't make it to the logging command.

Second; I want to save these rules but I have shorewall and fail2ban that dynamicaly add rules.  I seem to have several rules that I don't recal setting.  As I understand I can save iptables and have it load on startup but then I get all the dynamic stuff stuck in there, correct?

BobTo answer your first question, you are correct. When I added similar capability to my own iptables rules, I named the new chain "LOG_DROP" rather than "LOGGING" and I then changed all instances of DROP commands to LOG_DROP instead. That solves the problem; you can simply change DROP to LOGGING and have the same result. The only reason I used LOG_DROP as the name was to remind me in future as to what it's doing -- and I've not had to change the rule set for at least two years now.

For the second question, again you are correct -- but you can use a text editor to modify the saved version and take out all the dynamic stuff. Actually, you can temporarily stop fail2ban (which will remove all of its modifications) while you run the iptables-save utility, then re-start it when done. Again, it's been some two years since I last saved my rules to a file in /etc; it restores the iptables rules each time the interface comes up, rather than during the boot process. I did it this way after years of fighting with trying to restore via rc.local; the current boot process makes it possible for things to get out of sync. By restoring iptables using "post-up" in the interface definition, that keeps things in the proper order. Here's the relevant stanza from my /etc/network/interfaces file:
```
iface eth0 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	post-up iptables-restore < /etc/iptables.up.rules
auto eth0

```Hope this helps!

---

### Post by bob40 on 2014-07-25
> **JKyleOKC said:**
> Hope this helps!


Thanks it really does help!

---

