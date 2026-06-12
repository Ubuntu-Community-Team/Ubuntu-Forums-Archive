---
title: "[Guide] Install Ubuntu 18.04 on HP Spectre x360 13&quot;"
date: 2019-03-05
forum: Tutorials
---

### Post by fmstrat2 on 2019-03-05
_[SIZE=5]**Ubuntu 18.04 status on HP Spectre x360 13"**[/SIZE]_
[LIST]
[*]Pen, touchpad, touchscreen are all functioning after updating to mainline kernel and latest libinput
[LIST]
[*]Caveat: After using pen, touchscreen is non-responsive temporarily 
[/LIST]
  
[*]s2idle and hibernate work, s3 is not supported 
[*]Fingerprint reader does not function 
[*]Built-in microphone does not function (BT mics work) 
[*]Webcam works 
[/LIST]


_**[SIZE=5]Guide[/SIZE]**_
[SIZE=4]
**Booting from the USB installer**[/SIZE]
A few steps are required to get this working:
[LIST=1]
[*]Set BIOS to legacy so you can boot Ubuntu, while you're at it, update the BIOS to the latest version (important!) 
[*]Insert 18.04 USB, reboot, use F9 to get into the USB boot loader 
[/LIST]

From here you can use *gparted* to re-partition and keep Windows, or the installer to wipe everything out.

**[SIZE=4]Post install[/SIZE]**
A lot works out of the box, however a number of steps are required to get all of the hardware functioning as expected.

**Libinput drivers**
First up, is updating libinput. This is required to get the pen, touchpad, and touchscreen working in harmony. First we'll install the native Ubuntu drivers to get all the prerequisites, then we will update to version 1.12 which corrects some of the pen issues.
```
sudo apt-get install -y libinput-tools xdotool
wget https://launchpad.net/ubuntu/+source/libinput/1.12.6-1/+build/16328793/+files/libinput-bin_1.12.6-1_amd64.deb -O /tmp/libinput-bin.deb
wget https://launchpad.net/ubuntu/+source/libinput/1.12.6-1/+build/16328793/+files/libinput-tools_1.12.6-1_amd64.deb -O /tmp/libinput-tools.deb
wget https://launchpad.net/ubuntu/+source/libinput/1.12.6-1/+build/16328793/+files/libinput10_1.12.6-1_amd64.deb -O /tmp/libinput10.deb
sudo apt install -y /tmp/libinput*.deb
rm -rf /tmp/libinput*.deb
```

**Mainline kernel**
In addition to libinput updates, the pen and screen rotation require an updated kernel. As of this writing, kernel v5.0.0 works best. First thing is to get the latest icl firmware:
```
sudo wget https://kernel.googlesource.com/pub/scm/linux/kernel/git/firmware/linux-firmware/+/master/i915/icl_dmc_ver1_07.bin -O /lib/firmware/i915/icl_dmc_ver1_07.bin
```

Next, you'll need the newer kernel. You have three options:
[LIST=1]
[*]Mainline kernel - If you can deal with all the dmesg errors, you can use the official mainline kernel. 
[*]Compile the mainline kernel with the patches applied 
[*]Use my custom built kernel - You can use the custom built mainline kernel with the Spectre x360 patches applied 
[/LIST]

*Option 1) Official Mainline Kernel (will get a flood of dmesg errors)*
```
sudo wget https://raw.githubusercontent.com/pimlie/ubuntu-mainline-kernel.sh/master/ubuntu-mainline-kernel.sh -O /usr/sbin/ubuntu-mainline-kernel
sudo chmod +x /usr/sbin/ubuntu-mainline-kernel
sudo ubuntu-mainline-kernel -i v5.0.3
```

*Option 2) Compile the mainline kernel with patches*
```
sudo wget https://raw.githubusercontent.com/pimlie/ubuntu-mainline-kernel.sh/master/ubuntu-mainline-kernel.sh -O /usr/sbin/ubuntu-mainline-kernel
sudo chmod +x /usr/sbin/ubuntu-mainline-kernel
sudo ubuntu-mainline-kernel -i v5.0.3
sudo mkdir -p /opt/kernel
cd /opt/kernel
sudo wget https://dl.dropbox.com/s/7q6co76m2eizfin/spectre-x360.diff?dl=0 -O spectre-x360.diff
sudo git clone git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
cd linux-stable
sudo git checkout -b spectre v5.0
sudo git apply ../spectre-x360.diff
sudo cp -vi /boot/config-5.0.3-050003-generic .config
sudo make oldconfig
sudo make -j`nproc` deb-pkg
sudo ubuntu-mainline-kernel -u v5.0.3
cd ..
sudo apt install ./linux-headers-5.0.3+_5.0.3+-1_amd64.deb ./linux-image-5.0.3+_5.0.3+-1_amd64.deb
```

