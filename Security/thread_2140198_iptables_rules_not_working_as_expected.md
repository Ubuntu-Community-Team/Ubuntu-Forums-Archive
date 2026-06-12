---
title: "iptables rules not working as expected?"
date: 2013-04-28
forum: Security
---

### Post by mister3000 on 2013-04-28
Hi everyone, I'm hoping someone knows what could be causing this problem I am having with my iptables rules.

**Here is the desired behavior:**
I have a rule to time an IP out for 10 seconds if they have more than 15 connections opened to my server. If that IP is still trying to make connections during those 10 seconds, the timeout will update until at least 10 seconds with no new connections have passed.

I also have a rule before the timeout rule that will accept packets from all already established connections. So, the clients first 15 connections will stay opened.

**Here is the problem:**
For some reason these rules will sometimes give ALL already connected clients the 10 second timeout at once. It doesn't matter what port they are connected to, everybody will get the timeout. This usually seems to happen during peak time when more clients are connected to my machine.

According to munin, the firewall throughput is around 2.0 - 2.5 packets per second around the times it seems to happen the most. I'm not sure if that is low or high. When it does happen the time for it to happen again will be random, it might happen again in 5 minutes or it might be an hour.

**The rules:**
Here are the rules I use. I commented lines I feel might be the suspect with "HELP!".

```
#!/bin/bash



####################
# Start firewall.
####################
echo "Setting $(hostname) Firewall..."




#####################
# Setup variables.
#####################
IPT="/sbin/iptables"


PUB_IF="eth1"    # Public interface
LO_IF="lo"    # Loopback interface




#############################################
# Flush & delete current rules and chains.
#############################################
$IPT -F
$IPT -X




######################
# Setup our chains.
######################
$IPT -P INPUT DROP
$IPT -P FORWARD DROP
$IPT -P OUTPUT ACCEPT


$IPT -N Always
$IPT -N Allow
$IPT -N Bogus
$IPT -N Enemies
$IPT -N ValidPorts




#############################################
# Reset all chains packet & byte counters.
#############################################
$IPT -Z




###############################################################
# Jump to the specified chains in the order they are listed.
###############################################################
$IPT -A INPUT -j Bogus
$IPT -A INPUT -j Always
$IPT -A INPUT -j Enemies
$IPT -A INPUT -j Allow
$IPT -A INPUT -j DROP    # No matches made in our chains, so just drop.






##### Start managing our custom chains #####






#################
# Bogus chain.
#################
$IPT -A Bogus -i $PUB_IF -m state --state INVALID        -j DROP


$IPT -A Bogus -i $PUB_IF -m pkttype --pkt-type broadcast    -j DROP
$IPT -A Bogus -i $PUB_IF -m pkttype --pkt-type multicast    -j DROP


$IPT -A Bogus -f                        -j DROP
$IPT -A Bogus -p tcp ! --syn -m state --state NEW        -j DROP
$IPT -A Bogus -p tcp --tcp-flags ACK,FIN FIN            -j DROP
$IPT -A Bogus -p tcp --tcp-flags ACK,PSH PSH            -j DROP
$IPT -A Bogus -p tcp --tcp-flags ACK,URG URG            -j DROP
$IPT -A Bogus -p tcp --tcp-flags FIN,RST FIN,RST        -j DROP
$IPT -A Bogus -p tcp --tcp-flags SYN,FIN SYN,FIN        -j DROP
$IPT -A Bogus -p tcp --tcp-flags SYN,RST SYN,RST        -j DROP
$IPT -A Bogus -p tcp --tcp-flags ALL ALL            -j DROP
$IPT -A Bogus -p tcp --tcp-flags ALL NONE            -j DROP
$IPT -A Bogus -p tcp --tcp-flags ALL FIN,PSH,URG        -j DROP
$IPT -A Bogus -p tcp --tcp-flags ALL SYN,FIN,PSH,URG        -j DROP
$IPT -A Bogus -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG    -j DROP
$IPT -A Bogus -p tcp --tcp-flags ALL FIN            -j DROP


$IPT -A Bogus -s 169.254.0.0/16        -j DROP
$IPT -A Bogus -s 172.16.0.0/12        -j DROP
$IPT -A Bogus -s 192.0.2.0/24        -j DROP
$IPT -A Bogus -s 192.168.0.0/16        -j DROP
$IPT -A Bogus -s 10.0.0.0/8        -j DROP


$IPT -A Bogus -s 127.0.0.0/8 ! -i $LO_IF -j DROP




##################
# Always chain.
##################
$IPT -A Always -p udp --dport 123 -j ACCEPT
$IPT -A Always -i $LO_IF -j ACCEPT


# HELP! This rule should allow already connected clients stay connected, so why would a new connection be made?
# HELP! Not to mention the 'Always' chain is called before the 'Enemies' chain, so somehow this rule isn't hitting?
$IPT -A Always -m state --state ESTABLISHED,RELATED -j ACCEPT




#######################
# Valid ports chain.
#######################
$IPT -A ValidPorts -i $LO_IF -j RETURN
$IPT -A ValidPorts -m udp -p udp --dport 30000:30005 -j RETURN
$IPT -A ValidPorts -m tcp -p tcp --dport 6000 -j RETURN
$IPT -A ValidPorts -m udp -p udp --dport 6000 -j RETURN


$IPT -A ValidPorts -m recent --name portscan --set -j DROP




###################
# Enemies chain.
###################
# HELP! This rule should only go through when connspam is set below, right?
$IPT -A Enemies -m recent --name connspam --update --seconds 10 -j DROP


$IPT -A Enemies -m recent --name portscan --update --seconds 60 -j DROP


# Maximum of 15 connections per IP.
# HELP! Some reason connspam gets set for all clients at once every so often, and they get the 10 second timeout.
# HELP! Unless the 10 second timeout rule is being used even when connspam isn't set here?
$IPT -A Enemies -m connlimit --connlimit-above 15 -m recent --name connspam --set -j DROP


$IPT -A Enemies -j ValidPorts




#################
# Allow chain.
#################
$IPT -A Allow -i $PUB_IF -m udp -p udp --dport 30000:30005 -j ACCEPT
$IPT -A Allow -i $PUB_IF -m tcp -p tcp --dport 6000 -j ACCEPT
$IPT -A Allow -i $PUB_IF -m udp -p udp --dport 6000 -j ACCEPT






#####################
# End of firewall.
#####################


echo "Finished setting up firewall."
exit 0
```

