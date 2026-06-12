---
title: "Help required configuring IPTables in Hardy"
date: 2012-02-04
forum: Security
---

### Post by hatrack on 2012-02-04
I am an OAP and some years ago, I got fed up with Windows and so I set up a dual boot Linux/Windows system (Ver 8.04 (Hardy)/WinXP). Linux is used for Office applications and all connections to the outside world. The WinXp environment is only ever used (for reasons of compatibility with some legacy H-ware) for image processing in connection with my hobby of photography. This overall configuration has proved very stable and satisfies all my needs. Up until now, I have followed the common assumption that Linux is pretty-well immune to outside attack but it is clear that this happy situation cannot last indefinitely and so I wish to tighten up my firewall. 

I run ThunderBird for e-mail and Firefox for web searching; both have been up-graded to Ver 9.0.1. FireFox is used for searching, banking and web purchases and has been enhanced with the addition of NoScript, AdBlock, Ghostery, BetterPrivacy and WOT. What I would like to do is to restrict traffic access so far as is practical so that would mean (I guess)... Mail, In and Out for ThunderBird (pop3 and smtp) and both http and https Web sites for FireFox. I have tested things using the Gibson Research Web site and I find that my system is also accepting a "ping" (despite my best efforts with FireStarter to filter ICMP !). I have recently learned that FireStarter is incompatible with current version of Linux, so this has now been de-installed

I have searched through the pages here on this forum for advice but (quite frankly) I am lost in the mass of information and so I badly need some help and advice as to how best to edit IPTables so that the necessary rules run from boot-up. Can anyone please provide a simple script to enter from a terminal which will satisfy these requirements and (perhaps) comment on any other enhancements that I should consider. My thanks and Best Regards to all ...

---

### Post by cryptotheslow on 2012-02-04
Firstly a comment - Ubuntu 8.04 has been end of life for a fair while now, so will not be receiving any updates - unless you have specifically set up backports of everything. Probably time to be considering an upgrade.

As for firewall management - UFW (Uncomplicated FireWall) is fairly easy to use.

From a terminal:
```
ufw --help
```

Will get you started.

```
man ufw
``` will give a more in depth summary of the usage.

Alternatively see the manpage online here:
[http://manpages.ubuntu.com/cgi-bin/search.py?q=ufw](http://manpages.ubuntu.com/cgi-bin/search.py?q=ufw)


There is also a graphical interface for ufw called gufw which you should find in the repositories for installation.

As an aside - how are you connected to the internet? It could be your ISP router / modem responding to the ping rather than your PC.

As a further aside - unless you have purposefully set something up, by default Ubuntu has no listening ports open.

This command:
```
sudo netstat -ptvnl
```

will give you a list of currently listening ports and the processes doing so.

Hope that helps some.

---

### Post by hatrack on 2012-02-04
I thank you very much for your quick reply. I have now installed ufw and used gufw to look at this. With the aid of the "Help" file, I think that I can understand this. I plan to initially set all access to "Deny" and then create "Accept" rules as follows -

For DHCP                 -- Ports 67 & 68  -- Protocol = UDP
For Web Access        -- Ports 80 & 443 -- Protocol = TCP (Used for http & https)
For Email Access       -- Port 995      -- Protocol = TCP (Used for secure pop3 under T-Bird)        
For Email Access       -- Port 465      -- Protocol = TCP (Used for secure smtp under T-bird)     
For DNS Access         -- Port  53      -- Protocol = TCP & UDP

I think that that will cover my simple needs for just Email and Web, though I welcome any comments you would like to make ... I'm very much a "Newbie" in this field, so I'm feeling my way slowly.

Moving on ... I ran netstat as you suggested and got -- 

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4967/cupsd      
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      5223/exim4 

I guess that the numbers shown after the colon in the Local Address are Port Numbers ? I know that "cups" deals with printers and that "exim4" is a mail-handler, so this makes sense ... I have a printer hooked up to my router and I would expect Linux to be listening for incoming mail. The Gibson Research site seems to support my guess and shows Ports 25 and 631 to be in "Stealth" mode. Since I connect to the world via BroadBand, I guess your suggestion that it my ISP that is answering a "Ping" is probably correct and so I need not worry further on that score.

Turning now to your initial comment that Hardy is "life-expired", I am aware of this but ... I'm loath to up-grade. I did this once before (for Jaunty, I think) and turned my system into a complete "dog's breakfast" which took a week to sort out ! The problem arose (I think) because I have a dual-boot system. So ... although the Ubuntu up-grade installer worked perfectly, Windows just does not "play nicely" with any other OS. When I initially set up my system, I installed WinXP first and then used Hardy to "smack it about the ears" until it behaved properly. Trying to up-grade means that (in effect) I'm installing Ubuntu AFTER WinXP, which lead to disaster and ended up as a "Format C:" job ... re-install WinXP and start from scratch ! Until such times as Hardy will no longer do all I require, I think I'll "leave well alone" although again, I'd appreciate any comments,

I repeat my thanks for your speedy help and will report probably late tonight/tomorrow when I've got things sorted.  Best regards ...

---

### Post by Bucky Ball on 2012-02-04
As mentioned, 8.04 LTS not supported (and that includes security updates). In software sources you can set it to get notified about long-term support releases (LTS) only. Then it is a click and a couple of hours wait and you will be using 10.04 LTS which is supported until April 2013. You could of course wait until April this year for 12.04 LTS which is supported for five years but that would be a fresh install I would think (unless you can skip an LTS release and go straight from 8.04 LTS to 12.04 LTS). 

Be aware though that 12.04 has some radical changes, most notably the replacement of Gnome with Unity as the default desktop environment.

Just thought I'd say. Good luck with it all ... ;)

---

### Post by hatrack on 2012-02-04
To Bucky Ball,

Thank you for for your comment re up-grading. As I pointed out in my earlier reply, the snag for me is that up-grading to anything will probably open a real can of worms (I think) because I have a dual boot system. Now ... I _**can**_ completely re-install my whole system ... WinXP, all the drivers for my H-ware, Image Proc S/W, etc. ... _**plus**_ doing the up-grade and re-installing all the stuff I use with Ubuntu but this isn't a job I want to take on lightly. (I did it several times getting my original setup organised and about twice more, after the kerfuffle with the attempted up-grade) so I know it's a real pain !

Hardy does everything I want just fine and most of the new features in the new releases are of no interest whatsoever. However, I _**am**_ concerned about what you say regarding the security up-dates. Can you please offer any comments (or guesses :)) as to the scale of the security risk I will be exposed to if I continue to run Hardy on into the indefinite future but with a good firewall set-up ?

