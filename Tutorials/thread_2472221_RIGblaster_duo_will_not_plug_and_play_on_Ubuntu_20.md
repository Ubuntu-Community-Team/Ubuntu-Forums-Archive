---
title: "RIGblaster duo will not plug and play on Ubuntu 20.04.3 LTS"
date: 2022-02-21
forum: Tutorials
---

### Post by wx9m on 2022-02-21
[SIZE=5]**RIGblaster duo will not plug and play on Ubuntu 20.04.3 LTS**[/SIZE]

 
 **Environment:**
 
 Laptop – Juno Nyx 15” AMD v2, 16GB memory, 512GB SSD
 Operating System - Ubuntu 20.04.3 LTS
Software - WSJT-X v2.5.4
 Hardware - RIGblaster duo  
 
 
 **Setup:**
 
 Using a RIGblaster duo connected to a YAESU FT-100D and Kenwood TS-690S with receive audio going into the RIGblaster then out to mic input of a USB soundcard adapter plugged into the Laptop. RIGblaster USB cord is going to the Laptop for PTT control only. I am not using full rig control to the radios.
 
 
 **Background:**

 The setup was working fine for years with a older laptop running Windows 10. That laptop became so slow it was unbearable. So I opted to go with a new laptop running Linux preinstalled by Juno Computers. Hardware that Ubuntu just found and made work upon plugging in: Canon wireless printer, Logitech wireless mouse, HDMI port to 2[SUP]nd[/SUP] display, and a USB sound card interface – all good!  
 
 
 **Problem:**
 
 The RIGblaster duo was also “found” when plugging in the USB cable to the laptop. It can “hear” received audio from the radios via the USB Soundcard interface mic input. [FONT=Liberation Serif]WSJT-X needs to have a serial com port configured to allow the PTT function over the USB port [/FONT][FONT=Liberation Serif]to the [/FONT][FONT=Liberation Serif]RIGblaster duo [/FONT][FONT=Liberation Serif]so it can then control PTT through the radios mic input[/FONT][FONT=Liberation Serif]. [/FONT] 
 
 I was able to see the RIGblaster duo connected to USB:
 ```

 [FONT=Ubuntu Mono]$ lsusb[/FONT]
 [FONT=Ubuntu Mono]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
 [FONT=Ubuntu Mono]Bus 003 Device 003: ID 5986:9102 Acer, Inc BisonCam,NB Pro[/FONT]
 [FONT=Ubuntu Mono]Bus 003 Device 002: ID 8087:0029 Intel Corp. [/FONT] 
 [FONT=Ubuntu Mono]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
 [FONT=Ubuntu Mono]Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
 [FONT=Ubuntu Mono]Bus 001 Device 003: ID 0c76:120b JMTek, LLC. Plugable USB Audio Device[/FONT]
 [FONT=Ubuntu Mono]Bus 001 Device 002: ID 0403:b338 Future Technology Devices International, Ltd RIGblaster Duo[/FONT]
 [FONT=Ubuntu Mono]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
 
```
 
 Now I attempt to look for com ports associated to this USB, but this is all I see: 
```

[FONT=Ubuntu Mono]$ dmesg | grep tty[/FONT]

 [FONT=Ubuntu Mono][    0.097886] printk: console [tty0] enabled[/FONT]
 
```
 
 Maybe the FTDI driver is not installed? So I issue the following commands and it does find it:
```

 [FONT=Ubuntu Mono]$ dmesg | grep -i ftdi
[10141.816157] usbcore: registered new interface driver ftdi_sio
[10141.816167] usbserial: USB Serial support registered for FTDI USB Serial Device
[/FONT]
```
 
 [FONT=Liberation Serif]Check if [/FONT][FONT=Liberation Serif]the FTDI driver [/FONT][FONT=Liberation Serif]is [/FONT][FONT=Liberation Serif] pre-compiled as dynamically-loadable kernel modules. [/FONT]
