---
title: "Unable to check for firmware update: public key mismatch"
date: 2019-04-19
forum: System76 Support
---

### Post by e.meitner on 2019-04-19
Anybody else seen this?

**Problem:**

1. Run system76-firmware.
2.Output to the shell is:```
2019-04-19 22:29:23,142  ERROR  Failed to download firmware for oryp3
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/system76driver/firmware.py", line 414, in _run_firmware_updater
    digest, changelog_json = iface.Download()
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Failed:** public key mismatch**

```
 3. App window displays:```
Could not download firmware. Please check your network connection and try again
```

** Steps taken:**

[LIST]
[*]I've confirmed that system76-firmware is communicating with system76-firmware-daemon via DBUS. 
[*]I see the "public key mismatch" message coming over DBUS. 
[*]I've confirmed that system76-firmware-daemon is connecting with firmware.system76.com 
[*]I Purged and reinstalled the system76-firmware-daemon package. 
[/LIST]
 
** System:**[list][*]Oryx Pro, model oryp3
[*]Ubuntu 18.04(bionic)
[*]Ubuntu packages all up to date.
[/list]
** System76 packages:**
```
deb http://ppa.launchpad.net/system76-dev/stable/ubuntu bionic main:
``````
system76-coreboot-dkms    1.0.0~1551732971~18.04~0ef00d9~dev
system76-dkms    1.0.4~1554501662~18.04~5be9b0d~dev
system76-driver    19.04.7~1555460066~18.04~1090881~dev
system76-driver-nvidia    19.04.7~1555460066~18.04~1090881~dev
system76-firmware    1.0.3~1552487005~18.04~95d19ef~dev
system76-firmware-daemon    1.0.3~1552487005~18.04~95d19ef~dev
system76-io-dkms    1.0.0~1547223867~18.04~e58ff7f~dev
system76-power    1.0.0~1555432002~18.04~1c347b8~dev
system76-wallpapers    18.04.2~1525874807~18.04~d6171e2~dev

```

Thanks!

---

### Post by jlking3 on 2019-04-20
I have this same issue with my Galago Pro. I even took the step of zeroing my hard drive and reinstalling the system software from scratch.

---

### Post by hellslinger on 2019-04-22
Same thing happens to me. I have an Oryx Pro 2018.

---

### Post by aaronhoneycutt on 2019-04-24
There was an update to the system76-firmware package for all releases, the new version is [COLOR=#333333][FONT=Ubuntu]1.0.4~1555610581.

[/FONT][/COLOR][https://launchpad.net/~system76/+archive/ubuntu/pop](https://launchpad.net/~system76/+archive/ubuntu/pop)

The standard update method will upgrade this:

sudo apt update
sudo apt upgrade

---

### Post by e.meitner on 2019-04-24
Yep. Worked for me. Thank you!

---

