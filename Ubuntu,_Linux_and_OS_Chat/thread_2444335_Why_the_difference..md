---
title: "Why the difference."
date: 2020-05-28
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2020-05-28
Hello Ubuntu Forums,


I copy and paste these commands in terminal and get this. 

sudo dmidecode -t memory | grep -i size

sudo dmidecode -t memory | grep -i max

```


thomas@COMPAQ-SR5703WM:~$ sudo dmidecode -t memory | grep -i size
[sudo] password for thomas: 
        Maximum Memory Module Size: 1024 MB
        Maximum Total Memory Size: 2048 MB
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Size: 2048 MB
        Size: 2048 MB
thomas@COMPAQ-SR5703WM:~$ sudo dmidecode -t memory | grep -i max
        Maximum Memory Module Size: 1024 MB
        Maximum Total Memory Size: 2048 MB
        Maximum Capacity: 2 GB
thomas@COMPAQ-SR5703WM:~$ 


```

It does show 4.0 GB of memory although it displays this.

 Maximum Memory Module Size: 1024 MB
Maximum Total Memory Size: 2048 MB

Why the difference.



I copy and paste this command in root terminal and get this. 

inxi -zv7

Shows both installed modules correctly.

```


thomas@COMPAQ-SR5703WM:~$ sudo su
root@COMPAQ-SR5703WM:/home/thomas# inxi -zv7
System:    Kernel: 5.4.0-33-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: LXQt 0.14.1 
           info: lxqt-panel wm: Openbox 3.6.1 dm: SDDM Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop System: Compaq-Presario product: NC783AA-ABA SR5703WM v: N/A serial: <filter> 
           Chassis: Hewlett-Packard type: 3 serial: <filter> 
           Mobo: N/A model: IVY8 v: 2.00 serial: <filter> BIOS: Phoenix v: 5.16 date: 11/12/2008 

               
Memory:    RAM: total: 3.72 GiB used: 852.8 MiB (22.4%)                                                         
           Array-1: capacity: 4 GiB note: est. slots: 2 EC: None max module size: 2 GiB note: est.              
           Device-1: A0 size: 2 GiB info: double-bank speed: 667 MT/s type: DDR2 detail: none                   
           bus width: 64 bits total: 64 bits manufacturer: 7F98000000000000 part-no: N/A serial: <filter>       
           Device-2: A1 size: 2 GiB info: double-bank speed: 667 MT/s type: DDR2 detail: none                   
           bus width: 64 bits total: 64 bits manufacturer: 7F98000000000000 part-no: 2G-UDIMM                   
           serial: <filter> 

                                                                                    
CPU:       Topology: Dual Core model: AMD Athlon 64 X2 4800+ bits: 64 type: MCP arch: K8 rev.F+ rev: 2 
           L1 cache: 128 KiB L2 cache: 1024 KiB bogomips: 10046 
           Speed: 1000 MHz min/max: 1000/2500 MHz Core speeds (MHz): 1: 1000 2: 1000 
           Flags: 3dnow 3dnowext 3dnowprefetch apic clflush cmov cmp_legacy cpuid cr8_legacy cx16 cx8 de 
           extapic fpu fxsr fxsr_opt ht lahf_lm lbrv lm mca mce mmx mmxext msr mtrr nopl nx pae pat pge pni 
           pse pse36 rdtscp rep_good sep sse sse2 svm syscall tsc vme vmmcall 
Graphics:  Device-1: NVIDIA C61 [GeForce 6150SE nForce 430] vendor: Hewlett-Packard driver: nouveau 
           v: kernel bus ID: 00:0d.0 chip ID: 10de:03d0 
           Display: server: X.Org 1.20.8 driver: nouveau unloaded: fbdev,modesetting,vesa 
           resolution: 1152x720~60Hz 
           OpenGL: renderer: NV4C v: 2.1 Mesa 20.0.4 direct render: Yes 
Audio:     Device-1: NVIDIA MCP61 High Definition Audio vendor: Hewlett-Packard driver: snd_hda_intel 
           v: kernel bus ID: 00:05.0 chip ID: 10de:03f0 
           Sound Server: ALSA v: k5.4.0-33-generic 
Network:   Device-1: NVIDIA MCP61 Ethernet vendor: Hewlett-Packard type: network bridge driver: forcedeth 
           v: kernel port: fb00 bus ID: 00:07.0 chip ID: 10de:03ef 
           IF: enp0s7 state: up speed: 100 Mbps duplex: full mac: <filter> 
           IP v4: <filter> type: dynamic noprefixroute scope: global broadcast: <filter> 
           IP v6: <filter> type: dynamic noprefixroute scope: global 
           IP v6: <filter> type: temporary dynamic scope: global 
           IP v6: <filter> type: dynamic mngtmpaddr noprefixroute scope: global 
           IP v6: <filter> type: noprefixroute scope: link 
           WAN IP: No WAN IP data found. Connected to the web? SSL issues? 
Drives:    Local Storage: total: 76.34 GiB used: 7.28 GiB (9.5%) 
           ID-1: /dev/sda vendor: Maxtor model: 6Y080L0 size: 76.34 GiB speed: <unknown> serial: <filter> 
           rev: 1BW0 temp: 40 C scheme: MBR 
           Optical-1: /dev/sr0 vendor: _NEC model: DVD+RW ND-2100AD rev: 103D dev-links: cdrom,cdrw,dvd 
           Features: speed: 40 multisession: yes audio: yes dvd: yes rw: cd-r,cd-rw state: running 
RAID:      Message: No RAID data was found. 
Partition: ID-1: / size: 74.63 GiB used: 7.28 GiB (9.8%) fs: ext4 dev: /dev/sda1 label: N/A 
           uuid: c3e713cd-add8-47b9-be36-9d411378ac58 
Unmounted: Message: No unmounted partitions found. 
USB:       Hub: 1-0:1 info: Full speed (or root) Hub ports: 8 rev: 2.0 speed: 480 Mb/s chip ID: 1d6b:0002 
           Hub: 2-0:1 info: Full speed (or root) Hub ports: 8 rev: 1.1 speed: 12 Mb/s chip ID: 1d6b:0001 
           Device-1: 2-3:2 info: Primax Dell N889 Optical Mouse type: Mouse driver: hid-generic,usbhid 
           interfaces: 1 rev: 2.0 speed: 1.5 Mb/s chip ID: 0461:4d81 
           Device-2: 2-4:3 info: Dell Keyboard type: Keyboard driver: hid-generic,usbhid interfaces: 1 
           rev: 1.1 speed: 1.5 Mb/s chip ID: 413c:2003 
Sensors:   System Temperatures: cpu: 36.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 150 Uptime: 10h 22m Init: systemd v: 245 runlevel: 5 Compilers: gcc: 9.3.0 alt: 9 
           Shell: bash (sudo) v: 5.0.16 running in: qterminal inxi: 3.0.38 



```