*Option 3) Use my pre-built kernel (based on option 2) **<=- Easiest and best option***
```
wget https://dl.dropbox.com/s/3p90k3d6xaythbs/linux-headers-5.0.3%2B_5.0.3%2B-1_amd64.deb?dl=0 -O linux-headers-5.0.3+B_5.0.3+-1_amd64.deb
wget https://dl.dropbox.com/s/k6di26o6kadldne/linux-image-5.0.3%2B_5.0.3%2B-1_amd64.deb?dl=0 -O linux-image-5.0.3+_5.0.3+-1_amd64.deb
sudo apt install ./linux-headers-5.0.3+_5.0.3+-1_amd64.deb ./linux-image-5.0.3+_5.0.3+-1_amd64.deb
```

**Touchpad sensitivity**
The synaptic touchpad suffers from the sensitivity issues documented elsewhere. To fix this, toggle the settings that assit with palm detection.
```
USR=$(whoami)  
mkdir -p /home/$USR/.config/bin
echo "ID=\$(xinput -list |grep Touchpad |awk '{print \$6}')" > /home/$USR/.config/bin/synaptic.sh
echo 'ID=${ID##*=}' >> /home/$USR/.config/bin/synaptic.sh
echo 'xinput --set-prop "$ID" "Synaptics Finger" 50 90 255' >> /home/$USR/.config/bin/synaptic.sh
echo 'xinput --set-prop "$ID" "Synaptics Noise Cancellation" 20 20' >> /home/$USR/.config/bin/synaptic.sh
chmod +x /home/$USR/.config/bin/synaptic.sh
echo "[Desktop Entry]" > /home/$USR/.config/autostart/synaptic.desktop
echo "Type=Application" >> /home/$USR/.config/autostart/synaptic.desktop
echo "Exec=/home/$USR/.config/bin/synaptic.sh" >> /home/$USR/.config/autostart/synaptic.desktop
echo "Hidden=false" >> /home/$USR/.config/autostart/synaptic.desktop
echo "NoDisplay=false" >> /home/$USR/.config/autostart/synaptic.desktop
echo "X-GNOME-Autostart-enabled=true" >> /home/$USR/.config/autostart/synaptic.desktop
echo "Name[en_US]=synaptic" >> /home/$USR/.config/autostart/synaptic.desktop
echo "Name=synaptic" >> /home/$USR/.config/autostart/synaptic.desktop
echo "Comment[en_US]=" >> /home/$USR/.config/autostart/synaptic.desktop
echo "Comment=" >> /home/$USR/.config/autostart/synaptic.desktop
```

**Intel tearing fix**
The Spectre 13" with Intel graphics is susceptible to video tearing. To fix this, use the Tearfix option for Xorg.
```
sudo mkdir -p /etc/X11/xorg.conf.d
echo 'Section "Device"' |sudo tee /etc/X11/xorg.conf.d/20-intel.conf
echo '  Identifier  "Intel Graphics"' |sudo tee -a /etc/X11/xorg.conf.d/20-intel.conf
echo '  Driver      "intel"' |sudo tee -a /etc/X11/xorg.conf.d/20-intel.conf
echo '  Option      "TearFree" "true"' |sudo tee -a /etc/X11/xorg.conf.d/20-intel.conf
echo 'EndSection' |sudo tee -a /etc/X11/xorg.conf.d/20-intel.conf
```
**NOTE* One user has reported issues with Chrome menus after this fix. While I do not experience this on my UHD device, your results may vary.*
[B]
**Wifi updates**
[/B]Out of the box the v38 firmware is defaulted for Wifi, which is slower and offers lower connection speeds. The below line will download the v43 firmware that works best with our Wifi chipset.
```
sudo wget https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-9000-pu-b0-jf-b0-43.ucode -O /lib/firmware/iwlwifi-9000-pu-b0-jf-b0-43.ucode
```
[B]
Power management[/B]
The Spectre does not auto power manage out of the box, however TLP manages the laptop perfectly.
```
apt-get install -y tlp powertop
```


