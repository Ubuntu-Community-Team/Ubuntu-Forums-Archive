---
title: "iptables with ipset issues, ubuntu 12.04"
date: 2015-10-04
forum: Server Platforms
---

### Post by andrew725 on 2015-10-04
Hi all,

I'm still learning the ropes with iptables and seem to be hitting an error when trying to load my rules.  I'm not quite sure what's going as I've used the same setup without any problems on an Ubuntu 14.04 box..I'm not sure if my OS version (12.04) is causing a conflict somewhere or if a module is missing that I'm not aware of.

I'm using this tutorial to load standard iptables rules as well as ipset to block China - sorry for anyone reading this from China, I just don't have time to deal with their DDOS crap: [https://mattwilcox.net/web-development/unexpected-ddos-blocking-china-with-ipset-and-iptables](https://mattwilcox.net/web-development/unexpected-ddos-blocking-china-with-ipset-and-iptables)

if I try to load the rules with this bit added to the rules set ```
-A INPUT -p tcp -m set --match-set china src -j DROP
``` it'll error out: 
iptables-restore v1.4.12: Set china doesn't exist.
Error occurred at line: 13

if I comment out line #13 ```
-A INPUT -p tcp -m set --match-set china src -j DROP
``` and then try loading the rules, there's no issues at all.

furthermore, there's a crontab set up to run at 5am daily to keep the list of IPs up to date for China that seems to be failing as well with the following errors:
/etc/block-china.sh: 2: /etc/block-china.sh: ipset: not found
--2015-10-04 05:59:01--  [http://www.ipdeny.com/ipblocks/data/countries/cn.zone](http://www.ipdeny.com/ipblocks/data/countries/cn.zone)
Resolving [www.ipdeny.com]("http://www.ipdeny.com") ([www.ipdeny.com]("http://www.ipdeny.com"))... 192.241.240.22
Connecting to [www.ipdeny.com]("http://www.ipdeny.com") ([www.ipdeny.com]("http://www.ipdeny.com"))|192.241.240.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 90210 (88K)
Saving to: `./cn.zone'

     0K .......... .......... .......... .......... .......... 56%  481K 0s
    50K .......... .......... .......... ........             100% 1.04M=0.1s

2015-10-04 05:59:01 (630 KB/s) - `./cn.zone' saved [90210/90210]

here's the code in /etc/block-china.sh:
```

# Create the ipset list
ipset -N china hash:net

# remove any old list that might exist from previous runs of this script
rm cn.zone

# Pull the latest IP set for China
wget -P . http://www.ipdeny.com/ipblocks/data/countries/cn.zone

# Add each IP address from the downloaded list into the ipset 'china'
for i in $(cat /etc/cn.zone ); do ipset -A china $i; done

# Restore iptables
/sbin/iptables-restore < /etc/iptables.firewall.rules

```

if anyone can help me out, I'd greatly appreciate it!

thanks!!!

---

### Post by matt_symes on 2015-10-04
Thread moved to server platforms.

This may be a better sub forum for your query. I have left a redirect in the old sub forum.

---

### Post by andrew725 on 2015-10-04
> **matt_symes said:**
> Thread moved to server platforms.

This may be a better sub forum for your query. I have left a redirect in the old sub forum.

thanks.

---

### Post by Doug S on 2015-10-05
Thanks for your posting. Myself, I am getting tired of constantly adding China sub-nets to my iptables rule set, on a reactionary basis. So I might try your method, and just block all of China.

Anyway, It looks to me as though you do not have ipset installed on your 12.04 computer, so your script is failing, and subsequently your iptables rule set is failing.

---

### Post by andrew725 on 2015-10-05
> **Doug S said:**
> Thanks for your posting. Myself, I am getting tired of constantly adding China sub-nets to my iptables rule set, on a reactionary basis. So I might try your method, and just block all of China.

Anyway, It looks to me as though you do not have ipset installed on your 12.04 computer, so your script is failing, and subsequently your iptables rule set is failing.

ipset is installed, per running whereis on my box:

whereis ipset
ipset: /usr/sbin/ipset /usr/share/man/man8/ipset.8.gz

---

### Post by Doug S on 2015-10-06
I was going by this line:> /etc/block-china.sh: 2: /etc/block-china.sh: ipset: not foundfrom your post.

Anyway, to experiment, I have made a brand new 12.04.5 server guest VM on my main 14.04 test server host. I don't seem to be having any difficulties. This is my script:```
#!/bin/bash

# experiment with using ipset to block all of china.
# see also: http://ubuntuforums.org/showthread.php?t=2297530
#
IPTABLES=/sbin/iptables
IPSET=/usr/sbin/ipset

echo "begin block china script."
# this must be done first, or the next step complains
#flush any previous run of this. Only using the INPUT chain, so far.
$IPTABLES -F INPUT

# the list must not be in use before this will work.
# clear things, in case of any previous run.
$IPSET -destroy china

# Create the ipset list
$IPSET -create china hash:net

# remove any old list that might exist from previous runs of this script
#rm cn.zone

# Pull the latest IP set for China
#wget -P . http://www.ipdeny.com/ipblocks/data/countries/cn.zone

# Add each IP address from the downloaded list into the ipset 'china'
for i in $(cat /home/doug/cn.zone ); do $IPSET -A china $i; done

# Restore iptables
#/sbin/iptables-restore < /etc/iptables.firewall.rule

# And now set the rules
$IPTABLES -A INPUT -m set --match-set china src -j DROP

echo "end block china script."

```Note 1: I have commented out some stuff, since I am just experimenting for now.
Note 2: Observe, that I dropped the tcp protocol only DROP, but rather DROP all packets from China.

EDIT: To make it work with CRON, I had to specify the complete paths for the program names, as the default path didn't include the appropriate directories. In this edit, I am replacing the script above with the current version.  The "echo" statements are merely so that CRON will send an e-mail to "nobody" even when there are no issues, just so I know it worked.

---

