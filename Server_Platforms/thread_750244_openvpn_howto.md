---
title: "openvpn howto ?"
date: 2008-04-09
forum: Server Platforms
---

### Post by usernameomar on 2008-04-09
i'm running a network contains several machines some machines run virtual machines anyway i'm connected to the internet via static ip, our data center is at another locations it runs some servers contains virtual machines all i want to do is to use openvpn to connect machines from here to the machines there without enabling ssh, i mean i have here dynamic ips and there too so i want them to see eahc other like the same network, i didn't install or configure openvpn before i know i can install it using apt but i wanna know how the configuration should be from my experience i know that Microsoft's ISA can do a site to site using ISA can i do that with openvon? or what todo? give me any guide or howto to follow and i'll be thankful.

---

### Post by SpaceTeddy on 2008-04-09
A) you can "bridge" the servers together using openvpn. that way you have one "master-server" which will hold the connections to the other networks and will act as gateway between them. Use a static key and it is pretty simple so setup (i can provide sample configs if you wish)

the pro for this solution is that you can even forward layer 2 pakets, and non routeable pakets like dhcp-broadcasts

the con for this setup is that it does not scale well and will produce a LOT of bandwidth...

B) you can use routed VPN devices. the setup is pretty much the same, just that this time you cannot forward layer 2 or broadcasts... and every site has to have their own subnet. But you will be able to setup routing between them, and the communication is A LOT more efficient. This setup does acctually scale..

as for howtos... here they are
[static openvpn]("http://openvpn.net/index.php/documentation/miscellaneous/static-key-mini-howto.html") (links between computers)
[briding interfaces]("https://help.ubuntu.com/community/NetworkConnectionBridge")

i cannot find any more at the moment (have to google myself) - but i ahve done it before. If i find the time later i will write down what to do. This is acctually fairly simple to setup... only a dozen command a few files...

---

### Post by usernameomar on 2008-04-10
thanks you alot,  please provide me with the sample conf files, i'll provide all info when i'm done with that.

---

### Post by SpaceTeddy on 2008-04-10
ok... i'll first go into option B) - routed network. Option A is rarely needed, but very neat if you do run into a scenario where you need it.

i will assum the following setup for now:

Network A (nA) <---> routerA (rA) <----> Internet <----> routerB(rB) <---> Network B(nB)
log into two two routers and install openvpn via
```
apt-get install openvpn
```

we are only going to work on rA for now
go into the config dir of openvpn, and create a static shared key for the connection via
```
sudo su
cd /etc/openvpn
openvpn --genkey --secret static.key

```

then, create a config file for this side of the vpn that looks like this (i will comment the improtant lines):

> *#which tun device to use (this is important if you have mode than one connection and need to handle them differently in iptables). this VPN will always be bound to the device tun1 and no other*
dev tun1

*#this is the fqdn or IP of the remote server, i.e. the other end of the connection*
remote rB.example.net

*#definition which port to use locally, and which remote. Again, with only one tunnel, this can be left out (will default to port 1194). with more than one, you will need to specify it. this HAS TO MATCH on the other side of the tunnel*
lport 15001
rport 15000

*# IP confguration. first comes the local device, then the remote. this HAS TO MATCH the config in rB*
ifconfig 10.0.0.1 10.0.1.1
*#file where to find static key that is to be used.*
secret /etc/openvpn/static.key

*#run openvpn in background*
daemon 

*#add this route to the network. WIth this, you can tell your rA which networks are to be found behing rB.*
route 192.168.10.0 255.255.255.0 

*# this tells openvpn to drop it's privilegdes once started to the given user and group for enhanched security. The persistant bits is for restarting. Since openvpn drop its rights after the start, i would not be able to create a tun device or read the key needed to the connection. The static tells it to keep the information even on connection loss. (handy on dsl lines)*
user nobody
group nogroup
persist-key
persist-tun

*#where to log (you will have to create the dir /var/log/openvpn) and give it to the user/group menitoned above). Otherwise, openvpn cannot log to it. This also comes in handy when you have more than one VPN and need to know what is happening where*
status /var/log/openvpn/openvpn-status.log
log-append  /var/log/openvpn/openvpn.log

*#there are tweaking options and can be left out. for information what they do check the openvpn manual*
tun-mtu 1500
fragment 1500
mssfix
ping-restart 60
ping 20

next, copy the static.key to rB. Make sure that you use an encrypted chanel... ssh most preferibly. **Do not send this by email, via ftp, http  or any other unecrypted protocol ! this file has to stay hidden and secret at all costs!**

once the key is safely copied, create the config file for rB. i will not comment it again, but will point out the bits that differ from rA. most option will only be swapped.

> dev tun1
**remote rA.example.net**
**ifconfig 10.0.1.1 10.0.0.1**
secret /etc/openvpn/staticVPN.sec
daemon 
ping-restart 60
ping 20
**route 192.168.0.0 255.255.255.0 **
tun-mtu 1500
fragment 1500
mssfix
[B]lport 15000
rport 15001
[/B]
user nobody
group nogroup

persist-key
persist-tun

status /var/log/openvpn/openvpn-status.log
log-append  /var/log/openvpn/openvpn.log


as you can see the hostname has changed, the ifconfig has swapped it's configuration (by that matching the one from rA). The route for the network behind it have changed, and the ports have swapped. the rest stays exaclty the same. 

