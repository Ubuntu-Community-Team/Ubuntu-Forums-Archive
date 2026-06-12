---
title: "What is preventing nmap from scanning correctly?"
date: 2011-10-07
forum: Security
---

### Post by narnie on 2011-10-07
Hello,

On a single computer on my home lan, I have a setup with client browser -> iptables -> Dansguardian -> Privoxy -> Linksys home hardware router -> Outside internet

The above setup is running perfectly as expected.

If I run as a normal user with the firewall down

```
nmap -sP 192.168.1.0/24
```

I get the expected

```
Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-10-07 14:24 CDT
Nmap scan report for router (192.168.1.1)
Host is up (0.0086s latency).
Nmap scan report for bridge (192.168.1.2)
Host is up (0.0055s latency).
Nmap scan report for dell-desktop (192.168.1.50)
Host is up (0.047s latency).
Nmap scan report for printer (192.168.1.185)
Host is up (0.0057s latency).
Nmap done: 256 IP addresses (4 hosts up) scanned in 3.31 seconds
```

With the following iptable rules:

```
/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -t nat -F
/sbin/iptables -t nat -X
/sbin/iptables -t mangle -F
/sbin/iptables -t mangle -X
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables -P OUTPUT ACCEPT
/sbin/iptables -A OUTPUT -d 127.0.0.1 -p tcp --dport 8118 -m owner ! --uid-owner dansguardian -j DROP
/sbin/iptables -A POSTROUTING -t nat -o lo -p tcp --dport 8080 -j SNAT --to 127.0.0.1
/sbin/iptables -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -j REDIRECT --to-ports 8080
/sbin/iptables -P INPUT DROP
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

## Open port for ssh server (22), web server (80), and mail server (25)
/sbin/iptables -A INPUT -p tcp --dport 50505 -m state --state NEW -j ACCEPT
#/sbin/iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
#/sbin/iptables -A INPUT -p tcp --dport 25 -m state --state NEW -j ACCEPT

## Uncomment below to open NSF port, edit the port accoring actual setting
/sbin/iptables -A INPUT -p tcp --dport 111 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport 111 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 2049 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport 2049 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 4045 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport 4045 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 32771 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport 32771 -m state --state NEW -j ACCEPT
## Open ports for NSF end

#Accept Ping request
/sbin/iptables -A INPUT -p icmp -j ACCEPT

## Drop other packets, Logging, and closing firewall.
/sbin/iptables -A INPUT -d 255.255.255.255/0.0.0.255 -j DROP
/sbin/iptables -A INPUT -d 224.0.0.1 -j DROP
/sbin/iptables -A INPUT -j LOG
/sbin/iptables -A INPUT -j REJECT
```

When I run as a normal user with these iptable rules (running through Dansguardian to privoxy):

```
nmap -sP 192.168.1.0/24
``` 

I get

```
Nmap scan report for router (192.168.1.1)
Host is up (0.00091s latency).
Nmap scan report for bridge (192.168.1.2)
Host is up (0.00071s latency).
Nmap scan report for 192.168.1.3
Host is up (0.00063s latency).
Nmap scan report for 192.168.1.4
Host is up (0.00055s latency).
Nmap scan report for 192.168.1.5
...
Nmap scan report for 192.168.1.250
Host is up (0.00025s latency).
Nmap scan report for 192.168.1.251
Host is up (0.00017s latency).
Nmap scan report for 192.168.1.252
Host is up (0.00024s latency).
Nmap scan report for 192.168.1.253
Host is up (0.00018s latency).
Nmap scan report for 192.168.1.254
Host is up (0.00014s latency).
Nmap done: 256 IP addresses (254 hosts up) scanned in 4.01 seconds
```


Showing all 254 [mostly nonexistent] hosts on the 192.168.1.0/24 as up, which is not correct. Which rule(s) is/are causing that and how can I bypass it?

running as root this:

nmap -sP 192.168.1.0/24

I get 

