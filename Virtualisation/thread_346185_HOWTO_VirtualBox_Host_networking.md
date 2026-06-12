---
title: "HOWTO VirtualBox Host networking"
date: 2007-01-25
forum: Virtualisation
---

### Post by ipguru99 on 2007-01-25
[COLOR=darkred][SIZE=4]**_Edit bodhi.zazen**_ : With the most recent version of Virtualbox, 2.1.0, this entire thread is out dated.

It may take a while for the Ubuntu repo (OSE) edition to catch up.

With VirtualBox 2.1.0 you simply select host networking and select your network card (eth0 , wlan0, etc) from the pull down list.

**No need to manually bridge your network card, no need for a tap**, although you can use these devices if you wish.

See the VirtualBox users Guide for details.

[http://download.virtualbox.org/virtualbox/2.1.0/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.1.0/UserManual.pdf)[/SIZE][/COLOR]


=====================

I started messing around with this stuff (Virtualbox.org) a couple of weeks ago just like everyone else, frantically searching for how to uninstall it ([http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)) when it broke my laptop ;-)

But the last several days, off and on, I have had it running and wanted to get out of the NAT mode of operation.  I looked hard at this doc[html]https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03[/html]But for me, there were a couple of commands missing, as I followed this doc to a tee!  (Great doc, you should start there!)  So when I finally saw my virtual w2k machine boot and get an ip from my local dhcp server, I thought, I HAVE to put all of this down here in the forum.  So here are the commands ripped right out of my HISTORY.

Some things to make this easier to read.  My eth0 on my host is 192.168.0.45.  My tap0 is going to get 192.168.0.94 (totally arbitrary.. ping it first, just to make sure it isn't in use).  The "user" in the first command is the user you login with.

```
sudo tunctl -t tap0 -u user
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.0.94 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.0.45 dev tap0
sudo arp -Ds 192.168.0.45 eth0 pub

```Those first 7 commands are from the help.ubuntu.com page I listed above (bottom of that page.. long page.. but good!).  The rest of the commands are actually in the man page for 'tunctl' (man tunctl at a prompt).  I just stumbled on them because the first 7 commands alone were NOT doing it for me (Dapper).

Add tap0 into the Interface name under
Virtual machine/Network Tab/Adapter 0

Save and start machine.

And on a personal note... I am an old Novell guy (some say that is like being a Jedi these days).. then an old Microsoft guy (have to pay the bills), then an old Cisco guy.. but the last couple of years have been RH, SuSE.. then I found Debian, and now this.  Been running it as the only OS in the house for about 18 months... THAT is the real reason I wrote this.. I have to give something back to this incredible community!!

Thanks!!

---

### Post by kilou on 2007-01-26
Hi,

thanks for these infos!!! I have been looking for this for a long time. I'm trying to setup VirtualBox with 2X Application Server to publish Windows-only applications directly from Ubuntu. However I've not been able to achieve this yet. I need to build a host interface so I followed your directions (I chose the same IP address for tap= as you but my host IP is 192.168.112.200). I installed 2X Application Server in Windows (guest) and in Linux (host) as described here:

[http://searchopensource.techtarget.com/tip/0,289483,sid39_gci1238129,00.html](http://searchopensource.techtarget.com/tip/0,289483,sid39_gci1238129,00.html)

I tried to publish Internet Explorer as a test. I published it as "IEXPLORE" in Windows. So from Linux the following command should launch it:

./appserverclient &#8211;s192.168.0.94  &#8211;ukilou &#8211;a"IEXPLORE"

I'm not sure if I type this command correctly or if the host interface is not working. Do you know anything about that?

Thanks


PS: also what are the benefits of Host interface over NAT in general? I'm a newbie in both Ubuntu and networking and do not understand this clearly.

---

### Post by ipguru99 on 2007-01-26
Main difference for me between the NAT and Host is testing.  When the virtual machines are NAT'd, I can't get to them from my host.  So for App testing and Active Directory Domain testing on other windows Virtuals, it doesn't work well.

I have messed with the 2x stuff for the last 3 months.  I really like the concept, but I can't get it to work two times in a row!  At one point, I knew I had everything set up correctly, so I actually contacted their support (which was decent).  They rdp'd into my house and set it up for me.  Nice, but it didn't really help me do it the next time (which didn't work).  The next time I went through the same thing, I asked them what I was doing wrong.. they told me to publish more than one app... that sometimes that causes it to not work.

I don't know, great stuff when it works, but I wouldn't put it in at any of my customers.  And I use things like Samba/Squid/DansGuardian all the time.. so complexity shouldn't be a problem ;-)  I just don't think their stuff is ready for prime time.. yet!

EDIT:  I just re-read your post.. I don't think your tap interface can be the same as mine with your host being on the 192.168.112.0 subnet... not without some extra route statements.

---

### Post by lamego on 2007-01-26
Whats the main advantages of VirtualBox compared to VMWare ?

---

### Post by kilou on 2007-01-26
VirtualBox is GPL now and also people seem to review it as being slightly faster than VMWare Server (but there are mixed opionion about it). I tried both and I think I like VirtualBox better. I'm not sure but VB may have USB2 support while VMWare is only USB1.1. I'm really not sure about it but when I connect my USB stick in XP with VMWare, I get a message that says it is plugged in a USB1 port. Doing the same with VirtualBox doesn't bring any message....but the use of USB devices with VB is also a bit more tricky sometimes. Also I like the fact that the mouse cursor is automatically captured in the Virtual Machines and is released when you go out of the screen. Sometime you still need to release it with a key but overall it works quite well. Probably that for a serious user VMWare (Workstation and not Server) may be more adequate but VirtualBox has all the features I need and it is free (VMWare Server is free as well but not the Workstation). Just try both and decide which one suits you best.

I'm really wanting to try out this 2x Application software with VirtualBox but cannot achieve to do it. I'm sure I'm doing something wrong but I just don't know what. I could get Internet to work in the Virtual Machine with host interface so this part must be OK thanks to ipguru99. However I must still be doing something wrong with the IP. I reconfigured the IP of the virtual machine with **sudo ifconfig tap0 192.168.112.87 up** (my host is 192.168.112.200) but when I type ipconfig in XP I get IP 192.168.112.203. I then tried to give these 2 IPs for applicationserver command but none was able to launch internet explorer (the application I'm publishing from XP to Ubuntu).

---

### Post by lamego on 2007-01-26
Thanks for the info :)

Please note that the VirtualBox versions available for download are not GPL, you would need to build it from the source.

---

### Post by nfear24 on 2007-01-26
> **ipguru99 said:**
> 

```
sudo tunctl -t tap0 -u user
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.0.94 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.0.45 dev tap0
sudo arp -Ds 192.168.0.45 eth0 pub

```

Add tap0 into the Interface name under
Virtual machine/Network Tab/Adapter 0


Sweet!   Thanks you solved my problem.  So If I want to run multiple virtual guest I need to create a new tap device for each one.   like tap2 tap3.......

---

### Post by cleverselfreferentialname on 2007-01-26
You don't need to make a new bridge for each tap device, do you? I need to know this because I'm making a script to automate all this for you guys.

---

### Post by v.ipe.r on 2007-01-26
Awesome!!! I'm looking forward to it! Thank you very much! :D

---

### Post by ipguru99 on 2007-01-29
I have no idea how many tap's you need.. I am going to check on that tonight.  I want to keep working on the 2X thing.. and the SAMBA 4 stuff.. which scares the crap out of me because they keep saying it will eat my cat!  I will report back here as to whether or not you need a tap per vm

---

### Post by domino on 2007-01-30
Great post! I use every time I have to reboot the host :D. Do you have any problems with the instructions not sticking after every host reboot? i have no problems after I redo your steps. just an annoyance.

```

Failed to initialize Host Interface Networking.
At '/home/vbox/vbox/src/VBox/Main/ConsoleImpl.cpp' (5018) in static int Console::configConstructor(VM*, void*).
VBox status code: -3100 VERR_HOSTIF_INIT_FAILED
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

---

### Post by motumboe on 2007-02-01
Hello,
 these steps just work :-)
Just one thing, I'd like to use static IP addresses instead of dhcp; I'll post here the needed step as soon as I have them working.
But first I have to understand brctl and tunctl.
Cheers,
 Marco

---

### Post by ipguru99 on 2007-02-01
After getting the first one up and running (start of this post), if you want to add a second VirtualBox to the same 'Host' network, here is what I did:

```
sudo tunctl -t tap1 -u user
sudo /usr/sbin/brctl addif br0 tap1
sudo ifconfig tap1 192.168.0.95 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap1/proxy_arp'
sudo route add -host 192.168.0.45 dev tap1
sudo arp -Ds 192.168.0.45 eth1 pub
```

From the start of the post, I used 192.168.0.94 as the ip for the first 'tun' interface.  That was just an ip that wasn't being used.  The same principle applies to the second 'tun' interface.

After adding this, I could start up the second VirtualBox with the Network setting on "HOST" and the interface name of "tap1".  Up it came.

Just a note on the question about setting it static.. I haven't tried it, but it should be really easy to set the dhcp reservation, so the VB always gets the same ip.

On another note.  NONE of this worked on my wireless???  I can get this to work with NAT on my wireless, but none of the tap stuff worked with eth1 instead of eth0... I tried it several different ways... oh well...

---

### Post by kilou on 2007-02-01
There is something I don't understand: I ran the exact same code as in the first post (except I used different IPs for tap0 and host interfaces) but when I launch the virtual machine, internet in guest is working but the guest has another IP as the one I defined for tap0...... I checked the IP I assigned to tap0 and it was unused and within the correct range. What should I do to have the guest have the same IP as the one I assigned to tap0? Is this a dhcp issue???

Also is it possible to have the tap0 interface remain between boots? I always have to type the code in order to get the network working after a reboot. Do I need to put this into a startup script or is there any command that would make the tap0 "persistent"?

---

### Post by ipguru99 on 2007-02-01
I guess I never expected it (the guest) to have the same ip as the tun interface.  My understanding (and I could be wrong here.. anybody feel free to jump in) is that the bridging and the tun interface are just being used as bridge to the network your host is on.  You could reserve a dhcp address for your guest, or I think you could put a static ip on it between boots and it should be fine.  

The 'between boots' part (for the host.. not the guest) is also the part that still gets me.  I have the same issue.  I guess a script could be written for it, but I just copy and past all 6 or 7 commands into a terminal and go ;-)

---

### Post by domino on 2007-02-02
As for the "second VirtualBox to the same 'Host' network", I just use the same static IP on both guests (WinXP & Edgy Server) since I normally don't run two guests at the same time due to rescource requirments on the host.

Has anyone gotten the bridge settig to stick after a host reboot?

---

### Post by kilou on 2007-02-02
How do you set a static IP adress for the guest (XP)?? Do you have to set it from Ubuntu or only from Windows??

---

### Post by ipguru99 on 2007-02-02
Just set it in your guest.  I tried it and it does work ;-)

I have taken to leaving them as dhcp and reserving them in dhcp (since you can set the mac of the guest in the VirtualBox program, it is easy).  

After 10 years of getting crappy laptops from my employers, I actually bought a laptop with enough horsepower to run 3 or 4 virtuals.  Makes my wife happy, because the basement isn't filled with PIII 733's w/256mb.. all just for my testing of crazy situations :D

---

### Post by Mallah on 2007-02-03
hi guys,

i have done everything,

but i does not work..

her my settings :

> br0     Protokoll:Ethernet  Hardware Adresse 00:0E:35:38:D0:B4  
          inet Adresse:192.168.0.105  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::20e:35ff:fe38:d0b4/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8994 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:5136514 (4.8 MiB)  TX bytes:828325 (808.9 KiB)
> 
eth1    Protokoll:Ethernet  Hardware Adresse 00:0E:35:38:D0:B4  
          inet6 Adresse: fe80::20e:35ff:fe38:d0b4/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:6984 errors:0 dropped:5 overruns:0 frame:0
          TX packets:6718 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:34128532 (32.5 MiB)  TX bytes:4287636 (4.0 MiB)
          Interrupt:11 Basisadresse:0xa000 Speicher:c0214000-c0214fff

> tap1    Protokoll:Ethernet  Hardware Adresse 2A:34:FD:BC:72:C4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:500 
          RX bytes:3906 (3.8 KiB)  TX bytes:0 (0.0 b)

> # brctl show
bridge name     bridge id                       STP enabled     interfaces
br0                  8000.000e3538d0b4       no                   tap1
                                                                                 eth1

> sudo tunctl -t tap1 -u user
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth1 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth1
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap1

VirtualBox -> Networksettings:

Attached to **Host-Interface **

Host-interface settings: -> interface-name : tap1

but i dont get an ip addr in my guest sytem:

[IMG]http://melih.mydyn.de/virtualbox_prob.jpg[/IMG]


can you help me please...:confused:

---

### Post by dominicedmonds on 2007-02-04
Hi All, I too have been struggling with this. I have the following as per advices in this thread. My objective is to be able to 'see' the guest VM (WinXPSP2) from the host (Kubuntu Dapper). Here is my shell script to set up the TAP and bridge devices and routing. I would prefer to avoid the routing and leave that to VirtualBox automatically:
```

sudo /usr/sbin/tunctl -t tap1 -u user
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br1
sudo /sbin/ifconfig eth1 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br1 eth1
sudo /sbin/dhclient br1
sudo /usr/sbin/brctl addif br1 tap1
sudo /sbin/ifconfig tap1 192.168.25.143 up
sudo /bin/bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap1/proxy_arp'
sudo /sbin/route add -v -host 192.168.25.142 dev tap1
sudo /usr/sbin/arp -D -v -s 192.168.25.142 eth1 pub

```
As you can see I am using TAP interface [FONT="Courier New"]tap1[/FONT], ethernet hardware interface: [FONT="Courier New"]eth1[/FONT] (my wireless network interface) and bridge: [FONT="Courier New"]br1[/FONT].

192.168.25.142 is the host IP address of my Kubuntu Dapper host
192.168.25.143 is the guest IP address of my WinXPSP2 guest

The resultant output from the host is:
```

Set 'tap1' persistent and owned by uid 1000
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/br1/00:13:ce:b1:8c:98
Sending on   LPF/br1/00:13:ce:b1:8c:98
Sending on   Socket/fallback
DHCPREQUEST on br1 to 255.255.255.255 port 67
DHCPREQUEST on br1 to 255.255.255.255 port 67
DHCPDISCOVER on br1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.25.1
DHCPREQUEST on br1 to 255.255.255.255 port 67
DHCPACK from 192.168.25.1
bound to 192.168.25.142 -- renewal in 42681 seconds.
arp: device `eth1' has HW address ether `00:13:CE:B1:8C:98'.
arp: SIOCSARP()

```

Which seems all OK. 192.168.25.1 is the gateway DHCP server on my wireless router. But there are some [FONT="Courier New"]ifconfig[/FONT] problems:

```

br1       Link encap:Ethernet  HWaddr 00:13:CE:B1:8C:98
          inet addr:192.168.25.142  Bcast:192.168.25.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:feb1:8c98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3557 (3.4 KiB)  TX bytes:2112 (2.0 KiB)

eth0  <snip>

eth1      Link encap:Ethernet  HWaddr 00:13:CE:B1:8C:98
          :(
          inet6 addr: fe80::213:ceff:feb1:8c98/64 Scope:Link
          UP BROADCAST PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:111 dropped:116 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6545790 (6.2 MiB)  TX bytes:694184 (677.9 KiB)
          Interrupt:209 Base address:0xe000 Memory:dfbff000-dfbfffff

lo   <snip>

tap1      Link encap:Ethernet  HWaddr 22:CE:69:BA:5A:2A
          inet addr:192.168.25.143  Bcast:192.168.25.255  Mask:255.255.255.0
          inet6 addr: fe80::20ce:69ff:feba:5a2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:36 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I would expect [FONT="Courier New"]eth1[/FONT] still to have an IP address of 192.168.25.142 so that it can continue to be connected to the outside world, or is that meant to be happening through the bridge?? :confused:

I have set Network Settings in the guest VM with tap1:

[IMG]http://www.3lmr.com/test/VMNet.jpg[/IMG]

But what about the MAC address? SHould that be set to the same as eth1?
 
Meanwhile in the guest VM, I set the IP address statically:

[IMG]http://www.3lmr.com/test/WinXPNet.jpg[/IMG]

---

### Post by domino on 2007-02-04
Guys, redo the instructions but use **tap0** instead of tap1. That's how I 've always gotten it to work. Also this method may not work with wireless.

---

### Post by ipguru99 on 2007-02-05
This will be quick, and I can get into more detail later this afternoon, but I have to get my son to swimming lessons ;-)

First thing's first:  When all is said and done, you should ifconfig and see an ip address on your bridge and your tap.. NOT your ethernet (if you see it on your ethernet, you didn't follow the directions completely.. or there is a different way of doing it ;-).  That is the purpose of your bridge.  

