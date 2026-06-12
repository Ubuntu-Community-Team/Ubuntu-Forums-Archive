---
title: "Apt-get unable to access repositories"
date: 2008-08-12
forum: Server Platforms
---

### Post by SoundFriend on 2008-08-12
I have a Hardy server install that originally had SWAT and Ebox installed but I removed them.  Now apt-get (or aptitude) can't access the repositories. I also get a number of boot error messages from packages that are not set up and/or not properly removed, such as slapd, but also dansguardian and ebox.  I'd like to either clean up the installation, or re-install but keeping my samba and user names / passwords that I've set up if possible.

As apt-get can't access the repositories I'm stuck!  I don't think that it is a dns problem.  Previously Apache was installed as part of either SWAT or Ebox. Maybe this blocked port 80?  I can ssh to the server and the samba shares work ok.  What can I check?  Any help appreciated :)

John

---

### Post by SoundFriend on 2008-08-12
Hi,

Further to this I can't ping any websites, so it looks like port 80 is blocked.  

How do I fix this?

John

---

### Post by cariboo on 2008-08-13
It looks like you got a networking problem rather than a problem with apt. How do you connect to the internet? Port 80 has nothing to do with it. If you are connected to a router and using dhcp have you tried dhclient eth0 or whatever ethernet interface you are using?
If you are using a static ip address, has your /etc/network/interfaces changed?

Jim

---

### Post by jerome1232 on 2008-08-13
Can you ping them by ip? This is an IP for google.com see if you can ping it.
```
ping -c 4 72.14.207.99
```
if that does work, it's DNS, if it doesn't you have a general networking problem

---

### Post by SoundFriend on 2008-08-13
> **cariboo907 said:**
> If you are connected to a router and using dhcp have you tried dhclient eth0 or whatever ethernet interface you are using?
If you are using a static ip address, has your /etc/network/interfaces changed?


Thanks.  Yes I am using a router on 192.168.123.254. Trying dhclient eth0 initially showed up some weird stuff involving e-box (still not removed from the system) and DHCP.  I moved these ebox files and now get this:

```
There is already a pid file /var/run/dhclient.pid with pid 4984
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:01:6c:37:3d:22
Sending on   LPF/eth0/00:01:6c:37:3d:22
Sending on   Socket/fallback
DHCPREQUEST of 192.168.123.113 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.123.113 from 192.168.123.254
bound to 192.168.123.113 -- renewal in 230738 seconds.

```

I can confirm that I still can't ping google using
```
ping -c 4 72.14.207.99
```

Here is the interfaces information.  Looks ok?

```
john@ubuntu:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Networking works ok to the extent that I can SSH to the server, and it can ping local machines on my network, but not anything on the internet.

John

---

### Post by windependence on 2008-08-13
> Thanks. Yes I am using a router on 192.168.123.254. Trying dhclient eth0 initially showed up some weird stuff involving e-box (still not removed from the system) and DHCP. I moved these ebox files and now get this:

Are you SURE this is your router's LAN IP address? It wouldn't be unless you actaully changed it to that. This is most likely the problem: You don't normally need a DHCP server on your LAN because your router almost always has one built in to it. So we need to stop any DHCP server on the Ubuntu machine. In case you're not sure, a DHCP server assigns IP addresses to your network automatically when a machine is added and makes a request. My guess is that the old DHCP server from ebox is still active and is assigning an incorrect gateway to your machines. What I would like to do to test my theory is first make sure of what your IP address of your router is and then assign your machine a static IP inside the network and see if it works with the proper settings. The gateway address tells the machine how to get out to the outside world.

If you browse to [http://192.168.123.254](http://192.168.123.254) in your browser from inside your LAN, do you get a router config page? What brand and model router are you using? Let's start there first, then we'll fix this for you.

-Tim

---

### Post by SoundFriend on 2008-08-13
> **windependence said:**
> Are you SURE this is your router's LAN IP address? It wouldn't be unless you actaully changed it to that. 

Yes Tim really!  It's a SMC Barricade 7008

> If you browse to [http://192.168.123.254](http://192.168.123.254) in your browser from inside your LAN, do you get a router config page? What brand and model router are you using? Let's start there first, then we'll fix this for you.


Yes, I get the router. 
The machine was working ok before I removed Ebox and SWAT.  I don't know what happened, but these packages put a lot of tentacles into the system and removing them has caused the problems.

John

---

### Post by windependence on 2008-08-13
> The machine was working ok before I removed Ebox and SWAT. I don't know what happened, but these packages put a lot of tentacles into the system and removing them has caused the problems.

This is why you need to dump all that stuff and learn the CLI. I know, it's a bear but at some point you will just "get it", the light will go on and you will say "Eureka! I have found it!". ;)

OK so here is what I'm gonna have you do:

Change your /etc/network/interfaces to read like this:

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.123.100
gateway 192.168.123.254
netmask 255.255.255.0
network 192.168.123.0
broadcast 192.168.123.255
```

Then add this to your /etc/hosts below everything else:

```
91.189.88.45      us.archive.ubuntu.com
91.189.88.37      security.ubuntu.com

```

Then restart your network:

```
sudo /etc/init.d/networking restart
```

And try again with the install. Let me know if this works, and then we'll work on getting rid of that old DHCP server.

-Tim

---

### Post by SoundFriend on 2008-08-13
> **windependence said:**
> This is why you need to dump all that stuff and learn the CLI. I know, it's a bear but at some point you will just "get it", the light will go on and you will say "Eureka! I have found it!". ;)

Yes, I know, big mistake :)

