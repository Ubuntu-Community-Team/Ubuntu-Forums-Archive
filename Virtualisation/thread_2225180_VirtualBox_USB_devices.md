---
title: "VirtualBox USB devices"
date: 2014-05-20
forum: Virtualisation
---

### Post by john173 on 2014-05-20
[SIZE=5]As i messed up the posts CKECK DOWN[/SIZE] 
sorry..

---

### Post by john173 on 2014-05-20
[SIZE=5]Hi[/SIZE][SIZE=4] there[/SIZE] I am kindly experienced with VirtualBox in Windows but not through ubuntu


I have already installed VirtualBox and isntalled in Windows XP ......
I have added Guest Additions and Extension Pack


Now i just click my Windows XP icon got to > setting > USB >and click the (+)[IMG]http://s24.postimg.org/fw2q1vrvl/image.png[/IMG]  button and finally add the USB-Network Adapter(In my case ATHEROS USB 2.0 WLAN[0108])

Start Windows XP and all getting F**ED UP!!() 
Vbox Crashes and I Force Quit [http://s11.postimg.org/3krh9u8wj/Force_Quit.png](http://s11.postimg.org/3krh9u8wj/Force_Quit.png)

Activating ctrl+alt+F2 and a message filling multiple times my screen 
```
unregister_netdevice: waiting for wlan0 to become free. Usage count = 1
unregister_netdevice: waiting for wlan0 to become free. Usage count = 1
unregister_netdevice: waiting for wlan0 to become free. Usage count = 1
unregister_netdevice: waiting for wlan0 to become free. Usage count = 1
unregister_netdevice: waiting for wlan0 to become free. Usage count = 1
unregister_netdevice: waiting for wlan0 to become free. Usage count = 1
.
.
.
.
```

Going back with ctrl+alt+F7 and my network sigh is (off) 
was : [IMG]http://s14.postimg.org/3lb3mich9/Screenshot_from_2014_05_20_14_47_38.png[/IMG] [SIZE=2]is [/SIZE]: [IMG]http://s4.postimg.org/r11rtgfkp/wirestops.png[/IMG]
and the WLAN adapter is clearly dead 

Open Terminal typing "iwconfig" and used to be/is
user@user-desktop ~ $ iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ThomsonBF5BC0"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:76:FF:BF:5B:C0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:83   Missed beacon:0
```
And was/is 
```
user@user-desktop ~ $ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.
```
Then i must push the reboot button on the box and then everyting is fine but i am afraid to open Vbox again using USB device








> I can connect to the internet on Windows XP but it is showing this as eth0 and not wla0 on host wlan0 is XXX.XXX.X.XX 
and
 in windows through vbox is eth0 is on XX.X.X.XX

As i am testing things on soniar engineering i want the main local ip from wlan0 and not from eth0

---

### Post by slickymaster on 2014-05-20
Please **do not create duplicate threads**, it dilutes community effort.

I've merged your two threads and moved them to the proper sub-forum,** Virtualisation**.

---

