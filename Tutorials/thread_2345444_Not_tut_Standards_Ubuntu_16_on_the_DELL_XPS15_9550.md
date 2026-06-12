---
title: "Not tut Standards Ubuntu 16 on the DELL XPS15 9550"
date: 2016-12-04
forum: Tutorials
---

### Post by JumpingJack on 2016-12-04
Hi all,

After reading a few different guides, I would like to share a final step-by-step guide to make ubuntu 16 work fine on this laptop (I've taken information from several places, including this forum)

Maybe the **most important thing on this guide is the palm detection on the touchpad**, I managed to make it work after trying different approaches.

My laptop:
[LIST]
[*]CPU: Intel® Core&#8482; i7-6700HQ
[*]RAM: 16GB
[*]Graphics: Intel i915 / NVIDIA GTX960M
[*]FullHD screen (non-touch)
[*]HDD: 512GB SSD
[/LIST]

**[SIZE=5]Update bios[/SIZE]**
I used the factory default windows to update before installing ubuntu the laptop. Just go to dell website and follow steps.

**[SIZE=5]Install ubuntu[/SIZE]**
I installed ubuntu 16.04.1 (LTS).
[LIST]
[*]Booted using UEFI from the BIOS (Secure mode OFF)
[*]Removed all partitions on the SSD
[*]Created a 550 MB UEFI partition
[*]Used the rest of the SSD file as EXT4 partition mounted on /
[/LIST]

What works for me out of the box:
[LIST]
[*]Sound
[*]Wifi / Bluetooth
[*]Graphics (only using the intel i915 vga). (See how to install NVIDIA drivers below)
[*]Touchpad 
[*]USB
[*]Function keys: Bright control, keyboard light, volume control, etc
[*]Lid switch: Suspension works fine, no issues but no long term testing.
[/LIST]

**What DOESN'T work:**
[LIST]
[*]Touchpad palm detection: See how to fix it below
[/LIST]


**[SIZE=5]Update kernel[/SIZE]**
Ubuntu 16 ships with kernel 4.4, but from versions 4.6 onwards there are several important updates regarding DELL laptops and nvidia graphics boards. There are many ways to update your kernel, but in my opinion, this one is by far the easiest:

```

git clone [https://github.com/mtompkins/linux-kernel-utilities](https://github.com/mtompkins/linux-kernel-utilities)
cd linux kernel-utilities
./update_ubuntu_kernel.sh

```

(At the time of this writing 4.8.11) is the newest version. You can run the update_ubuntu_kernel.sh script whenever you want to update your kernel in the future.


During kernel update eventually you could see this errors: 
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915
You can safely ignore them.


[B][SIZE=5]Fix touchpad palm detection
[/SIZE][/B]

**[SIZE=4]1 - Fix the double touchpad detection[/SIZE]**

In my case, 2 touch pads were detected: DELL touchpad and Synaptics touchpad. To check this, just open a terminal and type:
```

xinput list

```

It will print a list of input devices. Under the &#8220;*Virtual core pointer*&#8221; line, you&#8217;ll see 2 touchpads, the DELL XXX and the Synaptics.

**To fix this issue:**  
As sudo user create a file &#8220;*synaptics.conf*&#8221; under */etc/modprobe.d/* and paste the following text inside:

```
blacklist i2c-designware-platform
```

You can do it just pasting this command in a console:
```
sudo echo &#8220;blacklist i2c-designware-platform&#8221; > /etc/modprobe.d/synaptics.conf
```


After adding this file, just reboot your computer and check again using &#8220;xinput list&#8221;, you should see *only* the synaptics touchpad


**[SIZE=4]2 - Fix the palm detection[/SIZE]**
(Taken from: [https://www.reddit.com/r/Dell/comments/4pgek1/dell_xps_13_touch_pad_palm_detection_on_ubuntu/](https://www.reddit.com/r/Dell/comments/4pgek1/dell_xps_13_touch_pad_palm_detection_on_ubuntu/))

Please take into account this procedure is only for ubuntu 16

Install libinput:
```
sudo apt-get install xserver-xorg-input-libinput
```

Create a file: */usr/share/X11/xorg.conf.d/60-libinput.conf* and paste inside the following text:

```
Section "InputClass"
        Identifier "libinput touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "libinput"
        Option "Tapping" "True"
        Option "PalmDetection" "True"
        Option "TappingDragLock" "True"
EndSection

```

[B][SIZE=5]NVIDIA drivers installation
[/SIZE][/B]

Install nvidia driver;
```
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-375 nvidia-prime

```

Install prime-indicator: Allows you to switch between the intel integrated grapchis (i915) and the NVIDIA.  

```

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt update
sudo apt install prime-indicator

```

**Please note:** At the time of writing, the latest nvidia driver version supporting the graphics hardware on the XPS15 is the nvidia-375, please check nvidia page to know wich version is the most &#8220;up-to-date&#8221;. Suggestion: DO NOT INSTALL the driver directly from nvidia, just use the ppa listed on this document.

---

### Post by slickymaster on 2016-12-05
*Thread moved to **Tutorials**.*

---

### Post by zzzace2000 on 2016-12-28
Thanks it works!

BTW, if you want to add natural scrolling, just put this additional options.

Option "NaturalScrolling" "True"

---

