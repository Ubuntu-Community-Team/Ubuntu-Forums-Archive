---
title: "UFW is blocking legitimate requests"
date: 2016-04-20
forum: Server Platforms
---

### Post by Bergschreck on 2016-04-20
I run some services on a hosted vserver with ufw installed.
 I have ports 443 and 993 allowed by app rules:
```
WWW Full                   ALLOW       Anywhere
IMAPS                      ALLOW       Anywhere
```
But sometimes I see blocked requests to these ports in ufw.log. How can I find the cause for these blockings?

  This is an example for such a blocked request:
```
Apr 19 20:16:45 s3 kernel: [1288908.787003] [UFW BLOCK] IN=eth0 OUT= MAC=xx:xx:xx:xx:xx:xx:00:26:88:75:be:09:08:00 SRC=88.217.126.43 DST=xx.xx.xx.xx LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=57119 DPT=993 WINDOW=0 RES=0x00 RST URGP=0
```

 The source IP is the dynamic WAN IP of my DSL connection. When I search for the vendor of the source MAC (00:26:88), I find it is "Juniper Networks". I don't own hardware from Juniper Networks, so I assume it is some router at my DSL provider.

  My questions are: why does some network equipment at my DSL provider contact my vserver with my ip address? And why are these requests blocked by ufw? Is there a way to find the cause with iptables commands?

Background: I run fail2ban with a rule to ban hosts that do a portscan. So I ban hosts that try to connect to a non-open port, by filtering the ufw.log for block entries. This way I lockout my self, because something is blocked from my own ip address, which should not be blocked.

---

### Post by darkod on 2016-04-20
I haven't used ufw much, only once when I didn't know enough about iptables and ufw looked easier to handle. But very soon i noticed it works strange sometimes and I lost my confidence in it.

Basic iptables is much easier than one might think, so you can probably try testing your server without ufw and only with iptables.

Apart from that, I really do not have a direct answer to your query.

---

### Post by Bergschreck on 2016-04-20
Thank you darkod for this hint. Do you know a good tutorial about iptables. I tried it several times to understand iptables, but always gave up because it seemed too complicated to me.

---

### Post by darkod on 2016-04-20
The "problem" with searching for iptables info on the internet is that they exist since many years ago, maybe even as long as linux exists. And in the first period it is probably true that it was more complex to use them. You can find examples using iptables with complex scripts, etc. That is what scared me too. But in recent years the process is much more user friendly, especially for simple setups.

For example, the most common way to load iptables rules on boot is to create a file, lets say /etc/iptables.rules, and load it with a command in /etc/network/interfaces. From that log entry I see your interface is eth0. In /etc/network/interfaces in the eth0 settings, add a new line:
```
post-up iptables-restore < /etc/iptables.rules
```

That command will load the rules from that file on each boot as soon as the interface comes up. When first setting it up, make sure you test the rules first before adding that line otherwise if the rules are "bad" they will always load on boot. :)

