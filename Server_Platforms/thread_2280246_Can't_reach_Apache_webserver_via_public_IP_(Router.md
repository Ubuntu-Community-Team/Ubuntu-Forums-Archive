---
title: "Can't reach Apache webserver via public IP (Router is not the problem), please help"
date: 2015-05-29
forum: Server Platforms
---

### Post by SomeITGuy on 2015-05-29
Hello,

I've got a problem with Ubuntu Server and Apache which I could not solve the last days, any help would be much appreciated:
I've installed Ubuntu Server and the bitnami ruby stack (wich is using Apache 2) for a webserver. After resolving some minor problems, everything is working now except one thing: The webserver can not be accessed from outside the local network. Some other servers in our Network (Windows Terminalserver) can be accessed from the web.

Some details: Ubuntu Server 14.04 LTS (VM on a Windows SRV 2012 R2, Hyper-V), two (virtual) ethernet interfaces, eth0 is local LAN , eth1 is part of a "DMZ" (and connected to the same network as the router/gateway). We use a Netgear Router/Firewall to access the web.

Things I've already checked:
- Port 80 on the Router is forwarded.
- The Apache can be accessed from other systems in the LAN.
- The Apache is listen to "0.0.0.0:80" (should listen on eth0 and eth1 (IPv4))
- It can NOT be accessed via Internet (tried not only public IP in the LAN but also remote via a server in a other department of our company, so "really outside the LAN") :(
- The traffic from the other departments server does reach the "public" interface eth1, monitored this via bash (tcpdump) while try to access the webserver via browser! So the router should not be the problem...
- The log files of the Apache does not show anything if you try to access it via public IP
- The Firewall/ufw is (at the moment) deactivated (until public access works)
- apparmor is active (Ubuntu default), but no profile for appache present. Installed the additional profiles via bash, didn't change anything on that.
- SELinux is not active it seems (Ubuntu default)

It seems that the traffic is lost/dropped between the Ubuntu network stack and the Apache webserver imho... but I have no more ideas why :( .

Any suggestions anyone?
Thanks for reading! :)

Best Regards
SomeITGuy

---

### Post by darkod on 2015-05-29
Why would you have it connected to both the lan and the dmz? I haven't used such configuration. Could that be confusing the routing from outside? Although I think it shouldn't matter.
But you usually use either local lan ip and port forwarding, or dmz. Not both.

---

### Post by SomeITGuy on 2015-05-29
Thanks for your reply! The internal LAN and the dmz use different subnets and here in this company you can't reach a dmz IP from internal LAN or the otherway round. That means that at the moment a system which should be accessable local and via the internet (which are only exceptional cases) has to have two interfaces/connections.
I have to say: This whole infrastructure was not created by me but by my predecessor/the former admin. If you say that's not the way it's normally done, you may totally be right ;) .

