---
title: "How to Optimize your Internet Connection using MTU and RWIN"
date: 2008-07-27
forum: Tutorials
---

### Post by caljohnsmith on 2008-07-27
[SIZE="4"]**TCP Maximum Transmission Unit (MTU)**[/SIZE]

The TCP Maximum Transmission Unit (MTU) is the maximum size of a single TCP packet that can pass through a TCP/IP network. 

An easy way to figure out what your MTU should be is to use ping where you specify the payload size:
```
ping -s [COLOR="Red"]1464[/COLOR] -c1 google.com
```
Note though that the [COLOR="Blue"]total IP packet size[/COLOR] will be 1464+28=[COLOR="Blue"]1492[/COLOR] bytes since there is [COLOR="Blue"]28 bytes of header info[/COLOR]. Thus if the packet gets fragmented for payload above 1464, then you should set your [COLOR="Blue"]MTU=1492[/COLOR]. Ping will let you know when it becomes fragmented with something like the following:
```
john@TECH5321:~$ ping -s [COLOR="Red"]1464[/COLOR] -c1 google.com
PING google.com (72.14.207.99) 1464(1492) bytes of data.
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=237 (truncated)

--- google.com ping statistics ---
[COLOR="Red"]1 packets transmitted, 1 received[/COLOR], 0% packet loss, time 0ms
rtt min/avg/max/mdev = 118.672/118.672/118.672/0.000 ms
john@TECH5321:~$ ping -s [COLOR="Red"]1465[/COLOR] -c1 google.com
PING google.com (64.233.167.99) 1465(1493) bytes of data.
From adsl-75-18-118-221.dsl.sndg02.sbcglobal.net (75.18.118.221) icmp_seq=1 [COLOR="Red"]Frag needed and DF set (mtu = 1492)
[/COLOR]
--- google.com ping statistics ---
[COLOR="Red"]1 packets transmitted, 0 received[/COLOR], +1 errors, 100% packet loss, time 0ms
```
In other words, to find your correct MTU, you would first start with a small packet size, and then gradually increase it until you see fragmentation; the cutoff point will be what to use for your MTU (using the formula payload + 28 = MTU). Note in the first case shown above where the payload size is 1464, the packet was transmitted fine, but in the second case where the payload size is 1465, ping complains "Frag needed"; to clarify, that means any packet with a payload of 1464 or less will be sent just fine, but a payload size of 1465 or above will end up being fragmented. Therefore, 1464 is the *maximum* payload, and that means the MTU is 1464+28=1492.

To set the MTU temporarily (will be lost after a reboot), you can do:
```
sudo ifconfig <interface> mtu 1492
```
Note that unfortunately some NICs do not allow you to change their MTU. You can use "ifconfig" by itself to see what the MTU is for your NIC and whether the MTU changes when you use the above command.
Or to make the change permanent, you can add it to [COLOR="Blue"]/etc/network/interfaces[/COLOR]:
```
gksudo gedit /etc/network/interfaces
```
And then add "mtu <value>" in it for the particular interface. Here's an example of mine that uses my wireless interface wlan0:
```
iface wlan0 inet static
address 192.168.1.23
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid John's Home WLAN
[COLOR="Red"]mtu 1492[/COLOR]

```

[SIZE="4"][B]TCP Receive Window (RWIN)
[/B][/SIZE]

In computer networking, [COLOR="Blue"]RWIN (TCP Receive Window)[/COLOR] is the maximum amount of data that a computer will accept before acknowledging the sender. In practical terms, that means when you download say a 20 MB file, the remote server does not just send you the 20 MB continuously after you request it. When your computer sends the request for the file, your computer tells the remote server what your RWIN value is; the remote server then starts streaming data at you until it reaches your RWIN value, and then the server waits until your computer acknowledges that you received that data OK. Once your computer sends the acknowledgement, then the server continues to send more data in chunks of your RWIN value, each time waiting for your acknowledgment before proceeding to send more.

Now the crux of the problem here is with what is called [COLOR="Blue"]latency[/COLOR], or the amount of time that it takes to send and receive packets from the remote server. Note that latency will depend not only on how fast the connection is between you and the remote server, but it also includes all additional delays, such as the time that it takes for the server to process your request and respond. You can easily find out the latency between you and the remote server with the [COLOR="Blue"]ping[/COLOR] command. When you use ping, the time that ping reports is the [COLOR="Blue"]round-trip time (RTT)[/COLOR], or latency, between you and the remote server. 