You should see an [FONT=Ubuntu Mono]ftdi_sio [/FONT](Serial I/O) module (and we do) [FONT=Liberation Serif]with the command:[/FONT]
```

 [FONT=Ubuntu Mono]$ find /lib/modules | grep -i ftdi
/lib/modules/5.14.0-1011-oem/kernel/drivers/usb/misc/ftdi-elan.ko
/lib/modules/5.14.0-1011-oem/kernel/drivers/usb/serial/ftdi_sio.ko
/lib/modules/5.13.0-27-generic/kernel/drivers/usb/misc/ftdi-elan.ko
/lib/modules/5.13.0-27-generic/kernel/drivers/usb/serial/ftdi_sio.ko
/lib/modules/5.14.0-1020-oem/kernel/drivers/usb/misc/ftdi-elan.ko
/lib/modules/5.14.0-1020-oem/kernel/drivers/usb/serial/ftdi_sio.ko
[/FONT]
```
 
 [FONT=Liberation Serif]Check to see if the FTDI module has been dynamically loaded into the running kernel (and it is), by using the command:[/FONT]
```

[FONT=Ubuntu Mono]$ lsmod | grep -i ftdi
ftdi_sio 61440 0
usbserial 57344 1 ftdi_sio[/FONT]
 
```
 
 [FONT=Liberation Serif]With all that in place, the FTDI driver should have created a tty device. Checking with the following command we do not see one:[/FONT]
```

[FONT=Ubuntu Mono]$ ls -l /dev/ttyUSB*[/FONT]

 [FONT=Ubuntu Mono]ls: cannot access '/dev/ttyUSB*': No such file or directory[/FONT]
 
```
 
 
 [FONT=Liberation Serif]**Root Cause:**[/FONT]

 [SIZE=2][FONT=Liberation Serif]At this point I reached out for help from Tech Support at West Mountain Radio, the manufacturer of the RIGblaster duo. Here was their response:[/FONT]

 “[FONT=Liberation Serif]My best guess is that the RIGblaster hardware id isn't listed in the current ftdi driver.”[/FONT]

 [FONT=Liberation Serif]Looking at the source code for the current ftdi linux driver, specifically the file ftdi_sio_ids.h (see[/FONT] [[FONT=Liberation Serif]https://github.com/torvalds/linux/blob/master/drivers/usb/serial/ftdi_sio_ids.h[/FONT]]("https://github.com/torvalds/linux/blob/master/drivers/usb/serial/ftdi_sio_ids.h")[FONT=Liberation Serif]) [/FONT][FONT=Liberation Serif]It has no definition for a product_id pid=0xb338, so that is surely the cause of [/FONT][FONT=Liberation Serif]the[/FONT][FONT=Liberation Serif] problem, i.e. the USB product_id for the RigBlaster Duo is not known to the built-in ftdi serial-I/O driver in Linux. [/FONT] 
[/SIZE]
 
 [FONT=Liberation Serif][SIZE=3]**Solution:**[/SIZE][/FONT]

 [SIZE=2][FONT=Liberation Serif]Now knowing what the actual cause of the problem is, an internet search produced the following forum post:[/FONT]
 [[FONT=Liberation Serif]https://unix.stackexchange.com/questions/67936/attaching-usb-serial-device-with-custom-pid-to-ttyusb0-on-embedded[/FONT]]("https://unix.stackexchange.com/questions/67936/attaching-usb-serial-device-with-custom-pid-to-ttyusb0-on-embedded")

 [FONT=Liberation Serif]Their solution to dynamically add the product_id to the running kernel worked! Here is the sequence:[/FONT]

 [FONT=Liberation Serif]1) Unplug the device[/FONT]
[FONT=Liberation Serif]2) issue commands:[/FONT][/SIZE]
[SIZE=2][FONT=Liberation Serif]```
[FONT=Ubuntu Mono]$ modprobe ftdi_sio[/FONT]
[FONT=Ubuntu Mono]$ [/FONT][FONT=Ubuntu Mono]echo 0403 b338 >/sys/bus/usb-serial/drivers/ftdi_sio/new_id[/FONT]

```
4) Plug in the device[/FONT]
[/SIZE]
 [SIZE=2][FONT=Liberation Serif]Farther down in that same forum post is a way to make it happen automatically at boot time which also worked:[/FONT]

 [FONT=Liberation Serif]Add the following single line to [FONT=Ubuntu Mono]/etc/udev/rules.d/99-ftdi.rules[/FONT]