if you fire up openvpn (on both servers) now it should connect, giving you an output in it's logfile that looks like this:
> Thu Apr 10 11:27:35 2008 OpenVPN 2.0.9 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] bui
lt on Sep 20 2007
Thu Apr 10 11:27:35 2008 TUN/TAP device tun1 opened
Thu Apr 10 11:27:35 2008 ifconfig tun1 10.0.0.1 pointopoint 10.0.1.1 mtu 1500
Thu Apr 10 11:27:35 2008 GID set to nogroup
Thu Apr 10 11:27:35 2008 UID set to nobody
Thu Apr 10 11:27:35 2008 UDPv4 link local (bound): [undef]:15001
Thu Apr 10 11:27:35 2008 UDPv4 link remote: x.x.x.x:15000
Thu Apr 10 11:27:45 2008 Peer Connection Initiated with x.x.x.x:15000
Thu Apr 10 11:27:46 2008** Initialization Sequence Completed**

the bold bit shows you the connection is done. you sould now be able to ping the servers with the vpn ip. 

now, confgure your routes, enable ip_forwarding, and you are all set... Any further question i'll be happy to answer :)

---

### Post by SpaceTeddy on 2008-04-11
i've written down a howto on for this. it can be found [here]("http://ubuntuforums.org/showthread.php?p=4695925#post4695925")

---

### Post by usernameomar on 2008-04-14
this is ok with me the 2 hosts are connected but i can't get the virtual machines connected? what is the network settings for the virtual machines should be if i have host rA & rB ..

my rA openvpn conf is

```

dev tun0
remote gbox31
ifconfig 10.0.0.1 10.0.1.1
secret /etc/openvpn/static.key
daemon

lport 15000
rport 1194

route 192.168.248.0 255.255.255.0
user nobody
group nogroup
persist-key
persist-tun

status /var/log/openvpn/gbox26-openvpn-status.log
log-append /var/log/openvpn/gbox26-openvpn.log

ping-restart 60
ping 20

```

my rB openvpn conf is 

```

dev tun0
remote gbox26
ifconfig 10.0.1.1 10.0.0.1
secret /etc/openvpn/static.key
daemon

route 192.168.248.0 255.255.255.0
lport 1194
rport 15000

user nobody
group nogroup
persist-key
persist-tun

status /var/log/openvpn/gbox31-openvpn-status.log
log-append /var/log/openvpn/gbox31-openvpn.log

ping-restart 60
ping 20

```

connection between hosts are ok but what should be the settings for the virtual machines after each host let's assume that i have 1 virtual machine under every host so what should the configuration look like the network to let the virtual machines connect to each other ..

---

### Post by SpaceTeddy on 2008-04-14
i am not understanding your setup. What virtual machines are you talking about ? and where exactly are the openvpn processes running... could you draw me a picture of what your setup looks like ?

also, the route to 192.168.248.0 cannot be set on both hosts... that would mean that the network is inbetween the two openvpn processes. That route is defintely not working :)

---

### Post by usernameomar on 2008-04-14
i will show u now 

the first host "gbox26"

openvpn conf is

```

dev tun0
remote gbox31
ifconfig 10.0.0.1 10.1.1.1
secret /etc/openvpn/static.key
daemon

lport 15000
rport 1194

route 192.168.62.2 255.255.255.0
user nobody
group nogroup
persist-key
persist-tun

status /var/log/openvpn/gbox26-openvpn-status.log
log-append /var/log/openvpn/gbox26-openvpn.log

ping-restart 60
ping 20

```

and the second host is gbox31

openvpn conf is

```

dev tun0
remote gbox26
ifconfig 10.1.1.1 10.0.0.1
secret /etc/openvpn/static.key
daemon

route 192.168.248.2 255.255.255.0
lport 1194
rport 15000

user nobody
group nogroup
persist-key
persist-tun

status /var/log/openvpn/gbox31-openvpn-status.log
log-append /var/log/openvpn/gbox31-openvpn.log

ping-restart 60
ping 20

```


they are connected i'm tailing the logs in both machines they are connected

in both hosts "Initialization Sequence Completed"

qa has avirtual machine with 2 ethernet

eth0  is addr:192.168.1.202
eth1 is addr:192.168.1.202


gbox31 has a virtual machine with this ip 

eth0 192.168.248.128


they don't connect please correct me i'm very confused . 

now i noticed an error 

in both hosts 
"Mon Apr 14 17:44:20 2008 ERROR: Linux route add command failed: shell command exited with error status: 4"

---

### Post by usernameomar on 2008-04-15
hey i'm connected now the conf file can't set the rputing anyway i don't know how to ethernet bridging i installed bridge-utils and tried to do the bridge manually or using the conf i read some examples form the documentation can be found in openvpn.net but it doesn't seems to work now .. can you post a howto about ethernet bridging over openvpn ?

---

### Post by SpaceTeddy on 2008-04-15
i am working on the part 2 - unforteunatly, it is a little more complicated that the first part, as it involves makeing changes to you physical network settings. I will not post it until i have figured out how i  this can be achived with possible minimal damage to a system if something goes wrong.

i can offer to send you the draft i have so far...

---

### Post by usernameomar on 2008-04-15
ok send it to me in a private p.m and plz if i can contatc you by chat tell me cause i'm very confused i'm reading in the manuall and it's very diffrent than what i've done with you, something about changing tun0 to tap0 ..etc it's about server and client's but i want todo this static one this would be better and easier for me.

---

### Post by andc on 2008-06-05
If I want to autenticate N client through internet to my private LAN, using openvpn on the gateway pof the LAN the conf is very different?

I would permit the access to the internal server (not exposed on internet) to some clients around th world.

The gateway is UbuntuServer 8.04, with 2 eth interf (the interface routing to internet as a dynamic ip with a dynamicDNS service on it).

Tnx

---