```
Starting Nmap 5.21 ( http://nmap.org ) at 2011-10-07 14:48 CDT
Nmap scan report for router (192.168.1.1)
Host is up (0.023s latency).
MAC Address: 00:0F:66:44:7F:BC (Cisco-Linksys)
Nmap scan report for bridge (192.168.1.2)
Host is up (0.0045s latency).
MAC Address: 00:11:50:35:4F:86 (Belkin)
Nmap scan report for dell-desktop (192.168.1.50)
Host is up (0.0093s latency).
MAC Address: AA:00:04:00:0A:04 (Digital Equipment)
Nmap scan report for gateway-laptop (192.168.1.64)
Host is up.
Nmap scan report for 192.168.1.100
Host is up (0.043s latency).
MAC Address: C4:17:FE:A5:D5:A9 (Unknown)
Nmap scan report for 192.168.1.103
Host is up (0.045s latency).
MAC Address: 00:21:5D:97:77:A2 (Intel Corporate)
Nmap scan report for 192.168.1.105
Host is up (0.39s latency).
MAC Address: 0C:60:76:46:8A:3C (Hon Hai Precision Ind. Co.)
Nmap scan report for printer (192.168.1.185)
Host is up (0.43s latency).
MAC Address: 18:A9:05:04:DD:61 (Hewlett Packard)
Nmap done: 256 IP addresses (8 hosts up) scanned in 3.89 seconds
```

I know the disparate behaviour is because root is not being routed via the -nat rules, but why as the non-root user is it showing hosts where there are none?

Regards,
Narnie

---

### Post by Dangertux on 2011-10-07
Ok here goes a better answer hopefully this one actually answers the  question. First are you scanning from the machine with the iptables  rules on them? If you are , you have this problem

```

/sbin/iptables -A INPUT -i lo -j ACCEPT

```

Because the scan is technically local, you will get all kinds of weird readings out of nmap, that could be one problem.

The second problem as you pointed out, if you are scanning from the  machine with the rules, since your rules do filter by owner of the  traffic it's going to make them wonky as you can see in your root scan.

However your initial question was why is are all addresses being shown as up. My guess would be this. You're using option -sP which is essentially the same as -sn (-sP is now deprecated in favor of sn) but in any case, it's saying no port scan, so it's only pinging the host to see if it's there.  Traditionally this translates in nmaps default terms to -PE.

I'm thinking that either the presence of RPC portmapper and or the firewall rules themselves are the problem, in conjunction with the fact you are scanning locally.

That being said if you just want to stop ICMP echo then you can add the following to your iptables script

```

echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all 

```

To scan your firewall more effectively you can do something like this

```

sudo nmap -T4 -v -A 

```

or

```

sudo nmap -T4 -v -sS -sV -PN 

```'

or if you really want that ping scan this may be more effective (note if you disable icmp echo request first you will get no response)

```

sudo nmap -T4 -v -PE80:8080 

```

Hope that helps.

---

### Post by narnie on 2011-10-07
> **Dangertux said:**
> I'm not entirely sure what you are doing with the -sP nmap doesn't include documentation on that, as it is deprecated I assume you're trying to do a Ping Scan, however the ICMP-ECHO request is set by default.

Personally if you are trying to test your firewall rules I would do it using this command

```

sudo nmap -T4 -v -sS -PN

```-T4 = fairly agressive timing
-v = verbose output
-sS = syn scan 
-PN = no ping

Alternatively you could do

```

sudo nmap -T4 -v -A 

```Which is mostly the same although it loads a lot of NSE scripts for service detection and OS detection.


Hope that helps, as far as the output from multiple hosts, nmap hit a broadcast address. Firewalls can often screw with nmap's host detection anyway, it's a fickle creature.

If you are trying to drop the response to the echo request entirely you can add the following to your iptables script.

echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all

Wow, Dangertux! You are all over the place and come thru for me again.

Actually, I wasn't doing firewall testing. I have a couple of scripts that I use to see if my kids have their netbooks up (at which point I'll do some maintenance via ssh or install progs I want {in this case Dansguardian/privoxy from my our previous discussions}) and to do the same with the home's desktop computer.

One I wrote uses my local machine's hosts tables to see what is going on:

```
#! /bin/bash
# whatsup script

HOSTS="`cat /etc/hosts|grep -ve ^# -e 127.0.0.1 -e ^$ -e router -e bridge|awk '{print $2}'`"

echo
for i in $HOSTS ; do 
        (ping -c 2 -w 2 $i &> /dev/null
        if [ $? = 0 ] ; then
                echo "$i is up"
        fi) &
done

wait

