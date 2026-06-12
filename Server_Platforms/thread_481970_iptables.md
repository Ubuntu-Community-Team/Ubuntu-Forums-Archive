---
title: "iptables"
date: 2007-06-23
forum: Server Platforms
---

### Post by tommytomato on 2007-06-23
Hi all

I have been following this link for a while, got one problem I cant seem to save so it can boot up at start.

link
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I'm running Ubuntu 6.06.1 LTS

> ave your firewall rules to a file

# iptables-save > /etc/iptables.up.rules

Then modify the /etc/network/interfaces script to apply the rules automatically (the bottom line is added)

auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.up.rules

You can also prepare a set of down rules and apply it automatically

auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.up.rules
  post-down iptables-restore < /etc/iptables.down.rules



this doesn't seem to work for me

can any one help me out please.

TT

---

### Post by dzoner on 2007-06-23
why don't you just create firewall script in /etc/init.d and symlink it to default runlevel?

---

### Post by keithweddell on 2007-06-23
Can you post the contents of /etc/network/interfaces and  /etc/iptables.up.rules?  An extra pair of eyes often helps and someone may be able to spot something.


Keith

---

### Post by tommytomato on 2007-06-24
I'm so sorry guys

I haven't been reciving the email replys back to my email box

What I've been trying to do is set up iptables from the comand line, I'm using ubuntu 6.0.6-1

I've been following this page [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I was adding this to my /etc/network/interfaces

I had the pre-up iptables-restore < /etc/firewall is the wrong spot, I had it before the iface eth0 inet static and not after it, ok so now it loads ok on start.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#pre-up iptables-restore < /etc/iptables.up.rules
#post-down iptables-restore < /etc/iptables.down.rules
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
pre-up iptables-restore < /etc/firewall

```

One thing thou when i try to access my site after taking out the port 80 I can still see the site and so can others out side my network can still view the site.

I'm not realy sure whats going on or am i doing the right thing

A couple of questions if i may

1. how do you turn on iptables, and thats if you do
2. how do i test to see if its blocked or unblocked I was using a port scanner on the net to can my IP address.

Here is a copy of my iptables I created

```
oot@rockinghamgateway:~# iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  a83-132-97-14.cpe.netcabo.pt  anywhere            
DROP       all  --  81.199.85.110        anywhere            
DROP       all  --  218.16.120.80        anywhere            
DROP       all  --  mx4.url.com.tw       anywhere            
DROP       all  --  218.0.153.219.broad.cq.cq.dynamic.163data.com.cn  anywhere            
DROP       all  --  63-93-95-121.lsan.mdsg-pacwest.com  anywhere            
DROP       all  --  002.011.dsl.syd.iprimus.net.au  anywhere            
DROP       all  --  mail.ala-hawaii.org  anywhere            
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  127.0.0.0/8          anywhere            
DROP       all  --  anywhere             127.0.0.0/8         
DROP       tcp  --  anywhere             anywhere            tcp flags:!SYN,RST,ACK/SYN state NEW 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  127.0.0.0/8          anywhere            
ACCEPT     all  --  10.0.0.0/8           anywhere            
ACCEPT     all  --  192.168.1.0/24       anywhere            
```

I now have lost the iptables i have created because i ran iptables-restore i think :D:o:):(

So I have to start again, any one care to explain whats going on, I am trying

O yer I've also set my instant email notification :)

TT

---

### Post by tommytomato on 2007-06-24
> **dzoner said:**
> why don't you just create firewall script in /etc/init.d and symlink it to default runlevel?

What the, sorry I haven't got that far yet

TT

---

### Post by tommytomato on 2007-06-24
Opp's here is my /etc/iptables.up.rules

but i created my other one and saved it as /etc/firewall

```
# Generated by iptables-save v1.3.3 on Sat Jun 23 14:26:42 2007
*filter
:INPUT ACCEPT [955:73113]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [739:286876]
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -j DROP
COMMIT
# Completed on Sat Jun 23 14:26:42 2007

