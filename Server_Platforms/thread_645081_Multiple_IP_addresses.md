---
title: "Multiple IP addresses"
date: 2007-12-19
forum: Server Platforms
---

### Post by hwheeler43 on 2007-12-19
:) I am wanting to run two Web Sites on the same server.  I will have two static IP addresses from my internet provider.  Can I do this with a single NIC?

---

### Post by tgilber1 on 2007-12-19
yes, you should be able to do this setup using the ifconfig command or through the network

Assuming eth0 is the device name

to bring up interface

sudo ifconfig eth0:1 192.168.0.2 netmask 255.255.255.0
sudo ifconfig eth0:2 192.168.1.2 netmask 255.255.255.0

next you need to build a route

sudo route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.1
sudo route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1


to bring down

sudo ifconfig eth0:1 down
sudo ifconfig eth0:2 down


sudo route del -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.1
sudo route del -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1

You can throw this info into a shell script and call it during start up using the rc.local.  There are other ways to call the script.  Hence, I will let you find the best way that suits you best.

Remember, if you use this info in a script.  Leave the sudo off, since root will calling the script.

Hope this info helps!

---

### Post by now-new on 2007-12-19
I am not sure but:

One: you could run them by name just one IP.
Two: You'll have to have multiple IP's which means that you could make 2 o up to 254 alias
you can check apaches website:
--- [http://httpd.apache.org/docs/2.2/vhosts/ip-based.html](http://httpd.apache.org/docs/2.2/vhosts/ip-based.html)
or check this out for alias
--- [http://www.cyberciti.biz/faq/linux-creating-or-adding-new-network-alias-to-a-network-card-nic/](http://www.cyberciti.biz/faq/linux-creating-or-adding-new-network-alias-to-a-network-card-nic/)

---

### Post by hwheeler43 on 2007-12-20
:)Thanks all.  I am doing a lot of reading and playing around with my desktop version at home.  I have now installed Ubuntu as a duel boot on one of my laptops and a desktop.  Very impressed so far.  I still have a lot to learn.  I worked with unix many years ago. I have purchased a couple of books although I believe you can find most of what you need online.  Thanks again...

---

### Post by now-new on 2007-12-20
The same happen to me when I wanted to start learning C I bought like 7 books and started reading, then I thought that I hadn't learn much so I took the class to my surprise they thought me less than I knew and now I see that I find more online than in 7 books or at school
---->>>we all keep learning.

thank to ubuntuforums.org creators
      :popcorn:

---

### Post by rsw686 on 2007-12-22
Yes you only need one NIC. I would suggest a hardware firewall in front of the box. You either can bridge it and pass through the IPs or use 1:1 NAT.

You really only need one public IP as only as your not going to use HTTPS on both websites. You can configure the apache virtual hosts based on hostname vs IP.

---

