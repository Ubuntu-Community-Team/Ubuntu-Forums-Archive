---
title: "filtering connection strings w/ iptables"
date: 2011-03-12
forum: Security
---

### Post by kajfat on 2011-03-12
Hello, I have several CS servers running on ubuntu server, and sometimes someone is trying to brute server's RCON password with the program called HLBrute. I've found the following rules to prevent such hack attacks, but they don't work :(
What can be wrong in these rules?

> iptables -A INPUT -p udp -m multiport --dport 26000:30000 -m string --algo kmp --string "HLBrute" -m limit --limit 1/hour --limit-burst 5 -j LOG --log-prefix " HLBrute_Ataka "
iptables -A INPUT -p udp -m multiport --dport 26000:30000 -m string --algo kmp --string "HLBrute" -j DROP

---

### Post by skraps on 2011-03-12
Is iptables taking the commands? Is it barking back a error? What does "--algo kmp" do? Iv tried googleing it and having problems finding a answer.

---

### Post by cariboo on 2011-03-12
@skraps, check man iptables, it is located [here]("http://linux.die.net/man/8/iptables")

---

### Post by BkkBonanza on 2011-03-12
I don't see a problem in the rule but you should note that it only searches for the string. If someone has modified the attack to use a different string then presumably it would not match. You may need to do more analysis of the packet data to determine what string to match on since this one doesn't seem to work. This is just a general comment as I'm not familiar with HLBrute in particular.

Also, after running the command check the output of **sudo iptables -vL** to be sure the rule is there. Maybe post here if unclear. Make sure the command is added to your firewall or init commands so it gets added after booting (just running the command once doesn't do that).

---

