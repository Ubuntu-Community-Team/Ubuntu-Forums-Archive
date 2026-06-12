---
title: "How to select best download server without GUI?"
date: 2009-04-21
forum: Server Platforms
---

### Post by Grey08 on 2009-04-21
How do i select the best download server in Server Edition without the GUI?

What is the command line?


Best regards
Grey08

---

### Post by smeerbartje on 2009-04-21
> **Grey08 said:**
> How do i select the best download server in Server Edition without the GUI?

What is the command line?


Best regards
Grey08

What exactly do you mean? You're browsing on the console? Or via Lynx?

---

### Post by cdenley on 2009-04-21
What type of download server? FTP, HTTP? Are you looking for a repository mirror? The only way to know which is fastest is to actually download data from the servers and compare, unless you went by geographic location and assumed closer meant faster. How would you determine the best download server with a GUI?

---

### Post by Grey08 on 2009-04-21
Ubuntu Software Tab - "Download from" drop down menu - Other - Select Best Server

This little known utility will do a pretty good job of picking a good server based on the response time it gets from them. 


that's what i saw from [http://ubuntuforums.org/showthread.php?t=766708&highlight=select+download+server](http://ubuntuforums.org/showthread.php?t=766708&highlight=select+download+server), #6 thread.

Hope this explained me. :)

Best regards,
Grey08

---

### Post by kevin11951 on 2009-04-21
> **Grey08 said:**
> Ubuntu Software Tab - "Download from" drop down menu - Other - Select Best Server

This little known utility will do a pretty good job of picking a good server based on the response time it gets from them. 


that's what i saw from [http://ubuntuforums.org/showthread.php?t=766708&highlight=select+download+server](http://ubuntuforums.org/showthread.php?t=766708&highlight=select+download+server), #6 thread.

Hope this explained me. :)

Best regards,
Grey08

you could ping all the servers that are close to you, and pick the one with the best response time.

---

### Post by Grey08 on 2009-04-21
> **kevin11951 said:**
> you could ping all the servers that are close to you, and pick the one with the best response time.

But how do i do this if i m in Server Edition without any [COLOR="Red"]Graphical User Interface[/COLOR]? Means that i m working under text based environment.

---

### Post by Spikerok on 2009-04-21
what you can do is to check your network settings...

type "nano /etc/network/interfaces" to see your settings
to leave nano program press on "Alt+X"

if you are using PuTTy or some other software to access your server just paste details.

---

### Post by Spikerok on 2009-04-21
you will get list of devices they are listed next way
auto ...
iface ...

if you did not added any special network software on your pc you will have some thing like next:
[PHP]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
[/PHP]

if you have next type of of config you can try changing 
[PHP]
iface eth0 inet static
[/PHP]
on
[PHP]
iface eth0 inet dhcp
[/PHP]
should work..
if you have other way round, go on your server and change
[PHP]
iface eth0 inet dhcp
[/PHP]
on
[PHP]
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
[/PHP]
you can modify ip's, I'm not sure how correct i'm, but this problem can happen with routers, some routers can not have static ip's and are being given ip's automatically.

Network changes should be made manually, because if error happened you will need to figure out what ip is set on your server machine.

to find out what local ip your server have use next command
[PHP]
ifconfig
[/PHP]
it will tell you info on your network devices
you do not need root rights to use it

---

### Post by Grey08 on 2009-04-22
Thanks Spikerok, appreciate your reply, but does this help to improve my download speed from the archieve server?(like when i type [COLOR="Red"]sudo apt-get install gedit[/COLOR], the speed could go up to [COLOR="Red"]60kbps[/COLOR] instead of now only [COLOR="Red"]5kbps[/COLOR])

What i m trying to solve is onlyget the fastes download speed from archieve server.

Best regards,
Grey08

---

### Post by dfreer on 2009-04-22
Something like apt-spy perhaps?
[http://wiki.linuxquestions.org/wiki/Apt-spy](http://wiki.linuxquestions.org/wiki/Apt-spy)

It never seemed to pull the right servers for me, but I only spent like 5 minutes playing with it, YMMV.

---

### Post by netztier on 2009-04-22
> **Grey08 said:**
> How do i select the best download server in Server Edition without the GUI?

What is the command line?


I would not know about tool that would to this automatically - but I can give you some hints on how to find it out yourself.

Check the list at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) and select some servers close to your location.