```

TT

---

### Post by tommytomato on 2007-06-24
yep another post

Here is what i've typed in via the command line

```
root@rockinghamgateway:~# iptables -A INPUT -s 83.132.97.14 -j DROP
root@rockinghamgateway:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  a83-132-97-14.cpe.netcabo.pt  anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
root@rockinghamgateway:~# iptables -A INPUT -s 81.199.85.110 -j DROP
root@rockinghamgateway:~# iptables -A INPUT -s 218.16.120.80 -j DROP
root@rockinghamgateway:~# iptables -A INPUT -s 210.59.228.94 -j DROP 
root@rockinghamgateway:~# iptables -A INPUT -s 219.153.0.218 -j DROP
root@rockinghamgateway:~# iptables -A INPUT -s 63.93.95.121 -j DROP 
root@rockinghamgateway:~# iptables -A INPUT -s 203.134.154.2 -j DROP
root@rockinghamgateway:~# iptables -A INPUT -s 67.52.65.10 -j DROP
root@rockinghamgateway:~# iptables -A INPUT -i lo -j ACCEPT
root@rockinghamgateway:~# iptables -A INPUT -s 127.0.0.0/255.0.0.0 -j DROP
root@rockinghamgateway:~# iptables -A INPUT -d 127.0.0.0/255.0.0.0 -j DROP
root@rockinghamgateway:~# iptables -A INPUT -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -m state --state NEW -j DROP
root@rockinghamgateway:~# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
root@rockinghamgateway:~# iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
root@rockinghamgateway:~# iptables -A INPUT -p tcp -m tcp --dport 25 -j ACCEPT
root@rockinghamgateway:~# iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
root@rockinghamgateway:~# iptables -A INPUT -p tcp -m tcp --dport 110 -j ACCEPT
root@rockinghamgateway:~# iptables -A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
root@rockinghamgateway:~# iptables -A INPUT -j DROP
root@rockinghamgateway:~# iptables -A OUTPUT -s 127.0.0.0/255.0.0.0 -j ACCEPT
root@rockinghamgateway:~# iptables -A OUTPUT -s 10.0.0.0/255.0.0.0 -j ACCEPT
root@rockinghamgateway:~# iptables -A OUTPUT -s 192.168.1.0/255.255.255.0 -j ACCEPT
root@rockinghamgateway:~# iptables-save > /etc/firewall
root@rockinghamgateway:~# iptables-save
# Generated by iptables-save v1.3.3 on Sun Jun 24 12:17:23 2007
*filter
:INPUT ACCEPT [1182:105185]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [1308:657320]
-A INPUT -s 83.132.97.14 -j DROP 
-A INPUT -s 81.199.85.110 -j DROP 
-A INPUT -s 218.16.120.80 -j DROP 
-A INPUT -s 210.59.228.94 -j DROP 
-A INPUT -s 219.153.0.218 -j DROP 
-A INPUT -s 63.93.95.121 -j DROP 
-A INPUT -s 203.134.154.2 -j DROP 
-A INPUT -s 67.52.65.10 -j DROP 
-A INPUT -i lo -j ACCEPT 
-A INPUT -s 127.0.0.0/255.0.0.0 -j DROP 
-A INPUT -d 127.0.0.0/255.0.0.0 -j DROP 
-A INPUT -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -m state --state NEW -j DROP 
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 25 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 110 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT 
-A INPUT -j DROP 
-A OUTPUT -s 127.0.0.0/255.0.0.0 -j ACCEPT 
-A OUTPUT -s 10.0.0.0/255.0.0.0 -j ACCEPT 
-A OUTPUT -s 192.168.1.0/255.255.255.0 -j ACCEPT 
COMMIT
# Completed on Sun Jun 24 12:17:23 2007
root@rockinghamgateway:~# 


