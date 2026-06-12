---
title: "Howto: add a blocklist to ufw"
date: 2023-10-10
forum: Security
---

### Post by poddmo on 2023-10-10
If your Ubuntu system is directly exposed to the internet, either via a public IP address or port forwarding, an IP blocklist will add another layer of protection. I created a couple of scripts that integrate with ufw and update the list daily. 
They have been designed to be very light on resource requirements and zero maintenance as the initial target platform was a single-board computer operating as a home internet gateway. After the initial installation, there are no further writes to the storage system to preserve solid state storage. Full details are available on the [GitHub]("https://help.ubuntu.com/community/GitHub") project: [https://github.com/poddmo/ufw-blocklist](https://github.com/poddmo/ufw-blocklist).

Install the ipset package
```

sudo apt install ipset

```

Backup the original ufw after.init example script
```

sudo cp /etc/ufw/after.init /etc/ufw/after.init.orig

```

Install the ufw-blocklist files
```

git clone [https://github.com/poddmo/ufw-blocklist.git](https://github.com/poddmo/ufw-blocklist.git)
cd ufw-blocklist
chmod 750 after.init ufw-blocklist-ipsum
sudo cp after.init /etc/ufw/after.init
sudo cp ufw-blocklist-ipsum /etc/cron.daily/ufw-blocklist-ipsum

```

Download an initial IP blocklist from [IPsum]("https://github.com/stamparm/ipsum")
```

curl -sS -f --compressed -o ipsum.4.txt 'https://raw.githubusercontent.com/stamparm/ipsum/master/levels/4.txt'
chmod 640 ipsum.4.txt
sudo cp ipsum.4.txt /etc/ipsum.4.txt

```

Start ufw-blocklist
```

sudo /etc/ufw/after.init start

```

Please check github for the latest releases and instructions.

---

### Post by TheFu on 2023-10-10
I'm confused.  Where is the blocklist connected to ipset and named?

With iptables, we have to create a named hash of the correct type (I use network), tell it the max size and then add an INPUT --match set with a name that DROPs any matches.
iptables:
```
-A INPUT --match set --match-set countryblocklist  src --jump DROP
```

ipset:
```
create countryblocklist hash:net family inet hashsize 2048 maxelem 65536
```
Then use ipset 
```
add countryblocklist {subnet}
```
to fill the list.  I don't bother blocking individual IPs. That's was other tools are for, like fail2ban.  I block the subnet from the provider. like
110.184.0.0/8 131.0.0.0/8 150.0.0.0/8 171.0.0.0/8 49.0.0.0/8  Based on network location and behavior.

Is something hidden or forgotten?

---

### Post by poddmo on 2023-10-10
The ipset creation and all the iptables rules are in the file: [https://github.com/poddmo/ufw-blocklist/blob/main/after.init](https://github.com/poddmo/ufw-blocklist/blob/main/after.init)
after.init is called as part of the ufw-framework(8)

I can't see any reason to set hashsize or maxlem when creating the ipset. In what way do you see them as important?
I considered changing the set type from hash:net to hash:ip but there is so little cost and it adds flexibility.

I like your subnet blocking and I will look to add an ipset for that too. Can you recommend a blocklist for subnets?

---

### Post by TheFu on 2023-10-10
> **poddmo said:**
>  
I like your subnet blocking and I will look to add an ipset for that too. Can you point me to a blocklist for subnets?

Mine are based on actions directly against my servers.  Basically, when an attack is launched, the source subnet will be added to the blocklist.
```
$ wc -l /etc/ipset.up.rules
7124 /etc/ipset.up.rules

```
It has been over a decade, but I think the initial list came from subnets tied to specific countries.  Certain places in the world are known for hacking others and since we don't do business with those countries, nothing was lost in adding them ... except our webapp logs were drastically smaller since all the bogus attempts get's them added to a blocklist.

As usual, there's always multiple ways to solve any issue.

---

### Post by poddmo on 2023-10-10
I recommend a good blocklist in addition to fail2ban. Hopefully the blocklist will prevent them having that first shot. IPsum looks to be a well-managed blocklist aggregator.
As for geo-based subnet blocking, I found this site: [https://www.ip2location.com/free/visitor-blocker](https://www.ip2location.com/free/visitor-blocker) 
Geo-based is easily circumvented but it should hopefully block botnets and "citizen activists".
Thanks for your feedback. I've added the geo-subnet blocking to my todo list.

---

### Post by Doug S on 2023-10-12
I have a fairly extensive manual block list, created over the last decade. I also block several countries via ipsets. Because they ignore robots.txt and insist on copying my entire website from a great many different IP addresses and sub-nets, I also block all of Microsoft as an ipset.

```

doug@s15:~$ sudo iptables -xvnL
Chain INPUT (policy DROP 3 packets, 147 bytes)
    pkts      bytes target     prot opt in     out     source               destination
...
  152984  8090484 DROP       all  --  enp1s0 *       0.0.0.0/0            0.0.0.0/0            match-set china src
   42445  2689428 DROP       all  --  enp1s0 *       0.0.0.0/0            0.0.0.0/0            match-set hongkong src
   19603   901362 DROP       all  --  enp1s0 *       0.0.0.0/0            0.0.0.0/0            match-set romania src
  230629  9421625 DROP       all  --  enp1s0 *       0.0.0.0/0            0.0.0.0/0            match-set russia src
    7911   486052 DROP       all  --  enp1s0 *       0.0.0.0/0            0.0.0.0/0            match-set ukraine src
  200194  8078495 DROP       all  --  enp1s0 *       0.0.0.0/0            0.0.0.0/0            match-set bulgaria src
   13549   832033 DROP       all  --  enp1s0 *       0.0.0.0/0            0.0.0.0/0            match-set microsoft src
...
    5019   218290 DROP       all  --  enp1s0 *       141.98.10.0/23       0.0.0.0/0
   45763  1830544 DROP       all  --  enp1s0 *       77.90.185.0/24       0.0.0.0/0
   22515   900600 DROP       all  --  enp1s0 *       194.26.135.0/24      0.0.0.0/0
...
  238347  9538541 DROP       all  --  enp1s0 *       89.248.160.0/20      0.0.0.0/0
...
   48335  2102898 DROP       all  --  enp1s0 *       94.102.48.0/20       0.0.0.0/0
    7291   353839 DROP       all  --  enp1s0 *       103.0.0.0/8          0.0.0.0/0
   22004   880160 DROP       all  --  enp1s0 *       104.156.155.0/24     0.0.0.0/0
...

```

---

### Post by poddmo on 2023-11-14
That is an impressive list of sets. Can you please share how you load the lists and how you keep the lists up to date?

---

### Post by Doug S on 2023-11-14
> **poddmo said:**
> That is an impressive list of sets. Can you please share how you load the lists and how you keep the lists up to date?

I use a script to load my entire firewall/router iptables rule set. The manually blocked IP's have merely been edited into the script over a great period of time. IP's that might only be blocked temporarily, or have not yet been added to the main script are added via a secondary script, currently:

```
doug@s15:~/post-boot$ cat iptables-manual-block
#! /bin/bash

sudo iptables -I INPUT 39 -s 213.109.202.0/24 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 171.67.71.80 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 198.12.88.139 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 109.205.213.150 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 104.152.52.0/24 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 141.98.10.0/23 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 77.90.185.0/24 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 194.26.135.0/24 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 52.25.208.208 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 44.230.252.91 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 100.21.24.205 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 198.144.159.0/24 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 199.167.138.161 -i enp1s0 -j DROP
sudo iptables -I INPUT 39 -s 199.19.95.83 -i enp1s0 -j DROP
```

Discovering potential new candidates for blocking is by observation of the log file at /var/log/syslog. I use unique identifiers for where each log entry came from in the iptables rule set (unlike ufw, which reuses log prefixes), so I can post process to help. Example from last week:

```
doug@s15:~/post-boot$ sudo grep GENERIC /var/log/syslog.1 | sed 's/ /\n/g' | grep "SRC=" | cut -d"." -f1,2,3,4 | sort | uniq -c | sort -g | tail -8
    405 SRC=45.140.17.205
   1402 SRC=104.255.152.65
   1462 SRC=46.17.102.6
   1841 SRC=199.19.95.83
   1850 SRC=199.167.138.161
   1852 SRC=198.144.159.129
   1863 SRC=198.144.159.105
   1870 SRC=198.144.159.22
doug@s15:~/post-boot$ sudo grep GENERIC /var/log/syslog.1 | sed 's/ /\n/g' | grep "SRC=" | cut -d"." -f1,2,3 | sort | uniq -c | sort -g | tail -8
    238 SRC=65.49.1
    375 SRC=192.33.14
    792 SRC=45.140.17
   1402 SRC=104.255.152
   1462 SRC=46.17.102
   1841 SRC=199.19.95
   1850 SRC=199.167.138
   5585 SRC=198.144.159
```So, now you see where the last couple of entries in that script came from.

As TheFu mentioned earlier, I am just trying to have less clutter in my log files.

For the entire country ipsets, and because I can never remember how, I use scripts download new aggregated lists and update the ipsets. Example:

```
doug@s15:~/post-boot$ cat block-russia.sh
#!/bin/sh
FWVER=0.01
#
# run as sudo
#
# block-russia.sh 2018.12.19 Ver:0.01
#       To get the Russia deny IP list. Use the aggregated list.
#       References (I do things a little different, and there are mistakes):
#       https://askubuntu.com/questions/868334/block-china-with-iptables
#       https://mattwilcox.net/web-development/unexpected-ddos-blocking-china-with-ipset-and-iptables
#

# First, must restore the current multi-country set.
#
ipset restore doug.ipset

# Flush any existing list.
#
ipset flush russia

# delete the list. No need actually, and fails if referenced by current iptables rule set.
#
# ipset destroy russia

# debug only
#
# ipset list russia | head -30

# Create the ipset list. If it already exists, this will give an error message.
#
ipset create russia hash:net

# Pull the latest aggregated IP set for China
#
mv ru-aggregated.zone ru-aggregated.zone.old
wget http://www.ipdeny.com/ipblocks/data/aggregated/ru-aggregated.zone

# Add each IP address from the downloaded list into the ipset 'russia'
#
for i in $(cat ru-aggregated.zone ); do ipset add russia $i; done

# Save the list as it will load a lot faster than re-generating it.
#
mv doug.ipset doug.ipset.old
ipset save --file doug.ipset

echo block-russia.sh $FWVER done.
```For the Microsoft list I get it from [here]("https://www.microsoft.com/en-us/download/details.aspx?id=53602"). As to how do I keep the lists up to date? I don't. I re-run the country stuff when I feel like it. I have noticed a delay between previously un-allocated IP address being allocated and the database getting updated. Russia seems to exploit this delay and run bad guy stuff via newly allocated IP addresses. So, I have just added a new ipset that contains all the un-allocated IP4 addresses. The releated areas of my iptables script are:


```

...
# Restore ipset stuff
#

echo "  Restoring any ipset country block lists.."

# Flush any existing lists.
# I wonder if I actually need to do this.
# Yes.
# V3.10: this is broken. Hack seems to be
# sleeps
#
echo "  ipset: flush and destroy china..."
ipset flush china
sleep 1
ipset destroy china
echo "  ipset: flush and destroy hongkong..."
ipset flush hongkong
sleep 1
ipset destroy hongkong
echo "  ipset: flush and destroy romania..."
ipset flush romania
sleep 1
ipset destroy romania
echo "  ipset: flush and destroy russia..."
ipset flush russia
sleep 1
ipset destroy russia
echo "  ipset: flush and destroy ukraine..."
ipset flush ukraine
sleep 1
ipset destroy ukraine
echo "  ipset: flush and destroy bulgaria..."
ipset flush bulgaria
sleep 1
ipset destroy bulgaria
echo "  ipset: flush and destroy microsoft..."
ipset flush microsoft
sleep 1
ipset destroy microsoft
echo "  ipset: flush and destroy unallocated..."
ipset flush unallocated
sleep 1
ipset destroy unallocated
echo "  ipset: restore..."
ipset restore --file /home/doug/post-boot/doug.ipset
...
# ipset - Entire Country Blocks
#

# China
$IPTABLES -A INPUT -i $EXTIF -m set --match-set china src -j DROP

# Hong Kong
$IPTABLES -A INPUT -i $EXTIF -m set --match-set hongkong src -j DROP

# Romania
$IPTABLES -A INPUT -i $EXTIF -m set --match-set romania src -j DROP

# Russia
$IPTABLES -A INPUT -i $EXTIF -m set --match-set russia src -j DROP

# Ukraine
$IPTABLES -A INPUT -i $EXTIF -m set --match-set ukraine src -j DROP

# Bulgaria
$IPTABLES -A INPUT -i $EXTIF -m set --match-set bulgaria src -j DROP

# Microsoft
$IPTABLES -A INPUT -i $EXTIF -m set --match-set microsoft src -j DROP

# Unallocated
$IPTABLES -A INPUT -i $EXTIF -m set --match-set unallocated src -j DROP

# direct drops. I do not like you.
#
...

```

---

### Post by edmoncu on 2024-06-25
> **poddmo said:**
> I recommend a good blocklist in addition to fail2ban. Hopefully the blocklist will prevent them having that first shot. IPsum looks to be a well-managed blocklist aggregator.
As for geo-based subnet blocking, I found this site: [https://www.ip2location.com/free/visitor-blocker](https://www.ip2location.com/free/visitor-blocker) 
Geo-based is easily circumvented but it should hopefully block botnets and "citizen activists".
Thanks for your feedback. I've added the geo-subnet blocking to my todo list.
Mentioning about fail2ban. I am curious if is it safe to have this running alongside fail2ban? I intend on having fail2ban block brute force https attacks on my web/admin panel though alongside your auto-blocklisting.

[COLOR=#000000]udpate:[/COLOR]
[COLOR=#000000]fail2ban seems to not work under Debian 12 but is working under Ubuntu 22 LTS.[/COLOR]

[COLOR=#000000]under debian 12, it just saysERROR Failed to access socket path: /var/run/fail2ban/fail2ban.sock. Is fail2ban running[/COLOR]

---

### Post by edmoncu on 2024-06-25
update 2:
there seems to be need to adjust to the setting from fail2ban under debian 12. it seems to default to monitor ssh even if it is not enabled (/etc/fail2ban/jail.d/defaults.conf).

here are the steps that i was guided to
> echo "sshd_backend = systemd" >> /etc/fail2ban/paths-debian.conf

from there, the rest works
> service fail2ban restart
fail2ban-client status

---

