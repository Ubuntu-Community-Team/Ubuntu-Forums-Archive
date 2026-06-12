---
title: "iptables logging"
date: 2016-05-17
forum: Security
---

### Post by posterberg on 2016-05-17
Hi

I'd like to add some extra logging on my server regarding configuration changes of security related settings.

One such thing could be whenever someone adds, removes or changes settings in iptables.

Iptables is the primary concern now, but it would be nice to also get other configuration changes logged. Like changing ip-addresses, adding nics, enabling/disabling forwarding, syncookies etc etc.

Is there any way to tell the kernel to log any security related changes? It should be pretty normal that changes of security should be logged. I don't understand why this isn't enabled by default.

BR,
Peter

---

### Post by Habitual on 2016-05-17
Peter: 
How many people are making such changes on a server?

Seen /var/log/syslog ?

---

### Post by posterberg on 2016-05-17
/var/log/syslog doesn't, by default, log when I make an iptables configuration change. Please tell me if you know how to enable that, it is exactly what I am looking for.

---

### Post by Habitual on 2016-05-17
> **posterberg said:**
> /var/log/syslog doesn't, by default, log when I make an iptables configuration change. Please tell me if you know how to enable that, it is exactly what I am looking for.
I'm not sure that there is such a feature since iptables is stored in memory.
```
grep iptables ~/.bash_history
```
Sorry, assumed bash here.
is about all I can think of.

---

### Post by posterberg on 2016-05-17
Yes, I realize that which is exactly why I want the changes logged in case someone makes a change directly to the tables instead of changing via the save file which can be monitored using tripwire techniques.

Anyway I would be surprised if it isn't possible to tell the kernel to log configuration changes, especially security related ones.

---

### Post by untrustytahr on 2016-05-17
iptables requires root to change, so you could just grep auth.log.  if you're worried that someone would create an interactive root shell with a "sudo -i", you could write a short script as root that outputs the current iptables to a file and do a diff/hash on it and if it changed from the previous value and write it to a log using logger.  run the script via a root cron job.

---

### Post by posterberg on 2016-05-17
Okay, sorry for not being clear... I know that there are other solutions to this but there should seriously be an option to tell the kernel to log whenever someone tries to make changes to it's configuration. This is what I am looking for. :-)

It pretty basic when it comes to logging that all security related changes should be logged, basically all applications have this possibility. Why shouldn't the kernel, the foundation for all other components, have this option?

So again... Is it possible to tell the Linux kernel to log when when configuration changes have been made? If not, does anyone know why this is not part of the design?

I am currently diving through sysctl options but am not finding anything. Btw, most systctl changes should also be logged...

/p

---

### Post by SeijiSensei on 2016-05-17
The kernel isn't going to know if you changed your iptables ruleset.  If you want to maintain an audit trail, the best approach is probably to use something like git, or just do it manually or via a wrapper script like this:
```

#!/bin/bash

# maintain a backup of changes to iptables rules and write a log when changes are made
LOG=/var/log/iptables-changes.log
EDITOR=/usr/bin/nano
# directory where iptables rulesets are kept
IPTABLES=/usr/local/lib/iptables

cd $IPTABLES
TODAY=$(date +%Y%m%d)
# back up file
cp iptables iptables.$TODAY

# edit the file
$EDITOR iptables

# write a log entry
echo "$(date +%c) iptables updated" >> $LOG

#restart iptables with new rules
$IPTABLES/iptables

exit 0

```

---

### Post by posterberg on 2016-05-17
Yes, but I wouldn't expect anyone that wants to avoid being logged to use that script nor git.

Anyways, why wouldn't the kernel know about iptables changes? It is a kernel function isn't it?

---

### Post by Habitual on 2016-05-17
> **posterberg said:**
> Yes, but I wouldn't expect anyone that wants to avoid being logged to use that script nor git.
You're right, IF a hacker gets access the wrapper script is useless.
If "he" gets access it won't matter what logging is done. so...
**what are we really doing here**?

I smell an [XY Problem]("http://xyproblem.info/").

---

### Post by posterberg on 2016-05-17
I am not that concerned about hackers, this is primarily for auditing purposes. There are normally a lot of administrators in a large company, not all follow protocol... It is good to be able to follow logs and see what has happened.

Those legit administrator, that don't follow protocol would most likely use iptables directly instead of using config files or workaround scripts.

Honestly, I don't understand why I have to explain why I need this. I have a simple question stated in the first post...

---

### Post by SeijiSensei on 2016-05-17
No matter how large the company might be, to let "many administrators" make changes to the iptables rulesets on border routers is bad security practice.  At most we should be talking about two or three people, not "many."

---

### Post by posterberg on 2016-05-17
I have never said that this is a border router... These are general servers that have host based firewall rules. Can we please stick to the original question?

---

### Post by Habitual on 2016-05-17
Here's an idea...

DON'T LOGIN AS ROOT and use 
```
$ sudo iptables <args> <args> <args>
```

All sudo commands are logged.

I'm out. You seem really demanding for a feature that may not exist and act surprised that's it not there, or "on by default"?
I asked in my very first reply about how may users were doing these changes and you chose to not answer.
We have given you 2 options and you persist to act with incredulity ?

I'm done. I feel like I should ask you if you want Fries.

---

### Post by posterberg on 2016-05-18
It may not exist, true. But I haven't seen any response yet that really state that. I have instead only seen responses suggestion other solutions instead of focusing on the question, and people miscrediting why I would need this. It just causes frustration at both ends. I know about the workarounds, I know why I need and want this. If it's not there so be it, I will find other not as good solutions. I might even make this an official feature request as it would be peculiar if its not already there.



 I already have complete sudo logs even every command after sudo su -. I am not completely satisfied with that solution since it becomes really hard to search through and isn't very easily parsed in the SIEM since the output doesn't come in a standardized format.

I also don't think it is that outrageous to expect that a OS such as Linux actually can log security changes. It is one of the first things everybody would want to have in their audit logs. That and changes to users, groups, and filepermissions. Even Windows has this, not on by default but you can certainly enable it. Why is it so strange that someone would expect that Linux can do this as well (out of the box without creative scripts that are easily bypassed).

---

### Post by posterberg on 2016-05-18
This actually looks really promising:

[http://security.blogoverflow.com/2013/01/a-brief-introduction-to-auditd/](http://security.blogoverflow.com/2013/01/a-brief-introduction-to-auditd/)

[http://unix.stackexchange.com/questions/206891/audit-on-changes-to-the-running-iptables-configuration](http://unix.stackexchange.com/questions/206891/audit-on-changes-to-the-running-iptables-configuration)

Looks like there is a good auditing function that can be used to get an audit trail of all relevant system changes, not only iptables.

:-)

---

