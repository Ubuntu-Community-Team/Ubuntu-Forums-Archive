---
title: "A Simple Mail Server"
date: 2008-01-07
forum: Server Platforms
---

### Post by Dr Small on 2008-01-07
Supposing I want to setup a simple mailserver on Ubuntu, that can send and receive mail with email addresses like user@IP and user1@IP with Webmail access, what would be the best route to take to set this up?

I have 0 experience with mail servers, so that is why I am asking for advice as to what to use.

IP will be my external IP.

Any suggestions?
Dr Small

---

### Post by reckless2k2 on 2008-01-07
2,215 posts and you are asking for help. hahaha. i would think you're ninja with that many posts.

i used postfix and squirrelmail WAY back in the day to achieve this. it wasn't hard to do but it was a lot of terminal tweak and setup. i use zimbra now which is incredibly easy to install and it's full collaboration with email, calendar, etc....and a nice GUI. here is some setup on postfix and squirrelmail is in the other link i think. user docs is great. i'll give you 2 resources:

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

that link is like simple postfix setup. 

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

search on postfix and such that link and you are good. 

zimbra info can be found here:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

you can go right to zimbra as well. 

postfix and squirrelmail use VERY little resources compared to zimbra. you decide.

---

### Post by Dr Small on 2008-01-07
[quote=reckless2k2]2,215 posts and you are asking for help. hahaha. i would think you're ninja with that many post[/quote]
Posts count general doesn't mean a whole lot. I normally answer questions in the ABT, so that's why I have such a big post count :p But mailservers have never been in my knowledge.

Thanks for the links, I check them out. :D

Edit, Question. On the zimbra page, it says:
> I will use the hostname mail.example.com in this tutorial together with the IP address 192.168.0.110. Adjust this to your needs, but make sure that mail.example.com has a valid MX record in DNS (Zimbra needs this!).

I don't know what MX's are, and I'm not going to have a domain, but simply my external IP. Will this still work?

Dr Small

---

### Post by HermanAB on 2008-01-08
Zimbra or Citadel can be configured in minutes.  Anything else will take weeks to set up.  

