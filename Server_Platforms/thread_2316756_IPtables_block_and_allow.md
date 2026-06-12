---
title: "IPtables block and allow"
date: 2016-03-10
forum: Server Platforms
---

### Post by Travis_Swentosky on 2016-03-10
Hello all,

First time posting on the forums, usually i can figure out most of my own problems but this time i'm stumped.

I have two servers
1. Ubuntu Server 14 with the Zimbra email server installed  IP address for example is 10.0.0.1 (public IP)
2. Sophos virtual email appliance  with an example IP of 10.0.0.2 (public IP)

I want to configure my ubuntu server to ONLY accept port 25 connections to it from my sophos virtual appliance and to block all other incoming port 25 connections?  How would i accomplish this with iptables?

---

### Post by papibe on 2016-03-10
Hi Travis_Swentosky. Welcome to the forums ):P

Start reading [here]("https://help.ubuntu.com/community/IptablesHowTo"), and [here]("https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-iptables-on-ubuntu-14-04"). 

Then try to come out with a draft of your rules, and we'll take a look and comment.

Do you have physical access to those servers? One of the most common mistakes while working with iptables is to lock yourself out of the server because of wrong rule.

If not, please consider that you would also have to include rules to allow remote access, so you can keep administrating the server (usually ssh).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by darkod on 2016-03-10
Ignoring any other setup you might need, the rule you are talking about is for example:
```
-A INPUT -i eth0 -p tcp -s 10.0.0.2 --dport 25 -j ACCEPT
```

It can be used like that in a file that you can load with iptables-restore on boot, or in a script with 'iptables' in front and run as root.

I usually use a file with rules and load it with iptables-restore.

---

### Post by Travis_Swentosky on 2016-03-10
Thanks darkod,

After using your code
My current iptables config looks like the following

DROP  all  --  114.134.184.0/21  anywhere
DROP  all  --  1.68.0.0/14  anywhere
DROP  all  --  1.80.0.0/13  anywhere
ACCEPT  tcp  --  sophosvirtualIP  anywhere  tcp dpt:smtp

Now just curious but since that is the accept line, how do i block the rest of the connections to port 25?

---

### Post by darkod on 2016-03-10
Usually the INPUT chain policy will be DROP, otherwise there is not much point. So all traffic not allowed by a rule, gets blocked by the general policy of the chain. That's why you don't need to specifically block port 25 for the rest of the world. Unless your policy is ACCEPT but in such case you are not really running a firewall... :)

---

### Post by Travis_Swentosky on 2016-03-10
Darkod,

I think i understand what you said.  The problem though is that after the change and performing sudo iptables -L is it shows that specific accept line, but i can still access port 25 from the outside world.  I don't need anything else configured to be blocked on this server, just port 25 with the exception of the sophos appliance being allowed to access it.
As it stands, the server is still accepting all port 25 connection attempts.

---

### Post by darkod on 2016-03-10
Post the output of:
```
sudo iptables -L -n -v
```

That will show us more...

---

### Post by Travis_Swentosky on 2016-03-10
Chain INPUT (policy ACCEPT 183K packets, 88M bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       all  --  *      *       114.134.184.0/21     0.0.0.0/0
    0     0 DROP       all  --  *      *       1.68.0.0/14          0.0.0.0/0
    0     0 DROP       all  --  *      *       1.80.0.0/13          0.0.0.0/0
    0     0 ACCEPT     tcp  --  eth0   *       96.89.61.132         0.0.0.0/0            tcp dpt:25

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 269K packets, 581M bytes)
 pkts bytes target     prot opt in     out     source               destination

The 3 DROPS are blocks for Russia, China, and Korea

---

### Post by darkod on 2016-03-10
You see, the chain INPUT policy is ACCEPT, so it accepts all connections not explicitly forbidden. I usually do it the other way around, to block all and allow only what I need. You can't think of which traffic to block in advance.

But how it is now, if you change INPUT policy to DROP you will block your ssh connection too because you have no rule to allow ssh. You also need to allow basic rules for related and established traffic.

Here are basic rules I am using. I create a file called /etc/iptables.rules and put this content in it:
```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]


-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
-A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT


COMMIT
```

The three rules for ssh create a sort of protection blocking connections from anyone that enters wrong pass three times in a short period of time.

To those rules you would need to add your port 25 rule, at the end. You can test the rules with:
```
sudo iptables-restore < /etc/iptables.rules
```

That loads them temporarily, if you get locked out reboot the server and they go away. After you are sure they are working as you expect them, you can make them load at boot. You can try them if you want to...

PS. Those rules allow ssh from anywhere. If you access the server only from specific IPs even better, you can allow only that traffic and ssh will be blocked for the rest.

PPS. When saying to add other rules you need at the end, I meant the end of the list of rules. All rules most be before the COMMIT command. That command should be the last.

---