Many thanks and Best regards ...

---

### Post by Ms. Daisy on 2012-02-04
You can read the basic security wiki (in my signature) regarding updating your OS, it's one of the basic tenets of security. If you use an EOL OS but set up the firewall, it's kind of like putting a few extra deadbolts on the front door while leaving the windows open.  

I have a dual boot Win 7/ Ubuntu computer. I attempted to upgrade 11.04 to 11.10 and suffered epic failure.  But it was simple to delete the hosed Ubuntu partitions with gparted & reinstall 11.10.  Of course it's important to have good backups of the Win and Ubuntu data before you attempt any upgrade.  It's not that bad. You just have to do ample research before hand. I can't remember which guide I followed but I found it through ubuntu forums.

---

### Post by Bucky Ball on 2012-02-04
You don't need to touch XP or whatever Win you may have installed. When installing Ubuntu, go for manual partitioning when you get to that bit, kill the Ubuntu partitions (or just leave them ticked to reformat) and leave the Win partitions (NTFS rather than EXT* filesystem) alone. They will be untouched and picked up by the new Ubuntu install.

You don't need to reinstall Win to reinstall Ubuntu. ;)

---

### Post by kevdog on 2012-02-04
Let's not stray too far off this guy's request.  He needs help with the firewall -- either straight out iptables nomenclature or help with a front end such as ufw.  I don't really care if he stays on Hardy or upgrades, his problem is going to be the same -- no matter what. 

The best advice I can give to you is to read up on IPTables.  Yes its a very boring subject, but it will give you what you want.  

