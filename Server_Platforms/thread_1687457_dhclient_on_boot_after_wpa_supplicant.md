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

### Post by Jive Turkey on 2012-07-02
> **Keozon said:**
> Hello wonderful Ubuntu-gurus. I apologize if there's a solution to this somewhere on the forum, but I searched around on google for several hours before posting this, so I assure you, I'm not trying to waste your time.

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

set static ip on the wlan0 interface in /etc/network/interfaces, that's what I'm going to try.

*  I found your unanswered year old thread on top of the google,   while searching for clues about my own wireless server.

---

