---
title: "dhclient on boot after wpa_supplicant"
date: 2011-02-13
forum: Server Platforms
---

### Post by Keozon on 2011-02-13
Hello wonderful Ubuntu-gurus. I apologize if there's a solution to this somewhere on the forum, but I searched around on google for several hours before posting this, so I assure you, I'm not trying to waste your time.

Here's the deal. I have a file/print server running wpa_supplicant on interface wlan0 via ndiswrapper. Its wireless because the location I need the printer in is really inconvenient to have to run wires to, or I wouldn't have this problem.

The box is running ubuntu server 10.10, with only ndiswrapper and the associated utils and wpa_supplicant installed in addition to the default packages required for file/print/web serving. (there may be a few trivial packages like Vim that should have no effect whatsoever.)

Basically, wpa_supplicant associates fine with the AP, but I can't get any elegant way of getting a IP address with it, DHCP or static makes no difference. My current fix is my rc.local file has:

```
sleep 60
dhclient wlan0
return 0
```

which works, except that startup takes a minute longer than it should, and occasionally association takes longer than 60 seconds, which means it fails. 

/etc/network/interfaces contains:
```

#This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#iface eth0 inet dhcp

#Wireless Networking Devices
auto wlan0
iface wlan0 inet dhcp
        pre-up wpa_supplicant -Dwext -iwlan0 -c/home/server/wpa.conf
        post-down killall -q wpa_supplicant

```

wpa.conf contains
```

network={
        ssid="ACTIONTEC"
        #psk="CENSORED"
        psk=CENSORED
}

```

and finally, /etc/dhcp3/dhclient.conf
```

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
timeout 10;
retry 60;
#reboot 10;
#select-timeout 5;
initial-interval 2;

```

I have tried changed the interfaces file to static and listing the network info, as I don't need it to be dynamic, and it doesn't work at all. If I don't run dhclient manually (or with rc.local) netstat -r outputs nothing, and ifconfig lists only IPv6 address. 

Any help with a more elegant solution would be wonderful.

---

### Post by James78 on 2011-02-15
Here's how I do mine (it's never failed me). If my instructions are not exact, just let me know and I'll try to fix them.

/etc/network/interfaces
```
...
# The primary network interface
auto wlan0
iface wlan0 inet static
	address 192.168.1.120
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
```
Then..
```
sudo wpa_passphrase apname > /etc/wpa_supplicant.conf
<enter password>
```
/etc/rc.local
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# start wpa_supplicant in background mode
wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -B
# start up dhclient
dhclient wlan0

exit 0

```

Extra reference (probably not much help though, basically the same thing I said above)
[http://ubuntuforums.org/showpost.php?p=10388675&postcount=11](http://ubuntuforums.org/showpost.php?p=10388675&postcount=11)

---

### Post by LasTSuRvivoR on 2012-03-04
Thanks for the answer but is there a way to do this without asking for a static ip ?

---

### Post by kevdog on 2012-03-04
See here it should be all you need: 
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by vinaobraga on 2012-08-31
Hello Guys.

I'm trying to configure my wireless connection on my server but something weird is happening.
I have two cards on my server, one wired and another one wireless.
After set up all the setting of wpa_supplicant and execute the commands to connect, the wlan0 network get IP and connected on my AP.
But, when I log into my AP and ask to list all attached devices, I see the wlan0 card connected with the same MAC Address from the wired card. And if I unplug the network cabe from eth0, both connections goes down.

I will sent the steps that I followed with my configuration files to see if you can help me, please.

root@server:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:54:21:27:1f
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe21:271f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:106880 (106.8 KB)  TX bytes:80933 (80.9 KB)
          Interrupt:19 Base address:0x2c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1524 (1.5 KB)  TX bytes:1524 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:06:4f:70:f8:c8
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe70:f8c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19857 (19.8 KB)  TX bytes:21919 (21.9 KB)

root@server:~#

Follow the steps:

ifconfig wlan0 up
ifconfig
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -B
ifconfig
ps aux | grep [w]pa
iwconfig wlan0
dhclient wlan0

root@server:~# cat /etc/wpa_supplicant/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="AP-NOVO"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        #psk="REMOVED"
        psk=REMOVED
}
root@server:~#

root@server:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#wireless
auto wlan0
iface wlan0 inet dhcp


Follow the output of the attached devices from router:

3	192.168.1.9	SERVER	00:08:54:21:27:1F
4	192.168.1.10	SERVER	00:08:54:21:27:1F

if you can see, the MAC is the same of the eth0.

What is wrong? I want to use only the wireless card..is it possible, right?

I'm running ubutu 12.04.

Thanks in advanced by any help.

---

### Post by jcjveraa on 2012-12-27
Heya, I was having some issues stoo. My solution is exactly wat the first poster had, and just added -B to the pre-up line. I didn't change anything for the dhclient or rc.local. This was in 12.04 by the way.

The .conf file should of course point to the proper location.

So in /etc/network/interfaces I have
```

#Wireless Networking Devices
auto wlan0
iface wlan0 inet dhcp
        pre-up wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf** -B**
        post-down killall -q wpa_supplicant
```

---

