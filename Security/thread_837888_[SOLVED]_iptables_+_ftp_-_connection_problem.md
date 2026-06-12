---
title: "[SOLVED] iptables + ftp - connection problem"
date: 2008-06-22
forum: Security
---

### Post by janskey on 2008-06-22
Why is it I'm having a problem connecting to an ftp server going outside?

# iptables -L -v
Chain INPUT (policy DROP 3622 packets, 206K bytes)
 pkts bytes target     prot opt in     out     source               destination
26582 2998K ACCEPT     all  --  lo     any     anywhere             anywhere
 273K  137M ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
  189 11474 ACCEPT     icmp --  any    any     anywhere             anywhere
 3804  234K ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh
  229 12592 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www
  147 10679 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:https
    0     0 ACCEPT     udp  --  any    any     ns1dns.net   anywhere            udp dpt:domain

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 248K packets, 28M bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by kevdog on 2008-06-23
Its because ftp involves both a command and data channel, not just one ftp port 21:

Connection tracking and ftp

Firstly, you need to load the ip_conntrack_ftp module.

*** Ok this can be done one of two ways depending on how you are setting up your firewall.
1.  If you are using firestarter or some GUI, you likely need to load the kernel module (either on the command line, in the rc.local file, in /etc/modules, in /etc/network/interfaces).  If loading at the command line do the following:
sudo modprobe ip_conntrack_ftp

2. If you are using a script to load the iptables such as explained here:
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

You would add this to this near the top of the script:
MODPROBE=/sbin/modprobe
$MODPROBE ip_conntrack_ftp


Assuming you have a single-homed box, a simple ruleset to allow an ftp connection would be:

iptables -A INPUT     -p tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT

(Please note, I am assuming here you have a separate ruleset to allow any icmp RELATED to the conection.)

This is not the whole story. An ftp connection also needs a data-channel, which can be provided in one of two ways:

1) Active ftp

The ftp client sends a port number over the ftp channel via a PORT command to the ftp server. The ftp server then connects from port 20 to this port to send data, such as a file, or the output from an ls command. The ftp-data connection is in the opposite sense from the original ftp connection.

To allow active ftp without knowing the port number that has been passed we need a general rule which allows connections from port 20 on remote ftp servers to high ports (port numbers > 1023) on ftp clients. This is simply too general to ever be secure.

Enter the ip_conntrack_ftp module. This module is able to recognize the PORT command and pick-out the port number. As such, the ftp-data connection can be classified as RELATED to the original outgoing connection to port 21 so we don't need NEW as a state match for the connection in the INPUT chain. The following rules will serve our purposes grandly:

iptables -A INPUT     -p tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT

2) Passive ftp

A PORT command is again issued, but this time it is from the server to the client. The client connects to the server for data transfer. Since the connection is in the same sense as the original ftp connection,  passive ftp is inherently more secure than active ftp, but note that this time we know even less about the port numbers. Now we have a connection between almost arbitrary port numbers.

Enter the ip_conntrack_ftp module once more. Again, this module is able to recognize the PORT command and pick-out the port number. Instead of NEW in the state match for the OUTPUT chain, we can use RELATED. The following rules will suffice:

iptables -A INPUT     -p tcp --sport 1024: --dport 1024:  -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 1024: --dport 1024:  -m state --state ESTABLISHED,RELATED -j ACCEPT

---

### Post by janskey on 2008-06-25
nice tips..thanks a lot..it works!

---

