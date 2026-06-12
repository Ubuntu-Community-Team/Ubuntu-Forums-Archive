---
title: "Require help with setting up multiple network interfaces in my LAN."
date: 2011-09-24
forum: Server Platforms
---

### Post by Antoniya001 on 2011-09-24
Hello all,
 
I've recently tried to increase the security (and increase the throughput) of my network by trying to move external services of the server to a secondary external IP. But I've not been successfull. I think that there is a problem with the firewall configuration and quite possibly also a default gateway problem. 
 
To make my question more clear I've created jpegs to help understanding what I wish to do. 
 
In the old situation I've setup firestarter but that program simply won't do for the new situation. See pic for the old setup.
 
In the new situation I've uninstalled firestarter and installed fwbuilder which seems to be complex enough to do what I wish to do. I'm not a very big fan of command line I'm afraid, so I skipped ufw for setting up iptables.
 
Now when I go into my website in a browser, it won't connect. When I connect with inside ip from inside it works. (as long as there are no mydomain.nl references.) I can see all interfaces have an IP, so that is not it. If I disable the firewall AND the internal interface, the website will work from the outside.
 
Is this a gateway problem or a firewall problem ? Any help appreciated. How can you setup 2 default gateways ?
 
Ar
 
```

**[SIZE=3][FONT=Calibri]/etc/hosts             (new situation)[/FONT][/SIZE]**
 
[SIZE=3][FONT=Calibri]Aaa.bbb.ext.ip  IOSERV [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]127.0.0.1       localhost.localdomain   localhost[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]::1     IOSERV  localhost6.localdomain6 localhost6[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]192.168.1.199   IOSERV[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]# IOSERV is the internal name of the server, not the domain.nl name.[/SIZE][/FONT]
 
[SIZE=3][FONT=Calibri]# The following lines are desirable for IPv6 capable hosts[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]::1     localhost ip6-localhost ip6-loopback[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]fe00::0 ip6-localnet[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]ff00::0 ip6-mcastprefix[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]ff02::1 ip6-allnodes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]ff02::2 ip6-allrouters[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]ff02::3 ip6-allhosts[/FONT][/SIZE]
 
**[SIZE=3][FONT=Calibri]/etc/network/interfaces             (new situation)[/FONT][/SIZE]**
 
[SIZE=3][FONT=Calibri]auto lo[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]iface lo inet loopback[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]# The primary network interface[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]auto eth0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]iface eth0 inet dhcp[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]# The secondary network interface[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]auto eth1[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]iface eth1 inet dhcp[/FONT][/SIZE]
 
**[SIZE=3][FONT=Calibri]/etc/hostname[/FONT][/SIZE]**
 
[SIZE=3][FONT=Calibri]IOSERV[/FONT][/SIZE]

```

---

### Post by ian dobson on 2011-09-24
Hi,

Shouldn't your secondary interface eth1 have a fixed IP address or how does it get it's IP (dhcp?).

What does ifconfig show?

So that all the clients behind the server (on the second interface) use the server's IP address as their gateway.

Also whats stopping the router handing an ip address to the server's first ethernet port?

Try breaking the problem into smaller parts. 
Does the server get an IP address on both ports? and if so are they correct.
Does the modem route all data for the correct ip's to the correct systems (router and server).


Regards
Ian Dobson

---

### Post by Ryan Dwyer on 2011-09-24
I'm having trouble understanding how you're physically connecting the server to the 5 client machines. I assume you're plugging the server into both switches.

I would disable DHCP on the server and set everything statically. This includes both IP addresses and the default gateway. This would stop the router from giving you two internal addresses if that's what it's doing.

You can't have 2 default gateways. The default gateway of your server should be your modem's internal IP.

---

### Post by oldfred on 2011-09-24
I have not used this, but is this the type of configuration you want? This is a full Linux distribution to control secuity.

