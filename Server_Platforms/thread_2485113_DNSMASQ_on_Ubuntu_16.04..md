---
title: "DNSMASQ on Ubuntu 16.04."
date: 2023-03-20
forum: Server Platforms
---

### Post by zooot on 2023-03-20
So here is my DNSMASQ problem.


I'm running to VirtualBox Ubuntu 16.04 servers on two seperate 2011 mac mini servers (macos High Sierra). Each of the two VirtualBox Ubuntu servers runs a LAMP website (Drupal based) and a DNSMASQ dns server. 


The network is controlled by a Fritz!Box 7590. In the configuration the two different DNSMASQ servers are listed instead of the standard provider DNS.


VirtualBox One:


    static IP             192.168.2.50
    website IP     192.168.2.50    xxx.mydomain.com
    DNSMASQ IP     192.168.2.50


VirtualBox Two:


    static IP             192.168.2.55
    website IP     192.168.2.55    yyy.mydomain.com
    DNSMASQ IP     192.168.2.55


Fritz!Box (router)


    Gateway        192.168.2.1
    DHCP        192.168.2.100-200






So far so good. This setup seemed to have worked for hals a year. Then recently I had to restore one of the VirtualBox servers. And now it only works somewhat. In short:


Each of the two DNSMASQ servers will only resolve the website on the other VirtualBox, the website on the same VirtualBox will resolve to localhost.


So if I want to be able to reach the domain in VirtualBox One I have to use the DNSMASQ server in VirtualBox Two and the other way around.


Here is the dnsmasq.conf file from VirtalBox Two (for Box One just substitute the 192.168.2.50 for 192.168.2.55).


cat /etc/dnsmasq.conf
----------------------------------------------------
# DNS configuration
port=53


#/etc/dnsmasq.conf
domain-needed
bogus-priv
expand-hosts
 
# The address 192.168.2.55 is the static IP of this server 
# You can find this ip by running ifconfig and look for the 
# IP of the interface which is connected to the router.
listen-address=127.0.0.1
listen-address=192.168.2.55
bind-interfaces
 
# Use open source DNS servers
server=8.8.8.8
server=8.8.4.4
 
# Create custom 'domains'.
# Custom 'domains' can also be added in /etc/hosts


address=/xxx.mydomain.com/192.168.2.50
address=/yyy.mydomain.com/192.168.2.55


# address=/www.anotherdomain.com/192.168.2.50
# address=/anotherdomain.com/192.168.2.50


# address=/www.stillanotherdomain.ch/192.168.2.50
# address=/stillanotherdomain.ch/192.168.2.50
----------------------------------------------------


I am not very experienced with DNS servers, so can you possible point me in the right direction if you see an error.


Thanks
Paul

---

### Post by TheFu on 2023-03-20
Standard support for 16.04 ended in 2021. Move to a supported release.  That's your first necessary step.  22.04 is the current LTS.

---

