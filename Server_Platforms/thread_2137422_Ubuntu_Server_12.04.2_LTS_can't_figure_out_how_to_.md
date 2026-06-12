---
title: "Ubuntu Server 12.04.2 LTS can't figure out how to eneter a static IP address."
date: 2013-04-20
forum: Server Platforms
---

### Post by rouletterun on 2013-04-20
I am doing a new install of Ubuntu Server 12.04.2 LTS for use as a home NAS server. I have been following directions given by "qidsup" on both Youtube@
[https://www.youtube.com/watch?v=-5Z_-3EBIHE](https://www.youtube.com/watch?v=-5Z_-3EBIHE)
and on Google@
[https://docs.google.com/document/d/1hFw1YnH9s-1Y9M4VPLgPOOjm1iH6PJOHefg5NhGC4oA/edit?pli=1](https://docs.google.com/document/d/1hFw1YnH9s-1Y9M4VPLgPOOjm1iH6PJOHefg5NhGC4oA/edit?pli=1)

I have followed his directions exactly other than I have mounted the OS onto a HDD rather than using a flash drive (I may change that shortly), I have gotten up to the: Set Static IP Address and have typed in his command of: [COLOR=#ff6309][FONT=Courier New]**sudo nano /etc/network/interfaces**[/FONT][/COLOR] and my system goes to the page he is showing on this video @ time 04:58 of the video, but I get nothing other than the header bar and the options across the bottom, which I can't figure out how to access. I'm stuck and don't know what to do here. I do understand the need for a static IP address and am trying to figure out how to set it. Help will be greatly appreciated. Thank you.

Chuck

---

### Post by rouletterun on 2013-04-20
I am doing a new install of Ubuntu Server 12.04.2 LTS for use as a home  NAS server. I have been following directions given by "qidsup" on both  Youtube@
[https://www.youtube.com/watch?v=-5Z_-3EBIHE](https://www.youtube.com/watch?v=-5Z_-3EBIHE)
and on Google@
[https://docs.google.com/document/d/1...4oA/edit?pli=1]("https://docs.google.com/document/d/1hFw1YnH9s-1Y9M4VPLgPOOjm1iH6PJOHefg5NhGC4oA/edit?pli=1")

I have followed his directions exactly other than I have mounted the OS  onto a HDD rather than using a flash drive (I may change that shortly), I  have gotten up to the: Set Static IP Address and have typed in his  command of: [COLOR=#ff6309][FONT=Courier New]**sudo nano /etc/network/interfaces**[/FONT][/COLOR]  and my system goes to the page he is showing on this video @ time 04:58  of the video, but I get nothing other than the header bar and the  options across the bottom, which I can't figure out how to access. I'm  stuck and don't know what to do here. I do understand the need for a  static IP address and am trying to figure out how to set it. Help will  be greatly appreciated. Thank you.

Chuck

P.S. I am a beginner at both Ubuntu and servers, please bear with me.

---

### Post by steeldriver on 2013-04-20
The options at the bottom aren't an actual menu system afaik - they just tell you what control key combos to type e.g. ^O (hold down the Ctrl key and hit the o key) to save and ^X (Ctrl-X) to quit (which will prompt you to save, if you've modified the file)

---

### Post by rouletterun on 2013-04-20
OK, I get that, but where your screenshot has this dropdown, I get nothing; that's where I'm stuck. You did just help me with the first part though, didn't know about Ctrl key. Thanks for that.

---

### Post by papibe on 2013-04-20
Hi rouletterun.

You have to choose an address that it consistent with your network. Examples given in tutorials, like 192.168.1.100, sometimes won't work with your actual setup.

Also, you have to choose the address so that is outside your router's DHCP range.

If your router supports it, it is much easier leave the server conf files as they are, and set a DHCP reservation on the router itself.

Could you post the results of these commands?
```
cat /etc/network/interfaces

cat /etc/resolv.conf

ifconfig

route -n
```
Regards.

---

### Post by Iowan on 2013-04-20
> **papibe said:**
> If your router supports it, it is much easier leave the server conf files as they are, and set a DHCP reservation on the router itself.

I was thinking similar things...
Do you know what subnet your network uses?

Threads merged.
From the Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.

---

### Post by rouletterun on 2013-04-20
Here's what it gave me, sorry it took so long, but I had to do this all by hand, two separate computers and I can't drag a screen shot to this one.

cat /etc/network/interfaces =

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces (5).
# The loopback network interface auto lo iface lo inet loopback
# The primary network interface auto eth0
iface eth0 inet dhcp

ifconfig =

eth0    Link encap:Ethernet HWaddr 00:1c:c0:7e:9c:72
          inet addr:10.0.0.6 Bcast:10.0.0.255 Mask:255.255.255.0
          inet6 addr: fe80:: 21c:c0ff:fe7e:9c72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric 1
          RX packets:26 errors:0 dropped:0 overruns:0 Frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions: 0 txqueuelen:1000
          RX bytes:4075 (4.0KB) TX bytes:5132 (5.1KB)
          Interrupt:20 Memory:e0600000-e620000

lo        Link encap: Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes: 480 (480.0 B) TX bytes: 480 (480.0 B)

rout -n =

Kernal IP routing table

Destination     Gateway     Genmask                     Flags        Metric        Ref        Use Iface
0.0.0.0      10.0.0.1       0.0.0.0                       UG               100             0            0 eth0
10.0.0.0            0.0.0.0         255.255.255.0       U                  0                     0          0 eth0  

If it makes and difference, Comcast is my ISP. This didn't do the last table very well, I hope you can decipher it, tried to fix it.

---

### Post by darkod on 2013-04-20
First of all, make sure you type the command correctly, letter to letter, and note that in linux small letters are NOT equal to capitals as often in windows. So, to edit the interface information you need to open the nano editor with:
```
sudo nano /etc/network/interfaces
```

Are you telling us it open a blank file? The fle should not be blank, you should see text already in it.

The section for the first wired interface by default would usually be like:
```
auto eth0
iface eth0 inet dhcp
```

You need to replace it with something like (note that the information will depend on your LAN subnet, the gateway, DNS servers you want to use, etc):
```
auto eth0
iface eth0 inet static
   address 192.168.1.x
   netmask 255.255.255.0
   gateway 192.168.1.1
   dns-nameservers x.x.x.x y.y.y.y
```

That is sort of a basic setup. Again, please note that the exact options you need to enter will depend on your LAN. Don't simply repeat the configuration since you might need modifications.

After you modify the file, save it with Ctrl+O, Enter. Then close it with Ctrl+X.

For the new config to be applied either restart the whole server or only the networking:
```
sudo service networking restart
```

---

### Post by rouletterun on 2013-04-20
I will try reentering the exact command again, I was pretty sure I did the first time, but, yes, it did open to a blank screen with no drop down, just the header bar and the options at the bottom. I will try entering the command again. I do appreciate the help!!!

---

### Post by rouletterun on 2013-04-20
This time I got the dropdown of:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces (5).

# The loopback network interface auto lo iface lo inet loopback

# The primary network interface auto eth0
iface eth0 inet dhcp

---

### Post by rouletterun on 2013-04-20
I'm still having a problem trying to figure out my dns-nameservers number.

---

### Post by cariboo on 2013-04-20
If you are behind a router, just use the router's ip address. I have both Google's DNS address and my routers ip address in my interfaces file. It looks like this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# eth0
auto eth0
iface eth0 inet static

	address		192.168.0.200
	netmask		255.255.255.0
	broadcast	192.168.0.254
	gateway		192.168.0.1
	dns-nameservers	8.8.8.8 192.168.0.1
```

---

