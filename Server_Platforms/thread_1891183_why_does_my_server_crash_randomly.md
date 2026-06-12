---
title: "why does my server crash randomly?"
date: 2011-12-05
forum: Server Platforms
---

### Post by yavuz.maslak on 2011-12-05
Hello

I use ubuntu11.10 server 64bit. apache22, php5, apc3.1.7 work on it. it works. But the server crashes every week randomly.
when I look at the monitor, the server was frozen. the monitor doesn't display anything. So I have to reboot on the button.  
as far as I can see, there is not any log in /var/log/... about that.
whats wrong with it ?

---

### Post by gradinaruvasile on 2011-12-05
> **yavuz.maslak said:**
> Hello

I use ubuntu11.10 server 64bit. apache22, php5, apc3.1.7 work on it. it works. But the server crashes every week randomly.
when I look at the monitor, the server was frozen. the monitor doesn't display anything. So I have to reboot on the button.  
as far as I can see, there is not any log in /var/log/... about that.
whats wrong with it ?

This post surely wont help. Ubuntu or any Linux distro does not have any generic bugs that lead to system freezes.
Your issue is localized (probably specific software configuration or hardware/driver issue) so you have to give more information such as server model, attached peripherals, lspci output etc. 
Another thing is to try to monitor the CPU/mobo temperatures.

BTW if you plan to use for production, i suggest using the long support releases for servers.

---

### Post by Xianath on 2011-12-05
Actually I wouldn't be so quick to dismiss the possibility of a bug causing a crash. If you check out the kernel revision history, there are a few of those fixed with every version. My brother's server, for example, was crashing due to the r8169 driver having replaced the r8168 one, and he has to make do with a manually built r8168 at least until Ubuntu makes it to kernel 3.1 where the 8111e is supported by r8169. Trust me, after almost two decades with Linux, I can assure you that "Linux doesn't crash" is about as much as an urban myth as "Linux doesn't need defragmentation" or even "Linux is cheaper than Windows".

Back on your question, without any error messages you're pretty much stuck right now. In order to get some logging info, you can try to connect a serial cable to another computer (if you have a laptop, a USB-RS232 adaptor works well, these are cheap) and enable the serial console on Ubuntu ([https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)). Run a terminal program on the other computer like minicom on Linux or putty on Windows and redirect output to file. When Ubuntu crashes, chances are it will spill out some info on the console. Post that, and we'll take it from there. If you're lucky, it will be something already known that either requires a kernel upgrade, a module upgrade or worst case, a hardware swap. If not, at least you'll have enough credible info to report a bug.

HTH,
Peter

---

### Post by yavuz.maslak on 2011-12-05
Here's some values;

root@www:~# sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +0.92 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:       +3.25 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.05 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +11.97 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      2343 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:    0 RPM  (min =  600 RPM)
POWER FAN Speed:       0 RPM  (min =    0 RPM)
CPU Temperature:     +40.0Â°C  (high = +60.0Â°C, crit = +75.0Â°C)
MB Temperature:      +41.0Â°C  (high = +45.0Â°C, crit = +75.0Â°C)

root@www:~# hddtemp /dev/sdb
/dev/sdb: ST31500341AS: 50°C

root@www:~# hddtemp /dev/sda
/dev/sda: ST31500341AS: 51°C

#lspci 
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
04:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
04:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)

---

### Post by Lars Noodén on 2011-12-05
Look in [font=Courier New]/var/log/syslog[/font] at the times of the crashes for possible clues.

---

### Post by yavuz.maslak on 2011-12-05
I went through syslog. there is not any error but only crontab error because of I had added a script into /etc/crontab but I hadn't added regarding the file. I have just removed from crontab.


How can I see all errors related to the server in syslog ?

---

### Post by yavuz.maslak on 2011-12-05
the server hasn't got com port.
is  there any easier way in order to see all errors related to the server?

---

### Post by Lars Noodén on 2011-12-05
> **yavuz.maslak said:**
> I went through syslog. there is not any error but only crontab error because of I had added a script into /etc/crontab but I hadn't added regarding the file. I have just removed from crontab.