Second, as domino mentioned.. and in my second post on how to get 2 of them working at the same time, wireless didn't work for me in host networking.  I have no idea why??  In principle, it should, they are all the same commands, thus my hate of wireless ;-)

I can get more specific later if someone has a more direct question (that I can answer, of course).. 

Hang in there.. and follow the directions to a tee!  Posting your history always helps me!

---

### Post by dominicedmonds on 2007-02-06
Three little thoughts:
1. Anyone any ideas how and where to tackle the wireless issue - i.e.: that it does not work.
2. I am quite :confused: and boscumdibulated about the br0 interface on the host. Does setting up a bridge still allow the host to continue communicating via the gateway? I would certainly expect it to.
3. Would xen be an alternative [http://www.xensource.com/products/xen_express/index.html]("http://www.xensource.com/products/xen_express/index.html") I am thinking of trying that too.

---

### Post by Keyed on 2007-02-06
Works for me, thanks. Just had to alter firewall to allow traffic to/from guest address. Also assigned static address for guest. Now with shared directory working and host networking working, all is well.

---

### Post by mmoalem on 2007-02-07
hi there all - as there is no solution for the reboot issue (tap not persistent after reboot) i guess i will have to keep manually inputting the list of commands every reboot to create the bridge and tap interface.
at the moment i copy from a text file and pasted into a terminal but was wandering how i can make the text file run as an excecutable script rather than the copy/paste process.
any ideas?
cheers
michel

---

### Post by David Floyd on 2007-02-07
> **ipguru99 said:**
> 
Some things to make this easier to read.  My eth0 on my host is 192.168.0.45.  My tap0 is going to get 192.168.0.94 (totally arbitrary.. ping it first, just to make sure it isn't in use).  The "user" in the first command is the user you login with.

```
sudo tunctl -t tap0 -u user
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.0.94 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.0.45 dev tap0
sudo arp -Ds 192.168.0.45 eth0 pub

```

Those first 7 commands are from the help.ubuntu.com page I listed above (bottom of that page.. long page.. but good!).  The rest of the commands are actually in the man page for 'tunctl' (man tunctl at a prompt).  I just stumbled on them because the first 7 commands alone were NOT doing it for me (Dapper).

 
I am a recent newbie and I've fallen at the first hurdle :( 
I get "sudo: tunctl: command not found" after the first line - why should that be? (running dapper)

Thanks,
David

---

### Post by Keyed on 2007-02-07
> **David Floyd said:**
> I am a recent newbie and I've fallen at the first hurdle :( 
I get "sudo: tunctl: command not found" after the first line - why should that be? (running dapper)


tunctl is part of the uml-utilities package.

---

### Post by David Floyd on 2007-02-08
> **Keyed said:**
> tunctl is part of the uml-utilities package.

Well, as I mentioned, I'm a relative newbie (3 weeks), so could you please expand on yor answer as it doesn't mean much to me.  Is it something I need to install - if so, where do I get it.

Thanks
David

---

### Post by ffxr on 2007-02-09
David install the two packages listed halfway down this.. [https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03](https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03)


has ANYONE got this working with wireless nics & routers..?

ve played around here for hours.. ve nearly no hair left ..

---

### Post by ffxr on 2007-02-09
Success.. 

i did the following..

post host reboot & clear ifconfig (just my wireless card & loopback)

```
sudo apt-get install uml-utilities
sudo modprobe tun 66.202.65.50
mkdir /dev/net    #may already exist
mknod /dev/net/tun c 10 200 
```

#Create the tap0 interface using tunctl

```
sudo tunctl
sudo ifconfig tap0 192.168.100.1 netmask 255.255.255.0 up

sudo modprobe ip_tables
sudo modprobe iptable_nat
sudo modprobe ip_nat_ftp
sudo modprobe ip_nat_irc
```


i then created a file setupnat with this in it

```
#!/bin/sh
echo "1" > /proc/sys/net/ipv4/ip_forward
/sbin/iptables -t nat -A POSTROUTING -o ra0 -j MASQUERADE
echo 1024 > /proc/sys/dev/rtc/max-user-freq

#---> ra0 is the name of my wireless card
```

then from su console

```
chmod a+x ./setupnat
./setupnat
```


In VirtualBox os details i set it use HOST interface & entered the MAC address of tap0 (from ifconfig) 

then in guestOS i set:

```
ipaddress : 192.1.100.2
subnet mask: 255.255.255.0
default gateway 192.1.100.1

dns: 192.168.1.1 my router
alternative: my isp dns server address   (i dunno which of these is doing the translating)
```


these threads are wher i cut this fix up from:
[http://www.ubuntuforums.org/showthread.php?t=196744&highlight=routing+tap](http://www.ubuntuforums.org/showthread.php?t=196744&highlight=routing+tap)
[http://www.ubuntuforums.org/showthread.php?t=179472&highlight=qemu+network](http://www.ubuntuforums.org/showthread.php?t=179472&highlight=qemu+network)


ll tidy this up later & make sure shares etc are available.. after i get a shower.. i just wanted to get this wriiten down incase anything goes wrong... i might even make this a HOWTO.. 

also i believe you make the tap0 config persistant by adding it to: /etc/network/interfaces, ll have a look at this later..

---

### Post by ipguru99 on 2007-02-09
Sweet!!  THAT is what I was looking for!  I wonder why the wired "Just Works" with this and the wireless has to have the NAT put in for it?

I am going to see if it will work with more than one host, I will report back.

Nice idea with the tap0 in /etc/network/interfaces, that should shrink the amount of commands to start this pig!

Thanks!

---

### Post by ffxr on 2007-02-09
just to automate things a little.

i added this to my interfaces file:  gksu mousepad /etc/network/interfaces


```
iface tap0 inet static
address 192.168.100.1
netmask 255.255.255.0
hwaddress ether 08:00:27:9C:D9:ED  
auto tap0

#i used the generate button in VirtualBox's Network config dialog to get the MAC address.
```

I updated my setupnat file to call tunctl from it..

```
#!/bin/sh
sudo tunctl
sudo echo "1" > /proc/sys/net/ipv4/ip_forward
sudo /sbin/iptables -t nat -A POSTROUTING -o ra0 -j MASQUERADE
sudo echo 1024 > /proc/sys/dev/rtc/max-user-freq
sudo ifconfig tap0 up
```


so now i just run ./setupnat (post host reboot) & i then launch my virtual machine... (ipaddress 192.168.100.2, GW 192.168.100.1) & it WORKS! no need for any bridges... & relatively well automated

---

### Post by timas on 2007-02-14
Hey guys,

Considering its my server that's running all this I don't use wireless and can get two VirtualBox guests working simultaneously with this script. It also fixes the DHCP troubles because it uses a static IP for the host machine as well. 

```

#!/bin/bash

tunctl -t tap0 -u timas
chmod 666 /dev/net/tun
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
ifconfig br0 192.168.1.2 netmask 255.255.255.0 broadcast 192.168.1.255 up
brctl addif br0 tap0
ifconfig tap0 192.168.1.101 up
bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
route add -host 192.168.1.2 dev tap0
arp -Ds 192.168.1.2 eth0 pub

tunctl -t tap1 -u timas
brctl addif br0 tap1
ifconfig tap1 192.168.1.102 up
bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap1/proxy_arp'
route add -host 192.168.1.2 dev tap1
arp -Ds 192.168.1.2 eth0 pub

ip route add default via 192.168.1.1


```

---

### Post by timas on 2007-02-14
UPDATE!
To be able to reach the guest OS you need to give it a /different/ IP than the TAP interface has!

Example: 
tap0 has IP 192.168.1.101  Guest OS has IP 192.168.1.103
tap1 has IP 192.168.1.102  Guest OS has IP 192.168.1.104

IP 101 and 102 connect to the HOST not the guest..

Network transfer rates from host to guest (NFS to share partitions, for example) are not tremendous on my machine.. doing 2.3M/s at best..

Cheers,
-T

---

### Post by ffxr on 2007-02-15
> "Network transfer rates from host to guest (NFS to share partitions, for example) are not tremendous on my machine.. doing 2.3M/s at best.."

god that does seem slow... whats your guest os? windows? is it samba your using to access your host shares..? m told their is a bug in the default virtualbox sharing between host & guest.. 

their is a good guide (i.e quick & worked for me) to samba here: [http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+how+to](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+how+to)

---

### Post by zdude on 2007-02-27
I've tried most of the scripts on this thread to setup my bridge for vbox with limited success but I wanted something I could automate, turn off or on and also keep my hosts same static IP address. Also, it would be a bonus to be able and select a dynamic or static address for my guest via the guest OS network setup. SO, I found this thread: [http://deb.riseup.net/miscellaneous/uml/](http://deb.riseup.net/miscellaneous/uml/)

I then fixed the few typos and added a two more lines needed an presto, a script that you can start or stop 
bridging at your whim! Here is the finished script - I place it in
 /etc/init.d/bridge :
-------- begin code
#!/bin/sh
 
# configure your static host info here and your user name
 
HOST_IP="10.0.0.15"
HOST_NETMASK="255.255.255.0"
HOST_GATEWAY="10.0.0.1"
HOST_IFACE="eth0"
USER_NAME=user
 
case "$1" in
  start)
    echo -n "Setting up fancy dancy bridge networking"
    ifconfig $HOST_IFACE 0.0.0.0 promisc up
    brctl addbr umlbridge
    brctl setfd umlbridge 0
    brctl sethello umlbridge 0
    brctl stp umlbridge off
 
    ifconfig umlbridge $HOST_IP netmask $HOST_NETMASK up
    route add default gw $HOST_GATEWAY
    brctl addif umlbridge $HOST_IFACE
 
    # first UML instance
       tunctl -u $USER_NAME -t tap0
       # added r/w privies
       ifconfig tap0 0.0.0.0 promisc up
       brctl addif umlbridge tap0
    # second UML instance
#     tunctl -u uml -t tap1
#     ifconfig tap1 0.0.0.0 promisc up
#     brctl addif umlbridge tap1
    # and so on...
       chmod 0666 /dev/net/tun
    echo "."
    ;;
  stop)
    echo -n "Stopping networking bridge"
    # add more tab1,tab2, etc as needed
    ifconfig umlbridge down
    brctl delif umlbridge $HOST_IFACE
    brctl delif umlbridge tap0
    brctl delbr umlbridge
    tunctl -d tap0
    ifconfig $HOST_IFACE $HOST_IP netmask $HOST_NETMASK up
    route add default gw $HOST_GATEWAY
    echo "."
    ;;
esac

exit 0 
----- end code

now you can /etc/init.d/bridge start|stop 
It is very fast as well!!!!
Setup the vbox Setting>Network as "Host Interface" and Interface name as "tap0" as others here have noted. This routine also allows for multiple taps as well!

---

### Post by maxky on 2007-03-11
See [http://www.virtualbox.org/discussion/1/126](http://www.virtualbox.org/discussion/1/126) on how to define the bridge in
/etc/network/interfaces

Add the line

   post-up chmod ugo+rw /dev/net/tun

to the bridge0 entry to make the device accessible by the user.
Configured in that way, the network access even survives a reboot.

---

### Post by NarsilAnduril on 2007-03-13
Trying to ... lets go step by step :

```
user@host:~$ sudo tunctl -t tap0 -u user
Set 'tap0' persistent and owned by uid 1000
```

What's next ?

```
user@host:~$ sudo /usr/sbin/brctl addbr br0
sudo: /usr/sbin/brctl: command not found

```

Oh !

I think i need help !

---

### Post by ipguru99 on 2007-03-14
NarsilAnduril

You have to:
sudo apt-get install bridge-utils

HTH,

brian

---

### Post by NarsilAnduril on 2007-03-15
That's it, thanks !

But i finally used another method (reboot persistent) : add the bridge to /etc/network/interfaces following this [howto]("http://www.virtualbox.org/discussion/1/126")

narsil

---

### Post by joff13 on 2007-03-21
Hi,
tnx to this post I got my VM connected to the Internet using 2 ip (one for tap the other one for eth0)

now the problem I have is that at work I have just 1 public ip and need to connect the VM to the LAN and also to a web server on my pc 

Any Idea?

tnx

---

### Post by NarsilAnduril on 2007-03-21
Theorically (not tested ...) :

You can build two interfaces in VM (ou can have up two 4 in the config tool) : One tap1 and one NAT.

Then in the guest OS, use the first (tap) to connect to your PC's web server and the second (NAT) for internet.

Let me know if that works :???: 

narsil

---

### Post by doomzday on 2007-03-31
hi, I've tried the method with the script and the first method described in this thread but no luck...
I can ping from the guest os to the host os Ip's (the tap ip and the bridge ip)

what am I doing wrong ? :(

---

### Post by NarsilAnduril on 2007-04-01
Do you mean you can ping guest <-> host both ways ?

If yes, your network is up. Now what's exactely the problem ? No Internet from the guest ?

Did you set your DNS's ? Your Gateway ? (in the guest)

narsil

---

### Post by mbertheau on 2007-04-30
I wrote up a post that describes all aspects of this, including
[LIST]
[*]static IP addresses vs. DHCP
[*]more than one tap device when you have several virtual machines
[*]no manual steps after every reboot
[/LIST]

[http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/](http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/)

---

### Post by scotttkd on 2007-05-01
mmoalem.....this link has a script in it that does the trick for loading the settings at boot up.  put it in the file shown in the example, not in the network/interfaces as that will hose up your system quite well thank you!! :  Fixed all issues with virtualbox for me.

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)


edit:  oops...I see someone already addressed the script issue.  oh well, great link anyway.

---

### Post by ipguru99 on 2007-05-01
Wow.. now only if all stuff came with directions like this!  Thanks for the link.. and thanks to Bodhi!!

---

### Post by ronald_stall on 2007-05-02
Trying to use SeamlessVirtualization with rdesktop:

I've got host networking working but when I try and run the command

Code:

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" <IP of VM>:3389 -u administrator -p passwor

d of course using my VM IP and user and password as required.

I get this output

Autoselected keyboard map en-us
ERROR: connect: Connection refused


Any ideas what I've done wrong?

---

### Post by ipguru99 on 2007-05-02
I just spent the last couple of days at a client doing the same thing and we are right up to the point where we are going to do the seamless test.. but alas, I am not there right now... so hopefully I will be able to share that it does work tomorrow.  

I HAVE to ask.. Can you just plain old RDP from one VM to the other VM?  Just asking... ;-)

---

### Post by ronald_stall on 2007-05-05
Ok, I have managed to get SeamlessVirtualization to work, sorta!

I got the host networking up with all your help. Thanks!

This is the only way I can get this to work but just does not seem right. 

I startup my Virtualbox guest which is WinXP, I must login, then logout. Silly huh. If I skip this step it fails completely.

Then I launch a WinXP application like

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\System32\sol.exe" 192.168.1.105 -u user -p password
```

And I'll be darn it works! Problem is once you close out of the app you launched you must power off your guest and startup and do it all over again or it will not run any other app. This certainly does not seem "Seamless".

Anyone else have any success?

---

### Post by tikey on 2007-05-08
@zdude (#36): great! after I tried a lot which didn't work this one worked perfect (after I restarted and all the tapX from before where gone).
Thanks!

---

### Post by MKdon on 2007-05-16
> **mmoalem said:**
> hi there all - as there is no solution for the reboot issue (tap not persistent after reboot) i guess i will have to keep manually inputting the list of commands every reboot to create the bridge and tap interface.
at the moment i copy from a text file and pasted into a terminal but was wandering how i can make the text file run as an excecutable script rather than the copy/paste process.
any ideas?
cheers
michel

Just paste the code into rc.local and it will run each time you boot

---

### Post by kilou on 2007-05-17
There is something I don't understand: VirtualBox host networking is used to allow to use internet from the guest, share files between host and guest and run guest application seamlessly through remote desktop. Except for browsing the web, it should be possible to achieve all the other things without being connected, no?

Is it possible to share files and folders between host and guest or launch a guest application seamlessly with remote desktop without any connection being active??? If this is not the case it's quite bad for me because I need to run MS application and share files with Ubuntu on the go (laptop) when I'm not connected to any network. The bridge thing doesn't seem to work if the eth0 interface is not connected...

Also is it possible to have both eth0 (wired) and eth1 (wireless) connections useable from the guest? I tried to apply the same code to create a bridge for eth1 but it didn't work. Is there anyway to have wired and wireless connection accessible from the guest??

Thanks

---

### Post by ipguru99 on 2007-05-17
to Mkdon.. and others that have asked about a script... 

I followed this link:
[http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/]("http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/")

I have rebooted this server several times now and everything always works.  I host 5 virtuals on this server and other than having a much longer than normal /etc/network/interfaces file, it works great!

---

### Post by scoot1212 on 2007-05-17
Can anybody tell me how to setup host-only networking on VirtualBox 1.3.8?  I am trying to give up on VMware Server since it's very slow on 7.04.  I can't seem to find anything related to host-only networking.
Thank you,
Scott

---

### Post by MKdon on 2007-05-18
After a couple of days googling and trying the various methods, I found none would work with Wi-Fi cards. I eventually found a site Hazards blog and a description using parproute which I downloaded via Synaptic and installed.  Then the following code in rc.local:
#!/bin/sh -e
# # rc.local
# # This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
# # In order to enable or disable this script just change the execution
# bits.
# # By default this script does nothing.
# For Network Bridging/TAP to enable Virtual Box
# Set permissions of tun device

chown root:vboxusers /dev/net/tun


#Be sure to change user_name to your user name

/usr/sbin/tunctl -t tap1 -u bob
/sbin/ip link set tap1 up
/sbin/ip addr add 10.1.1.0/24 dev tap1
/usr/sbin/parprouted -p ra0 tap1


exit 0
After this I also installed guarddog and guidedog to allow me to alter the firewall sttings to communicate between host guest and the web.  I can oing between host and guest and vice versa and connect to the web.  I am now trying to sort out samba.  When everything is up and running I&#314;l publish the results.

---

### Post by MKdon on 2007-05-18
PS my /etc/network/interfaces  has no changes, just the wireless interface code.:guitar:

---

### Post by kilou on 2007-05-18
MKdon, does your settings work with Wifi AND Ethernet connections or just with Wifi??

Also what is 10.1.1.0/24?? I guess the 10.1.1.0 is the guest's IP but what is the 24??

---

### Post by kfries6 on 2007-05-18
I think I have finally figured out why I am having so much trouble getting VirtualBox to do what I want... Symantics!

Like many of you, I come from a VMWare environment.  VMWare has four types of network options between the host, guest, and outside world.  VirtualBox describes two of these, but calls the second network type by a name used by VMWare for something very different.  This is extremely bad form!!!!

VMWare networking types are:
   NAT: this is the same as it is in VirtualBox
   Bridged: VirtualBox is incorrectly calling this Host Networking... Can someone make them stop that!
   Host Only: This one is the one I am interested in, but does not seem to get discussed
   Other: VirtualBox documentation indicates that they set this up automatically to go from VM to VM

What I need is Host Only networking.  In this network, my host has an IP address that is on the same network as my Virtual Machines, but not on any network tied to my NIC.  In VMWare, they set up VMNet1 for this purpose (my machine also has VMNet8 for machines that bridge to the network).  The IP address bound to VMNet1 is only valid within my machine (172.16.238.1).  As I bring up each of the virtual machines, VMWare acts as DHCP and assigns an address in the 172.16.238.x range for each host only machine, and from the corporate DHCP server for any bridging machines, along with a 172.16.17.x address for host to guest interaction.

All I see discussed is bridging, and it is being called host networking.  What I want is host only networking, where my machine, and my VMs are on a network all by themselves.  No external references to the VMs in either direction.

Where can I find a "Howto" to do this?

Also, I have my virtual machines come up on startup, and shutdown on poweroff.  It seems to me that with the extensive command line interface VirtualBox has, this should be pretty trivial.  Before writing my own and re-inventing the wheel, has anyone published any scripts to do this automatically?


thx
Kevin Fries


PS.  To answer the inevitable question, I still get updated software, and can install at will on the VM even though it has no access to the internet.  Use Apt-Cacher on your host, and point the VM instance's apt sources at the VMNet1 address (see apt-cache documentation).  Poof, apt-get works perfectly without access to the internet.

---

### Post by kfries6 on 2007-05-18
> **kilou said:**
> Also what is 10.1.1.0/24?? I guess the 10.1.1.0 is the guest's IP but what is the 24??

the 24 is the subnet mask 255.255.255.0.  A netmask writen in this way is known as [CIDR notation]("http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing").  It represents the number of consecutive 1 bits on the left side of the 32 bit netmask.

HTH
Kevin Fries

---

### Post by scotttkd on 2007-05-18
mkdon...did I understand you correctly that you got the host networking option to work with wifi??  If so a link would be much appreciated.

scott

---

### Post by youbecha on 2007-05-19
The commands at the beginning of this thread work perfectly on my machine...

But I would like to use the option to run scripts off the Virtualbox interface.

(you know, to start up the network it runs one script, and to shut down it can run another)


How do incorporate all the fine commands here into two separate scripts...up and down...?

---

### Post by angem1 on 2007-05-28
Hello,
using Ubuntu Feisty, VirtualBox 1.3.8;
I have a ppp0 link and not eth0 so I can't bridge it.
How else can I do port redirection from Ubuntu host to WINDOWS XP guest ?

---

### Post by angem1 on 2007-05-28
The bridge was meant to redirect port 80 so IIS receives incoming connections from host...
I managed to solve this problem by making IIS listen to port 8033,
allowing this port in Windows Firewall, and running:
(MyXP is the VirtualMachine name in VirtualBox)

```
VBoxManage setextradata "MyXP" \
      "VBoxInternal/Devices/pcnet/0/LUN#0/Config/http/UDP" 0
VBoxManage setextradata "MyXP" \
      "VBoxInternal/Devices/pcnet/0/LUN#0/Config/http/GuestPort" 8033
VBoxManage setextradata "MyXP" \
      "VBoxInternal/Devices/pcnet/0/LUN#0/Config/http/HostPort" 8033
```

I chose port 8033 since it wasn't blocked like 80.
(Maybe apache on the host makes the block even though it's off, or because it's higher than port 1023, any idea? or maybe inetd)

---

### Post by Beamerboy on 2007-07-14
> **ipguru99 said:**
> I started messing around with this stuff (Virtualbox.org) a couple of weeks ago just like everyone else, frantically searching for how to uninstall it ([http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)) when it broke my laptop ;-)

But the last several days, off and on, I have had it running and wanted to get out of the NAT mode of operation.  I looked hard at this doc[HTML]https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03[/HTML]

But for me, there were a couple of commands missing, as I followed this doc to a tee!  (Great doc, you should start there!)  So when I finally saw my virtual w2k machine boot and get an ip from my local dhcp server, I thought, I HAVE to put all of this down here in the forum.  So here are the commands ripped right out of my HISTORY.

Some things to make this easier to read.  My eth0 on my host is 192.168.0.45.  My tap0 is going to get 192.168.0.94 (totally arbitrary.. ping it first, just to make sure it isn't in use).  The "user" in the first command is the user you login with.

```
sudo tunctl -t tap0 -u user
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.0.94 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.0.45 dev tap0
sudo arp -Ds 192.168.0.45 eth0 pub

```

Those first 7 commands are from the help.ubuntu.com page I listed above (bottom of that page.. long page.. but good!).  The rest of the commands are actually in the man page for 'tunctl' (man tunctl at a prompt).  I just stumbled on them because the first 7 commands alone were NOT doing it for me (Dapper).

Add tap0 into the Interface name under
Virtual machine/Network Tab/Adapter 0

Save and start machine.

And on a personal note... I am an old Novell guy (some say that is like being a Jedi these days).. then an old Microsoft guy (have to pay the bills), then an old Cisco guy.. but the last couple of years have been RH, SuSE.. then I found Debian, and now this.  Been running it as the only OS in the house for about 18 months... THAT is the real reason I wrote this.. I have to give something back to this incredible community!!

Thanks!!

Firstly thanks for this, I don't like using NAT especially since I have a /29 subnet.

However, I am new to bridging in Linux, can you tell me how to do this without having to assign tap0's IP with DHCP?  I would like to set tap0 to have a static IP as it is for running sandboxed websites.

The IP it needs to use is 87.127.87.187
According to ifconfig it actually has this IP but my guest installation in virtualbox is being assigned a different IP (currently 87.127.87.189 but it changes depending on whether the lease runs out).

Here is the output for ifconfig on the Host:

```

root@mail:/home/paladine# ifconfig
br0       Link encap:Ethernet  HWaddr 00:11:D8:D9:81:4D  
          inet addr:87.127.87.186  Bcast:87.127.87.191  Mask:255.255.255.248
          inet6 addr: fe80::211:d8ff:fed9:814d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:405760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:547319332 (521.9 MiB)  TX bytes:14009963 (13.3 MiB)

eth0      Link encap:Ethernet  HWaddr 00:11:D8:D9:81:4D  
          inet6 addr: fe80::211:d8ff:fed9:814d/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:1249640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:807329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1517827452 (1.4 GiB)  TX bytes:93149753 (88.8 MiB)
          Interrupt:16 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:11:D8:D9:91:B5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 

eth1:avah Link encap:Ethernet  HWaddr 00:11:D8:D9:91:B5  
          inet addr:169.254.10.26  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:59761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8502700 (8.1 MiB)  TX bytes:8502700 (8.1 MiB)

tap0      Link encap:Ethernet  HWaddr 00:FF:09:0A:88:E7  
          inet addr:87.127.87.187  Bcast:87.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2ff:9ff:fe0a:88e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90606 errors:0 dropped:267 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:3071177 (2.9 MiB)  TX bytes:134166908 (127.9 MiB)

```

I was actually thinking of using eth1 for the guest OS but I am not sure if I can get virtualbox to use a static IP on a second interface, it seems to only support bridged networking, NAT or private.

Any help appreciated.

Paladine

---

### Post by ipguru99 on 2007-07-14
Beamerboy... personal note.. is the beamer for bmw?  I just bought a new 335xi... and after driving audi's for 10 years, I have officially switched!  If not, sorry...

anyway, you can assign your tap's to be static in your /etc/network/interfaces file.

Here is one of my test boxes (see the w2k3 server stanza for how to put your own static ip on your host):

```
root@lab-host:~# cat /etc/network/interfaces
#This file has been altered from it's original state to 
#help facilitate different networks for Virtualbox
#
#Please don't alter it directly
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

iface eth1 inet manual 

#stanza for 7.04 ltsp box
auto tap1
iface tap1 inet manual
tunctl_user tuser

#stanza for w2ksp4 box
auto tap2
iface tap2 inet manual
tunctl_user tuser

#stanza for w2k3 box 
auto tap3
iface tap3 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  down ifconfig $IFACE down
  tunctl_user tuser

#stanza for Xubunt7.04-Desktop-LIVE
auto tap4 
iface tap4 inet manual
tunctl_user tuser

#stanza for PXE_Etherboot image
auto tap5
iface tap5 inet manual
tunctl_user tuser

auto bridge0
iface bridge0 inet static
 address 192.168.15.19
 netmask 255.255.255.0
 broadcast 192.168.15.255
 gateway 192.168.15.1
 bridge-ports eth0 tap1 tap2 tap3 tap4 tap5
 bridge-ageing 7200
 bridge-fd 0

```

---

### Post by Beamerboy on 2007-07-14
> **ipguru99 said:**
> Beamerboy... personal note.. is the beamer for bmw?  I just bought a new 335xi... and after driving audi's for 10 years, I have officially switched!  If not, sorry...

anyway, you can assign your tap's to be static in your /etc/network/interfaces file.

Here is one of my test boxes (see the w2k3 server stanza for how to put your own static ip on your host):

```
root@lab-host:~# cat /etc/network/interfaces
#This file has been altered from it's original state to 
#help facilitate different networks for Virtualbox
#
#Please don't alter it directly
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

iface eth1 inet manual 

#stanza for 7.04 ltsp box
auto tap1
iface tap1 inet manual
tunctl_user tuser

#stanza for w2ksp4 box
auto tap2
iface tap2 inet manual
tunctl_user tuser

#stanza for w2k3 box 
auto tap3
iface tap3 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  down ifconfig $IFACE down
  tunctl_user tuser

#stanza for Xubunt7.04-Desktop-LIVE
auto tap4 
iface tap4 inet manual
tunctl_user tuser

#stanza for PXE_Etherboot image
auto tap5
iface tap5 inet manual
tunctl_user tuser

auto bridge0
iface bridge0 inet static
 address 192.168.15.19
 netmask 255.255.255.0
 broadcast 192.168.15.255
 gateway 192.168.15.1
 bridge-ports eth0 tap1 tap2 tap3 tap4 tap5
 bridge-ageing 7200
 bridge-fd 0

```

Not quite sure I get that, I presume I would set the the hosts static IP in the bridge0 stanza? so I would have the following stanzas in my hosts interfaces file?:

```

auto tap0
iface tap0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  down ifconfig $IFACE down
  tunctl_user tuser

auto bridge0
iface bridge0 inet static
 address 87.127.87.186
 netmask 255.255.255.248
 broadcast 87.127.87.191
 gateway 87.127.87.185
 bridge-ports eth0 tap0
 bridge-ageing 7200
 bridge-fd 0

```

and replace tuser with my actual username?

And then on my guest OS I would have the following in my interfaces file?:

```

auto eth0
iface eth0 inet static
address 87.127.87.187
 netmask 255.255.255.248
 broadcast 87.127.87.191
 gateway 87.127.87.185

```

Is that correct?

Thanks for responding too.

Paladine
PS.  Beamerboy comes from my character name on Anarchy Online who amassed his wealth from making and selling a gun called a Perennium Beamer.  My next car will be an LWB Audi A8 :)

---

### Post by Peedy on 2007-09-13
I've just tried the process as stated in the first post, and I now have a direct connection to my router with ip 192.168.1.14 (static). But, now my Ubuntu (guest is what you call this?) installation doesn't have internet. I don't know what to look for or something..can somebody help me out?

I can't post my ifconfig, because I can't figure out how to copy my clipboard contents to the virtualbox......

But I'm using eth2 with IP 192.168.1.20, my br0 has IP 192.168.1.15, my tap0 has IP 192.168.1.22. At first I had eth2 on 192.168.1.15 also but that didn't work and neither does this...

---

### Post by Peedy on 2007-09-13
Ok I fixed my internet on my ubuntu installation again by removing all taps and bridges... now I am going to repeat the process and hope it will work :P

---

### Post by Mattallyc on 2007-09-16
Hi All,

Anyone having trouble with this might find an article titled "VirtualBox: Windows on Ubuntu" useful which can be found on page 98 of November 2007's issue of Linux Format.
It includes:
[LIST]
[*]Configuring USB and DVD Burning
[*]Setting up a TAP device (ideal for WLAN interface) on the Host
[*]Configuring XP to use the TAP device
[*]Configuring VirtualBox to run 'headless' and automatically start and more...
[/LIST]
I'm now about to give it a go - I'll let you know how I get on.
Cheers,
Matt.

---

### Post by siepo on 2007-09-17
For those people who prefer VMware-style host-only networking, without connecting virtual machines to the internet I list here my setup:

You need uml-utilities. Put the following lines in /etc/rc.local

tunctl -t tap0 -u <your_user_name>
/sbin/ifconfig tap0 172.16.18.1
chown root:uml-net /dev/net/tun
exit 0

and make rc.local executable. I give my virtual machine(s) static 172.16.18.x IP addresses. Nothing wrong with 192.168.15.x though

DON'T ADD ANYTHING TO /etc/network/interfaces; this network is a private affair.

For more simultaneous virtual machines, you can create a tap interface for each vm, and bundle those interfaces into a bridge. This requires bridge-utils in addition to uml-utilities. The code in rc.local now becomes

tunctl -t tap0 -u <your_user_name>
tunctl -t tap1 -u <your_user_name>

# bundle these tap interfaces into a bridge
brctl addbr br0
ifconfig tap0 0.0.0.0
brctl addif br0 tap0
ifconfig tap1 0.0.0.0
brctl addif br0 tap1
ifconfig br0 172.16.18.1

chown root:uml-net /dev/net/tun
exit 0

---

### Post by fjgaude on 2007-09-17
> **lamego said:**
> Whats the main advantages of VirtualBox compared to VMWare ?

All the things kilou said seem true... I've been using both VB and VM... for me the big differences are only two, one for each hypervisor: with VB you have only 10Mb NIC connections but 1000Mb with VM; VM USBs are 1.1, VB they are 2.0. I use VM mostly because I go to a raid5 array for graphic and photo data all the time. Need the throughput of over 100MB/sec.

That's it as far as I've found out.

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by finite9 on 2007-09-18
how do i use host networking if my NIC is a wireless 802.11g and Im using Network Manager exclusively?  I cannot really edit my interfaces file in this way to put the NIC in promiscuous mode etc without breaking my hosts network connection.

EDIT: I did follow the ubuntu wiki for getting bridged networking to work, but it only gets a 169.254.x.x address, not a 192.168.1.x address from my router...

QUESTION!  Where does it get the 169.254.x.x address from and why does it not get DHCP from my router??

---

### Post by jba6511 on 2007-09-26
the 169 address is a private address range assigned when a dhcp server can not be found. SOrry I can not be any more help as I am trying to figure this out myself.

This process works well but when I put the eth connection into promiscuous mode, I loose the network connection on my host. Is there a way to still maintain this connection so that I can have a virtual server and my host act as a client pc that connects to the server? Newbie here so bare with me as alot of this discussion is over my head.

---

### Post by jba6511 on 2007-09-28
can someone explain what these lines of code do and why a 192.168.0.94 address is used and then a .45? Is the .94 for the bridge -> which should be the same ip as the host and the .45 for the guest? I know they have something to do with setting the route and the address resolution protocol, but are they necessary if assigning a static ip instead of using dhcp?

sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.0.45 dev tap0
sudo arp -Ds 192.168.0.45 eth0 pub

---

### Post by jba6511 on 2007-09-28
[PHP]sudo tunctl -t tap0 -u blake
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth2 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth2
sudo ifconfig br0 192.168.1.101
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.1.104 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.1.101 dev tap0
sudo arp -Ds 192.168.1.101 eth2 pub[/PHP]

I have been running this script and can get network access on the guest but not the host once executed. My host ip is 192.168.1.101 and I want to make the guest 104. What am I doing wrong?

---

### Post by justask on 2007-09-30
> **siepo said:**
> For those people who prefer VMware-style host-only networking, without connecting virtual machines to the internet I list here my setup:

You need uml-utilities. Put the following lines in /etc/rc.local

tunctl -t tap0 -u <your_user_name>
/sbin/ifconfig tap0 172.16.18.1
chown root:uml-net /dev/net/tun
exit 0



I too prefer the vmware style host-only networking and have it setup like you've described.  It partly works. I can ping the host from the winxp guest but I cannot ping the host from the guest.  

siepo, what else do I need to check?

---

### Post by justask on 2007-10-01
> **justask said:**
> I too prefer the vmware style host-only networking and have it setup like you've described.  It partly works. I can ping the host from the winxp guest but I cannot ping the host from the guest.  

siepo, what else do I need to check?

I actually meant to say that I couldn't ping the guest from the host.  However, that was a firewall problem, now fixed.

---

### Post by CuBone on 2007-10-16
The first post in this thread works like a charm for me. My only problem is making it stick between host reboots. What do I have to do to make it work automagicly after a reboot of my ubuntu host?

---

### Post by ipguru99 on 2007-10-16
This is an example of the code that needs to be in the /etc/network/interfaces file

It came from here [http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/]("http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/")
```
uto tap0
iface tap0 inet manual
tunctl_user markus
uml_proxy_arp markus.bcs-it.loc
uml_proxy_ether eth0

auto tap1
iface tap1 inet manual
tunctl_user markus
uml_proxy_arp markus.bcs-it.loc
uml_proxy_ether eth0

auto tap2
iface tap2 inet manual
tunctl_user markus
uml_proxy_arp markus.bcs-it.loc
uml_proxy_ether eth0

auto br0
iface br0 inet dhcp
bridge_ports eth0 tap0 tap1 tap2
bridge_maxwait 0
```

---

### Post by ipguru99 on 2007-10-16
This is an example of the code that needs to be in the /etc/network/interfaces file

It came from here .. this allows you to reboot and maintain the settings
[http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/]("http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/")
```
uto tap0
iface tap0 inet manual
tunctl_user markus
uml_proxy_arp markus.bcs-it.loc
uml_proxy_ether eth0

auto tap1
iface tap1 inet manual
tunctl_user markus
uml_proxy_arp markus.bcs-it.loc
uml_proxy_ether eth0

auto tap2
iface tap2 inet manual
tunctl_user markus
uml_proxy_arp markus.bcs-it.loc
uml_proxy_ether eth0

auto br0
iface br0 inet dhcp
bridge_ports eth0 tap0 tap1 tap2
bridge_maxwait 0
```

---

### Post by dmcocca on 2007-10-27
I have two interfaces - one wired, one wireless.  I can get this to work easily via the wired ... but wireless doesn't work.  Anyone know what I'm doing wrong?

This is what my script looks lile

sudo tunctl -t tap1 -u $2
sudo ifconfig tap1 up
sudo chmod 0666 /dev/net/tun
brctl addbr br0
ifconfig $1 0.0.0.0 promisc
ifconfig tap1 0.0.0.0 promisc
brctl addif br0 $1
brctl addif br0 tap1
dhclient br0
~                     

So if $1 is eth0 (wired interface) and $2 is my login name, everything works fine.  If it is eth1 (wireless) I can't get an IP, nor ping anything (if I assign a static IP) from my guest OS (Windows XP).  The host OS (UBUNTO 7.10) works fine, but the guest has no networking.

This is my ifconfig before running the above script

eth0      Link encap:Ethernet  HWaddr 00:16:36:1E:0E:A3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:02:01:8F:F2  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe01:8ff2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101 errors:7 dropped:118 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15130 (14.7 KB)  TX bytes:12732 (12.4 KB)
          Interrupt:17 Base address:0xe000 Memory:54000000-54000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5176 (5.0 KB)  TX bytes:5176 (5.0 KB)

After the script

br0       Link encap:Ethernet  HWaddr 00:13:02:01:8F:F2  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe01:8ff2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4040 (3.9 KB)  TX bytes:4627 (4.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:36:1E:0E:A3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:02:01:8F:F2  
          inet6 addr: fe80::213:2ff:fe01:8ff2/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:151 errors:8 dropped:128 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21948 (21.4 KB)  TX bytes:16516 (16.1 KB)
          Interrupt:17 Base address:0xe000 Memory:54000000-54000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5176 (5.0 KB)  TX bytes:5176 (5.0 KB)

tap1      Link encap:Ethernet  HWaddr 00:FF:89:33:8A:DE  
          inet6 addr: fe80::2ff:89ff:fe33:8ade/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

brctl show

bridge name     bridge id               STP enabled     interfaces
br0             8000.0016361e0ea3       no              tap1
                                                        eth1


lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Any help would be GREATLY appreciated.

---

### Post by mk4umha on 2007-11-03
> **Mattallyc said:**
> Hi All,

Anyone having trouble with this might find an article titled "VirtualBox: Windows on Ubuntu" useful which can be found on page 98 of November 2007's issue of Linux Format.
It includes:
[LIST]
[*]Configuring USB and DVD Burning
[*]Setting up a TAP device (ideal for WLAN interface) on the Host
[*]Configuring XP to use the TAP device
[*]Configuring VirtualBox to run 'headless' and automatically start and more...
[/LIST]
I'm now about to give it a go - I'll let you know how I get on.
Cheers,
Matt.

Any new updates after reading that article?

---

### Post by dominicedmonds on 2007-11-07
I finally got all mine working wirelessly with some considerable help and I have posted my solution here: [http://ubuntuforums.org/showthread.php?t=543356](http://ubuntuforums.org/showthread.php?t=543356).

---

### Post by Achetar on 2007-11-15
Alright, so I am trying to ping the guest from the host, not working!

I followed the steps (only bump was needed to get uml-utilities package), and for the first time was able to boot with a Host Interface Network on VBox, but now I still can't ping it!

I would like to be able to ping, etc. as if the guest were a normal computer. Any help?

Thanks

---

### Post by anxean on 2007-11-18
Hey all the commands work but, "sudo /usr/sbin/brctl addbr br0"

I am in gutsy i suspect this is why.

Anyone know how to fix it?

---

### Post by shauns on 2007-11-25
Ok so i have read through 9 pages in this post. can anybody give me something that will work for wireless DHCP?

---

### Post by MarshallClan on 2008-01-12
Big Thanks to ipguru99 for setting the wheels in motion and to all you other folks for the details!

---

### Post by karyonix on 2008-01-15
Thank you, ipguru99.  Your HOWTO works for me.  
After testing it and trying some alternative methods, I have some suggestion.

> **ipguru99 said:**
> Some things to make this easier to read. My eth0 on my host is 192.168.0.45. My tap0 is going to get 192.168.0.94 (totally arbitrary.. ping it first, just to make sure it isn't in use). The "user" in the first command is the user you login with.
```
sudo tunctl -t tap0 -u user
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 [COLOR="DarkRed"]192.168.0.94[/COLOR] up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
[COLOR="DarkRed"]sudo route add -host 192.168.0.45 dev tap0[/COLOR]
[COLOR="DarkRed"]sudo arp -Ds 192.168.0.45 eth0 pub[/COLOR]

```

You do not need an IP address for tap0. Line 8 can be changed to "sudo ifconfig tap0 0.0.0.0 up".

What is the meaning of lines 10-11 when 192.168.0.45 is the host machine's IP address (not the guest's IP) ?
- I think "route add -host *host_ip* dev tap0" means "if someone here want to go to *host_ip*, go that way (tap0)."  
  But *host_ip* is here, you do not have to go through tap0 to get back here.  
- "arp -Ds *host_ip* eth0 pub" means "if anyone ask where *host_ip* is, tell him that it is here at HWaddr of eth0."  
  It is normal reply for arp requests. No need to tell the program to do its job.  
Lines 10-11 doesn't seems to make sense to me.  If the specified IP is guest OS's IP, it will look better.  However, the network runs well without these 2 commands.

Just run lines 1-9 (with changed line 8 ) then it should works.  But we now have another good method (modify /etc/network/interfaces) , we don't have to type these commands every time after reboot anymore.

---

### Post by ipguru99 on 2008-01-15
Sweet!  People keep adding stuff (or subtracting actually!) to this and it gets smaller and easier each time.

Thanks!

---

### Post by karyonix on 2008-01-23
If you create TAP/TUN interface and network bridge using **/etc/network/interfaces**, uml_proxy* lines are not needed.

My **/etc/network/interfaces** looks like this. 
```
auto lo
iface lo inet loopback

iface eth0 inet manual

auto tap0
iface tap0 inet manual
  tunctl_user *myusername*

auto br0
iface br0 inet dhcp
  bridge_ports eth0 tap0
  bridge_maxwait 0

```
The TUN/TAP interface must be created before the bridge starts ('auto tap0' before 'auto br0').  
The user account (*myusername*) must be a member of **vboxusers** and **uml-net** groups to be able to use tap0 wtith VirtualBox.  

My br0 get an IP address (192.168.x.x) automatically from DHCP server on another computer.  My guest OS also gets an IP address (192.168.x.x) automatically from the DHCP server and can communicate well with other computers on the network.  

My network use 2 subnet on the same LAN hardware, so I added another IP address from different subnet to the bridge interface by editing **/etc/network/interfaces** file and add these lines.
```
auto br0:1
iface br0:1 inet static
  address 10.0.0.99
  netmask 255.0.0.0
  gateway 10.0.0.9

```
Now my computer has 2 IP addresses and can communicate with both subnet. The virtual machine still communicates well like before.


To allow multiple users to run virtual machine with host network bridge, the file **/etc/network/interfaces** can be written like this. 
```
auto lo
iface lo inet loopback

iface eth0 inet manual

auto tap0 tap1 tap2 tap3
iface tap0 inet manual
  tunctl_user *cid*
iface tap1 inet manual
  tunctl_user *barret*
iface tap2 inet manual
  tunctl_user *cloud*
iface tap3 inet manual
  tunctl_user *cid*

auto br0
iface br0 inet dhcp
  bridge_ports eth0 tap0 tap1 tap2 tap3
  bridge_maxwait 0

```
*cid*, *barret*, *cloud* must be members of **vboxusers** and **uml-net** groups to use these TUN/TAP interface with VirtualBox. 

In this example, *cid* will be able to run 2 virtual machines that can communicate with each other, host machine, and other computers in the network (using tap0, tap3).
While one of *cid*'s virtual machine is running, if *cloud* comes and logon to his account, then  starts his virtual machine (using tap2), his virtual machine will be able to can communicate with *cid*'s virtual machine, host machine, and other machines on the network as well. 
I have not tried running more than 2 virtual machines at the same time.

---

### Post by irvin on 2008-02-07
Hallo

I read and tried a lot but I can't get it working after reboot:
I use Ubuntu 7.10 64bit and installed the deb package from virtualbox 1.5.4.
I installed bridge-utils + uml-utilities

Now I made this for networking:

sudo modprobe tun

sudo tunctl -u username -t tap0

sudo ifconfig tap0 0.0.0.0 promisc up

sudo tunctl -u username -t tap1

sudo ifconfig tap1 0.0.0.0 promisc up

sudo tunctl -u username -t tap2

sudo ifconfig tap2 0.0.0.0 promisc up

sudo chmod 0666 /dev/net/tun

sudo brctl addbr br0

sudo brctl addif br0 eth0

sudo brctl addif br0 tap0

sudo brctl addif br0 tap1

sudo brctl addif br0 tap2

sudo ifconfig br0 192.168.2.9 netmask 255.255.255.0 broadcast 192.168.2.255 up

sudo ifconfig eth0 0.0.0.0 promisc up

sudo route add default gw 192.168.2.1

+++
So, 192.168.2.9 ist my host ubuntu and i can give my VM's static IP's like 192.168.2.10 etc.

This works now ! Now I like to have this after reboot. I tried to add this to the rc.local file
(/etc/rc.local) but nothing works after reboot. I have to do it again !
This would not be the biggest prob, but if I make a reboot via vnc I cannot make this by hand cause after one of these commands the network dies and I can't reconnect.

this is what I added:

# For VirtualBox Host Interface Networking
/sbin/modprobe tun
/usr/sbin/tunctl -u username -t tap0
/sbin/ifconfig tap0 0.0.0.0 promisc up
/usr/sbin/tunctl -u username -t tap1
/sbin/ifconfig tap1 0.0.0.0 promisc up
/usr/sbin/tunctl -u username -t tap2
/sbin/ifconfig tap2 0.0.0.0 promisc up
/bin/chmod 0666 /dev/net/tun
/usr/sbin/brctl addbr br0
/usr/sbin/brctl addif br0 eth0
/usr/sbin/brctl addif br0 tap0
/usr/sbin/brctl addif br0 tap1
/usr/sbin/brctl addif br0 tap2
/sbin/ifconfig br0 192.168.2.9 netmask 255.255.255.0 broadcast 192.168.2.255 up
/sbin/ifconfig eth0 0.0.0.0 promisc up
/sbin/route add default gw 192.168.2.1

I also tried to make a bash script but nothing worked for me. Does anyone has an ides how to make this work after rebbot oder just a script which I can use to make these commands automatically.
Thanx
Irvin

---

### Post by karyonix on 2008-02-09
#92 irvin 
The scripts you wanted is already installed with packages bridge-utils and uml-utilities.    If you want to read these scripts, you can see them in subdirectories of /etc/network.  
Try these step to make it works after next boot.

Let the module tun be loaded automatically at startup.
Take a look at /etc/modules. If 'tun' is not already there, add it to the file.
```
sudo echo 'tun' >> /etc/modules
```

Make your *username* a member of **uml-net** group with this command.
```
sudo gpasswd -a *username* uml-net
```

And modify your network configuration file **/etc/network/interfaces** like this.
```

auto lo
iface lo inet loopback

iface eth0 inet manual

auto tap0 tap1 tap2
iface tap0 inet manual
  tunctl_user *username*
iface tap1 inet manual
  tunctl_user *username*
iface tap2 inet manual
  tunctl_user *username*

auto br0
iface br0 inet static
  bridge_ports eth0 tap0 tap1 tap2
  bridge_maxwait 0
  address 192.168.2.9
  netmask 255.255.255.0
  gateway 192.168.2.1

```

---

### Post by irvin on 2008-02-11
Hi "karyonix"

Many thanx for your help, I tried your settings but it didn't work for me. I'm sorry but I don't understand everything you wrote. I'm missing in your code who's makiing the bridge, may that's the problem ?

I'm just happy to have it run my way, but I need the autostart version ;-)

So many wrote it's working for them, but isn't it possible to make my commands automatically after reboot ?

Bye

---

### Post by irvin on 2008-02-11
Hallo

Now it works !!! I tried several things, don't know where my mistake really was ?

I did this now:

Make your username a member of uml-net group with this command.

sudo gpasswd -a username uml-net

and the edit or change the /etc/network/interfaces file like this:
Mine looks like this now:

----
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp

iface eth0 inet manual

auto tap0 tap1 tap2 tap3
iface tap0 inet manual
tunctl_user username
iface tap1 inet manual
tunctl_user username
iface tap2 inet manual
tunctl_user username
iface tap3 inet manual
tunctl_user username

auto br0
iface br0 inet static
address 192.168.2.9
netmask 255.255.255.0
gateway 192.168.2.1
bridge_maxwait 0
bridge_ports eth0 tap0 tap1 tap2 tap3
bridge_fd 0
----

Now I have my static ip for the host and taps for 4 guests with static ip's.
It works great !
Thanx again !!!

I only didn't do the "tun" in the modules and made a different order.

---

### Post by qopit on 2008-02-12
I've tried MKDon's method (post 56) of setting up host networking by doing the following...

```
sudo chown root:vboxusers /dev/net/tun
sudo tunctl -t tap1 -u qopit
sudo ip link set tap1 up
sudo ip addr add 192.168.1.201/24 dev tap1
sudo parprouted -p ra0 tap1

```
and it results in the following ifconfig output on my host pc:

```

eth1      Link encap:Ethernet  HWaddr 00:0E:35:D2:FE:F4  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fed2:fef4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8713 errors:2 dropped:2 overruns:0 frame:0
          TX packets:9257 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2234626805 (2.0 GB)  TX bytes:776806216 (740.8 MB)
          Interrupt:22 Base address:0xc000 Memory:c8400000-c8400fff 

eth2      Link encap:Ethernet  HWaddr 00:14:C2:D5:5F:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth2:avah Link encap:Ethernet  HWaddr 00:14:C2:D5:5F:A4  
          inet addr:169.254.8.200  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11129148 (10.6 MB)  TX bytes:11129148 (10.6 MB)

tap1      Link encap:Ethernet  HWaddr 00:FF:D9:00:23:BF  
          inet addr:192.168.1.201  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::2ff:d9ff:fe00:23bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:17 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:4718 (4.6 KB)  TX bytes:0 (0.0 b)

```

Seems reasonable and I can ping the address I created (192.168.1.201) from the host.  In addition, VB will start up properly when I connect host networking  to tap1 (and it fails if I specify something incorrect like tap2).

However - when I get into my guest system the guest can't actually connect... is there something I'm missing?  It all seemed so promising...

---

### Post by trifftruff on 2008-02-15
Hi,

I've tried everything, I use the /etc/network/interfaces for the setup it looks like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto tap0
iface tap0 inet manual
        tunctl_user {user}

auto br0
iface br0 inet static
        address 192.168.1.58
        network 192.168.1.0
        netmask 255.255.255.0
        gateway 192.168.1.1
        bridge_ports eth0 tap0
        bridge_maxwait 0
        brdige_fd 0

```

I use Debian etch 4.0 as guest operating system, I set tap0 for host networking in virtualbox, but after booting the guest, it doesn't have any ethernet cards. typing an ifconfig results in shoing the loop back device and that's it.

a little off topic, but once I maximized the virtualbox guest window. and  I have not found a way to unmaximize it. so I can not run it in a little window. any ideas?

---

### Post by trifftruff on 2008-02-15
I successfully reached that after (and even before) an:
apt-get purge uml-utilities bridge-utility

the guest OS doesn't even work with NAT. As I said, it doesn't have any network adapters shown, only the loop device.

---

### Post by karyonix on 2008-02-17
trifftruff
Make sure you have enabled network adapter in VirtualBox - Virtual Machine Settings - Network. 
If you already do that and it does not work even with NAT settings, try different guest OSes.

---

### Post by trifftruff on 2008-02-17
It has worked before with NAT, but I tried so many variations to use host interface and bridging (starting with the one in the virtualbox manual) and neither worked, that somehow I messed it up. I think I'll reinstall virtualbox and try again.

---

### Post by scaine on 2008-02-17
@trifftruff
Try changing your entry for eth0 from "manual" to "static".  A manual entry would require you to issue the "sudo ifconfig eth0 up" command, or "sudo ifup eth0" if you prefer.

This foxed me for a while too.

---

### Post by karyonix on 2008-02-19
trifftruff
It works with NAT but not works with host interface +/- bridging. Right?

Changing eth0 from 'manual' to 'static' is probably not helpful.  You don't need an IP address for eth0.  'auto br0' will cause the computer to execute 'ifconfig eth0 0.0.0.0 up', so you don't have to manually run it.  

Make sure you have installed **uml-utilities** and **bridge-utils** and your username is a member of **uml-net** group.

---

### Post by trifftruff on 2008-02-19
I completely uninstalled and purged uml-utilities and bridge-utils to clear everything. 
I suppose NAT should work without these!
But now even NAT doesn't work. with the basic
eth0 and loop device configured in
 /etc/network/interfaces file.

---

### Post by scaine on 2008-02-20
@trifftruff - post up your /etc/network/interfaces file.  I've got mine working now, but it took a lot of trial and error before it all fell into place.

For example, here's my file, with added comments:
```

#Keep the default loopback interface going :
iface lo inet loopback

# Bring up my main network interface, but don't give it an IP
address, and make it promiscious by default, so that it passes traffic
to/from the virtual machines without interfering :
auto eth1
iface eth1 inet static
	ifconfig eth1 0.0.0.0 up
	up ip link set eth1 promisc on
	down ip link set eth1 promisc off
	down ifconfig eth1 down

# I don't bring this broken network card up at all :
iface eth0 inet manual

#Bring up my tap interface, which I created using the VBoxAddIF
utility, hence the name vbox0 instead of the more common tap0
(that's the name the VirtualBox manual gives as an example):
auto vbox0
	iface vbox0 inet manual
	tunctl_user scaine

# Bring up my bridge.  It uses the address I used to have on eth1
(192.168.1.50) and the same gateway too (my ADSL router).  The
maxwait is zero, cos I don't care about spanning tree.
auto br0
iface br0 inet static
	address 192.168.1.50
	netmask 255.255.255.0
	gateway 192.168.1.1
	bridge-ports eth1 vbox0
	bridge_maxwait 0

```

Hope this helps.  Also, did you try uses static, instead of manual to bring up your main interface card on boot?

---

### Post by trifftruff on 2008-02-20
thank you for helping. I'll try this config, but my english seems to be too bad.
From the beginning:
I installed** Virtualbox**.
I set up an operating system (debian etch 4.0 as **guest**).
By default it used **NAT**. (without setting anything up in my
**host's /etc/network/interfaces** file)
Internet **worked properly** on both the **host and guest**.

**I tried** setting up the guest using **host interface**.
I tried first the way described in the virtualbox manual. Next an Ubuntu manual on the internet, I might use another one from howtoforge.
**But none of them worked**: I couldn't find any network interface in my **guest**. I'm not a linux guru, but I'm using it for a while, and can follow a guide properly!
** And now it doesn't work with NAT either:**
My host OS has Internet and local network.
But my guest doesn't have any network interfaces (cards) shown, and does not have internet connection.

Unfortunately, I don't have too much time nowadays. But I definitely want to try re-installing Virtualbox.

---

### Post by scaine on 2008-02-21
Ah right - I understand.  To be honest, it sounds more like you need to re-install your guest O/S than Virtual Box.  If your guest can't see ANY network, regardless of type of network chosen, then it's sounding like the guest has an issue.

Can you pop onto your guest when you get a minute and post back the results of an "ifconfig -a"?  Doesn't matter which method you try - I'm more curious to see what state the interfaces are in on the guest.

---

### Post by gwi on 2008-02-26
> **siepo said:**
> For those people who prefer VMware-style host-only networking, without connecting virtual machines to the internet I list here my setup:

You need uml-utilities. Put the following lines in /etc/rc.local

tunctl -t tap0 -u <your_user_name>
/sbin/ifconfig tap0 172.16.18.1
chown root:uml-net /dev/net/tun
exit 0

and make rc.local executable. I give my virtual machine(s) static 172.16.18.x IP addresses. Nothing wrong with 192.168.15.x though

DON'T ADD ANYTHING TO /etc/network/interfaces; this network is a private affair.

For more simultaneous virtual machines, you can create a tap interface for each vm, and bundle those interfaces into a bridge. This requires bridge-utils in addition to uml-utilities. The code in rc.local now becomes

tunctl -t tap0 -u <your_user_name>
tunctl -t tap1 -u <your_user_name>

# bundle these tap interfaces into a bridge
brctl addbr br0
ifconfig tap0 0.0.0.0
brctl addif br0 tap0
ifconfig tap1 0.0.0.0
brctl addif br0 tap1
ifconfig br0 172.16.18.1

chown root:uml-net /dev/net/tun
exit 0

How do I combine this with an existing vmnet1? I have some VMware virtual machines in a host only network (vmnet1, IP -address on the host 192.268.25.1). I want a VirtualBox virtual machine to become part of that host only network, so the VMware machines can communicatie with the VirtualBox machine (for testing purposes, maybe leading to migrating the Vmware machines to VirtualBox).

---

### Post by bodhi.zazen on 2008-02-26
ipguru99 (and others) FYI: The ubuntu wiki is user maintained :)

So, create an account on Launchpad and feel free to add information to the wiki :twisted:

See also : [http://www.virtualbox.org/wiki/Advanced_Networking_Linux](http://www.virtualbox.org/wiki/Advanced_Networking_Linux)

---

### Post by iNDEFiX on 2008-04-02
Hello guys,

very good topic, got a lot of things solved with your help :) I would like to share with you some testings I made during these weeks on virtualization in general. I am looking for a good solution to create virtual private servers (VPS) with linux mostly and windows. So I have tested almost all known software available for this work. Here are some results and opinions:

**VIRTUAL BOX (on Ubuntu & Linux Mint)**
-----------------------------------------------
Advantages:
- Very quick and easy to use 
- Good support and managment of virtual devices (cdrom, usb, audio etc)
- Windows are running extremly well!

Disadvantages:
- Cannot assign CPU and also slows down the host
- Cannot use partition for disk usage (only image available)


**XEN (on Fedora 7 - only tested with paravirtual mode)**
-----------------------------------------------
Advantages:
- Paravirtual mode is extremly good! Guest Fedora's are running very quick
- Can assign a disk partition or image file for disk usage
- Uses VNC connection and can be also accessed remotely
- Virtual manager showing utilization and info of guest OS 

Disantavtages:
- Some versions are not working quite well
- Not very good support of devices


**QEMU (on Fedora 7 & Ubuntu)**
-------------------------------------
Advantages:
- Very good for quick testings 

Disadvantages:
- Very slow on Windows install 
- No managment software


**VMware (on Fedora 7)**
---------------------------
Advantages:
- Very good administration panel (and web panel)
- Good support of most OS and devices

Disadvantages:
- Not very easy to setup
- Very slow on small servers

So, in conclusion I can suggest the following solutions:

1) If you plan to use Windows  as guest under a Linux host, Virtualbox is your best selection

2) If you plan to make VPS for business I suggest XEN on Fedora with Paravirtual mode

