---
title: "Help finding Internet Traffic Logging Software"
date: 2008-05-14
forum: The Cafe
---

### Post by ncosens on 2008-05-14
We recently changed internet service providers from dial-up to Verizon's EVDO Broadband Internet.  It's great minus the 5 GB per month limit.  Go over that and we would have to pay per kilobyte.  Unfortunately the connection software requires Windows to run.  It's ok but I have to use WinXP SP1a with no updates and then turn almost everything off just to make the old PC we are using as an internet gateway run.  And it's only main function is connecting to the internet and using Windows Internet Connection Sharing.  The computer is an old HP Pavilion (before the merger with Compaq) Pentium 2 with 96 MB RAM.  Very fast with the right OS.

Well, Verizon's Connection software is buggy and doesn't log the amount of internet traffic correctly and the server based counter is always a day to 2 behind.  I was wondering if anyone knew of some free software that logged incoming and outgoing traffic.  I've looked around and most software is either massive, not free, or logs content like a proxy server, which I don't need.  I just need how many bytes have been transfered via the network device.  In this case the PCMCIA card.

In case your wondering, I do use Ubuntu on my main machine most of the time.  With the occasional switch to WinXP for certain software and gaming use.

Thanks

---

### Post by pytheas22 on 2008-05-14
There's probably a better solution, but in case no one else responds: you could run [Wireshark]("http://www.wireshark.org/") and have it capture on the interface you're using.  The size of the packet dump should correspond pretty closely to how much has gone in or out of your network, I believe (but you may want to test it just to be sure--for instance, download a file of a certain size from the Internet and see how large the packet dump for that time is).  I'm not sure how well Wireshark would run on such a low-end machine, but it should work.  Also, the packet dump will take up a lot of space on your machine, so you'll want to delete it periodically.

If only the gateway machine ran Linux, there would be so many better ways to do this...

---

### Post by Kevbert on 2008-05-14
> **pytheas22 said:**
> 
If only the gateway machine ran Linux, there would be so many better ways to do this...

I'm after something similar for a Ubuntu PC.  The only thing is that the PC will be turned off at night.  Can you recommend something that can be used to monitor data transfered over a period of a month ?
Thx.

---

### Post by ncosens on 2008-05-14
pytheas, thanks but filedumping is what I'm trying to avoid.

I just talked to a tech support guy who uses Linux himself and he said that is possible to access the internet using Linux.  He gave me the login info which I had before, and he recommended I contact the manufacturer of the card to see if there are any Linux drivers.  I did have it installed once before on either/both PuppyLinux and Damn Small Linux (DSL).  So if you know how to log internet traffic with Linux please let me know.  I will be trying to get this to work with Linux as soon as possible.

One reason I went with Windows is so my dad and mom and brother could understand how to access the internet.

---

### Post by uraldinho on 2008-05-14
wireshark or tcpdump may not be the best thing to do. wireshark keeps a log of every packet sent, that will make the log file too large for a resource constrained computer. 

One idea I can suggest is to use nothing. That's right nothing. ifconfig keeps accounting information, and its output tells me the total size of packets sent and recieved. Eg: check the last line. 

wlan0     Link encap:Ethernet  HWaddr xx.xx.xx.xx.xx
          inet addr:XXXXX
          inet6 addr: XXXXXXXX
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:746150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:461117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1038763791 (990.6 MB)  TX bytes:46815854 (44.6 MB)


That is the amount of bytes received and sent since the interface has been up.... 

I believe you can play with the settings with the IPTABLES command line tool. read the man pages for iptables, ifconfig, etc. 

look at this link on how to use iptables to keep stats: [http://www.linux.com/articles/50649](http://www.linux.com/articles/50649)

PS: iptables is not the most difficult command line tool. it's one of those that many people use, and are very likely to point you in the right direction. Saying that, you should have posted this message in the networking forum/pages where you can get proper answers.

---

### Post by uraldinho on 2008-05-18
I was just going through some TCP/IP stuff, and I saw what you need. 

there is a tcpquata service in ubuntu, which i presume is part of standard linux. it does exactly what you need. 

I didn't read the details, but I think it works in the same way, or uses the same information as in iptables. it reads /proc/net stats and puts them into mysql. 

check out tcpquotad tcpquotaadmin and tcpquotatop tools.. all the answers you need should be in the man pages.

---

