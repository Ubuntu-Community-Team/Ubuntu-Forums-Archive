---
title: "Disable specific USB ports"
date: 2011-09-26
forum: Security
---

### Post by sooofunky on 2011-09-26
Hello,

I need to disable specific USB ports (not all), but could not find any useful information so far. What do I need to do?

Thank you!

---

### Post by underquark on 2011-09-26
What type of machine?  WHY do you want to disable them?  If it's to prevent people from plugging removable drives into the front of a PC (in corporate setting, for example) then the only sure way is to physically disconnect the ports, otherwise they can just insert a boot USB stick, run ubuntu (or puppy, or one of many other OS's) and carry on unrestricted.

---

### Post by sooofunky on 2011-09-26
Hi,

I've got a USB UMTS modem and it's not working properly. Now I would like to disable all the other USB ports, to run tests.

---

### Post by matt_symes on 2011-09-26
Hi

At the terminal type

```
for device in $(ls /sys/bus/usb/devices/*/product); do echo $device;cat $device;done
```

This will get you a list of usb devices. You can then turn the power off and on to them like so.


Turn it off.

```
echo suspend | sudo tee /sys/bus/usb/devices/[COLOR=Red]XXXX[/COLOR]/power/level
```

Turn it on

```
echo on | sudo tee /sys/bus/usb/devices/[COLOR=Red]XXXX[/COLOR]/power/level 						
```

Where XXXX is the device to switch off.

Here is an example from my machine.

```
matthew@matthew-laptop:/sys/bus/usb$ for device in $(ls /sys/bus/usb/devices/*/product); do echo $device;cat $device;done
/sys/bus/usb/devices/2-5/product
Video WebCam
/sys/bus/usb/devices/usb1/product
EHCI Host Controller
/sys/bus/usb/devices/usb2/product
EHCI Host Controller
/sys/bus/usb/devices/usb3/product
OHCI Host Controller
/sys/bus/usb/devices/usb4/product
OHCI Host Controller
/sys/bus/usb/devices/usb5/product
OHCI Host Controller
/sys/bus/usb/devices/usb6/product
OHCI Host Controller
matthew@matthew-laptop:/sys/bus/usb$ echo suspend | sudo tee /sys/bus/usb/devices/4-1/power/level
tee: /sys/bus/usb/devices/4-1/power/level: No such file or directory
suspend
matthew@matthew-laptop:/sys/bus/usb$ echo suspend | sudo tee /sys/bus/usb/devices/2-5/power/level
suspend
matthew@matthew-laptop:/sys/bus/usb$ echo on | sudo tee /sys/bus/usb/devices/2-5/power/level 
on
matthew@matthew-laptop:/sys/bus/usb$ 

```

It turns off and on my web cam.

Kind regards

---

### Post by r+9 on 2011-09-26
That was a useful answer!  
I don't need it but I'm writing that bit down in case someday I do.

---

### Post by VVAW on 2012-01-29
i am trying to this and can't figure out which one to disable.
i have a 24 usb hub connected to one usb port. I want to disable and enable on the fly via the command prompt


 ls /sys/bus/usb/devices
1-0:1.0    1-3.5.1:1.0  1-3.6.1:1.0  1-3.7.1:1.0  1-7:1.0    3-2.3:1.0
1-3        1-3.5.2      1-3.6.2      1-3.7.2      2-0:1.0    4-0:1.0
1-3.1      1-3.5.2:1.0  1-3.6.2:1.0  1-3.7.2:1.0  2-1        5-0:1.0
1-3:1.0    1-3.5.3      1-3.6.4      1-3.7.3      2-1:1.0    usb1
1-3.1:1.0  1-3.5.3:1.0  1-3.6.4:1.0  1-3.7.3:1.0  2-2        usb2
1-3.2      1-3.5.4      1-3.6.5      1-3.7.4      2-2:1.0    usb3
1-3.2:1.0  1-3.5.4:1.0  1-3.6.5:1.0  1-3.7.4:1.0  3-0:1.0    usb4
1-3.3      1-3.5.6      1-3.6.6      1-3.7.6      3-2        usb5
1-3.3:1.0  1-3.5.6:1.0  1-3.6.6:1.0  1-3.7.6:1.0  3-2:1.0
1-3.5      1-3.6        1-3.7        1-3.7.7      3-2.2
1-3.5.1    1-3.6.1      1-3.7.1      1-3.7.7:1.0  3-2.2:1.0
1-3.5:1.0  1-3.6:1.0    1-3.7:1.0    1-7          3-2.3

---

### Post by VVAW on 2012-01-29
Sorry but if I would like to shut disable a usb port

issues this command

echo suspend | sudo tee /sys/bus/usb/devices/USB1/power/level

to shutdown usb1

tHE PORT I WANT TO SHUTDOWN IS 1-3

---

### Post by matt_symes on 2012-01-30
Hi

Can you post the output of

```
lsusb -t
```

Can you post it between code tags 

[noparse]```
like this
```[/noparse]

to make it easier to read.

Kind regards

---

### Post by VVAW on 2012-01-30
~$ lsusb -t
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=hub, Driver=hub/4p, 12M
        |__ Port 2: Dev 3, If 0, Class=vend., Driver=pl2303, 12M
        |__ Port 3: Dev 4, If 0, Class=vend., Driver=pl2303, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=vend., Driver=pl2303, 12M
    |__ Port 2: Dev 3, If 0, Class=vend., Driver=pl2303, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 7: Dev 6, If 0, Class=stor., Driver=usb-storage, 480M

---

### Post by Merrattic on 2012-09-02
Sorry to drag this one up, but has something changed in 12.04?

If I run the suspend command for my webcam which is on 3-5

```
echo suspend | sudo tee /sys/bus/usb/devices/3-5/power/level
```I get

```
Invalid Argument
```Same with other devices. Just try to turning off annoying blue light on webcam when not in use :)

---

### Post by madjoe on 2012-09-09
If you have a kernel newer than 2.6.32 (which you do) it sounds like you cannot force a USB device to suspend anymore.

[http://unix.stackexchange.com/questions/13281/disable-usb-power-for-usb-controlled-power-strip](http://unix.stackexchange.com/questions/13281/disable-usb-power-for-usb-controlled-power-strip)

[http://stackoverflow.com/questions/1163824/linux-usb-turning-the-power-on-and-off](http://stackoverflow.com/questions/1163824/linux-usb-turning-the-power-on-and-off)

I'm looking for the same answer on how to do this. If anyone knows how to do it on Ubuntu 12.04, please share your thoughts.

---

### Post by rembeita on 2013-06-27
[COLOR=#000000][FONT=Arial]for kernels around 2.6.38 and above to disable.[/FONT][/COLOR]


echo "0" > "/sys/bus/usb/devices/usbX/power/autosuspend_delay_ms"echo "auto" > "/sys/bus/usb/devices/usbX/power/control"

---

### Post by matan2 on 2013-08-16
As mentioned, the initial suggestion on this thread seems to no longer work as of new kernels.[URL="http://unix.stackexchange.com/questions/13281/disable-usb-power-for-usb-controlled-power-strip"]
http://unix.stackexchange.com/questions/13281/disable-usb-power-for-usb-controlled-power-strip[/URL]
Not sure about the post from [[COLOR=#000000]rembeita[/COLOR]]("http://ubuntuforums.org/member.php?u=1834379")[COLOR=#000000] how it can actually be used to disable and then enable a USB device.... perhaps someone can clarify.. :)[/COLOR]

---