3) If you plan to use any OS as guest for home/test use I suggest Virtualbox  again

4) For testings and quick check of installations Qemu is the best (just one command to start the install)

---

### Post by karyonix on 2008-04-05
Hey iNDEFiX, VirtuaBox can use raw disk or raw partition. 
This feature is described in VirtualBox 1.5.6 User Manual section 9.9 "Using a raw host hard disk from a guest".

---

### Post by iNDEFiX on 2008-04-05
Thanks for the info karyonix! Will try it right now :)

Btw yesterday night I have installed Windows XP with Xen on a Quad Core (VT support). Too slow and not easy at all to setup windows... Virtualbox is still on the top

---

### Post by morris.johns on 2008-04-15
> **scaine said:**
> 
For example, here's my file, with added comments:
  ...SNIP...


thanks scaine : now my windows VirtualBox and Ubuntu have their own IP addresses (Ubuntu IP adress set up in file, windows IP adress set up as static address within windows).

I removed your redundant eth interface (ending up with the /etc/network/interfaces file below). Restarted Ubuntu and did:
sudo VBoxAddIF vbox0 {username} br1

```

iface lo inet loopback

auto eth0
iface eth0 inet static
	ifconfig eth0 0.0.0.0 up
	up ip link set eth0 promisc on
	down ip link set eth0 promisc off
	down ifconfig eth0 down

auto vbox0
	iface vbox0 inet manual

auto br1
iface br1 inet static
	address 192.168.10.4
	netmask 255.255.255.0
	gateway 192.168.10.1
	bridge-ports eth0 vbox0
	bridge_maxwait 0

```