IPCop - Red, green, orange, blue networks
[http://www.ipcop.org/1.4.0/en/install/html/decide-configuration.html](http://www.ipcop.org/1.4.0/en/install/html/decide-configuration.html)

---

### Post by Antoniya001 on 2011-09-24
> I'm having trouble understanding how you're physically connecting the server to the 5 client machines. I assume you're plugging the server into both switches.
 
Yes, just as the drawing with the new setup shows. one goes into switch 1 (behind the modem), the second goes into switch 2 (behind the router).
 
> I would disable DHCP on the server and set everything statically. This includes both IP addresses and the default gateway. This would stop the router from giving you two internal addresses if that's what it's doing.

 
The external IP cannot be static, it is assigned by my ISP. The internal one is assigned by DHCP (of the router), but is always the same. The IP assignments are not really my problem. The interfaces always have the IPs that I want them to be.
 
> You can't have 2 default gateways. The default gateway of your server should be your modem's internal IP. 
 
This is what I first thought. But the internal networks gateway knows about the internal network, while the external network does not. So any trafic coming from external cannot be routed back thru the internal one. This is when my packets get lost I guess.
 
THX Ar

---

### Post by Antoniya001 on 2011-09-24
What does not seem to be understood is this : 
 
I have 2 paths to the internet. 
 
the first I wish to use for my personal stuff
 
the second I wish to use for the server
 
So they both have their own pathway to the internet. BUT I wish to be able to communicate to the server without having to go outside of my own network. Hence the second interface on the server. Which is then connected to the first path.
 
I found this :
 
[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)
 
That might be the ticket. Having default routes. When it comes IN thru eth1 it should also go OUT of eth1. Same for eth0.
 
Will try this tomorrow.
 
Any suggestions on the firewall settings ?
 
Ar

---

### Post by Antoniya001 on 2011-09-24
> **ian dobson said:**
>  Shouldn't your secondary interface eth1 have a fixed IP address or how does it get it's IP (dhcp?).
 
both dhcp, both have correct IP.
 
> So that all the clients behind the server (on the second interface) use the server's IP address as their gateway.
Server is NOT allowed to act as gateway. My network travel should go out of the router, not thru the server.
 
> Also whats stopping the router handing an ip address to the server's first ethernet port?
It is not on the same network ? It is before the router, not behind it.
 
> Try breaking the problem into smaller parts. 
Always good advice THX..
> Does the server get an IP address on both ports? and if so are they correct. YES
> Does the modem route all data for the correct ip's to the correct systems (router and server). This I can only hope so. I have absolutely NO control over my ISP's network. But I can only assume that since I get 2 different public IPs from them that it should not be a problem.
 
>  
What does ifconfig show?
 Will print it out tomorrow. I have gone back to the previous situation until I understand my problem and till then my website needs to be served. But I did not see any trouble there. As far as I can tell (I'm no guru, far from.)

---

### Post by Antoniya001 on 2011-09-24
> **oldfred said:**
> I have not used this, but is this the type of configuration you want? This is a full Linux distribution to control secuity.
 
IPCop - Red, green, orange, blue networks
[http://www.ipcop.org/1.4.0/en/install/html/decide-configuration.html](http://www.ipcop.org/1.4.0/en/install/html/decide-configuration.html)
 
This one also seems to only use a single entry point to the internet.
 
THX for the reply...

---

### Post by ian dobson on 2011-09-24
Hi,

The reason I asked if the server is getting the correct IP address is that my isp gives me 2 ip addresses and if I reboot the router that sits between the modem and the servers, the servers sometimes get the wrong/other IP address.

Maybe get the router and the clients working first, then the server. Your problem could well be that the router it not alowing the packets from the clients to be routed to the server on it's internet IP address.

Regards
Ian Dobson

---

### Post by Antoniya001 on 2011-09-24
My ISP hands out IP based on MAC address. Since server has different MAC than my ROUTER, they both get the right IP, always. 
 
If I disable the internal interface of the server everything works. I just cannot securely access the server, except locally, since I have to do it via the internet.
This is also a lot of trouble, since the server is usually headless.
 
THX for the suggestion,
 
Ar

---

### Post by patryk77 on 2011-09-24
Can you post the output of:

sudo route -n
sudo ifconfig

on the server, and the output of:

tracepath yourdomain.nl
on the client?

If you don't wish to advertise your (public) IPs, just change the first 2 bytes (i.e.: x.y.256.257)

If you are using a Windows client, just use "tracert" instead of tracepath.

If you do not have tracepath in Linux, it's in the iputils-tracepath package.

Edit: Or wouldn't you be better off simply using the LAN IP to access the server from the LAN?
You can simply install a DNS server (BIND: [https://help.ubuntu.com/10.04/serverguide/C/dns.html](https://help.ubuntu.com/10.04/serverguide/C/dns.html)) and have the server point the LAN clients to its internal address. Or edit HOSTS files like it was 1995.

---

### Post by koenn on 2011-09-24
> **Antoniya001 said:**
> Now when I go into my website in a browser, it won't connect. When I connect with inside ip from inside it works. (as long as there are no mydomain.nl references.) I can see all interfaces have an IP, so that is not it. If I disable the firewall AND the internal interface, the website will work from the outside.

you probably need yo look into how DNS works in your LAN

---

### Post by Antoniya001 on 2011-09-25
I have figured it out :
 
It is a default gateway problem. And I need 2 default gateways to make things work right.
 
The messages coming in on eth0 were being send out on eth1... etc...
 
Required ip static route...
 
Will post my solution later.. Now only to setup firewall correctly and go to a concert :-)
 
Ar
 
THX All..

---

### Post by HuckBerry on 2011-09-25
I came late to this thread, but you really should still check this link out.

I have the exact same setup with my server, except for 3 nics instead of two.
[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

Now, in practice I found that if I didn't need ALL of the traffic to be perfectly separated by which interface it entered on, then it was acceptable to just run
```

ip route del default via (internal gateway here)

```

which was enough to force all outbound traffic out of the external interface, which is my personal end goal. The link above will show you how to make it so that traffic entering via the external interface leaves out that interface as well.

---

### Post by Antoniya001 on 2011-09-26
THX ALL,
 
At Huckberry : I mentioned that link already.
 
I also used this post :
[http://www.debian-administration.org/article/Routing_for_multiple_uplinks/print](http://www.debian-administration.org/article/Routing_for_multiple_uplinks/print)
Which describes also how to store them.
 
So I ended up with :
Make sure that the following is installed :

apt-get install iproute
 
edit /etc/iproute2/rt_tables

#
# reserved values
#
255 local
254 main
253 default
0 unspec
#
# local
#
#1 inr.ruhep
200 adminlnk
201 uplink1
 
Setup the interfaces file. /etc/network/interfaces 
Both of the interfaces are assigned an IP by DHCP for me.
# The internal loopback interface
auto lo
iface lo inet loopback
 
# The primary network interface (adminlnk) IP = 192.168.1.xxx
auto eth0
iface eth0 inet dhcp
metric 20
# to add the route when the interface goes up :
post-up ip route add 192.168.1.0/24 dev eth0 src 192.168.1.xxx table adminlnk
post-up ip route add default via 192.168.1.1 dev eth0 table adminlnk
post-up ip rule add from 192.168.1.xxx/32 table adminlnk
post-up ip rule add to 192.168.1.xxx/32 table adminlnk
# to remove the route when the interface goes down :
post-down ip rule del from 192.168.1.xxx/32 table adminlnk
post-down ip rule del to 192.168.1.xxx/32 table adminlnk
 
# The secondary network interface (uplink1)
auto eth1
iface eth1 inet dhcp
metric 10
# to add the route when the interface goes up :
post-up ip route add all dev eth1 src xxx.yyy.21.243 table uplink1
post-up ip route add default via xxx.yyy.20.1 dev eth1 table uplink1
post-up ip rule add from xxx.yyy.21.243/32 table uplink1
post-up ip rule add to xxx.yyy.21.243/32 table uplink1
# to remove the route when the interface goes down :
post-down ip rule del from xxx.yyy.21.243/32 table uplink1
post-down ip rule del to xxx.yyy.21.243/32 table uplink1
 
To apply all settings :
ip route flush cache
ifup -a

---

### Post by Drenriza on 2011-09-26
It seams fairly simple what you want to do. But two questions.

What is it you want to accomplish with your network?
Why do your server have its own public ip? It's unnecessary, from what i can see.

Kind regards.

---

### Post by Antoniya001 on 2011-09-26
The server is also a samba/nfs server (internal) and the webtrafic and audio services that I have exposed to the outside take quite some bandwidth. So when copying on the internal network to the server I find that my copy speed is reduced from aprox 105/110MB/s to somewhere in the 80ies. (I'm doing much audio/video work.)
 
Just wanted to get rid of that. Plus it allows me to keep administration of the server on the internal network. And since the internal network has it's own IP, I can remote into a different IP than which the server is on. Which again is more secure. No ?
 
QUESTION :
Is there anything still wrong with my firewall ?  Second last rule is simply there (hopefully) to log what my server sends out by itself..!? portscan shows only http & https are open, but I need to know if I should do more...
 
(just wish to learn as much of administrating a linux network.)

---

### Post by Drenriza on 2011-09-26
> **Antoniya001 said:**
> The server is also a samba/nfs server (internal) and the webtrafic and audio services that I have exposed to the outside take quite some bandwidth. So when copying on the internal network to the server I find that my copy speed is reduced from aprox 105/110MB/s to somewhere in the 80ies. (I'm doing much audio/video work.)

On a Cisco router (as you can with many routers) you can setup NAT. So lets say you have a public ip of 80.0.0.1, just to pick one. And your server got ip 192.168.0.1.

Then you can set ip up so. If anyone tries to reach your server, they will use 80.0.0.1 you then setup a rule that says

"anyone that comes in on 80.0.0.1 and has port 80, will be re-directed to 192.168.0.1"
Just as an example. You can do this with any port for any service.

Also, who is it you want to secure yourself against from? The outside network? Should it be possible to reach the server from the WAN? It's hard to help with the info you give.

How do you wan't to protect yourself from something you don't know what is?

---

### Post by Antoniya001 on 2011-09-26
Since the server has been up, there has been a large increase of trafic trying to exploit ssh, remote desktop and other access posibilities. So yeah, I want protection from the outside world. I know I can use my router to route my trafic to just one interface, but (i'm paranoid probably) to increase protection, I prefer my outside services and my own personal trafic, to have seperate access to the internet. One that is locked down completely and just allows http(s) and the other where I can have my normal computing needs with open ports when required. 
 
So no errors in the firewall setup ?
 
Ar..

---