Using **traceroute**, or even better **tcptraceroute**, you can get an impression how "far" a server is from you in terms of routing hop count and latency (round trip times)

Chances are good that a server with a low hop count and (more important) **lower latency** will deliver better throughput for you, but it can still be that a server "further" away still is better.

I live in Switzerland, and therfore my local mirror is ch.archive.ubuntu.com, and the round-trip time is less than 25ms.

```
user@host:~$ **tcptraceroute -n ch.archive.ubuntu.com**
Selected device eth1, address 172.20.XXX.XX, port 60710 for outgoing packets
Tracing the path to ch.archive.ubuntu.com (130.59.10.36) on TCP port 80 (www), 30 hops max
 1  172.20.XXX.X  2.048 ms  1.270 ms  1.787 ms
 2  195.186.54.49  24.619 ms  29.896 ms  28.609 ms
 3  195.186.20.14  24.681 ms  24.426 ms  24.435 ms
 4  195.186.59.225  25.176 ms  25.917 ms  26.187 ms
 5  195.186.51.13  24.505 ms  25.848 ms  24.437 ms
 6  195.186.122.233  25.175 ms  25.676 ms  75.398 ms
 7  195.186.0.225  25.175 ms  25.440 ms  27.118 ms
 8  * * *
 9  * * *
10  * * *
11  * * *
12  164.128.22.130  33.939 ms  22.625 ms  22.472 ms
13  130.59.36.249  48.229 ms  23.148 ms  23.121 ms
14  130.59.36.17  23.444 ms  26.720 ms  22.906 ms
15  130.59.10.36 [open]  22.664 ms  23.926 ms  23.976 ms
```


According to the list of mirrors (see above), archive.mmu.edu.my is one of the ubuntu mirror hosts in Malaysia, which might be a bit closer to you (you are located in Northern Borneo, says your profile), but from Switzerland, the tcptraceroute looks like this, and has considerable RTTs of more than 0.3 seconds:

```
user@host:~$ **tcptraceroute -n archive.mmu.edu.my**
Selected device eth1, address 172.20.XXX.XX, port 54073 for outgoing packets
Tracing the path to archive.mmu.edu.my (203.106.62.125) on TCP port 80 (www), 30 hops max
 1  172.20.XXX.X  2.008 ms  1.171 ms  1.135 ms
 2  195.186.54.49  32.091 ms  22.456 ms  20.810 ms
 3  195.186.20.14  24.936 ms  25.183 ms  29.616 ms
 4  195.186.59.225  25.158 ms  24.952 ms  24.937 ms
 5  195.186.51.13  31.213 ms  34.368 ms  24.971 ms
 6  195.186.122.233  24.604 ms  35.649 ms  25.178 ms
 7  195.186.0.225  25.124 ms  24.176 ms  24.194 ms
 8  * * *
 9  * * *
10  164.128.33.118  23.226 ms  22.759 ms  23.149 ms
11  213.248.65.41  37.214 ms  28.499 ms  28.418 ms
12  80.91.249.101  28.965 ms  28.940 ms  29.004 ms
13  213.248.89.206  335.362 ms  328.115 ms  337.218 ms
14  58.27.106.213  327.120 ms  328.177 ms  327.886 ms
15  203.106.6.189  328.309 ms  328.087 ms  327.900 ms
16  210.187.129.143  242.662 ms  255.678 ms  242.133 ms
17  210.187.129.143  242.445 ms  242.715 ms  242.137 ms
18  218.208.61.234  250.171 ms  245.903 ms  243.638 ms
19  203.106.62.125  243.359 ms  247.450 ms  243.172 ms
20  203.106.62.125 [open]  327.386 ms * 328.707 ms
```

Guess which server is better for me? ;-)

regards

Marc

---

### Post by koenn on 2009-04-22
> **Grey08 said:**
> How do i select the best download server in Server Edition without the GUI?

What is the command line?


Best regards
Grey08
use 'netselect' to find the fastest server from a list of servers you provide, or use 'netselect-apt' to find the fastest repo server and automatically generate a sources.list to use that server.

Minor problem : the ubuntu package for netselect-apt is apparently straight from debian and unmodified, so it checks for debian repo's

If you can't configure it to look for ubuntu servers, you might want to file a bug report against it, or start using debian for your servers :)

