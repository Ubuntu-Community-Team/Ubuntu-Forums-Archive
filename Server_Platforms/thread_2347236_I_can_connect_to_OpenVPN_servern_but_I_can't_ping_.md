---
title: "I can connect to OpenVPN servern but I can't ping or access to my computers"
date: 2016-12-22
forum: Server Platforms
---

### Post by cazz on 2016-12-22
hi
Last time I did use openVPN I got it to work but it was sometime now
Now I trying to make a new OpenVPN server and I did use this guide here

[https://www.cyberciti.biz/faq/howto-setup-openvpn-server-on-ubuntu-linux-14-04-or-16-04-lts/](https://www.cyberciti.biz/faq/howto-setup-openvpn-server-on-ubuntu-linux-14-04-or-16-04-lts/)

I have it install and what I can see even the client can connect to the server (the client got a 10.8.0.2) address and it say Everything is ok

I can ping my server (192.168.1.7) but I can't ping my other computers in 192.168.1.x

I guess I have to routing something but what and where?

I have work with Linux sometime now but this is new for me

---

### Post by darkod on 2016-12-22
Is the 192.168.1.x on the server side or the client side?

Here is one recent thread about openvpn, it might not be 100% identical to your case but you can use part of the discussion to modify your setup. Then ask for the things that are missing for your specific setup...
[https://ubuntuforums.org/showthread.php?t=2347032](https://ubuntuforums.org/showthread.php?t=2347032)

---

### Post by SeijiSensei on 2016-12-22
I'll ask my standard question about situations like this:  Did you enable packet forwarding by removing the hash mark from "net.ipv4.ip_forward=1" in /etc/sysctl.conf on the server?  If not, do that, reboot, and see if things work better.

---

### Post by cazz on 2016-12-22
thanks for the fast replay
is on the server side
when I try to run openVPN I use 4G access so I don't have any access to my local Network to be sure that I got it right

mm yes I have try to read and understand but not so easy when this is a little new for me


The ip_forward is a 1 so that is ok

I was thinking maybe some kind of routing I have problem with, I can pin the local LAN serverns IP address and that is 192.168.1.7

---

### Post by SeijiSensei on 2016-12-22
When you say "it is a 1," it is always a one in the file.  What matters is whether there's a hash mark at the beginning of the line.  
```
#net.ipv4.ip_forward=1
```
If so, remove the hash mark and reboot.
```
net.ipv4.ip_forward=1
```
The default is zero, meaning packets are not forwarded between interfaces on the machine.  A hash mark ("#") means the line is treated as a comment and ignored.

---

### Post by cazz on 2016-12-22
I have this and I have reboot

```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
```

 still same problem, I can example not ping 192.168.1.3

not even my router does it ping to 192.168.1.1

---

### Post by volkswagner on 2016-12-22
You need to add your local network to the server config and advertise that so clients know to route 192.168.1.0/24 via the tun interface.

```
push 'route 192.168.1.0 255.255.255.0'
```

You'll also need to set a route on your LAN router for tun traffic.

The above came from this [link]("https://openvpn.net/index.php/open-source/documentation/howto.html#scope").

Once you get this working the way your want, you should consider changing your LAN subnet to a more
unique scope. 192.168.1.0/24 is very common. If you try to connect to your VPN (while not using 4G) for
example at a free WiFi hotSpot or your friends house, you'll may end up having 192.168.1.0/24 on both sides
of the tunnel which will cause routing problems.  See this [link for choosing subnets]("https://openvpn.net/index.php/open-source/documentation/howto.html#numbering").

---

### Post by cazz on 2016-12-23
I have got it to work now

I did follow the firewall setup from this page :)
[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04)

---

