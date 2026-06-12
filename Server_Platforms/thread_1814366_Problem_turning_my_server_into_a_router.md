---
title: "Problem turning my server into a router"
date: 2011-07-29
forum: Server Platforms
---

### Post by That Guy Is Here on 2011-07-29
Hi all,

Im having problems turning my server into a gateway. I followed this guide- [http://www.server-servers.com/ubuntu-router-network-gateway/](http://www.server-servers.com/ubuntu-router-network-gateway/) - and I cant get it to work. In my server I installed two new gigabit network cards, and I cant seem to be able to get it to work. Any help would be greatly appreciated :)

Thanks,
Joshua

---

### Post by volkswagner on 2011-07-29
I think your post is lacking description.

What is working?  

What is not working?

Can the server connect to the internet?

What is the output of the following commands
```
host google.com
```
```
route
```
```
ifconfig
```
```
cat /etc/network/interfaces
```

What type of internet connection do you have?

---

### Post by kwamaking on 2011-07-30
I think I know what you mean.  You're wanting to a windows styled "internet connection sharing" ?

If so you're in luck because I use a server for my 360 and I do ICS through that same box. 

This article helped me a lot:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Here's an example of how I forwarded everything from my Eth port to my Wifi. 



Setting up the iptables

```
 sudo iptables -A FORWARD -o wlan1 -i eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
 sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
 sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
```
Saving iptables

 ```
sudo iptables-save | sudo tee /etc/iptables.sav
```

Add the following to /etc/rc.local
```
 iptables-restore < /etc/iptables.sav
 sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

Add the following to /etc/sysctl.conf
```
 net.ipv4.conf.default.forwarding=1
 net.ipv4.conf.all.forwarding=1
```
Restart Networking

```
 /etc/init.d/networking restart
```

---