But as I said: The routing seems correct, as the traffic reaches eth1 on the Ubuntu server, either the Apache drops it or does not respond or... it get lost somewhere between "Ubuntu" and Apache? :(

---

### Post by darkod on 2015-05-29
Now that you mention it again, the routing might not seem correct. You said eth0 is the lan and eth1 the dmz. And that you can see port 80 traffic on eth1.

But the dmz has nothing to do with port forwarding. The dmz is sort of "direct entry" and the port forwarding done by the router is towards the lan only because the router is between the public internet and the lan. So the forwarded port 80 should reach only eth0, nothing else.

Have you tried without the dmz connection? Just for a test. I still think the setup is weird (not saying it's your fault :) ). The reason is this: if the idea of using dmz and lan is to offer access to both local and remote users, port forwarding is not needed. Local users access using the local lan ip and internet users using the dmz ip. No port forwarding is done. If you use it, no need for dmz because internet users will use the router public ip and then the router does the forwarding. Makes sense?

---

### Post by SomeITGuy on 2015-05-29
Thanks again for your fast reply! I got your point, but I don't think this is really the reason of this specific problem. Not only because of the traffic (from outside) is visible while monitoring eth1 ("dmz") which is the way I want it, the same configuration (with the two interfaces and so on) was also used for the former webserver of the company (a "server" based on WinXP... brrrr 8-[ ). On the router side, we changed simply the IP from the old webserver to the new one for port forwarding (both same port 80 and same subnet ("dmz")). Perhaps we should not talk about "dmz" any longer, that was the intention of the former admin (I guess) but at last there are two different LANs with different subnets...

Also, if I login on a local server in the LAN (remote), I can access the webserver from there with both adresses without problems! ("192.168.110.20" = local/eth0, "192.168.100.20" = "DMZ"/eth1) 

I would think the problem it's something very simple (setting of some kind) on the Ubuntu or Apache side, but I don't know where to search now...

---

### Post by darkod on 2015-05-29
I am not an expert in apache but if you can browse the websites from the lan there are no special settings you need to make so that it works from the outside. Not that I know of.

The same goes for ubuntu/networking/firewall. It works using the local ip from the lan. The router is simply doing forwarding to the same lan ip. So it should work...

---

### Post by volkswagner on 2015-05-29
How are the interfaces configured?

Please post contents of /etc/network/interfaces.

Please also post your apache2 vhost file.

Are you testing with basic Apache2 site or a ruby site?

You say some of your terminal servers can be accessed from the web. Is the same router/dmz
already routing port 80 to another server? You may need a reverse proxy from main server to point to the Ubuntu server.

Please post output to verify Apache2 is listening on all interfaces:
```
sudo netstat -tulpn | grep :80
```


Your workplace may have multiple public ip addresses. Is the public ip you are trying the same as seen by the server's public ip. To check your servers public ip make sure curl is installed and run the following:

```
curl ifconfig.me
```

---

### Post by SomeITGuy on 2015-05-29
Thank you both! :) Here's the reqested information, first the /etc/network/interfaces:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

(The network interfaces were configured via a installed   Kubuntu-Desktop, I guess the config is nearly empty because of this?  Here in the company there is  nobody that could administrate a Linux  server only via terminal/ssh at  the moment, and I know KDE  from my  private Mint-Installation & Knoppix, so I installed a GUI (first  Linux server here, I hope we  could solve the problem so we can use  more Linux machines in the  future!))

This is how we configured the interfaces (eth0 on the left side, eth1 on the right side, 192.168.100.8 is our Netgear Router):

[ATTACH=CONFIG]262283[/ATTACH]

The httpd-vhosts.conf (I hope this is the right file, it was not manually edited, does not seem relevant to me):

> # Virtual Hosts
#
# Required modules: mod_log_config

# If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them. Most configurations
# use only name-based virtual hosts so the server doesn't need to worry about
# IP addresses. This is indicated by the asterisks in the directives below.
#
# Please see the documentation at 
# <URL:http://httpd.apache.org/docs/2.4/vhosts/>
# for further details before you try to setup virtual hosts.
#
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
# The first VirtualHost section is used for all requests that do not
# match a ServerName or ServerAlias in any <VirtualHost> block.
#
<VirtualHost *:80>
    ServerAdmin [EMAIL="webmaster@dummy-host.example.com"]webmaster@dummy-host.example.com[/EMAIL]
    DocumentRoot "/data/rubystack/apache2/docs/dummy-host.example.com"
    ServerName dummy-host.example.com
    ServerAlias [www.dummy-host.example.com]("http://www.dummy-host.example.com")
    ErrorLog "logs/dummy-host.example.com-error_log"
    CustomLog "logs/dummy-host.example.com-access_log" common
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin [EMAIL="webmaster@dummy-host2.example.com"]webmaster@dummy-host2.example.com[/EMAIL]
    DocumentRoot "/data/rubystack/apache2/docs/dummy-host2.example.com"
    ServerName dummy-host2.example.com
    ErrorLog "logs/dummy-host2.example.com-error_log"
    CustomLog "logs/dummy-host2.example.com-access_log" common
</VirtualHost>


I'm testing with a ruby site.

Port 80 is only forwarded to the new webserver (192.168.100.20 = eth1) at the moment.

Output for "sudo netstat -tulpn | grep :80"
> tcp          0        0 0.0.0.0:80                          0.0.0.0:*                           LISTEN                8632/httpd      
Edit: The PID is one of the httpd processes. If you access the page locally, the processes become active. If you try it from outside, you don't see any httpd process cpu activity (but activity on the eth1 as I mentioned above).

The output of "curl ifconfig.me" is the correct public IP (which I use for my tests).


Some more info:
I can access the webserver via browser without problems direct on the ubuntu server AND on another local server (remote) via: 127.0.0.1, localhost, 192.168.110.20, 192.168.100.20 and the domain name... but not via public IP. As already mentioned public IP (or domain name) does not work even from a system which is really outside the local network.
I don't get any error messages or something like that, only a time out and blank page of course.
We have a static IP and it should not have to do anything with the ISP or the router, because it worked with the old simple webserver on the same port (and in the router only the destination adress for the port forwarding was changed to the new one).


If you have any suggestions or need more information, please just let me know! :)