I found this article really useful as well (using your changes to the interfaces file, trather than theirs which I couldnt get working):
[http://www.fsckin.com/2007/10/29/how-to-run-microsoft-outlook-natively-on-linux-using-virtualbox/](http://www.fsckin.com/2007/10/29/how-to-run-microsoft-outlook-natively-on-linux-using-virtualbox/)

---

### Post by iClou on 2008-05-03
Hi
Since 2 nights I try to get host-if running, without success - NAT is working fine.
[B]
On host ubuntu 8.04:[/B]
sudo tunctl -t tap0 -u sah
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.1.10 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.1.2 dev tap0
sudo arp -Ds 192.168.1.2 eth0 pub

**On host, ifconfig:**
br0       Link encap:Ethernet  HWaddr 00:1c:25:4e:65:e3  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe4e:65e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2301157 (2.1 MB)  TX bytes:165768 (161.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:1c:25:4e:65:e3  
          inet6 addr: fe80::21c:25ff:fe4e:65e3/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:3914 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3340153 (3.1 MB)  TX bytes:387716 (378.6 KB)
          Interrupt:254 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68700 (67.0 KB)  TX bytes:68700 (67.0 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:a9:54:0e:81  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2ff:a9ff:fe54:e81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:549 errors:0 dropped:45 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:7992 (7.8 KB)  TX bytes:33242 (32.4 KB)

**On host - route:**
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
cetus2          *               255.255.255.255 UH    0      0        0 tap0
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
192.168.1.0     *               255.255.255.0   U     0      0        0 tap0
default         B37_1           0.0.0.0         UG    0      0        0 br0

**On guest** - ubuntu 8.04 server I have no route at all.
Any help or idea how to solve it is very much appreciated.
--
Best regards,
Mike

---

### Post by iClou on 2008-05-04
Hi all

I found a very elegant way to achieve HostInterface with VirtualBox - it works like a charm!
See here:
[http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/](http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/)
--
Best regards,
Mike

---

### Post by leetcharmer on 2008-05-05
> **morris.johns said:**
> thanks scaine : now my windows VirtualBox and Ubuntu have their own IP addresses (Ubuntu IP adress set up in file, windows IP adress set up as static address within windows).

I removed your redundant eth interface (ending up with the /etc/network/interfaces file below). Restarted Ubuntu and did:
sudo VBoxAddIF vbox0 {username} br1

```

iface lo inet loopback

auto eth0
iface eth0 inet static
	ifconfig eth0 0.0.0.0 up
	up ip link set eth0 promisc on
	down ip link set eth0 promisc off
	down ifconfig eth0 down

auto vbox0
	iface vbox0 inet manual

auto br1
iface br1 inet static
	address 192.168.10.4
	netmask 255.255.255.0
	gateway 192.168.10.1
	bridge-ports eth0 vbox0
	bridge_maxwait 0

```

I found this article really useful as well (using your changes to the interfaces file, trather than theirs which I couldnt get working):
[http://www.fsckin.com/2007/10/29/how-to-run-microsoft-outlook-natively-on-linux-using-virtualbox/](http://www.fsckin.com/2007/10/29/how-to-run-microsoft-outlook-natively-on-linux-using-virtualbox/)

This worked until I upgraded to 1.6.0 -- now I get 'limited or no connectivity' under Windows XP.  Not quite sure where to begin.

---

### Post by dlugidll on 2008-05-11
im confirm this isue

---

### Post by slusig on 2008-05-11
I tried to get host networking working with Virtual Box 1.6 and 8.04 for a couple hours today, but I was never able to get it working. ](*,)

I tried to follow the instructions in the manual and in this thread, but couldn't get things working.  Would really appreciate it if someone could provide step-by-step instructions.

---

### Post by agim on 2008-05-11
great post. Can't wait to try it out.

---

### Post by dlugidll on 2008-05-12
**[SIZE="4"] i have works virtualbox 1.6 with bridge on ubuntu 8.04[/SIZE]**

set virtualbox  network to NAT
boot windows
1. download drivesr for intel 82540em from 
[http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=871]("http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=871")

set in vurtualbox adapter type - > intel pro/1000 mt desktop 82540EM
in interface name set tap0
boot windows with this setings in virtualbox
now install drivers for intel adapter because windows dont know this network adapter 

now bridge works fine for me
this method too
[http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/]("http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/")

i have read this

[http://steveballantyne.blogspot.com/2008/04/virtualbox-with-multiple-bridged.html]("http://steveballantyne.blogspot.com/2008/04/virtualbox-with-multiple-bridged.html")
and
[http://forums.virtualbox.org/viewtopic.php?p=22164#22164]("http://forums.virtualbox.org/viewtopic.php?p=22164#22164")

> I initially had a problem with the AMD NIC after any upgrade from 1.5.6 to 1.6.0 on a CentOS host and a WinXP guest.

I shutdown the WinXP VM and created a shared folder on the host and downloaded the Intel driver for WinXP from here for the Intel NIC:

[http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=871](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=871)

I then adjusted the VM NIC settings and picked the Intel NIC.

After I installed the new drivers from the Shared Folder for the Intel NIC, it seems to work OK on hard boots and on soft reboots.

---

### Post by Thomy23 on 2008-05-15
Hello

I have set up Virtualbox on my kubuntu 8.04 host running an ubuntu 8.04 guest OS. I tried to install and set up the bridge but i can't get access inside my guest OS. Here's my /etc/network/interfaces:

```



auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet manual

auto tap0
iface tap0 inet manual
        #up ifconfig $IFACE 0.0.0.0 up
        #down ifconfig $IFACE down
        tunctl_user stather

auto br0
iface br0 inet dhcp
        bridge_ports eth0 tap0
        bridge_maxwait 0


```

and heere ifconfig:

```


br0       Link encap:Ethernet  Hardware Adresse 00:1a:a0:51:50:27
          inet Adresse:141.12.90.43  Bcast:141.12.91.255  Maske:255.255.252.0
          inet6-Adresse: fe80::21a:a0ff:fe51:5027/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:2352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1241 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:979041 (956.0 KB)  TX bytes:251800 (245.8 KB)

eth0      Link encap:Ethernet  Hardware Adresse 00:1a:a0:51:50:27
          inet6-Adresse: fe80::21a:a0ff:fe51:5027/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:2424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1257 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:1028245 (1004.1 KB)  TX bytes:257331 (251.2 KB)
          Interrupt:16

lo        Link encap:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:18184 (17.7 KB)  TX bytes:18184 (17.7 KB)

tap0      Link encap:Ethernet  Hardware Adresse 00:ff:b8:e3:cc:3a
          inet6-Adresse: fe80::2ff:b8ff:fee3:cc3a/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4222 errors:0 dropped:1358 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:500
          RX bytes:15175 (14.8 KB)  TX bytes:427606 (417.5 KB)


```

Is it normal for the bridge that eth0 and tap0 don't get an IP adress at all? Needn't they have the host IP address of the bridge?



Greets

Thomy

---

### Post by sgperkins on 2008-05-17
Just to say thanks to everyone for a very useful thread. 

One point though is that if, like me, you only want to be able to connect host->guest, guest->guest, or guest->host for development/testing purposes, you can leave out the physical adapter from the bridge, and assign it (the bridge) and the guest OSs static IP's on the same (new and unused) subnet which leaves just the host and guests in a completely internal network, somewhat like vmware. You can then add a second network card to the guest set up as NAT if the it also requires Internet access.

Not much difference, but it makes life easier, especially if you are constantly on the move and the DHCP on the physical adapter is constantly changing, or if you just don't want the guests on the external network at all.. 

So in my interfaces file I have :

```
auto tap0
iface tap0 inet manual
    tunctl_user steve
    uml_proxy_arp sativex-ub

# Create bridge and attach tap0
auto br0
iface br0 inet static
    address 192.168.101.2
    netmask 255.255.255.0
    gateway 192.168.101.254
    broadcast 192.168.101.255
    bridge_ports tap0
    bridge_maxwait 0

```

which in my case creates a routing table of 

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.101.0   *               255.255.255.0   U     0      0        0 br0
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 br0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

Only a little thing, but it might be useful to someone out there.

---

### Post by Kalinda on 2008-05-18
Hello,

Okay, I tried to get host networking to work using the howto on the community docs, but it didn't... and now NAT no longer works in my Windows XP VM. I uninstalled the VM and reinstalled and it still didn't work...

Then I went back to the howto and proceeded to undo all the stuff I had done and it still won't work.

I have a static IP in Kubuntu and my inernet is working fine over here; during my fiddling, I made no changes to my interfaces file. I can also access my router and ping my IP in my VM, but if I try to ping google it doesn't work.

I don't really care about host networking anymore, I just want my VM to have internet with NAT again, since I really need it.

Can anyone help me?

---

### Post by sgperkins on 2008-05-18
Have you tried actually surfing to the site, or running NSLOOKUP. ICMP (ping) doesn't work in VBOX over NAT. Well, its kind of unreliable. 
I make that mistake all the time ...

---

### Post by qyzhh on 2008-05-19
now, virtualbox is "Sun xVM VirtualBox"

---

### Post by c49doug on 2008-05-20
I have gotten the host interface to work with my XP guest using VirtualBox 1.6 running on Hardy Heron. My problem occurs when I reboot the system, the settings don't stick.

---

### Post by Kalinda on 2008-05-21
> **c49doug said:**
> I have gotten the host interface to work with my XP guest using VirtualBox 1.6 running on Hardy Heron. My problem occurs when I reboot the system, the settings don't stick.
Yes, that's because you have to edit your /etc/networking/interfaces file to include the bridge. Check the VirtualBox manual for Host Networking and read the info on making it permanent.

My only problem is that I did make it permanent, switched to DHCP (it worked!), and then a few days later I lost my internet, so I switched back to static IP and killed the bridge.

Right now my VM still has no internet and I'm not going to risk screwing around with the interfaces file while on static IP because last time I did it killed my internet and I had to switch to DHCP to make it work again.

Sgperkins, what exactly is NSLOOKUP and how do I run it? It appears to be some sort of DNS lookup tool, but could I have some more info please? And yes, I did try surfing the web; the VM gets no internet at all.

---

### Post by driise on 2008-05-25
> **dlugidll said:**
> **[SIZE="4"] i have works virtualbox 1.6 with bridge on ubuntu 8.04[/SIZE]**

set virtualbox  network to NAT
boot windows
1. download drivesr for intel 82540em from 
[http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=871]("http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=871")

set in vurtualbox adapter type - 
in interface name set tap0
boot windows with this setings in virtualbox
now install drivers for intel adapter because windows dont know this network adapter 

now bridge works fine for me
this method too
[http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/]("http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/")

i have read this

[http://steveballantyne.blogspot.com/2008/04/virtualbox-with-multiple-bridged.html]("http://steveballantyne.blogspot.com/2008/04/virtualbox-with-multiple-bridged.html")
and
[http://forums.virtualbox.org/viewtopic.php?p=22164#22164]("http://forums.virtualbox.org/viewtopic.php?p=22164#22164")

After switching to the intel NIC, and installing the drivers, I was up and running!  Thank you so much!

I believe this will work with just about any method you choose to build the br0 and tap0 interfaces.

edit - spoke too soon, it was working, I rebooted the xp guest a few times, then rebooted ubuntu (8.04) host and it is broke yet again.  I read on the virtualbox forms that this is a known issue and fixed in 1.6.2, but I can't find where to download it (the 'closed' version as I need USB support).  Sadly, Virtualbox doesn't seem to be ready for prime time.

---

### Post by gpan on 2008-05-28
Hello everyone. I have three virtual machines (windows server, xp and debian) running in Sun x86 Virtualbox and I would like someone to give me some instructions about how to create a virtual local network. I want these machines to be able to ping each other. Any help would be highly appreciated. Thanks!:(

---

### Post by orbitron on 2008-05-29
This walkthrough worked like a charm **but** now DNS doesn't resolve properly from the ubuntu console.

When I try to ping or nslookup yahoo.com from the ubuntu command line nothing comes up.  When I try to ping yahoo.com's IP address (66.94.234.13) it works fine.

Any suggestions???

---

### Post by dinxter on 2008-05-30
> **driise said:**
> After switching to the intel NIC, and installing the drivers, I was up and running!  Thank you so much!

I believe this will work with just about any method you choose to build the br0 and tap0 interfaces.

edit - spoke too soon, it was working, I rebooted the xp guest a few times, then rebooted ubuntu (8.04) host and it is broke yet again.  I read on the virtualbox forms that this is a known issue and fixed in 1.6.2, but I can't find where to download it (the 'closed' version as I need USB support).  Sadly, Virtualbox doesn't seem to be ready for prime time.


From the virtualbox tickets, release date for 1.6.2 is officially "a day or 2" from today :)

---

### Post by john_navarro on 2008-06-06
I got Host Networking working real easy following the instructions here:

[http://spinczyk.net/blog/2008/03/05/setting-up-a-bridged-network-for-virtualbox-on-ubuntu-linux/](http://spinczyk.net/blog/2008/03/05/setting-up-a-bridged-network-for-virtualbox-on-ubuntu-linux/)

---

### Post by astranberg on 2008-06-23
Wow after hours of struggling with this, I finally copied almost verbatim from sgperkins config and my host network is right as rain!  I had been trying to force an IP on the vbox interface using a rc.local ifconfig, not realizing it should be on the br0 int. Thanks to all of the folks who forged the way on this.

-Aaron

> **sgperkins said:**
> Just to say thanks to everyone for a very useful thread. 

One point though is that if, like me, you only want to be able to connect host->guest, guest->guest, or guest->host for development/testing purposes, you can leave out the physical adapter from the bridge, and assign it (the bridge) and the guest OSs static IP's on the same (new and unused) subnet which leaves just the host and guests in a completely internal network, somewhat like vmware. You can then add a second network card to the guest set up as NAT if the it also requires Internet access.

Not much difference, but it makes life easier, especially if you are constantly on the move and the DHCP on the physical adapter is constantly changing, or if you just don't want the guests on the external network at all.. 

So in my interfaces file I have :

```
auto tap0
iface tap0 inet manual
    tunctl_user steve
    uml_proxy_arp sativex-ub

# Create bridge and attach tap0
auto br0
iface br0 inet static
    address 192.168.101.2
    netmask 255.255.255.0
    gateway 192.168.101.254
    broadcast 192.168.101.255
    bridge_ports tap0
    bridge_maxwait 0

```

which in my case creates a routing table of 

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.101.0   *               255.255.255.0   U     0      0        0 br0
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 br0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

Only a little thing, but it might be useful to someone out there.

---

### Post by cuby on 2008-06-26
Thanks man! it worked!

---

### Post by foxmajik on 2008-07-12
Confirmed working on hardy with xpsp2 guest on virtualbox 1.6.2.

---

### Post by ctothej on 2008-10-13
Can someone please explain in detail that interfaces file. I understand the basics of bridging and ip addressing, but I'd really like to know how the tap interface is assigned an ip address on the local machine yet still needs to be assigned an ipaddress by the guest OS or given one via DHCP.

---

### Post by xaprb on 2008-10-14
I made a quick script to do this on my laptop:

#!/bin/sh

set -e
set -u
set -x

sudo tunctl -t tap0 -u `whoami`
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.1.51 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
IP=`ifconfig | grep inet | head -n 1 | awk '{print $2}' | cut -d: -f2`
sudo route add -host $IP dev tap0
sudo arp -Ds $IP eth0 pub

---

### Post by bkraptor on 2008-11-14
I roam a lot with my laptop, so I kinda need to change settings a lot. I've developed a script based on a lot of what's been posted here for setting up a TAP device before starting up my machine, and for deleting the TAP after I've stopped the machine.
```

#!/bin/bash

HOST_IP_DHCP="0"
HOST_IP="10.0.0.200"
HOST_NETMASK="255.255.255.0"
HOST_GATEWAY="10.0.0.202"
HOST_IF="eth0"
BRIDGE_IF="br0"
GUEST_IF="$2"
USERNAME="user_goes_here"


case "$1" in

start)
	echo "Starting bridge for TAP device $GUEST_IF..."

	sudo /usr/sbin/brctl addbr $BRIDGE_IF
	sudo /sbin/ifconfig $HOST_IF 0.0.0.0 promisc up
	sudo /usr/sbin/brctl addif $BRIDGE_IF $HOST_IF

	if [ $HOST_IP_DHCP -eq 0 ]; then
		sudo /sbin/ifconfig $BRIDGE_IF $HOST_IP netmask $HOST_NETMASK
		sudo /sbin/route add default gw $HOST_GATEWAY
	else
		sudo /sbin/dhclient $BRIDGE_IF
	fi

	sudo tunctl -t $GUEST_IF -u $USERNAME
	sudo /sbin/ifconfig $GUEST_IF 0.0.0.0 promisc up	
	sudo /usr/sbin/brctl addif $BRIDGE_IF $GUEST_IF

	# is this really needed any more?
	sudo chmod 666 /dev/net/tun
	
	#apparently this is not needed
	#sudo su -c "echo 1 > /proc/sys/net/ipv4/conf/$GUEST_IF/proxy_arp"

	echo "Done!"
;;
stop)
	echo "Stopping bridge for TAP device $GUEST_IF..."
	sudo /usr/sbin/brctl delif $BRIDGE_IF $HOST_IF
	sudo /usr/sbin/brctl delif $BRIDGE_IF $GUEST_IF
	sudo /sbin/ifconfig $BRIDGE_IF down
	sudo /usr/sbin/brctl delbr $BRIDGE_IF

	#apparently this is not needed
	#sudo su -c "echo 0 > /proc/sys/net/ipv4/conf/$GUEST_IF/proxy_arp"

	sudo /sbin/ifconfig $GUEST_IF down
	sudo tunctl -d $GUEST_IF

	# is this really needed any more?
	sudo chmod 660 /dev/net/tun

	if [ $HOST_IP_DHCP -eq 0 ]; then
		sudo /sbin/ifconfig $HOST_IF $HOST_IP netmask $HOST_NETMASK
		sudo /sbin/route add default gw $HOST_GATEWAY
	else
		sudo /sbin/dhclient $HOST_IF
	fi
	
	echo "Done!"
;;
*)
	echo "Usage: $0 <start/stop> <tap_name>"
	echo "Example: $0 start tap0"
;;
esac

exit 0

```

Example of usage:
# ./script.sh start tap0
# ./script.sh stop tap0

Host IP address, mask and gateway are only used if HOST_IP_DHCP is 0.


What I would really like is to keep eth0 bound to br0, have Network Manager be able to manage br0 as if it were eth0 and then only use the portion of the script that deals with setting up and tearing down the TAP interface, and using that in VirtualBox. Does anyone know how to do that?

---

### Post by JapanFred on 2008-12-21
Hi guys,

Got mine working using this post i found...

[http://www.spikedsoftware.co.uk/blog/index.php/2008/12/14/suns-virtualbox-ubuntu-64bit-intrepid-ibex/](http://www.spikedsoftware.co.uk/blog/index.php/2008/12/14/suns-virtualbox-ubuntu-64bit-intrepid-ibex/)

Cheers!

---

### Post by skao on 2008-12-21
Hi everyone

My Virtualbox NAT guest networking is working fine, and I try to setup my Host networking, but I have some problem, I am unable to setup the bridge the following is my interfaces file

```

auto lo
iface lo inet loopback

iface eth0 inet static
address 10.0.0.4
netmask 255.0.0.0
gateway 10.0.0.138

auto eth0

iface tap0 inet static
address 10.0.0.7
netmask 255.0.0.0
gateway 10.0.0.138
tunctl_user stephen

auto tap0

#iface br0 inet static
#address 10.0.0.67
#network 10.0.0.0
#broadcast 10.255.255.255
#netmask 255.0.0.0
#getway 10.0.0.138
#bridge_ports eth0 tap0

#auto br0

```
The bridge section is comment out is because if I enable it my host network will no longer work (i.e. unable to access internet, unable to ping other machine on my LAN) but if the bridge is disable the host network (eth0) is working fine and the tap0 interface also working find as well.

Did I miss something here

Thanks for your help

Stephen

---

### Post by bodhi.zazen on 2008-12-21
With the most recent version of Virtualbox, 2.1.0, this entire thread is out dated.

It may take a while for the Ubuntu repo (OSE) edition to catch up.

With VirtualBox 2.1.0 you simply select host networking and select your network card (eth0 , wlan0, etc) from the pull down list.

No need to manually bridge your network card, not need for a tap, although you can use these devices if you wish.

See the VirtualBox users Guide for details.

[http://download.virtualbox.org/virtualbox/2.1.0/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.1.0/UserManual.pdf)

---

### Post by scaine on 2008-12-21
So, bodhi.zazen, just to clarify, once you chose the network connection from the drop down, VirtualBox somehow auto-configures that connection as a bridge?

I have to admit, I can't see how Virtual Box would get around the need for bridges?  I mean, for basic NAT operation, sure - easy.  But what we were discussing on this thread (months ago) is the creation of a virtual machine that can accept incoming conections - like a web server, for example.

Sounds great if it works like you say though.

---

### Post by bodhi.zazen on 2008-12-21
> **scaine said:**
> So, bodhi.zazen, just to clarify, once you chose the network connection from the drop down, VirtualBox somehow auto-configures that connection as a bridge?

I have to admit, I can't see how Virtual Box would get around the need for bridges?  I mean, for basic NAT operation, sure - easy.  But what we were discussing on this thread (months ago) is the creation of a virtual machine that can accept incoming conections - like a web server, for example.

Sounds great if it works like you say though.

That is how it works. If you wish to know the details, check out the VirtualBox User Manual (PDF) I linked, I think the networking section is less then 5 pages.

I believe Virtualbox now automatically bridges your network card, similar to VMWare. Also there have been changes to how NAT works.

And yes, it is much easier. Again, in the network tab, select Host networking -> then select eth0 (or wireless, or whatever).

Again, there is not need to manually create a bridge, it is now handled "automagically".

If you wish to install the newest version, purge the old first.

And again OSE will lag behind ...

---

### Post by scorp123 on 2008-12-21
> **bodhi.zazen said:**
> That is how it works. Not really. It's a bit more elegant than that :)

> **bodhi.zazen said:**
>  I believe Virtualbox now automatically bridges your network card, similar to VMWare.  No. It's even better IMHO. :D VMware creates separate network interfaces: **vmnet0** for bridging, **vmnet1** for host-only, **vmnet8** for NAT ... depending on the other applications you have on your system they might get confused by the presence of these interfaces.

VirtualBox 2.1.0 is more elegant than that: it does not need create extra interfaces anymore. Therefore it has also stopped to mess up NetworkManager ... the two now "just work" side by side. It's super duper cool. What VirtualBox now does is that it creates a "netfilter" ... it's comparable to sniffing network traffic and having a firewall. It filters out traffic that wants to reach your bridged VM from the physical interface, and when your VM wants to talk to the rest of the world VirtualBox injects appropriate packets onto your network. All this is handled by a new kernel module (= "device driver" in Windows-speak) called **"vboxnetflt"** .... when you do a "**lsmod**" to check for the loaded modules you will notice that one. If it's loaded then it means that VirtualBox is ready for it's new bridged networking magic :D

It's really really cool and very elegant. The thing even works with Wireless interfaces.

> **bodhi.zazen said:**
>  And yes, it is much easier.  Absolutely!!! It's so easy my wife (= total utter complete nooob!!) can use this. No kidding. :D

Here is a posting that explains how to get SUN's xVM VirtualBox repository ... installing VirtualBox 2.1.0 is very easy then, plus: if there are any updates you will be automagically be notified:

[http://ubuntuforums.org/showpost.php?p=6332363&postcount=16](http://ubuntuforums.org/showpost.php?p=6332363&postcount=16)

---

### Post by celem on 2008-12-21
Wonderful - thank you. Your instructions worked like a charm and solved a problem that had really been frustrating me.

---

### Post by albinootje on 2008-12-21
> **ipguru99 said:**
> 
With VirtualBox 2.1.0 you simply select host networking and select your network card (eth0 , wlan0, etc) from the pull down list.

**No need to manually bridge your network card, no need for a tap**, although you can use these devices if you wish.

See the VirtualBox users Guide for details.

[http://download.virtualbox.org/virtualbox/2.1.0/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.1.0/UserManual.pdf)

Thanks for the info. Super cool news !!! :) :) :)

---

### Post by eko291 on 2009-02-09
Same goes for me.  This has been driving me crazy and I can't believe how easy it was. thanks!

> **celem said:**
> Wonderful - thank you. Your instructions worked like a charm and solved a problem that had really been frustrating me.

---

### Post by slw4qd on 2009-04-23
I'm using 2.0.4_OSE/Ubuntu 8.10. The post helped me solve the network bridging problem in minutes. 

To use tunctl and brctl mentioned in the command list, you have to: 
> apt-get install uml-utilities bridge-utils

Thanks!

---

### Post by burkas on 2009-07-29
I just add a script. One of them is for add tap whatever you like...
[LINK]("http://lgibm.wordpress.com/files/2009/07/virtualnetwork.odt")

---

### Post by bodhi.zazen on 2009-07-29
> **burkas said:**
> I just add a script. One of them is for add tap whatever you like...
[LINK]("http://lgibm.wordpress.com/files/2009/07/virtualnetwork.odt")

That is a very nice script, I add some of that , especially bringing up a bridge, in /etc/network/interfaces and would use the script only to add a tap.

At any rate , such a script is no longer necessary for VirtualBox, can be helpful if you use kvm, although there are script for kvm networking as well (/etc/kvm-ifup /etc/kvm-ifdown).

---

### Post by burkas on 2009-07-29
@bodhi.zazen
thx bodhi, i never heard about kvm networking. I'm searching it in google now.

---

