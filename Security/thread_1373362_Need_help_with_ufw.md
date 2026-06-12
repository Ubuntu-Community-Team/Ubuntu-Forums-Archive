---
title: "Need help with ufw"
date: 2010-01-05
forum: Security
---

### Post by kpfuser on 2010-01-05
Returning to Ubuntu after a long absence, I took Xubuntu 9.10 for a test drive.  After ironing out some initial problems, I turned my attention to security and the ufw firewall.  Relevant documentation states that I must enable ufw first and then supply a ruleset because by default ufw runs in "allow" mode. However, I need help from the forum in order to put together a proper ruleset.

Borrowing from past experience with WinXP and the Sygate firewall, I could switch ufw to "deny" mode (exactly how is not clear to me right now but I expect it to be straightforward) and then allow specific applications/processes to reach specific ip address ranges using specific protocols and ports.  This ruleset should be secure but from past experience it can become massive and thus time-consuming to maintain.  A sharp reduction in the number of rules can be achieved if key parts of domain names (eg .yahoo.) can be used instead of ip address ranges.  However, I am not sure if this can be done in the case of ufw.

A convenient solution would be the compact (~12-15 rules) ruleset of Puppy Linux.  Relevant Puppy Forum security threads state that this ruleset is sufficient for standalone pcs which do not run as servers.  Unfortunately, this ruleset is written in ip-tables lingo, which is an area of zero expertise for me.

So, how have forum members resolved this issue? What ruleset(s) do they use with ufw in the case of standalone pcs?  Are there any better firewall solutions available?

---

### Post by njdove on 2010-01-05
To begin with, you can enable UFW by running "sudo ufw enable". Ubuntu 9.10's default configuration drops incoming traffic[1] and allows all outgoing traffic.

It may be difficult to predict what protocols and ports you will need to function comfortably. I'm fairly security conscious, but I'm confident in running an Ubuntu desktop that allows outgoing traffic by default.

You cannot restrict network access on a per-application basis because Linux dropped support for iptables' --{cmd,sid,pid}-owner matching in 2005 (see [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=34b4a4a624bafe089107966a6c56d2a1aca026d4](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=34b4a4a624bafe089107966a6c56d2a1aca026d4)). Even if this were possible, its value is diminished by the necessity of allowing rich scripting languages (e.g. python) to access the network.

You can put iptables-restore style rules in /etc/ufw/before.rules and /etc/ufw/after.rules - this is probably the rule format you're referring to from  Puppy Linux. These rules run before and after the UFW-added rules, respectively.

UWF offers a straightforward syntax for simple port-based rules. From the ufw man page, the following command will allow TCP ports 80, 443, and 80 through 8090:
```
ufw allow proto tcp from any to any port 80,443,8080:8090
```

[1] The default Ubuntu 9.10 config allows some traffic in:
[LIST]
[*] traffic on the same subnet
[*] housekeeping ICMP types
[*] DHCP traffic
[*] multicasts
[*] broadcasts
[/LIST]

---