_**[SIZE=5]Optional[/SIZE]**_
[SIZE=4]
[/SIZE]**Enable Hibernation**
Hibernation is included in this guide because of the Spectre's unique need to disable i2c prior to hibernation, and then re-enable post. Hibernation can be implemented one of two ways.
[B]
Hibernate option 1) Via GNOME settings[/B]
This option works best if you do not have encrypted drives. This is true because when resuming with encrypted drives, you already have to enter a password post-hibernate. If you use this option with encrypted drives, you will be required to enter 2 passwords on resume.
```
echo "[Re-enable hibernate by default in upower]" |sudo tee /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
echo "Identity=unix-user:*" |sudo tee -a /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
echo "Action=org.freedesktop.upower.hibernate" |sudo tee -a /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
echo "ResultActive=yes" |sudo tee -a /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
echo "" |sudo tee -a /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
echo "[Re-enable hibernate by default in logind]" |sudo tee -a /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
echo "Identity=unix-user:*" |sudo tee -a /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
echo "Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit" |sudo tee -a /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
echo "ResultActive=yes" |sudo tee -a /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
echo "i2c_hid" |sudo tee /etc/suspend-modules.conf
echo '#!/bin/bash' |sudo tee /lib/systemd/system-sleep/suspend-modules
echo '' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo 'case $1 in' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo '    pre)' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo '        for mod in $(</etc/suspend-modules.conf); do' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo '            modprobe -r $mod' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo '        done' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo '    ;;' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo '    post)' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo '        for mod in $(</etc/suspend-modules.conf); do' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo '            modprobe $mod' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo '        done' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo '    ;;' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
echo 'esac' |sudo tee -a /lib/systemd/system-sleep/suspend-modules
sudo chmod a+x /lib/systemd/system-sleep/suspend-modules
echo '#!/bin/bash' |sudo tee -a /etc/pm/sleep.d/99_resume
echo 'case "$1" in' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '    thaw|resume)' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '  sleep 1' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '        XINPUTUSER=$(who | grep :0 | sed 's/\([a-z]*\).*/\1/')' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '        DISPLAY=:0.0 su $XINPUTUSER -c "sh /home/$XINPUTUSER/.config/bin/synaptic.sh"' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '        ;;' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '    *)' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '        ;;' |sudo tee -a /etc/pm/sleep.d/99_resume
echo 'esac' |sudo tee -a /etc/pm/sleep.d/99_resume
echo 'exit $?' |sudo tee -a /etc/pm/sleep.d/99_resume
sudo chmod a+x /etc/pm/sleep.d/99_resume
gsettings set org.gnome.settings-daemon.plugins.power power-button-action 'hibernate'
```

**Hibernate option 2) Via ACPID**
This option works better for encrypted drives because it runs at the system level and bypasses GNOME login. This way you only have to enter one password. The reason to use ACPID instead of GNOME is if you want to be able to have the lid close and go into s2idle while requiring a password at resume (GNOME), while at the same time NOT requiring the gnome password on resume from hibernation.
```
sudo apt-get install pm-tools
echo 'event=button/power' |sudo tee /etc/acpi/events/power
echo 'action=/etc/acpi/hibernate.sh "%e"' |sudo tee -a /etc/acpi/events/power
echo '#!/bin/bash' |sudo tee /etc/acpi/hibernate.sh
echo '' |sudo tee -a /etc/acpi/hibernate.sh
echo 'if [ `whoami` == "root" ]; then' |sudo tee -a /etc/acpi/hibernate.sh
echo '  modprobe -r i2c_hid' |sudo tee -a /etc/acpi/hibernate.sh
echo '  pm-hibernate' |sudo tee -a /etc/acpi/hibernate.sh
echo '  sleep 1' |sudo tee -a /etc/acpi/hibernate.sh
echo '  modprobe i2c_hid' |sudo tee -a /etc/acpi/hibernate.sh
echo '  sleep 1' |sudo tee -a /etc/acpi/hibernate.sh
echo '  XINPUTUSER=$(who | grep :0 | sed "s/\([a-z]*\).*/\1/")' |sudo tee -a /etc/acpi/hibernate.sh
echo '  DISPLAY=:0.0 su $XINPUTUSER -c "sh /home/$XINPUTUSER/.config/bin/synaptic.sh"' |sudo tee -a /etc/acpi/hibernate.sh
echo 'else' |sudo tee -a /etc/acpi/hibernate.sh
echo '  echo "Must be root";' |sudo tee -a /etc/acpi/hibernate.sh
echo 'fi' |sudo tee -a /etc/acpi/hibernate.sh
sudo chmod a+x /etc/acpi/hibernate.sh
gsettings set org.gnome.settings-daemon.plugins.power power-button-action 'nothing'
```

