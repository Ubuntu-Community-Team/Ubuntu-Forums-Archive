---
title: "Site to Site IPSEC VPN with Ubuntu and Meraki"
date: 2015-04-14
forum: Server Platforms
---

### Post by seanmancini2010 on 2015-04-14
Hello Everyone!

I am facing an issue with setting up a IPSEC tunnel between our Server and a Meraki MX64 appliance

I tried using VPNC which  establishes phase 1 but since the meraki doest support aggressive mode it wont work 
I tried using Openswan but I think I am missing the mark somewhere

Here is my config 

VPNC Config

IPSec gateway x.x.x.x
IPSec ID NWG
IPSec secret xxxxxxxxxx
#IKE Authmode cert
Xauth username xxxxxxxxxxxxxx
Xauth password xxxxxxxxxxxxx
nat Traversal Mode cisco-udp



Opensawn config


version 2.0     # conforms to second version of ipsec.conf specification
# basic configuration
config setup
# Debug-logging controls:  "none" for (almost) none, "all" for lots.
# klipsdebug=none
# plutodebug="control parsing"
# For Red Hat Enterprise Linux and Fedora, leave protostack=netkey
    protostack=netkey
    nat_traversal=yes
    interfaces=%defaultroute
    oe=off
# Enable this if you see "failed to find any available worker"
    nhelpers=0


 #You may put your configuration (.conf) file in the "/etc/ipsec.d/" and uncomment this.
conn sonicwall
    type=tunnel
    left=xxxxxxxxxx               
    #leftsubnet=xxxxxxxxx     
    leftid=@GroupVPN              
    leftxauthclient=yes
    right=xxxxxxxxxxx         
    rightsubnet=xxxxxxxxxxx    
    rightid=@xxxxx
    rightxauthserver=yes
    keyingtries=0
    pfs=yes
    auto=add
    auth=esp
    esp=3DES-SHA1                 
    ike=3DES-SHA1
    authby=secret
    aggrmode=no



When I test the VPN connection using the L2tp IPSEC VPN manager it works fine 
This is on a headless server so no GUI i was thinking of installing webmin and using the plugin to do the vpn tunnel
if someone can help me either with VPNC or Opensawn that would be great 


Thank you in advanced

---