My personal favourite is Citadel: [http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

Cheers,

Herman

---

### Post by reckless2k2 on 2008-01-08
a mailserver for external purposes is going to require a real world domain name that can resolve back to your host/machine. i paid for a domain along with DDNS (allows for DHCP IPs to resolve to a Domain name). 

in other words, your ISP has probably got you setup with an IP that may change after "x" amount of time. therefore, your mailserver will not longer work. some people just get free domain names that will resolve back. i never bothered with it but i think dyndns, godaddy, and no-ip all offer this. i think ddns is going to cost you no matter what. i paid like $25 a year for 5 or something year's in advance a few years ago for a domain and ddns. i think it's somewhere around $32 now a year. i know there are free solutions though at those places. 

again, you will need something to resolve back to the mailserver other than a changing IP address.

---

### Post by Dr Small on 2008-03-31
There ain't no sense starting a new thread, since my problem is sorta Mailserver'ish.

Right now I am trying to open port 25 on my server.
Firestarter says it is open, nmap says otherwise:
```
drsmall@darkghost:~$ nmap -P0 192.168.0.70

Starting Nmap 4.20 ( http://insecure.org ) at 2008-03-31 14:01 EDT
Interesting ports on mycroft (192.168.0.70):
Not shown: 1688 filtered ports
PORT      STATE  SERVICE
21/tcp    open   ftp
22/tcp    open   ssh
**25/tcp    closed smtp**
53/tcp    open   domain
79/tcp    open   finger
80/tcp    open   http
888/tcp   closed accessbuilder
8080/tcp  closed http-proxy
10000/tcp open   snet-sensor-mgmt

Nmap finished: 1 IP address (1 host up) scanned in 28.173 seconds
```

Iptables says it is open too, I guess:
```
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:25 

```

So why can't I get it to open properly?
I need to be able to send mail from without to the local mailserver!

I keep getting:
```
connect to mycroftserver.homelinux.org[70.41.142.144]: Connection refused
```

Dr Small

---

### Post by HermanAB on 2008-03-31
The port is 'open', but there is nothing listening on it.

In other words, your SMTP server is not running.

---

### Post by Dr Small on 2008-03-31
Hmm, well that is definately strange then.
Postfix is running, and I can send mail to hackermail with it.

Also:
```
drsmall@mycroft:~$ ps aux | grep postfix
postfix   3562  0.0  0.2   4996  1632 ?        S    10:10   0:00 qmgr -l -t fifo -u
postfix  14030  0.0  0.1   4956  1496 ?        S    15:04   0:00 pickup -l -t fifo -u -c
postfix  14142  0.0  0.1   4960  1548 ?        S    15:06   0:00 showq -t unix -u -c
drsmall  14159  0.0  0.0   2880   748 pts/0    R+   15:06   0:00 grep postfix
root     22633  0.0  0.2   4948  1568 ?        Ss   Mar25   0:01 /usr/lib/postfix/master

```


I still believe it is a firewall problem, so I ditched Firestarter and am using this script from this thread:
[http://ubuntuforums.org/showpost.php?p=2894882&postcount=4](http://ubuntuforums.org/showpost.php?p=2894882&postcount=4)

Only, I changed mine:
```

#!/bin/sh
# /etc/init.d/firewall
# from http://wiki.linuxquestions.org/wiki/A_basic_firewall_configuration_suitable_for_a_workstation

set -e

iptables="/sbin/iptables"
modprobe="/sbin/modprobe"

load () {

 echo "Loading kernel modules..."
 $modprobe ip_tables
 $modprobe ip_conntrack
 $modprobe iptable_filter
 $modprobe ipt_state
 $modprobe iptable_nat
 echo "Kernel modules loaded."

 echo "Loading rules..."
 $iptables -P FORWARD DROP
 $iptables -P INPUT DROP

##### PORTS #####
# comment out the ones you don't need

### ftp
$iptables -A INPUT -p tcp -m tcp --destination-port 21 -j ACCEPT

### ssh
$iptables -A INPUT -p tcp -m tcp --destination-port 22 -j ACCEPT

### http
$iptables -A INPUT -p tcp -m tcp --destination-port 80 -j ACCEPT

### Webmin
$iptables -A INPUT -p tcp -m tcp --destination-port 10000 -j ACCEPT
$iptables -A INPUT -p tcp -m tcp --destination-port 20000 -j ACCEPT

#HTTPS
$iptables -A INPUT -p tcp -m tcp --destination-port 443 -j ACCEPT

###SMTP
$iptables -A INPUT -p tcp -m tcp --destination-port 25 -j ACCEPT

### Finger
$iptables -A INPUT -p tcp -m tcp --destination-port 79 -j ACCEPT

###DNS
$iptables -A INPUT -p tcp -m tcp --destination-port 53 -j ACCEPT

### NetBIOS (Windows Networking, Samba)
#$iptables -A INPUT -i eth1 --protocol tcp --dport 137 -j ACCEPT
#$iptables -A INPUT -i eth1 --protocol tcp --dport 139 -j ACCEPT

### for Duelle: World of Warcraft
#$iptables -A INPUT -p tcp -m tcp --destination-port 6112:6119 -j ACCEPT

### for Duelle:  Bittorrent
#$iptables -A INPUT -p tcp -m tcp --destination-port 49200 -j ACCEPT


##### BLOCK OUT INTRUSION #####
$iptables -A INPUT -i ath0 -m state --state NEW,INVALID -j DROP
$iptables -A FORWARD -i ath0 -m state --state NEW,INVALID -j DROP


###### DEFAULTS #####
 $iptables -A INPUT -p ALL -m state --state ESTABLISHED,RELATED -j ACCEPT
 $iptables -A INPUT -s 127.0.0.1 -j ACCEPT
 echo "Rules loaded."

}

flush () {

 echo "Flushing rules..." $iptables -P FORWARD ACCEPT
 $iptables -F INPUT
 $iptables -P INPUT ACCEPT
 echo "Rules flushed."

}

case "$1" in

 start|restart)
   flush
   load
   ;;
 stop)
   flush
   ;;
 *)
   echo "usage: start|stop|restart."
   ;;

esac
exit 0

```

Ran it, but there still seems to be no difference. This is really getting mind boggling, and I am beginning to lose my patience with it, since I have been trying everything all morning long.

Dr Small

---

### Post by Poleh on 2008-03-31
> **HermanAB said:**
> Zimbra or Citadel can be configured in minutes.  Anything else will take weeks to set up.  

My personal favourite is Citadel: [http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

Cheers,

Herman

Agreed, I have just followed the how-to-forge link for Ubuntu 7.10 earlier, and while it is quite comprehensive it's not complete. It's taken me about a month of figuring out to get my "simple" mail server working. Although, now that it IS working, it's SWEET!

Citadel is the way to go for you I think. I had it running in 5 minutes ...

---

### Post by Dr Small on 2008-03-31
I had Citdel, but really didn't like it's interface that well.
But this problem should not be that hard. All I need to do is get port 25 open, or something.

I have tried flushing iptables, starting the firewall script, restarting postfix... You name it. I keep getting a connection refused in the mail queue though.

---

### Post by Dr Small on 2008-03-31
I finally got Postfix working properly, so I can send and receive mail on the server!
Well, next question.

How can I (is it even possible?) setup an account in Evolution (per say) to download all of my emails and send via the server? To download, I think it requires a POP server, and all of this is beginning to get over my head.

How would I be able to do this?

Dr Small

---

### Post by ambre on 2008-04-01
Hi Doc,

I used [_this link_]("http://www.howtoforge.org/perfect_server_ubuntu7.10") to set up my server.  It does a lot more than you (or I) require, but with a little tweaking it does what it says on the box and you will have a working e-mail server.

With the addition of 'fetchmail', run through cron, I collect all the household e-mail from four different ISP's at regular intervals throughout the day, store them on the Ubuntu box in readiness for the users to collect when they switch on their WINXP boxes.  All out-going mail is relayed through one of the ISP's.  I had to do it this way because some mail was being bounced by the receiver not being able to resolve the senders MX record.

Fred
PS Don't dispare, I started from the same point as you.  (I must get out more!)

---

### Post by alby69 on 2008-04-01
I used [Desknow]("http://www.desknow.com/") mailserver in Windows server, but it's in Java so no problem in Linux....

It's really an incredible software....

Mail Server and Collaboration software

I'm using since 2 years without problems...
It's not free, but licences are very cheap...

hope this helps!

---

### Post by ryazkhan on 2008-04-01
I read your post and it looks good. I want to configure zimba as mailserver for my setup so please help me. I dont have ldap configured, i want to use samba password for authentication. I have Ubuntu 7.10 Server edition and waiting to update with 8.04 LTS. Can you help me with this by showing me exact codes or command to put because I already tried several time with no luck so please................

---

