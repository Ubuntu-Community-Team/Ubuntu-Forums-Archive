---
title: "Monitor network smtp traffic"
date: 2009-08-26
forum: Server Platforms
---

### Post by R.Bucky on 2009-08-26
I want to monitor all outgoing smtp traffic on my employer's network. Someone is using their 3rd party smtp server instead of ours and I want to monitor how often this server is being used. I have tried Wireshark and Darkstat, however they only seem to capture port 80. 

Anyone have an idea?

---

### Post by compiledkernel on 2009-08-26
sudo ifconfig <iface> promisc 

sudo tcpdump -i <iface> port 25 and host <host you think is the problem>

or

sudo tcpdump -i <iface> port 25 > output.txt 

Then control+c when you think you have enough traffic to analyse it. I usually do a cat output.txt | less , and just search through until I find it.

---

### Post by R.Bucky on 2009-08-26
That is what I am looking for. However, this is my Terminal return:
 ```
ifconfig 192.16.1.118 promisc 
192.16.1.118: ERROR while getting interface flags: No such device

```

The 118 is my internal lease.

---

### Post by compiledkernel on 2009-08-26
no, you need to promisc the interface 

so like this 

sudo ifconfig eth0 promisc 

sudo tcpdump -i eth0 port 25 and host <host you think is a problem>

---

### Post by R.Bucky on 2009-08-26
Man, I am clueless this morning. Got it. Thanks for the assisitance!

~Mark

---

