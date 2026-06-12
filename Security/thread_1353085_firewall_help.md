---
title: "firewall help"
date: 2009-12-12
forum: Security
---

### Post by boabbyrab on 2009-12-12
[FONT=Georgia][SIZE=1]hi guys i need sime help here, i am at college and one of the courses is linux, i have intalled ubuntu on an old PC to help me with it an have been managing to get by with so far untill i came to firewall. the quetion i have is this[/SIZE][/FONT]

[SIZE=1][FONT=Georgia]FIREWALL – produce a report containing an iptable firewall definition for a system requiring the following features:[/FONT][/SIZE]
[LIST]
[*]
[LIST]
[*][SIZE=1][FONT=Georgia]Full egress and ingress filtering (i.e. defaults are all REJECT)[/FONT][/SIZE]
[*][SIZE=1][FONT=Georgia]The machine has only one network connection, eth0.[/FONT][/SIZE]
[*][SIZE=1][FONT=Georgia]The machine runs ssh, telnet, apache, and qmail.[/FONT][/SIZE]
[*][SIZE=1][FONT=Georgia]It should be able to surf the web, send email, and make DNS lookups.[/FONT][/SIZE]
[*][FONT=Georgia][SIZE=1]The apache user should not be allowed to surf the web[/SIZE][/FONT]
[*][FONT=Times New Roman][FONT=Georgia][SIZE=1]You should make the rest of the rules as security focused (and sensible) as possible[/SIZE][/FONT][/FONT]
[/LIST]
[/LIST][FONT=Times New Roman][FONT=Georgia][SIZE=1]now i can flush the tables and set the policy (by changing REJECT to either DROP/ACCEPT)but the other actual commands confuses me, so i was wondering (well hoping) that anybody can help me out with this one.[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Georgia][SIZE=1]any help much appreciated.[/SIZE][/FONT][/FONT]

---

### Post by lovinglinux on 2009-12-12
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

---

### Post by boabbyrab on 2009-12-12
had a look at those tutorials before posting still bit confused but this is commands i have so far:
[SIZE=1]iptables –F INPUT [/SIZE]
[SIZE=1]iptables –F OUTPUT[/SIZE]
[SIZE=1]iptables –F FORWARD `[/SIZE]
[SIZE=1]# -F flushes the tables, no rules set[/SIZE]
[SIZE=1] [/SIZE]
[SIZE=1]iptables –P INPUT REJECT[/SIZE]
[SIZE=1]iptables –P OUTPUT REJECT[/SIZE]
[SIZE=1]iptables –P FORWARD REJECT[/SIZE]
[SIZE=1]# -P sets the policy, REJECT deletes packets and terminates, however sends back a #ICMP message to sender (shows info about firewall ruleset)[/SIZE]
[SIZE=1] [/SIZE]
[SIZE=1] iptables –A INPUT –p tcp --sport 22 –j ACCEPT[/SIZE]
[SIZE=1] iptables –A INPUT –p tcp --sport 23 –j ACCEPT[/SIZE]
[SIZE=1] [/SIZE]
[SIZE=1] iptables –A INPUT –p tcp --sport http –j ACCEPT[/SIZE]
[SIZE=1] iptables –A INPUT –p tcp  --sport smtp –j ACCEPT[/SIZE]
[SIZE=1] iptables –A INPUT  -p udp  --sport ns_addr –j ACCEPT[/SIZE]
[SIZE=1]#assuming DNS nameserver is ns_addr[/SIZE]
[SIZE=1] iptables –A OUTPUT state --state NEW –p tcp --sport  80 –m owner –uid-owner=apache             –j DROP[/SIZE]
[SIZE=1]does the above look ok or do i need more info[/SIZE]
[SIZE=1]cheers[/SIZE]

---

### Post by Rob_H on 2009-12-12
If you haven't already, consider using **ufw** to configure firewall rules. It is a little more user-friendly than manipulating iptables directly.

---

### Post by boabbyrab on 2009-12-12
cheers for info but i have to show the configuration as above (if right) to do it so really need to know if its right or do i need more

---

### Post by cariboo on 2009-12-12
I always like to suggest a hands on approach, set up your rules and try things out. Watch /var/log/syslog for results.

BTW standard font formatting makes your posts a lot easier to read.

---

### Post by boabbyrab on 2009-12-12
sorry about the font copy & pasted from word proccessor and it was different font from standard, how do i test it to check it works, college has vm but i cannot for life of me remember login details and it has to be in for monday (its harder than i thought)
looked at tutorials etc i know that ssh is port 22, http is port 80 and dns look up is the adress name and i thinl blocking apache works (got that from tutorial) just hoping it is the right commands.
cheers

---

