---
title: "switching from ufw to iptables, config rules ok &amp; enough or not?"
date: 2013-04-27
forum: Security
---

### Post by clearski on 2013-04-27
Some time ago I had iptables set on a Darwin running workstation, but now I realise that most of the rules I had were not really helping. Not sure if they could have done any evil... luckily I was behind another router enabled firewall. Because I like iptables more than ufw, I'd like to completely remove ufw and use iptables only. After reading* and a little bit of thinking :), I imagined how the iptables config would look like. But before it would be great to know from the experts here if the config lines below are fine and enough.

I am not doing routing, nor do I have any servers running at this time, nor any LAN. I'll definitely setup a ftp and web server for testing in a few weeks, but right now all I'm doing beyond the local interface is browsing and reading emails, listening music, kinda regular stuff. I am going out through a router which provides DHCP fixed addressing (via mac filtering).

However, I am using OpenDNS servers instead of my providers', they are configured through the Network Manager (Network Connections via GUI). I am not sure if they should appear or not in this config, the OpenSND servers are being reffered to only here on Linux, not on the router.

Below is the script:

```
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts #drop ICMP Echo requests to broadcast addresses
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route #drop source routed packets
echo 1 > /proc/sys/net/ipv4/tcp_syncookies #enable TCP SYN cookies
echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects #do not accept ICMP redirect
echo 0 >/proc/sys/net/ipv4/conf/all/send_redirects #do not send ICMP redirect
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter #spoofing protection
echo 1 > /proc/sys/net/ipv4/conf/all/log_martians #log martian packets

iptables --flush  #flush all existing chains

#Allow all traffic on loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -i lo -j ACCEPT

#Default policies
iptables -P INPUT REJECT **
iptables -P OUTPUT REJECT
iptables -P FORWARD REJECT #Not doing any routing stuff

#Allow established connections to continue uninterrupted
iptables -A INPUT -i eth0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -i eth0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

#Block all traffic which isn't affected by the above rules
iptables -A INPUT -j REJECT

#Only log dropped packets, I don't know if this will log rejected ones, too.
iptables -A -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level7
```

Any comment & help in fine-tuning these lines is much appreciated.

