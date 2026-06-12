---
title: "Dhclient hangs"
date: 2008-09-13
forum: Server Platforms
---

### Post by mrdek11 on 2008-09-13
My router operates using WPA. Unable to find any other way to connect via the ubuntu terminal for my Hardy server, I followed a tutorial, and developed this script to run at startup:

iwconfig ath0 essid peterson
wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -B
dhclient -d ath0

Once it gets to dhclient, it binds to an address, and dhclient hangs. It never exits. Ctrl+C doesn't help. I can SSH in, and do everything I want to do, so this normally isn't a problem, but I think some of my startup scripts aren't running because of the hang.

In case it matters, the contents of /etc/wpa_supplicant.conf are:
```

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
fast_reauth=1
network={
ssid="peterson"
psk="mywepkey"
priority=5
}

```

Does anybody know what is wrong?
Thank you for your time and help!

---

### Post by mrdek11 on 2008-09-13
I just added a space in the script, between -c and /etc
This seems to have had no effect. I haven't actually looked at the monitor's display in some time, and after changing that, I checked, and it seems to have gotten past dhclient, and is now stuck at:
Loading OpenBSD Secure Shell server's configurration sshd

[edit]
After restarting again, it seems to have gone back to hanging at:
```
bound to 192.168.0.108 -- renewal in 42464 seconds.
_
```

---

