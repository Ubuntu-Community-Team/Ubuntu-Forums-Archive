---
title: "Super slow networking in VBox"
date: 2014-05-27
forum: Virtualisation
---

### Post by Ben_C. on 2014-05-27
Greetings all,

This is both a Virtualization and a Networking issue, but it's networking through virtualization so this seemed the appropriate forum to post in. Anyway.

I have a Ubuntu 12.04 Guest OS machine installed via VirtualBox 4.3.12. All updates performed, initial packages installed (i.e. dkms, VBoxGuestAdditions, etc.). Everything is working properly, but the download speeds are atrocious, around 30-65 kbps where 350 kbps is normal for the host OS (Windows 7).

I've done some looking around and various blogs have suggested switching the network adapter from NAT to Bridged, which I've done but seen no difference. The current network settings are the Bridged Adapter using the Paravirtualized Network (virtio adapter), and the host OS connects to my home network via a wireless usb card.

Thanks in advance, please let me know if you need more information! Any help is appreciated.

---

### Post by TheFu on 2014-05-28
**via a wireless usb card.**

There is your issue. Use wired ethernet.
Also, providing some fact about the hostOS transfer speeds would be helpful.  **iperf** should be useful to test that out between the systems.

---

### Post by Ben_C. on 2014-05-29
I would use a wired connection if that were possible, but unfortunately wireless is my only option right now for this computer. I attempted to use iperf to get transfer speed info, but I don't believe I'm using it properly as I've never used it before.

---

### Post by TheFu on 2014-05-29
> **Ben_C. said:**
> I would use a wired connection if that were possible, but unfortunately wireless is my only option right now for this computer. I attempted to use iperf to get transfer speed info, but I don't believe I'm using it properly as I've never used it before.

iperf has a client and a server.  One of the machines must be running as the server and the other machine connects as the client.

a) istar (server)
b) chromebook (client)

On the server side:
```
istar:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 172.22.22.20 port 5001 connected with 172.22.22.13 port 35680
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  1.07 GBytes   919 Mbits/sec

```
Then on the client side:
```
c720:~$ iperf -c istar
------------------------------------------------------------
Client connecting to istar, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.13 port 35680 connected with 172.22.22.20 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.07 GBytes   920 Mbits/sec

```
Hope that helps clear things up.

Ran it against a VM and got 739 Mbits/sec.

I routinely see 70+MB/sec (about 560Mb/s)  throughput for virtio connections through KVM using normal Linux bridging. Of course everything is wired ethernet, gige here, so that is to be expected. It has been awhile, but under VirtualBox, I don't remember anything being slow - again all wired GigE ethernet.

So ... I can only guess that wireless is the issue.  I've designed over 1000 wifi deployments for my day-job and avoid using it for anything if it can be avoided. It is just too hard to get great network performance over wifi. It is fine for casual web surfing and email, but not when solid network connections are required. There are too many ways for those connections to be screwed, interfered and outside our control.  Heck, I have a chromebook (chromeOS wiped and running 14.04), which only has wifi networking built-in, so I got a USB3-->GigE network adapter ... it gets 70+MB/sec just like the other systems. The C720 w/GigE was used for those tests above.

Network performance over a WAN connection will be very different for most people, including me.  The best I can see is 4.5MB/sec up thanks to my ISP throttling based on what I actually pay to get. ;)

Is wired not an option at all?  Heck, even ethernet-over-powerline is better than wifi when a solid connection is needed.

---

### Post by Ben_C. on 2014-05-29
I think I'm understanding iperf now, although still getting a few hangups. From your linked code, I'm assuming "istar" is the name of your server machine (i.e. host OS), so I attempted iperf listing my computer's name (the one that shows up before the cursor in the command line) as the target location to test under Ubuntu. Server side started listening no problem, but on client side I keep getting "error: no address associated with hostname", so I'm not sure what target name/address I'm supposed to tell ubuntu to yell for.

After looking around on the host OS some I also came across this:
[IMG]http://i62.tinypic.com/2nk57k2.png[/IMG]

Listed under my usual wireless network is what should be the connection Ubuntu is using to connect to the internet via the host OS and is listed at 100 Mbps. The "No network access" lines concern me, but I don't really understand if what I'm looking at is telling me anything or (if it is) whether that's good or bad. If it helps, the host OS is Windows 7 fully updated and guest OS is Ubuntu 12.04 (if I didn't already list that). I've been running iperf through Cygwin on the windows side.

Ethernet isn't *technically* out of the question, but with my location in the house, I would have to run a cable down a hallway, over 3 doorways, and then across a wall to the router. So not impossible, it would just require permission to do so and an afternoon of setup.

---

### Post by TheFu on 2014-05-29
It is bad.  Setting vbox to "host only networking" probably is NOT what you want. Try bridging instead.

I don't use Windows much. Sorry. When forced to use it, I get frustrated.  My iperf runs are between different machines on the network - 1 was a VM. The others are physical machines. On my network, all machines, physical or virtual are full network clients and treated the same.

You can always use IP addresses instead of machine names for the iperf connection.

Here's a vbox performance article that might help: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)  I've been presenting the ideas inside it for 3 yrs around the world. Hope it helps.

[http://www.amazon.com/TP-LINK-TL-PA511-Powerline-Starter-Kit/dp/B0081FLFQE](http://www.amazon.com/TP-LINK-TL-PA511-Powerline-Starter-Kit/dp/B0081FLFQE) is the type of powerline ethernet connection I'm suggesting. It will be like night and day compared to your current wifi connection.  Or you could get a better wifi AP from Ubiquity for more than the powerline-ethernet and less performance.

---

### Post by Ben_C. on 2014-05-29
I'll have to look into the powerline things, I didn't even know stuff like that existed.

The host-only network has me confused though, as the blog you linked is exactly what I had followed when setting it up. Thinking back, what's showing up there may have been created when I was changing settings around to test things, but Bridged Adapter is the setting I've been using for the machine.

Also, finally got iperf figured out. This was my result:
```
------------------------------------------------------------Client connecting to ***.***.**.**, TCP port 5001
TCP window size: 22.9 KByte (default)
------------------------------------------------------------
[  3] local ***.***.**.** port 52755 connected with ***.***.**.** port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   501 MBytes   420 Mbits/sec



```

This is posted from the ubuntu side. Comparing to yours, the transfer speed seems fine (granted my internet connection isn't fantastic to start, but it's def. better than 65 Kbps!).

[IMG]http://www.speedtest.net/result/3531764725.png[/IMG]
[IMG]http://www.speedtest.net/result/3531764017.png[/IMG]

These are the results of 2 tests from speedtest.net, 1 per os. The first is through the browser in the host os, the second through the browser in the guest os (don't freak out, our internet is just that slow :-/). In addition to that, I also downloaded a large file through firefox in ubuntu and was seeing the normal expected download speeds, i.e. the same as the host os. I had initially seen the issue while I was downloading updates for the VM, is it possible I was just seeing throttling/bottlenecking from the mirror?

---

### Post by TheFu on 2014-05-30
Wifi connections are flaky. From minute to minute, the throughput possible changes.
Plus - bandwidth limiting is common on remote servers.

---

### Post by Ben_C. on 2014-05-30
Blegh, ok. Thanks for all the help! :)

---

