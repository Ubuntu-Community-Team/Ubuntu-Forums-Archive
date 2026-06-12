---
title: "Server freezes without error logs"
date: 2021-05-23
forum: Server Platforms
---

### Post by morris_horesh on 2021-05-23
Hi all,

I am running ubuntu server with kernel [COLOR=#000000][FONT=Calibri]4.15.0-142-generic on a HP Elite 800 G4. There are 10 USB Bluetooth dongles connected via a HUB and I am running software that connects to Bluetooth devices. Every once in a while the server freezes, there is no output on the screen, no response to the keyboard and no network connectivity. When the server is restarted, journalctl -b -1 does not show anything out of the ordinary other than the logs just stopping. I would suspect the hardware but there is another server that behaves exactly the same. This only started to happen once I installed a clean OS. I have used different kernel versions including 5.xx. I ran a script that logs the temperature and memory consumption every minute and there was nothing out of the ordinary when the logs stopped.

Help will be much appreciated.
[/FONT][/COLOR]

---

### Post by mIk3_08 on 2021-05-23
There are a lot of possible causes of this freeze 
Is the machine new? If the machine is not new maybe the dusty machine can cause it to freeze due to the heat sink can't performed well during the 
processors turns very hot due to the dusty build ups from the heat sink.
If the machine is new then other says that if "Kernel hangs" are very difficult to debug as no message is displayed on screen as in case of crash.
And if you are really lucky you will see something inside
/var/log/messages 
as during hang your entire system hangs along with syslog daemon and nothing will be write inside these files.

---

### Post by morris_horesh on 2021-05-23
Thanks for the reply. It is probably not a temperature issue. The sensors did not indicate any abnormal temperature and the issue began right after re-installation of the OS.

---

### Post by mIk3_08 on 2021-05-23
Did you try to check your memory
check dmidecode
```
sudo dmidecode --type memory 
```
and also try to check running applications
This is some basic on checking Linux server or 
this maybe some compatibility issue to your hardware. 
hardware compatibility is a rare issue it might be
to your machine running applications.
```
sudo ps -ef | grep apache2
```
```
sudo netstat -plunt | grep apache2
```

---

### Post by morris_horesh on 2021-05-24
Apache is not running and there doesn't seem to be anything out of the ordinary with the memory:

```

Getting SMBIOS data from sysfs.
SMBIOS 3.1 present.

Handle 0x0007, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0039, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x0007
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM1
    Bank Locator: ChannelB
    Type: DDR4
    Type Detail: Synchronous
    Speed: 2667 MT/s
    Manufacturer: Micron
    Serial Number: 1F4F8C01
    Asset Tag:  
    Part Number: 4ATF51264HZ-2G6E1   
    Rank: 1
    Configured Clock Speed: 2667 MT/s
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: 1.2 V

Handle 0x000A, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x0007
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: Other
    Set: None
    Locator: DIMM3
    Bank Locator: ChannelA
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Rank: Unknown
    Configured Clock Speed: Unknown
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: Unknown



```

---

