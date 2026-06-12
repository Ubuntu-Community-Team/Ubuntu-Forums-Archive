---
title: "ASUS S56C Ultrabook - Touchpad &amp; Brightness Fn Configs"
date: 2013-06-12
forum: Tutorials
---

### Post by Roasted on 2013-06-12
Hello there. I have an ASUS S56C ultrabook. With the help of various other forum posts, along with some users in the IRC channel, the two main complaints I had about this laptop with Ubuntu on it has been fixed. Below are instructions on what I did to enable brightness functionality through the function keys, as well as better touchpad settings.


To enable function key support for brightness controls:
```
sudo gedit /etc/default/grub
```

Change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
```
Save the file. Once you reboot, this will allow your function keys to control brightness. (Fn F5 and Fn F6)


In my experience, I didn't have much luck with the built in controls within system settings for my touchpad on this laptop. I still felt the palm detection needed significantly more work as I had a hard time typing without shooting my cursor into other windows. A user in an IRC channel gave me this config that they were using for the same type of touchpad. I take no credit for this. I am simply reposting it for others to benefit from.

First,
```
sudo gedit /etc/X11/xorg.conf
```
Then, paste this section in:
```
Section "InputClass"
    Identifier "ETPS/2 Elantech Touchpad"
    MatchProduct "ETPS/2 Elantech Touchpad"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "TapButton1" "1"
    Option "TapButton2" "3"
    Option "TapButton3" "2"
    Option "VertTwoFingerScroll" "1"
    Option "HorizTwoFingerScroll" "1"
    Option "CoastingSpeed" "10"
    Option "EdgeMotionMinZ" "30"
    Option "EdgeMotionMaxZ" "40"
    Option "EdgeMotionMinSpeed" "100"
    Option "EdgeMotionMaxSpeed" "400"
    Option "FingerLow" "9"
    Option "FingerHigh" "12"
    Option "EmulateMidButtonTime" "0"
    Option "ClickPad" "True"
    Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
    Option "SHMConfig" "true"
EndSection
```

You might find yourself wanting to tweak these settings, and that's fine. Do so as you see fit. Other than that, these two configs are all that was needed to grant me a fully functional ASUS S56C. Hope these help.

---

### Post by carini2 on 2013-08-01
On my Aus S56C which is a kubuntu 12.04 installation with no customization apart from package selection

dmidecode:

System Information
        Manufacturer: ASUSTeK COMPUTER INC.
        Product Name: K56CB
        Version: 1.0       
        Serial Number: D3N0C..........     
        UUID: F2EC5980-62C2-......................
        Wake-up Type: Power Switch
        SKU Number: ASUS-NotebookSKU
        Family: K


The screen brightness and audio volume keys works with only


root@host:~# cat /etc/default/grub
[...]
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[...]

---