When I ping google.com, I typically get a latency of 100 msec. Now if there were no concept of RWIN, and thus my computer had to acknowledge every single packet sent between me and google, then transfer speed between me and them would be simply the (packet size)/RTT. Thus for a maximum sized packet (my MTU as we learned above), my transfer speed would be:
```
1492 bytes/.1 sec = 14,920 B/sec or 14.57 KiB/sec
```
That is pathetically slow considering that my connection is 3 Mb/sec, which is the same as 366 KiB/sec; so I would be using only about 4% of my available bandwidth. Therefore, we use the concept of RWIN so that a remote server can stream data to me without having to acknowledge every single packet and slow everything down to a crawl. 

Note that the TCP receive window (RWIN) is independent of the MTU setting. RWIN is determined by the [COLOR="Blue"]BDP (Bandwidth Delay Product)[/COLOR] for your internet connection, and [COLOR="Blue"]BDP[/COLOR] can be calculated as:
```
BDP = max bandwidth of your internet connection (Bytes/second) * RTT (seconds)
```
Therefore RWIN does not depend on the TCP packet size, and TCP packet size is of course limited by the MTU (Maximum Transmission Unit).

Before we change RWIN, use the following command to get the kernel variables related to RWIN:
```
sysctl -a 2> /dev/null | grep -iE "_mem |_rmem|_wmem"
```
Note the space after the _mem is deliberate, don't remove it or add other spaces elsewhere between the quotes.

You should get the following three variables:
```
net.ipv4.tcp_rmem = 4096    87380    2584576        
net.ipv4.tcp_wmem = 4096    16384    2584576
net.ipv4.tcp_mem = 258576    258576    258576
```
The variable numbers are in bytes, and they represent the minimum, default, and maximum values for each of those variables.
```
net.ipv4.tcp_rmem = Receive window memory vector
net.ipv4.tcp_wmem = Send window memory vector
net.ipv4.tcp_mem = TCP stack memory vector
```
Note that there is no exact equivalent variable in Linux that corresponds to RWIN, the closest is the [COLOR="Blue"]net.ipv4.tcp_rmem[/COLOR] variable. The variables above control the actual memory usage (not just the TCP window size) and include memory used by the socket data structures as well as memory wasted by short packets in large buffers. The maximum values have to be larger than the BDP (Bandwidth Delay Product) of the path by some suitable overhead. 

To try and optimize RWIN, first use ping to send the maximum size packet your connection allows (MTU) to some distant server. Since my MTU is 1492, the ping command payload would be 1492-28=1464. Thus:
```
john@TECH5321:~$ ping -s 1464 -c5 google.com
PING google.com (64.233.167.99) 1464(1492) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=237 (truncated)
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=237 (truncated)
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=237 (truncated)
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=4 ttl=237 (truncated)
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=5 ttl=237 (truncated)

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 101.411/[COLOR="Red"]102.699[/COLOR]/105.723/1.637 ms

```
Note though that you should run the above test several times at different times during the day, and also try pinging other destinations. You'll see RTT might vary quite a bit.

But for the above example, the RTT average is about [COLOR="Blue"]103 msec[/COLOR]. Now since the maximum speed of my internet connection is 3 Mbits/sec, then the BDP is:
```
(3,000,000 bits/sec) * (.103 sec) * (1 byte/8 bits) = 38,625 bytes
```
Thus I should set the default value in [COLOR="Blue"]net.ipv4.tcp_rmem[/COLOR] to about [COLOR="Blue"]39,000[/COLOR]. For my internet connection, I've seen RTT as bad as [COLOR="Blue"]500 msec[/COLOR], which would lead to a BDP of [COLOR="Blue"]187,000 bytes[/COLOR]. Therefore, I could set the max value in [COLOR="Blue"]net.ipv4.tcp_rmem[/COLOR] to about 187,000. The values in [COLOR="Blue"]net.ipv4.tcp_wmem[/COLOR] should be the same as [COLOR="Blue"]net.ipv4.tcp_rmem[/COLOR] since both sending and receiving use the same internet connection. And since [COLOR="Blue"]net.ipv4.tcp_mem[/COLOR] is the maximum total memory buffer for TCP transactions, it is usually set to the the max value used in [COLOR="Blue"]net.ipv4.tcp_rmem[/COLOR] and [COLOR="Blue"]net.ipv4.tcp_wmem[/COLOR].

And lastly, there are two more kernel TCP variables related to RWIN that you should set:
```
sysctl -a 2> /dev/null | grep -iE "rcvbuf|save"
```
which returns:
```
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1

```
Note enabling [COLOR="Blue"]net.ipv4.tcp_no_metrics_save[/COLOR] (setting it to 1) means have Linux optimize the TCP receive window dynamically between the values in [COLOR="Blue"]net.ipv4.tcp_rmem[/COLOR] and [COLOR="Blue"]net.ipv4.tcp_wmem[/COLOR]. And enabling [COLOR="Blue"]net.ipv4.tcp_moderate_rcvbuf[/COLOR] removes an odd behavior in the 2.6 kernels, whereby the kernel stores the slow start threshold for a client between TCP sessions. This can cause undesired results, as a single period of congestion can affect many subsequent connections.

