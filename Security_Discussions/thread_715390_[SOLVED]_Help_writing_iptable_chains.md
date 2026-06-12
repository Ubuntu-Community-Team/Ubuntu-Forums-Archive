---
title: "[SOLVED] Help writing iptable chains"
date: 2008-03-04
forum: Security Discussions
---

### Post by tad1073 on 2008-03-04
I need some help writing iptable chains. i have looked through the man pages but i don't understand it. I want my request sent to where they are supposed to go, I ant to receive replies from where they are supposed to be from, I want to be able to use my network printer, access my xp machine from ubuntu and access ubuntu from xp. i have tried firestarter but it is too restrictive for my network.

i don't know the technical jargon for this question,(I want my request sent to where they are supposed to go, I ant to receive replies from where they are supposed to be from) so i hope whoever understands what I am aking.

---

### Post by tad1073 on 2008-03-04
bump...

---

### Post by Matt Yun on 2008-03-04
First, open the gedit text editor as root.  To do this, run the Terminal program from Accessories, then type:

**$ gksudo gedit /etc/init.d/firewall**

Cut and paste the following code into the text editor, then save and close:

```
#!/bin/sh
# /etc/init.d/firewall
# based on  http://wiki.linuxquestions.org/wiki/A_basic_firewall_configuration_suitable_for_a_workstation

set -e

iptables="/sbin/iptables"
modprobe="/sbin/modprobe"

load () {

 echo "Loading kernel modules..."
 $modprobe ip_tables
 $modprobe ip_conntrack
 $modprobe iptable_filter
 $modprobe ipt_state
 echo "Kernel modules loaded."

 echo "Loading rules..."
 $iptables -P FORWARD DROP
 $iptables -P INPUT DROP

##### MASQUERADING ######

# enable masquerading to allow LAN internet access
# $iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# forward LAN traffic from eth1 to eth0 internet interface for e-mail
# $iptables -A FORWARD -i eth1 -o eth0 -m state --state NEW,ESTABLISHED -j ACCEPT

##### PORTS #####
# just uncomment the iptables commands for the ports you want to open

### ftp
# $iptables -A INPUT -p tcp -m tcp --destination-port 21 -j ACCEPT

### ssh
$iptables -A INPUT -p tcp -m tcp --destination-port 22 -j ACCEPT

### dhclient
# $iptables -A INPUT -p tcp -m tcp --destination-port 67 -j ACCEPT

### http
# $iptables -A INPUT -p tcp -m tcp --destination-port 80 -j ACCEPT

### NetBIOS (Windows Networking, Samba -- careful, this is insecure!)
# $iptables -A INPUT -i eth1 --protocol tcp --dport 137 -j ACCEPT
# $iptables -A INPUT -i eth1 --protocol tcp --dport 139 -j ACCEPT

### Bittorrent
# $iptables -A INPUT -p tcp -m tcp --destination-port 6881:6889 -j ACCEPT

### Palm Lifedrive WiFi HotSync
# $iptables -A INPUT -p tcp -m tcp --destination-port 11096 -j ACCEPT
# $iptables -A INPUT -p tcp -m tcp --destination-port 14238 -j ACCEPT


##### BLOCK #####
# $iptables -A INPUT -i eth0 -m state --state NEW,INVALID -j DROP
# $iptables -A FORWARD -i eth0 -m state --state NEW,INVALID -j DROP


###### DEFAULTS #####
 $iptables -A INPUT -p ALL -m state --state ESTABLISHED,RELATED -j ACCEPT
 $iptables -A INPUT -s 127.0.0.1 -j ACCEPT
 echo "Rules loaded."

}

flush () {

 echo "Flushing rules..."
 $iptables -P FORWARD ACCEPT
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

While still in the Terminal, type the following:

**$ sudo chmod 755 /etc/init.d/firewall && update-rc.d firewall defaults && sudo /etc/init.d/firewall start**

To check your iptables rules, use the following command:

**$ sudo iptables -L**

---

### Post by tad1073 on 2008-03-05
I need to add https, imaps, submission and ntp. How would that be written?

---

### Post by Matt Yun on 2008-03-05
https is port 443.  I don't know what the rest are, so you'll have to look them up: here's a Wikipedia [List of TCP and UDP port numbers]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers").

As you see from the firewall script I posted above, I only keep port 22 open for SSH.

If you want to do anything more complex with iptables, I strongly suggest that you google some iptables tutorials.  There's a pretty thorough one on howtoforge.com:  [Basic Iptables - Debian/Red Hat]("http://www.howtoforge.com/linux_iptables_sarge")

---

### Post by tad1073 on 2008-03-05
Thanks for the script. i need to save it as a sh extenstion, correct?

---

### Post by Matt Yun on 2008-03-05
> **tad1073 said:**
> Thanks for the script. i need to save it as a sh extenstion, correct?

It is unnecessary to save it with any extension; the **chmod 755 ** command is what sets it as an executable.

Just follow my directions to the letter; as you see, the file will be called **firewall** and it is located at **/etc/init.d**.

---

### Post by tad1073 on 2008-03-05
other than adding rules for mail and 445 I followed it to the letter.It is up and running, again thanks for your help.

---

### Post by tad1073 on 2008-03-07
I need some more help. I have an iptables wrote like listed below but I am unable to se my network.
```
### NetBIOS (Windows Networking, Samba -- careful, this is insecure!)
 $iptables -A INPUT -i ath0 -s ip address -d ip address -p tcp --dport 137 -j ACCEPT
 $iptables -A OUTPUT -s ip address -d ip address -p tcp --dport 137 -j ACCEPT