**Hibernate add-on: Hibernate after s2idle**
Regardless of the option you choose, you can also enable "Hibernate after s2idle" so that when you close the lid the machine will hibernate after a period of time. The below assumes you wish to hibernate after the machine has been in s2idle state for 5400 seconds.
```
echo '#!/bin/bash' |sudo tee -a /etc/pm/sleep.d/99_resume
echo 'case "$1" in' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '    thaw|resume)' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '  sleep 1' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '        XINPUTUSER=$(who | grep :0 | sed "s/\([a-z]*\).*/\1/")' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '        DISPLAY=:0.0 su $XINPUTUSER -c "sh /home/$XINPUTUSER/.config/bin/synaptic.sh"' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '        ;;' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '    *)' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '        ;;' |sudo tee -a /etc/pm/sleep.d/99_resume
echo 'esac' |sudo tee -a /etc/pm/sleep.d/99_resume
echo 'exit $?' |sudo tee -a /etc/pm/sleep.d/99_resume
echo '[Sleep]' |sudo tee /etc/systemd/sleep.conf
echo 'HibernateDelaySec=5400' |sudo tee -a /etc/systemd/sleep.conf
sed -i 's/#HandleLidSwitch=suspend/HandleLidSwitch=suspend-then-hibernate/g' /etc/systemd/logind.conf
```

---

### Post by mayurvirkar on 2019-03-09
Hey Ben, 
Thank you!
Continuing our discussion, yes, I was able to get the webcam work. Actually, it was working out of the box for me. 
I am facing only three known issues as of now.
1: Mic = this is the biggest issue for me.
2: Speakers. Only L & R which are placed below the laptop work. the ones which are placed near the screen, they dont.
3: Orientation = I care less, very less for this one.

EDIT:
```

# ./ubuntu-mainline-kernel.sh -i v5.0.0Downloading index from kernel.ubuntu.com
It seems version v5.0.0 is already installed, continue? (y/N) 
/tmp/ubuntu-mainline-kernel.sh/ is not writable

```
If anyone else is facing the same problem, add ```
 -p . 
```

---

### Post by fmstrat2 on 2019-03-09
> **mayurvirkar said:**
> Hey Ben, 
Thank you!
Continuing our discussion, yes, I was able to get the webcam work. Actually, it was working out of the box for me. 
I am facing only three known issues as of now.
1: Mic = this is the biggest issue for me.
2: Speakers. Only L & R which are placed below the laptop work. the ones which are placed near the screen, they dont.
3: Orientation = I care less, very less for this one.

EDIT:
```

# ./ubuntu-mainline-kernel.sh -i v5.0.0Downloading index from kernel.ubuntu.com
It seems version v5.0.0 is already installed, continue? (y/N) 
/tmp/ubuntu-mainline-kernel.sh/ is not writable

```
If anyone else is facing the same problem, add ```
 -p . 
```

I will continue to investigate the mic and speakers. The orientation should be fixed if you use the mainline kernel, but I believe we discussed that in our email off the patch on the 5.0.0 kernel on launchpad. 

Good catch on the script error, it looks like the author uses the same temporary directory name as the script name. I will alter the instructions to keep that from happening (and may do a PR too).

My webcam issue seemed to be frome issuing the patch for the libinput bug. I was still running my device 5.0.0+ kernel and hadnt conpiled in v4l. Easy fix and updating that in the status.

Thanks!

---

### Post by mayurvirkar on 2019-03-09
Two more issues from my dmesg

