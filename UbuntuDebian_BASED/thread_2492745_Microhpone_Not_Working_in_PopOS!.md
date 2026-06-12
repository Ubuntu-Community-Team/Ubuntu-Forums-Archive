---
title: "Microhpone Not Working in PopOS!"
date: 2023-11-21
forum: Ubuntu/Debian BASED
---

### Post by midnight-sunflower on 2023-11-21
I am trying to get my headphones mic to work, I have them plugged into the front of my Desktop PC and am unable to find them under input device in my settings. Neither the headphones or the audio jack is the source of the issue. I think I am using Pipewire instead of Pulse Audio. I am using the audiojack on the front of my Corsair 4000D Airflow case. I plugged in the port to the motherboard's F_Audio header, and according to the manual, > [FONT=sans-serif]the front panel audio header supports Intel[/FONT][FONT=sans-serif]®[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]High[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]Definition[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]audio[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif](HD).[/FONT][FONT=sans-serif][/FONT]

```
Operating System: Pop!_OS 22.04 LTS               
          Kernel: Linux 6.2.6-76060206-generic
    Architecture: x86-64
 Hardware Vendor: Gigabyte Technology Co., Ltd.
  Hardware Model: Z170X-Gaming 7

```

  ```
$amixer -c 0 contents
numid=50,iface=CARD,name='Front Headphone Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=on
```

```
$lspci -v | grep -A6 Audio
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family HD Audio Controller
    Flags: bus master, fast devsel, latency 32, IRQ 150
    Memory at ed840000 (64-bit, non-prefetchable) [size=16K]
    Memory at ed820000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_avs
```

---