I'm probably using something wrong as I'm still rather bad at making the rules. A lot of the 'Bogus' chain rules I found while trying to learn iptables.

---

### Post by Doug S on 2013-04-29
I can not see a problem with what you have done for tcp packets.
It is less clear (to me) for udp packets, as there are not the same clear states with udp (I think).
When the issues occurs, it is with udp?
I have been trying to think up a way to test this on one of my computers, but so far haven't.

---

### Post by mister3000 on 2013-04-29
> **Doug S said:**
> I can not see a problem with what you have done for tcp packets.
It is less clear (to me) for udp packets, as there are not the same clear states with udp (I think).
When the issues occurs, it is with udp?
I have been trying to think up a way to test this on one of my computers, but so far haven't.

Yes this does occur on UDP. All of my applications use UDP so I have no way to know if it happens on TCP. I just find it strange how it happens to everyone at once as I thought both states and recent are IP based? Unless UDP drops all states at once and forces everyone to make a NEW state up to 16 times? I'm just speculating.

---

### Post by Doug S on 2013-04-29
> I just find it strange how it happens to everyone at once as I thought both states and recent are IP based?I agree it is strange.> Unless UDP drops all states at once and forces everyone to make a NEW state up to 16 times?No it shouldn't, as far as I know.

You mentioned a packet rate of 2 to 2.5 per second through the firewall, which seems very low. But if your site rate is actually low, then perhaps some extra logging steps could be added to your iptable rule set to help figure out what is happening. You could also monitor the connection tracking table to look for anomalies and possible insight.```
sudo cat /proc/net/ip_conntrack
```I have even used a script to help before:```
doug@doug-64:~/bin$ cat con_track
#!/bin/dash
echo "conntrack monitor. Doug Smythies 2011.02.11"
echo
COUNTER=0
date >con_t_data
sudo cat /proc/net/ip_conntrack >>con_t_data
while [ $COUNTER -lt 500 ];
do
  date >>con_t_data
  sudo cat /proc/net/ip_conntrack >>con_t_data
  echo "COUNTER $COUNTER"
  $((COUNTER=$COUNTER+1))
  sleep 1
done
echo "conntrack monitor. finished."
```