```

[    0.093158] ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.XDCI], AE_NOT_FOUND (20180531/dswload2-160)
[    0.093162] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20180531/psobject-221)
[    0.093164] ACPI Error: Ignore error and continue table load (20180531/psobject-604)
[    0.093165] ACPI Error: Skip parsing opcode Scope (20180531/psloop-543)
[    0.093419] ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.I2C1.TPL1], AE_NOT_FOUND (20180531/dswload2-160)
[    0.093422] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20180531/psobject-221)
[    0.093423] ACPI Error: Ignore error and continue table load (20180531/psobject-604)
[    0.093425] ACPI Error: Skip parsing opcode Scope (20180531/psloop-543)
[    0.093918] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.GPLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.093921] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.093922] ACPI Error: Skip parsing opcode Method (20180531/psloop-543)
[    0.093924] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.TPLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.093926] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.093927] ACPI Error: Skip parsing opcode Method (20180531/psloop-543)
[    0.093929] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.GUPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.093931] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.093932] ACPI Error: Skip parsing opcode Method (20180531/psloop-543)
[    0.093934] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.TUPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.093936] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.093937] ACPI Error: Skip parsing opcode Method (20180531/psloop-543)

```
=> No functional issues AFAIK.
And

```

$ dmesg | grep iwlwifi
[   35.153965] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[   35.156058] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-43.ucode failed with error -2
[   35.156199] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-42.ucode failed with error -2
[   35.156337] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-41.ucode failed with error -2
[   35.156349] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-40.ucode failed with error -2
[   35.156358] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-39.ucode failed with error -2
[   35.159839] iwlwifi 0000:00:14.3: loaded firmware version 38.c0e03d94.0 op_mode iwlmvm
[   35.188070] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[   35.237939] iwlwifi 0000:00:14.3: base HW address: 50:76:af:8b:16:90
[   35.322588] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0

```
=> Wifi is slow and low network strength

---

### Post by fmstrat2 on 2019-03-09
What kernel are you running for the below errors?

> **mayurvirkar said:**
> Two more issues from my dmesg

```

[    0.093158] ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.XDCI], AE_NOT_FOUND (20180531/dswload2-160)
[    0.093162] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20180531/psobject-221)
[    0.093164] ACPI Error: Ignore error and continue table load (20180531/psobject-604)
[    0.093165] ACPI Error: Skip parsing opcode Scope (20180531/psloop-543)
[    0.093419] ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.I2C1.TPL1], AE_NOT_FOUND (20180531/dswload2-160)
[    0.093422] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20180531/psobject-221)
[    0.093423] ACPI Error: Ignore error and continue table load (20180531/psobject-604)
[    0.093425] ACPI Error: Skip parsing opcode Scope (20180531/psloop-543)
[    0.093918] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.GPLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.093921] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.093922] ACPI Error: Skip parsing opcode Method (20180531/psloop-543)
[    0.093924] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.TPLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.093926] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.093927] ACPI Error: Skip parsing opcode Method (20180531/psloop-543)
[    0.093929] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.GUPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.093931] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.093932] ACPI Error: Skip parsing opcode Method (20180531/psloop-543)
[    0.093934] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.TUPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.093936] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.093937] ACPI Error: Skip parsing opcode Method (20180531/psloop-543)

```
=> No functional issues AFAIK.


