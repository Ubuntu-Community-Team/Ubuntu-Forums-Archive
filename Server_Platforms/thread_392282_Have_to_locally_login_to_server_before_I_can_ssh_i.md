---
title: "Have to locally login to server before I can ssh in on startup"
date: 2007-03-24
forum: Server Platforms
---

### Post by Skeletor on 2007-03-24
I just installed a LAMP server on Ubuntu server 6.10.  I've setup a static IP address for the server and installed" ssh-server", and updated the server using apt-get update/upgrade.  I followed the instructions on:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4)
to setup the networking and such.  Although, I used the default install of the LAMP server from the Ubuntu CD instead of installing everything myself as the website tutorial suggests.  

My problem is that once I turn the power of the server off and restart, I cannot ssh into the machine until I locally login on that machine first.  That is, I restart the server and I cannot ssh into it.  But if I were to plug a keyboard and monitor into this problematic server and locally login, ssh connections will then be accepted into that server for all logins.  I cannot even ping this server until someone locally (physically) logs in with a keyboard and monitor.

I'm new to setting up servers so I may have made a small mistake somewhere, does this problem sound familiar?  

When does the server connect to the network and initialize itself?  Shouldn't it do all of this work before anyone logs in?  How would logging into the system fix this problem of it not connecting to the network?

Any help and advice would be greatly appreciated.  Thank you.

---

### Post by Mr. C. on 2007-03-24
It sounds like your network is not getting initialized correctly.

Please explain your network setup, and show output from :

ifconfig -a
lspci

MrC

---

### Post by speedcoder on 2007-03-30
Did you ever resolved this? How? Im having the same issue.

---

### Post by Skeletor on 2007-03-31
Hi Mrc. C, 
  I'm still having the same issues with ssh login:

Here is the info you asked for:
>> ifconfig -a output:
eth0      Link encap:Ethernet  HWaddr 00:06:5B:3A:52:58  
          inet addr:192.168.1.123  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe3a:5258/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7851 (7.6 KiB)  TX bytes:9060 (8.8 KiB)

eth1      Link encap:Ethernet  HWaddr 00:06:5B:3A:52:59  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1496 (1.4 KiB)  TX bytes:1496 (1.4 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


>>output of lspci:
eth0      Link encap:Ethernet  HWaddr 00:06:5B:3A:52:58  
          inet addr:192.168.1.123  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe3a:5258/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7851 (7.6 KiB)  TX bytes:9060 (8.8 KiB)

eth1      Link encap:Ethernet  HWaddr 00:06:5B:3A:52:59  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1496 (1.4 KiB)  TX bytes:1496 (1.4 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I hope there is no personal info in these outputs that will open me up to attacks by hackers or anything, but I don't think there is because it looks like all the IP addresses are just on my local network on my router.

Please let me know what I can do to fix this problem.  Thanks for your time and your help with this.

---

### Post by Mr. C. on 2007-03-31
Not being able to ping the system before logon indicates that the network startup script failed.  There we so many changes made to your system, it would be impractical to determine what hte state of your system is.

We are going to need to examine your log messages, from before you login, what errors or problems occur, or by absence, what has not occurred.  Nothing occurs to me immediately what a console login would initiate, that shouldn't already have run.

I would like to see the logs from /var/log :
```
auth.log
daemon.log
syslog
messages
dmesg
```

First, edit the file as root /etc/default/rcS, and change the set the variable VERBOSE to yes :

VERBOSE=yes

Save the file, and reboot your system.  Write down the date/time of the boot, and also the current time immediately *before* you log on.  Next, log on, and then archive and compress the log files into logs.tgz as follows:

```
cd /var/log
sudo tar -czf logs.tgz auth.log daemon.log syslog messages dmesg
```

You can either PM me the archive, or post it here as you see fit, but in either case, please provide the data/time requested above.

MrC
btw. your lspci output below was output from ifconfig -a.

---

### Post by Skeletor on 2007-03-31
Hi Mr C.,
  Here is the lspci output:
lspci
00:00.0 Host bridge: Broadcom CNB20HE Host Bridge (rev 23)
00:00.1 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:00.2 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:00.3 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:01.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
00:02.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
00:03.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 50)
00:0f.1 IDE interface: Broadcom OSB4 IDE Controller
00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 04)
02:05.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
02:05.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)

---

### Post by Skeletor on 2007-03-31
Hi Mr. C,
  I think I never really had a problem to start with.  I notice now that if I restat my server and wait for about 3-4 minutes to let it completely boot up I am able to ping it and ssh into it.  It is hard to say whether I could login faster when I had a keyboard and monitor plugged into the rack server, but I was probably less impatient since I saw the screen booting up.  When I ssh into my rack server I'm doing it blindly.

I think the whole problem may have been my poor estimation of how long the boot on my rack server would take.  Booting up my rack server takes a whole lot longer than for my normal tower server which I use as my main dev. box, I think it is the extra hard drives, network cards, and possibly the SCSI controller booting up that takes longer.

To speedcoder, I would suggest trying to wait 3-5 minutes after booting up your server before attempting to ssh in.  I read the "man rcS" pages and the section on "DELAYLOGIN" helped me to understand this process a little better.

Thanks a lot for your help Mr. C!  Just like my mechanic always tells me, there is nothing wrong with my car, I just don't know how to drive.

---

### Post by Mr. C. on 2007-03-31
Fair enough. Thanks for the update.

If you don't have a keyboard, mouse attached, you might want to see if there are timeouts waiting to detect it.

Also, you might be able move the start order of ssh in the /etc/rc*.d directories to start before some of the other services. It is probably S20ssh.  I don't know if it depends on S20makedev; if not, you could move it to S18ssh, which starts it ahead of a few more services.

MrC

---

### Post by speedcoder on 2007-04-01
edit /etc/ssh/sshd_config

and make sure you have UseDNS no

after that run /etc/rc.d/sshd restart

this worked for me.

---

