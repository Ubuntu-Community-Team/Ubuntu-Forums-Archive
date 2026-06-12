---
title: "What steps should I take to secure apache 2"
date: 2006-06-13
forum: Server Platforms
---

### Post by scrook on 2006-06-13
Hi,

I've installed apache 2 and php 5 on my ubuntu 6.06 install. I don't intend to have it accessible to the network. I just want to use it to be able to test websites I build locally.

Here is what i have done so far to try and keep this as secure as possible. I'm no expert so if there are better ways to do this or something I overlooked please tell me.

1. The computer is on a DSL connection but it is behind a NAT router

2. I have installed firestarter but I haven't changed any settings so my iptables settings are whatever firestarter does by default.

3. I have used the sygate security scan website to check for open ports and my box is not listening on port 80 according to this test.

4. I have tried to access the server from another computer on my LAN by typing http://<local ip address>/  and I was presented with an error page in the browser. (obviously I put the IP address the router assigned to my ubuntu box in place of <local ip address>

What other precautions should I be taking to secure this computer? I realize that just because I can't see the server running on my network doesn't mean someone smarter or more knowledgable than myself can't.

Thanks for taking the time to read this

Scott

---

### Post by DarthMandeep on 2006-06-13
If you installed Firestarter and have not allowed connections to port 80 the server should be completely blocked to other computers.

You could install nmap on another computer on your network and run a port scan to see if Firestarter is working as it should.

For a test environment, a proper firewall like Firestarter is all you really need.

---

### Post by Randomskk on 2006-06-13
In /etc/apache2/ports.conf, change Listen 80 to Listen 127.0.0.1:80 and restart the Apache server, Apache should now only listen on localhost.
Although I agree, it sounds like you are already pretty well set up.

---

### Post by LordHunter317 on 2006-06-14
You didn't need to install firestarter.  In fact, I would remove it.

Your test on that website was inconclusive.  It tested the security of the router and any port forwards.  It didn't examine that computer one bit.

Your test with the IP addresses was performed incorrectly.  To test it's network access, you must use it's real IP address.  If you want to check port forwards on the router, you need to do that externally.

But if you're behind that router, you are fine.

---

### Post by scrook on 2006-06-14
[quote=LordHunter317]
Your test with the IP addresses was performed incorrectly.  To test it's network access, you must use it's real IP address.  If you want to check port forwards on the router, you need to do that externally.
[/quote]

How do i find the real IP address of the computer? I ran /sbin/ifconfig eth1 in a terminal and got to following output:

eth1      Link encap:Ethernet  HWaddr 00:04:5A:7E:1C:82
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe7e:1c82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:632242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344979 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:857787909 (818.0 MiB)  TX bytes:23115328 (22.0 MiB)
          Interrupt:209 Base address:0x9000

The 'inet addr' is what i tested on the other computer on my LAN. I realize that this address is assigned by the router and the router has it's own address assigned by my ISP but beyond that I have no clue how it actually works.

---

### Post by LordHunter317 on 2006-06-14
My mistake, you did perform the test correctly.  I misread your statment as: you used the address of the router on the Internet.  My apologies.

---