These are likely harmless but theoretically could be resulting in something like the lack of s3. The DSDT is out of the range of my knowledge, so this likely needs to be reported upstream (I'm seeing them, too).

> 
And

```

$ dmesg | grep iwlwifi
[   35.153965] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[   35.156058] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-43.ucode failed with error -2
[   35.156199] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-42.ucode failed with error -2
[   35.156337] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-41.ucode failed with error -2
[   35.156349] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-40.ucode failed with error -2
[   35.156358] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-39.ucode failed with error -2
[   35.159839] iwlwifi 0000:00:14.3: loaded firmware version 38.c0e03d94.0 op_mode iwlmvm
[   35.188070] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[   35.237939] iwlwifi 0000:00:14.3: base HW address: 50:76:af:8b:16:90
[   35.322588] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0

```
=> Wifi is slow and low network strength


Could you try replacing your ucode file with the one mentioned in this kernel bug: [https://bugzilla.kernel.org/show_bug.cgi?id=201813#c24](https://bugzilla.kernel.org/show_bug.cgi?id=201813#c24)

The direct link to the file is: [https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-9000-pu-b0-jf-b0-43.ucode](https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-9000-pu-b0-jf-b0-43.ucode)

---

### Post by fmstrat2 on 2019-03-09
To be specific, run this command:

[HTML]sudo wget https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-9000-pu-b0-jf-b0-43.ucode -O /lib/firmware/iwlwifi-9000-pu-b0-jf-b0-43.ucode[/HTML]

Then reboot. The v43 firmware loaded for me fine, but I haven't done any speed tests. If you confirm speed and signal strength are better, I'll update the guide until that hits the main kernel tree.

---

### Post by mayurvirkar on 2019-03-09
Hello,
Loading the ucode file did the trick. And yes, the performance has also improved.


Also, about "Intel tearing fix" fix from the initial post, it actually causes problems for me, especially on google chrome.
Without the fix, everything works fine.


Problems caused by the fix: unclear right-click menu for Google Chrome. (See attached picture.)

---

### Post by fmstrat2 on 2019-03-09
Interesting. I'll put that in a note, and update for Wifi accordingly. As for top speakers, can you try this:

```
sudo apt install alsa-tools alsa-tools-gui
hdajackretask
```

A window will popup, so:
[LIST=1]
[*]At the top, change Codec to Realtek ALC285
[*]On the right, check the box for "Show unconnected pins"
[*]For pin 0x14, check "Override"
[*]For pin 0x14, select "Internal speaker (LFE)"
[*]For pin 0x1e, check "Override"
[*]For pin 0x1e, select "Internal speaker"
[*]Click "Apply now"
[/LIST]

Then test the speakers?

---

### Post by fmstrat2 on 2019-03-09
Btw, what were your before/after signal strength and speeds?

---

### Post by fmstrat2 on 2019-03-09
Added option in guide for hibernate after s2idle time.

---

### Post by mayurvirkar on 2019-03-09
hdajackretask gives error device or resource busy.
Trying apply on boot option. Will update.


About wifi:
Old link speed ~500mbps. Now, 866mbps.

---

### Post by mayurvirkar on 2019-03-09
Not able to make out.
Is there any package which will play every speaker individually?

---

### Post by fmstrat2 on 2019-03-09
Hrm, give this a shot:

Before running hda:
```
systemctl --user mask pulseaudio.socket
systemctl --user stop pulseaudio.service
```

And after:

```
systemctl --user unmask pulseaudio.socket
systemctl --user start pulseaudio.service
```

If mask/unmask doesn't work, try stop/start.

---

### Post by fmstrat2 on 2019-03-09
Actually, give this a shot:

```
echo "autospawn = no" | sudo tee -a /etc/pulse/client.conf
pulseaudio --kill

echo "0x12 0x411111f0" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x13 0x40000000" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x14 0x90170151" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x16 0x411111f0" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x17 0x90170110" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x18 0x411111f0" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x19 0x04a110c0" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x1a 0x411111f0" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x1b 0x411111f0" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x1d 0x40600001" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x1e 0x90170150" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo "0x21 0x04211020" | sudo tee /sys/class/sound/hwC0D0/user_pin_configs
echo 1 | sudo tee /sys/class/sound/hwC0D0/reconfig

sudo sed -i 's/^autospawn = no//g' /etc/pulse/client.conf
pulseaudio --start
```

It doesn't give me the device busy error, but I can't tell if it's working. I never used Windows so I don't know what I'm listening for.

---

### Post by mayurvirkar on 2019-03-10
Trying

---

### Post by mayurvirkar on 2019-03-10
No audio output at all.
None.
I also played with hdajackretask, the moment there is any configuration in [COLOR=#000000][FONT=&quot]/sys/class/sound/hwC0D0/user_pin_configs, everything breaks. 

PS: reboot fixes everything & yes, the above user_pin_configs file is empty on reboot.[/FONT][/COLOR]

---

### Post by fmstrat2 on 2019-03-11
Ok, I will keep toying with it and see if I can figure it out. The above script still gives me audio, though, so I'm not sure what's different about our setups.

---

### Post by mayurvirkar on 2019-03-15
Hey,
I installed kernel 5.0.2, dmesg is still flooded, looks like that patch didn't get approved.
How are things at your side? Any improvements?

---

### Post by fmstrat2 on 2019-03-15
> **mayurvirkar said:**
> Hey,
I installed kernel 5.0.2, dmesg is still flooded, looks like that patch didn't get approved.
How are things at your side? Any improvements?

Yea, they haven't integrated the patch yet. There is also a second patch for a tiny flood of messages from the pen, too. 

Is there interest in me posting a link to a precompiled `deb` of a patched kernel?

---

### Post by mayurvirkar on 2019-03-18
I think the mic should have higher priority here. Coz thats the only thing making me consider moving to windows.
Do you have any luck with the same?

---

### Post by fmstrat2 on 2019-03-20
Added precompiled kernel options.

I haven't focused on the mic because I use a BT headset instead. If the mic is anything like the fingerprint sensor, it's because it uses a new interface that there are no kernel drivers for the subsystem yet. That would be the likely reason behind it not being a higher priority for kernel devs.

---

### Post by mayurvirkar on 2019-03-21
I am on kernel 5.1-rc1 :)
The reason I can think of is not many users using linux on this laptop. I only know two. :D

---

### Post by fmstrat2 on 2019-03-21
> **mayurvirkar said:**
> I am on kernel 5.1-rc1 :)
The reason I can think of is not many users using linux on this laptop. I only know two. :D

Yea, I used 5.0.3 as the version for the guide as it is the newest in the stable branch.

It's a catch 22. If people can't find a good guide that says "everything works!" such as this one, people who want to run Linux don't buy the laptop. But then if people don't try, we don't get the guides. So hopefully this sways a few people in their purchase.

---

### Post by silverark2 on 2019-03-27
> **mayurvirkar said:**
> I am on kernel 5.1-rc1 :)
The reason I can think of is not many users using linux on this laptop. I only know two. :D