Edit: Strange thing: If I change the destination IP in the router (port forwarding) to the adress of the old simple webserver, it can be accessed imediately (local via public IP and from outside). Change it back to the 192.168.100.20, and it can be reached only locally, but not from outside. Definitely seems not to be a router problem so... :confused:

---

### Post by volkswagner on 2015-05-29
Your mention of simple web server, was it a Hyper-v guest as well?

Problem may be misconfigured Hyper-v interfaces.

You will need to do some testing with tools such as tcpdump, wireshark, traceroute to see where the failure occurs.

Post output of:
```
route
```

```
ifconfig
```

Since server has GUI, go to [http://canyouseeme.org](http://canyouseeme.org) and check port 80.

I'm no ruby guru. I'd try the default apache site first. Some software sites expect a certain URL, your site may not be expecting the public IP in URL.

---

### Post by SomeITGuy on 2015-06-01
Thank you again volkswagner :) ! I don't think it should be a problem of the Hyper-V-Host (or it's firewall) because the old webserver runs on the same host... but I will check these settings again.
Edit: Couldn't find any differences between the Hyper-V-settings of the old Webserver and the new (ubuntu) one.

Here's the requested information:

Output route:

> Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
default         192.168.110.22  0.0.0.0         UG    0      0        0 eth0
192.168.100.0   *               255.255.255.0   U     1      0        0 eth1
192.168.110.0   *               255.255.255.0   U     1      0        0 eth0

Output ifconfig:

> eth0      Link encap:Ethernet  Hardware Adresse 00:15:5d:6e:60:29
          inet Adresse:192.168.110.20  Bcast:192.168.110.255  Maske:255.255.255.0
          inet6-Adresse: fe80::215:5dff:fe6e:6029/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:874193 Fehler:0 Verloren:61915 Überläufe:0 Fenster:0
          TX-Pakete:568 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
         RX-Bytes:96236484 (96.2 MB)   TX-Bytes:78497 (78.4 KB)

eth1      Link encap:Ethernet  Hardware Adresse 00:15:5d:6e:60:2a
         inet Adresse:192.168.100.20  Bcast:192.168.100.255  Maske:255.255.255.0
          inet6-Adresse: fe80::215:5dff:fe6e:602a/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:989951 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:6233 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
         RX-Bytes:90044123 (90.0 MB)  TX-Bytes:268298 (268.2 KB)

lo        Link encap:Lokale Schleife
        inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:65536  Metrik:1
          RX-Pakete:553 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:553 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:0
         RX-Bytes:48755 (48.7 KB)  TX-Bytes:48755 (48.7 KB)


