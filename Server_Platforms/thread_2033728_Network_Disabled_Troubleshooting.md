---
title: "Network Disabled Troubleshooting"
date: 2012-07-26
forum: Server Platforms
---

### Post by jason328 on 2012-07-26
I'm a completely new to Ubuntu server and am having a hard time connecting the server to the internet. 
  
I first ran ping -n 8.8.8.8 
  
connect:Network is unreachable   

Then I ran ifconfig
  Link encap:Local Loopback 
inet addr:127.0.0.1 Mask 255.0.0.0 
inet6 addr: ::1/28Scope:host 
UP LOOPBACK RUNNING MTU:16436 RX packets:192 errors:0 dropped:0 overruns:0 frame:0 
TX packets:192 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 
txqueuelen:0 RX bytes:15360 (15.2KB) TX bytes:15360 (15.3KB)   

Here is ouput for sudo lspci -n
  00:00.0 0600: 8086:2580 (rev 04) 
00:02.0 0300: 8086:2582 (rev 04) 
00:1d.0 0c03: 8086:2658 (rev 03) 
00:1d.1 0c03: 8086:2659 (rev 03) 
00:1d.0 0c03: 8086:265a (rev 03) 
00:1d.0 0c03: 8086:265b (rev 03)
00:1d.0 0c03: 8086:265c (rev 03)
00:1e.0 0604: 8086:244e (rev d3) 
00:1e.0 0401: 8086:266e (rev 03) 
00:1f.0 0601: 8086:2640 (rev 03) 
00:1f.0 0101: 8086:2651 (rev 03) 
00:1f.0 0c05: 8086:266a (rev 03) 
00:0b.0 0200: 8086:1654 (rev 03)   

lshw-c network returns
  WARNING: you should run this program as super-user. 
*-network DISABLED 
description:Ethernet interface 
product: NetXtreme BCM5705_2 Gigabit Ethernet 
vender: Broadcom Corporation 
physical id:b bus info:pci@0000:0a:0b.0 
logical name: eth0 
capabilities: bus_master_cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd   1000bt 1000bt-fd autonegotiation  
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion= 3.121   firmware=5705-v3.18 latency=32 mingnt=64 multicast=yes port=twister pair   

lsmod code returned this
  Module                                        Size                                Used By 
e100                                              37213                                        0 
dm_crypt                                23125                                        1 
ppdev                                         17113                                         0 
psmouse                                 87603                                         0 
snd_intel8x0                      38570                                        0 
snd_ac97_codec        134826                                     1 snd_intel8x0 
ac97_bus                                 12730                                        1  snd_ac97_codec 
snd_pcm                                   97188                                         2 snd_intel8x0, snd_ac97_codec 
serio_raw                               13211                                        0 
snd_timer                               29990                                        1  snd_pcm 
snd                                                 78855                                        4 snd_intel8x0, snd_ac97_codec, snd_pcm,snd_timer 
soundcore                             15091                                         1 snd 
snd_page_alloc         18529                                        2  snd_intel8x0, snd_pcm 
ext2                                              73795                                        1 
parport_pc                           32866                                        1 
mac_hid                                    13253                              0 
lp                                                     17799                                        0 
parport                                     46562                                        3    ppdev, parport_pc,lp 
usbhid                                       47199                                        0 
hid                                                 99559                                       1 usbhid 
tg3                                                 152032                                     0 
i915                                               468651                                     1 
floppy                           70365                                        0 
drm_kms_helper           46978                                          1 i915 
drm                                               242038                             2 i915,drm_kms_helper 
i2c_algo_bit                13423                                1 i915 
video                                           19596                                1 i915   

Again there is more but it's giving info on the driver itself. I know  it works, I've used it. I assume then that my network got disabled when  I installed Ubuntu Server. How do I enable it?

I checked and the internet cable is connected to the D-link router. I  have also used this same computer for internet access when I had Ubuntu  Desktop installed so internet does work.

---

### Post by Cheesehead on 2012-07-26
You haven't defined any network interfaces in /etc/network/interfaces.

The loopback interface is defined, but that just means the system can listen to itself. If you're using Network Manager on a desktop system, that's fine - NM will discover and configure interfaces that are not previously defined. But you said you're using server, so you are not using NM and must configure your network settings manually.

That's sensible. Servers need to be discoverable and predictable on the network for both clients and the serving processses, so autoconfiguration -which may lead to an unpredictable interface or IP address- is often undesirable. 

