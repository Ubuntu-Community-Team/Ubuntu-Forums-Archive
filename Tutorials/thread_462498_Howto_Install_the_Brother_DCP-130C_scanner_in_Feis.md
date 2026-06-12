---
title: "Howto: Install the Brother DCP-130C scanner in Feisty on a 32 bit system with a USB c"
date: 2007-06-02
forum: Tutorials
---

### Post by lonoy on 2007-06-02
This guide is a how to install the Brother DCP-130C scanner in Ubuntu Feisty/Gutsy/Hardy on a 32 Bit system with a USB connection. The guide is based on instructions from the Brother web site, which alone didn't  make my scanner work, and from various posts found within the Ubuntu forum and the Internet referring to different Brother models on older Ubuntu versions.
You will require the scanner driver from the Brother web site, the link is below. This guide assumes you already have the printer part of the unit functioning, if not then get that up and running first before attempting to install the scanner. The instructions on the Brother web site will work for the printer.

I am a Ubuntu novice so use this guide at your own risk.

1. **IMPORTANT**: Ensure the scanner is switched off before starting the install. If the power is on during the install the install will not work. Remove the power cord just to make sure.

2. Go to the Brother web site:

[http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html)

3. Locate the driver: brscan2 driver ver.0.2.4-0 for Debian 32 bit users.

4. Download the driver to your desktop. Once downloaded you should see the following file on your desktop. 

brscan2-0.2.4-0.i386.deb

Double check if you have the correct file. Move it to your desktop if you have downloaded it elsewhere. No need to extract the files.

5. Save your weekend! Check again if the power to the scanner is definitely switched off.

6. Check if you have the file "/etc/sane.d/brother.conf", if so delete it. 

7. Install the latest versions of Sane and Xsane

```
apt-get install sane xsane
```

8. Install the Brother scanner driver:
```
sudo dpkg -i ~/Desktop/brscan2-0.2.4-0.i386.deb
```

9. Modify the /etc/fstab file. 
```
gksudo gedit /etc/fstab
```

If the line which starts with:
"none /proc/bus/usb" or "usbfs /proc/bus/usb" 
DOES NOT exist in the /etc/fstab file, run the following command:
```
echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab
```

If the line which starts with:
"none /proc/bus/usb" or "usbfs /proc/bus/usb" 
DOES exist in the /etc/fstab file, edit the line as below:
```
none /proc/bus/usb usbfs auto,devmode=0666 0 0
```

10. Modify the USB access control:

```
umount /proc/bus/usb
```
then
```
mount /proc/bus/usb
```
then
```
mknod -m 666 /dev/usbscanner c 180 48
```

11. Edit the libsane.rules:
```
gksudo gedit /etc/udev/rules.d/45-libsane.rules
```

Add the following:

```
#Brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner
```

12. Power up your scanner and see if XSane recognizes it via: Applications: Graphics : XSane Image Scanner

If it is not working then all I can suggest is that you start from the beginning again ensuring you have the downloaded the correct driver as well as entering the correct commands.  I never tried try to uninstall the driver so in the end the above worked once I had it all sorted. 
If you have further questions once you have the scanner up and running then check Brothers FAQ page:
 
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html)

The above works on a 64bit system as long as you download the applicable 64bit driver from the Brother link above.


Have added link to Brother website. This page gives you instructions for different versions of Ubuntu.
[Brother Scanner Instructions]("http://solutions.brother.com/linux/en_us/instruction_scn1c.html")

Regards
Lonoy

---

### Post by doctorbrowder on 2007-09-04
I'm trying to install the scanner driver for a Brother DCP-130C. I got as far as Step 9 in the instructions given below. When I attempt the command 

echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab

it comes back with "permission denied". Does anybody know how to get around this? Thanx!

---

### Post by lonoy on 2007-09-05
Did you sign in as root? That is the only reason i can think of.

---

### Post by lesfrancoeurs on 2011-11-29
Also have this problem at step 9.  I accidentally erased everything in my fstab file and now I am lost.

---

### Post by lesfrancoeurs on 2011-11-29
In step when I ```
mount /proc/bus/usb
```
I get > mount: mount point /proc/bus/usb does not exist
It looks according to [this thread]("http://ubuntuforums.org/showthread.php?t=1432598") its because I'm using ubuntu 10.04 with a newer kernel and the solution looks a little scarry to me.

---