As far as basic services (I'm not too sure what you mean by that), I'll give you a skeleton script that will at least get you started.  The forwarding chain and NAT redirection likely not needed.

#!/bin/bash

IPTABLES=/sbin/iptables
IP6TABLES=/sbin/ip6tables
MODPROBE=/sbin/modprobe
INT_NET=<INTERNAL LAND IP SUBNET ie 192.0.1.0/24>

### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

### this policy does not handle IPv6 traffic except to drop it.
#
echo "[+] Disabling IPv6 traffic..."
$IP6TABLES -P INPUT DROP
$IP6TABLES -P OUTPUT DROP
$IP6TABLES -P FORWARD DROP

### load connection-tracking modules
#
$MODPROBE ip_conntrack
$MODPROBE iptable_nat
$MODPROBE ip_conntrack_ftp
$MODPROBE ip_nat_ftp

###### INPUT chain ######
#
echo "[+] Setting up INPUT chain..."

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
$IPTABLES -A INPUT ! -s $INT_NET -j LOG --log-prefix "SPOOFED PKT "
$IPTABLES -A INPUT ! -s $INT_NET -j DROP

### ACCEPT rules
##Accept SSH connections explicitly from LAN area IP's, the rest are dropped
$IPTABLES -A INPUT -p tcp -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
##Ping Requests
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

### default INPUT LOG rule
$IPTABLES -A INPUT ! -i lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

### make sure that loopback traffic is accepted
$IPTABLES -A INPUT -i lo -j ACCEPT

###### OUTPUT chain ######
#
echo "[+] Setting up OUTPUT chain..."

### state tracking rules
$IPTABLES -A OUTPUT -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules for allowing connections out (Basic outbound ports)
#Port 21 - telnet
#Port 22 - ssh
#Port 25 - POP
#Port 43 - WhoIs
#Port 80 - HTTP
#Port 443 - HTTPS
#Port 4321 - Referral Whois
#Port 53 - DHCP
$IPTABLES -A OUTPUT -p tcp --dport 21 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 25 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 43 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 4321 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

### default OUTPUT LOG rule
$IPTABLES -A OUTPUT ! -o lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

### make sure that loopback traffic is accepted
$IPTABLES -A OUTPUT -o lo -j ACCEPT

###### FORWARD chain ######
#
echo "[+] Setting up FORWARD chain..."

### state tracking rules
$IPTABLES -A FORWARD -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A FORWARD -m state --state INVALID -j DROP
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
$IPTABLES -A FORWARD ! -s $INT_NET -j LOG --log-prefix "SPOOFED PKT "
$IPTABLES -A FORWARD ! -s $INT_NET -j DROP

### ACCEPT rules
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 21 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 25 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 43 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 4321 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp --dport 53 -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p udp --dport 53 -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT

### default LOG rule
$IPTABLES -A FORWARD ! -i lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

###### NAT rules ######
#
echo "[+] Setting up NAT rules..."
#$IPTABLES -t nat -A PREROUTING -p tcp --dport 80 -i eth0 -j DNAT --to 192.168.10.3:80
#$IPTABLES -t nat -A PREROUTING -p tcp --dport 443 -i eth0 -j DNAT --to 192.168.10.3:443
#$IPTABLES -t nat -A PREROUTING -p udp --dport 53 -i eth0 -j DNAT --to 192.168.10.4:53
#$IPTABLES -t nat -A POSTROUTING -s $INT_NET -o eth0 -j MASQUERADE

###### forwarding ######
#
echo "[+] Enabling IP forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward

exit
### EOF ###

---

### Post by Bucky Ball on 2012-02-05
> **kevdog said:**
> Let's not stray too far off this guy's request. 

OP not necessarily a 'guy'. Maybe just OP ... ;)

---

### Post by hatrack on 2012-02-05
I thank all you kind people for the very helpful advice you have provided. 

As mentioned in my reply to Cryptotheslow, I have now downloaded and installed ufw & gufw and then set up Access Permissions as I described there. I have spent most of today testing this with just about everything that I do routinely with email and on the Web. All appears to work perfectly.

Moving on the the vexed question as to whether or not to up-grade from Hardy, my feeling today is to still stay with this. I thank Ms Daisy for the wiki on security (See [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)). After reading this, I am pleased to report that I was doing all that it recommends (except for the firewall config.). 

I have reviewed the information on the available new releases but find that I don't really like any of them and most certainly, wont be using any of the new features. In addition, the replacement of Gnome by Unity will be an annoyance because I do not use most of the features of Compiz now so, all the "Gee-Whizz" aspects of configuring my Desktop will be switched off (my present one is very uncluttered, is set for good contrast with a solid-colour background and has all the animations switched off). It looks like a very early version of OS/2 which I used extensively in the early 90s. This is not because I am an old Fuddy-Duddy (although at 78 yrs old, I am !) but because I have macular degeneration and am waiting to go into hospital later this year to have cataracts in both eyes fixed. Image Contrast, clean, simple fonts and an un-cluttered layout, are important when you no longer have the 20/20 vision of youth.

In short, therefore, I would be up-grading just for the security features but (having reviewed my work-practices) I think the security risks are minimal and have been reduced now that the firewall is configured. 

Very best regards to you all ...

---

