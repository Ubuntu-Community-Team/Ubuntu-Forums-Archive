---
title: "Ubuntu Proxy Server"
date: 2007-11-23
forum: Server Platforms
---

### Post by Alan03 on 2007-11-23
Hey Folks,

Could you please be so kind as to help me out,
iv bin trying for days now to put up a simple proxy server.. all attempts failed sorry to say.

im trying something very simple to be honest,

Im in Vmware, got 2 images (server and client)

Server = Ubuntu, got Squid installed.
Client = Windows Xp Pro.

Now im able to browse with XP PRO so got internet and all that.

the only thing im trying to do is, being able to browse on my XP client but then using the Proxy server. 

now im not an expert on this whole networks and all that but ill try to give you some basic information, hoping that it might help you help me.

this is how i started on Ubuntu.

sudo apt-get install squid squid-common (No probs here)
sudo cp /etc/squid/squid.conf /etc/squid/squid.conf.original (No probs here aswell)

now this i can still follow.
now we need to open the config file.. 
nano squid.conf (No probs here either)

but then??
iv kinda followed like 12 howtos and all of them failed.


 My Windows Xp is saying: 
Connection-specific DNS suffix: localdomain
Ip address: 192.168.79.129
SubnetMask: 255.255.255.0
Defualt Gateway: 192.168.79.2 

Iv bin following this Howto: 
[http://www.brennan.id.au/11-Squid_Web_Proxy.html](http://www.brennan.id.au/11-Squid_Web_Proxy.html)

can you guys help me out? 
can you like give me a squid.conf file i can just typ over and be done with it or can you tell me what i need to do differently from the howto url i just posted.

And can i just typ these commands on like the top over the Squid explaining text or do they need to be typd at an specific location.

Really sorry to bother you guys, 
but if you can help then please do. 

its an assignment for school and really truly have tryd but this is like the first time wir using linux and configuration a proxy so im all lost here.

Thanks alot in advance,
Alan.

---

### Post by bmathis on 2007-11-23
Have you tried this howto out? I wrote it awhile back but it still works.

[http://ubuntuforums.org/showthread.php?t=320733]("http://ubuntuforums.org/showthread.php?t=320733")

---

### Post by koenn on 2007-11-24
squid installs with a default "deny everything', so the first thing you have to do after installing, is to decide which hosts should be allowed to use it, and edit /etc/squid/squid.conf accordingly.
This is a very basic "allow hosts on my LAN to use squid for web browsing" config : 

```

# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS

# Example rule allowing access from your local networks. Adapt
# to list your (internal) IP networks from where browsing should
# be allowed
acl our_networks src 192.168.120.0/24 192.168.200.0/24
http_access allow our_networks
http_access allow localhost


# And finally deny all other access to this proxy
http_access deny all


```

---

### Post by veloce on 2007-11-24
personally, for something as specific as a proxy server, I use a purpose built distro like IPCop or pfsense.  But as a learning exercise, I suppose building it up from Ubuntu Server would be more interesting.

---

### Post by Alan03 on 2007-11-24
Hey Folks!

Thanks so much for the replys!
finally got it working!

now iv got one Client connected.
still need 29 other clients to be connected but that shouldn't be a problem.

im actually trying to build up a whole network.

got like 4 linux servers (DNS, Web/Secured, Mail server)
3 windows (File Server, DHCP Server, Authentication Server)
and 29 Win Xp clients.

my only question left is (and it might sound stupid)
but do i need to add the other servers to the squid aswell?
or just the clients? 

cuz as the assignment says "All of the interneting needs to go trough the proxy, so the Proxy can keep an eye out for the internet traffic, it also has to filter it and log it"

i was thinking if the Mail Server needs to be able to send and retrieve mails, it to will need to connect to the internet right? 

i know its all vague and well any little bit of help would be most appreciate it. Thanks again for the kind replys.

Regards,
Alan.

---

### Post by Alan03 on 2007-11-24
Folks im facing a little prob,

like i said The proxy server is good and running.

just that the Proxy and the Xp client dont have the correct IP address.

The Xp client is: 192.168.79.129 but needs to be 192.168.4.50
And the Proxy is 192.168.79.132 but needs to be 192.168.3.11 

iv followed this Howto but ended up reinstalling Ubuntu!

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

can you guys please help out.

Thanks a million.

Regards,
Alan.

---

### Post by veloce on 2007-11-24
> **Alan03 said:**
> 

The Xp client is: 192.168.79.129 but needs to be 192.168.4.50
And the Proxy is 192.168.79.132 but needs to be 192.168.3.11 



They both will be getting their addresses from the DHCP server.  If you want them to have specific addresses then you need to set each of them manually.

---

### Post by Alan03 on 2007-11-25
Yeah and thats what iv done but after setting them up manualy i cant seem to connect anymore.

this is how iv set them up.

(Ubuntu)
auto eth0
iface eth0 inet static
address 192.168.3.11
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255
gateway 192.168.3.1

(Squid.conf)

http_port 192.168.3.11:8080 
acl dmznetwerk src 192.168.4.50/24
http_access allow dmznetwerk
http_access deny all

(xp client)

address 192.168.4.50
subnetmask 255.255.255.0
default gateway 192.168.4.0
Preferred DNS Server 192.168.4.0

Still new with this, so im sure iv made a mistake some where in this all.

Thanks again, really appreciate it.

Regards,
Alan.

---

### Post by koenn on 2007-11-25
If you do manual network configuration, you really have to know a bit about networks - you can't just put pretty numbers there and expect things to work. If you're really interested in this sort of stuff, you shoud read a beginners guide to tcp/ip / subnetting / network administration. 

On first sight 
1- you've put your server (ubuntu) and your client (xp) in separate networks, so they can't talk to each other unless there's a router in between

2- your definition of dmznetwerk is a host address, it should be a network address or ip range
have a look here : [http://www.subnet-calculator.com/](http://www.subnet-calculator.com/)


3- less important mistakes : the gateway address on your xp machine is a network address in stead of a host address. it's less important in this case because you probably don't have a gateway (router) anyway. 
4- likewise for the xp's DNS server.

try this ;

(Squid.conf)
http_port 192.168.3.11:8080
acl dmznetwerk src 192.168.3.0/24
http_access allow dmznetwerk
http_access deny all


(xp client)
address 192.168.3.50
subnetmask 255.255.255.0
default gateway 192.168.3.1
Preferred DNS Server <a valid dns server address>

---

