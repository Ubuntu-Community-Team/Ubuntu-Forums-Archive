---
title: "HOWTO: Xbox LIVE Access through Ubuntu"
date: 2007-07-23
forum: Tutorials
---

### Post by st33med on 2007-07-23
I have borrowed this technique from [this post]("http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN"), but made it shorter.

First, go into terminal and type this:

```
sudo gedit /etc/rc.local
```

Insert this at the end of the script, before the exit 0:

```
ifconfig eth0 up
ifconfig eth0 192.168.2.1
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o ethX -s 192.168.2.1/24 -j MASQUERADE
```
Where ethX is your wireless card. Reboot.

Hookup your Xbox360 and your computer via Ethernet and boot up the Xbox360 without a game in it. Go to Network Settings and Edit Settings. Now change these things:

IP Address: 192.168.2.2
Subnet mask: 255.255.255.0
Gateway: 192.168.2.1

It will ask you to test these settings. Test Xbox Live. You should get an IP, but no DNS. Go to Edit settings once it's finished.

Your DNS should be the router's IP Address. To check it, return to your computer, right-click the wireless bars/two computers in the taskbar. Click 'Connection Information'. The Default route should be the router's IP address. 

Now, If you're still not connecting and Network Manager is connecting to the Ethernet automatically instead of your wireless connection, you need to set the network manually. Go to System->Network. Click eth0 (or whatever your Ethernet is) and hit 'Properties'. Uncheck 'Enable Roaming mode' and change the configuration from DHCP to Static IP Address. Now do this:

