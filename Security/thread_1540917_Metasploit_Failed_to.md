---
title: "Metasploit: Failed to"
date: 2010-07-28
forum: Security
---

### Post by ubuntuv on 2010-07-28
Hi,

I am using Ubuntu 9.10.  I installed aircrack-ng and metasploit.  Using airmon-ng, I am able to put wireless interface into monitor mode.  Using airbase-ng, I am able to create a fake accesspoint as well. 
But when metasploit, I am getting error like 

"Auxiliary failed: RuntimeError LORCON could not detect a driver and none specified"

-----------------------------------------
Here is the dump of:

msf auxiliary(fakeap) > show options

Module options:

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   BSSID                       no        Use this static BSSID (e.g. AA:BB:CC:DD:EE:FF)
   CHANNEL    1                yes       The initial channel
   DRIVER     autodetect       yes       The name of the wireless driver for lorcon
   INTERFACE  wlan1            yes       The name of the wireless interface
   NUM        50               no        Number of beacons to send
   SSID                        no        Use this static SSID

msf auxiliary(fakeap) > run

[-] Auxiliary failed: RuntimeError LORCON could not detect a driver and none specified
[-] Call stack:
[-]   /opt/metasploit3/msf3/lib/msf/core/exploit/lorcon2.rb:70:in `new'
[-]   /opt/metasploit3/msf3/lib/msf/core/exploit/lorcon2.rb:70:in `open_wifi'
[-]   (eval):44:in `run'
[*] Auxiliary module execution completed

------------------------------------------------
Thanks in advance
-uv.

---

