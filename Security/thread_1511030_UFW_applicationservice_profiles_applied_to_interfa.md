---
title: "UFW application/service profiles applied to interface names only"
date: 2010-06-16
forum: Security
---

### Post by airtonix on 2010-06-16
Greetings, 

The issue today is : 

"how to apply an application/service profile (/etc/ufw/applications.d/*) to a interface name in a cli ufw rule command " 

[SIZE="4"]Background[/SIZE]
`man ufw` tells us that : 
```
ufw allow in on eth0 to any port 80 proto tcp
```
Allows traffic through interface eth0 on port 80 over the tcp protocol.


[SIZE="4"]The Target Scenario[/SIZE]
[LIST]
[*] Two wifi cards.
[*] One internally to a trusted group of computers (wlan0)
[*] The other facing an untrusted network that provides iternet access (wlan1)
[*] The two interfaces (wlan0 & wlan1) are bridged using the NAT feature of UFWs before.rules (see here : [http://www.nowhere.dk/articles/tip_nat_with_ubuntus_ufw_firewall](http://www.nowhere.dk/articles/tip_nat_with_ubuntus_ufw_firewall) )
[/LIST]

When managing firewall rules for wlan1 to limit access to various ports, it would be desired to only specify the interface name instead of having to rename a bunch of rules and specify ip addresses.

Why? 
1. To edit a rule, you need to delete it and recreate it.
2. It gets tedious to use the delete command for each rule you have that specifies a port and ip address using : 
```
sudo ufw delete blah blah blah [wall of text] 
```
3. GUFW is terrible in this regard. 
 b. It doesn't allow you to specify interfaces in a rule yet.
 c. It also randomly removes the wrong rule when removing a rule.


[SIZE="4"]Desired Scenario[/SIZE]
Ideally i want to simply use a command like : 

```
$ sudo ufw deny in on wlan0 for samba
$ sudo ufw deny out on wlan0 for samba
$ sudo ufw deny in on wlan0 for cups
$ sudo ufw deny out on wlan0 for cups
$ sudo ufw deny in on wlan0 for zeroconf
$ sudo ufw deny out on wlan0 for zeroconf
```

But ufw responds that it does not like that command.


The purpose of this thread is to begin dialoge on the usage of application profiles being applied to interface names.

---

### Post by bodhi.zazen on 2010-06-16
Most graphical front ends (firestarter, gufw) and even ufw itself are all front ends to iptables.

To some extent these applications are "dumbed down" in that not all the options available on the command line (iptables) are available on the graphical front ends or in ufw.

While this works well for many desktop users who do not have complex firewall needs (such as NAT) , I suggest for your needs you use ufw or iptables.

This general advice applies to many graphical tools, not just gufw.

If you want to communicate your suggestions for improvements to gufw, I suggest you file a bug report.

On the other side of the coin, now that you understand the basics of firewalls, you will likely find teh syntax of iptables very very easy.

iptables -A INPUT -p tcp -i wlan0 -m multiport --dports 22,80,443 -j ACCEPT

You can specify port ranges as well

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by marquinos on 2010-06-17
> **airtonix said:**
> 3. GUFW is terrible in this regard. 
 b. It doesn't allow you to specify interfaces in a rule yet.
True, this is a good improvement for the future ;)

 > **airtonix said:**
> c. It also randomly removes the wrong rule when removing a rule.
In 4 days was [fixed]("https://bugs.launchpad.net/gui-ufw/+bug/578404"). Now it's waiting [upload]("https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/581091"). Edit 20-Jun: uploaded 18 Jun 2010 ;)

Best regards ;)

---

### Post by airtonix on 2010-06-19
> **bodhi.zazen said:**
> 
Blah blah blah...

Use iptables instead 

Blah blah blah.

:confused:
I don't think you read my post properly.

---

### Post by Syzzer on 2010-08-05
I was looking for the same thing. This works in 10.04:

```

ufw allow in on eth0 to any app Samba

```

---

