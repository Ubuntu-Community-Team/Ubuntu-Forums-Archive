---
title: "eucalyptus_ip address natted to other range"
date: 2011-09-19
forum: Ubuntu Cloud and Juju
---

### Post by sumitkhamkar on 2011-09-19
Hi friends,


I m using eucalyptus 2.0.3. version . and my setup is CC and CLC on 1 machine (10.20.74.200) and NC (10.20.74.201) with same broadcast domain. my instanaces are running fine but instance is not getting exact IP address which I mentioned in eucalyptus.conf for your reference i m sending details of my eucaluptus.conf

problem : - In my eucalyptus.conf i mentioned VNET _SUBNET (private ip range) 192.168.0.0/16 but while running instance , instance take the IP address of **192.168.[COLOR=Red]1[/COLOR].2** instead of **192.168.[COLOR=Red]0[/COLOR].1**  please guide me in to fix this problem . 

=======================================

CC configuration

VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth0"
VNET_BRIDGE="xenbr0"


VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="192.168.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="10.20.74.55"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="10.20.74.205-10.20.74.230"

==========================================

Thanks in advance.

---

