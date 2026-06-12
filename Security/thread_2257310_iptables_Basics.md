---
title: "iptables_Basics"
date: 2014-12-18
forum: Security
---

### Post by sophie4 on 2014-12-18
Hi all,

I'm totally new to iptables, have read the man page and went through some tutorials on the web but could not find the answers to my questions. I would much appreciate it if you could help me with the following questions:

1. I know that you can set default policies for chains. What policy is applied to a chain if there is none specified? I guess ACCEPT?
2. suppose you are using two or more tables in your ruleset, e.g. raw and filter. You have a match for a rule in the first table i.e raw then comes the COMMIT and then there is the other table. Are the chains in the second table also traversed? Or is it like the moment you have a match the traversing is stopped and the target is applied?
3. Does the default policies for chains in one table affect the others?


Thank you in advance! :)

---

### Post by kevdog on 2014-12-18
2. Not counting any logging, once a match is made in a particular chain -- that's it, the rule is applied and no further transversing of the ruleset occurs.
3.  I believe default policies are independent.  I believe the default policy is ACCEPT #1, however everytime I've written a firewall script (a script I can use to refresh the ruleset), I've always included a default rule policy.

---

### Post by sophie4 on 2014-12-19
> **kevdog said:**
> 2. Not counting any logging, once a match is made in a particular chain -- that's it, the rule is applied and no further transversing of the ruleset occurs.
3.  I believe default policies are independent.  I believe the default policy is ACCEPT #1, however everytime I've written a firewall script (a script I can use to refresh the ruleset), I've always included a default rule policy.

Thank you for the response. I have another question about input and output interfaces, would be grateful if you could share your thoughts:
I know that -i and -o are both used in the FORWARD chain. When a packet reaches a firewall and is meant to be forwarded further, an interface on this firewall(router) can be addressed as both the input and output interface, i.e. it's an input interface when the packet just arrives and when is about to be sent further it becomes an output interface right? or Am I missing something here?

---

### Post by kevdog on 2014-12-19
I don't think your're right here.  Incoming packets are usually destined for a listening packet or server which is listening over a specific port.  The listening process or server takes this information, processes it, and then may or may not send a response back through a specific local port (known in iptables as the source port) to a remote port.  To my knowledge the input chain is never sent to the output chain specifically regarding the INPUT and OUTPUT chains.

---

### Post by sophie4 on 2014-12-19
> **kevdog said:**
> I don't think your're right here.  Incoming packets are usually destined for a listening packet or server which is listening over a specific port.  The listening process or server takes this information, processes it, and then may or may not send a response back through a specific local port (known in iptables as the source port) to a remote port.  To my knowledge the input chain is never sent to the output chain specifically regarding the INPUT and OUTPUT chains.

I think you and I are talking about two different things here. I indeed agree that that the packets entering the INPUT and OUTPUT chains are not sent to each other(as they are not related anyways). I was talking about the input and output "interfaces" in the FORWARD chain. 
I just found this great tutorial on frozentux.net from which I paste an excerpt concerning these concepts. I think I am correct on this part. ;) Please do speak if you have any objections. ;)
[TABLE="class: CALSTABLE, width: 1062"]
[TR]
[TD]Example[/TD]
[TD]iptables -A INPUT -i eth0[/TD]
[/TR]
[TR]
[TD]Explanation[/TD]
[TD]This match is used for the interface the packet came in on. Note that this option is only legal in the INPUT, FORWARD and PREROUTING chains and will return an error message when used anywhere else. The default behavior of this match, if no particular interface is specified, is to assume a string value of +. The + value is used to match a string of letters and numbers. A single + would, in other words, tell the kernel to match all packets without considering which interface it came in on. The + string can also be appended to the type of interface, so eth+ would be all Ethernet devices. We can also invert the meaning of this option with the help of the ! sign. The line would then have a syntax looking something like -i ! eth0, which would match all incoming interfaces, except eth0.[/TD]
[/TR]
[TR]
[TD]Match[/TD]
[TD]-o, --out-interface[/TD]
[/TR]
[TR]
[TD]Kernel[/TD]
[TD]2.3, 2.4, 2.5 and 2.6[/TD]
[/TR]
[TR]
[TD]Example[/TD]
[TD]iptables -A FORWARD -o eth0[/TD]
[/TR]
[TR]
[TD]Explanation[/TD]
[TD]The --out-interface match is used for packets on the interface from which they are leaving. Note that this match is only available in the OUTPUT, FORWARD and POSTROUTING chains, the opposite in fact of the --in-interface match. Other than this, it works pretty much the same as the --in-interface match. The + extension is understood as matching all devices of similar type, so eth+ would match all eth devices and so on. To invert the meaning of the match, you can use the ! sign in exactly the same way as for the --in-interface match. If no --out-interface is specified, the default behavior for this match is to match all devices, regardless of where the packet is going.[/TD]
[/TR]
[/TABLE]

[https://www.frozentux.net/iptables-tutorial/iptables-tutorial.html](https://www.frozentux.net/iptables-tutorial/iptables-tutorial.html)

---

### Post by SeijiSensei on 2014-12-20
> **sophie4 said:**
> I know that -i and -o are both used in the FORWARD chain. When a packet reaches a firewall and is meant to be forwarded further, an interface on this firewall(router) can be addressed as both the input and output interface, i.e. it's an input interface when the packet just arrives and when is about to be sent further it becomes an output interface right? or Am I missing something here?

Packets are forwarded across interfaces on the router.  The interface on which the packet arrives is the "input" interface; the interface that forwards the packet along is the "output" interface.  It's possible, but rare, that a single interface could be both the input and output interface, but usually forwarding implies two interfaces.

---

### Post by sophie4 on 2014-12-20
> **SeijiSensei said:**
> Packets are forwarded across interfaces on the router.  The interface on which the packet arrives is the "input" interface; the interface that forwards the packet along is the "output" interface.  It's possible, but rare, that a single interface could be both the input and output interface, but usually forwarding implies two interfaces.
Thank you for the reply. So if i have 2 interfaces on my router say int1 and int2 what about the scenario that a packet is generated at the router and sent on one of these two direction, then those interfaces should be specified as output interfaces right?

---

### Post by SeijiSensei on 2014-12-20
> **sophie4 said:**
> Thank you for the reply. So if i have 2 interfaces on my router say int1 and int2 what about the scenario that a packet is generated at the router and sent on one of these two direction, then those interfaces should be specified as output interfaces right?

If the packet is generated on the router, then there is no forwarding going on. The interface to be used depends entirely on the system's routing table.  In that case, the packet will be evaluated based on the OUTPUT category of the filter table for the appropriate interface.

---

