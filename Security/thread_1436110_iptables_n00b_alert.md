---
title: "iptables n00b alert"
date: 2010-03-22
forum: Security
---

### Post by mituw16 on 2010-03-22
Hello all, 
I've been a long time linux user, and am not new at all to command line. Basically this isn't really a question about iptables, but more of a is the script i wrote good. I'm just starting to dive into iptables and the machine this script is running on is acting as the DHCP and router for my home network. 

Theoretically, I want all incoming ports blocked, and only FTP, L2T via IPSEC, and custom SSH port forwarded to a Mac server I have behind the linux machine. I think that is what I accomplished, but I would rather post my script here to be sure I haven't left anything out. In my current configuration of this script, all my other comps can browse / do whatever, port forwarding is working and I can connect to my VPN, and FTP from outside my house. 

###i know ip masquerade isn't turned on, the network topology is...

Actiontec DSL modem (no dhcp or firewall, but it does have NAT on) ----> Linux router ---> switch ----> rest of my comps

## so basically the modem is actually connecting to the net, and my linux machines internet interface has a static IP I assigned, and there is a static route from my modem to my linux pc's subnet. 

##########

## script start
##################################################
########## IPTABLES FIREWALL SCRIPT ##############
##################################################


#clear old **** out of the firewall
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -t nat -X
iptables -t mangle -X
iptables -X

#always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

#create white list and black list
iptables -N blacklist
iptables -N whitelist

#add all LAN traffic to whitelist
iptables -A whitelist -s 192.168.1.0/24 -j ACCEPT

#add annoying chinese hackers to my blacklist
#add dad's G5 to my blacklist, cause it's really annoying
iptables -A blacklist -s 192.168.0.254 -j DROP


#drop new connections with no syn flag and invalid info
iptables -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
iptables -A INPUT -m state --state INVALID -j DROP

#put the whitelist and black list into place
iptables -A INPUT -j whitelist
iptables -A INPUT -j blacklist

#set up explicity port forwarding
####
####
####
##############################################################DNAT
#FTP TO G4
iptables -t nat -A PREROUTING -i eth1 -p tcp -m multiport --dports 20,21 -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.1.201:20-21
iptables -t nat -A PREROUTING -i eth1 -p udp -m multiport --dports 20 -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.1.201:20
#VPN to G4
iptables -t nat -A PREROUTING -i eth1 -p udp -m multiport --dports 500 -m state --state NEW -j DNAT --to 192.168.1.201:500
iptables -t nat -A PREROUTING -i eth1 -p udp -m multiport --dports 1701 -m state --state NEW -j DNAT --to 192.168.1.201:1701
iptables -t nat -A PREROUTING -i eth1 -p udp -m multiport --dports 4500 -m state --state NEW -j DNAT --to 192.168.1.201:4500
#VNC to G4
iptables -t nat -A PREROUTING -i eth1 -p tcp -m multiport --dports 5900 -m state --state NEW -j DNAT --to 192.168.1.201:5900
iptables -t nat -A PREROUTING -i eth1 -p tcp -m multiport --dports 5800 -m state --state NEW -j DNAT --to 192.168.1.201:5800

##################################################################moving on to the forward chain
#FTP to G4
iptables -A FORWARD -p tcp -m state --state NEW,ESTABLISHED,RELATED -m multiport --dports 20,21 -i eth1 -o eth0 -d 192.168.1.201 -j ACCEPT
iptables -A FORWARD -p udp -m state --state NEW,ESTABLISHED,RELATED -m multiport --dports 20 -i eth1 -o eth0 -d 192.168.1.201 -j ACCEPT
#VPN to G4
iptables -A FORWARD -p udp -m state --state NEW,ESTABLISHED,RELATED -m multiport --dports 500 -i eth1 -o eth0 -d 192.168.1.201 -j ACCEPT
iptables -A FORWARD -p udp -m state --state NEW,ESTABLISHED,RELATED -m multiport --dports 4500 -i eth1 -o eth0 -d 192.168.1.201 -j ACCEPT
iptables -A FORWARD -p udp -m state --state NEW,ESTABLISHED,RELATED -m multiport --dports 1701 -i eth1 -o eth0 -d 192.168.1.201 -j ACCEPT
#VNC to G4
iptables -A FORWARD -p tcp -m state --state NEW,ESTABLISHED,RELATED -m multiport --dports 5900 -i eth1 -o eth0 -d 192.168.1.201 -j ACCEPT
iptables -A FORWARD -p tcp -m state --state NEW,ESTABLISHED,RELATED -m multiport --dports 5800 -i eth1 -o eth0 -d 192.168.1.201 -j ACCEPT
#SSH to G4
iptables -A FORWARD -p tcp -m state --state NEW,ESTABLISHED -m multiport --dports 48559 -i eth1 -o eth0 -d 192.168.1.201 -j ACCEPT
#AFP to G4
iptables -A FORWARD -p tcp -m state --state NEW,ESTABLISHED -m multiport --dports 548 -i eth1 -o eth0 -d 192.168.1.201 -j ACCEPT


##########################################################################allow ssh to this computer
iptables -A INPUT -i eth1 -p tcp --dport 48558 -m state --state NEW,ESTABLISHED -j ACCEPT

###########################################################################allow this computer to be pinged
iptables -A INPUT -p icmp -m state --state NEW,ESTABLISHED -j ACCEPT

#################################################################################allow this PC to browse the web and ****
iptables -A INPUT -i eth1 -p tcp --sport 80 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -p udp --sport 80 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -p udp --sport 53 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --sport 53 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -p tcp -m multiport --sports 20,21 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -p udp -m multiport --sports 20 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --sport 443 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --sport 5353 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

###############################################################################drop all other input traffic
iptables -A INPUT -j DROP

#############################################################################log the denied packets
iptables -I INPUT 15 -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7


########## 
End script                                                                                        

(forgot to mention, the linux machine runs ubuntu server)

anyways, I'm sorry this is a long post, but other than that, what do some of you iptables god's think about this setup and my script. 

Cheers,
Matt

---

### Post by mituw16 on 2010-03-22
really? no one here knows about iptables...

---

### Post by bodhi.zazen on 2010-03-22
It is always difficult to read these things and know if they work or not.

My advice is :

1. for the number of enteries, your blacklist and whitelist seems excessive. You can do the same thing with one line each, without the need for user defined tables.

2. Are you accepting new connections ? I suspect you do not need to accept new connections on most of those ports.

3. No need for both udp and tcp on most of the ports you listed.

4. Why do you multiport only 2 ports, you can use multiport to define all ports.

If you want to know if your script works, scan your box.

---

### Post by mituw16 on 2010-03-23
thank you for the information. I found a website called auditmypc.com and they did a scan on my WAN ip address and it reported the only ports that were open were the ones I defined in the script. So I guess its working. 

Cheers, 
Matt

---