Before you change any of the above variables, try going to [http://www.speedtest.net](http://www.speedtest.net) or a similar website and check the speed of your connection. Then temporarily change the variables by using the following command with your own computed values:
```
sudo sysctl -w net.ipv4.tcp_rmem="4096 39000 187000" net.ipv4.tcp_wmem="4096 39000 187000" net.ipv4.tcp_mem="187000 187000 187000" net.ipv4.tcp_no_metrics_save=1 net.ipv4.tcp_moderate_rcvbuf=1
```
Then retest your connection and see if your speed improved at all.

Once you tweak the values to your liking, you can make them permanent by adding them to [COLOR="Blue"]/etc/sysctl.conf[/COLOR] as follows:
```
net.ipv4.tcp_rmem=4096 39000 187000
net.ipv4.tcp_wmem=4096 39000 187000
net.ipv4.tcp_mem=187000 187000 187000
net.ipv4.tcp_no_metrics_save=1
net.ipv4.tcp_moderate_rcvbuf=1
```
And then do the following command to make the changes permanent:
```
sudo sysctl -p
```

If everything went well, now you can enjoy a faster internet connection! :)

---

### Post by ferd on 2008-07-31
Thank you. Brilliant.:guitar:

---

### Post by pitirpol on 2008-12-01
Hi. How can I set 
net.ipv4.tcp_no_metrics_save = 0
net.ipv4.tcp_moderate_rcvbuf = 1

to
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1

Thanks!

---

### Post by fireman300 on 2009-04-18
I have had mixed success with this method. I had two Kubuntu boxes one running 8.04 stock with the recommended updates and one running 8.10 with a generic x86_64 2.6.29 kernel (from kernel.org not in the repos). Both computers are served by the same ISP but at two different locations. When running speedtest from speakeasy both would have an upload speed twice of what the download was. 

> from the 8.10 system:
Download Speed: 1620 kbps (202.5 KB/sec transfer rate)
Upload Speed: 3163 kbps (395.4 KB/sec transfer rate)

