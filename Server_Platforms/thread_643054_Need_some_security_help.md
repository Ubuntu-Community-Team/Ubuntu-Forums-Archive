---
title: "Need some security help"
date: 2007-12-17
forum: Server Platforms
---

### Post by Orbital75 on 2007-12-17
I originally posted this in the Beginners section because I feel
that I am a beginner in a since.  I believe something may
be on my Ubuntu that I don't want and would like
some of you knowledgeable Ubuntu gurus to take a look.
Thank you for your help..

Here is a Link that will take you to my post in the Absolute
Beginner section. 

[http://ubuntuforums.org/showthread.php?p=3967910#post3967910](http://ubuntuforums.org/showthread.php?p=3967910#post3967910)

---

### Post by koenn on 2007-12-17
open a terminal window and run
```
netstat -tanc
```
run that net monitor next to it and see if any connections appear in netstat while you get those "receive" peaks. 
the c option will have netstat run continously - you'll have to keep watching it.

man netstat or netstat --help will show other options you can use with netstat in case the above doesn't seem to work.

---

### Post by The Cog on 2007-12-17
It looks lke something happens every minute or two. You should be able to capture this quite quickly with wireshark. Install package wireshark, and launch wireshark (as root) and capture packets while one of the network spikes happens. Wireshark will tell you what the packets are.

---

### Post by Orbital75 on 2007-12-18
Thanks..... This is troubling and scary to me.
I'm hoping its just network gibberish and nothing bad.

---

### Post by stmurray on 2007-12-18
You don't have to install wireshark to see where the traffic is coming from.  I beleive tcpdump is installed by default--just enter;

sudo tcpdump -vv

you can see the the data being displayed will show the IP traffic with a lot of detail, but look for "source > destination", where source is the packets originating ip address and port number (192.168.0.1.25 would be port 25 of ip address 192.168.0.1) or if the ip address can be resolved, tcpdump will show the host name instead-- mymachine.me.com.25.  the destination, to the right of the ">" is the destination ip or host name of the packet.  

It could be your router is trying to use universal plug and play and sending out broadcast traffic periodically  to advertise itself.  Mine does that.  tcpdump shows It like 

14:15:16.253546 IP (tos 0x0, ttl 127, id 30158, offset 0, flags [none], proto UDP (17), length 346) 192.168.100.1.1900 > 239.255.255.250.1900: UDP, length 318

(my router's IP address being 192.168.100.1) 

Sean T Murray

---

