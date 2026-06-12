---
title: "Upgrade problem"
date: 2016-08-20
forum: Ubuntu Development Version
---

### Post by P-I H on 2016-08-20
I used Synaptic to do today's upgrades. My graphic driver, amdgpu-pro broke. The screen was filled with garbage. The same happened the other day when I upgraded and had proposed enabled. After a reboot I got this message
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```
After I applied the command and rebooted everything worked OK

---

### Post by ventrical on 2016-08-20
> **P-I H said:**
> I used Synaptic to do today's upgrades. My graphic driver, amdgpu-pro broke. The screen was filled with garbage. The same happened the other day when I upgraded and had proposed enabled. After a reboot I got this message
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```
After I applied the command and rebooted everything worked OK

..and another trick is to..

```

sudo apt-get install -f

```

it is happening a lot with unity8 desktop.

You have to sometimes:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

a few times to get all the upgrades.

regards..

---