As for the rules in /etc/iptables.rules, the basic ones I use for ssh access allowed and all outgoing traffic allowed (I see no point blocking my server's outgoing traffic for my use):
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

Short explanation:
That first line for the INPUT chain allows traffic for the localhost interface (lo interface).
The second line allows all related and established traffic. The thing with iptables is that if you tell it to DROP the INPUT traffic, that will also drop the reply packets of your own outgoing traffic unless you have that line.
The lines about SSH basically count attempts from the source IP and if someone tries 4 times in 60secs with wrong password, they drop it.

As you can see at the top are the policies you want for each chain. I have DROP for INPUT and FORWARD, and ACCEPT for OUTPUT. If you want to be more restrictive and use DROP for OUTPUT you will need adequate rules allowing your own outgoing traffic otherwise nothing will go out of your server.

You said you want to allow port 443 and 993 TCP for all source IPs right? In such case add these two rules to the above (always before the COMMIT line, that line should be last and always present!):
```
-A INPUT -i eth0 -p tcp --dport 443 -j ACCEPT
-A INPUT -i eth0 -p tcp --dport 993 -j ACCEPT
```

Basically what you are saying is:
-A INPUT add input rule
-i eth0 incoming interface
-p tcp protocol type
--dport XXX destination port, the port you want to open
-j ACCEPT the action, ACCEPT

I usually don't use fail2ban so I don't know if you will need some adjustments, but on their own the above rules work 100%.

You can always load iptales rules from file manually with:
```
sudo iptables-restore < /etc/iptables.rules
```

You can test that way after you create the file and before adding it to /etc/network/interfaces. If you lock yourself out, simply reboot the server from the provider CP and your "bad" iptables rules are gone (because they are still not loading on boot).

In the future you can have two files, like /etc/iptables.test and /etc/iptables.rules. You can make your tests with the test file (especially until you get more familiar with iptables) loading it manually, and if it locks you, reboot the server which will load your "good" rules. Only after you are sure the test rules work, you can copy the file into the main file and that one gets loaded on boot.

Give it a go...

---

### Post by Bergschreck on 2016-04-21
Thank you darkod, I will give it a try.

---

### Post by Habitual on 2016-04-21
> **Bergschreck said:**
> 
Background: I run fail2ban with a rule to ban hosts that do a portscan. So I ban hosts that try to connect to a non-open port, by filtering the ufw.log for block entries. This way I lockout my self, because something is blocked from my own ip address, which should not be blocked.

Try adding your_IP to the fail2ban exclusion in 2 ways:
```
fail2ban-client set <jail> ignoreip <My_ip> 
```

Can I see the portscan filter?

Or open your /etc/fail2ban/jail.local (you did make a copy of /etc/fail2ban/jail.conf, yes?)
[my_jail] or 
[DEFAULT] sections:
ignoreip = <my_IP>

Resources:
```
http://www.fail2ban.org/wiki/index.php/Whitelist
```

References:
```
fail2ban-client help
```

---

### Post by darkod on 2016-04-21
> Try adding your_IP to the fail2ban exclusion

But how would that work for a dynamic WAN IP? He has one...

---

### Post by Habitual on 2016-04-21
> **darkod said:**
> But how would that work for a dynamic WAN IP? He has one...

ignoreip accepts /cidr values
so whitelisting dynamic IPs is possible.


```
ignoreip = 10.0.0.0/8
ignoreip = 172.16.0.0/12
ignoreip = 192.168.0.0/24
ignoreip = 192.168.1.0/24
ignoreip = 127.0.0.1/24
ignoreip = 127.0.0.1/32

```
are all valid ignoreip directives.

---

### Post by Habitual on 2016-04-21
> **Habitual said:**
> ignoreip accepts /cidr values
so whitelisting dynamic IPs is possible.
I quoted my own post. See above post for actual edit.

---

### Post by Bergschreck on 2016-04-21
> **Habitual said:**
> Can I see the portscan filter?The filter is simple:```
failregex = ^%(__prefix_line)s\[UFW BLOCK] IN=eth0 .* SRC=<HOST>
```Whitelisting is difficult, because my DSL provider uses several ip ranges (which I don't know all).Whitellisting is only a workaround for a problem that should not exist.

---

### Post by Habitual on 2016-04-21
> **Bergschreck said:**
> Whitelisting is difficult, because my DSL provider uses several ip ranges (which I don't know all)
Ask your provider for CIDR network values?
It's not a "secret". Perfectly acceptable to ask.

You seem intent on doing it your way, so I'll leave you to it.

Good Luck.

---

### Post by Bergschreck on 2016-04-26
darkod, thank you again for your iptables instruction. It helped me understanding iptables. Yesterday I configured my firewall according your instruction, and it works great!
Now, that I understand iptables better, maybe I found the cause why ufw is blocking some requests. I found this in before.rules:
```
-A ufw-before-input -m state --state INVALID -j DROP
```
This drops invalid packets and logs them the same as drops by chain policy.
I will change the logging label for these invalid packets, and see if this is the cause.

---

### Post by darkod on 2016-04-26
No problem, glad I could help.

I'm not sure that's an issue because that rule is dropping only invalid packets, which like it says, would be invalid even if they are allowed through. But you can investigate...

---

### Post by Bergschreck on 2016-04-26
Hi darkod,my problem is, I try to protect myself against portscans. So I made a fail2ban filter that looks for blocked packets in the log.I now made iptable filters, that distinguish between explicit drops and drops by policy. I now can see that there are often invlid packets, looks like they are coming from one of our smartphones (Android). I now ban only on packets that are dropped by policy, and that looks good at the moment.

---