Edit: Perhaps something could also be learned by observing the "recent" table itself:```
cat /proc/net/xt_recent/connspam
```

---

### Post by mister3000 on 2013-04-29
My system is setup to allow 29 seconds before a UDP state table entry expires. When looking at ip_conntrack I can see connected clients will keep a steady 29 seconds until they disconnect, then it starts counting down to 0. This seems correct to me.

It's as if the whole state table isn't being read or is being dumped during the time this problem happens, though. I'm so lost.

> **Doug S said:**
> Perhaps something could also be learned by observing the "recent" table itself:```
cat /proc/net/xt_recent/connspam
```
I see numbers after "last_seen:" and "oldest_pkt:". At first I thought they were unix timestamps but after converting them they don't appear to be. Any idea what they represent?

---

### Post by Doug S on 2013-04-29
> I see numbers after "last_seen:" and "oldest_pkt:". At first I thought they were unix timestamps but after converting them they don't appear to be. Any idea what they represent?It had actually been awhile since I looked at a "recent" table, so I was wondering also. I reverse calculated from enties in one of mine. The number is basic clock ticks, typically 250 ticks per second. As far as I could determine the 0 point was arbitrary, at about 214 days ago for my computer.
Maybe I am sending this whole thread sideways, which is not my intent.

Oh... I keep forgetting to ask: Does your computer need to do dns lookups, and should special allowance be made for such?

---

### Post by mister3000 on 2013-04-29
> **Doug S said:**
> It had actually been awhile since I looked at a "recent" table, so I was wondering also. I reverse calculated from enties in one of mine. The number is basic clock ticks, typically 250 ticks per second. As far as I could determine the 0 point was arbitrary, at about 214 days ago for my computer.
Maybe I am sending this whole thread sideways, which is not my intent.

Oh... I keep forgetting to ask: Does your computer need to do dns lookups, and should special allowance be made for such?

Thanks for all the help Doug I really appreciate it. As for DNS lookups I'm not too sure. I don't really think so. Wouldn't the rules I posted allow that though? I set the default output policy to accept and any already established,related input packets are also allowed in (unless a dns lookup works differently).

I'm going to try increasing the values for the ip_list_tot and ip_pkt_list_tot parameters of the xt_recent module to see if that helps anything.

---

### Post by Doug S on 2013-04-29
> As for DNS lookups I'm not too sure. I don't really think so. Wouldn't the rules I posted allow that though? I set the default output policy to accept and any already established,related input packets are also allowed in (unless a dns lookup works differently).Yes, of course. Not sure what I was thinking.

---

### Post by Doug S on 2013-04-30
> **mister3000 said:**
> I'm going to try increasing the values for the ip_list_tot and ip_pkt_list_tot parameters of the xt_recent module to see if that helps anything.I would be very interested in the results of your test, and hope you will report back. Things remain unclear to me as to what is going wrong for you, but I think increasing ip_list_tot is a good idea for a test. It is less clear to me that increasing ip_pkt_list_tot will help.