How can I see all errors related to the server in syslog ?

The errors *should* be getting logged to [font=Courier New]/var/log/syslog[/font].  Maybe try looking in [font=Courier New]/var/log/kern.log[/font], too, in case it is kernel related.  

Is there any way you can find out what makes it crash and do it on purpose?

---

### Post by SeijiSensei on 2011-12-05
I suggest running a memory test.  Random crashes and lockups often are a symptom of bad memory.

---

### Post by yavuz.maslak on 2011-12-05
can I run memtest while the server is running ? 

if i can, How can I do that ?

Thanks

---

### Post by gradinaruvasile on 2011-12-05
> **Xianath said:**
> Actually I wouldn't be so quick to dismiss the possibility of a bug causing a crash. If you check out the kernel revision history, there are a few of those fixed with every version. My brother's server, for example, was crashing due to the r8169 driver having replaced the r8168 one, and he has to make do with a manually built r8168 at least until Ubuntu makes it to kernel 3.1 where the 8111e is supported by r8169. Trust me, after almost two decades with Linux, I can assure you that "Linux doesn't crash" is about as much as an urban myth as "Linux doesn't need defragmentation" or even "Linux is cheaper than Windows".


Read carefully. I said that it is probably some localized issue tied to particular driver/software configs. You describe exactly what i said. Not every Linux computer/server uses the r816x drivers you know.

There is NO Linux bug that affects ALL computers making them freeze (as it can be understood by the OPs question - "My system is Ubuntu x and its crashing. Tell me why.").

PS Given the same expertise of net admins, Linux IS cheaper than Windows.We had 9 servers and 7 of them were running Linux (2 run Windows only because they had a production program running that was based on .NET and MSSQL) and we had exactly 0 issues. But we had very good admins.

---

### Post by SeijiSensei on 2011-12-06
> **yavuz.maslak said:**
> can I run memtest while the server is running ?

No, you'll need to take the server offline.  memtest just writes random data to the memory; you can't do that and run the server at the same time.

---

### Post by yavuz.maslak on 2011-12-07
Meanwhile, the server froze again so I have to manual restart by the button.

I saw some fail errors in boot.log as below;

initctl: Event failed
 * Starting load fallback graphics devices fail
 * Starting automatic crash report generation fail
there is no fail but above errors.
Also hddtemp is 49 celcius  is that normal ? I use sata2 disk
/dev/sda: ST31500341AS: 49Â°C

My graphic card;
# lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: nVidia Corporation G98 [GeForce 8400 GS] [10de:06e4] (rev a1)


#sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +41.0Â°C  (high = +80.0Â°C, crit = +100.0Â°C)
Core 1:       +38.0Â°C  (high = +80.0Â°C, crit = +100.0Â°C)
Core 2:       +42.0Â°C  (high = +80.0Â°C, crit = +100.0Â°C)
Core 3:       +40.0Â°C  (high = +80.0Â°C, crit = +100.0Â°C)

w83667hg-isa-0290
Adapter: ISA adapter
Vcore:        +0.92 V  (min =  +0.00 V, max =  +1.74 V)
in1:          +1.70 V  (min =  +1.38 V, max =  +0.00 V)  ALARM
AVCC:         +3.28 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:        +3.25 V  (min =  +2.98 V, max =  +3.63 V)
in4:          +1.68 V  (min =  +0.51 V, max =  +0.07 V)  ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.64 V)  ALARM
3VSB:         +3.36 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:         +3.26 V  (min =  +2.70 V, max =  +3.30 V)
fan1:           0 RPM  (min = 21093 RPM, div = 64)  ALARM
fan2:        2220 RPM  (min =  860 RPM, div = 16)
fan3:           0 RPM  (min = 21093 RPM, div = 64)  ALARM
fan4:           0 RPM  (min = 21093 RPM, div = 64)  ALARM
fan5:           0 RPM  (min =    0 RPM, div = 128)  ALARM
temp1:        +39.0Â°C  (high = +50.0Â°C, hyst = +162.0Â°C)  sensor = thermistor
temp2:        +41.0Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)  sensor = diode
temp3:        +34.5Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)  sensor = thermistor
cpu0_vid:    +2.050 V

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +0.92 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:       +3.25 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.05 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +11.97 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      2220 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:    0 RPM  (min =  600 RPM)
POWER FAN Speed:       0 RPM  (min =    0 RPM)
CPU Temperature:     +41.0Â°C  (high = +60.0Â°C, crit = +75.0Â°C)
MB Temperature:      +39.0Â°C  (high = +45.0Â°C, crit = +75.0Â°C)

