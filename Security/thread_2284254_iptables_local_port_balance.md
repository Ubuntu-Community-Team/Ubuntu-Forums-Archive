---
title: "iptables: local port balance"
date: 2015-06-28
forum: Security
---

### Post by apterix on 2015-06-28
Hey!

I have two app servers that use one port each. 

For example:
Java 1 port 2771
Java 2 port 2772

The connections are been made to 2771 (java client standard)

The problem is that this java server does not has good support above a certain number of connections (because app implementation problems).


So I need to start new instances (Java 2 for example) to do balance between this servers. The best way is using iptables statistics/nth module to do the round robin. The problem is it did not work.


See above which rules I tried.


iptables -t nat -A PREROUTING -p tcp --dport 2771 -m state --state NEW -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 127.0.0.1:2771
iptables -t nat -A PREROUTING -p tcp --dport 2771 -m state --state NEW -m statistic --mode nth --every 1 --packet 0 -j DNAT --to-destination 127.0.0.1:2772

What is wrong? What is missing?

PS: I would like to use statistics modules. Of course I can write a crontab rule to change route every minute, but if round robin is ready to use, I want to try this. I know this balance is not a perfect balance, but for a emergency it will be a solution.

---

### Post by TheFu on 2015-06-28
I would use a normal reverse proxy for this - haproxy, pound, nginx ... all are pretty easy to configure and light on resources.

---

### Post by Doug S on 2015-06-29
Interesting idea.
I was not able to make it work via the lo interface either. However, I was able to make it work by destination network address translation of the port only.
I'll post my script below.
 Note that I don't bother with the "NEW" test, because the PREROUTING table is only traversed once per connection anyhow.
 Note that I don't bother using the statistic module for the second DNAT because at that point we want every hit to go through DNAT anyhow.
 I don't use java, so I used web pages, with identifiers for which page was loaded from which port.
I used ports 81 and 82 to specifically cover the case of inadvertent fall-through, where it remained at port 80.

```
#!/bin/sh
FWVER=0.01
#
# test statistics 2015.06.28 Ver:0.01
#     For a test, http://ubuntuforums.org/showthread.php?t=2284254
#     run as sudo
#

echo "Loading test rule set version $FWVER..\n"

# The location of the iptables program
#
IPTABLES=/sbin/iptables

#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
EXTIF="eth0"
EXTIP="192.168.111.140"
UNIVERSE="0.0.0.0/0"

# Don't know if needed or not
echo Enabling forwarding...
echo "1" > /proc/sys/net/ipv4/ip_forward

#Clearing any previous configuration
#
echo "  Clearing any existing rules and setting default policy to ACCEPT.."
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -F FORWARD
$IPTABLES -t nat -F
# Delete user defined chains
$IPTABLES -X
# Reset all IPTABLES counters
$IPTABLES -Z

echo about to load rules.

$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -p tcp --destination-port 22 -j ACCEPT
#$IPTABLES -A INPUT -i $EXTIF -p tcp --destination-port 80 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -p tcp --destination-port 81 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -p tcp --destination-port 82 -j ACCEPT

echo about to load statistic rules.

$IPTABLES -t nat -A PREROUTING -i $EXTIF -d $EXTIP -p tcp --dport 80 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to $EXTIP:81
$IPTABLES -t nat -A PREROUTING -i $EXTIF -d $EXTIP -p tcp --dport 80 -j DNAT --to $EXTIP:82

echo Test rule set version $FWVER done.
```I did this from another computer:```
#!/bin/dash

echo "wget from test-smy once every 5 seconds forever. Doug Smythies 2015.06.29"
echo
while [ 1 ];
do
# eliminate the dns step by using the ip address.
  wget 192.168.111.140
  grep port index.html
  rm index.html
  sleep 5
done
```And observed it alternate between port 81 and 82. Additionally:```
doug@test-smy:~$ [COLOR=#ff0000]sudo iptables -v -L -n -x[/COLOR]
Chain INPUT (policy DROP 15 packets, 1828 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       2      100 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
     526    39146 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       1      104 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
      [COLOR=#ff0000]43[/COLOR]     2580 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            [COLOR=#ff0000]tcp dpt:81[/COLOR]
      [COLOR=#ff0000]43[/COLOR]     2580 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            [COLOR=#ff0000]tcp dpt:82[/COLOR]

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 439 packets, 117953 bytes)
    pkts      bytes target     prot opt in     out     source               destination
``````
doug@test-smy:~$ [COLOR=#ff0000]sudo iptables -t nat -v -L -n -x[/COLOR]
Chain PREROUTING (policy ACCEPT 22 packets, 1803 bytes)
    pkts      bytes target     prot opt in     out     source               destination
      [COLOR=#ff0000]43[/COLOR]     2580 DNAT       tcp  --  eth0   *       0.0.0.0/0            192.168.111.140      tcp dpt:80 statistic mode nth every 2 to:192.168.111.140:[COLOR=#ff0000]81[/COLOR]
      [COLOR=#ff0000]43[/COLOR]     2580 DNAT       tcp  --  eth0   *       0.0.0.0/0            192.168.111.140      tcp dpt:80 to:192.168.111.140:[COLOR=#ff0000]82[/COLOR]

Chain INPUT (policy ACCEPT 87 packets, 5264 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 2 packets, 320 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain POSTROUTING (policy ACCEPT 2 packets, 320 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

---

