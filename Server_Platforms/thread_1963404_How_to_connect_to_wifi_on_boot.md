---
title: "How to connect to wifi on boot?"
date: 2012-04-22
forum: Server Platforms
---

### Post by john1923 on 2012-04-22
Hi, I am running ubuntu 11.10 server, on a home WPA PSK wifi network.

To connect to the wifi network I type these commands.

```

sudo ifconfig ra0 up 
sudo wpa_passphrase NetworkName "Password" > ~/WifiSetup/wpa_supplicant.conf 
sudo wpa_supplicant -B -Dwext -i ra0 -c ~/WifiSetup/wpa_supplicant.conf 
sudo dhcpcd ra0

```However I want my server to connect to wifi without me logging in.

Is there a "right" way of doing this?

I have tried putting those commands into ```
/etc/rc.local
```If I do this, the first line works propperly, and ra0 is up, but the rest of the commands don't seem to work.

Also as the server boots it spends 60 seconds waiting for network info. Ideally I would connect to the wifi network at this point?

Any Ideas?

Thank you in advance.

---

### Post by Habitual on 2012-04-22
make an .sh script with 
```

#!/bin/bash
ifconfig ra0 up 
wpa_passphrase NetworkName "Password" > /absolute/path/to/WifiSetup/wpa_supplicant.conf 
wpa_supplicant -B -Dwext -i ra0 -c /absolute/path/to/WifiSetup/wpa_supplicant.conf 
dhcpcd ra0

```

chmod 700 the same script.
Use same script in /etc/rc.local

HTH

---

### Post by john1923 on 2012-04-22
Thanks Habitual, 

It still isn't working...

here's the script
/home/john/WifiSetup/ConnectWifi.sh 
```

#!/bin/bash
ifconfig ra0 up
wpa_passphrase network "password" > /home/john/WifiSetup/wpa_supplicant.conf
wpa_supplicant -B -Dwext -i ra0 -c /home/john/WifiSetup/wpa_supplicant.conf
dhcpcd ra0
echo " run on $(date)" >> /home/john/WifiSetup/log.txt

```Here's my /etc/rc.local

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

# Connect To Wifi John 22Apr11
sh /home/john/WifiSetup/ConnectWifi.sh
# End Connect to wifi

exit 0


```I put the echo date command into the script, so I could see when it runs. It is not running automatically.

but it works if I type
```
sudo sh /home/john/WifiSetup/ConnectWifi.sh
```Thank you for your help.

---

### Post by Habitual on 2012-04-22
/home/john/WifiSetup/ConnectWifi.sh has a "#!/bin/bash" line, then the "sh" in /etc/rc.local
```
sh /home/john/WifiSetup/ConnectWifi.sh
```should not be necessary.

Try this to get a Log file of the script's running (only a a temp measure)...

crontab -e```

/home/john/WifiSetup/ConnectWifi.sh >> /home/john/WifiSetup/log.txt 2>&1
```save and reboot and someone smarter than I will be along to help if that still doesn't work.

Try adding /absolute/path/to/wpa_supplicant and /absolute/path/to/wpa_passphrase in the .sh file :)

---

### Post by john1923 on 2012-04-23
lol, I like the cron command.

Turn the server on then it will connect after midnight :D

I can see why most servers have an Ethernet connection, but there must be a way of doing it by wifi...

For the moment I have turned it on, manually connected it to wifi and logged out. It's pretty low power so leaving it on all the time should be OK, but it would be nice to have this fixed so I can turn it off and on whenever I want.

---

### Post by doogs on 2012-04-26
> **john1923 said:**
> Hi, I am running ubuntu 11.10 server, on a home WPA PSK wifi network.

To connect to the wifi network I type these commands.

```

sudo ifconfig ra0 up 
sudo wpa_passphrase NetworkName "Password" > ~/WifiSetup/wpa_supplicant.conf 
sudo wpa_supplicant -B -Dwext -i ra0 -c ~/WifiSetup/wpa_supplicant.conf 
sudo dhcpcd ra0

```However I want my server to connect to wifi without me logging in.

Is there a "right" way of doing this?

I have tried putting those commands into ```
/etc/rc.local
```If I do this, the first line works propperly, and ra0 is up, but the rest of the commands don't seem to work.

Also as the server boots it spends 60 seconds waiting for network info. Ideally I would connect to the wifi network at this point?

Any Ideas?

Thank you in advance.

Hi,
I'm no expert by any means but, I edited the etc/network/interfaces files following the guide here:
[HTML]http://prupert.co.uk/2010/06/25/how-to-configure-wireless-wifi-networking-in-ubuntu-via-the-command-line-cli/[/HTML]

My headless server now connects to my local network via wifi when the server is booted without logging in. Only thing I need to figure out now is how to get the wifi interface to switch off automatically if the server is shutdown!

Also, I commented out the lines regarding the loopback interface as well (this seemed to be a problem for me, since I don't have any ethernet connection between the server and my router).

Hope this is of help.

Cheers,
Doogs

---

### Post by SeijiSensei on 2012-04-26
Replace "wpa_passphrase" and "wpa_supplicant" with "/usr/bin/wpa_passphrase" and "/sbin/wpa_supplicant" in case there's a path problem.

---

### Post by haqking on 2012-04-26
I just put it in ```
/etc/network/interfaces
```

set it as auto wlan0 (or whatever the iface is)

And thats it for me anyways.

Peace

---

### Post by chili555 on 2012-04-26
> **haqking said:**
> I just put it in ```
/etc/network/interfaces
```

set it as auto wlan0 (or whatever the iface is)

And thats it for me anyways.

PeaceThat's what I'd do, too.```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
    wpa-ssid NetworkName
    wpa-psk Password
```No rc.local, no scripts, no fuss.

---

### Post by haqking on 2012-04-26
> **chili555 said:**
> That's what I'd do, too.```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
    wpa-ssid NetworkName
    wpa-psk Password
```No rc.local, no scripts, no fuss.

+1

Totally agree

---

### Post by Jive Turkey on 2012-04-26
> **haqking said:**
> +1

Totally agree

That's what I do too but I occaisionally have to manually kick it to make it start working with:
```
sudo ifdown wlan0 && sudo ifup wlan0
``` if it doesn't connect at boot time.

---

### Post by azzamite on 2012-04-26
I use **wicd**, it's an alternative to network-manager, it automatically connects to any registered network on boot without you having to login first.

---

### Post by haqking on 2012-04-26
> **azzamite said:**
> I use **wicd**, it's an alternative to network-manager, it automatically connects to any registered network on boot without you having to login first.

so does /etc/network/interfaces

everyone has different mileage i guess, personally WICD has always been flaky for me.

wicd-curses has worked better for me though on a non GUI system.

---

