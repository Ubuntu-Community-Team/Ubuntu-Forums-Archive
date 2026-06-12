---
title: "Adding a wireless connection - at the same time!"
date: 2018-04-04
forum: Server Platforms
---

### Post by unluckyforsome on 2018-04-04
Hi Guys,

  I'm a little stuck. I'm running Ubuntu Server 16.04.4 LTS headless, I have my Ubuntu Server running perfectly when  connected via ethernet, however I would like to add wireless capability  (there's a wifi card in the machine).

  I tried updating **/etc/network/interfaces** by adding the "secondary network interface" using the "wlp4s1" interface (which is the name of my wireless adapter):

  ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp2s0
iface enp2s0 inet dhcp

# The secondary network interface (this is the bit I added!)
auto wlp4s1
iface wlp4s1 inet dhcp
wpa-ssid *MYSSID*
wpa-psk *MYNETWORKKEY*

```  This enables my wireless! (with a different local IP) But this seems  to override my ethernet setting and the system hangs for 5 minutes when  booting and then gives up and ignores the ethernet.
  Ideally I would like a way of bridging my wireless and my ethernet so  the system thinks that they're the same connection (with the same local  IP) but with ethernet taking priority. If that's not possible I'd like  them just to both be enabled at the same time with different local IP's  (which I've had when using OpenMediaVault).
  Does anybody know how this is done? :-)
  Many thanks!

---

### Post by TheFu on 2018-04-04
While you can do this, it might not be a good idea to have them on the same subnet.  Routing becomes confused, so you'll have to manually decide what routes you want for which interface. It won't be automatic.  Automatic routing that gets setup for us uses subnets.

To merge both onto the same IP, that is known as *link aggregation*. The switch/router need to support it or it won't work. TLDP has lots of details about this.  [https://www.kernel.org/doc/Documentation/networking/bonding.txt](https://www.kernel.org/doc/Documentation/networking/bonding.txt)

But I'm certain others have different ideas about doing this. Hopefully, they will chime in.

---

### Post by unluckyforsome on 2018-04-06
Thanks for your reply,

I managed to get both interfaces working at the same time, weirdly, only after installing ubuntu server with wifi and then building /etc/networks/interfaces like above but with "allow-hotplug" instead of "auto". If I installed Ubuntu using ethernet adapter this setup wouldn't work, the wireless would not connect (no idea why).

The networks are on different local IP's, while not ideal, it's better than nothing.

If anyone has any advice it's most welcome, but for now I'm giving up!

---

### Post by TheFu on 2018-04-06
I can't see any reason to have wifi on the same network and as the primary route.
I can see reasons to have them on different networks - perhaps an internet facing one and a management/storage/backup network.

I wouldn't expect link aggregation/bonding to work.  It isn't something I've seen advertised in any real routers.  Plus there are the huge security issues in using wifi at all.  IMHO, wifi without a full VPN isn't secure. I don't believe the marketing.

Of course, doing something like this just because you can is a perfectly valid reason too.  Learning how is a reward alone!

---

### Post by unluckyforsome on 2018-04-07
Haha, it's because my NAS box may not be plugged into ethernet the whole time, It might sometimes get moved "out of the way" - which is why I wanted it to use WiFi as a backup way of staying connected.

I can see the use of WiFi on Ubuntu Server is quite rare as I've had trouble finding anyone else getting support on the subject - and even on the system install it "forgets" its WiFi config on the install when you finally boot into the system. However when you pick an ethernet connection during server install it remembers your config. I can't imagine this is deliberate but I could be wrong, so maybe a bug to report there? Lol

---

### Post by TheFu on 2018-04-07
WiFi connections aren't nearly as stable as humans think they are. If you watch the bandwidth over ethernet, it is solid, stable, unwaivering.  Do the same with wifi, even what appears to be excellent connections varies wildly from second to second.  Wifi really isn't a good idea for a file server. "Stay wired, my friends." [https://www.youtube.com/watch?v=NgEbLgs__W8](https://www.youtube.com/watch?v=NgEbLgs__W8)

---

