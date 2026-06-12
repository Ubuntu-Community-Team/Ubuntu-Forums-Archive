---
title: "Iptables script secure?"
date: 2010-06-15
forum: Security
---

### Post by Blackbird_13 on 2010-06-15
First attempt at iptables.  How secure is this iptables script?

```
# flush all chains
iptables -F
# Configure default policies
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
# Rules added to the INPUT chain.
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i wlan0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -i wlan0 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -i eth0 -j ACCEPT
# Finally, DENY all connection requests to any UDP port not yet provided
# for and all SYN connection requests to any TCP port not yet provided for.
iptables -A INPUT -s 0/0 -d 0/0 -p udp -j DROP
iptables -A INPUT -s 0/0 -d 0/0 -p tcp --syn -j DROP
```Additional information: For ssh I use rsa key authentication (no password). I only install software from authorised repositories.

How secure would my pc be with this script? Is it possible for a third party to hack into my pc?

---

### Post by bodhi.zazen on 2010-06-15
You can shorten your rule set, but I do not see any "problem".

Is it working ? Is it doing what you want ?

```
# flush all chains[FONT=monospace]
[/FONT]iptables -F[FONT=monospace]
[/FONT]# Configure default policies[FONT=monospace]
[/FONT]iptables -P INPUT DROP[FONT=monospace]
[/FONT]iptables -P OUTPUT ACCEPT[FONT=monospace]
[/FONT]iptables -P FORWARD DROP[FONT=monospace]
[/FONT]# Rules added to the INPUT chain.[FONT=monospace]
[/FONT]iptables -A INPUT -i lo -j ACCEPT[FONT=monospace]
[/FONT]iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT[FONT=monospace]
[/FONT]iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```You do not need to specify and interface for your "ESTABLISHED,RELATED as you do not have an eth1 eth2 wlan1 wlan2 ect, and you are not accepting traffic on one interface and not another.

Same with ssh

You set the default policy for DROP so you do not need to add any additional rules for SYN packets (your policy already drops these packets).

You will loose your ssh access if you flush iptables (due to your default policy of DROP).

---

### Post by Blackbird_13 on 2010-06-15
Many thanks for your comments. 

>  You will loose your ssh access if you flush iptables (due to your  default policy of DROP).I have obviously misunderstood the effect of "flush". I thought that each time I boot and run the script "flush" deletes all rules prior to re-building the INPUT rules. I thought that the default policy of DROP would only then apply to anything that falls through my INPUT rules (including ssh port 22).

Where am I going wrong?

---

### Post by bodhi.zazen on 2010-06-15
> **Blackbird_13 said:**
> Many thanks for your comments. 

I have obviously misunderstood the effect of "flush". I thought that each time I boot and run the script "flush" deletes all rules prior to re-building the INPUT rules. I thought that the default policy of DROP would only then apply to anything that falls through my INPUT rules (including ssh port 22).

Where am I going wrong?

I am not sure what you are asking.

```
sudo iptables -F
``` removes all your rules.

If you do that via a ssh connection, because your default policy is DROP, you will now be locked out.

As it is now you are setting your rules via a script, so the script adds in rules that allow you to have ssh access.

My point is that a default policy of DROP can result in a lock out if you manually flush your rules.

For remove servers, where I do not have physical access, I keep the Default policy set to ACCEPT and make the last rule in a chain to dorp all traffic.

iptables -A INPUT -j DROP

Same effect as setting the default policy to DROP, but now if I flush the rules with

```
sudo iptables -F
``` then I am not locked out.

While you might *think* you are always going to use your script, 6 months from now you may have an issue and flush your rules -> lock out.

---

### Post by Blackbird_13 on 2010-06-15
I now understand your point. Many thanks for taking the trouble to explain.

---

### Post by bodhi.zazen on 2010-06-15
> **Blackbird_13 said:**
> I now understand your point. Many thanks for taking the trouble to explain.

You are most welcome =)

Not that I have ***ever*** locked myself out mind you :twisted:

---

### Post by linux-hack on 2010-06-15
> **Blackbird_13 said:**
> 
How secure would my pc be with this script? Is it possible for a third party to hack into my pc?

Thats not a rely good question ... cause you never rely know that, or you can do some pentesting on it and find out.. iptables is a good why to close dors for hackers but juste a simple script will not guaranty you good security. You could install intrusion detection systems, anti rootkits and so on and you computer will still not be impenetrable ... It is a start though ...

To secure at a reasonably level you must know first what you want to secure and why ? close non needed ports, stop non needed services and have a good policy in using your computer (no outside code execution, packages from I don't know where and so on). 

Hope this helps you understand that a computer is never 100% sure and hacker safe.

---

### Post by linux-hack on 2010-06-17
Here is something you'd like ;) : [http://www.linuxtopia.org/LinuxSecurity/index.html](http://www.linuxtopia.org/LinuxSecurity/index.html)
[http://www.linuxtopia.org/Linux_Firewall_iptables/index.html](http://www.linuxtopia.org/Linux_Firewall_iptables/index.html)

---

### Post by Blackbird_13 on 2010-06-18
Thanks for the links - very informative.

---