Now it's three! I've arrived here trying to get the internal microphone working too. Took a while to get the touchpad right, but now I'm happy with it. Just the mic to go!

---

### Post by mayurvirkar on 2019-03-28
Awesome!
Yes, mic is the biggest problem for me as well.
Btw, you got all four speakers working? 
I am on 5.1-rc2 and the dmesg is still flooded.

---

### Post by mayurvirkar on 2019-03-28
Just FYI: [https://bugzilla.kernel.org/show_bug.cgi?id=189331](https://bugzilla.kernel.org/show_bug.cgi?id=189331)

---

### Post by mayurvirkar on 2019-04-03
Please add support to: [https://bugzilla.kernel.org/show_bug.cgi?id=203129](https://bugzilla.kernel.org/show_bug.cgi?id=203129)
Lets help them fix this issue

---

### Post by nalsubaie on 2019-05-03
This worked on an old HP specte x360:
Install pulseAudio volume control
```
sudo apt install pavucontrol
``` 
Go to input device tab and select "Main Microphone (unplugged)" from the drop down menu

---

### Post by perttuu on 2019-08-09
Hello from the fourth (or fifth?) guy to use Ubuntu on the Spectre! ):P

I've got most of my setup working but the mic remains a problem, along with hibernation. After invoking hibernation, the computer doesn't resume but boots when power button is pressed.

In pavucontrol, under input devices there's only the already-chosen option "Microphone (unplugged)" under Built-In Audio Analog Stereo. (And, Monitor of built-in analog stereo which is just a looper of the audio out)

Otherwise, my setup involves i3-wm which required quite a bit fiddling to get things scaled properly but atm practically everything works. Using the i3-gnome in order to get many programs to scale with a single  setting. Spotify remains a problem though, it's UI flickering badly. For some reason there is no option to disable hardware acceleration in the GUI and upon first googling I didn't find a way to set it from terminal.


P.S. I have to say that betterlockscreen looks just amazing with the UHD screen :cool:

---

### Post by brandonhowlett on 2019-08-29
Hey all! Thanks for the guide. I'm trying for number 6?

 I've gotten hung up installing the headers. I can't make any sense of this so hopefully someone can weigh in.

I tried option 2 and 3 for the kernal. In both instances I get stuck on the final line:
```
sudo apt install ./linux-headers-5.0.3+_5.0.3+-1_amd64.deb ./linux-image-5.0.3+_5.0.3+-1_amd64.deb
```

Output
```

Reading package lists... Done
E: Unsupported file ./linux-headers-5.0.3+_5.0.3+-1_amd64.deb given on commandline
E: Unsupported file ./linux-image-5.0.3+_5.0.3+-1_amd64.deb given on commandline
```

Suggestions?

Update:

The headers were downloaded to the home folder. Ugh.

Another question. Has anyone had problems with their camera. Testing it with Cheese produced a heavily fragmented flashing image that produced a blank picture.

---

### Post by knichols-dtc on 2020-04-05
Mic is working in 20.04 beta.

---

