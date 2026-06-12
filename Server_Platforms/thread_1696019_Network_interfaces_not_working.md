---
title: "Network interfaces not working"
date: 2011-02-26
forum: Server Platforms
---

### Post by Jonny87 on 2011-02-26
I have been trying to set up Ubuntu server 10.04-2 and am a couple issues.

One issue is that the network interfaces aren't starting properly. I have to start them manually. I've tried to edit the /etc/network/interfaces with the following.
```

auto lo 
iface lo inet loopback

auto eth0 
iface eth0 inet static 
address 192.168.1.100 
netmask 255.255.255.0 
gateway 192.168.1.254

auto eth1 
iface eth1 inet static 
address 192.168.1.200 
netmask 255.255.255.0 

```But when I try to enable them with the ifup command some sort of error saying some thing allong the lines of;
```
missed placed option:2:
can't read /etc/network/interfaces 
```If I remove the stuff that I added I still get them the same error when using the if up command. 
The only way I can seem to bring up the interfaces with the desired ip is to use;
```
sudo ifconfig eth0 up 192.168.1.100
```The problem is though that this is temporary and I want it to be the same if I reboot or shutdown.

Can someone please help me with this?

---

### Post by Kljuka on 2011-02-26
```
auto eth1 
iface eth1 inet static 
[COLOR=Red]address 192.168.200 [/COLOR]
netmask 255.255.255.0
```

There is the problem.
Write 192.168.200.1 (or something like that)

---

### Post by Jonny87 on 2011-02-26
> **Kljuka said:**
> ```
auto eth1 
iface eth1 inet static 
[COLOR=Red]address 192.168.200 [/COLOR]
netmask 255.255.255.0
```There is the problem.
Write 192.168.200.1 (or something like that)

Sorry didn't notice that. That was just a typo in typing up the post. I had that correct on the server, I know I did because I checked that when I was having the trouble.

---

### Post by kevinthecomputerguy on 2011-02-26
Here is what mine looks like. Using allow-hotplug instead of saying auto again.
 
[http://woodel.com/index_files/network.jpg](http://woodel.com/index_files/network.jpg)
 
You can also run the following command
 
ifconfig -a
 
This will show you all the interfaces, just incase they are eth3 and 4 for some strange reason.

---

### Post by Jonny87 on 2011-02-26
Also I'm not sure if this is related but when I use ```
sudo ifconfig eth0 up 192.168.1.100
``` to start the interface, I seem to have a connection to other devices on my network but not the internet.

I've established this by using ping to other devices and to web pages, also I can't download any packages with either aptitude or apt-get.

---

### Post by kevinthecomputerguy on 2011-02-26
Make sure the gateway is the address of your router

---

### Post by Jonny87 on 2011-02-26
> **kevinthecomputerguy said:**
> Here is what mine looks like. Using allow-hotplug instead of saying auto again.
 
[http://woodel.com/index_files/network.jpg](http://woodel.com/index_files/network.jpg)
 
You can also run the following command
 
ifconfig -a
 
This will show you all the interfaces, just incase they are eth3 and 4 for some strange reason.

I tried to set mine like yours and got the same message.
```

/etc/network/interfaces:2: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"

```

---

### Post by Jonny87 on 2011-02-27
After some browsing I finally found the cause of the problem and the solution. see te second to last post in the following thread;
[http://ubuntuforums.org/showthread.php?t=632181](http://ubuntuforums.org/showthread.php?t=632181)

---

### Post by highspider on 2011-02-27
did you edit resolv.conf also to define a dns 

------------/etc/resolv.conf------------------
search test.com                                                     # defualt search provider dummy name
nameserver 192.168.0.1                          # dns server router works fine or use yours
-------------------------------------------------

then 

sudo ifconfig ath0 down
sudo /etc/init.d/networking restart
sudo ifconfig ath0 up

---