```

reboot comes up ok, iptables loads ok on boot up, now what ? how do I test it ?

TT

---

### Post by tommytomato on 2007-06-24
found a way to test it, now i'm lost, I see that the iptables i created is not working :(

> GRC Port Authority Report created on UTC: 2007-06-24 at 04:40:41

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
                            119, 135, 139, 143, 389, 443, 445, 
                            1002, 1024-1030, 1720, 5000

    1 Ports Open
   20 Ports Closed
    5 Ports Stealth
---------------------
   26 Ports Tested

The port found to be OPEN was: 80

Ports found to be STEALTH were: 21, 23, 135, 139, 445

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

TT

---

### Post by tommytomato on 2007-06-24
Can any one please tell me why i get this error
just to test it, when i turn off the firewall i can access SSH, but when i turn it on i cant access SSH, so it must be working what you reckon ?

```
/etc/init.d/firewall restart
Removing all iptables rules:  [End of flush]
Iptables rules creation: iptables: Invalid argument
iptables: Invalid argument
iptables: Invalid argument
iptables: Invalid argument
```

And here is my latest try
later i want to be able to allow access to 25 and 110 for my network only and not the outside, would the email server still send and recive mail  ???

```
/etc/init.d/firewall status
Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
TRUSTED    all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   all  --  anywhere             anywhere            
DROP       all  --  a83-132-97-14.cpe.netcabo.pt  anywhere            
DROP       all  --  81.199.85.110        anywhere            
DROP       all  --  218.16.120.80        anywhere            
DROP       all  --  mx4.url.com.tw       anywhere            
DROP       all  --  218.0.153.219.broad.cq.cq.dynamic.163data.com.cn  anywhere            
DROP       all  --  63-93-95-121.lsan.mdsg-pacwest.com  anywhere            
DROP       all  --  002.011.dsl.syd.iprimus.net.au  anywhere            
DROP       all  --  mail.ala-hawaii.org  anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ftp 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:pop3 
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

TT

---

### Post by keithweddell on 2007-06-24
Sorry for the silence.  I've not been around most of the day.  

Just a general point to start - it's not usually thought to be a good idea to work as root.  It is usually safer to use sudo to gain temporary root privileges.  A bit less convenient but you are less likely to do serious damage.

It looks as though you worked out how to get iptables-restore to work for you.  So now you just need to figure out the iptables rules.

The first point is that you probably want to change the INPUT policy to DROP.  Your firewall will then block everything by default and you have more control over what you allow in.  You seem to have got the hang of rules so start with a simple setup and embellish it later. 

For services that you only want available on your own network you can use something like source = 192.168.1.0/24 (amend to suit your network address).

To test which ports are open, use the Network Tools that you can find by clicking on System /  Administration.  Remember the port won't show up as open unless you have a service (e.g. apache) listening on it.

If you really get stuck, the way I figured it out was by loading Firestarter and looking at the iptables rules that it produces.   They are a bit messy but a good pointer to what you want to achieve.

Hope this helps.


Keith

PS What have you got in the file /etc/init.d/firewall?

---

### Post by tommytomato on 2007-06-24
here it is

```
~# cat /etc/firewall.bash
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

iptables -A INPUT -s 83.132.97.14 -j DROP
iptables -A INPUT -s 81.199.85.110 -j DROP
iptables -A INPUT -s 218.16.120.80 -j DROP 
iptables -A INPUT -s 210.59.228.94 -j DROP 
iptables -A INPUT -s 219.153.0.218 -j DROP 
iptables -A INPUT -s 63.93.95.121 -j DROP 
iptables -A INPUT -s 203.134.154.2 -j DROP 
iptables -A INPUT -s 67.52.65.10 -j DROP 
iptables -A INPUT -i lo -j ACCEPT 
iptables -A INPUT -s 127.0.0.0/255.0.0.0 -j DROP 
iptables -A INPUT -d 127.0.0.0/255.0.0.0 -j DROP
iptables -A INPUT -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -m state --state NEW -j DROP
iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --dport 25 -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --dport 110 -j ACCEPT

```

