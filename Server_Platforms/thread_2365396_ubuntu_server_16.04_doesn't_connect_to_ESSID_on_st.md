---
title: "ubuntu server 16.04 doesn't connect to ESSID on startup (but does via cli)"
date: 2017-07-06
forum: Server Platforms
---

### Post by syberon on 2017-07-06
Hi

I hope someone can help me with this problem:

I am trying to setup my portable (dell precision 5510, linux edition) with ubuntu 16.04. I got my thunderbolt3 connection working, but would like to use the wifi for a second interface. I can get it to connect from cli, but when rebooting, it doesn't reconnect to my ESSID.
I checked the fora ande tried multiply solutions already, without succes.
Here is what I have until now:

```
sudo vi /etc/network/interface

#thunderbolt 3 interface
auto <logical name>
iface <logical name> inet dhcp


#wifi interface
auto <logical name>
iface <logical name> inet dhcp
```

```
sudo apt install wireless-toolsiwconfig
sudo iwlist <logical name> scan | grep ESSID
sudo apt install wpasupplicant
wpa_passphrase "<ESSID>" "<passphrase>" | sudo tee /etc/wpa_supplicant.conf   # $ are written as \$
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i <logical name>
ctrl+c if successful
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i <logical name> -B          #run service in the background
sudo dhclient -r                                                              #release dhcp ip address
sudo dhclient <logical name>                                                  #request dhcp ip address


Test:
ping 8.8.8.8
```

I can ping 8.8.8.8 with this setup. Now I have to get it working at startup:

```
Start wireless at boot:
sudo vi /lib/systemd/system/wpa_supplicant.service

CHANGE:
ExecStart=/sbin/wpa_supplicant -u -s -O /run/wpa_supplicant

TO:
ExecStart=/sbin/wpa_supplicant -u -s -c /etc/wpa_supplicant.conf -i <logical name> 

enable wpa_supplicant service to start at boot time:

sudo systemclt enable wpa_supplicant.service

sudo reboot
```

Failure, i am not connected to my ESSID, according to iwconfig.


> I am not so proficient in troubleshooting linux, I can follow commands on the internet, but not yet by myself, nor where to look.
I will be glad to perform all sort of commands.

thanks in advance for any help!

---

### Post by syberon on 2017-07-06
I got it solved, but I don't know if it is a workaround:
These are the changes I made to get it working:

```
sudo vi /etc/network/interface

#thunderbolt 3 interface
auto <logical name>
iface <logical name> inet dhcp


#wifi interface
auto <logical name>
iface <logical name> inet dhcp
pre-up wpa_supplicant -c /etc/wpa_supplicant.conf -i <logical name>
post-down killall -q wpa_supplicant
```

```
make dhcp request at boot:
sudo vi /etc/rc.local


# before "exit 0" add:


dhclient <logical name>
```

---

