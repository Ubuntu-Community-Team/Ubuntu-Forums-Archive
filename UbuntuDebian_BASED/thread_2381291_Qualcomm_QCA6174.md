---
title: "Qualcomm QCA6174"
date: 2017-12-28
forum: Ubuntu/Debian BASED
---

### Post by leewil1 on 2017-12-28
Hi Jeremy, I am trying to download the files but it requires a username and password to access?

---

### Post by jeremy31 on 2017-12-28
Try copy/paste for the commands, use the right click on the mouse/touchpad or CTRL + ALT + v to paste in terminal.  The only time I have seen github ask for a username/password for git clone commands, it was because of a typo

---

### Post by leewil1 on 2017-12-28
Thanks Jeremy, copy and pasting the latest commands worked for git. 

However its still not working, any ideas?:

root@kali:~# lspci -nnk | grep -iA2 net; dmesg | grep ath10k
01:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Samsung Electronics Co Ltd QCA6174 802.11ac Wireless Network Adapter [144d:c14f]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci
[    2.536704] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    2.538909] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    2.817657] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/pre-cal-pci-0000:01:00.0.bin (-2)
[    2.817666] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/cal-pci-0000:01:00.0.bin (-2)
[    2.821187] ath10k_pci 0000:01:00.0: firmware: direct-loading firmware ath10k/QCA6174/hw3.0/firmware-6.bin
[    2.821195] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[    2.821197] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 0 tracing 0 dfs 0 testmode 0
[    2.821723] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4-00022-QCARMSWPZ-2 api 6 features wowlan,ignore-otp crc32 4d458559
[    2.884641] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/QCA6174/hw3.0/board-2.bin (-2)
[    2.886431] ath10k_pci 0000:01:00.0: firmware: direct-loading firmware ath10k/QCA6174/hw3.0/board.bin
[    2.886769] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 20d869c3
[    3.434685] ath10k_pci 0000:01:00.0: firmware crashed! (uuid n/a)
[    3.434687] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[    3.434689] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 0 tracing 0 dfs 0 testmode 0
[    3.435118] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4-00022-QCARMSWPZ-2 api 6 features wowlan,ignore-otp crc32 4d458559
[    3.435460] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 20d869c3
[    3.435461] ath10k_pci 0000:01:00.0: htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    3.437786] ath10k_pci 0000:01:00.0: firmware register dump:
[    3.437787] ath10k_pci 0000:01:00.0: [00]: 0x05030000 0x000015B3 0x0094AF7F 0x00955B31
[    3.437788] ath10k_pci 0000:01:00.0: [04]: 0x0094AF7F 0x00060130 0x0000001E 0x00000010
[    3.437788] ath10k_pci 0000:01:00.0: [08]: 0x00401FC0 0x0040E948 0x0040E950 0x00408794
[    3.437789] ath10k_pci 0000:01:00.0: [12]: 0x00000009 0x00000000 0x00952A41 0x00952A4F
[    3.437790] ath10k_pci 0000:01:00.0: [16]: 0x00952CC4 0x0091080D 0x00000000 0x00000000
[    3.437791] ath10k_pci 0000:01:00.0: [20]: 0x4094AF7F 0x0040E8C8 0x00000000 0x0040A2E0
[    3.437791] ath10k_pci 0000:01:00.0: [24]: 0x8093F091 0x0040E928 0x00400000 0xC094AF7F
[    3.437792] ath10k_pci 0000:01:00.0: [28]: 0x8093F0E6 0x0040E948 0x00401FC0 0x0040EA30
[    3.437793] ath10k_pci 0000:01:00.0: [32]: 0x80926B65 0x0040E988 0x00401FC0 0x0040EA30
[    3.437793] ath10k_pci 0000:01:00.0: [36]: 0x809E1F05 0x0040E9A8 0x0040EA2C 0x00000000
[    3.437794] ath10k_pci 0000:01:00.0: [40]: 0x800A113F 0x0040E9E8 0x0040EA2C 0x00428650
[    3.437795] ath10k_pci 0000:01:00.0: [44]: 0x800A08C5 0x0040EA18 0x004202E4 0x00400000
[    3.437795] ath10k_pci 0000:01:00.0: [48]: 0x800A0B72 0x0040EA88 0x00416DA0 0x00400000
[    3.437796] ath10k_pci 0000:01:00.0: [52]: 0x800A0658 0x0040EAA8 0x000008E0 0x00100000
[    3.437797] ath10k_pci 0000:01:00.0: [56]: 0x80910829 0x0040EAC8 0x03EF1480 0x00007DE2
[    3.437797] ath10k_pci 0000:01:00.0: Copy Engine register dump:
[    3.437910] ath10k_pci 0000:01:00.0: [00]: 0x00034400   4   4   5   4
[    3.437969] ath10k_pci 0000:01:00.0: [01]: 0x00034800  16  16  15  16
[    3.437976] ath10k_pci 0000:01:00.0: [02]: 0x00034c00   0   0 127   0
[    3.438037] ath10k_pci 0000:01:00.0: [03]: 0x00035000   0   0   0   0
[    3.438044] ath10k_pci 0000:01:00.0: [04]: 0x00035400   0   0   0   0
[    3.438103] ath10k_pci 0000:01:00.0: [05]: 0x00035800   0   0   0   0
[    3.438162] ath10k_pci 0000:01:00.0: [06]: 0x00035c00   0   0   0   0
[    3.438169] ath10k_pci 0000:01:00.0: [07]: 0x00036000   1   1   1   1
[    4.444085] ath10k_pci 0000:01:00.0: failed to receive control response completion, polling..
[    5.468224] ath10k_pci 0000:01:00.0: ctl_resp never came in (-110)
[    5.468238] ath10k_pci 0000:01:00.0: failed to connect to HTC: -110
[    5.518979] ath10k_pci 0000:01:00.0: device has crashed during init
[    5.546965] ath10k_pci 0000:01:00.0: device has crashed during init
[    5.546967] ath10k_pci 0000:01:00.0: failed to wait for target init: -70
[    5.548668] ath10k_pci 0000:01:00.0: could not init core (-110)
[    5.548699] ath10k_pci 0000:01:00.0: could not probe fw (-110)
[    5.572174] ath10k_pci 0000:01:00.0: cannot restart a device that hasn't been started