*
Primary sources:
1) [https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall)
2) [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Plus other Internet forums / sites.

**
According to [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables) & [http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject), REJECT is preffered to DROP.

---

### Post by TheFu on 2013-04-27
Do you understand that ufw is just an interface to iptables?  All it does is make setting up rules inside iptables easier.

Just because you configure opendns, that doesn't mean that your provider isn't intercepting DNS calls and redirecting them to their DNS servers. Mine was doing that - until I discovered the account setting that overrode the behavior.

Sorry, can't help you with iptables settings.  I only use it to create 1-to-1 port forwarding rules on a specific public IP on the router or to block subnets from any access to the public IPs after cracking attempts are seen. I DROP those attempts to let the attackers wait.

There are a few books that describe all the different firewall rules and other techniques available.  No Starch Press has 1 that I can recommend.

---

### Post by Doug S on 2013-04-27
Probably you wanted this:```
iptables -A OUTPUT [COLOR=#ff0000]-i[/COLOR] eth0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```to be this:```
iptables -A OUTPUT [COLOR=#ff0000]-o[/COLOR] eth0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```However, taking a look at the bigger context```
#Allow established connections to continue uninterrupted
```How is any "NEW" connection allowed such that it can become "ESTABLISHED,RELATED"? You need to either relax the OUTPUT restrictions or specify some allowed NEW outgoing sessions.

---

### Post by clearski on 2013-04-27
> **TheFu said:**
> Do you understand that ufw is just an interface to iptables?  All it does is make setting up rules inside iptables easier. 

Yes, I know, but I want to use iptables directly.

> Just because you configure opendns, that doesn't mean that your provider isn't intercepting DNS calls and redirecting them to their DNS servers. Mine was doing that - until I discovered the account setting that overrode the behavior. 

I know that, too. I used to run DNSCrypt so that they knew that I had requests to resolve domains, but didn't know what domains I was looking for because all requests were addressed to OpenDNS with an encrypted connection. But it was on OS X, I found it more difficult here on Linux and requires a lot of stuff which I don't understand right now. I didn't say that OpenDNS means a private, direct resolving, but I thought they might need a rule somewhere in the ipchains config, that's why I mentioned it.

> 
Sorry, can't help you with iptables settings.  I only use it to create 1-to-1 port forwarding rules on a specific public IP on the router or to block subnets from any access to the public IPs after cracking attempts are seen. I DROP those attempts to let the attackers wait.

There are a few books that describe all the different firewall rules and other techniques available.  No Starch Press has 1 that I can recommend.

I was going to get some books, but I'm not sure which one is best for starting. No Starch Press is among publishing houses which have interesting titles, I've already seen 'em. First I got to get an Unleashed title, then some Networking books will come. :) Soon, I hope! :)

Thanks for your points!

---

### Post by clearski on 2013-04-27
> **Doug S said:**
> 
Probably you wanted this:

```
iptables -A OUTPUT [COLOR=#ff0000]-i[/COLOR] eth0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```
to be this:
```
iptables -A OUTPUT [COLOR=#ff0000]-o[/COLOR] eth0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```

Actually, it was a mistake. I thought that was the same synthax for both incoming and outgoing connections. I read again the options and indeed there is **-i** (only match if the packet is coming in on the specified interface) and **-o** (out-interface), so even if the interface is eth0, incoming and outgoing should be addresses with -i / -o.

> 
However, taking a look at the bigger context```
#Allow established connections to continue uninterrupted
```How is any "NEW" connection allowed such that it can become "ESTABLISHED,RELATED"? You need to either relax the OUTPUT restrictions or specify some allowed NEW outgoing sessions.

I think you're talking about the default OUTGOING policy.

```
iptables -P OUTPUT ACCEPT
```

Is it right?

---

### Post by Doug S on 2013-04-27
Yes, you could it via a default OUTPUT policy of accept. Many people do exactly that. Others prefer to only allow out to certain destination ports. It is up to you how tight you want to make it. Myself, I think the default OUTUT policy of ACCEPT is good enough for your application (which you can then delete the OUTPUT ESTABLISHED,RELATED rule as it is no longer needed).

---

### Post by clearski on 2013-04-27
> **Doug S said:**
> Yes, you could it via a default OUTPUT policy of accept. Many people do exactly that. Others prefer to only allow out to certain destination ports. It is up to you how tight you want to make it. Myself, I think the default OUTUT policy of ACCEPT is good enough for your application (which you can then delete the OUTPUT ESTABLISHED,RELATED rule as it is no longer needed).


Alright. I am not going to set destinations ports for outgoing connections, I'll just let the applications do that. So the config should be like this now (I am only posting the part which was modified):

...

iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

iptables -A INPUT -i eth0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -j DROP

...

---

### Post by Doug S on 2013-04-27
For your DHCP you probably need:```
iptables -A INPUT -i eth0 -p udp --sport 68 --dport 67 -j ACCEPT
```near the start of your INPUT chain.

---

### Post by clearski on 2013-04-28
> **Doug S said:**
> For your DHCP you probably need:```
iptables -A INPUT -i eth0 -p udp --sport 68 --dport 67 -j ACCEPT
```near the start of your INPUT chain.

I also found an interesting rule which drops packets coming on eth0 but claiming to be from localhost. I added this rule to the script and actually put it first after flushing the chain rules. I also corrected the the output rule on lo which had **-i **option instead **-o**

I am attaching the script and if everything's fine that would be it for now.

Thank you very much, Doug!

---

### Post by clearski on 2013-04-28
IPTABLES up and running well!

```
sudo iptables -v -L INPUT
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  eth0   any     localhost            anywhere            
83244   13M ACCEPT     all  --  lo     any     anywhere             anywhere            
    0     0 ACCEPT     udp  --  eth0   any     anywhere             anywhere             udp spt:bootpc dpt:bootps
 1554 2066K ACCEPT     all  --  eth0   any     anywhere             anywhere             ctstate RELATED,ESTABLISHED
   55 11911 DROP       all  --  any    any     anywhere             anywhere            
    0     0 LOGNDROP   all  --  any    any     anywhere             anywhere
```

```
sudo iptables -v -L OUTPUT
Chain OUTPUT (policy ACCEPT 1177 packets, 341K bytes)
 pkts bytes target     prot opt in     out     source               destination         
83322   13M ACCEPT     all  --  any    lo      anywhere             anywhere
```

 ```
sudo iptables -v -L FORWARD
Chain FORWARD (policy DROP 0 packets, 0 bytes)
```

Here's how I did it, maybe there are some interested to setup a *very simple* iptables firewall.

1. Disconnected and disabled networking with Network Manager.
2. sudo apt-get remove ufw gufw
3. sudo apt-get autoremove
4. Wrote all the iptables rules in a file, ~/Desktop/iptables.txt

#I am attaching my latest config, I've done some changes to log rules and added 

```
iptables-save > /etc/iptables.rules
```

at the end of file. Basically, any updates to the rules in this file will be written to /etc/iptables.conf (I'll make this file a script and run it just below)

5. Renamed the file from iptables.txt to iptables.sh
6. Changed permissions so the script could be run:

```
sudo chmod 755 iptables.sh
```

6. Run the file

```
sudo ./iptables.sh
```

To make rules persistent and automatically load them at every bood, I did

```
sudo nano /etc/network/interfaces
```

and added

```
pre-up iptables-restore < /etc/iptables.rules
```

after the line with my interface. Saved the file.

Restarted. Tested the firewall. Enabled Networking and Selected a connection.

Here's my automatic generated /etc/iptables.rules

```
cat /etc/iptables.rules 
# Generated by iptables-save v1.4.12 on Sun Apr 28 08:23:55 2013
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
:LOGNDROP - [0:0]
-A INPUT -s 127.0.0.1/32 -i eth0 -j DROP
-A INPUT -i lo -j ACCEPT
-A INPUT -i eth0 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
-A INPUT -i eth0 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -j DROP
-A INPUT -j LOGNDROP
-A OUTPUT -o lo -j ACCEPT
-A LOGNDROP -j LOG
-A LOGNDROP -j DROP
COMMIT
```

And some netstat output:

```
sudo netstat -pcaW | grep -i est
tcp        0      0 localhost:9151          localhost:59230         ESTABLISHED 2553/tor        
tcp        0      0 192.168.2.153:52819     someserver:https ESTABLISHED 2553/tor        
tcp        0      0 192.168.2.153:33774     someserver:https ESTABLISHED 2553/tor        
tcp        0      0 localhost:59230         localhost:9151          ESTABLISHED 2550/vidalia
```

Many thanks to everyone who helped me in setting this firewall and to those who wrote the how-to-s I mentioned in my first post.
Most of the setup is described there.

---

### Post by Doug S on 2013-04-28
Glad it is working for you.
Note that with the change to a default policy of ACCEPT for the OUTPUT chain, you no longer need this rule:```
iptables -A OUTPUT -o lo -p all -j ACCEPT
```Your newly added rule```
iptables -A INPUT -p all -s localhost -i eth0 -j DROP
```is interesting, and I have not seen such a rule before. Please let us know if you ever get a hit on that rule. Myself, I am questioning the need for such a rule. I have reviewed my tcpdump logs for every packet on my networks external interface back to 2012.03.20 (over a year) and never would have had a hit on such a rule. Even if such a packet did arrive on the external interface, it wouldn't satisfy the generic criteria to be ACCEPTED and so would be DROPped or REJECTed anyhow.

---

### Post by clearski on 2013-04-28
I've updated both the rules file and the script, now I have only one ACCEPT policy for the OUTPUT chain on every interface.

I found the rule which drops packets claiming to be from localhost on netfilter's website ([http://netfilter.org/documentation/index.html#documentation-howto](http://netfilter.org/documentation/index.html#documentation-howto)), I don't remember exactly where, but I think it was in the tutorials section. They have great info there, I can't wait to spare some free time to read more about networking and filtering.

I think this thread could be marked as solved.

Thank you!

---