---

### Post by cariboo on 2011-12-08
The only time I've had a server lock up, is due to hardware errors. If memtest doesn't show any errors, I'd suggest you check the SMART data of the hard drives. You can now do this remotely from another computer running Ubuntu using the disk utility applet. Once the application has started, go to File->Connect to Server, enter the ip address and user name, you will be prompted for a password before the connection is made.

As you can see, in the screenshot, I have a drive that has a problem, it hasn't failed completely yet, but it will soon. I have a complete backup already, as the data on that drive never changes. I have a new drive on the way.

---

### Post by yavuz.maslak on 2011-12-08
I forgot a thing. when the server was frozen, the display wasn't show anything it gots to black screen. Namely the blank screen, power is on, the disk in on because its led is red, network is down I can't ping it. 
the server goes to freeze everyweek randomly and when I looked at the monitor, the screen had turned to black.    
I didn't gnome, kde, kubuntu or other xwindows.
 lshw -C display
  *-display               
       description: VGA compatible controller
       product: G98 [GeForce 8400 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:bc00(size=128) memory:fbbe0000-fbbfffff

---

### Post by Xianath on 2011-12-08
I'll reiterate my advice to use a serial console to collect crash info for the very simple reason that if the crash is in one of the storage subsystems or filesystems (XFS in my case), that info will never make it to disk. 

There's no such thing as a server with no serial port :) There is either a DB9 one on the back panel, an RJ45 one, or a COM header on the motherboard itself. Your motherboard looks like an Asus PQ5 series which all have on-board COM port headers.

---

### Post by yavuz.maslak on 2011-12-08
My motherboard is ASUS P6T SE
is there an eaiser way such as crash report instead of com port?
How can I connect on mother board and watch with hyper terminal or similiar tool ? 
Could you explain  ?

---

### Post by yavuz.maslak on 2011-12-08
How can I execute the commands what you said because of I didn't install xwindows ?

---

### Post by yavuz.maslak on 2011-12-08
I found 2 errors in /var/log/kern.log during the reboot;

May the problem be related to these fails ?

Dec  5 09:08:51 www kernel: [    0.588667]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec  5 09:08:51 www kernel: [   71.091654] init: failsafe main process (1142) killed by TERM signal
Dec  7 21:45:22 www kernel: [    0.588667]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec  7 21:45:25 www kernel: [   97.746022] init: failsafe main process (1035) killed by TERM signal

---

### Post by Xianath on 2011-12-11
Well, to connect via Hyper Terminal or Putty (my preference) you will need a serial connection, i.e. a serial port. You *might* be able to get a copy of the virtual console via ssh, like so:

sudo tail -f /dev/vcs* | tee console.log

Depending on when the server crashes though, it might not be able to capture all information. Worth a try though, especially since your crashes seem to be quite predictable.

---

### Post by yavuz.maslak on 2011-12-15
Ok I 'll go through via serial cable.

Meanwhile, I saw disk(49 celcius) and motherboard's ( 41 celcius) temp . I fixed the cooler Now. the disk 44 and motherboard 36.
Also I saw "Starting load fallback graphics devices[fail]" and 
unity-greeter[20557]: segfault at 0 ip 00007fc6e3fc0b70 sp 00007fff4a96a048 error
in boot.log. I reinstalled the vga card. I performed the link "http://ubuntuforums.org/showthread.php?t=1860240" for other error.

the server has been working for 8 days.
I am not sure that is my did above. but it is good for now.
what do you consider about that ?

---

