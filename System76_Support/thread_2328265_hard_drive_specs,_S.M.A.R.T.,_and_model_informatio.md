---
title: "hard drive specs, S.M.A.R.T., and model information"
date: 2016-06-19
forum: System76 Support
---

### Post by donald-a-pellegrino on 2016-06-19
I have a System76 Lemur lemu6 with the "256 GB NVMe PCIe M.2 SSD" option. Running "smartctl -i /dev/nvme0n1" gives output indicating that it could not auto-detect the device type and needs a "-d" flag. I could not figure out what to pass in with "-d."

 Is there software that can report on the drive's specifications, S.M.A.R.T. indicators, make, and model information?

---

### Post by DuckHook on 2016-06-19
Welcome to the forums, donald-a-pellegrino,

The "Disks" app (actually *gnome-disks*) is very informative and displays most of what you want. But it is only available on Ubuntu proper and Ubuntu-Gnome. Click on the upper right details icon to give you SMART health report.

To use *smartmontools*, make sure SMART reporting is enabled in your BIOS. On my mobo, it was disabled by default.

The -d switch is just asking for type of drive because smartctl could not guess. To find the actual /dev, please post results of:```
sudo blkid
``````
df -a
```Your /dev should actually be of the form:```
/dev/sdx
```...but if, for some unknown reason, your system assigns your ssd an odd device name, then:```
smartctl -i /dev/nvme0n1 -d ata
```It is better to find the proper sd<a,b,c...> and do:```
smartctl -i /dev/sda
```

---

