---
title: "Ubuntu server advanced networking"
date: 2010-06-13
forum: Server Platforms
---

### Post by Rich43 on 2010-06-13
I am thinking of converting our server from Windows server 2008 to Ubuntu server. It serves files, provides internet, hosts gameservers etc.

I tried this before and hit a brick wall with networking.

The server has 4 gigabit ethernet ports,
eth0 - provides internet from router
eth1-3 - acts as a switch and sends high speed gigabit (and internet) to all 3 desktops.

I used brctl to bridge all the connections but none of the desktops can connect into it as if traffic is being blocked.

On Windows, I just bridge all the connections and it works fine. I'd like a similar or better setup on linux.

---

### Post by vandorjw on 2010-06-13
If you do, let us know how it went.
And if you need any help specifically, post your questions.

I also have a windows 2008 R2 server, that I use as a gaming server, web-server, and for file sharing. Sharing between windows is painless but with Mac and Linux it doesn't always complete the connection.

---

### Post by Ryan Dwyer on 2010-06-13
You probably haven't configured the server to forward packets (ie. act as a router).

Please post the output of: cat /proc/sys/net/ipv4/ip_forward

0 means it's not forwarding, 1 means it is. If it's not forwarding, you can type:
sudo bash
echo 1 > /proc/sys/net/ipv4/ip_forward

That will make it forward until the machine is rebooted. To make it forward permanently, add net.ipv4.ip_forward = 1 to /etc/sysctl.conf.

---

### Post by Rich43 on 2010-06-26
I got it routing traffic using bridge tools and above advice but I cannot access the internet on the server itself as the connection is part of the bridge. 
Do I need to seperate the connection that provides internet from the bridge?
 If so, how would I forward internet traffic to the bridge?

I had to give the bridge a static IP and uninstall network manager since I'm keeping desktop on it.

---

### Post by Ryan Dwyer on 2010-06-26
You probably need to play with the route command. I'm not very familiar with it. Try Googling something like "how to add a default route".

---