```
cat /etc/init.d/firewall
#!/bin/bash

RETVAL=0

# To start the firewall
start() {
  echo -n "Iptables rules creation: "
  /etc/firewall.bash
  RETVAL=0
}

# To stop the firewall
stop() {
  echo -n "Removing all iptables rules: "
  /etc/flush_iptables.bash
  RETVAL=0
}

case $1 in
  start)
    start
    ;;
  stop)
    stop
    ;;
  restart)
    stop
    start
    ;;
  status)
    /sbin/iptables -L
    /sbin/iptables -t nat -L
    RETVAL=0
    ;;
  *)
    echo "Usage: firewall {start|stop|restart|status}"
    RETVAL=1
esac

exit

```

I want to be able to open up ports 25 and 110 on my router, but block all access from the outside apart from my localnetwork, can this be done ?

I still want to be able to send and recive from the out side thou:scratch: I hope that makes sence :rolleyes: 

TT

---

### Post by keithweddell on 2007-06-25
We seem to be talking across time zones.  No problem - things might take a little longer thoug.

I think the error from your /etc/init.d/firewall script is caused because the environment variable $PATH is not being read.  You should be able to solve this by amending **/etc/firewall.bash** as follows:

```
#!/bin/bash
PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin

etc ...
```

I still think you should change the INPUT chain policy to DROP so that nothing is allowed in by default and then you can only let in what you want.  Amend /etc/firewall.bash to:
```
iptables -P INPUT DROP
```

I'm not clear on what you are trying to achieve with opening the various ports:

Port 22/80 - SSH and webserver access only from within your own network?  Something like this should work:

```
iptables -s 192.168.1.0/24 -p tcp -m tcp --dport 22 -J ACCEPT
iptables -s 192.168.1.0/24 -p tcp -m tcp --dport 80 -J ACCEPT
```

Port 25/110 - SMTP and POP access from anywhere?  Your rules should be OK.  Have you forwarded these ports from your router?  Make sure you have configured your mail server and pop server securely or you'll be acting as an open relay or something in no time.


Keith

---

### Post by tommytomato on 2007-06-25
Thanks

Here is the out put now

```
~# cat /etc/firewall.bash
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
#iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

iptables -A INPUT -s 83.132.97.14 -j DROP
iptables -A INPUT -s 81.199.85.110 -j DROP
iptables -A INPUT -s 218.16.120.80 -j DROP 
iptables -A INPUT -s 210.59.228.94 -j DROP 
iptables -A INPUT -s 219.153.0.218 -j DROP 
iptables -A INPUT -s 63.93.95.121 -j DROP 
iptables -A INPUT -s 203.134.154.2 -j DROP 
iptables -A INPUT -s 67.52.65.10 -j DROP 
iptables -A INPUT -i lo -j ACCEPT 
iptables -A INPUT -s 127.0.0.0/255.0.0.0 -j DROP 
iptables -A INPUT -d 127.0.0.0/255.0.0.0 -j DROP
iptables -A INPUT -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -m state --state NEW -j DROP
iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
#iptables -s 192.168.1.0/24 -p tcp -m tcp --dport 22 -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --dport 25 -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
#iptables -s 192.168.1.0/24 -p tcp -m tcp --dport 80 -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --dport 110 -j ACCEPT

```

I added this is and it throws up errors on boot

this is what i want, if that's correct, iptables for me is not easy its taking me some time to under stand.

25 -110 to send and recive out side network
22 with in local network all
21 outside and localnetwork
80 outside and localwork


where do i find the start up log to find the error it gave me

TT

---

### Post by keithweddell on 2007-06-25
Start up errors should be in /var/log/dmesg.  You'll probably need to try grep or less to find the right bits.  

Your iptable rules look OK so I'm guessing it's something in the start up script.  I don't use one - got iptables-restore working for me.  Did you try the PATH= ??


Keith

---

### Post by keithweddell on 2007-06-25
I can see I made an error in the iptables rules in my earlier post - the ones you have commented out.  It should of course have been:

```
iptables -A INPUT -s 192.168.1.0/24 -p tcp -m tcp --dport 22 -J ACCEPT
iptables -A INPUT -s 192.168.1.0/24 -p tcp -m tcp --dport 80 -J ACCEPT
```


Keith

---

### Post by tommytomato on 2007-06-25
I see you changed the J to j

The J threw up the error on boot up 

TT

---

