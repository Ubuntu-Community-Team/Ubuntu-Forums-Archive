---
title: "Got a pair of amdgpu driver bugs"
date: 2020-03-29
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2020-03-29
GPU RX 580 (gigabtye RX 580 GAMING 8G)
Issue:[INDENT]The driver ignores the vbios voltages and shoves 1.2v into the core, this causes excessive heat and causes the card to hit the power limit which hurts performance, in windows the driver uses 1.15v
I have tired altering the voltage in the vBIOS, changes affect stock behavior with voltage in windows and i am able to change the default voltage to say 1125 mV (my card appears to handle stock at 1100 mV just fine) the linux driver completely ignores the voltages set in the vBIOS and shoves 1.2v into the core
[/INDENT]
Workaround:

[INDENT]Use advanced features [Radeon Profile](https://launchpad.net/~trebelnik-stefina/+archive/ubuntu/radeon-profile) to manually change the voltage, this requires using the kernel parameter [FONT=courier new]amdgpu.ppfeaturemask=0xffffffff[/FONT] 
[/INDENT]
Workaround bug:

[INDENT]however this features has another bug, when using dual monitors (same model 1080p panels using displayport at the same fresh rate) the memory power states will change (it says at level 3 (2000Mhz @ 950 mV) normally), this causes artifacting every time something changes on the screen (mouse movement for example), this can be mitigated by setting all 3 memory power states to the full speed, this is not 100% effective, but it makes it usable, to fully workaround this you need to set [FONT=courier new]power_dpm_force_performance_level[/FONT] to [FONT=courier new]high[/FONT], this lock both the core and memory speed to there max value, however this prevents the card from down-clocking at idle, we only needed to prevent the memory from doing this
[/INDENT]

---

### Post by pqwoerituytrueiwoq on 2020-03-30
I checked for this issue on another box with a Sapphire Nitro + 580 8gb, and it was using proper voltage

i also noticed the manual frequency control section in radeon profile, by unchecking the lower memory speed states i can lock the card to full memory speed and allow the core to idle properly

This shows what happens when you enable [FONT=courier new]amdgpu.ppfeaturemask=0xffffffff[/FONT] and how it is worked around
[https://www.youtube.com/watch?v=eiqwF6DWfyE](https://www.youtube.com/watch?v=eiqwF6DWfyE)

---

### Post by pqwoerituytrueiwoq on 2020-04-15
I did a bit of testing today, auto voltage is only outrageous using my nitro plus on the factory OC profile (this card has a BIOS switch) (it is horrifying across the board on 18.04)

All testing was done using a live session using daily live of xubuntu 20.04 (April 15th)

[LIST]
[*]amdgpu_*.log
[LIST]
[*]These files are sensor logs I recorded (4 readings per second) while running the Superposition benchmark 
[/LIST]
  
[*]amdgpu_*.ods
[LIST]
[*]These files are the processed data pulled from the .log version of the file 
[/LIST]
  
[*]pp_table_*.log
[LIST]
[*]These files log the power play table as well as check the voltage at a given power state to see if the power play table is being respected 
[*]When you boot the system the driver does not care what power play table in the card's vBIOS says it does what ever it wants and makes it own default table and then ignores that table and applies yet another table 
[/LIST]
  
[*]pp_table_xubuntu_18.04.4.log
[LIST]
[*]This file was make using xubuntu 18.04.4 (live session), just look at what it does, it is shameful 
[/LIST]
  
[*]Superposition_Benchmark_v1.0_*.png
[LIST]
[*]This is a screenshot of benchmark results to serve as a sanity check for performance 
[/LIST]
  
[*]vBIOS folders
[LIST]
[*]*.png is a screenshot of the vBIOS in a vBIOS editor 
[*]*.txt is the report made using ATOMBIOSReader.exe 
[*]*.rom is the vBIOS on the GPU 
[*]**Please take note the cards power limit** 
[/LIST]
  
[*]amdGPUlog.sh
[LIST]
[*]This is the script i used to generate the amdgpu_*.log and pp_table_*.log files 
[*]pp_table_*.log is made by running the script as root otherwise it makes a amdgpu_*.log 
[*]when making a amdgpu_*.log press [Ctrl]+[C] to stop logging 
[/LIST]
  
[*]amdSensors.sh
[LIST]
[*]This is the script I made to manage and experiment with the files you get access to files that you can use to config how the GPU runs and monitor it and not need to remember where the files are 
[/LIST]
   
[/LIST]

Here is the data I collected
[https://www.mediafire.com/file/mocb9xvh78my4rq/Linux_Testing_Results.7z/filehttp://www.mediafire.com/file/mocb9xvh78my4rq/Linux_Testing_Results.7z/file](https://www.mediafire.com/file/mocb9xvh78my4rq/Linux_Testing_Results.7z/filehttp://www.mediafire.com/file/mocb9xvh78my4rq/Linux_Testing_Results.7z/file)
```
chad@X470GamingPlus:~/Desktop/Linux Testing Results$ tree ./
./
&#9500;&#9472;&#9472; amdGPUlog.sh
&#9500;&#9472;&#9472; amdSensors.sh
&#9492;&#9472;&#9472; data
    &#9500;&#9472;&#9472; Gigabyte_580
    &#9474;   &#9500;&#9472;&#9472; default
    &#9474;   &#9474;   &#9500;&#9472;&#9472; amdgpu_1586960620.log
    &#9474;   &#9474;   &#9500;&#9472;&#9472; amdgpu_1586960620.ods
    &#9474;   &#9474;   &#9500;&#9472;&#9472; pp_table_1586959691.log
    &#9474;   &#9474;   &#9500;&#9472;&#9472; pp_table_xubuntu_18.04.4.log
    &#9474;   &#9474;   &#9492;&#9472;&#9472; Superposition_Benchmark_v1.0_4800_1586960796.png
    &#9474;   &#9500;&#9472;&#9472; mild_undervolt
    &#9474;   &#9474;   &#9500;&#9472;&#9472; amdgpu_1586961447.log
    &#9474;   &#9474;   &#9500;&#9472;&#9472; amdgpu_1586961447.ods
    &#9474;   &#9474;   &#9500;&#9472;&#9472; pp_table_1586961774.log
    &#9474;   &#9474;   &#9492;&#9472;&#9472; Superposition_Benchmark_v1.0_4818_1586961623.png
    &#9474;   &#9500;&#9472;&#9472; undervolt
    &#9474;   &#9474;   &#9500;&#9472;&#9472; amdgpu_1586962184.log
    &#9474;   &#9474;   &#9500;&#9472;&#9472; amdgpu_1586962184.ods
    &#9474;   &#9474;   &#9500;&#9472;&#9472; pp_table_1586962146.log
    &#9474;   &#9474;   &#9492;&#9472;&#9472; Superposition_Benchmark_v1.0_4820_1586962360.png
    &#9474;   &#9492;&#9472;&#9472; vBIOS
    &#9474;       &#9500;&#9472;&#9472; Gigabyte.RX580.8192.170904_Patched.png
    &#9474;       &#9500;&#9472;&#9472; Gigabyte.RX580.8192.170904_Patched.rom
    &#9474;       &#9492;&#9472;&#9472; Gigabyte.RX580.8192.170904_Patched.txt
    &#9492;&#9472;&#9472; Sapphire_580
        &#9500;&#9472;&#9472; Factory_OC
        &#9474;   &#9500;&#9472;&#9472; amdgpu_1587000606.log
        &#9474;   &#9500;&#9472;&#9472; amdgpu_1587000606.ods
        &#9474;   &#9500;&#9472;&#9472; less_voltage
        &#9474;   &#9474;   &#9500;&#9472;&#9472; amdgpu_1587001270.log
        &#9474;   &#9474;   &#9500;&#9472;&#9472; amdgpu_1587001270.ods
        &#9474;   &#9474;   &#9500;&#9472;&#9472; pp_table_1587001077.log
        &#9474;   &#9474;   &#9492;&#9472;&#9472; Superposition_Benchmark_v1.0_4995_1587001446.png
        &#9474;   &#9500;&#9472;&#9472; pp_table_1587000467.log
        &#9474;   &#9500;&#9472;&#9472; pp_table_xubuntu_18.04.4.log
        &#9474;   &#9500;&#9472;&#9472; Superposition_Benchmark_v1.0_4978_1587000782.png
        &#9474;   &#9492;&#9472;&#9472; vBIOS
        &#9474;       &#9500;&#9472;&#9472; Sapphire.RX580.FactoryOC.png
        &#9474;       &#9500;&#9472;&#9472; Sapphire.RX580.FactoryOC.rom
        &#9474;       &#9492;&#9472;&#9472; Sapphire.RX580.FactoryOC.txt
        &#9492;&#9472;&#9472; Silent
            &#9500;&#9472;&#9472; amdgpu_1586999390.log
            &#9500;&#9472;&#9472; amdgpu_1586999390.ods
            &#9500;&#9472;&#9472; pp_table_1586999143.log
            &#9500;&#9472;&#9472; pp_table_xubuntu_18.04.4.log
            &#9500;&#9472;&#9472; Superposition_Benchmark_v1.0_4823_1586999566.png
            &#9492;&#9472;&#9472; vBIOS
                &#9500;&#9472;&#9472; Sapphire.RX580.Silent.png
                &#9500;&#9472;&#9472; Sapphire.RX580.Silent.rom
                &#9492;&#9472;&#9472; Sapphire.RX580.Silent.txt

12 directories, 38 files
```
Here is the data, I'll let some who knows more about how the driver works to decided what is working as intended and what is not and what needs to be tweaked

---

### Post by P-I H on 2020-04-16
My Radeon RX 580 works as expected.
```
p-i@pi-MS-7A34:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +33.1°C  (high = +70.0°C)
Tctl:         +33.1°C  


amdgpu-pci-2100
Adapter: PCI adapter
vddgfx:      725.00 mV 
fan1:        1148 RPM  (min =    0 RPM, max = 3500 RPM)
edge:         +29.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       30.02 W  (cap = 165.00 W)


p-i@pi-MS-7A34

```
System HW.
```
p-i@pi-MS-7A34:~$ inxi -Fz
System:    Kernel: 5.4.0-21-generic x86_64 bits: 64 Desktop: Gnome 3.36.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: <filter> UEFI: American Megatrends 
           v: 1.H0 date: 05/02/2018 
CPU:       Topology: Quad Core model: AMD Ryzen 3 1200 bits: 64 type: MCP L2 cache: 2048 KiB 
           Speed: 1376 MHz min/max: 1550/3600 MHz Core speeds (MHz): 1: 1378 2: 1378 3: 1378 4: 1377 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] driver: amdgpu 
           v: kernel 
           Display: x11 server: X.Org 1.20.8 driver: amdgpu resolution: 2560x1440~60Hz 
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 DRM 3.35.0 5.4.0-21-generic LLVM 9.0.1) v: 4.6 Mesa 20.0.4 
Audio:     Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
           Device-2: AMD Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590] driver: snd_hda_intel 
           Device-3: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.4.0-21-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp30s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 454.60 GiB used: 7.59 GiB (1.7%) 
           ID-1: /dev/sda vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
           ID-2: /dev/sdb vendor: Samsung model: SSD 830 Series size: 119.24 GiB 
           ID-3: /dev/sdc vendor: Kingston model: SV300S37A120G size: 111.79 GiB 
Partition: ID-1: / size: 109.04 GiB used: 7.54 GiB (6.9%) fs: ext4 dev: /dev/sdc2 
Sensors:   System Temperatures: cpu: 33.8 C mobo: N/A gpu: amdgpu temp: 29 C 
           Fan Speeds (RPM): N/A gpu: amdgpu fan: 1163 
Info:      Processes: 251 Uptime: 3h 17m Memory: 15.65 GiB used: 1.82 GiB (11.6%) Shell: bash inxi: 3.0.38 
p-i@pi-MS-7A34:~$
```

---

### Post by pqwoerituytrueiwoq on 2020-04-16
Which model of the 580?
if you run the amdGPUlog.sh script in my attachment as root it will read the voltage/clock table, that is what matters (a copy will be in the data folder)
* you will need to cd to the folder so it can use the amdSensors.sh script
if you are using sensors watch the vddgfx value what is it as the load increases, your reading was done at idle

---

### Post by P-I H on 2020-04-16
I have a MSI Radeon RX580  Gaming X.
I will test with the CIV VI Gathering Storm Graphic Benchmark and provide the vddgfx value.
I have to change computer, but I will edit this post with the result.

Took some time. Had to install Steam and download CIV VI.
Made some sensor readings during the benchmark
```
p-i@pi-MS-7A34:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +53.8°C  (high = +70.0°C)
Tctl:         +53.8°C  


amdgpu-pci-2100
Adapter: PCI adapter
vddgfx:      725.00 mV 
fan1:        1163 RPM  (min =    0 RPM, max = 3500 RPM)
edge:         +32.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       30.02 W  (cap = 165.00 W)


p-i@pi-MS-7A34:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +46.2°C  (high = +70.0°C)
Tctl:         +46.2°C  


amdgpu-pci-2100
Adapter: PCI adapter
vddgfx:        1.17 V  
fan1:        1300 RPM  (min =    0 RPM, max = 3500 RPM)
edge:         +41.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       75.09 W  (cap = 165.00 W)


p-i@pi-MS-7A34:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +47.6°C  (high = +70.0°C)
Tctl:         +47.6°C  


amdgpu-pci-2100
Adapter: PCI adapter
vddgfx:        1.17 V  
fan1:        1412 RPM  (min =    0 RPM, max = 3500 RPM)
edge:         +44.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       81.19 W  (cap = 165.00 W)


p-i@pi-MS-7A34:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +47.9°C  (high = +70.0°C)
Tctl:         +47.9°C  


amdgpu-pci-2100
Adapter: PCI adapter
vddgfx:        1.17 V  
fan1:        1384 RPM  (min =    0 RPM, max = 3500 RPM)
edge:         +46.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       88.17 W  (cap = 165.00 W)


p-i@pi-MS-7A34:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +48.1°C  (high = +70.0°C)
Tctl:         +48.1°C  


amdgpu-pci-2100
Adapter: PCI adapter
vddgfx:        1.17 V  
fan1:        1400 RPM  (min =    0 RPM, max = 3500 RPM)
edge:         +45.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       84.08 W  (cap = 165.00 W)


p-i@pi-MS-7A34:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +48.5°C  (high = +70.0°C)
Tctl:         +48.5°C  


amdgpu-pci-2100
Adapter: PCI adapter
vddgfx:        1.17 V  
fan1:        1428 RPM  (min =    0 RPM, max = 3500 RPM)
edge:         +46.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       79.21 W  (cap = 165.00 W)


p-i@pi-MS-7A34:~$
```

---

### Post by zika on 2020-04-17
[https://en.wikisource.org/wiki/Slavonic_Fairy_Tales/The_Emperor_Trojan%27s_Goat%27s_Ears](https://en.wikisource.org/wiki/Slavonic_Fairy_Tales/The_Emperor_Trojan%27s_Goat%27s_Ears)
If You do not make a proper bug report in a proper place all this is about Trojan's ears... ;)

---