---

### Post by leewil1 on 2017-12-28
I figured i had to many files from previous attempts to fix this in lib/firmware/ath10k/QCA6174/hw.30 so I blew away the old files and just loaded your files and this is the latest after a reboot:

root@kali:~# lspci -nnk | grep -iA2 net; dmesg | grep ath10k
01:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
	Subsystem: Samsung Electronics Co Ltd QCA6174 802.11ac Wireless Network Adapter [144d:c14f]
	Kernel driver in use: ath10k_pci
	Kernel modules: ath10k_pci
[    2.496980] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    2.499196] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    2.774273] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/pre-cal-pci-0000:01:00.0.bin (-2)
[    2.774284] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/cal-pci-0000:01:00.0.bin (-2)
[    2.775547] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/QCA6174/hw3.0/firmware-6.bin (-2)
[    2.775553] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/QCA6174/hw3.0/firmware-5.bin (-2)
[    2.778081] ath10k_pci 0000:01:00.0: firmware: direct-loading firmware ath10k/QCA6174/hw3.0/firmware-4.bin
[    2.778086] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[    2.778087] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 0 tracing 0 dfs 0 testmode 0
[    2.778516] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    2.840599] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/QCA6174/hw3.0/board-2.bin (-2)
[    2.842046] ath10k_pci 0000:01:00.0: firmware: direct-loading firmware ath10k/QCA6174/hw3.0/board.bin
[    2.842391] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 20d869c3
[    3.404911] ath10k_pci 0000:01:00.0: firmware crashed! (uuid n/a)
[    3.404914] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[    3.404915] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 0 tracing 0 dfs 0 testmode 0
[    3.405364] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    3.405697] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 20d869c3
[    3.405698] ath10k_pci 0000:01:00.0: htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    3.408026] ath10k_pci 0000:01:00.0: firmware register dump:
[    3.408027] ath10k_pci 0000:01:00.0: [00]: 0x05030000 0x000015B3 0x0094AF7F 0x00955B31
[    3.408028] ath10k_pci 0000:01:00.0: [04]: 0x0094AF7F 0x00060730 0x0000001E 0x00404580
[    3.408028] ath10k_pci 0000:01:00.0: [08]: 0x00401FC0 0x0040E988 0x0040E990 0x00408794
[    3.408029] ath10k_pci 0000:01:00.0: [12]: 0x00000009 0x00000000 0x00952A41 0x00952A4F
[    3.408030] ath10k_pci 0000:01:00.0: [16]: 0x00952CC4 0x0091080D 0x00000000 0x00000000
[    3.408031] ath10k_pci 0000:01:00.0: [20]: 0x4094AF7F 0x0040E908 0x00000000 0x0040A2E0
[    3.408031] ath10k_pci 0000:01:00.0: [24]: 0x8093F091 0x0040E968 0x00000000 0xC094AF7F
[    3.408032] ath10k_pci 0000:01:00.0: [28]: 0x8093F0E6 0x0040E988 0x00401FC0 0x0040EA3C
[    3.408033] ath10k_pci 0000:01:00.0: [32]: 0x80926B65 0x0040E9C8 0x00401FC0 0x0040EA3C
[    3.408033] ath10k_pci 0000:01:00.0: [36]: 0x800A13C4 0x0040E9E8 0x0040EA38 0x00426BDC
[    3.408034] ath10k_pci 0000:01:00.0: [40]: 0x800A0864 0x0040EA28 0x0041F1D0 0x0041E1D0
[    3.408034] ath10k_pci 0000:01:00.0: [44]: 0x800A0C5A 0x0040EA98 0x0041DDD0 0x00400000
[    3.408035] ath10k_pci 0000:01:00.0: [48]: 0x800A061B 0x0040EAB8 0x0041D7A0 0x0041DDD0
[    3.408036] ath10k_pci 0000:01:00.0: [52]: 0x80910829 0x0040EAD8 0x00000000 0x00400600
[    3.408036] ath10k_pci 0000:01:00.0: [56]: 0x80910927 0x0040EB08 0x00000000 0xFFF08040
[    3.408037] ath10k_pci 0000:01:00.0: Copy Engine register dump:
[    3.408149] ath10k_pci 0000:01:00.0: [00]: 0x00034400  13  13  30  29
[    3.408210] ath10k_pci 0000:01:00.0: [01]: 0x00034800  16  16  15  16
[    3.408217] ath10k_pci 0000:01:00.0: [02]: 0x00034c00   0   0 127   0
[    3.408277] ath10k_pci 0000:01:00.0: [03]: 0x00035000   0   0   0   0
[    3.408336] ath10k_pci 0000:01:00.0: [04]: 0x00035400   0   0   0   0
[    3.408343] ath10k_pci 0000:01:00.0: [05]: 0x00035800   0   0   0   0
[    3.408403] ath10k_pci 0000:01:00.0: [06]: 0x00035c00   0   0   0   0
[    3.408410] ath10k_pci 0000:01:00.0: [07]: 0x00036000   1   1   1   1
[    4.412217] ath10k_pci 0000:01:00.0: failed to receive control response completion, polling..
[    5.436201] ath10k_pci 0000:01:00.0: ctl_resp never came in (-110)
[    5.436206] ath10k_pci 0000:01:00.0: failed to connect to HTC: -110
[    5.487220] ath10k_pci 0000:01:00.0: device has crashed during init
[    5.515142] ath10k_pci 0000:01:00.0: device has crashed during init
[    5.515149] ath10k_pci 0000:01:00.0: failed to wait for target init: -70
[    5.519449] ath10k_pci 0000:01:00.0: could not init core (-110)
[    5.519541] ath10k_pci 0000:01:00.0: could not probe fw (-110)
[    5.532259] ath10k_pci 0000:01:00.0: cannot restart a device that hasn't been started
root@kali:~#

---

### Post by jeremy31 on 2017-12-29
*Thread moved to **Ubuntu/Debian BASED**.*
Split from [https://ubuntuforums.org/showthread.php?t=2323812](https://ubuntuforums.org/showthread.php?t=2323812)
Sorry I don't know much about Kali but there seems to be an issue with the board.bin file

---