I'm curious.

Computer was put together from spare parts.


Thanks.

---

### Post by TheFu on 2020-05-29
There are multiple memory slots on most motherboards.  A system with 2x1GB RAM will have a total of 2GB RAM.  But usually on those sorts of systems, some of the RAM gets taken for use by an iGPU, so the reported RAM could be less than 2GB.

For example:
```
$ sudo dmidecode -t memory | grep -i size
        Size: 8192 MB
        Size: 8192 MB
        Size: 8192 MB
        Size: 8192 MB
```
Shows the machine has 4 RAM slots with 8GB in each. The total is 32GB in that machine.
Another machine (a virtual machine), show:
```
$ sudo dmidecode -t memory | grep -i size
        Size: 2048 MB
```
That VM is only allocated 2G and the hypervisor shows that RAM as a single slot.
A different machine:
```
$ sudo dmidecode -t memory | grep -i size
        Size: 8192 MB
        Size: No Module Installed
        Size: No Module Installed
        Size: No Module Installed
```
One 8GB RAM stick installed. There's room for more.

The "Maximum Capacity:" is probably reported by the BIOS as the most possible RAM a system can hold.  I'm seeing these results:
```
$ sudo dmidecode -t memory | grep -i max
        Maximum Capacity: 128 GB
        Maximum Voltage: 1.2 V
        Maximum Voltage: 1.2 V
        Maximum Voltage: 1.2 V
        Maximum Voltage: 1.2 V
```
That machine has 32G and can hold up to 128G of RAM. That is true.

```
$ sudo dmidecode -t memory | grep -i max
        Maximum Capacity: 32 GB
```
That machine has 8G and can hold up to 32G of RAM. That is true.

```
$ sudo dmidecode -t memory | grep -i max
        Maximum Memory Module Size: 4096 MB
        Maximum Total Memory Size: 16384 MB
        **Maximum Capacity: 4 GB**
```
That machine has 16G and can hold up to 16G of RAM. The Capacity line is incorrect.

BTW, most of my systems are running 16.04.  One has 14.04 ESM and one is a 20.04 VM.

Really, I just use: 
```
more /proc/meminfo
```
to see the RAM that the OS sees. No programs need be installed and this is actually what the OS sees and can use.

If you are looking to see whether adding more RAM to a 2GB system makes sense, in general, only of that RAM is free would it be.  I wouldn't spend any upgrade money on an old system that has just 2GB of RAM, except for an SSD storage device, perhaps.

---

### Post by poorguy on 2020-05-29
Hello TheFu,

Sounds as though the bios may be showing the maximum allowable ram the computer was built for if I'm understanding what you're say correctly.

Originally this computer came with Vista Basic 32 bit going by the COA tag.

Anyway it's working good and being it's 12 years old and probably best to leave it as it is.


Thanks for your reply. :)

---

