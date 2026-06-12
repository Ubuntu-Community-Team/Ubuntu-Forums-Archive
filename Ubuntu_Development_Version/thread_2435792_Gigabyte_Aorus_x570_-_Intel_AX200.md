---
title: "Gigabyte Aorus x570 - Intel AX200"
date: 2020-01-26
forum: Ubuntu Development Version
---

### Post by tom.j.tang on 2020-01-26
Hi All,

I'm stumped!  Have a dual boot system Win10 and Ubuntu 20.04.  When I boot directly into Ubuntu the wifi never works.  But when I boot into Win10 and then warm reboot into Ubuntu, wifi works!  My Ubuntu is 'stock' 20.04 with iwlwifi backport applied.  Any thoughts on the below?
[B]
When wifi works...[/B]
```
dmesg | grep iwlwifi
[    4.269670] Loading modules backported from iwlwifi
[    4.269671] iwlwifi-stack-public:master:8324:9176b151
[    4.342297] iwlwifi 0000:05:00.0: enabling device (0000 -> 0002)
[    4.347959] iwlwifi 0000:05:00.0: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
[    4.347984] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-cc-a0-55.ucode failed with error -2                        // Is the NIC trying to load new firmware, failing but the AX200 already has the right firmware from Windows?
[    4.347997] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-cc-a0-54.ucode failed with error -2
[    4.348008] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-cc-a0-53.ucode failed with error -2
[    4.348019] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-cc-a0-52.ucode failed with error -2
[    4.348030] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-cc-a0-51.ucode failed with error -2
[    4.348042] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-cc-a0-50.ucode failed with error -2
[    4.348053] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-cc-a0-49.ucode failed with error -2
[    4.352633] iwlwifi 0000:05:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[    4.352635] iwlwifi 0000:05:00.0: Found debug destination: EXTERNAL_DRAM
[    4.352636] iwlwifi 0000:05:00.0: Found debug configuration: 0
[    4.352842] iwlwifi 0000:05:00.0: loaded firmware version 48.4fa0041f.0 cc-a0-48.ucode op_mode iwlmvm
[    4.352860] iwlwifi 0000:05:00.0: Direct firmware load for iwl-debug-yoyo.bin failed with error -2
[    4.387854] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    4.399567] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[    4.399897] iwlwifi 0000:05:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    4.991752] iwlwifi 0000:05:00.0: base HW address: dc:71:96:88:04:69
[    5.006711] iwlwifi 0000:05:00.0 wlp5s0: renamed from wlan0
[    5.709464] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[    5.857902] iwlwifi 0000:05:00.0: FW already configured (0) - re-configuring
```
[B]
When wifi doesn't work[/B]
```
[    3.865594] Loading modules backported from iwlwifi
[    3.865594] iwlwifi-stack-public:master:8324:9176b151
[    3.942724] iwlwifi 0000:05:00.0: enabling device (0000 -> 0002)
[    4.068089] iwlwifi: probe of 0000:05:00.0 failed with error -110
```


**uname - a**
Linux tom-X570-I-AORUS-PRO-WIFI 5.4.0-9-generic #12-Ubuntu SMP Mon Dec 16 22:34:19 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by praseodym on 2020-01-26
20.04 LTS is still beta. Tried 18.04 LTS or 19.10 instead?

---

### Post by oldfred on 2020-01-26
Have you updated UEFI from Gigabyte?

[https://askubuntu.com/questions/1149116/intel-wifi-support-for-ax200-cyclone-peak](https://askubuntu.com/questions/1149116/intel-wifi-support-for-ax200-cyclone-peak)
[https://askubuntu.com/questions/1175392/ax200-wifi-does-not-work-with-ubuntu-18-04-razer-15](https://askubuntu.com/questions/1175392/ax200-wifi-does-not-work-with-ubuntu-18-04-razer-15)

[https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html)

---

### Post by tom.j.tang on 2020-01-27
Hi both.  Thanks for responding.  I am on 20.04 because for some reason 18.04 and 19.10 didn't boot on install and it was suggested that with my HW being so 'shiny' to try 20.04.  Lo and behold it did work.  Probably because I have a Radeon 5700 but not sure.  Also my BIOS is updated to the most recent, F11.   

Is this something the driver team should be looking at, I can reach out if someone points me that direction.

Thanks!

---

### Post by howefield on 2020-01-27
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by tom.j.tang on 2020-01-28
Thanks howefield.  Please do let me know if there is anything that I can help troubleshoot...

---

