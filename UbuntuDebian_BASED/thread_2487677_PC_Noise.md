---
title: "PC Noise"
date: 2023-06-12
forum: Ubuntu/Debian BASED
---

### Post by kmukomela00 on 2023-06-12
PC makes noise after installing Ubuntu

---

### Post by Autodave on 2023-06-12
What kind of noise: from within the unit, through the speakers, ???  Is this a desktop or laptop?

---

### Post by kmukomela00 on 2023-06-13
Noisy desktop cooling system

---

### Post by TheFu on 2023-06-13
> **kmukomela00 said:**
> Noisy desktop cooling system

Did you monitor the heat?
Is the system overclocked?  Mine run at 7% OC.
Did you set the fans to "quiet mode" in the BIOS?
Did you try using better quality, quieter, fans?  They are relatively cheap and can make a huge difference.  I've been happy with Noctua fans.

You know, an overview of the hardware would really help, since different motherboards, CPUs, and other internal components can have specific cooling and performance needs.

**inxi -bz** is a useful command to get system overview data.

---

### Post by kmukomela00 on 2023-06-13
There is no such noise on windows.
Motherboard Asus H110M-K
Processor intel core i3 7100
Video card Gtx 1050

---

### Post by TheFu on 2023-06-13
So, will you be running the requested command and posting the output or not?
If not, please let me know.

---

### Post by kmukomela00 on 2023-06-14
System:
  Kernel: 6.2.6-76060206-generic x86_64 bits: 64 Desktop: GNOME 42.5
    Distro: Pop!_OS 22.04 LTS
Machine:
  Type: Desktop Mobo: ASUSTeK model: H110M-K v: Rev X.0x
    serial: <superuser required> UEFI: American Megatrends v: 4211
    date: 02/04/2021
CPU:
  Info: dual core Intel Core i3-7100 [MT MCP] speed (MHz): avg: 3125
    min/max: 800/3900
Graphics:
  Device-1: NVIDIA GP107 [GeForce GTX 1050] driver: nvidia v: 525.105.17
  Device-2: KYE Systems (Mouse Systems) FaceCam 1020 type: USB
    driver: snd-usb-audio,uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,nouveau,vesa gpu: nvidia
    resolution: 1920x1080~60Hz
  OpenGL: renderer: NVIDIA GeForce GTX 1050/PCIe/SSE2
    v: 4.6.0 NVIDIA 525.105.17
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
Drives:
  Local Storage: total: 931.51 GiB used: 27.37 GiB (2.9%)
Info:
  Processes: 233 Uptime: 1m Memory: 7.69 GiB used: 2.15 GiB (27.9%)
  Shell: Bash inxi: 3.3.13

---

### Post by TheFu on 2023-06-14
We can assume the correct drivers,for now.  Looks like it is just settings.  

Drivers in Linux sometimes aren't as full featured as for MS-Windows.  That's the vendor's management choice.  Complain to them and consider taking your money to a competitor if they do better with Linux support. Our money talks.

I'll have to shotgun some ideas for your consideration: 
[LIST]
[*]Go into the BIOS and set the fans to "Quiet Profile", if it exists.  
[*]Run the nvidia driver software GUI and see if there's any fan controls inside it.
[*]Clean the outside and inside of the case removing all dust and other junk.
[*]Cables all over the place can slow or block airflow to some components. Get internal cable management under control, so air movement inside the case flows front to back wherever the PSU is.  If the PSU is at the back-top, ensure there's clear airflow from the front-bottom.  If the PSU is at the back-bottom, ensure there's clear airflow from the front-top. This can't hurt.
[*]Consider getting a case fan to pull air in from the front if any of the temperatures for internal components are high.  I have an extra fan pulling air over my 4 internal drives on 1 system.  The fan included with the drive cage started making noise as it was dying.  Replaced that fan with a Noctua fan of the same size and the motherboard saw it and incorporated it into the cooling options as a "case fan2".
[/LIST]

Use **psensors** and **sensors** to see which component temperatures are on the high side. Each has an expected operating range. Ideally, they'd be in the high-30s°C.  Normally, I see low to mid-40s°C:
```
Adapter: PCI adapter
Tctl:         +45.4°C  

nvme-pci-0800
Adapter: PCI adapter
Composite:    +40.9°C  (low  = -273.1°C, high = +81.8°C)
                       (crit = +84.8°C)
Sensor 1:     +40.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +44.9°C  (low  = -273.1°C, high = +65261.8°C)

amdgpu-pci-0900
Adapter: PCI adapter
vddgfx:        1.29 V  
vddnb:       993.00 mV 
edge:         +40.0°C  

```
My HDDs tend to be around 40°C too - some high 30s.  A Samsung NVMe SSD is running at: 55 Celsius. That's the hottest thing in any of my systems now. It doesn't have a heatsink.  I need to spend the $5.

I've never used any specific OS tools that deal with dynamic fan speeds.  My motherboards have those built in, but if cooling is an issue for a component, it could be hotter, so getting overall system cooling working better helps.  Lots of us have SSDs that run hot.  Many need an extra heatsink to get the heat away from the SSD and into the case, but if the case doesn't have airflow (just enough, not huge fans on full), then the 

Lastly, I'd look at the PSU and consider getting a quiet brand with Bronze or higher efficiency.  I've been using Seasonic for over a decade ... there was a great deal, so I bought 3 of them before I needed any. Seasonic has quieter cooling.

If you can figure out exactly which fan is making the noise, perhaps changing that one out would be the easiest?

Lastly, I had a boss who was all about "Data and Facts".  So, when it comes to noise, that means measuring the difference.  If you have a smartphone, there are dB meter applications.  Just be consistent when measuring.  Place everything the same and let the app record the noise.  May want to turn off other items in the room - perhaps an external HDD or other things with fans.
Gather the data so you can compare it with the "fix" to know something better happened ... or if the efforts made it worse.   Try at boot, 10 minutes without any workload and under full loading.  We want to use facts in our decisions.

There are lots of other ideas for people who really want a quite system. Plenty of "quiet" equipment sold.

I really hope it is just a BIOS setting that fixes it. That would be nice.

---

### Post by coffeecat on 2023-06-14
Pop!_OS. * Thread moved to **Ubuntu/Debian BASED** sub-forum.*

---

