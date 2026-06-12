---
title: "Wpa_supplicant - if installed, please help"
date: 2006-04-16
forum: Server Platforms
---

### Post by Vinze on 2006-04-16
Hey, if anyone has wpa_supplicant installed, could you post the contents of **/etc/wap_supplicant.conf** and **/etc/default/wpa_supplicant**?

The reason why I'm asking is because there's WPA encryption on our network, and now I (with Linux) have to find out how to do that on Linux, as, of course, the company of my network adapter doesn't support Linux ](*,) . Then I found the WPA HOWTO in the Ubuntu Wiki which told me to edit those files, which didn't exist.

Thanks in advance.

PS: I posted this in desktop support before but I guess that wasn't the right forum. If a mod reads this, please lock the other one.

---

### Post by Ginger The Cat on 2006-04-18
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=0

# Useful flags:
#  -D <driver>		Wireless drive, typically optional.
#  -i <ifname>		Interface
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="-w"

# EXAMPLES:

# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"
# OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"



and my wpasupplicant.conf is as follows but this wont necessarily be right for you of course...


# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="<ssid value>"
        mode=0
        auth_alg=OPEN
        group=TKIP
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        psk="<32 chars>"
}


Cheers

Mike

---

