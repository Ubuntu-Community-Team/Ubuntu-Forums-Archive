---
title: "[SOLVED]No Wifi in Kodachi Linux with Intel Corporation Alder Lake-P PCH CNVi WiFi"
date: 2023-07-31
forum: Ubuntu/Debian BASED
---

### Post by blackwolf-oz9 on 2023-07-31
Hi all & apologies if this isn't the correct forum
I downloaded Linux Kodachi, based on Xubuntu but am unable to connect to any WiFi
Tried Linux Mint, wifi installed straight away but not on [URL="https://distrowatch.com/table.php?distribution=kodachi"]Kodachi 
[/URL]
```
System:
  Kernel: 5.15.0-78-generic x86_64 bits: 64 compiler: gcc v: 11.3.0
    Desktop: Cinnamon 5.8.4 Distro: Linux Mint 21.2 Victoria
    base: Ubuntu 22.04 jammy
Machine:
  Type: Laptop System: _COM1_ product: NBINF-M7-12R5N5 (15) v: Standard
    serial: <superuser required>
  Mobo: Standard model: GM7AGEM0015COM v: Standard
    serial: <superuser required> UEFI: American Megatrends LLC. v: N.1.07COM02
    date: 06/09/2022
Battery:
  ID-1: BAT0 charge: 62.3 Wh (100.0%) condition: 62.3/62.3 Wh (100.0%)
    volts: 17.3 min: 15.2 model: standard status: Full
CPU:
  Info: 12-core (4-mt/8-st) model: 12th Gen Intel Core i5-12500H bits: 64
    type: MST AMCP arch: Alder Lake rev: 3 cache: L1: 1.1 MiB L2: 9 MiB
    L3: 18 MiB
  Speed (MHz): avg: 438 high: 608 min/max: 400/4500:3300 cores: 1: 608
    2: 401 3: 454 4: 496 5: 456 6: 442 7: 436 8: 406 9: 398 10: 400 11: 395
    12: 399 13: 400 14: 390 15: 538 16: 400 bogomips: 99532
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics vendor: Tongfang Hongkong
    driver: i915 v: kernel bus-ID: 00:02.0
  Device-2: NVIDIA GA107M [GeForce RTX 3050 Mobile]
    vendor: Tongfang Hongkong driver: nvidia v: 535.54.03 bus-ID: 01:00.0
  Device-3: Chicony HD Webcam type: USB driver: uvcvideo bus-ID: 1-5:4
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,nouveau,vesa gpu: i915
    resolution: 1920x1080~144Hz
  OpenGL: renderer: NVIDIA GeForce RTX 3050 Laptop GPU/PCIe/SSE2
    v: 4.6.0 NVIDIA 535.54.03 direct render: Yes
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio
    vendor: Tongfang Hongkong driver: snd_hda_intel v: kernel bus-ID: 00:1f.3
  Device-2: NVIDIA vendor: Tongfang Hongkong driver: snd_hda_intel
    v: kernel bus-ID: 01:00.1
  Sound Server-1: ALSA v: k5.15.0-78-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Alder Lake-P PCH CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3
  IF: wlo1 state: up mac: <filter>
  Device-2: Realtek RTL8125 2.5GbE vendor: Tongfang Hongkong driver: r8169
    v: kernel port: 3000 bus-ID: 03:00.0
  IF: enp3s0 state: down mac: <filter>
  Device-3: Realtek RTL8152 Fast Ethernet Adapter type: USB driver: r8152
    bus-ID: 1-9.2:8
  IF: enx00e04c3615ab state: up speed: 100 Mbps duplex: full mac: <filter>
Bluetooth:
  Device-1: Intel AX201 Bluetooth type: USB driver: btusb v: 0.8
    bus-ID: 1-10:6
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.2
Drives:
  Local Storage: total: 476.94 GiB used: 19.67 GiB (4.1%)
  ID-1: /dev/nvme0n1 vendor: Seagate model: XPG GAMMIX S50 Lite
    size: 476.94 GiB temp: 30.9 C
  Message: No optical or floppy data found.
Partition:
  ID-1: / size: 465.29 GiB used: 19.3 GiB (4.1%) fs: ext4 dev: /dev/dm-1
    mapped: vgmint-root
  ID-2: /boot size: 1.61 GiB used: 369.9 MiB (22.5%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-3: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: partition size: 980 MiB used: 0 KiB (0.0%)
    dev: /dev/dm-2 mapped: vgmint-swap_1
Sensors:
  System Temperatures: cpu: 47.0 C mobo: 47.0 C gpu: nvidia temp: 41 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 380 Uptime: 53m Memory: 31.09 GiB used: 2.73 GiB (8.8%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2317 Shell: Bash
  v: 5.1.16 inxi: 3.3.13


```

```
blackwolf@blackwolf-NBINF-M7-12R5N5-15:~$ rfkill list && lsusb && mokutil --sb-state
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
Bus 002 Device 003: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 002 Device 002: ID 2109:0813 VIA Labs, Inc. VL813 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 2109:8888 VIA Labs, Inc. 
Bus 001 Device 008: ID 0bda:8152 Realtek Semiconductor Corp. RTL8152 Fast Ethernet Adapter
Bus 001 Device 005: ID 2109:2813 VIA Labs, Inc. VL813 Hub
Bus 001 Device 004: ID 04f2:b711 Chicony Electronics Co., Ltd HD Webcam
Bus 001 Device 003: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 001 Device 006: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 001 Device 002: ID 1a81:1015 Holtek Semiconductor, Inc. Wireless Dongle
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
SecureBoot disabled
```

```
blackwolf@blackwolf-NBINF-M7-12R5N5-15:~$ lspci -k
00:00.0 Host bridge: Intel Corporation Device 4621 (rev 02)
    DeviceName: Onboard - Other
    Subsystem: Tongfang Hongkong Limited Device 1178
    Kernel driver in use: igen6_edac
    Kernel modules: igen6_edac
00:01.0 PCI bridge: Intel Corporation 12th Gen Core Processor PCI Express x16 Controller #1 (rev 02)
    Kernel driver in use: pcieport
00:02.0 VGA compatible controller: Intel Corporation Alder Lake-P Integrated Graphics Controller (rev 0c)
    DeviceName: Onboard - Video
    Subsystem: Tongfang Hongkong Limited Device 1178
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller: Intel Corporation Alder Lake Innovation Platform Framework Processor Participant (rev 02)
    DeviceName: Onboard - Other
    Subsystem: Tongfang Hongkong Limited Device 1178
    Kernel driver in use: proc_thermal_pci
    Kernel modules: processor_thermal_device_pci
00:06.0 PCI bridge: Intel Corporation 12th Gen Core Processor PCI Express x4 Controller #0 (rev 02)
    Kernel driver in use: pcieport
00:08.0 System peripheral: Intel Corporation 12th Gen Core Processor Gaussian & Neural Accelerator (rev 02)
    DeviceName: Onboard - Other
    Subsystem: Tongfang Hongkong Limited Device 1178
00:0a.0 Signal processing controller: Intel Corporation Platform Monitoring Technology (rev 01)
    DeviceName: Onboard - Other
    Kernel driver in use: intel-pmt
    Kernel modules: intel_pmt
00:14.0 USB controller: Intel Corporation Alder Lake PCH USB 3.2 xHCI Host Controller (rev 01)
    DeviceName: Onboard - Other
    Subsystem: Tongfang Hongkong Limited Device 1178
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci
00:14.2 RAM memory: Intel Corporation Alder Lake PCH Shared SRAM (rev 01)
    DeviceName: Onboard - Other
00:14.3 Network controller: Intel Corporation Alder Lake-P PCH CNVi WiFi (rev 01)
    DeviceName: Onboard - Ethernet
    Subsystem: Intel Corporation Wi-Fi 6 AX201 160MHz
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
00:15.0 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #0 (rev 01)
    DeviceName: Onboard - Other
    Subsystem: Tongfang Hongkong Limited Device 1178
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:16.0 Communication controller: Intel Corporation Alder Lake PCH HECI Controller (rev 01)
    DeviceName: Onboard - Other
    Subsystem: Tongfang Hongkong Limited Device 1178
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:17.0 SATA controller: Intel Corporation Alder Lake-P SATA AHCI Controller (rev 01)
    DeviceName: Onboard - SATA
    Subsystem: Tongfang Hongkong Limited Device 1178
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1c.0 PCI bridge: Intel Corporation Alder Lake PCH-P PCI Express Root Port #9 (rev 01)
    Kernel driver in use: pcieport
00:1f.0 ISA bridge: Intel Corporation Alder Lake PCH eSPI Controller (rev 01)
    DeviceName: Onboard - Other
    Subsystem: Tongfang Hongkong Limited Device 1178
00:1f.3 Audio device: Intel Corporation Alder Lake PCH-P High Definition Audio Controller (rev 01)
    DeviceName: Onboard - Sound
    Subsystem: Tongfang Hongkong Limited Device 1208
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl
00:1f.4 SMBus: Intel Corporation Alder Lake PCH-P SMBus Host Controller (rev 01)
    DeviceName: Onboard - Other
    Subsystem: Tongfang Hongkong Limited Device 1178
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801
00:1f.5 Serial bus controller: Intel Corporation Alder Lake-P PCH SPI Controller (rev 01)
    DeviceName: Onboard - Other
    Subsystem: Tongfang Hongkong Limited Device 1178
01:00.0 VGA compatible controller: NVIDIA Corporation GA107M [GeForce RTX 3050 Mobile] (rev a1)
    Subsystem: Tongfang Hongkong Limited GA107M [GeForce RTX 3050 Mobile]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device: NVIDIA Corporation Device 2291 (rev a1)
    Subsystem: Tongfang Hongkong Limited Device 1178
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
02:00.0 Non-Volatile memory controller: ADATA Technology Co., Ltd. Device 5350 (rev 03)
    Subsystem: ADATA Technology Co., Ltd. Device 5350
    Kernel driver in use: nvme
    Kernel modules: nvme
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller (rev 05)
    Subsystem: Tongfang Hongkong Limited RTL8125 2.5GbE Controller
    Kernel driver in use: r8169
    Kernel modules: r8169
blackwolf@blackwolf-NBINF-M7-12R5N5-15:~$ 


```

