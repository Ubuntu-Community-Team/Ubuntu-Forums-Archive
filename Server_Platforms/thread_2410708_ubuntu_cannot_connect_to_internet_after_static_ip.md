---
title: "ubuntu cannot connect to internet after static ip"
date: 2019-01-19
forum: Server Platforms
---

### Post by christophe195 on 2019-01-19
Hello,

I need to give my ubuntu server 2 static ip's. I use 2 different networks, on one is all the network stuff like pc, phone, tv,... on the other network i have the IOT device's (no DHCP and no default gateway). After setting it all up, i did a network test but i do not got connection with google or other website's. What do i wrong? i do not see the problem.

my netplan
```


network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      addresses: [192.168.0.11/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [1.1.1.1, 1.0.0.1]
      dhcp4: no
      dhcp6: no

```

my interface's (without this the network port's are DOWN on boot)
```


# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d


auto eth0
iface eth0 inet static
address 192.168.0.11


# Netwerk interface IOT
auto eth1
iface eth1 inet static
address 192.168.11.1



```

---

### Post by SeijiSensei on 2019-01-19
Did you edit /etc/sysctl.conf to enable packet forwarding?

As a quick test use:

```
echo '1' > /proc/sys/net/ipv4/ip_forward
```

then see if you can connect.  If that fixes the problem, edit /etc/sysctl.conf and remove the hash mark from 

```
net.ipv4.ip_forward=1
```

and reboot. 

Packet forwarding across interfaces is disabled by default in most distributions as a security measure.

Also, let's see the results of the command "route -n" and "sudo iptables -t nat -L -nv".

---

### Post by christophe195 on 2019-01-19
Hello SeijiSensei

The quick test did not work.

the output is:
```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1



```
and
```



Chain PREROUTING (policy ACCEPT 13533 packets, 2794K bytes)
 pkts bytes target     prot opt in     out     source               destination 


Chain INPUT (policy ACCEPT 5489 packets, 934K bytes)
 pkts bytes target     prot opt in     out     source               destination 


Chain OUTPUT (policy ACCEPT 76506 packets, 4591K bytes)
 pkts bytes target     prot opt in     out     source               destination 


Chain POSTROUTING (policy ACCEPT 76521 packets, 4596K bytes)
 pkts bytes target     prot opt in     out     source               destination 



```

---

### Post by SeijiSensei on 2019-01-19
OK, so you don't have a default gateway on the box.  Unless you only want to pass traffic between the two networks, you'll need a default route that points toward your gateway router. Otherwise you cannot reach IP addresses outside your network like Google.  Is the router at 192.168.0.1? If so, try

```
sudo ip route add default via 192.168.0.1
```

to set up the default route on the fly.  (Obviously if the router is at a different address you would use that instead.) You'll have to edit the netplan files to make that permanent.

Enabling packet forwarding should have enabled pinging between the two networks.  Did you try that?

---

### Post by christophe195 on 2019-01-19
Sorry, i think you don't get what i'm tray to do.

I have a home network with dhcp (192.168.0.100 - 192.168.0.254) and default gateway is on ip 192.168.0.1.

Now i have a device with 2 network interfaces. One needs to be ip 192.168.0.11, so i can reatch it from the home network (and the internet if i want to). The other port is for a new network (without internet) and only static ip's (192.168.11.*)
On the offline network i want to add network devices for iot and manage them with openhab or something.

On this momment sudo apt-get update can not reacht the ubuntu domain.

---

### Post by The Cog on 2019-01-19
I think  SeijiSensei understands very well. 
But not only does your forwarding PC need a default route like SeijiSensei says, all the devices on 192.168.11.* need a default route via whatever the IP address of your forwarding PC.
Also, unless your PC is using masquerading NAT, the router will need a route to 192.168.11.0/24 via 192.168.0.11 so it knows where to send replies from the internet.
Every device needs to know where to send packets that are not for a directly connected network.

---

### Post by christophe195 on 2019-01-19
@SeijiSensei
yes i did but without luck:

```
sudo apt-get update                                        Err:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic InRelease  Temporary failure resolving 'ports.ubuntu.com'
Err:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates InRelease
  Temporary failure resolving 'ports.ubuntu.com'
Err:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security InRelease
  Temporary failure resolving 'ports.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/bionic/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/bionic/InRelease)  Temporary failure resolving 'ports.ubuntu.com'
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/bionic-updates/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/bionic-updates/InRelease)  Temporary failure resolving 'ports.ubuntu.com'
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/bionic-security/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/bionic-security/InRelease)  Temporary failure resolving 'ports.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

@The Cog
it is not realy forwarding, for example: i have a arduino on ip 192.168.11.6 that get's json from a webserver on 192.168.11.1, when it gets a {power:1} the light goes on. I can go to the webserver 192.168.0.11 with my phone and turn the light's on with a button on the webpage. Do i need to forward for this?

---

### Post by The Cog on 2019-01-20
You don't need forwarding for that, if I understand you right. The web server is on the PC which is directly connected to both networks. It's an application on the PC that 1: gets the web connection (192.168.0.) and command from you, and 2: makes a connection (192.168.11.) to the arduino. In both these cases, the PC and what it's talking to are on the same network, so it already knows where to send packets (both locally connected networks are in the routing table). You don't need a default route for that, and you don't need IP forwarding for that either.

So I think I understand now that your IOT device does not need a default route either, as it only talks to the PC.

On the other hand, your PC needs a default route if it is to talk to things (like the Ubuntu repositories) on the internet. You posted the output of **route -n** before you used "sudo ip route add...". I wonder if that worked. Please try the command **ping -c4 8.8.8.8** and see if you can talk to the internet without using DNS. If this works then it would seem that you have a DNS name resolution problem and we can work on that. 

If the ping doesn't work, run **route -n** again to make sure the route got added properly (and post the results).

---

### Post by christophe195 on 2019-01-20
Ok, the ping seems to work but "apt-get update" not. The gateway keeps 0.0.0.0

[IMG]https://i.snag.gy/DLb7H6.jpg[/IMG]

---

### Post by howefield on 2019-01-20
Moved to the "*Server Platforms*" forum.

---

### Post by SeijiSensei on 2019-01-21
You have a name resolution problem.  Where is this update being run?  On the machine that has

```

      nameservers:
        addresses: [1.1.1.1, 1.0.0.1]

