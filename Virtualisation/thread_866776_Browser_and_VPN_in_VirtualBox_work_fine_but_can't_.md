---
title: "Browser and VPN in VirtualBox work fine but can't broswe using ubuntu"
date: 2008-07-22
forum: Virtualisation
---

### Post by Chosen320 on 2008-07-22
Yesterday I tried connecting my Windows XP install in VirtualBox to my office VPN. I then discovered NAT wouldn't allow this and set up hosted networking as described by the Virtual Box manual (somwhere around page 65).

My steps were as follows

In a terminal:
```
sudo apt-get install bridge-utils
sudo gedit /etc/network/interfaces
```

I then added the following to the file
```
auto br0
iface br0 inet dhcp
    bridge_ports eth0
```

In a terminal:
```
sudo /etc/init.d/networking  restart
sudo VBoxAddIF vbox0 gareth br0
```

I then changed the VirtualBox device to use the newly set up vbox0.

I started up my Windows XP VirtualBox and everything worked perfectly. I could connect to my office VPN as well as resolve network addresses etc.

I could also browse normally from Ubuntu using firefox and download torrents using Transmission.

This morning I booted up and now everything in VirtualBox is still working 100% but in Ubuntu niether Firefox or Transmission are able to get an internet connection. 

Any ideas why?

Here is my ifconfig 

```
br0       Link encap:Ethernet  HWaddr 00:1c:c0:26:bd:3f  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe26:bd3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:512087 (500.0 KB)  TX bytes:259467 (253.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:26:bd:3f  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe26:bd3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:24271868 (23.1 MB)  TX bytes:4525812 (4.3 MB)
          Memory:53200000-53220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110628 (108.0 KB)  TX bytes:110628 (108.0 KB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:e7:21:0f:0b  
          inet6 addr: fe80::2ff:e7ff:fe21:f0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28455 errors:0 dropped:48 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:4188580 (3.9 MB)  TX bytes:23608823 (22.5 MB)

```



I'm still a newbie so forgive me if the answer seems obvious.


Regards,
Chosen

---

### Post by nelfer on 2008-07-23
Coincidentally, I'm having the similar problem. I can connect to the VPN but cannot RDP (hosts do not get resolved or there is some sort of conflict I guess). But now you enlighted me on doing the bridged network instead of NAT.
Thanks.

I'll post my results later.

---

### Post by estyles on 2008-08-05
EDIT: Spoke too soon!  This seemed to be working for me, but once I restarted, it isn't working correctly.  I need to figure out what is wrong and post some corrections, I guess.  Anyone out there that can help?



Did you ever figure this out?  I had essentially the same problem (eventually, once I figured out from your post that I actually had to create a bridge connection in order to use my VM the way I wanted to), and finally found the solution on this page: [https://help.ubuntu.com/community/VirtualBox#Automate%20The%20Process](https://help.ubuntu.com/community/VirtualBox#Automate%20The%20Process).  You should be able to delete the br0 lines from /etc/network/interfaces, then add ```
auto tap1
iface tap1 inet manual
up ifconfig $iface 0.0.0.0 up
down ifconfig $iface down
tunctl_user USERNAME <-- replace USERNAME with your user
```

Then create a bash script for BridgeUp and BridgeDown.

/etc/network/BridgeUp.sh```
#! /bin/bash
sudo tunctl -t tap1 -u estyles
sudo chown root.vboxusers /dev/net/tun
sudo chmod g+rw /dev/net/tun
sudo brctl addbr br0
sudo ifconfig eth0 0.0.0.0 promisc
sudo brctl addif br0 eth0
sudo dhclient br0
sudo brctl addif br0 tap1
sudo ifconfig tap1 up
```

/etc/network/BridgeDown.sh```
#! /bin/bash
sudo ifconfig tap1 down
sudo ifconfig br0 down
sudo brctl delbr br0
sudo dhclient eth0
```

I then made a shell script to start my virtual machine (startvm.sh) that does the following:

~/startvm.sh
```
#! /bin/bash
gksudo /etc/network/BridgeUp.sh
vboxmanage startvm WinXP  #<-- replace with the name of your VM
gksudo /etc/network/BridgeDown.sh
```

Then a made a launcher on my desktop that runs /home/$USER/startvm.sh

I haven't tested the shell script to make sure that it brings the bridge down correctly, but honestly, it shouldn't be that important, since as far as I can tell, so far, I can use both connections while the bridge is up.

I figure you've probably solved this by now, but at least if someone else has the same problem and puts in the same search terms that led me to your thread, hopefully this will help them.  And now that I've posted it, it'll be easier for *me* to find when I need to fix this again...  :biggrin:

edit: a few mistakes in here.  also a few notes that I skipped: 1) to make the scripts executable (for those who don't know) you need to do ```
chmod u+x /etc/network/Bridge*
chmod u+x ~/startvm.sh.
```  2) if tunctl doesn't work, you need to ```
sudo apt-get install uml-utilities
```

---

### Post by estyles on 2008-08-05
Okay, well, now it works, and I have no idea why.  I did what I posted above, then it worked, then it didn't work, and now it's working.  :confused:

Anyway, one thing I did forget to mention was that you have to change the network in VirtualBox to use Hosted Network->tap1, instead of NAT.  Also, there are boxes in VirtualBox setup for putting in scripts to be run to setup and shutdown the network, so I would tend to use those instead of the bash script that I setup (I'm planning on doing that soon, but since it's working right now and I need to do some work, I don't want to mess with it)...

---

### Post by Chosen320 on 2008-08-06
Ok, still havn't got a permanent fix but I did find that sometimes it worked and sometimes it didn't.

Sometimes only the Virtual Box had access to the web and at other times only Ubuntu.

What I do however now as my temporary solution is that before I startup my virtual box I quickly run the last two lines from the Virtual Box manual as perviously posted. 

```
sudo /etc/init.d/networking  restart
sudo VBoxAddIF vbox0 gareth br0
```

As long as I run those 2 commands then both Ubuntu and my WinXP Virtual Box get access to the world wide web.

---