I asked for help on the Mint forum but my post was deleted & I was advised "we don't support that OS here."
I'd be very appreciative of a knowledgeable person who can help me get Wi-Fi working with my  Intel Corporation Alder Lake-P PCH CNVi WiFi

Thankyou!!

Found this link but have no idea how to install it??  [https://linux-hardware.org/?id=pci:8086-51f0-8086-0090](https://linux-hardware.org/?id=pci:8086-51f0-8086-0090)

[IMG]https://ibb.co/vZLjb9Q[/IMG][IMG]https://i.ibb.co/0hYGk5F/Screenshot-from-2023-08-01-09-45-58.png[/IMG][IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAnEAAAAnCAIAAADvp4msAAAAA3NCSVQICAjb4U/gAAAXxElEQVR4Xu2dd3wU1fbAp zO9uxuNtk0kmwIEIr0FpqGKNIEQYqIIkVFfYri84dP9Cniwwb ngXrTwEJPoXwUIooIhAEAgiEIgRID l1e9 dmd9syWZ2dyZsgMSE3Pnkj82de88953vOvWfuvZMsnJqaCjVdBoMhMjLS92vzByRh2srlydlrPjqsJiEIibjzmRXpDZvXbr1s5g9c PrCiCPrN57QUHdcl6Df3OWz5YfXrftFPXTpW1PqP1nzYwkOIdFjHpmVmLdt6x8NBIT2fujNJdytr2RcdPr6oMr 9Ri2deXmP50Q0m3qyy8kZK364oSRhGXjnn1tVP669w gE/6 fJTml617z1UaSb5MQtSWN LXa/Ubmfbci m237bsOF2HJd09f/7A6i3vffunEaE19OgAC 6Y/8qiIQLz6a/XbL1qZ6AAitqAAD206DEAoT3nrFoq2rHymwtOd50BBd989WsZLOWbq9DRLwRHAlX9qbhj//7yQKWF8OkJi/s9 PfHBptP7f3lRH6dmeRJY1RhjX ct48LJSpc ixNOPdt5u8lWm5C2ryHh2sz3914Rg9HpYfQnD/ksTfncH/ 7LuTNRYo YFXFmOZr265RPjbUi27b7U77C8pQpBJY9JkoqCFAVib3MwEik5/7u8TyKNbdxwr1sEx6Uuf7H7qnQ8PNSBxE1seVnSfux3R6 zHG09ovaPdYbalLFgdbCbZNL6uKMc/9dwE554Pvsyuh5n68o00/0mG1i2bE FJtEmJqg8LRz655j71529kFuCe5mjcsLQES1Fprd6GSOJHznhoPO/QuvcPSh/0TTW0MOMw stnCDUvURfKZIKTha2XEdWISY0D3KltPalCvIELV88yb1i9vQD3G1wshlC QFX3r3xmGM/pOPf12z8UNc/PLr5hw5a8PEv4 6atp40Jk5bMT/pz/drdpQ6fpziDFr832/Tlqsx8L36IkzJ31SL 9lUZf3al ZRDHzIhfiYaju/OHvv8AxNOFhyKHNkPyt12tFRjbAog7emsMxP Nmx4woHf TzIYXe4bxA12RmfZjd1YLfa0TABF4L8fNZy93jlb19tRB64b/4L06QYYWq4/NOXm46rW25D9Vt7eOPXnFn3P/LSFBGuLT2744udF32q jUmLZezjjcMHXTxWEFXCoDrAewI94nyI7uOdp zYOUYxFKdveWDHxgiob70ZFb 4olLJhW /WNx05iGSGNu5oefVU ZOPahZ2eKOYRFV1N6bt lcxdDjQoIFiSNXzh8gQwxVl7a9/X2HD0VzmRIQWW9uHdHr3mTnn1jJh9x2ky66mwz1TbAlvWXvYBDD1S6R2BJf/YBuH8XnUlN1ob/g2dOn/lcupwH2U2ayrMNNkpUq4cVqpry4ptTvEo4Lm15dSOTmT4lHVWHt xIXjHn4bSi9YeYhnB98xMQS6yxOPGCjqW rxgWCMMTRg5Pm6GQ8GG7rrrgeMZ3WdUEJGVsyOyvgKqMuOpZ2HrbsqmRQJfdNpOqveBiHve /ipOQVHT/OztlNkQAsKvZWdX3jUN3XusJHByJvU52zaGz5uzaOUkrrEsJ3PDL7SEyoSUmzSgL5q3s6A57TLVuu3K4JDWqbed2f4GoTwhl0Tk/acvmc7duy7jPHPSvc0hAPOCCAQ82gfdBwWAQEcnwE1 4OXHwve9u G062mwPS9Ylrr0HxPqvnr3x KulVSR9qTcQftCYtOfXbP2zWV3Y9mbMi AhNpB3QTUAgQAgdYScBT/ticvYep9fYVwa5veVH1Y1H/alLgruw UdK2ESkED69SbihzQGBAABACBDk0AFkbHCdUVDe18pIVFdpMbK2st7bw8/utdcSPnqX 91kADQAAQAAQAgVAIkOaaCnMoFW9tHXt9Re2tldhJpIG9307iKKAmIAAIAAKAQIcnAHJqh3cRUBAQAAQAAUCgkxAAObWTOAqoCQgAAoAAINDhCYCc2uFdBBQEBAABQAAQ6CQEAt9RKnl0YyfRHKgJCAACgAAgAAh0LAJgndqx/AG0AQQAAUAAEOi8BEBO7by A5oDAoAAIAAIdCwCIKd2LH8AbQABQAAQAAQ6LwGQUzuv74DmgAAgAAgAAh2LAMipHcsfQBtAABAABACBzksA5NTO6zugOSAACAACgEDHItC5ciocG8HvJ hYBKnvIYiQ8brzPVrRP3c0PW9vfQD5YP yM4FhhQChvsC4za6OOVTbzNy/TDAczkfa9xtnXKYiGCrvXKmjHR3UlmBgmHdrvY3wl90TtTTy1gr1h30DOiOCf0yOekrh1or uR29ePt3dV2/dCLyNFtgnuiDuQmfdEfbJKbZmST2iz6aLolpk17dwdgOQ7WjBv2N bTlVmx3RdHyrdMVE7B2ZoFOHh37/RC sJ277STdhZZTYd5LM1WHxghp6QyZdY/q2Ah 4P M8JnNEa2fH7eiTfPfLUfcGXW 5RDaWaA7tDL7cloKxJvziyRcvDI99th8VeFCVc6smE/786XtbCO9O39bSIf9QL5hv5q4 S/Eik2Jzl0YvzrUPHlD6TQUZ90MWxh7empi4aKkksVJ Y8kZE1VruyBhdEFtliBwdFIYHTBPPGmR P/FUSJrS3LpIdMH594eaL/QwlXuG6eamsfDhzoU3jg0G5598tSWJArU6KvzlWk4k2R4IZcujjJ95M/QSJ3MsUJjC0eLtHmag/eim9xg/n8p8fHnVmgujQn5q1kLs8POzJsYEzOXMVo7yjF953Xm1LCF8lYTLqZGOj8bVlzYrBp3XtGfm6sefSCLcTvDeK2NE0Gi 8QJZ1R5w4Bro2VuGG/iJXy/9wbxr2mXf1bfZ4VCpfyB3NwYxtr27J4P1sIx97zmpbrh3QX5T3aj2 zkzP6iT6tNtaF1KYDVoIlGHzxbOVjV3EOD03pJl01KqY7VPFkIU54lWWtIGR0NBnSHMQcJO62LJMekVVstt4lnigyfNMUTOIY0d0c69prToKA/H1KFjbaHX2wFC6U505 vQbEbE22Pb1b/QdO/Qb3UmCkxpTndKg9keDOU fOVj2V7/RYTeKEBieD40QYGzZfaH4t3 ESc7MXOn2U8glM/7edRk2E7NOxyuX6qvfqqSc9OCpasmywdHI4InU2p25ca/iyXPpGX/6m4xbLzXZ9u7VvRU49W2CE 0WuUle/XI4HPFajQsEzI VzYrAI0pF9Vf3KeYtrVMPcx6eqHocgp0b3kVr8FFc9 qBRB0HRvaMP9bbN3qW5TEK8uIhjd8KvbK8/yOU/OTL80W5YOOE8W6JdfcZ4lfp eBh7aJziiVgsngdbdLolP1mb8MNJvZTfD4Y 3lf3na5ZF4TPf3xE KJ4LAImSooa5p4wGwTMYhenRy6K5ERTe9MOZ06RZuVp0zVP/DbrrJ2 xzRwDK333ZqzPCZp7CHBhMXfot2aM02zBbuYLnOHeu4OxS 7NHkCpngL5gRji1Kl0RX1U46aGtx3ywyO8 4PCEtg MXbHtMdd0UsjuLGYLDD6jhZrH3nnKnQGXLz3Vp0cMyHvbFIDtmgMX9xvHFzg3s9So xn6wLZiuFx8ueLyPZVGJl4jbEc4V1C5vDM7 VjT fJp0rM36ipd1r siVCF9MDZ8TwxHanVetCEqNL/d101EKjxzKZKZXvN9QZegraIXucBJaO07Y8bqrmoxE0fIoDC200EcJQ4UinNnRsN9yiwEKVcQWJO62bJOeocp00K6cruJuueRJacid3YWc6sb91IIDEbwz1 tTT49Wta0IkfSXwbvrSKq7iSqeNIwzVan5o5r6ldMvHCmrtOl8rcpdjRwOvN7ie5JgkEnpPUwl5FbWZwfPk7s15/gBA8Q6YFz8B2jjmCyT3uVywduzlWGnyp8t8XJFRKIHuxH//VV30kBCBs3nyd1e6sn/oN5CZVGJhGMqrp ZF7ZvOJ0fcazEwhstGoZajt6KlM7sms5ZGtJznMc0c4N22Qn7uLGR88P8l/wwd0mach5iXL6rfNIRc1ifyFUq9/kQ6dz4y7WUjNK uzXfVtqICN4dKFWKDI7i8cN4g1wv9cA9o3iCeksOzl2UFrUEM7 0pyL9V01BpGJjqlDuuo8OiMXKLlSN2VYaA t2lgxSQqNgxBthys/56WUKmpauH4qMf55ld/rhi3s/p/LtsMMKvYXpGcwvNVd2ZWTDlshJIjViU3HWg166y9Qvr3TrJIY3M8IxYWi9hkdK1yGA3JLxBLvAXBQsMEE2TEb/lmT0Jtvs8eGH7xRqIpSm7x aq07RUzjhjMCZEZqULXvnGIzQkyv6DhkZ3lI/5bs97AX5kqUXnGDT3GfLmCXSYrE589MGdab6Gt1PBzueEHHffBFL73hTk6EAR7ZrxyOmFYtqs8fV/DHn1TKrsFUcpiprt3v6HK2FeQ1zwFMIJ07xY2QwEVapnXYfQKJJujWYTTi1mDxF2JddJzWLaX4P2SRElun8I8wfQ48kCBWc3UI260XbBy itQarZFZcKJQnNGMXS3iu9K2hysv5S4UM9sI5OwpjKYO1CB5NXbba7uA2eqoAkZOVNuJaMEQ9xrKI5CMIprzapuflBBpVhP2HFV64kK4kqjUyrHotyTeGGB p08a03Qo7 l0ZaHYQMkLenYNe 1IqdSgKpLGlYUc166U9rXlR29FxounhPh2Hxan2PCr1VqPy DxsTz3M HJEGQNpy0E6S2ynyOKxhN7b jvDGRzit6bEw0QoXCqBjOxUqrIVw8L9Lx9UntUZ2zstH0do4JSZRMaJoYdCZnnRWvNOCeTYbIeMWmUdivh2s/8zz109SghHx1QpulcdYaHRd1ONyiWKPZWWtxFlXpMiqhgUqsacHerLMnvny921uU1ozj ligAIuC23blkuv6BWGNt0BsMA VQXitJXApREVs6PGmNzmrzM6Cav3Lp0yYSnIPDwq9uUZvLzLhapMtM99iCMOSvKMtMMYovVuWycLEay8qFc LIvYVWy2kfXexPaq7ZHzQSytouGi6zLbhlO64Dq/WWg/W4Z7VBfvgbUWUspgJBQxVpr740 9yHaAWLVJdGCf0aD10WLdLC1QFjybuGyvQXK178Yp3C9Tn3eAKEIujPU089S8vUFE/uXMjxvnPeWxB4uuOcdKjJrecAmOJXDzT/XJiVKJkrN20vTIo83ikEPacBrJPJEZNaT0SRcoq4yeFZjJeNIIDceS8/rDrbkDsDhkWd HhxIvUz/y4fyiZji1hNFpA1lmaT LpM1XwhGyrMp9ABRNcouA 8UJFjel3364fVcSBhQRh8q44SYuDhKiSAJ38fyVtzjoCjREw6dZiw9v Ziv2ft0siOyc owp0esG2b5rYoMKOVEIb8UM1YueEhjCq1Ah7BdepNVysCF8dhznY0SQajauLhOujeOLatG75PYDFU5YxlESjlKTV6LD4KhGeLGUtxjO3uG iSKh1fSRgQwIQ5cahKOMdthLlYQiVmcj CG8jx6iNF/EsGBxbx2CKwQCbH5hAcuwA0U90GkhRMmnhr1fsLTWlR5lrXpHJSKKEVCbpSHFFTVR3TNY8Xx3XpIAtjshCWxu4QE2RJlMTOABPcQpRtPrrtMvqLTUeH6wfK4K3Zfvd0CDCjjUqUpF0KsQLDBbE6WsZgYOVaa kJzsqnvPQ5SHCLvTAbmy6qVLNcsLnFZq89NKMuoRXAFlcbTHca76hU00uMJ3p/q99sQWJLQIZZj0qLu4xrCtXvpET/76RufMXvyKQvUphhj0iCFOV9uxvvzeHPyeJOTQKUtjHbGfUD4Qi5RJeEqt RS12PTPTbkXa5cVeB4mSGPQQ6FHKAxDgZOg wYTZ1RgN 2pUryq4vNriMkJ6PEL5kaahaSTNCOoiFopuY94hVwYokpoFRg/EhBM6QCuAAKtzanU6aht/THd2MkRT1D7 K69eQi34I24Ze2Omv/QnYCKcBLGfMtZ0rm/1Laih2giJjBX1f9RAdf1EU5M5NyhNq00QjjmrEcEiSKvQI6YE03iVcyRRP5 svp4YtT794abf2mkP2pRaqgRXjz1cGXw2oibQxLbPN2SkJ/O/qhClOZrxIwF6XB/XdthhwSbX1jAMjxV43rrMYP8gR6C/602018Eaq0rPYg4IjSKxOusEI6GFFfixPD3U6CP9ld820hw4yIOpLmnH5YYC1GlwOUMJZDDn5PM5fIkG d5t GECAL3FCcU6K7RXOuR310MQdQbDfRyxsHbmihlNtNtasBQZXYcXRs3IZvVec0QuDal1wquwOZoTytXfb1XIMzzbnf5BLbc1lstaNJzlZPOXXnm50aK7y3DZ8tsGYftrCkVgmprLCXDhWk94KmIeUUNFQS2nSXE5p7iKzBWVa0uo/zqn5xsNmeFkQYh HGMxBus8ADXYiDw7RY2zlkFpn OEaeX4ZMx81vlfq a4zp7ARnWh9pHpE58IaS3gqPT2GsZoq3ZDzAXVSD4edpil 6jrvw52FfXp2FX61ZexJUibxTgauOPWt7TqdJxck4EH01SYPFUpiac10zoKJWAOrlPjuBSGyQ1ZaYzMukbPaBD1 x2nWm/VfjPQbzcYnMlFWBq47YG7mMjpWOlaGy46OVhYuia/gCbt5yObUdq/20R/3tc0wGVW2VKyA8a3hOpsjQ5J1LA6RPO4bVKLCUiSGc6C3YlCTOOJCm4EheP5s/MWK5PF9QIIuDvF5mGKd5o5Jvbk7YNZ4zWpMhvRoelR3BVYdx 0aKHkzBuKwID7hkrHCLlUGH5P0PE3ApjFpVTQ2xOHXS4VKE2F2GEyqWeGYolxkKVGcRGEieexLN9uK9yyi7vz7QTZkuEeIYsMBqpIfbEaPnEcE6EgBPH9y4wbiBKMQyNFnFi3D/UW36UIAYzPXr6D9Ub6CvIXJYCFkcznCsHCwitbcCk5xGjLtPvdoheGyuWVuh3tfg2Oa61HDZgS4aKLcWGHFfuJXMLDKWx8mXRxO8VLSXjYH29JaQjV0P2UnCDV0VsnE1Vhp0O4eujxVCJ4UjTG2oeaYTJlFmBzBoiHR3G6Z0k/1sM/kOBlWGXkKYNV471ctov Q7mWRXtcjeCPRIKAvJqbsOXibGzvQ6xf3aoDhkhf2 KXMmBdAbz wfqvtfbNp/RD0uN/LUXrNfqX/hZfcRs2lYuHx1m ol6KZF07C1xPDcQ31bqfhYjHZuy6rCR8venyeWk81yxeskZ5tN r3K4fdPRxuHTFGv7WufnOrwbRIT980O16Aj5O1NlkQhZXa1ZfEDfOrGkv877/N8SZ1OSsG3PtawfqHy pnJNHf0zE5YWB14o6LtinQC//KxmjDeaF5ofsNXlDXP325cPkLwzKVyBQnqT/Vyp9lCpOfTACFNKP07GomH8crn2yZPG pDD1VimeSMm4vlJ8f/kQnYHUas1uF4BYYsxtui6jr/Re3sIofKGLXVO39sx1UW6nf2jZyTzPjtDj0bHxkO1yIjw1yZLY7iQ1eq8UuIwufRpdZQOGhx7fLBXLVt5/fAsJjN9avsNVaa 3HtdN38xO/paC0vH5j5Da s/6XlaO62br9rnDUW yTUzvWpNM4u0/1ruXNoX31HkzaC4wZhZK1sjNe8POkwNjQZ5sszCHyIchFpPBywoCRbOhO37PPuiofCmvOB8ie86URc7WrF hoxvte06UfuR yiB/YKHJgqxKvUfjLvz7M26wh04NTXVZ6fBYDC uKcrmA1sBASuTyDojyKu3wTUAATajQDKf/1 ZdyFyqeKArd/21oFRCj56n5p8cHKt1x7xeDyI3Aje78AISAACAACgMBfTAC3fnbW0n IPC3oNe82Vgy5e6isT6X6C5BQmUCDdSoTFVAGCAACgEAnIID0UCCVjc52/mdGwjAsxmovavnEtRPQaxMVb w8tU1UAUIBAUAAEAAEWkOAKGxk aPY1khpbV0z9YfXrW3TZeqDvd8u42pgKCAACAACgEAbEwA5tY0BA/GAACAACAACXYYAyKldxtXAUEAAEAAEAIE2JgByahsDBuIBAUAAEAAEugyBwHeUkjKWdBnbgaGAACAACAACgMCtJADWqbeSJpAFCAACgAAg0JUJgJzalb0PbAcEAAFAABC4lQT HynesFWdK/EgAAAAAElFTkSuQmCC[/IMG]

---

### Post by blackwolf-oz9 on 2023-07-31
Found [this ]("https://askubuntu.com/questions/1326386/ubuntu-20-04-lts-driver-intel-wi-fi-6e-ax210-160mhz")but unsure how to install? Even if it's okay to do so ?

Moderators, please move post to [Any Other OS]("https://ubuntuforums.org/forumdisplay.php?f=401")

---

### Post by blackwolf-oz9 on 2023-08-01
More info
```
lspci -knn | grep Net -A3
```

```
blackwolf@blackwolf-NBINF-M7-12R5N5-15:~$ lspci -knn | grep Net -A3
00:14.3 Network controller [0280]: Intel Corporation Alder Lake-P PCH CNVi WiFi [8086:51f0] (rev 01)
    DeviceName: Onboard - Ethernet
    Subsystem: Intel Corporation Wi-Fi 6 AX201 160MHz [8086:0074]
    Kernel driver in use: iwlwifi
blackwolf@blackwolf-NBINF-M7-12R5N5-15:
```

Also found [URL="https://askubuntu.com/questions/1352653/intel-ax201-wi-fi-6-is-not-working-on-ubuntu-21-04"]https://askubuntu.com/questions/1352653/intel-ax201-wi-fi-6-is-not-working-on-ubuntu-21-04


[/URL]

---

### Post by blackwolf-oz9 on 2023-08-01
I downloaded  [IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAt0AAAAgCAIAAABBxlNLAAAAA3NCSVQICAjb4U/gAAAgAElEQVR4Xu2dB1wTyffAs mhE0LvTWpAunQRrGDvvaGiAoq9nXo/saLoiR7WUzxP7IANVEQFBKQoRaV3AZEOIaTvf9MghHKcd/c/y 7Hjya7szPvfae9eW8mAiAIIuALJgATgAmIEAAA4DsYGb4PLeCGCRP4cQjw yzyx1EY1hQmABOACcAEYAIwga cAGyXfOUVBIsHE4AJwARgAjCBH4gAbJf8QJUNqwoTgAnABGACMIGvnABsl3zlFQSLBxOACcAEYAIwgR IAGyX/ECVDasKE4AJwARgAjCBr5wAbJd85RUEiwcTgAnABGACMIEfiABsl/xAlQ2rChOACcAEYAIwga cAPo/kI9WER8RmdbIQaCUnOYtGqWF w9kgIuECcAEYAIwAZgATODrI9DXX8JM2eNiOjI4nfXPCdtxb7UF2fd2M/cX3MCO5F9Ol7kE7oSutQ4FJ0 mUEQKYhf/OtXMfH5EDafnJu1T/ts3H2q7RJJ1Pt5gZ Z9/D2bU31prrnF6uj2AYTtehRoYSR2kf2i2sBBX2TVv47YvWyim62lhY3LmJmrDz0opQ1QAIL1/oSPqbHl0sg6EZE5dTH zqYuQY8aem6Cbcl7Rps7 t2uYUN5sT5n/LHPb5qHnaW5uZWz99K9N9 39/zAHdiWF7l3qbezFdnCzmPGurDnHxm9yue0Fz8 HTTZ3mzEjiTmQJJx79Pr0iP3LfawNJ97qVpEPu4jWtXz8C0LxjlbW1jauU Yu/6X57VcwaBr4NK5bcPExHnj4xbxH PrSt8/xtTEYcdLnjhc7GZTfy0WZMjPtfm2L9l8XsRHMTn4ZcJ/fwsE2BUXZpuJdidjq41PezdNrhq06sQLu7j9x8KMbOs dXXIwzLR3vufatpVMzkwzimeOsRWyHifqxjw6tAn8fY kA7c9P4vt1YI0rOa67eeSlReFytxqCSvcwhFg8w3aYVzjr1UCYrDr3uqvT9j5dOGskG7 ECSiN/ndF0Kj0cFvD7T1vOE qluS3iyBlRWUIJVeMGNT6IdtlcGzI7WiKhM46BYk i2npkBZGbxpV0fhw18anA050ghvVcWIOtdZuGsIy8U18VJbX5ucTw3pIjOQYAVCWm41Y8AsT8BqScaedw4nSFHYkWfItdnR4nORyCr5F3Z8pBnuMCsq71bFqW2dvOvXI0IQQnDfy24ViciLK398q0My21P8IFPNA9k7Xzb2X j5NCfP8113R0vGfBYcXfqkqdNn4bYVsSJw9 /nMDf8JdAU/v88ac0TqaGjMIOXQDmm2ft7n6tV34 SpPRGrPAteVcNtPJBSPIAKXn5qp16kpqetuiqfIA7ybl5ZFF6x5xRocknJwoy7/FyE3NpKqOdzNCARSz8QsWEAwGEwClM/Ng8FSNbgsMKasjBf2a5UAvcuoebZu/5bnkmCVrg620pWg175MLGBihgOKK0t9E36/AElCZ0Q rZvnqoPjPkaoTd29PmLblwH4vu1BvRahosCnh4E 3aaND/jdNHUrELLkbGlGgP2XV3vW6JFb547Ohe1e0St0/PkEB0pCRf37VkhOVw2b77QtSoec/OHfBf1HtyVsHPKGHYEdx3KWwX3 PLwWUSKxBRkvmp/QbZ8Iu3M1skVeW6DOwsUoj/RcFv1OfsnTDYnN1PKXibXItC8tDNFjpPO04TbEnzi9w32KF74bBLv3j2M0qNkJWHA/8/bsiALY0taDIK8L3jCPyeyKAlNPs0zWoub H3q6zmR4420RLlpofFXZ88woq8f4eR4keGGBbwYukOlXXkcaCPv3/xQktNXGkdqcWmi//P14qSoG0aqSkgwwvY5B5905uaD3p2CrLUUoEQ2zXnxTN6brxe/qSdIahpebmGTKqKFZ5 acL9zPv5Bjc9zd06uluXyA158OL3A15DI5ggOJJ1/nZ/2T2Q5LukZVmBojO6NiChScZ J0WkyV75c mtF55XHwwqbEShyOKdXFGx82UZqyRzvGxUorsztiE4p2/vgG2jdisyqfLTo/NGBvbZeWqGzpOWg3JyC9ubgdRSASgMtz4vjJTZLpnpz7NPdAgYyHDexFk1FMAuzG2p62xwmaG0RdIzi55Vxn8sPxaFVtFFhBbO7Mbq eeeJckq7Z9jsEwSKP40kXHKbQtNstIAIJDPXvudUCN9LrJVqdVkDVFlT9dTq9BOl yFBQh1Jn1Iuq19wuWq8ewy/qYptLqA/cyR3fYpUwjSotSgazbrXmM2aMeOYu9/gVVA7/SD4G/YZf0k9tQb7EaKho7CZ1tIEJJbHxAGbm6qFyISXlDm pJ4GZHz05OpyKRnPSkzK6JnryRjV2clt6s4OxujkYAcvaLttkPXiwgoWZqbWMo0iO56Qd4EWxPCN0fi55 9upeF8GI6eI1cP7U1OjYZnv/DXIXDsXEFC1dZyIsBank/dNPL6ZtOBD8yO64D6kxNnjvA TksN3jlXiTP8Z45R9xfkiBreRgS/qYMuf68xzmhFFYsCk27Gyu3Mxz53a7SEN0vLxsZJZMPXwsYp77BjIaQS Ie1RjtPzkiTlqDxfOujagaGBDyr007JhdV33HfQ522dwgmpDz6e7BoxnKK65GrCfzICNGuI7lJ/iT0qFEgKwisTYy9Masy4sFZhjY OjExUJ5FYXP/S9ABpQRfvCNEeBAdglSnWxHNuc3m/7Fl7DfeuchCiXoCvbDcYWJq5NeFLAcrXtGG87H2KPb472uuxnLinXM/vP8x 5iZH2n/YvmM0pFLXiGUFiQXtrElhum4Wcqy1s4YQctGvyY s4vnTlyluNddykB3xFaq20LPMNKFt1TyJ1FFLHr/hoPamXp4nsUFyvi89yeFzvyP97qkNkZaLRYBRpm5EfI01/uL/k933Sybe9JgdpyLZc9cpLd9hFAyP8yEkRLxhEPb3AU3lDw1EXk7vwQ9b5ro6oENLKxayvWxnVYT3OO9ZDkrxs9zdX4ifFEuTHEnoxASu35ao6Fl5YbPx3I/EwBdLSJdtp92wZYmleTJatxaauuc/lbozui0rCfxBXFgcqXAyzn8 zCKSYEyr6cn IaZy9QxFZWhRYB05dah9jwLAk9ec3OJM HVZvIBuYiMQN2Q/Wul9Rhox1jJsly7UBLZVt0inN84QXXEUGK/5IpK6oC/FlAoG8cp1dNF56abD391ItnJ/2nulmTybYec3beLoRmH3bZuRlkr0NvmJR7q8lGxjabE7jeXLAtN3LP0gnOw82hlDM3nE1t6OsXxFh7yiRGM2wnzp47lvju9yS5UcN7LbgwFu7OREpGSh5/jc96n5xKsZ4xRb8zLTGbzpONU/M6rVrayd0K2pfCqb 22NwiMHbAMMtAFT3Ai2D7y hnbeQ5y52GsowD257fjafae0 ZOtFDruxBdLaoSxsgjdmxxwcTfzD4/tuovcHxUnP3bx8p8AFBUiGFRglXQjaNRkegsRhuy6dmJKR1aYybOoJrlHAvlPakqfaYypcvSyGaAGniidg7R/289KUHrzosed312Is7Ztko9fElceoex7zmOC1a3M/sMnjpXHGQShPXzlXLPhcWz4vLQQKnnzn5kjjXf4rK4BLxEvMuXhBNLLr2JZXYkyP86f DAEhpbmbIKcr38ZCIF95tlHAfsGg0FiBo3OIJ// /sz7NCowb9ZLGrC2x9n8yK0uw5Oa0tdxMq3stiKWCVc/TCJuy74oOK6zmwJ2xmtebBH2c0/Xidc29j0x H2BVF5EDnq8r5jAK32sEJO35CLKqCs0CEndUchpTMqCYBS60ooopKLr/sACnMyKxsVND55ir0CjhwSEaGhywx1akVT6gQt/A5FvPcT8XZgqz4JUClTuI4xQBUpt2XC5rtDb/1Q4v2kOZTDYLgZIQDg8AFoVHgDQmRywvlJLuk70jzo0i6fYZSMRrD4mEWgYWxR 3wJzMmlyCyiYngVEinrjnO1iUWvGIo7DGSYpvEIE0egMLq9L/AIceO8c1189ovhZGfEnNan3wniFP1pjKd1ZBY6WM8lJzzOcPn9PZCOrnzmpA0kGbN8RyL6SltjSirjGhVVRd8NOHzxkcmfkjZITOKaTVCDVrTtuDD1D4SXA1vMrAb8i5x TEXY1Hro4b/4oBZQFS285fTzfb hi7hhefWhOLCXgyNpHG4cYNxSJW3ObXfxvoYfKjf/rzqYRecmn7sSJT38MXL4cF2bXf37v1t0I2Snte OOrq80wkl7BjxMS7u9wwiLo78N9lx7/oL3o0O93bp3dPKIhwj/oarm4ZQJIu6xbY9RSmnn3dlpxu1VAoJNU7zrAWbuPkG54ncLbnMAueZXSYDRyySwPzZaUpA/cQQRsyUgtwDu42w22ZOuVJQiyRa5BWwS77H0hQ8lY/sOp9bO97C3NLey95m69lNHU70tgw5OoJI6jzygFKUcfL4WaR1GvezkMAOKo7Xun4uN3LtrzSmnZwQ3dloZYo6MXR565X688drw11K3ZdeXVdJSuvm7PUgGQ1tNXBqsrqvksgSHa7QBygISswvdFoK4h/sWR1dNG2lqYWzqOW7Ln5vsOqHv9eemQ7DgL3/XjkI9PXMiGxm12yR ht2lj1i23FN3Bs7m83pHvGQajPDniQIrvjrO9xJaCVXD/Kfjns/emf9r/Xnuks4zOxzS31cbS3INiOn UObkvrECHv3PUr2xQsJNL1xY437rn3/S31QKkreypzkglae7QEWpHxYEJG9Lo3K7WMgK7GwHWek5CHapNFyE81wn4ua3vHGAkZZ dIrOfNi6hu48xpYXdRUIqU4UadnOEWr6T392X6zOlLBxrIo2KPIV0N9gO4ooEBre12H0DRUMBQfktHORnI4elta3WDGx4AoQca927nnEJoXZyqL abljVQ9ca1nHn0qoIEgnXo3tioDT5pu3D1z92Q5lBGHRaXcvl/ kqC4xJJn/YDM7CoqoC7FSns3dt8zmYA46W1JPnfrCvvuRmK2hCe1yVtpzxIuBTkURiPISXucbr7tCSHgidbBrN15XT3vAYh QYLUzhIKQl9VUqTSkEZqEkBHZ0knAkdAEzj0mp59iODHpi42p6u0qRe50noqBy9lKohSch hiFJGOLD0M69h8C4FW8vCXSZeaKT7VOeyYPcIWwwAMm5dy1hXRNjuP7Ix1OvdSh1rDNJlmkusGx6JVzm/16M8mPdnn8tlewmspLy3AT9kLswR/rcPAXGjs08CqIGpzjgcuoY3awzXb34ZtyfjTRNopKSopiKLQwASCmrqatxn7bHnLpVYbozdPYe3bjYy3FaYMO9BfPWCFTpimeJ1vFZtGzg4QrBzt8fHvU6v5Ziq16S qtR1c9U2p7irXE5OKt5kZULLSs1B2W53EDNnuE4HCpUhnPsAJEZCisAbCln5JyeTTwpkQKkuuBz/k/1AanPaWls5LQ9CfnFcsObnxToSlMK4M8dC/GpRdy4vEm4eEWrDqX4UlY52OewmB/UUO 8xKrfuRyVucRnLj5HyUgFyDpM81O5e/WQ8zqcf5wSUgl2fHLZpy/niYQHhm5x5gd0uaheIxEviRTofQJAgIFhUbt/8B ZusKutjcauuHbgitcSv8N auim7KhTv xd0SJx75fxg5cu6PJIec9AP5spx0JvzDwid/xiicXaEC95RqkQDP/fXtiFjzA2vE8oKZIav/6oub9uDMtSX3XhyJSeHUC9M4K/fTUEsMo6esoM8tRZa7dId1UkXjp2dt0aZOStALP PSj0yrjDQT/dbHLcecHPnJeEXX5 7uTj73jrC8hOLZtJPg99RJsE3Lm5WjzS i9rjZSeaE4IyWnM5ZDsEdR7uVR9VXxuzueK0br6rJZnZQj3aSSoY4tYXUhnC5J8atOLJtBaEZGZ3UBTkpIqrX/cqbFQkgnZMbKm k6iGNAYNSJeDoVA4rHaCgRuvxXZDcFhsjqY3f TO4DBoQk0JhTWlpPEiJslCAReAiOBYLXRILuk3xlZAIpBZ1HZQtsFAAh4NA4Aq17n WVhNgUZjSIg O7mbqxIovrxqfUe196apgBoAGQh8JPnmy7o8egOkT Y /CVzYN2rnIAxm0iWbAvEGQ2UUFmXWkgU23zZKt90mBVcdWuB9nj6ZjsuSShR4NbRGNOxe/Nkn7uij0bONB4QxUcXVt9xQRjOUZnbHzBwfNZyE1Oe7X6sukREmSwO6HpCAftX m5JLjeGzaFAeIMVKfI1F6KLvZaqOcpD5YXVKx5QUEi0HTuHr1uqiCVwYYcPhK9MKMghw V3k0WgcRhtYlYKA1DkqCjwIsKsTuSylhkd725mjhoyjEbrrdct2pXFYWJkMABKCUifwXNKUh8tzUb6bvSaoP6YIoMkfv3nWygCbpHa6SMhb2xYDoEJOTksGBlVz9dhF35vrCTVnPYx/6o4F2QSWWqtXf8ZX6AjKObFSo4Jb11oXtacqGK8w59FJo9yk3hWvKr6rUG9WmZdMtVTtCY0ftiph0Y63sDOn3MuwDZaWeSD47kfkTpzjl2ZKYmvykAGKK4fSGaDYDGYEGG4rwTx9cY8dCQhxuxikcHP4yvnt 9q5X/ArvkfnSuhPsJV56Zj7XyHqtx7UZUfNOYadAuK8FFfXs6 FaHsaVW8bndv42MWCnkKMih8fWZLZvCc SnHLq2a6KewHUI2SAAh9YJIcYJ8wGp1C4EWoI3uP39C8CgoWGIbeZ3 sA8NR4V8nDNjg9Tzt5PbBtnMbTSkZozNs6PnB8euApXSZr7 yxoxCgRk6wXdugZ2B4fvPJCr0Tsj9HbAs40eYVc9beSFK/Pv68onMM/TAClOeVYzBRhpmRLM2SJ55ZHcQVrzMh9nCHM2oRjQduvVOosPhm5cZSaYJxBacw4dmckz812JWBz2oiQsEUG0Ks4hX52EvzDwvfJDrAiK6k/b37RANoA9fcaiFuXSx89U/ wWWd1a1MiQ367qfiWRgkD5dH47GclzCAiNfod22eqGepGbnQ c4FFS3w5avQC7v6Pvu6APuVCN8Ds2BSHWIrQUEH6LPaMscBAA0l1J3c3qBjMrk5mJwItTxi0h4BdZ06/hAJJguJQciF7HNexK5fdbjL0cdzZz5gH1r7JHXez3drbKtJCmoRg5OWVb7uZ7osfccm6V7inP/lF7wHDXK0yLdkcFrOirGbfg9ceTIdXk QIAJJrEqBIh/3MZvHWW/a68oqtbV7ptUkzSd7d0w6n88qLBpq 8QqtHu1QJPVrO9WFZcg6aCE 7Mq58aZjl5bsINMVFIeShHYS0NmiADu59gRaCgsAEkrHVhi3XSn23lPCgcwXeYVAT/WGe02QoCLKAJAdg6CzO3t5piCzBiGJE0Sn qeBlLLVREXk1LxyMnSTRrRU1dz5iHK0kxE1U vffZhyu91 9ogTZuLtqv88f y7g1S0EAwG2/9qSAwcEoVCKkwIvhoosl8EwMoo9Rmx/hQ4QHR2twDDUjM/45JzZV1WcTeToiw83GRvJ6XUjfic3mI6w4V7xqX3hTZfdirCp3t9gyYZcaMiUBqAoGxgZj601RhSTVMVidU20u3mAshrqEmCbzs6xYpj5kbHFDFb8tfa3O95AtRHxdZOWcg3h8GO18d3RDS67Ltz1Pjekrmnt52yu7bBSrh3jV3zcNvS7U8x43vme6Yc ONpSqriaOnV8CBcCGC4QAO8pK6wENbc2/jlIcEu87Vl1DCUUcZsjfgsu9g1LTVEGx2zo6kYOXLhLOwpGXb/CO9o/heJ/0tYD8KOLxuj7YweYCaMcMN0jOv8C2tJA1e9P1Nl75eaxyn9rsTgZ/ GoJAJJqGkREVlt7n6mUXnxt3bL9WcrzTtzaPEZT1JzGyGsaykMasRlELIAlahkaDq1j/hsQMDpK46WrnhXTp9Hri/S1fIZJFRPLY951jaQ2fdbRHNvrAAavfLzCJCPk6oKWVrXWh3RSiDEJZYacl9PYINeSDCocNhzCWCpQAxjmZBlv3H2cDlBQQSPxMnYqiLiipkKOvOhOTMjNAgWbGDiiPXd3qrjLBGSDghEPwE2fZW9B7faXYPTlEDmPql52slh3k/B3e/it3vZop6Nt7UKpyGd1n4zJGeNV VELE3VpZmXCsmd1u6109Qc1gcTqAi8jaclzgFjpyMs3NI15XZvhLeeGwuoqoNAMabOecDugTcIhGUzuOWMhKlp5VXgFavIyNe2BSwRwBB0pRDLPYhvkAiQkDaQQN2s76QhJ4XDKKaqjglKq rzv8nq6d/ZoNzZRG0GMJglHS886jZQi9w5u6SlLIOmU/GbQR3if3UQppAO6ShKDDb4A1sNaQfpq2bid5dC2FwZAGO0x/Ixjj3nXWVU681KtjJfd706SQ5pMB9Hzx3g09L7Ulwd3dxuHI3BwoXTIJpIX8j60KHiLHCDlvzRwm ubKfcOUtnFzejI1ecRYBbW6QCZV5N4Gw8XyY0v7jxuq9b3cOWv83u9DcjqWNnr9J/hkO itJ2ddcIev3lHG23N91 wK9/lt P1DMSiDF3p0Q9r1GYe 2W vnBO5Xx 8NPaiOj75fP8oENtYGtSyK7Ido DuyepEpDLD65/NTtk21GHmz85c/0r7LKITbueEOadi9jqIOb5kbAd6YB/ jgqbbUl7zwOgl11LzqdqTnPTXhUbsjaDJAQbeLqpBCZk13FttPj9zZafl4JW26EAQk5eOmiIwMgO2pPTHwgKK/Wx3U1QLmit nFVzcEXQdn/np80TDxjSlDeB1O8p8QYHZ1IQgE4cjK ZSXV4/U1tcSG7Lp2aeCDmZpBV4 v8rsi4 Q/H/oh5abZIqek18b2UFxdFRUQGGmWBJOZn 8waEOt1QUbgfhdkHhbI/2tCCyYxp k21pNTFyh9bQw5Vwlz dlqO0Gejxjw8OUWwpkqw7SSyt1GI30rHIik0vVaI8era NhUW78xk6LpoefNQcmPTdBZFIBDY8LFd HtASHUNYreTgZ81aaR1pk3PPlZGYeGoaOb6teZzlCSwINeTALI4IoEqKBICqQqZOoPHi0TFBplsBKbHlcDpoLERKCTPEEU5mRIlclvS2kEz/gABst5WdiJICj1OY5B5/3lNJVH9Ern3phYWFJFBSQqnJk5LW0YrYKAq8SdzFVp2ggn2XN7HqHYl/nkcsL3 0jsmiazYE7YHkCSSFBc8qyMssRFjSh7Ta5cioGqiaAMU/ZHWHsA/j4PgvH1d xaQ3W C67V0QgJQm2d3B Jo9dtuNdnO97hjg2ymIaQkMdzzSMKL1Vy7/GzxR3PLRB/5oZymEOX7w37 k7oejAtSQVdHlp5870aqhquBto6i /Jl5vPDgtYC/gvdDWQ5DfkvkrvGbls nIDASErh2DlvU0tGjTYkDiUYgdJycdE5ceHaU7xniI2g5RDsPJwwmyOugpqLd/fjlhxM0r/wDGW6MHB8zJZNgbiAha46uOacOyfPFevM2eHVu0V1JEU9bhq2aPF4M5HlnpHcTLur7F5PtuMGuNP7D7Dm300Z 8eb4AtN6C/Ztfzfx55/4Rtw PIXGKH0bncsyXWzPykpME0gE4NbKdviwAkCb4 0YuPLVlJcpvgbMKLf/fNvZCeELoEOCf9DF8HRd63D7EP G9lrZzmoAbWpV09cbyQHLnCA9gvh/kLpBHm1IW8 FhUdbHoevPZItubS0FkqzeVlzdxnSAlFTRXpwRYl/5DycDZfSoD5Pnzeynjt6bM8rQyUMU050eHhbxQmhk3imuxdySG Ybl2G35b74B4Gx1TJmkTZNicldTduKV0rIdrisTtUWZBD/OCvlSSf o9lLOFIvZSaSgod8yX610fbqmkllB ApDePY/An1kAPFoapGUWtdfKy6rhEPImys6R ftfISctJnKjEwbK45BvjyUh3GeTRPZKfpl4gJaTeXjx66W3U 0KNRaZ836/pOzTb6 bO7QN7k9U4AVDAGMjBc3H9WfSta3tCB2VVWvimpmIAe16gqyUpciZaHoTtHmFo6EqY869iZrhqHD4etGcO BGSxlFBCMnp3zPB6THHBUDJIL6oWDcg1a3yfbBRoN5MhnVJS6nP k668wzlCIBjPz8qn2ZbKsJata8bkyyNtz8Mm1z LuOcWoOMpyivPIdWYgx8zSHdy/kmmrCclk2PlqOvXwInKy4VO9syWUuyk6qeGxHS0RsaYqM2h170bm X8LoceMMPfPerz2VW OpzP39kmclMQjSqfGK0FY2kNqw dJHjJmysyqe0EV59LLk9Gdi6EJV7uFfDiX8t7w/0JoRizT0FbX2uX70eZo1hW2wXA/TXFa9P4Gi52q3AkonmgwjaaQAns qeqSpaqEkqcm1XTnNzdQ6hpQ0GuBu8BeeOQBpLbvP5t3DaVz2kqZ8phTwKpEgTdCWHAxsv r9UDf/zlyHc1q1c1ZpyC03 dHJ50wN1k5bkrxFNhV8M2RTTScSR9m7GLCVxrHcCNmLvULuPc9k0q ncDhrQvH2Xo5qp trjB1t21d JB1GOWAexMu7uBv9i9MXQBq77woq/Gj4L0EXGxgEVRO3VeGbfYXGEb9tgE3Pop53WQVN6e3BQKqMnzny KYHUZkzKyJ/fgiOD905rjvehNKc8b8dSdO3/bzb0TzMp7WplUMrPBvge7a7taFUF16O38U17XFmfmcvyoQevxq 42YnhmTguPTEptWj 0auvryhorRmnYjAnzx28ZD/6Ra2lLrFqM0XN80fxmsM/37pCFbxyxfVDErl2ZU 3fpj3Q4knpv l3fdfTkD M2/SgBjPG Xf8fFO5eCIz5REDIaZNeV4euXu/HqjNNSnpeTq8g9dQm2NreyW54fXf28pwC06bro22v u5DNQKpKGip5ImuidVQm8KI2GC3lSXLlv CUvIU/VoHR1thoXr/jVtZ 5ZGnjZCAFGmSLie2WmmqoLMQp/U6SwQAAAMMSURBVJqiIrJkJvbZjDJQiYPdRxLmLnEaZlJ2OKn 2O3KRgZ3gsMQVY7P1LEX2v94g2HXpzPX3HtFuopQUFNaN9mgM7J6sDwHfAbouVi9wJXsSShdnEjrQKDV1YiLFo3YyZv 2ZTOjIo21Z6ga/ 5YNU0j45nhqaW sZ3tXLQqipyPjPsf3aTESw90TLb19jLxRSGRWZu7UIoKBFnLrAPdhAYfFCTSU sTEMrXnSU7D2cIy3dzPZ2lf327P2JFha05d/WTD9mku74Pucc sqEUtK6uR61J6rsRGRtMwIzzEDjt8XDFvKrEkmw0wTOJBddbKB1YvDmRhq/b9SfyQ2NQRe7uqY1HU3iqgugPWfY35ct3JNcuCiBIyEnM8HH9tBoBe6qFBRJhpRZN0Mv62bF9CNlYxZ6xDiQVjhJTnqQqsWP6UO7WaSlJ4wyDR9DlGtsfPCR3cWpmn2gSigwYD/FLWWsmNZ9tfmh7wBgtzPqh YAKw8TgAn0EACgX0T 9keGb1sLDqukqO5CYuWlvE6Mpur/FpKXCX5HFW6oXxeBlrfZRn8wd6y3XK2OhQ4rcFiM9yl5Xrdo63c6bReYPl XwF zNPw3f8JV zdrBsMAGYAEzgWyaARBsYax4y1tzb2nInnaID xK/1srkOlOYtPfVlDJJKRUcgtLakV5F7ZSUNhb NObXKvjXK9f3sCr6eunCksEEvk0C37anQcj8 9Di22xBP5LUICM1sWhfckNaPa2NDcjISFgOU/UfrzdD5V/ccPC98uX3Wdgu V7rF9YLJvDlBL6PGf370OLLaxF EybwrRHg91l4V/C3Vm wvDABmABMACYAE/h CcB2yfdbt7BmMAGYAEwAJgAT NYIwHbJt1ZjsLwwAZgATAAmABP4fgnAdsn3W7ewZjABmABMACYAE/jWCMB2ybdWY7C8MAGYAEwAJgAT H4JwHbJ91u3sGYwAZgATAAmABP41gjAdsm3VmOwvDABmABMACYAE4AJwARgAjABmABMACYAE4AJ/KsEoP8B4/8APksF1fUGPeAAAAAASUVORK5CYII=[/IMG]  
[TABLE="class: icstable"]
[TR]
[TD]Intel® Wi-Fi 6 AX201 160MHz[/TD]
			[TD]5.2+[/TD]
			[TD][iwlwifi-Qu-48.13675109.0.tgz]("https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi/iwlwifi-qu-48.13675109.0.tgz")[/TD]
[/TR]
[/TABLE]
 from here >>[https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html)

and copied the extracted files to /lib/firmware/intel but nothing changed..... I was in the live system, so maybe I have to install Kodachi, use LAN & then do the same process? A reboot should then pick wifi up???

---

### Post by Rubi1200 on 2023-08-01
It's been a very long time since I tried Kodachi but don't you need to use/set a password when first using? Did you try to install drivers via the Panic Room menu?

---

### Post by blackwolf-oz9 on 2023-08-01
Hi, thanks for replying.
Yes, I installed it to hard disk (have used for many years, with no issues but new LT)
Check for drivers via Panic Room as well as the normal check for drivers via Software Manager

[IMG]https://i.ytimg.com/vi/ADQL5bJw-8s/maxresdefault.jpg?sqp=-oaymwEmCIAKENAF8quKqQMa8AEB-AHUBoAC4AOKAgwIABABGEMgZSgyMA8=&rs=AOn4CLBa_52aIpxccS-DVRjuXRZzDJef7w[/IMG]

[IMG]https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.GKHkozA2UW-D2LSrDL-wpgHaE8%26pid%3DApi&f=1&ipt=f61a52a56ebf9ed89eb45bcc7505ef70ae6b483bb79b10e808d218461cfc2fb0&ipo=images[/IMG]

But no drivers were/are available.

Also I have disable secure boot in the EFI/BIOS.

(image as sample only) :o

---

### Post by chili555 on 2023-08-02
Is this a dual-boot with Windows? [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

Does the message log have any interesting clues?

```
sudo modprobe iwlwifi && sudo dmesg | grep iwl
```

_Note to the searchers:_ The message log is the first step in any diagnosis. For exampe:

```
sudo dmesg | grep <driver>
sudo dmesg | grep -i firmware
sudo dmesg | grep <interface>
```

---

### Post by blackwolf-oz9 on 2023-08-02
> **chili555 said:**
> Is this a dual-boot with Windows? [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

Does the message log have any interesting clues?

```
sudo modprobe iwlwifi && sudo dmesg | grep iwl
```

_Note to the searchers:_ The message log is the first step in any diagnosis. For exampe:

```
sudo dmesg | grep <driver>
sudo dmesg | grep -i firmware
sudo dmesg | grep <interface>
```


 Hello
No, no dual boot with Windows, kinda contradicts the reason.
I've since installed Qubes.
I put as much info in the posts above, so unable to run more, since I installed Qubes, which picked up Wi-Fi autmomagically, BTW, seems to be a newer kernel issue with Alderlake, so unless there's a fix, way to add drivers, I'll have to wait until Kodachi is based odd Debian, which I believe the creator is working on.

---

### Post by chili555 on 2023-08-02
> seems to be a newer kernel issue with Alderlake, I don't think we know the real issue without the logs. Moreover, since, as you said, it works with Mint and Qubes but not Kodachi, isn't this a Kodachi issue?

---

### Post by blackwolf-oz9 on 2023-08-02
Yep, looks to be the case. Appreciate you taking the time to reply :P

Ill run those codes over the next few days & let you know.

---

### Post by blackwolf-oz9 on 2023-08-06
> **chili555 said:**
> I don't think we know the real issue without the logs. Moreover, since, as you said, it works with Mint and Qubes but not Kodachi, isn't this a Kodachi issue?

```
[    4.678620] iwlwifi 0000:00:14.3: api flags index 2 larger than supported by driver
[    4.678633] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.0.2.25
[    4.678871] iwlwifi 0000:00:14.3: loaded firmware version 64.97bbee0a.0 so-a0-hr-b0-64.ucode op_mode iwlmvm
[    4.805284] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x370
[    4.916996] iwlwifi 0000:00:14.3: Detected RF HR B5, rfid=0x10a100
[    4.983411] iwlwifi 0000:00:14.3: base HW address: 70:1a:b8:94:a5:70
[    5.005715] iwlwifi 0000:00:14.3 wlo1: renamed from wlan0
[ 1024.068250] Modules linked in: rfcomm ccm cmac algif_hash algif_skcipher af_alg bnep binfmt_misc zfs(PO) zunicode(PO) zzstd(O) zlua(O) zavl(PO) icp(PO) zcommon(PO) znvpair(PO) spl(O) snd_sof_pci_intel_tgl snd_sof_intel_hda_common soundwire_intel soundwire_generic_allocation soundwire_cadence snd_sof_intel_hda snd_sof_pci snd_sof_xtensa_dsp snd_sof snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi soundwire_bus iwlmvm intel_tcc_cooling snd_soc_core x86_pkg_temp_thermal intel_powerclamp snd_compress snd_hda_codec_generic ac97_bus snd_pcm_dmaengine coretemp ledtrig_audio mei_hdcp intel_rapl_msr mac80211 snd_hda_codec_hdmi snd_hda_intel libarc4 snd_intel_dspcfg kvm_intel snd_intel_sdw_acpi kvm iwlwifi snd_hda_codec uvcvideo btusb snd_seq_midi snd_seq_midi_event btrtl videobuf2_vmalloc snd_hda_core btbcm rapl snd_rawmidi btintel videobuf2_memops snd_hwdep asus_wmi videobuf2_v4l2 nls_iso8859_1 intel_cstate serio_raw platform_profile wmi_bmof ee1004 joydev input_leds
blackwolf@blackwolf-NBINF-M7-12R5N5-15:~$ 


```

```
$ sudo dmesg | grep -i firmware
[sudo] password for blackwolf:           
[    1.754704] i915 0000:00:02.0: [drm] Finished loading DMC firmware i915/adlp_dmc_ver2_12.bin (v2.12)
[    1.785522] i915 0000:00:02.0: [drm] GuC firmware i915/adlp_guc_62.0.3.bin version 62.0 submission:enabled
[    1.785529] i915 0000:00:02.0: [drm] HuC firmware i915/tgl_huc_7.9.3.bin version 7.9 authenticated:yes
[    4.670648] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    4.671521] Bluetooth: hci0: Found device firmware: intel/ibt-0040-4150.sfi
[    4.677239] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-so-a0-hr-b0-66.ucode failed with error -2
[    4.677300] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-so-a0-hr-b0-65.ucode failed with error -2
[    4.678871] iwlwifi 0000:00:14.3: loaded firmware version 64.97bbee0a.0 so-a0-hr-b0-64.ucode op_mode iwlmvm
[    6.220388] Bluetooth: hci0: Waiting for firmware download to complete
[    6.220683] Bluetooth: hci0: Firmware loaded in 1512851 usecs
[    6.243968] Bluetooth: hci0: Firmware timestamp 2022.51 buildtype 1 build 566
```

---

### Post by blackwolf-oz9 on 2023-08-06
```
       configuration: broadcast=yes driver=iwlwifi driverversion=5.15.0-78-generic firmware=64.97bbee0a.0 so-a0-hr-b0-64.uc ip=192.168.1.113 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: iomemory:610-60f irq:16 memory:610313c000-610313ffff
  *-network
       description: Ethernet interface
       product: RTL8125 2.5GbE Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 05
       serial: b0:25:aa:4f:21:22
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-78-generic firmware=rtl8125b-2_0.0.2 07/13/20 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:19 ioport:3000(size=256) memory:82100000-8210ffff memory:82110000-82113fff
blackwolf@blackwolf-NBINF-M7-12R5N5-15:~$ 


```

---

### Post by chili555 on 2023-08-06
> Modules linked in: rfcomm ccm cmac algif_hash etc., etc.This suggests a crash (and probably recovery) of some system that may or may not be related to the driver iwlwifi. All of the loaded modules are listed when this occurs whether they contributed or not. Without seeing the several lines preceeding this, it's impossible to know if it's significant. 

> [    4.678633] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.0.2.25
[    4.678871] iwlwifi 0000:00:14.3: loaded firmware version 64.97bbee0a.0 so-a0-hr-b0-64.ucode op_mode iwlmvm
[    4.805284] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x370
[    4.916996] iwlwifi 0000:00:14.3: Detected RF HR B5, rfid=0x10a100
[    4.983411] iwlwifi 0000:00:14.3: base HW address: 70:1a:b8:94:a5:70
[    5.005715] iwlwifi 0000:00:14.3 wlo1: renamed from wlan0Almost perfect. A wireless interface is created and, I assume, it connects and works as expected.

The only suggestion I have relates to the firmware version that is loaded. Please see:

> [    4.677239] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-so-a0-hr-b0-66.ucode failed with error -2
[    4.677300] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-so-a0-hr-b0-65.ucode failed with error -2
[    4.678871] iwlwifi 0000:00:14.3: loaded firmware version 64.97bbee0a.0 so-a0-hr-b0-64.ucode op_mode iwlmvmThe driver looked for 66, didn't find it, looked for 65 and didn't find it. It looked for 64, found it and loaded it.

You might try installing 66 and 65 to see if there is any change in performance. Of course, if the performance is good now, I'd do nothing.

If you decide to try updating the firmware, we need to know where the firmware files are located in Qube. For reference, in Ubuntu, they reside in /usr/lib/firmware/iwlwifi-so-a0-hr-b0-xx.

---

### Post by blackwolf-oz9 on 2023-08-06
Appreciate the time you have given!

(all the above codes were run in Mint Victoria) 

Trying to install Kodachi again.
Took a photo on boot up.
Can you advise how I CAN load, flash the relevant driver?
[IMG]https://i.ibb.co/7kVnkFz/20230807-082935.jpg[/IMG]

[IMG]https://i.ibb.co/bQMZcFj/Screenshot-20230807-082557-Gallery.png[/IMG]

Intel folder in kodachi

[URL="https://ibb.co/mNt9N7B"]

[/URL]

---

### Post by chili555 on 2023-08-06
If you scroll further down, I believe you'll see many dozens of iwlwifi-xxx.ucode files, indicating that the relevent files reside in /lib/firmware and not in a sub-directory. Assuming that's true, with a working internet connection, open a terminal and do:

```
cd /lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-so-a0-hr-b0-72.ucode
```

This installs -72.ucode which is, at once, the *newest* version your driver accepts and the *oldest* version at the git repository!

Please reboot and show us again:

```
sudo dmesg | grep iwl
```

---

### Post by blackwolf-oz9 on 2023-08-07
Dear chili555,

I want to express my deepest gratitude to you for your incredible assistance with my wifi issue. Your expertise and guidance have made all the difference, and I cannot thank you enough.

You are a true legend in your field, and your willingness to help others is truly remarkable. Your patience, knowledge, and dedication are exceptional, and I am so grateful to have benefited from your expertise.

Thanks to your invaluable support, my wifi is now working flawlessly. You have saved me countless hours of frustration and restored smooth connectivity to my life. The impact of your help cannot be overstated, and I am truly indebted to you.

Please accept my heartfelt thanks for going above and beyond to help me. Your generosity and selflessness have touched me deeply, and I am inspired by your dedication to making a positive difference in the world.

If there is ever anything I can do to repay your kindness, please do not hesitate to let me know. You deserve all the appreciation and recognition for your incredible talents.

Once again, thank you a million times over, chili555. You are a real hero in my eyes and have made a significant impact on my life.

With sincere gratitude,
  :o

```
[IP:00.000.000.000 Germany Sec: +VPN Score:77/100 &#12541;&#3900; &#3232;&#30410;&#3232; &#3901;&#65417;]
[15:08:30] kodachi@Secure-OS:~ $ sudo dmesg | grep iwl
[   16.416610] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[   16.423828] iwlwifi 0000:00:14.3: api flags index 2 larger than supported by driver
[   16.423857] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.0.2.36
[   16.424513] iwlwifi 0000:00:14.3: loaded firmware version 72.daa05125.0 so-a0-hr-b0-72.ucode op_mode iwlmvm
[   16.757072] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x370
[   16.873663] iwlwifi 0000:00:14.3: WFPM_UMAC_PD_NOTIFICATION: 0x1f
[   16.873725] iwlwifi 0000:00:14.3: WFPM_LMAC2_PD_NOTIFICATION: 0x1f
[   16.873733] iwlwifi 0000:00:14.3: WFPM_AUTH_KEY_0: 0x90
[   16.873741] iwlwifi 0000:00:14.3: CNVI_SCU_SEQ_DATA_DW9: 0x10
[   16.873802] iwlwifi 0000:00:14.3: Detected RF HR B5, rfid=0x10a100
[   16.940981] iwlwifi 0000:00:14.3: base HW address: 70:1a:b8:94:a5:70
[   16.958098] iwlwifi 0000:00:14.3 wlo1: renamed from wlan0
[   17.107888] iwlwifi 0000:00:14.3: WFPM_UMAC_PD_NOTIFICATION: 0x1f
[   17.107946] iwlwifi 0000:00:14.3: WFPM_LMAC2_PD_NOTIFICATION: 0x1f
[   17.108018] iwlwifi 0000:00:14.3: WFPM_AUTH_KEY_0: 0x90
[   17.108084] iwlwifi 0000:00:14.3: CNVI_SCU_SEQ_DATA_DW9: 0x10

```

---