By the way, I have (sort of) figured out how to interprete the "oldest_pkt:" entry in the "recent" table list: The list of hit times for a given IP address is actually a ring buffer array type list, and the "oldest_pkt" points to the oldest packet entry in the list, counting off from the start with an index of 0***. Below is an excerpt from two different snapshots from my bad guy SSH detector "recent" table, with added time difference calculations:```
Snap Snot # 1, yesterday:
src=111.113.13.86 last_seen: 4635131547 oldest_pkt: 8 4626550898 4627814364 4629089779 4630375738 4631633222 4632828617 4634002862 4635131547 4612071483 4613201087 4614322227 4615452069 4616593997 4617807264 4619055347 4620279434 4621542715 4622824607 4624090530 4625317402
                              Seconds since previous: 4933.984   5053.864   5101.66    5143.836   5029.936   4781.58    4696.98    4514.74    [COLOR=#ff0000]Oldest[/COLOR]     4518.416   4484.56    4519.368   4567.712   4853.068   4992.332   4896.348   5053.124   5127.568   5063.692   4907.488
.
Snap Snot # 2, today:
src=111.113.13.86 last_seen: 4653438736 oldest_pkt: 3 4650937853 4652205935 4653438736 4630375738 4631633222 4632828617 4634002862 4635131547 4636252999 4637370015 4638510524 4639726216 4640968433 4642198027 4643444517 4644714641 4645959396 4647185189 4648408335 4649671395
                              Seconds since previous: 5065.832   5072.328   4931.204   [COLOR=#ff0000]Oldest[/COLOR]     5029.936   4781.58    4696.98    4514.74    4485.808   4468.064   4562.036   4862.768   4968.868   4918.376   4985.96    5080.496   4979.02    4903.172   4892.584   5052.24
```*** If the ring buffer has not wrapped around the oldest packet index points to a non-existant entry, just after the most recent entry.

A completely unrelated side note: My site has been under SSH attack from 111.113.13.86 (China) for over a week. It only opens a new TCP session every 1.4 hours or so (see times above) and so never triggers my block rule. It uses all allowed per session attempts ( MaxAuthTries in sshd_config (Which, on my system, I have set to 2. The default is 6)). I have never seen this particular attack signature before.

---

### Post by mister3000 on 2013-05-01
It is very nice to know the math behind the times, thank you. I will be sure to report back soon with the results of changing ip_list_tot and ip_pkt_list_tot. I'm hoping it will be fixed as from what I read the default ip_list_tot is only 100 and I clearly have more than 100 connections during peak days/hours.

I am curious how the recent table reuses its data once it's full. My guess would be it overwrites the oldest last_seen entry.

---

### Post by Doug S on 2013-05-05
> **mister3000 said:**
> I am curious how the recent table reuses its data once it's full. My guess would be it overwrites the oldest last_seen entry.It took a couple of weeks, but my recent table finally got to 100 entries. And yes, it overwrites the the oldest last_seen entry. I had to wait for the third overwrite because for the first two the oldest last_seen entry and the oldest list entries were the same.

By the way for this:> The number is basic clock ticks, typically 250 ticks per second. As far as I could determine the 0 point was arbitrary, at about 214 days ago for my computer.The clock tick counter (jiffies is the name used in the code) is initalized to 2**32 - 300 * 250 = 4,294,892,296. Originally the idea was "starting with an offset of -300 seconds is done on purpose, to expose bugs in drivers which don't handle wrapping of the jiffies". However, now and at least on my 64 bit server, the jiffy count does not wrap in those first 5 minutes. I did a check calculation that my up time = what is listed - that offset, and it does.

---

### Post by mister3000 on 2013-05-07
Hello again Doug, as promised I'm here to report my findings. From what I can tell my issue was fixed by increasing [COLOR=#000000]ip_list_tot. I played around a bit with [/COLOR][COLOR=#000000]ip_pkt_list_tot and it didn't seem to make a difference. I still have a user complaining about strange lag, but it doesn't happen to everyone at once anymore so I'm guessing he has a different problem.

I really appreciate your time helping and teaching me, thank you![/COLOR]

---

### Post by Doug S on 2013-05-08
Thanks very much for reporting back. I learned a lot from this thread.

---

