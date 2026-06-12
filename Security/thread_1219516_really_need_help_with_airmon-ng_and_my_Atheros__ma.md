---
title: "really need help with airmon-ng and my Atheros  madwifi-ng"
date: 2009-07-21
forum: Security
---

### Post by davewickett on 2009-07-21
hi just seing if you could help me im having problems with airmon-ng and my Atheros madwifi-ng this is my output i am new but really want to learn  this is my output

root@davewickett-laptop:/home/davewickett# airmon-ng start wifi0


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
2917    NetworkManager
2935    wpa_supplicant
2939    avahi-daemon
2942    avahi-daemon


Interface    Chipset        Driver

wifi0        Atheros        madwifi-ngError for wireless request "Set Frequency" (8B04) :
    SET failed on device ath0 ; No such device.
ath0: ERROR while getting interface flags: No such device

ath1        Atheros        madwifi-ng VAP (parent: wifi0)

root@davewickett-laptop:/home/davewickett# kismet_server --daemonize
Backgrounding to daemon mode after startup
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 1 (Atheros): Enabling monitor mode for madwifi_g source interface wifi0 channel 6...
Silencing output and entering daemon mode...
NOTICE:  Created Madwifi-NG RFMON VAP kis0
WARNING: wifi0 appears to be using Madwifi-NG. Some versions of the Madwifi-NG drivers have problems in monitor mode, especially if non-monitor VAPs are active. If you experience problems, be sure to try the latest versions of Madwifi-NG and remove other VAPs
root@davewickett-laptop:/home/davewickett# Source 1 (Atheros): Opening madwifi_g source interface kis0...
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source. Kismet will not function if no packet sources are defined in kismet.conf or on the command line. Please read the README for more information about configuring Kismet.
WARNING: Sometimes cards don't always come out of monitor mode
         cleanly.  If your card is not fully working, you may need to
         restart or reconfigure it for normal operation.
Kismet exiting.
root@davewickett-laptop:/home/davewickett# kismet_client
FATAL:  Could not connect to localhost:2501.
root@davewickett-laptop:/home/davewickett# killall -I kismet_server
kismet_server: no process killed
root@davewickett-laptop:/home/davewickett# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                   [ OK ] 
root@davewickett-laptop:/home/davewickett# 

it seems to change names my wifi itself is fine please any help would be good thanks
dave
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                                                                                                            [[IMG]http://ubuntuforums.org/images/buttons/forward.gif[/IMG]]("http://ubuntuforums.org/private.php?do=newpm&forward=1&pmid=1063402")

---