---

### Post by Grey08 on 2009-04-23
Thanks, netztier

So what i need to do is, ping and find the fastest reply server from [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors), then edit at the "source.list".

Where is the source.list located? What command line i should edit into it?

Best regards,
Grey08

---

### Post by netztier on 2009-04-23
> **Grey08 said:**
> 
So what i need to do is, ping and find the fastest reply server from [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors), then edit at the "source.list".


Exactly. Of course, from the list of archive servers, you should only select the ones that are obvious - no need to test severs from Norway or Canada. In the list, klick on a server and look at the *Mirror URLs* to see the hostname you have to test against:

```
deb http://[COLOR="Red"]archive.mmu.edu.my[/COLOR]/ubuntu/ intrepid main

```

So in this example for "Multimedia University (MMU)", the server to test with ping or tcptraceroute is **archive.mmu.edu.my**.

You may use *ping* or *tcptraceroute* to determine the RoundTripTime between your computer and the archive server. I suggested tcptraceroute instead of ping, because some firewalls are blocking the ICMP protocol, but they must allow tcp port 80 for http access - so if you measure with tcptraceroute, you can still get a meaningful result where you might get none at all ("timeouts") with ping.

> 
Where is the source.list located? What command line i should edit into it?


sources.list is located in the directory **/etc/apt/**. To edit it, you may use a text editor program. On all unixoid systems, ther is one form of **vi** or another, which is a very powerful editor, although a bit cryptic to use. If you know it already and you are comfortable with it, then use vi.

By default, Ubuntu also installs the editor **nano**, which is less complicated to use (I prefer it a lot over vi). It is explained here: [https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

Here, you'll have to launch with **sudo**, because /etc/apt/sources.list is a system file and may not be edited as unpriviledged user:

```
user@server:~$ **sudo nano /etc/apt/sources.list**
```

Refer to the list of archive mirrors on launchpad.net, if you klick on the server in the list, the next page shows you the exact lines you have to copy into your /etc/apt/sources.list. For example, if you select MMU University and "The Intrepid Ibex" as your distribution, it shows you:

```
deb http://archive.mmu.edu.my/ubuntu/ intrepid main
deb-src http://archive.mmu.edu.my/ubuntu/ intrepid main

```

And these are the lines you have to add to source.list - or modify existing ones to look like this.

regards

Marc

---

### Post by sean4u on 2009-06-13
> no need to test severs from Norway or Canada
Well, normally you'd be right, but not in Malaysia. Today, for example, there's no response from archive.mmu.edu.my via the government monopoly wired broadband connection, but I can use it just fine via DiGi's EDGE mobile network.

The local network so often performs so badly that it's not unusual to find very distant servers deliver the best performance. Several servers in Taiwan often far out-perform many local servers for Ubuntu downloads. My Slackware servers in west-coast Malaysia are all configured to download updates from Brazil - as close to 'the other side of the world' as it gets from here. I have yet to find another Slackware package server that can max out my local 512kbit/s 'broadband' connection.

If you're in Malaysia, physics and common sense don't count for much. Spending a counter-intuitively long time playing 'pin the tail on the donkey' (just brute-force trying an update from each server) seems to work best for me. Oh, and what works this week won't work next week.

Latency doesn't always count for much in Malaysia either. Some of the 'local' servers will give fast response but just don't seem to have the bandwidth, so 5KB/s downloads from local servers are not unusual.

Just in case I'm coming across as some sort of end-of-life emo, that archive.mmu.edu.my suggestion of yours seems to be the best thing that's happened to Ubuntu in Malaysia for years. I found it a month or so ago, and it seems to be reliably fast for updates - Ubuntu updates take minutes instead of hours now!

---

### Post by jringoot on 2010-06-16
Without the GUI I don't know either but you can do it remotely via a text based "ssh -X" connection.
Then start the gui-based  
"update-manager - GNOME application that manages apt updates"

"/usr/bin/update-manager"

and let it search for the best repository.
See here for the full tutorial:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If the update-manager is absent on your system, it can be installed with apt-get as well.

I hope this helps you.
For me this is less cumbersome than the manual speed tests that were kindly suggested by the other forum members.

> **Grey08 said:**
> How do i select the best download server in Server Edition without the GUI?

What is the command line?


Best regards
Grey08

---