IP Address: 192.168.2.1
Subnet mask: 255.255.255.0
Gateway: 192.168.1.1 (this should be your Router's IP)

Now connect to Xbox live and keep trash talking :popcorn:

Update: Having trouble connecting to a few people? Your wireless card could be the problem. Usually, a wireless card needs to be in promiscuous mode to operate this well, however, 95% of wireless cards do not unless you force it to. All you need to do is this:
```
sudo ifconfig ethX -promisc #ethX is your wireless card
```

If that doesn't help, try the same thing on you Ethernet card. Your Xbox 360 may still say it is moderate or strict NAT, though, Ubuntu might not, in theory, be giving the Xbox a NAT.
Try adding the line above in /etc/rc.local, but without the sudo. I have not tested this part, however, it should work.

---

### Post by frodon on 2007-07-26
Thanks for sharing however i'd like to say users reading this that it is really not clean to handle iptables rules diectly in the rc.local file like suggested here, it is better for you to handle iptables rules in a more suitable way.

---

### Post by st33med on 2007-07-26
There also maybe a little problem. The NAT in your Xbox 360 may pop-up as 'Strict' or 'Moderate'. This may hinder you when you talk to some people or try to join a host. There is a way around this. It is called bridging. However, most wireless network cards have to have a promiscuous mode on it in order for the bridge to work. Most don't have this option, but you can force it to that mode. However, the connection can be unstable. You could lose connection to Xbox Live, you could not see what your friends are doing, etc. So, I will not cover that here.

And, frodon, is there a better way of doing this?

---

### Post by frodon on 2007-07-27
Yes, ithink it is better to handle your iptables rules with your firewall apps or your iptables script, your method works but is not really clean but maybe a beginner who don't even want a firewall will prefer your way of doing this.
However in the case you use another iptables script or apps (like firestarter) it might conflict so in this case better to put your rule in your iptables script or your firewall apps.

---

### Post by st33med on 2007-07-27
Yeah, I tried Firestarter, but it kept saying either my wireless or ethernet card was not working, so I couldn't have it shared through it.

---

### Post by nanonomic on 2007-07-31
Wait, so if that worked would you be able to go on Xbox Live without paying?  Or would it require a username and pass?


In other words if i did that would I be able to get on Live a credit card number?


EDIT: o wait never mind of course that wouldnt work

---

### Post by st33med on 2007-08-14
scratch that

---

### Post by runemaste644 on 2007-10-17
One problem though: The XBox 360 is made by M$!
Well, there is an Xbox Linux distro anyway

---

### Post by st33med on 2007-11-08
The first post has been updated.

And, yes runemaste644, but what are you going to do about it? Buy the Xbox360 license from Microsoft?

---

### Post by TheAL76 on 2007-11-15
So just to clarify, this process will allow me to connect my Xbox 360 to the internet using a wirelessly connected laptop? Thus removing the need to shell out 100 bucks for the wireless adapter?

If so, does having a home wireless router change anything in the process? My router is a standard Netgear, using DHCP and it sits at 192.168.0.1.

Thanks for your help.

Edit: OK, just re-read the original post (I really should get another cup of coffee!). Looks like this procedure could definitely help me. Thanks again.

---

### Post by st33med on 2007-11-15
Yes, this should save you big bucks if you have a laptop. Microsoft pretty much overcharges on their wireless card because wireless adapters for PCs cost around $10-$50. In other words, you are being sapped by MS. I'm not sure if USB adapters for PCs would work on Xbox, but it would be interesting to try.

---

### Post by Ominide on 2007-12-06
Hi, sorry to dig this out but I'm in the process of trying to get this done too.  I've gone through the list and it seems that my DNS is not resolving, does anyone know how to correct this?

here is my ifconfig report
```
ath0      Link encap:Ethernet  HWaddr 00:0E:9B:01:73:74  
          inet addr:10.0.1.3  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:fe01:7374/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4252859 (4.0 MB)  TX bytes:722631 (705.6 KB)

eth0      Link encap:Ethernet  HWaddr 08:00:46:CF:64:51  
          inet addr:10.0.2.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::a00:46ff:fecf:6451/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31830 (31.0 KB)  TX bytes:10768 (10.5 KB)
          Interrupt:3 Base address:0x4c00 

```

---

### Post by The Noble on 2007-12-09
This is EXACTLY what I was looking for. I have been using a bridged laptop in XP to connect the 360 my brother and I play off of and the connection has been utterly appalling. Sometimes it works, sometimes it doesn't, but recently it has been so bad we are lagging out of games. I will set this up next week when I have access to the 360; I can't wait to finally have a lag-free experience! Thank you so much!

---

### Post by unarmedninja on 2007-12-25
did you set the dns on the xbox to the ip of the router not the computer its connected to.

unless you're not using a router. you dont have the typical class C address of 192.168 range. which device is your xbox connected to(ath0 or eth0)?

---

### Post by Juggrnott on 2008-03-11
I followed this guide and was on xbox live for 10 mins then I got dropped and now my intetnet is broken - will someone help???:confused:

---

### Post by designwiz on 2008-03-25
hi well just had a doubt im using a wired router to connect to the internet
how can i setup my xbox live such that both my ethernet cables are connected to my router? 
1 ethernet cable from my xbox live to my router
2 ethernet cable from my pc to my router

is it possible ? any help would be greatly appreciated!

---

### Post by st33med on 2008-06-27
Woof! I haven't updated this forever. Just to let everyone know, I don't know if this will still work on Hardy Heron, but, it should.

Designwiz: What do you need this for?

Juggrnott: Your connection might be very weak or your NAT is very strict. If you do an Xbox Live test, does it say Strict for the NAT? Usually, wireless cards on laptops are very notorious for having bad NAT for acting like a router.

---

### Post by flytripper on 2008-06-27
ok i have tried this one before and it dropped every ten minutes.. really bad imo....
i did a clean install . installed and configured firestarter . manually configured my eth0 to 192.168.0.1 and set my 360 to automatic on both ip and dns.. IT works perfectly!!!!! also see twonky media server for streaming... i would not go back to xp except to recode mkv to mp4.. hurray for ubuntu

---

### Post by flytripper on 2008-06-27
design wiz it should work if youturn on the dhcp server in the router..

---

### Post by flytripper on 2008-06-27
scratch my comments. its late an i miss read the post..

---

### Post by ronniet on 2008-06-29
> **st33med said:**
> 

```
ifconfig eth0 up
ifconfig eth0 192.168.2.1
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o ethX -s 192.168.2.1/24 -j MASQUERADE
```
Where ethX is your wireless card. Reboot.


The above didn't seem to work for me. eth0 was up but didn't have the IP assigned.

I assigned the IP manually but when I did the 'ehco "1"' thing (With a sudo) it wouldn't alter the ip_forward file. It said:

bash: /proc/sys/net/ipv4/ip_forward: Permission denied


> 
It will ask you to test these settings. Test Xbox Live. You should get an IP, but no DNS. Go to Edit settings once it's finished.


Yep, got that far. Then...

> 
Your DNS should be the router's IP Address. To check it, return to your computer, right-click the wireless bars/two computers in the taskbar. Click 'Connection Information'. The Default route should be the router's IP address.


I tried all sorts of IP addresses for my router. Tried it's 192.168.0.1, tried .0.3 (which Network Manager was showing) and even tried the IP address from within my routers admin panel 92.5.x.x

Still fails at DNS look up...  :(

Any ideas where I'm going wrong??  :confused:

I even tried entering the DNS entries from my routers admin panel too, still no go...

---

### Post by st33med on 2008-06-29
> **ronniet said:**
> The above didn't seem to work for me. eth0 was up but didn't have the IP assigned.

I assigned the IP manually but when I did the 'ehco "1"' thing (With a sudo) it wouldn't alter the ip_forward file. It said:

bash: /proc/sys/net/ipv4/ip_forward: Permission denied


Huh... I guess that is fine...

> 
I tried all sorts of IP addresses for my router. Tried it's 192.168.0.1, tried .0.3 (which Network Manager was showing) and even tried the IP address from within my routers admin panel 92.5.x.x

Still fails at DNS look up...  :(

Any ideas where I'm going wrong??  :confused:

I even tried entering the DNS entries from my routers admin panel too, still no go...

Have you tried the usual default for all routers (192.168.1.1)?

---

### Post by Infini on 2008-10-28
I managed to get this working a while back on my Hardy install. I use the USB ADSL Modem Manager to connect to the internet and I simply replaced the ethX part with ppp0 and configured everything else right. I used [this site]("http://www.doxpara.com/") to check my DNS and it worked fine but now that I've got a new install and I'm running into DNS problems. I'm not sure what I'm doing wrong, I feel like I'm forgetting something.

---

### Post by NastyT23 on 2008-11-08
I dont know what im doing wrong but i cant get this to work for the life of me! I've tried a couple differen't methods from various tutorials and none of them have worked for me...I am using a laptop which is connected to the internet via wireless, the wireless is coming from a neighbor so i do not have access to the router...I need to share this wireless connection with my xbox360...here is what my ifconfig looks like:

terry@terry:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:14:22:d3:2e:a4  
          inet6 addr: fe80::214:22ff:fed3:2ea4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78446 (76.6 KB)  TX bytes:22582 (22.0 KB)

br0:avahi Link encap:Ethernet  HWaddr 00:14:22:d3:2e:a4  
          inet addr:169.254.6.190  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:14:22:d3:2e:a4  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fed3:2ea4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106306 (103.8 KB)  TX bytes:26656 (26.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:279440 (272.8 KB)  TX bytes:279440 (272.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:e9:ad:7d  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fee9:ad7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19144673 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24725481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2814591334 (2.6 GB)  TX bytes:2106523741 (1.9 GB)
          Interrupt:18 Memory:dfcfe000-dfd00000 

terry@terry:~$ 


Please any help will be appreciated!

---

### Post by oblivion_08 on 2008-11-10
i had the same problem with dns, it always fails on test. but i only used the dns servers from the computer and when that didn't work i tried the 192.168.1.1 and that didnt work. but thats all i tried. what else should i try. and P.S. for the 192.168.1.1 i put it as primary and secondary, could that be the problem?

---

### Post by NastyT23 on 2008-11-12
bumpity bump! call of duty 5 is out and i want to get online soo badly! lol please help us out, thanks! Like i said before, i've done a couple google searches and followed a few tutorials on how to get this working but i still don't have any luck...the xbox realizes that it's a wired connection but when i go to test the connection it fails on ip address.

---

### Post by cox377 on 2009-04-12
> **flytripper said:**
> ok i have tried this one before and it dropped every ten minutes.. really bad imo....
i did a clean install . installed and configured firestarter . manually configured my eth0 to 192.168.0.1 and set my 360 to automatic on both ip and dns.. IT works perfectly!!!!! also see twonky media server for streaming... i would not go back to xp except to recode mkv to mp4.. hurray for ubuntu

Hello there, how did you get the 360 to pick up the IP via DHCP?

CoXen

---

### Post by GoldenSpartan on 2009-04-19
I can get my xbox to connect to the network, but when it tries to connect to the internet it fails. HELP PLZ!!

---

### Post by Joeagain on 2009-05-17
Well, the original post solved my problem and I'm currently hooking to xbox Live with only one problem; it's a small one, but I'd like to fix it.

When the xbox powers on or powers off, the ip in eth0 goes away.  It's easy enough to fix and only takes a few seconds, which I do by:

```

sudo ifconfig eth0 down 192.168.2.1
sudo ifconfig eth0 up

```

Then I usually type ifconfig just to check, though there's never been a problem getting that working.

I'd love to fix it permanently, instead of turning it into a script.  Does anyone have any ideas?


Thanks again,

Joe

---

### Post by alantsui on 2009-05-28
For people who get "Permission Denied" when doing this:
```

echo "1" > /proc/sys/net/ipv4/ip_forward

```
Use the following command instead:
```

sudo sh -c 'echo "1" > /proc/sys/net/ipv4/ip_forward'

```

See:[http://marc-abramowitz.com/archives/2006/05/17/su-su-sudo-oh-no/](http://marc-abramowitz.com/archives/2006/05/17/su-su-sudo-oh-no/)

---

### Post by joek1997 on 2009-09-06
I have Ubuntu and Vista dual-installed on the laptop that I've been using to get Xbox Live through.  The laptop is connected to the internet through its wireless card and my wireless router, and is connected to my Xbox 360 through its ethernet cable.  I've been able to get Xbox Live through Vista by following the Microsoft tutorials for setting up ICS and automatically assigning the IP and DNS addresses on my Xbox 360.  The Xbox Live connection is often unstable though and I wanted to see if Ubuntu could handle it better.
 

 I tried starting over and using the how-to in the initial post here.  The Xbox Live test failed on the IP address.  When I switched the IP address to automatic, the IP test passed but still failed on the DNS test.  So then I tried setting the DNS addresses to automatic, but it still failed, even though that works when I have the computer in Vista.  So, it seems that there is something wrong with the ICS settings on my Ubuntu computer that are causing the problem, though of course I don't know for sure.
 

 I know there is a general guide for enabling ICS in Ubuntu at [https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing), but I'm a Ubuntu noobie, so I am having a hard time following it.
 

 I have also installed Firestarter and tried to follow their instructions for getting ICS at [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php).  However, I am running into a problem disabling DHCP on my internal network device per their instructions.  The only place I can see an option to do this (at least in Firestarter) is in its Firewall Wizard on the "Internet connection sharing wizard" step.  The "Enable DHCP for local network" option is greyed out, and is set to be checked.  So, I cannot uncheck it.
 

 Does anyone know why this option is greyed out?  How should I disable DHCP on my internal network device?  Please bear in mind that I have already made the changes to the script in the initial post to this thread.  If anyone can help, please share your insights with as much detail as possible.
 

 If it helps, I've copied below the "ifconfig" readout on the Terminal.
 

 eth0      Link encap:Ethernet  HWaddr 00:19:b9:57:c0:de  
           inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
           inet6 addr: fe80::219:b9ff:fe57:c0de/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:51 errors:0 dropped:0 overruns:0 frame:0
           TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:15196 (15.1 KB)  TX bytes:2010 (2.0 KB)
           Interrupt:21
 

 eth1      Link encap:Ethernet  HWaddr 00:19:7d:a7:e7:02  
           inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
           inet6 addr: fe80::219:7dff:fea7:e702/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:2545 errors:0 dropped:0 overruns:0 frame:27919
           TX packets:2515 errors:6 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:2677298 (2.6 MB)  TX bytes:394016 (394.0 KB)
           Interrupt:18
 

 lo        Link encap:Local Loopback  
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:644 errors:0 dropped:0 overruns:0 frame:0
           TX packets:644 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:40248 (40.2 KB)  TX bytes:40248 (40.2 KB)

---

### Post by blatchfordp on 2010-02-16
I had this working once. as soon as i unplugged my crossover cable and tried it again it stopped working i try to activate eth0 and it always says wired disconnected.Here is my ifconfig report 


eth0      Link encap:Ethernet  HWaddr 00:24:8c:01:87:eb  
          inet6 addr: fe80::224:8cff:fe01:87eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1845 errors:0 dropped:0 overruns:0 carrier:16
          collisions:0 txqueuelen:1000 
          RX bytes:315835 (315.8 KB)  TX bytes:1727478 (1.7 MB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41576 (41.5 KB)  TX bytes:41576 (41.5 KB)

ra0       Link encap:Ethernet  HWaddr 00:22:43:5e:49:d0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe5e:49d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1390513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:909623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1435541216 (1.4 GB)  TX bytes:96678433 (96.6 MB)
          Interrupt:19

---

### Post by ookami-no-kobushi on 2010-08-07
okay, i dont know if this is just me, but im really lost i tried to follow everything step by step but you lost me after the first code input into the terminal, can some one help me please i am really lost

---

### Post by GhostTalker on 2011-05-24
I found an easy way just go to network connections then select wired, as I have a network cable connected to my laptop from the Xbox360. Then edit Auto eth0, then on the tab select IPV4 settings and under method select shared to other computers. I was on in seconds to Xbox Live.

I then got the :popcorn: out and started to watch a film on my Xbox 360.

I found this to be the quickest way to get on Xbox Live via Ubuntu and a T-Mobile USB mobile broadband stick.

I hope this helps you all out as I am new to using Ubuntu and find a LOT better the Windows glad I made the move :)

---

### Post by Dlambert on 2011-12-30
With 11.10 I could not get any of this to work, Even the shared to other computers. As soon as my xbox tried to connect to xbox live "Wired connection disconnected" then "reconnected" and back and forth. I tried a ton of things, even a live cd. I got fed up and I had to use my Moms vista laptop.

---

