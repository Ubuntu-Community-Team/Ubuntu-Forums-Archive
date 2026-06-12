---
title: "Need help to set up wireless DHCP on Lemur"
date: 2010-11-11
forum: System76 Support
---

### Post by bluekey on 2010-11-11
I just got a brand new lemu2 (ubuntu 10.10) and couldn't connect to internet wirelessly. Below is what I got when trying to start the network services:[INDENT]> ... ...
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/INDENT]I'm new to Linux networking setup. I have tried to find any solutions on the web including this forum but nothing worked. Wired DHCP connection worked fine on my lemur. And my home router currently serves wireless DHCP connections to my Windows PCs and iPad. 

I've tried the following ways as far as I can remember (not necessarily in the same order), plus numerous reboots or network restarts in between:

1. Disabled wired interface. In /etc/network/interfaces, I have only
> auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp2. Removed any references to "rfc3442" in dhclient.conf

3. Uninstalled Network Manager

4. Moved the laptop closer to the router to see if it's a range problem

5. Disabled router security to rule out any WEP or WPA password issues

6. Set a static IP (didn't work )

Frankly I didn't spend too much time on the last option (static IP) so I might have got the settings wrong, but anyway at this time it all seems like a witch hunt here and there so I'm almost ready to give up :( unless someone can offer a virtual hand ...

---

### Post by Flyers2391 on 2010-11-11
My guess is that it would be something on your wireless router, although you say it works on other wireless network devices.  Do you have a maximum set for the number of IP addresses to be leased, or a very small lease range?  Do you have any other settings enabled on your wireless router like MAC address filtering or something?

---

### Post by isantop on 2010-11-11
Looks like the problem could also be in your interfaces file. The standard file should look like:

```
auto lo
iface lo inet loopback
```

If your's is different, network-manager can't handle your connection. Open a terminal and run:
```
gksudo gedit /etc/network/interfaces &
``` to get it up and functioning.

If you made any changes to your configurations, then right-click on the network-manager icon in the upper panel and click on edit connections. Goto the wireless tab. If there are any connections there, delete them by selecting them and clicking "Remove" then try reconnection.

If that doesn't work, I'd reset your router by unplugging, waiting minute or two, then plugging it back in. If that also fails, then I'd check the settings.

---

### Post by bluekey on 2010-11-12
Thank you guys for help.

Flyers2391 - My lemur can get a new IP via wired DHCP connection. So I guess the availability of IP numbers isn't a problem. The MAC filter is disabled. My router configuration page says the WiFi Protected Setup is enabled by default. [COLOR=Blue]Is that an issue?[/COLOR] Anyway I disabled it still to no avail. 

isantop - Your suggestion seems to rely on NM to manage it all. I saw some opinions about how unreliable NM can be. That's why I removed NM and tried to set it up manually. So this time I just reinstalled NM to give it another try. I cleaned up the /etc/network/interfaces file. NM wireless tab has no existing connections. After rebooting the router then my laptop, I still had no internet access. At one point, after one laptop reboot, I saw a popup asking to click the NM icon to connect network. I haven't figured out what that means and the popup faded away. In subsequent reboots I didn't see such a popup again. [COLOR=Blue]What are the other settings to check? Should I create a new connection in NM?[/COLOR]

I also realized that currently I couldn't scan and find my router. 'iwlist' returns nothing.
```

~$ sudo iwlist wlan0 scan
wlan0    Scan completed :

```[COLOR=Blue]Can this be related to my problem? Still looking for more tips...[/COLOR]

---

### Post by isantop on 2010-11-12
Is the wireless card enabled? What is the status of the wireless indicator on the front of the computer? It's the one furthest to the right.

If it's off, press Fn+F11 to toggle it on. Then try connecting again by clicking on the network-manager icon in the panel. It should list available networks. (If it doesn't give it a minute, as the card may need to finish initializing.)

---

### Post by bluekey on 2010-11-13
Sorry about that. I accidentally turned the card off during my latest experiments. That's my fault. But the wireless connection still failed after turning it on. Now NM can auto detect the router and show the router name, but I couldn't connect to it via NM. I suspect DHCP fails again behind the scene but I don't know where the log is for NM. I let NM manage everything now without my intervention. Still no internet and when I pinged the router, it says "network is unreachable". 

"ifconfig" output:
```
eth0      Link encap:Ethernet  HWaddr 00:90:f5:ff:77:ca  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:0b:ee:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1957 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58272 (58.2 KB)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:ffffc900110e8000-ffffc900110e8100 
```"iwconfig" output:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"2WIRE053"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.432 GHz  Access Point: B0:E7:54:59:F2:79   
          Bit Rate=300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```What might be wrong with my configuration?

---

### Post by isantop on 2010-11-15
Did you end up rebooting your router? If not, I'd go ahead and try it at this point. I've seen cases like this where doing that solves all of the problems right up.

---

### Post by bluekey on 2010-11-16
Hi isantop -

Unfortunately rebooting didn't help. I powered down the laptop then rebooted the router, let it refresh device list and reset IP addresses (these are the relevant options from the router setup page). Then I powered up the laptop. The NM icon flashed for a while and popped up a message saying the wireless network is disconnected. Other devices at home have re-connected to the router without problems. 

As I mentioned before, I have disabled router security a long time ago so the problem shouldn't be any WEP or WPA issues. 

I saw another thread where some reported the connection often dropped for lemur. For me, I never got a wireless connection established on this laptop. 

How to check NM error messages? Should we tweak the dhclient.conf file?

---

### Post by bluekey on 2010-11-16
I just tried the WiFi connection in a Borders bookstore and it's the same story. Lemur could find the router and couldn't establish the connection. So the problem is in the laptop, not in the router. It doesn't seem that my laptop could connect wirelessly out of box. But without WiFi, why would I still use a laptop ...

---

### Post by bluekey on 2010-11-17
Booting via the Live USB method didn't give me WiFi connection either. The NM behaved the same way as I described before. Does this mean the problem lies in the hardware?

---

### Post by thomasaaron on 2010-11-18
I see you emailed us on this one. We'll pick up the conversation there. It does look like it's probably a hardware issue though. I'll respond to your email.

---

