---
title: "Firewall and LAN"
date: 2009-11-23
forum: Ubuntu Christian Edition
---

### Post by yedidyah on 2009-11-23
My main problem is I cannot (and do not know how) to set up my LAN with Ubuntu CE's firewall. Even when I shutdown the firewall the LAN is inconsistent. Other computers cannot print or access my computer on the LAN and complain of an enabled firewall.

In responding to this post please do not assume I automatically know how to "punch a hole in the firewall" for the LAN. If you say that to me I will have no idea where to start (typical of noobs).

Thank you for your help.

---

### Post by david_kt on 2009-11-23
> **yedidyah said:**
> My main problem is I cannot (and do not know how) to set up my LAN with Ubuntu CE's firewall. Even when I shutdown the firewall the LAN is inconsistent. Other computers cannot print or access my computer on the LAN and complain of an enabled firewall.

In responding to this post please do not assume I automatically know how to "punch a hole in the firewall" for the LAN. If you say that to me I will have no idea where to start (typical of noobs).

Thank you for your help.

First, please let us know your configuration:
- How many computers on LAN and what is the operating system
- How they get IP address
- what services you have on the LAN (printing, file server) and attached to which computer/server

DK

---

### Post by yedidyah on 2009-11-24
Thank you for your response. 

- There is (currently) only one other computer on the LAN and it is currently Kubuntu Hardy Heron (a guest laptop comes and goes that runs XP). But if CE works out I am going to put 9.04 CE on it too and give a donation to the UCE.
- I have the LAN set up for static IP (to keep the Wii from screwing up the printing configuration).
- The UCE computer is the host for the LAN printer and they (UCE and Kubuntu) both share files with each other.
- Also we are using Samba between the computers.

---

### Post by david_kt on 2009-11-24
> **yedidyah said:**
> Thank you for your response. 

- There is (currently) only one other computer on the LAN and it is currently Kubuntu Hardy Heron (a guest laptop comes and goes that runs XP). But if CE works out I am going to put 9.04 CE on it too and give a donation to the UCE.
- I have the LAN set up for static IP (to keep the Wii from screwing up the printing configuration).
- The UCE computer is the host for the LAN printer and they (UCE and Kubuntu) both share files with each other.
- Also we are using Samba between the computers.

For samba sharing, you have to stop ubuntu ce firewall as I have not figure out which ports to open for samba:

```
sudo /etc/init.d/ubuntu_ce_firewall stop
```

How do you share printer? Do you use samba as well? As from my experience, it is better to use IPP (internet printing protocol), it works very well among ubuntu as well as with windows XP.

And how many network cards does the UCE have? One or two? 

DK

---

### Post by yedidyah on 2009-11-25
Is there no information anywhere on how to control the firewall program so as to use Samba (I find that somewhat troubling). 

Okay I will switch to the ipp for printing instead of samba (that is if I can figure it out).

I do not know how many network cards this computer has, how do you tell?

---

### Post by poohman on 2009-11-25
Do a lspci to find the number of network cards.
Open terminal
lspci

---

### Post by david_kt on 2009-11-25
> **yedidyah said:**
> Is there no information anywhere on how to control the firewall program so as to use Samba (I find that somewhat troubling). 

Okay I will switch to the ipp for printing instead of samba (that is if I can figure it out).

I do not know how many network cards this computer has, how do you tell?

Yes, there are instructions to open ports for samba, i.e. 137, 138, 139, and 445. I have not tried it out. Once I managed to run samba with firewall, I will include this option in dansguardian-gui.

How many network cable connected to the UCE? If you have one network cable connected to internet, and another one connected to LAN, that would be the best to protect your LAN.

DK

---

### Post by jacobs444 on 2009-11-25
are you behind a router? If you are then you do not need the firewall enabled.

---

### Post by samden on 2009-11-25
> **jacobs444 said:**
> are you behind a router? If you are then you do not need the firewall enabled.
Doesn't that depend on whether your router has a firewall?

---

### Post by yedidyah on 2009-11-25
lspci
seems there is only one ethernet card (controller).


My computer connects to a router (with other computers) and the router connects to the modem.

where would I find the instructions for opening the ports for samba?

---