```

I first tried it like listed below and that didn't work either.
```
### NetBIOS (Windows Networking, Samba -- careful, this is insecure!)
# $iptables -A INPUT -i eth1 --protocol tcp --dport 137 -j ACCEPT
# $iptables -A INPUT -i eth1 --protocol tcp --dport 139 -j ACCEPT
```

---

### Post by tad1073 on 2008-03-07
bump

---

### Post by tad1073 on 2008-03-08
bump...

---

### Post by Matt Yun on 2008-03-10
> **tad1073 said:**
> I need some more help. I have an iptables wrote like listed below but I am unable to se my network.
```
### NetBIOS (Windows Networking, Samba -- careful, this is insecure!)
 $iptables -A INPUT -i ath0 -s ip address -d ip address -p tcp --dport 137 -j ACCEPT
 $iptables -A OUTPUT -s ip address -d ip address -p tcp --dport 137 -j ACCEPT

```

I first tried it like listed below and that didn't work either.
```
### NetBIOS (Windows Networking, Samba -- careful, this is insecure!)
# $iptables -A INPUT -i eth1 --protocol tcp --dport 137 -j ACCEPT
# $iptables -A INPUT -i eth1 --protocol tcp --dport 139 -j ACCEPT
```

Your post is unclear as to what you are trying to accomplish, but I suspect that your iptables rules are not the problem here.  

I'm able to connect to my employer's Microsoft CIFS/SMB network simply by going to the **Places** menu -> **Network** -> **Windows Network**, without having to open any ports in my firewall.

However, if you are trying to set up your Ubuntu box as a SAMBA server for Windows machines, then you probably have not configured it properly.  I am no expert at that, so I've reached the limit of my help to you, but you should look at tutorials like [this one on howtoforge.com]("http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller") (google others), then start a new thread at ubuntuforums.org.

It would be helpful in your question if you described the steps you took to configure your server, the problems you encountered, and your attempts to fix them.  Good luck!

---

### Post by tad1073 on 2008-03-11
I didn't want to use fiestarter because last time I did i couldn't print to a network printer or see ubuntu from xp, but i installed it any way and it is working great, I can print, i can access ubuntu from xp and vice versa.

I think what the problem was, was when I first installed ubuntu. I was following a tutorial and did something like:
```
iptables A-INPUT something something something -j REJECT
```
I can't remember exactly, but i didn't flush those rules and I think that was causing the problem.

Anyway, thanks again. Everything is working good.

---