> Change your /etc/network/interfaces to read like this:

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.123.100
gateway 192.168.123.254
netmask 255.255.255.0
network 192.168.123.0
broadcast 192.168.123.255
```


Done

> 
Then add this to your /etc/hosts below everything else:

```
91.189.88.45      us.archive.ubuntu.com
91.189.88.37      security.ubuntu.com

```


Done, except I used 194.169.254.10 as the address of gb.archive.ubuntu.com which apt-get calls up.

> 
Then restart your network:

```
sudo /etc/init.d/networking restart
```


It boots, but apt-get still doesn't work, as it still cannot contact the archives.

FYI, here's the output of ifconfig:
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6c:37:3d:22
          inet addr:192.168.123.100  Bcast:192.168.123.255   Mask:255.255.255.0
          inet6 addr: fe80::201:6cff:fe37:3d22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:74116 (72.3 KB)  TX bytes:79238 (77.3 KB)
          Interrupt:16 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15941 (15.5 KB)  TX bytes:15941 (15.5 KB)


```

John

---

### Post by SoundFriend on 2008-08-13
Hold that, I just issued a fixed IP mapping to the box and apt-get is partly working and ping is now working!

Apt-get fails when 'gb.security.ubuntu.com' cannot be resolved.

I can't ping this address either, it doesn't seem to exist.

John

---

### Post by windependence on 2008-08-13
I don't think you want the gb.security.ubuntu.com in your hosts file. Let it resolve itself. OH, and maybe try this. What is in your /etc/resolv.conf?

Add a line for another nameserver:

nameserver 2.2.2.4

Don't forget to restart the network.

-Tim

---

### Post by SoundFriend on 2008-08-13
resolv.conf:

```

search jle
nameserver 194.168.4.100
nameserver 194.168.8.100
nameserver 2.2.2.4

```

Running apt-get update still gives the message:
still unable to resolve 'gb.security.ubuntu.com'

John

---

### Post by windependence on 2008-08-13
What's up with the 2 local nameservers? They aren't gonna do you much good. Use your gateway for one and use these for the other two:

208.67.222.222
208.67.220.220

These are OpenDNS servers.

You can also try:

4.2.2.1
4.2.2.3
4.2.2.4
4.2.2.5

Ping them, and use the ones you get a faster ping on. You may still get a better result with the OpenDNS servers because they have so much stuff cached. Sorry, the 2.2.2.4 was incorrect (was going off memory) :(

Try this and let me know, but get rid of those two you have in there.

-Tim

---

### Post by SoundFriend on 2008-08-13
> **windependence said:**
> What's up with the 2 local nameservers? They aren't gonna do you much good. Use your gateway for one and use these for the other two:


They are my ISP's nameservers!
> 
208.67.222.222
208.67.220.220


But these are in California and I'm in Cambridge UK...

> 
These are OpenDNS servers.

You can also try:

4.2.2.1
4.2.2.3
4.2.2.4
4.2.2.5

Ping them, and use the ones you get a faster ping on. You may still get a better result with the OpenDNS servers because they have so much stuff cached. Sorry, the 2.2.2.4 was incorrect (was going off memory) :(

Try this and let me know, but get rid of those two you have in there.


With respect I don't believe there is a problem with these nameservers.  They are less than 60 miles away, and on the ISP's network, so are probably the fastest, and I've always used them...  

I have fixed the apt-get complaints about 'gb.security.ubuntu.com' by removing the entries in /etc/apt/sources.list , hopefully this won't come back to bite me!  

So I am now able to use apt-get and aptitude except I still get error messages concerning another package 'slapd' that I can't remove or install.  

Thanks a lot for your help so far, I have made some progress. 

Now, how do I tell if there is still a DNS server running on the Ubuntu system, and how to stop it if there is?

John

---

### Post by windependence on 2008-08-13
No, you don't understand. It's great that your ISP is using OpenDNS servers....BUT they have to be in your /etc/resolv.conf or they are no good to you. So, your resolv.conf should look like this:

nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.123.254

That should make everything work for you. You will want to put that repo back in your list. You can leave the entries in your hosts file, that will make your lookup much faster.

-Tim

---

### Post by SoundFriend on 2008-08-14
Hi Tim,

I r-eread my post and see I may have caused confusion over the nameservers.  The 194.168.x.100 are the UK ISP ones.  I ping'd them all and the OpenDNS servers were actually faster than the UK ones... so they are now on my system :)

I tried pinging the ubuntu repo addresses, and 'gb.security.ubuntu.com' doesn't exist, only 'security.ubuntu.com' so it is a mystery how they got into sources.list.  I have fixed this by putting in 'security.ubuntu.com' etc. 

I have finally managed to remove slapd that was broken firstly by getting it to install and them removing it. I had to hack some things around first, so the CLI has been getting a lot of use!

The server looks a lot happier now. Many thanks for your help, I've learnt a few things along the way :)

John

---

### Post by windependence on 2008-08-14
Actually, now that you mention it, I am not sure why the 'gb.security.ubuntu.com' was even in there. I will have to check my fresh install when I get off work and see if it's there. I don't think it is because when I got you the IPs to put in your hosts file, I got all the repos off my live install.

Second, I apologize for the confusion, I thought your nameserver addresses were 19**2**.168.xxx.xxx. I now see they were 194. BIG difference. But, the Open DNS servers are faster and actually I think the ones I gave you WERE UK servers anyway. Glad you got it up and working. If anything, DNS should be lighning fast for you especially with those repository IPs in your hosts file.

Good luck!

-Tim

---