### Post by david_kt on 2009-11-25
> **yedidyah said:**
> lspci
seems there is only one ethernet card (controller).


My computer connects to a router (with other computers) and the router connects to the modem.

where would I find the instructions for opening the ports for samba?

Please try below steps and please report if it is working/not working:
```

gksudo gedit /etc/init.d/ubuntu_ce_firewall
```

Copy and paste below after the line:
## Open ports for NSF end

```
## Open ports for samba start

iptables -A INPUT -p tcp --dport 137 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 137 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 138 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 138 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 139 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 139 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 445 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 445 -m state --state NEW -j ACCEPT

## Open ports for samba end 
```

save and close it, and then

```
sudo /etc/init.d/ubuntu_ce_firewall restart
```

Hopefully samba will work after that.

DK

---

### Post by yedidyah on 2009-11-27
Thank you so much for your information david_kt.
I attempted to do what you instructed but the line:

## Open ports for NSF end

is not in the /etc/init.d/ubuntu_ce_firewall file
I would have gone ahead and added the code you published but I didn't know if it had to be in a particular spot or not. 

Here is the actual contents of the file (again thank you):

#!/bin/bash
### BEGIN INIT INFO
# Provides:          ubuntu_ce_firewall
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: firewall
# Description:       Start, stop or reload firewall.
### END INIT INFO

set -e

case "$1" in
  start)
    echo -e "\nStarting Ubuntu CE firewall .....\n"

/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -t nat -F
/sbin/iptables -t nat -X
/sbin/iptables -t mangle -F
/sbin/iptables -t mangle -X
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables -P OUTPUT ACCEPT
iptables -A POSTROUTING -t nat -o lo -p tcp --dport 8080 -j SNAT --to 127.0.0.1
iptables -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -j REDIRECT --to-ports 8080
/sbin/iptables -P INPUT DROP
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 25 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p icmp -j ACCEPT
/sbin/iptables -A INPUT -d 255.255.255.255/0.0.0.255 -j DROP
/sbin/iptables -A INPUT -d 224.0.0.1 -j DROP
/sbin/iptables -A INPUT -j LOG
/sbin/iptables -A INPUT -j REJECT
	;;

  stop)
   echo -e "\nFlushing firewall and setting default policies to ACCEPT\n"

	/sbin/iptables -F
	/sbin/iptables -X
	/sbin/iptables -t nat -F
	/sbin/iptables -t nat -X
	/sbin/iptables -t mangle -F
	/sbin/iptables -t mangle -X
	/sbin/iptables -P INPUT ACCEPT
	/sbin/iptables -P FORWARD ACCEPT
	/sbin/iptables -P OUTPUT ACCEPT
	;;

  status)
        /sbin/iptables -L
	;;

  restart|force-reload)
	$0 stop
	$0 start
;;
  *)
        echo "Usage: /etc/init.d/ubuntu_ce_firewall {start|stop|restart|force-reload|status}"

        exit 1
	;;
esac

---

### Post by david_kt on 2009-11-27
> **yedidyah said:**
> 
## Open ports for NSF end

is not in the /etc/init.d/ubuntu_ce_firewall file
I would have gone ahead and added the code you published but I didn't know if it had to be in a particular spot or not. 

Then you could put it after 

/sbin/iptables -P INPUT DROP

DK

---

### Post by yedidyah on 2009-12-04
david_kt

Okay I just wanted to let you know that your solution worked. Thank you for your help I am VERY grateful!

---

### Post by yedidyah on 2009-12-27
New development.

I upgraded to 9.10 and wrestled for days trying to configure the LAN so computers would share stuff. Ultimately I uninstalled dansguardian and now the network works without any problems.

---

### Post by yedidyah on 2010-01-03
I found some other information that was posted concerning the firewall. 

I wanted to keep Ubuntu CE so that it updates properly so I reinstalled ubuntu-ce through synaptic (which also reinstalled dansguardian) and did the following command after the reinstallation:


sudo update-rc.d -f ubuntu_ce_firewall remove


This is what I needed to establish the LAN and keep everything good.

Now I will continue to test UCE and if it looks like it is going to remain stable and take care of my needs then I will help contribute to UCE.

I appreciate your work thank you.

---