I tried the above method and achieved great success on the 8.04 system but the 8.10 system just doesn't seem to change. I tried various combinations of max, min, and default BDP values with no luck. I also referenced 
[http://www.ubuntu-unleashed.com/2008/05/howto-tweak-your-internet-connection.html]("http://www.ubuntu-unleashed.com/2008/05/howto-tweak-your-internet-connection.html")
and 
[http://ubuntuforums.org/showthread.php?t=251509]("http://ubuntuforums.org/showthread.php?t=251509")

```
user@Jeff-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0c:76:96:a1:da
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe96:a1da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:93879482 (93.8 MB)  TX bytes:81355184 (81.3 MB)
          Interrupt:16 Base address:0x6f00

```

```
user@Jeff-desktop:~$ sysctl -a 2> /dev/null | grep -iE "_mem |_rmem|_wmem"
net.ipv4.tcp_mem = 187000       187000  187000
net.ipv4.tcp_wmem = 4096        39000   187000
net.ipv4.tcp_rmem = 4096        39000   187000
net.ipv4.udp_mem = 187000       187000  187000
net.ipv4.udp_rmem_min = 4096
net.ipv4.udp_wmem_min = 4096
```

Does anybody else have any suggestions?

---

### Post by caljohnsmith on 2009-04-20
> **fireman300 said:**
> I have had mixed success with this method. I had two Kubuntu boxes one running 8.04 stock with the recommended updates and one running 8.10 with a generic x86_64 2.6.29 kernel (from kernel.org not in the repos). Both computers are served by the same ISP but at two different locations. When running speedtest from speakeasy both would have an upload speed twice of what the download was. 
> from the 8.10 system:
Download Speed: 1620 kbps (202.5 KB/sec transfer rate)
Upload Speed: 3163 kbps (395.4 KB/sec transfer rate)


Something isn't quite right if you are getting a faster upload speed compared to your download speed. Do you have a DSL connection, or what exactly is your internet connection? If you have a DSL connection, please connect to your DSL modem through your web browser and let me know what the DSL modem's maximum download/upload speeds are theoretically supposed to be. If you don't know offhand how to access your DSL modem setup through a web browser, normally you just type its local IP address into your browser, such as 192.168.0.1, 192.168.1.254, etc. depending on how yours is setup. Or you can manually find the DSL modem's IP address by doing a "tracepath" to some arbitrary website (for instance google) like the following example for my computer:
```
john@TECH3142:~/Desktop$ tracepath www.google.com
 1:  TECH3142.local (192.168.1.30)                          0.405ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              3.985ms asymm 36 
 1:  192.168.1.1 (192.168.1.1)                              3.861ms asymm 36 
 2:  75.42.179.167 (75.42.179.167)                          2.371ms pmtu 1492
 2:  **192.168.0.1** (192.168.0.1)                              3.005ms 
 3:  75.42.179.254 (75.42.179.254)                         48.037ms 
 4:  dist2-vlan50.sndg02.pbi.net (63.200.206.131)          46.803ms 
```
Note 192.168.1.30 is the local IP address of my computer, 192.168.1.1 (the next step) is the address of my router, so the DSL modem is actually 192.168.0.1 in my case (the last step before seeing a non-local internet address, like 75.42.179.254). Please let me know what you come up with and maybe we will have some better clues why you are experiencing problems. And lastly, what result did you get for MTU for your connection?

---

### Post by fireman300 on 2009-04-21
John,

I agree there is something very wrong with the picture that is where I get stuck. My recently acquired provider is Comcast and we have a 6 Mbps connection. I never noticed the difference when using DSL but now with the faster connection I could tell something was wrong. 

I connect through a home plug (ethernet over power lines) that is connected to a netgear router. The router plugs into the modem from Comcast. I have two other win boxes for my fam on the network and they get full speed wired directly from the router. I have to try switching to direct wire from the home plug to see if it makes a difference over the weekend. 

I know the home plug is 10 Mbps but that should not be the limiting factor because the uploads are still greater than the downloads. I'll post again when I get to try direct wiring or after my impending Jaunty upgrade whichever comes first. 

Thanks a million for your help. If you have any suggestion I'd appreciate them. 

Jeff

---

### Post by digitals on 2009-04-21
nice tips thanks for sharing

---

### Post by ktmom on 2009-09-24
> **digitals said:**
> nice tips thanks for sharing

+1

---

### Post by sigurnjak on 2009-09-25
I tried to do oing as you suggested and this is output :
andrey@ubuntu:~$ ping -s 1464 -c1 google.com
PING google.com (74.125.127.100) 1464(1492) bytes of data.

--- google.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

andrey@ubuntu:~$ ping -s 1462 -c1 google.com
PING google.com (74.125.45.100) 1462(1490) bytes of data.

--- google.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

andrey@ubuntu:~$ ping -s 1461 -c1 google.com
PING google.com (74.125.45.100) 1461(1489) bytes of data.

--- google.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms


What should i do now ?

These are my interfaces :
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

---

### Post by sadi2009 on 2009-11-23
[B]Thanks man... my internet speed has increased dramatically bcz of your suggestion... I am truly grateful to you... :p:D:)


God Bless.
[/B]

---

### Post by rishi_singh on 2011-10-07
All those commands that you showed, can they be made into some kind of an executable that does all that for me ?

---

### Post by Elfy on 2011-10-07
The OP's not been back since 2009.

Please start your own thread instead of resurrecting 2 year old ones.

Closed

---

### Post by Sensayshun on 2012-03-13
Sorry to bring up a bit of an old thread, is there any way to find out what the RWIN size is at a particular moment in time?

Been trying for hours and I'm not getting anywhere, the only hint I've been given is to use 'netstat' but I can't find any parameters to give it which return the RWIN size. The most I can get out of it is my MTU.

Edit: I believe it is reported in old versions of netstat, but I can't seem to get it. I'm running bash 4.1
I believe netstat has been superseded with ss, but I can't find the information I want using that either.

Thanks for any help.

---

### Post by nogasbiker on 2012-04-02
This is an old-ish thread, but wanted to add a tip.  Instead of varying the ping size to infer the mtu size, you can do it directly by giving ping a mtu hint.

```
$ ping -s 50000 -c 1 -M do www.yahoo.com
PING any-fp3-real.wa1.b.yahoo.com (72.30.38.140) 50000(50028) bytes of data.
From tl-laptop.local (192.168.2.21) icmp_seq=1 Frag needed and DF set (mtu = 1500)

--- any-fp3-real.wa1.b.yahoo.com ping statistics ---
0 packets transmitted, 0 received, +1 errors
```

So here, the mtu size of 1500 is discovered directly.  Hope this helps someone.

---

### Post by sergioabreu on 2012-06-10
Thank you very much for your instrutions! 
Now my internet is really fast on Ubuntu !

---

