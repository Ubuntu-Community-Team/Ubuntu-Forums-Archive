---
title: "The &quot;nat&quot; table is not intended for filtering, the use of DROP is therefore inhibited"
date: 2013-06-20
forum: Security
---

### Post by MikeMunn on 2013-06-20
I am getting an error in my iptables config. I am getting the following error.

[TABLE="width: 500"]
[TR]
[TD]  * Loading FTP Rules...
iptables v1.4.4:
The "nat" table is not intended for filtering, the use of DROP is therefore inhibited.


Try `iptables -h' or 'iptables --help' for more information.
[/TD]
[/TR]
[/TABLE]

The config for concerned area is as such:

[TABLE="width: 500"]
[TR]
[TD]WANIFACE="eth0"
BWANIFACE="eth2"
LANIFACE="eth1"
VLANTRUNKIFACE="eth3"

FTP_EXT="1.1.1.1"

$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FTP_EXT -j DROP
[/TD]
[/TR]
[/TABLE]

Any comments or ideas on how to fix this?

---

### Post by SeijiSensei on 2013-06-20
Use an INPUT rule.

---

### Post by MikeMunn on 2013-06-20
> **SeijiSensei said:**
> Use an INPUT rule.

I am not familiar with that rule. Can you give me an example?

---

### Post by SeijiSensei on 2013-06-20
```
/sbin/iptables -A INPUT -p tcp -d 1.1.1.1 --dport 21 -j REJECT
```

That blocks all packets destined for port 21, the FTP port, on the remote machine at 1.1.1.1.

---

### Post by MikeMunn on 2013-06-20
> **SeijiSensei said:**
> ```
/sbin/iptables -A INPUT -p tcp -d 1.1.1.1 --dport 21 -j REJECT
```

That blocks all packets destined for port 21, the FTP port, on the remote machine at 1.1.1.1.

Maybe I need to be more specific. This is my whole rule for FTP:

echo "  * Loading FTP Rules..."
$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FTP_EXT -p tcp --dport 20:21 -j DNAT --to $FTP_INT
$IPTABLES -t nat -A PREROUTING -i $WANIFACE -d $FTP_EXT -j DROP 

Can you explain to me what that is doing because it looks to me to be excessive. I apologize if this is a newbie question. I have been given the task of maintaining this firewall and have no experience with iptables and little with Linux.

Thank you for all the help. I have had a lot of my questions answered on this forum. Also, is there anyone out there that would be willing to consult on this. It would not be a favor, it would get payment for any items helped with beyond this.

---

### Post by SeijiSensei on 2013-06-20
The NAT table enables "network address translation", which replaces the source and/or target IP addresses in a packet with a different address.  Home routers use this method to "masquerade" traffic from computers behind the firewall so it appears to come from the firewall itself.  The NAT table is not designed to filter packets; that is what the "filter" table is for.  Since that is the default table you don't need to use "-t filter" with rules like INPUT or OUTPUT.

The rules you presented first redirect all FTP traffic to the address $FTP_INT then attempts to block those packets with a DROP.  As you discovered, DROP is not a valid disposition in the NAT table.  Even if it worked, that method is unnecessarily complex.  Try replacing the two rules you have with the rule I gave you and see if that does what you want.  Obviously you can modify it to use the various environment variables that you have defined.

Most firewalls use some combination of INPUT, OUTPUT, and FORWARD to permit or block traffic.  The NAT table is used for more arcane tasks like port forwarding or masquerading.  There the primary targets are PREROUTING, which means to rewrite a packet before it is routed to another host, and POSTROUTING which rewrites packets after they have been routed.

---

### Post by MikeMunn on 2013-06-20
So really the first one is the only one that I need. The second one is not rejecting anything. The first rule is pushing it towards the internal IP of the FTP server. The other is erroneous. I can just remove it.

I don't want to block FTP, we have an ftp site that external users post things to.

---