echo -e "\nDone checking"
```

This is great for known connections that can resolve host names.

Sometimes, I want to check for other things (like their Nintendo DS-I or 3DS or the Wii) and other things I don't have mapped to certain IP numbers. For that, I read a trick somewhere about using

```
nmap -sP 192.168.1.0/24
```

From the man pages it says of this switch:

> 
-sP (Skip port scan) .

This option tells Nmap not to do a port scan after host discovery, and only print out the available hosts that responded to the scan.

This is often known as a “ping scan”, but you can also request that traceroute and NSE host scripts be run. This is by default one
step more intrusive than the list scan, and can often be used for the same purposes. It allows light reconnaissance of a target
network without attracting much attention. Knowing how many hosts are up is more valuable to attackers than the list provided by list
scan of every single IP and host name.

Systems administrators often find this option valuable as well. It can easily be used to count available machines on a network or
monitor server availability. This is often called a ping sweep, and is more reliable than pinging the broadcast address because many
hosts do not reply to broadcast queries.

The -sP option sends an ICMP echo request, TCP SYN to port 443, TCP ACK to port 80, and an ICMP timestamp request by default. When
executed by an unprivileged user, only SYN packets are sent (using a connect call) to ports 80 and 443 on the target. When a
privileged user tries to scan targets on a local ethernet network, ARP requests are used unless --send-ip was specified. The -sP
option can be combined with any of the discovery probe types (the -P* options, excluding -PN) for greater flexibility. If any of those
probe type and port number options are used, the default probes are overridden. When strict firewalls are in place between the source
host running Nmap and the target network, using those advanced techniques is recommended. Otherwise hosts could be missed when the
firewall drops probes or their responses.

This script I wrote is simpler:

> #! /bin/bash
# whatsup_nmap script

IP=${1:-192.168.1.0/24}

nmap -sP $IP

I should have included the 192.168.1.0/24 on the above, I will edit it to change that.

Just the second script will try to find out what hosts are actually up by running through all possible 256 host locations.

I understand from you post that nmaps can be dodgy with firewalls, so I'll just disable when I'm doing this unless there is a way to punch nmap requests such as this through the firewall.

Thanks for the info, as always, Adam!

Regards,
Narnie

---

### Post by narnie on 2011-10-07
On looking at that again, perhaps I could use a rule that allows input of SYN on port 443 from -s 192.168.1.0/24. I'll try when I get a chance and see what happens.

Cheerio,
Narnie

---

### Post by Dangertux on 2011-10-07
Ok one more edit than I'm thinking it'll work out lol

If you want to detect if there hosts are up even with your firewall script you can do something along these lines (since some of those devices will drop icmp echo) This would probably be more effective.

```

sudo nmap -T4 -v -sS 192.168.0.0/24

```or 

```

sudo nmap -T4 -v -sT 192.168.0.0/24

```(this might be more effective) for the wii and stuff like that.

Hope all this was helpful , sorry I wasn't so on point today with my response it feels very much friday lol :-P

Have a great weekend!

---

### Post by narnie on 2011-10-07
> **Dangertux said:**
> Ok one more edit than I'm thinking it'll work out lol

If you want to detect if there hosts are up even with your firewall script you can do something along these lines (since some of those devices will drop icmp echo) This would probably be more effective.

```

sudo nmap -T4 -v -sS 192.168.0.0/24

```or 

```

sudo nmap -T4 -v -sT 192.168.0.0/24

```(this might be more effective) for the wii and stuff like that.

Hope all this was helpful , sorry I wasn't so on point today with my response it feels very much friday lol :-P

Have a great weekend!

Adam,

I don't know what you mean!?!? You first post that you ended up changes WAS helpful to me, because it taught me some things I didn't know. Please, no apologies! Your second post was even better!, then your last even better.

You are very kind in helping people as you do, and I can tell you are serious about it.

The first and second ways you showed resulted in it taking over a minute to get an answer vs seconds for the way I was doing it. They also showed all hosts were down (which is not the case). I seem to remember reading about the -sP option (which I need to change to -sn because I don't like using depreciated techniques) is quick, down, and dirty, but for more thorough testing, what you supplied is best. I'm wanting just quick checks. It will likely be quicker to just clear the rules and restart them after I do my rapid scan.

Regardless, those tricks you gave me will propel me to read those sections of nmap's man pages to better understand what they are doing.

As always, thanks much and have a great weekend!

Warmly,
Narnie

---

### Post by Dangertux on 2011-10-07
Thanks! You too :-)

Regards,
Adam

---

