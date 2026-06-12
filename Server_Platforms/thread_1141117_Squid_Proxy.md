---
title: "Squid Proxy"
date: 2009-04-28
forum: Server Platforms
---

### Post by jjfourtwenty on 2009-04-28
I'm trying to set up a Squid proxy server in ubuntu with the foloowing config:

2 NIC's -one is connected to the gateway router and other is connected to internal network

The idea is to use Squid to replace ISA and allow all users to connect through the internet via the squid server.

The issue is that I'm totaclly clueless in how to configure Squid. I've installed webmin which has helped in that it gives me a GUI but any more info would be most welcom.

Many Thanks

---

### Post by jjfourtwenty on 2009-04-28
bump...

---

### Post by moonpup on 2009-04-28
Although written for Red Hat / CentOS, you should be able to figure out how to apply this to Ubuntu.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid)

The main page has a lot of other goodies as well, so check there too!

---

### Post by jongers on 2009-05-08
I have successfully achieved this using Ubuntu 9.04 and Squid3 using this [howto]("http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html") just look into loading and saving iptables as this howto doesn't cover them that well for ubuntu. I think i outputted iptbales-save after running the fw.proxy to an execuable file and made it a startup script (also any config that refers to /etc/squid should be /etc/squid3).

The config files are excellent here and only require tweaking
If you are unfamiliar with command line only, can i suggest installing [Webmin]("http://www/webmin.com")

I hope this helps.

---

### Post by Weecka on 2009-05-14
Hello,

I'm trying to achieve same result as **jjfourtwenty**, but I've stucked at the same spot. My goal is to make Dansguardian + Squid proxy (transparent) work right. So whole config is: 

eth0 - connection from outside (other gateway router), with IP set in example 172.1.1.1;
eth1 - connection from internal network, with IP set in example 192.1.1.1.

I've added in squid.conf "http_port 3128 transparent" and it seems that squid works fine, gives no errors on start/restart.

Main problem is that I've tried tons of examples and tutorials about iptables, but nothing seems working for me. If I set browser proxy IP and port manualy (192.1.1.1:8080), then web pages is working fine and Dansguardian blocks improper content. But if I dont set browsers proxy IP, then it can't get any page.

Any ideas and suggestions how to solve this problem?

Many thanks in advance :)

---