```

[FONT=Ubuntu Mono]ACTION=="add", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="b338", RUN+="/sbin/modprobe ftdi_sio" RUN+="/bin/sh -c 'echo 0403 b338 > /sys/bus/usb-serial/drivers/ftdi_sio/new_id'"[/FONT]
```[/FONT][/SIZE]

 [FONT=Liberation Serif]If the file does not exist, create a empty file with this command:[/FONT]
 ```
 
[FONT=Ubuntu Mono]$sudo touch /etc/udev/rules.d/99-ftdi.rules[/FONT]

```
 
 [FONT=Liberation Serif]Once the file exists, you can edit it with the following command:[/FONT]
```

$ [FONT=Ubuntu Mono]gedit admin:///etc/udev/rules.d/99-ftdi.rules[/FONT]

```

 [FONT=Liberation Serif]**Note: **It would be best to cut and paste the above into the file to avoid a typo. Additionally, if your device is not the RIGblaster duo, you will need to substitute the values of [FONT=Ubuntu Mono]0403[/FONT] and [FONT=Ubuntu Mono]b338[/FONT] as found with issuing the command previously listed above ([FONT=Ubuntu Mono]$[/FONT][FONT=Ubuntu Mono]lsusb[/FONT][FONT=Ubuntu Mono])[/FONT][/FONT]

 [FONT=Liberation Serif]Save the edited file and reboot.[/FONT]

 [FONT=Liberation Serif]The RIGblaster duo should now have a[FONT=Ubuntu Mono] ttyUSB*[/FONT] associated with it that can be configured in WSJT-X. In my case it was ttyUSB0.[/FONT]

 
 [FONT=Liberation Serif]**Reverting Changes:**[/FONT]

 [FONT=Liberation Serif]If this solution does not work for your problem and the [FONT=Ubuntu Mono]99-ftdi.rules[/FONT] file was newly created by you in solution section above, simply issue the following commands and reboot:[/FONT]
```

[FONT=Ubuntu Mono]$cd /etc/udev/rules.d[/FONT]
[FONT=Liberation Serif][FONT=Ubuntu Mono]$sudo rm 99-ftdi.rule[/FONT]s[/FONT]

```

 [FONT=Liberation Serif]If the [FONT=Ubuntu Mono]99-ftdi.rules[/FONT] file previously existed you will need to edit it and remove the pasted line you previously added leaving all previous file contents in place and reboot.[/FONT]

 
 [FONT=Liberation Serif]**Credits:**[/FONT]

 [FONT=Liberation Serif]Many thanks to the following sources![/FONT]

 [FONT=Liberation Serif]QRZ.com Forum - [/FONT][[FONT=Liberation Serif]click here to view post[/FONT]]("https://forums.qrz.com/index.php?threads/ubuntu-linux-wsjt-x-trying-to-get-virtual-com-port-set-up-for-ptt.798360/#post-6092605")
[FONT=Liberation Serif]eham.net Forum - [/FONT][[FONT=Liberation Serif]click here to view post[/FONT]]("https://www.eham.net/community/smf/index.php/topic,135469.0.html")  
unix.stackexchange.com Forum – see link above in Solution section
[FONT=Liberation Serif]David Nessl, W1DRN – Linux commands, ftdi driver source code [/FONT][FONT=Liberation Serif]troubleshooting and suggestions[/FONT]
[SIZE=2][FONT=Liberation Serif]Sholto Fisher, K7TMG -  Tech Support at West Mountain Radio[/FONT][/SIZE]
 
 
 [FONT=Liberation Serif]Thanks,[/FONT]
[FONT=Liberation Serif]Rick/WX9M[/FONT]

---