There are lots of tutorials and reference on how to set up /etc/network/interfaces. For example, [http://ubuntu-for-humans.blogspot.com/2009/11/configure-network-interfaces-in-ubuntu.html](http://ubuntu-for-humans.blogspot.com/2009/11/configure-network-interfaces-in-ubuntu.html) is a fairly good, simple one.

---

### Post by jason328 on 2012-07-26
Thanks for the help. I did that and now I no longer get network disabled. However, I still can't connect to the internet. For example, sudo apt-get update does not work and I receive errors saying failed to fetch...

---

### Post by brent1975 on 2012-07-27
> **jason328 said:**
> Thanks for the help. I did that and now I no longer get network disabled. However, I still can't connect to the internet. For example, sudo apt-get update does not work and I receive errors saying failed to fetch...

I will just assume that you are running server 12.04. This sounds like dns has not been set to resolve your requests. 
check this file ```
/etc/network/interfaces
```

Typically running a server you would want to set a static IP so that when you install software such as apache,Mysql you can forward ports to a specific IP.
Sorry if you have already done this
```
/
iface eth0 inet static <--- change from dhcp to static 

address 192.168.2.106
netmask 255.255.255.0 
gateway 192.168.2.1[FONT=monospace]
[/FONT]network 192.168.2.0[FONT=monospace]
[/FONT]broadcast 192.168.2.255[FONT=monospace]

[/FONT]dns-nameservers 192.168.2.1 8.8.8.8  [192.168.2.1 is my router]
dns-search google.com 
```                         

Hope this helps...

---

### Post by Cheesehead on 2012-07-27
> **jason328 said:**
> Thanks for the help. I did that and now I no longer get network disabled.

Wait a second.... How were you getting a "network disabled" message, and what was the exact message? That seems like Network Manager, which isn't included in Ubuntu Server. If using ifup/ifdown, you would simply get an "unable to connect" message.

Do you have Network Manager installed? If so, it won't work well after you have set up /etc/network/interfaces. You cannot mix the two - pick one system and stick with it.

---

### Post by jason328 on 2012-07-27
I'll tell you what I did. I installed Ubuntu 12.04 and that is it. I haven't been able to connect to the internet or install anything. It's the biggest pain in the butt.

I was receiving the network disabled message when I did the input lshw-c network returns

---

### Post by jason328 on 2012-07-27
As for the checking /etc/network/interface it is telling me no such file or directory. I feel like none of the files I search for exist. Nothing works. I can't do anything on this. Ubuntu desktop was installed on this same computer and I never had trouble with it.

---

### Post by Cheesehead on 2012-07-27
/etc/network/interface**s**  - plural.

It can be frustrating when something that should seem so familiar...just isn't.
Nevertheless, it's *really* satisfying the first time you get manual networking to work properly.

I think brent1975 is very much on the right track. 
There's no magic here; your system is just a bit misconfigured. It's not at all hard to fix...once you have done it the first time.

---

### Post by jason328 on 2012-07-27
I turned on the computer and logged in and typed in /etc/network/interfaces and received this response even after I signed in as root user as well:      bash: /etc/network/interfaces: Permission denied

I then ran chmod+x /etc/network/interfaces which returned no errors. However, when I put in the /etc/network/interfaces code again I still got Permission Denied.

---

### Post by cariboo on 2012-07-27
> **jason328 said:**
> I turned on the computer and logged in and typed in /etc/network/interfaces and received this response even after I signed in as root user as well:      bash: /etc/network/interfaces: Permission denied

I then ran chmod+x /etc/network/interfaces which returned no errors. However, when I put in the /etc/network/interfaces code again I still got Permission Denied.

/etc/network/interfaces is a configuration file you need to open it in a text editor and make it look similar to the example brent1975 gave you. You need elevated privileges to edit the file, so at the prompt type:

```
sudo nano /etc/network/interfaces
```

See the screenshot:

---

### Post by jason328 on 2012-07-27
I went and edited the /etc/network/interfaces file and added the code below to it. It still does not work. I'm still getting no internet connection.


```
auto eth0
iface eth0 inet static
      address 192.168.2.106
      netmask 255.255.255.0
      gateway 192.168.0.1
      network 192.168.2.0
      broadcast 192.168.2.255

dns- nameservers 192.168.0.1 8.8.8.8
dns-search google.com
```
I did a route -n on my server computer to find the gateway but no numbers returned. So I used my laptop gateway instead, I assume they may be the same.

---

### Post by cariboo on 2012-07-27
> **jason328 said:**
> I went and edited the /etc/network/interfaces file and added the code below to it. It still does not work. I'm still getting no internet connection.


```

auto eth0
iface eth0 inet static
      address 192.168.2.106
      netmask 255.255.255.0
      gateway 192.168.0.1
      network 192.168.2.0
      broadcast 192.168.2.255

dns- nameservers 192.168.0.1 8.8.8.8
dns-search google.com
```
I did a route -n on my server computer to find the gateway but no numbers returned. So I used my laptop gateway instead, I assume they may be the same.

Your ip addresses have to be in the same netblock as your gateway, you just can't add random ip addresses and expect it to work. I'd suggest you try the following, it should work.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
      address 192.168.0.106
      netmask 255.255.255.0
      broadcast 192.168.0.254
      gateway 192.168.0.1
         
dns- nameservers 192.168.0.1 8.8.8.8
dns-search google.com
```

---

### Post by jason328 on 2012-07-27
I put the code in as written and I'm still not able to connect to the internet. lshw -c network returns saying *-network instead of *-network disabled. Also when I type in sudo route I get one row from IP routing table written as:

```
Destination     Gateway     Genmask                Flags   Metric    Ref   Use            Iface
192.168.0.0           *               255.255.255.0          U            O          O        0               eth0
```

---

### Post by two00lbwaster on 2012-07-27
> **jason328 said:**
> I put the code in as written and I'm still not able to connect to the internet. lshw -c network returns saying *-network instead of *-network disabled. Also when I type in sudo route I get one row from IP routing table written as:

```
Destination     Gateway     Genmask                Flags   Metric    Ref   Use            Iface
192.168.0.0           *               255.255.255.0          U            O          O        0               eth0
```

Hi Jason,

I just came across your thread trying to get my new Ubuntu Server build working.  What I was finding was that I'd said that I'd set up networking later as DHCP wasn't working on my RTL8111 adaptor.

I had to add a line into the interfaces file and then run:
```
ifup eth0
```

Subsequently running ifconfig showed that I had an eth0 and could connect to the network.

---

### Post by jason328 on 2012-07-27
So adding ifup eth0 on the first line of /etc/network/interfaces worked for you? I'll try it out and get back to you in a second.

---

### Post by two00lbwaster on 2012-07-27
> **jason328 said:**
> I went and edited the /etc/network/interfaces file and added the code below to it. It still does not work. I'm still getting no internet connection.


```
auto eth0
iface eth0 inet static
      address 192.168.2.106
      netmask 255.255.255.0
      gateway 192.168.0.1
      network 192.168.2.0
      broadcast 192.168.2.255

dns- nameservers 192.168.0.1 8.8.8.8
dns-search google.com
```
I did a route -n on my server computer to find the gateway but no numbers returned. So I used my laptop gateway instead, I assume they may be the same.

Hi Jason,

That gateway IP is incorrect, or your IP, network and broadcast addresses are incorrect as per cariboo907's post.  That gateway is not in your subnet range so your OS will not be able to communicate with the network.  Either your gateway should be between 192.168.2.0 and 192.168.2.255 or you should change your settings as cariboo907 already suggested.

```
auto eth0
iface eth0 inet static
      address 192.168.0.106
      netmask 255.255.255.0
      gateway 192.168.0.1
      network 192.168.0.0
      broadcast 192.168.0.255

dns-nameservers 192.168.0.1 8.8.8.8
dns-search google.com
```

Normally your gateway IP address is your router IP address.

---

### Post by two00lbwaster on 2012-07-27
> **jason328 said:**
> So adding ifup eth0 on the first line of /etc/network/interfaces worked for you? I'll try it out and get back to you in a second.

Sorry, no I ran ifup eth0 in the terminal whilst root, so sudo if using a regular user account.

The line that I added to my interfaces file was:
```
iface eth0 inet dhcp
```

Edit: I don't think that my issue applies to you as mine was due to a missing auto eth0.

---

### Post by jason328 on 2012-07-27
Ok, I changed static to dhcp and then I ran ```
 sudo ifup eth0
```. I then typed in ```
sudo apt-get update
```. This time it's telling me ```
0% Connecting to us.archive.ubuntu.com
``` but it's producing the same errors as before. I still get errors such as Err or Failed to fetch. and it ends by saying ```
Some index files failed to download. They have been ignored, or old ones used instead
```.

---

### Post by brent1975 on 2012-07-27
> **jason328 said:**
> Ok, I changed static to dhcp and then I ran ```
 sudo ifup eth0
```. I then typed in ```
sudo apt-get update
```. This time it's telling me ```
0% Connecting to us.archive.ubuntu.com
``` but it's producing the same errors as before. I still get errors such as Err or Failed to fetch. and it ends by saying ```
Some index files failed to download. They have been ignored, or old ones used instead
```.


after you made the changes you need to restart the networking..

You can either just simply reboot the server with

```
 sudo reboot -n
```or

```
 sudo  /etc/network/interfaces restart 
```

---

### Post by jason328 on 2012-07-27
Thank you so much everyone for your help. I appreciate everybody's patience and advice. Everything works now!!!:D

---

### Post by brent1975 on 2012-07-27
> **jason328 said:**
> Thank you so much everyone for your help. I appreciate everybody's patience and advice. Everything works now!!!:D


Great... good job! 

Don't forget to mark this as resolved. :)

---