Output of [http://canyouseeme.org](http://canyouseeme.org) (I replaced the true public IP by "..."):

> Error: I could not see your service on ... on port (80)
Reason: Connection timed out 


Edit: If I change the port forwarding (80) simply to the IP of the old webserver (which is running on the same host and works with bitnami (not Wamp, I was wrong on that)), the canyouseeme test is successfull... changing from 192.168.100.20 to 192.168.100.15 is all I changed to test this.

**I think we can be sure now (after all tests I did and mentioned) that it's NOT a problem of the ISP, NOT of the Router, NOT of the Hyper-V-Host, it has to do something with the ubuntu server OR the apache (because there's incoming traffic at eth1 personally I think it is a apache problem, but I'm not sure...) but what exactly... ? :confused:** This really drives me mad... :(

---

### Post by The Cog on 2015-06-01
There's your problem. The routing isn't right.
You have a default route directing all packets (except those destined for the local networks) to 192.168.110.22 on eth0. 
I would think that the default gateway should be the router on the DMZ eth1, sending it towards the internet. 

Try these two commands to see if that gets the internet working. They change the default route to point towards the internet router. I don't know the internet router's address so I will use  192.168.100.x and leave you to find the correct address:
```
sudo ip route del default via 192.168.110.22
sudo ip route add default via 192.168.100.x
```

Edit:
The windows command **route print** on the windows server will show you its routing table for comparison.

Another edit:
Using two windows, running **sudo tcpdump -np -i eth0** in one and **sudo tcpdump -np -i eth1** in the other will probably show you packets arriving on one interface and responses leaving on the other (in the wrong direction) until the routing is changed.

---

### Post by SomeITGuy on 2015-06-01
That was it! Thank you very much 'The Cog'!  :D :D :D
And thanks 'volkswagner' too for asking me about 'route'!

I configured the gateways for both interfaces via gui and didn't thought that a default route would be the problem... :oops:

I added the del and the add command to the rc.local and now it works even after a reboot (I know this is not the best way, but I don't want to uninstall the network manager completely and configure everything again via /etc/network/interfaces manually now... didn't find anything on the web about a third way to solve this).

Ironically, I think it would have worked all the time if the external interface would have been eth0 instead of eth1... (the auto default route seems to be the gateway of eth0?)

Anyway, it works now! \\:D/
Thanks again!!

---

### Post by The Cog on 2015-06-01
> That was it! Thank you very much!
Good to hear it, and you're welcome.
> the auto default route seems to be the gateway of eth0?
I have no idea. I've never used the GUI to configure the network - I've always used /etc/network/interfaces on servers, and let the network manager do its own thing on workstations, laptops etc. A quick look at the GUI shows that you have a place to add routes, but I don't know how that interacts with a default gateway that DHCP hands out.

Using rc.local may not be reliable. I don't know which order things happen in, but I know the route command won't work until the interface and networking come up. So if it doesn't seem to come up properly after a reboot, I would look at that first.

---

### Post by SomeITGuy on 2015-06-01
I've tried to add routes via the gui option but that didn't solve my problem.

> Using rc.local may not be reliable. I don't know which order things  happen in, but I know the route command won't work until the interface  and networking come up. So if it doesn't seem to come up properly after a  reboot, I would look at that first.

Thanks for that hint :), it still works after two test reboots now, but I will remember this one... ;)

---

### Post by JKyleOKC on 2015-06-01
If the *rc.local *race condition ever becomes a problem, you might try moving the code to the *if-up* script for the appropriate interface. I did that for setting up my *ip-tables* rules after running into the race condition here, and it works perfectly.

---

### Post by SomeITGuy on 2015-06-02
Ok, I will make a personal note about that, so if this ever becomes a problem, hopefully I will not search as long as the last time... ;)
Thanks! :)

---

