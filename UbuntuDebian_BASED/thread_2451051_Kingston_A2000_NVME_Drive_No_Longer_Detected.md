---
title: "Kingston A2000 NVME Drive No Longer Detected"
date: 2020-09-25
forum: Ubuntu/Debian BASED
---

### Post by akeijzer on 2020-09-25
Hello,

I had been running Pop_OS for a couple of days without any issues when suddenly I was unable to boot into it. It was clear systemd-boot was not able to find my installation anymore.
I've since tried tried bootable usb drives with both Pop_OS and Ubuntu 18.04 but none of them are able to detect my drive anymore. I am posting here as there are a lot more Ubuntu users and the problem is identical.

I have a dual boot with Windows on another NVME drive. In Windows I can access the Kingston drive (with my Pop_OS installation) with no issues. I am booting with systemd-boot on my Kingston drive, Pop_OS is listed but won't boot.

fdisk does not show the drive. dmesg shows this when searching for nvme:

```
nvme0: missing or invalid SUBNQN field.
nvme0: Could not set queue count (270)
nvme0: IO queues not created
```

However, I think the actual drive used to be nvme2 (with nvme1 being the windows drive).
The Windows drive is detected in the bootable USB.

Notebook: HP ZBook Studio G4
Drive: Kingston A2000 250GB

BIOS settings are as they should be (and as worked before), no secure boot, legacy mode, RAID off.

I've found issues like this: [https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/](https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/) which might be related. I have tried setting this in systemd-boot for Pop_OS without results.

Thanks in advance!

---

### Post by CelticWarrior on 2020-09-25
Welcome.

Legacy mode is certainly NOT as it should be. Everything else is OK (RAID off > AHCI OK, Secure Boot off OK - by the way, it makes no sense mentioning Secure Boot in Legacy mode because it's not even supported). And if you have a factory installed Windows -and- you changed UEFI to Legacy/CSM mode it autom automatically prevents Windows from booting.

Firmware update, UEFI's and NVME's, is probably what you need to do before anything else.
Then, speculating about what might have happened... A firmware update or major Windows update could have change the boot order or reset other settings.

---

### Post by Irihapeti on 2020-09-25
*Moved to **Ubuntu/Debian BASED** for a better fit.*

---

### Post by akeijzer on 2020-09-26
Thank you!
I meant to write legacy *support *enabled (set automatically when disabling secure boot), but still using EUFI for both.

Both the NVME firmware and UEFI are on their latest version (updated everything before installing Pop).

---