```

On that machine, try "host google.com 1.1.1.1".  Does it return something like 
```
google.com has address 172.217.11.46
```
as it does for me?

What if you use 8.8.8.8 and 8.8.4.4?

---

### Post by christophe195 on 2019-01-21
yes, the update is on that device, i have chante it to 8.8.8.8 and 8.8.4.4.

after reboot running your code give's me:
> root@OrangePizero:~# host google.com 1.1.1.1Using domain server:
Name: 1.1.1.1
Address: 1.1.1.1#53
Aliases:


google.com has address 216.58.211.110
google.com has IPv6 address 2a00:1450:400e:80a::200e
google.com mail is handled by 50 alt4.aspmx.l.google.com.
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.
google.com mail is handled by 40 alt3.aspmx.l.google.com.

but when i ssh "sudo apt-get update":
> Err:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic InRelease  Temporary failure resolving 'ports.ubuntu.com'
Err:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates InRelease
  Temporary failure resolving 'ports.ubuntu.com'
Err:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security InRelease
  Temporary failure resolving 'ports.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/bionic/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/bionic/InRelease)  Temporary failure resolving 'ports.ubuntu.com'
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/bionic-updates/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/bionic-updates/InRelease)  Temporary failure resolving 'ports.ubuntu.com'
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/bionic-security/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/bionic-security/InRelease)  Temporary failure resolving 'ports.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.


Thanks that you want to help me with this, i really appreciate it.
[COLOR=#212121][FONT=arial]I really appreciate this[/FONT][/COLOR][COLOR=#212121][FONT=arial]I really appreciate this[/FONT][/COLOR][COLOR=#212121][FONT=arial]I really appreciate this[/FONT][/COLOR][COLOR=#212121][FONT=arial]I really appreciate this[/FONT][/COLOR][COLOR=#212121][FONT=arial].I really appreciate this[/FONT][/COLOR]

---

### Post by SeijiSensei on 2019-01-23
Try this experiment:

```

cd /etc
sudo mv resolv.conf resolv.conf.link
sudo echo 'nameserver 8.8.8.8' > resolv.conf

```

Now see if you can resolve names.  If not, then delete this new resolv.conf and reverse the mv command.

---

### Post by christophe195 on 2019-01-27
Thanks:

after reboot i did this:

```

[COLOR=#000000]sudo ip route add default via 192.168.0. 
sudo echo 'nameserver 8.8.8.8' > resolv.conf
```[/COLOR]
> Hit:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic InReleaseHit:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates InRelease
Hit:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security InRelease
Reading package lists... Done
E: Release file for [http://ports.ubuntu.com/ubuntu-ports/dists/bionic/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/bionic/InRelease) is not valid yet (invalid for another 88d 7h 11min 31s). Updates for this repository will not be applied.
E: Release file for [http://ports.ubuntu.com/ubuntu-ports/dists/bionic-updates/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/bionic-updates/InRelease) is not valid yet (invalid for another 363d 17h 22min 27s). Updates for this repository will not be applied.
E: Release file for [http://ports.ubuntu.com/ubuntu-ports/dists/bionic-security/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/bionic-security/InRelease) is not valid yet (invalid for another 363d 17h 22min 10s). Updates for this repository will not be applied.


---

### Post by SeijiSensei on 2019-01-27
What version of Ubuntu Server is this?  18.04 LTS or 16.04 LTS?  You should only use LTS versions for servers.

---

### Post by christophe195 on 2019-01-28
It is 18.04 LTS but i think i have change something for updating to the 18.04LTS version

---

### Post by awebdev17 on 2020-01-21
If OP requires the interfaces file as mentioned in the first post, and in order to make the progress he has so far he needs to manually add the route and nameserver, then maybe Netplan isn't working as expected. 

We can simplify this problem by finishing up the interfaces file to include the gateway and nameserver, rebooting, then testing the internet connection. Put this in your interfaces file and reboot.

[COLOR=#212529][FONT=Inconsolata]iface eth0 inet static[/FONT][/COLOR]
[COLOR=#212529][FONT=Inconsolata]address 192.168.0.11[/FONT][/COLOR]
[COLOR=#212529][FONT=Inconsolata]netmask 255.255.255.0[/FONT][/COLOR]
[COLOR=#212529][FONT=Inconsolata]gateway 192.168.0.1
dns-nameservers 8.8.8.8
[/FONT][/COLOR]
if "ping www.google.com" and "host ports.ubuntu.com" comes back happy after that then you have a repo issue to work on instead of a network issue.

---

### Post by coffeecat on 2020-01-21
The OP has not logged into the forum for nearly a year.

Back to sleep old thread. Thread closed.

---

