---
title: "Setup Guide 2020: Asus ROG Zephyrus GA502 Ryzen 7 3750H + Nvidia GTX 1660 Ti"
date: 2020-04-13
forum: Tutorials
---

### Post by andrewfer000 on 2020-04-13
After almost a year of owning my laptop I have come up with much better ways of using it. I have improved battery life, fixed sensor and the infamous 400 Mhz throttle, improved functionality, and increased the system's performance overall. I worked very hard on this so please leave a thank you if this helped. I hope we can continue to make Asus ROG laptops more Linux friendly since they are great for the price.

Original post: [https://ubuntuforums.org/showthread.php?t=2420199](https://ubuntuforums.org/showthread.php?t=2420199)

If you are thinking about buying this laptop for ANY GNU/Linux use DONT! (unless your okay with some compromise) There are better laptop options for maybe only $200 more. 
The GPU part of the guide should work on most if not all AMD/Nvidia hybrids. 

The full model name is: Asus-ROG-Zephyrus-G-GU502DU-GA502DU

I can attest Ubuntu 19.04,19.10 and 20.04 LTS work great. I would recommend Ubuntu 20.04 since it uses Kernel 5.4, Has pre-installed drivers, and its LTS. 

Pros-
Ubuntu works with some workarounds
Battery life is better than most (prob. will improve over time)
GPU is great
In my case, Ubuntu works better than Windows now.
System is quiet-ish when gaming
Screen is great for the price.

Cons-
Keyboard special functions like back light controls and manual fan controls don't work
The included Wi-Fi card is crap.
It has no webcam (but does any real GNU/Linux user care about that?!)
Battery life is bad when gaming or any time the Nvidia GPU is in use.

From [https://www.reddit.com/r/linux_gaming/comments/gcz3v5/asus_rog_zephyrus_ga502du_linux_setup_scripts/](https://www.reddit.com/r/linux_gaming/comments/gcz3v5/asus_rog_zephyrus_ga502du_linux_setup_scripts/)
You  can now run scripts from [https://github.com/saladhax/ga502-linux](https://github.com/saladhax/ga502-linux) This  will help if you are concerned with messing something up manually. Thank you Saladhax! This DOES NOT implement everything in this guide

I will be using the command line and Nano for my text editor FYI. please be familar with it. If you cannout "write to a file" make sure you use Sudo.

Out of the box, The system has only one major issue and that is the Realtek WiFi Driver. Follow this post here for fix - [https://askubuntu.com/questions/1071...n-ubuntu-18-04](https://askubuntu.com/questions/1071...n-ubuntu-18-04) But here is the Answer anyway
```

sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh

```

For the Kernel config. I suggest putting the following in the /etc/default/grub after the word splash
```
 nouveau.modeset=0 tpm_tis.interrupts=0 acpi_osi=Linux i915.preliminary_hw_support=1 idle=nomwait
```


You will need to install the Nvidia GPU driver if you do not have it already! The instructions change sometimes so I suggest doing a search on it. But its mostly just adding the graphics PPA and installing nvidia-utils-440 Once you follow the instructions and the driver as well as the xserver settings is installed go on to the next step.

```
 sudo add-apt-repository ppa:graphics-drivers/ppa 
```

Press enter to update the repos, then Install the latest Nvidia Driver. As of April, 2020
```
 sudo apt install nvidia-driver-440 
```

Then reboot

So, here is the new thing that saves battery and allows the laptop to sleep! There is a new way to operate the GPUs. If your on the go, the best way is to do use the AMD Vega 10 with Nvidia GTX 1660 Ti as an GL/Vulkan offload card but that disables the USB-C DP Port or you can use the Nvidia card as the primary card for everything which enables the USB-C DP.   

So how do we go about setting this up? Lets go over the first part, Using the Nvidia as the primary card I will be following these instructions for the most part. This uses the PRIME feature of Xorg. It does not work with wayland
Heres the original post on Nvidia Forums. I put the instructions here and made them more gamer/noob-friendly.
Original Post:[ https://devtalk.nvidia.com/default/t...04726/#5404726]("https://devtalk.nvidia.com/default/topic/1067083/linux/nvidia-xconfig-doesnt-do-what-i-want-it-to-nor-does-nvidia-settings/post/5404726/#5404726")

Make sure you have sudo ready since you will need it for most of this. 
Make sure this file does not exist  /etc/X11/xorg.conf

Edit /usr/share/X11/xorg.conf.d/10-amdgpu.conf
as sudo and Replace
```
Driver "amdgpu" 
```
With
```
Driver "modesetting"
```

For faster AMD Acceleration, Put in the following in the Output Class, under the modesetting will work. This is optional and may use more battery life.
```
 
 Option "AccelMethod" "glamor"
Option "DRI" "3"
 
```

Save and exit

inside the OutputClass of /usr/share/X11/xorg.conf.d/10-nvidia.conf
```
Option "PrimaryGPU" "Yes"
``` This makes Nvidia the primary GPU

Save and exit.

Create and edit
```
 /etc/xdg/autostart/optimus.desktop
```



```


[Desktop Entry]
Type=Application
Name=Optimus
Exec=sh -c "xrandr --setprovideroutputsource modesetting NVIDIA-0; xrandr --auto"
NoDisplay=true
X-GNOME-Autostart-Phase=DisplayServer


```

Do the same with this file below

```
nano /usr/share/gdm/greeter/autostart/ 
```

Save and exit the files

```
nano /etc/X11/xorg.conf
```

insert the code below in the file.

```

Section "ServerLayout"
  Identifier "layout"
  Option "AllowNVIDIAGPUScreens"
EndSection

```

Reboot and when you login you should run ```
 glxinfo |grep "vendor"
``` in a terminal and you should see
```

server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

```

Now to go into APU + Offload mode edit the /usr/share/X11/xorg.conf.d/10-nvidia.conf and comment out the Primary GPU Line Save the file. Then Log out and in again. But I suggest rebooting. You will use this file to switch between the APU + Nvidia Offload to Nvidia Only.


You should be able to login. Run ```
 glxinfo |grep "vendor" 
``` and you should see
```

server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: X.Org

```

When you run this ```
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia glxinfo | grep vendor 
```

You should get
```

server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

```

Now you can run ```
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia steam
``` to use the GPU with steam and all of its child processes.
 
Want the latest and greatest open source AMD Drivers? Add this PPA (This may cause issues but I haven't had any yet.)
```
 sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt-get dist-upgrade 
```

Okay here is the "hard" part. In order to get the thermal throttle issue fixed on the LTS Kernel we need to patch and build a Ubuntu Kernel from source

First things first. we need to prepare our system so run these commands one at a time

```

sudo apt-get install git build-essential kernel-package fakeroot libncurses5-dev
cd ~
mkdir kernel5.4-patched
cd kernel5.4-patched/
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-focal.git 

```
(This will take a long time! do the next few steps while its doing it)

open another terminal and *cd ~/kernel5.4-patched/ubuntu-focal/*

type *nano asus_wmi.patch * and copy and paste the following (from [https://patchwork.kernel.org/patch/11292815/](https://patchwork.kernel.org/patch/11292815/)) into the file

```

diff --git a/drivers/platform/x86/asus-wmi.c b/drivers/platform/x86/asus-wmi.c
index f10ec9d745e5..469f1a852719 100644
--- a/drivers/platform/x86/asus-wmi.c
+++ b/drivers/platform/x86/asus-wmi.c
@@ -1780,6 +1780,15 @@  static int throttle_thermal_policy_write(struct asus_wmi *asus)
     return 0;
 }
 
+static int throttle_thermal_policy_set_default(struct asus_wmi *asus)
+{
+    if (!asus->throttle_thermal_policy_available)
+        return 0;
+
+    asus->throttle_thermal_policy_mode = ASUS_THROTTLE_THERMAL_POLICY_DEFAULT;
+    return throttle_thermal_policy_write(asus);
+}
+
 static int throttle_thermal_policy_switch_next(struct asus_wmi *asus)
 {
     u8 new_mode = asus->throttle_thermal_policy_mode + 1;
@@ -2548,6 +2557,8 @@  static int asus_wmi_add(struct platform_device *pdev)
     err = throttle_thermal_policy_check_present(asus);
     if (err)
         goto fail_throttle_thermal_policy;
+    else
+        throttle_thermal_policy_set_default(asus);
 
     err = asus_wmi_sysfs_init(asus->platform_device);
     if (err)

```

save and exit. Then enter *nano asus_wmit.patch  *and copy and paste to create the second patch (from [https://patchwork.kernel.org/patch/11292813/](https://patchwork.kernel.org/patch/11292813/))

```

diff --git a/Documentation/ABI/testing/sysfs-platform-asus-wmi b/Documentation/ABI/testing/sysfs-platform-asus-wmi
index 9e99f2909612..1efac0ddb417 100644
--- a/Documentation/ABI/testing/sysfs-platform-asus-wmi
+++ b/Documentation/ABI/testing/sysfs-platform-asus-wmi
@@ -46,3 +46,13 @@  Description:
             * 0 - normal,
             * 1 - overboost,
             * 2 - silent
+
+What:        /sys/devices/platform/<platform>/throttle_thermal_policy
+Date:        Dec 2019
+KernelVersion:    5.6
+Contact:    "Leonid Maksymchuk" <leonmaxx@gmail.com>
+Description:
+        Throttle thermal policy mode:
+            * 0 - default,
+            * 1 - overboost,
+            * 2 - silent
diff --git a/drivers/platform/x86/asus-wmi.c b/drivers/platform/x86/asus-wmi.c
index 821b08e01635..f10ec9d745e5 100644
--- a/drivers/platform/x86/asus-wmi.c
+++ b/drivers/platform/x86/asus-wmi.c
@@ -61,6 +61,7 @@  MODULE_LICENSE("GPL");
 #define NOTIFY_KBD_BRTDWN        0xc5
 #define NOTIFY_KBD_BRTTOGGLE        0xc7
 #define NOTIFY_KBD_FBM            0x99
+#define NOTIFY_KBD_TTP            0xae
 
 #define ASUS_WMI_FNLOCK_BIOS_DISABLED    BIT(0)
 
@@ -81,6 +82,10 @@  MODULE_LICENSE("GPL");
 #define ASUS_FAN_BOOST_MODE_SILENT_MASK        0x02
 #define ASUS_FAN_BOOST_MODES_MASK        0x03
 
+#define ASUS_THROTTLE_THERMAL_POLICY_DEFAULT    0
+#define ASUS_THROTTLE_THERMAL_POLICY_OVERBOOST    1
+#define ASUS_THROTTLE_THERMAL_POLICY_SILENT    2
+
 #define USB_INTEL_XUSB2PR        0xD0
 #define PCI_DEVICE_ID_INTEL_LYNXPOINT_LP_XHCI    0x9c31
 
@@ -198,6 +203,9 @@  struct asus_wmi {
     u8 fan_boost_mode_mask;
     u8 fan_boost_mode;
 
+    bool throttle_thermal_policy_available;
+    u8 throttle_thermal_policy_mode;
+
     // The RSOC controls the maximum charging percentage.
     bool battery_rsoc_available;
 
@@ -1724,6 +1732,98 @@  static ssize_t fan_boost_mode_store(struct device *dev,
 // Fan boost mode: 0 - normal, 1 - overboost, 2 - silent
 static DEVICE_ATTR_RW(fan_boost_mode);
 
+/* Throttle thermal policy ****************************************************/
+
+static int throttle_thermal_policy_check_present(struct asus_wmi *asus)
+{
+    u32 result;
+    int err;
+
+    asus->throttle_thermal_policy_available = false;
+
+    err = asus_wmi_get_devstate(asus,
+                    ASUS_WMI_DEVID_THROTTLE_THERMAL_POLICY,
+                    &result);
+    if (err) {
+        if (err == -ENODEV)
+            return 0;
+        return err;
+    }
+
+    if (result & ASUS_WMI_DSTS_PRESENCE_BIT)
+        asus->throttle_thermal_policy_available = true;
+
+    return 0;
+}
+
+static int throttle_thermal_policy_write(struct asus_wmi *asus)
+{
+    int err;
+    u8 value;
+    u32 retval;
+
+    value = asus->throttle_thermal_policy_mode;
+
+    err = asus_wmi_set_devstate(ASUS_WMI_DEVID_THROTTLE_THERMAL_POLICY,
+                    value, &retval);
+    if (err) {
+        pr_warn("Failed to set throttle thermal policy: %d\n", err);
+        return err;
+    }
+
+    if (retval != 1) {
+        pr_warn("Failed to set throttle thermal policy (retval): 0x%x\n",
+            retval);
+        return -EIO;
+    }
+
+    return 0;
+}
+
+static int throttle_thermal_policy_switch_next(struct asus_wmi *asus)
+{
+    u8 new_mode = asus->throttle_thermal_policy_mode + 1;
+
+    if (new_mode > ASUS_THROTTLE_THERMAL_POLICY_SILENT)
+        new_mode = ASUS_THROTTLE_THERMAL_POLICY_DEFAULT;
+
+    asus->throttle_thermal_policy_mode = new_mode;
+    return throttle_thermal_policy_write(asus);
+}
+
+static ssize_t throttle_thermal_policy_show(struct device *dev,
+                   struct device_attribute *attr, char *buf)
+{
+    struct asus_wmi *asus = dev_get_drvdata(dev);
+    u8 mode = asus->throttle_thermal_policy_mode;
+
+    return scnprintf(buf, PAGE_SIZE, "%d\n", mode);
+}
+
+static ssize_t throttle_thermal_policy_store(struct device *dev,
+                    struct device_attribute *attr,
+                    const char *buf, size_t count)
+{
+    int result;
+    u8 new_mode;
+    struct asus_wmi *asus = dev_get_drvdata(dev);
+
+    result = kstrtou8(buf, 10, &new_mode);
+    if (result < 0)
+        return result;
+
+    if (new_mode > ASUS_THROTTLE_THERMAL_POLICY_SILENT)
+        return -EINVAL;
+
+    asus->throttle_thermal_policy_mode = new_mode;
+    throttle_thermal_policy_write(asus);
+
+    return count;
+}
+
+// Throttle thermal policy: 0 - default, 1 - overboost, 2 - silent
+static DEVICE_ATTR_RW(throttle_thermal_policy);
+
 /* Backlight ******************************************************************/
 
 static int read_backlight_power(struct asus_wmi *asus)
@@ -2005,6 +2105,11 @@  static void asus_wmi_handle_event_code(int code, struct asus_wmi *asus)
         return;
     }
 
+    if (asus->throttle_thermal_policy_available && code == NOTIFY_KBD_TTP) {
+        throttle_thermal_policy_switch_next(asus);
+        return;
+    }
+
     if (is_display_toggle(code) && asus->driver->quirks->no_display_toggle)
         return;
 
@@ -2155,6 +2260,7 @@  static struct attribute *platform_attributes[] = {
     &dev_attr_lid_resume.attr,
     &dev_attr_als_enable.attr,
     &dev_attr_fan_boost_mode.attr,
+    &dev_attr_throttle_thermal_policy.attr,
     NULL
 };
 
@@ -2178,6 +2284,8 @@  static umode_t asus_sysfs_is_visible(struct kobject *kobj,
         devid = ASUS_WMI_DEVID_ALS_ENABLE;
     else if (attr == &dev_attr_fan_boost_mode.attr)
         ok = asus->fan_boost_mode_available;
+    else if (attr == &dev_attr_throttle_thermal_policy.attr)
+        ok = asus->throttle_thermal_policy_available;
 
     if (devid != -1)
         ok = !(asus_wmi_get_devstate_simple(asus, devid) < 0);
@@ -2437,6 +2545,10 @@  static int asus_wmi_add(struct platform_device *pdev)
     if (err)
         goto fail_fan_boost_mode;
 
+    err = throttle_thermal_policy_check_present(asus);
+    if (err)
+        goto fail_throttle_thermal_policy;
+
     err = asus_wmi_sysfs_init(asus->platform_device);
     if (err)
         goto fail_sysfs;
@@ -2521,6 +2633,7 @@  static int asus_wmi_add(struct platform_device *pdev)
 fail_input:
     asus_wmi_sysfs_exit(asus->platform_device);
 fail_sysfs:
+fail_throttle_thermal_policy:
 fail_fan_boost_mode:
 fail_platform:
     kfree(asus);
diff --git a/include/linux/platform_data/x86/asus-wmi.h b/include/linux/platform_data/x86/asus-wmi.h
index 60249e22e844..d39fc658c320 100644
--- a/include/linux/platform_data/x86/asus-wmi.h
+++ b/include/linux/platform_data/x86/asus-wmi.h
@@ -58,6 +58,7 @@ 
 #define ASUS_WMI_DEVID_LIGHT_SENSOR    0x00050022 /* ?? */
 #define ASUS_WMI_DEVID_LIGHTBAR        0x00050025
 #define ASUS_WMI_DEVID_FAN_BOOST_MODE    0x00110018
+#define ASUS_WMI_DEVID_THROTTLE_THERMAL_POLICY 0x00120075
 
 /* Misc */
 #define ASUS_WMI_DEVID_CAMERA        0x00060013

```

Save and exit. Wait for git to finish downloading the kernel's code.

Once done make sure you're in the *~/kernel5.4-patched/ubuntu-focal/* and that all the kernel source files are there along with our patch files. Now we patch the kernel with these commands. Do it in order. One at a time :)

```

patch -p1 < asus_wmit.patch
patch -p1 < asus_wmi.patch

```

Next run  *cp /boot/config-`uname -r` .config  *to copy your current kernel config to the new one.
Run  *make oldconfig  *To ensure that the config is setup properly. Press enter until its done.
Run  *make menuconfig  *and make sure your terminal is large enough to show the program. Onces its loaded you can just exit out of it
Run  *make clean   *to clean up any stray or unwanted files
Finally, run  *make -j `getconf _NPROCESSORS_ONLN` deb-pkg LOCALVERSION=-patched  *you can put what you want after the - for example I used *generic* to keep things consistant.

WARNING! This will compile our Kernel. IT MAY TAKE UP TO 2 HOURS! Be aware that the dpkg-deb may look like its stuck but it just takes a long time. Do not interupt it. Go grab a bite to eat or watch TV or somthing. You can keep using the laptop during this but it will take a little longer.

Once done run  *sudo dpkg -i ../*.deb  *and then wait It will need to rebuild the kernel modules such as the WiFI.
To end it off, run  *sudo update-grub   *Then reboot 

If this is your newest kernel, It should be the top option. If not, go into Advance Options (under Ubuntu) and select our custom kernel

If all goes well, You should be able to have temps below 50 dC and above 90 dC and not have any throttling issues. As well as fan control. To check sensors, Install psensor by running  [I]sudo apt install psensor 
[/I]and launch it with *psensor *(If you cannot find the sensor list you may need to drag it out from the left part of the window)

Congrats! You just patched, compiled, and installed your very own custom kernel..

Get more out of your Ryzen- [https://wiki.archlinux.org/index.php/CPU_frequency_scaling](https://wiki.archlinux.org/index.php/CPU_frequency_scaling)

Thanks to [Rog-Core]("https://github.com/flukejones/rog-core"), The Fn keys (such as display brightness, fan, touchpad), keyboard backlight control, and microphone mute work! Here is how you go about installing it. The commands are from the github page.

```

sudo add-apt-repository ppa:lukedjones/rog-core
sudo apt-get update
sudo apt-get install rog-core

```

After a reboot, You should now be able to use the keyboard much like on Windows.

Rog-core Alternatives Below, NOT REQUIRED

Keyboard Backlight & Fans -
Thanks to [https://github.com/qquique/rogauracore](https://github.com/qquique/rogauracore) we can now control our keyboard backlight Run each line individually!

```

git clone https://github.com/qquique/rogauracore
cd rogauracore 
git checkout initialize_keyboard
autoreconf -i 
./configure
make

```
You can now run

```
sudo ./rogauracore initialize_keyboard
``` to initialize the keyboard and
```
sudo ./rogauracore brightness 1
``` to turn it on. This number can go up to 3.

You will need to run this command at system startup in the rogauracore directory (most likley /home/rogauracore)
```
sudo ./rogauracore initialize_keyboard
```

If you are on Kernel 5.6 or newer, or have a patched kernel 5.4, you can  now run ```
echo 2 | sudo tee  /sys/devices/platform/asus-nb-wmi/throttle_thermal_policy
``` The  number can be 0 for Balanced, 1 for turbo, and 2 for silent

Commands to keep handy (just in case)
```

__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia *program*

sudo ./rogauracore initialize_keyboard #Prepares keyboard light. Run inside the *~/rogauracore* direcory

sudo ./rogauracore brightness 1 # can go up to 3

echo 2 | sudo tee /sys/devices/platform/asus-nb-wmi/throttle_thermal_policy # 0 for Balanced, 1 for Turbo, and 2 for silent

cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor # View CPU Govenor

sudo bash -c 'for ((i=0;i<$(nproc);i++)); do cpufreq-set -c $i -g *performance*; done'   #Can be* powersave, conservative, ondemand, userspace, or performance *Each have their own benefits

 echo* 0* | sudo tee /sys/devices/system/cpu/cpufreq/boost # 0 Disables turbo, 1 Enables Turbo. 


```

NOTE 0- I use GDM for my login screen and KDE as my main desktop. I also  use GNOME sometimes. I suggest using GDM so all the scripts properly  execute.

NOTE 1- I tested both GNOME and KDE. My battery life has been increased by around 50% when i'm on the go (I now get around 6 hours when not gaming with 60% screen brightness). In my opinion the APU is powerful enough for most basic tasks and even HD gaming on the go. I use the Open Source AMD driver from Mesa. This has not been tested on Debian, PopOS or Mint but it should work if you get the proper drivers working. Gnome seems to have some issues with the HDMI 

NOTE 2- If you use any DisplayLink USB to VGA or docking station hardware you MUST use the Nvidia GPU in primary mode or else you will get some nasty lag. You also must install the driver with the [Debian Displaylink installer]("https://github.com/AdnanHodzic/displaylink-debian") on kernels newer than 5.3 (I am using 5.6.5 with no issues for the most part.)

NOTE 3- INFO FOR THERMAL THROTTLING (5/2/2020)- I heard a rumor that new  versions of Kernel 5.6 will be bringing a patch that will allow ASUS  laptops to not throttle at 90 dC. When this upgrade comes out and I can  prove it works (and wont break my system) I will update this Tutorial  soon after! Personally, I run Kernel 5.6.5 (from Canonical) and still  have the issue so we will see (possibly around kernel 5.7 release) what  happens. I may also compile my own kernel from kernel.org sources if I  do not see it soon but hopfully it wont come to that (Its an easy, but  long and boring process) I learned this from these two sources I DO NOT recommed you follow the instructions they provide (yet) I will update this tutorial if things work out.-
    
NOTE 3 Update- The thermal throttling issue is fixed. I am running BIOS 302 with a patched kernel 5.4. I am assuming that you can use kernel 5.6 but it is not LTS so it will not be supported for long. My issue was that I had blacklist *asus-nb-wmi* inside of /etc/modprobe.d/blacklist.conf which should have been commented out. After that everything should work fine. If you want to use Kernel 5.4 from focal repos I will update this guide soon.


[https://forum.level1techs.com/t/laptop-ryzen-3750h-dropping-to-400mhz-in-linux-and-staying-there/148651](https://forum.level1techs.com/t/laptop-ryzen-3750h-dropping-to-400mhz-in-linux-and-staying-there/148651)
[https://bbs.archlinux.org/viewtopic.php?id=248477](https://bbs.archlinux.org/viewtopic.php?id=248477)

Also when BestBuy opens back up in my area I will be taking my laptop in for "repair" (asus recommended me to)

This is it for the tutorial. if you have anything to add feel free to add a comment. Anyone involved with this laptop should try to research the following. We're almost there to a perfect laptop! 
[LIST]
[*]Fan Control and Improving thermal issues //FIXED 
[*]Sleep Mode //(Mostly) FIXED 
[*](Continue Improving) Battery life 
[*]Keyboard backlight // FIXED
[*]Function Keys //FIXED 
[/LIST]

---

### Post by djun2 on 2020-04-30
as a beginner ubuntu user this helps me a lot. thank you very much for your help :)

---

### Post by CelticWarrior on 2020-04-30
Thank you very much for such tutorial.

For 20.04 the only difference is that you don't need the graphics drivers PPA. Newer Nvidia drivers versions are available in the main repositories already.

---

### Post by coffeecat on 2020-04-30
*Thread moved to **Tutorials** sub-forum.*

[Tutorials Sub-forum – Guidelines](https://ubuntuforums.org/showthread.php?t=2143602)

---

### Post by charmchi on 2020-06-01
Dude, thank you so so much for this. I was so close to returning this laptop but I followed your tutorial and tried patching the kernel and it worked, no more cpus stuck at 400mhz haha. I literally created this account just now to say thank you lol.

---

### Post by MemoNick on 2020-06-09
Thanks so much! Followed the tutorial for the GPU and it's working peachy so far :)

---

### Post by MemoNick on 2020-06-09
I noticed that I was still having thermal throttling. I couldn't follow the guide (patching rejects most changes), but I have updated to BIOS 302. As you can see below (from cpupower), the frequency has gone down to 399MHz. Do you have any suggestions on how I can fix it please?

```
Setting cpu: 0Setting cpu: 1
Setting cpu: 2
Setting cpu: 3
Setting cpu: 4
Setting cpu: 5
Setting cpu: 6
Setting cpu: 7
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency:  Cannot determine or is not supported.
  hardware limits: 1.40 GHz - 2.30 GHz
  available frequency steps:  2.30 GHz, 1.70 GHz, 1.40 GHz
  available cpufreq governors: conservative ondemand userspace powersave performance schedutil
  current policy: frequency should be within 1.40 GHz and 2.30 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency: Unable to call hardware
  current CPU frequency: 399 MHz (asserted by call to kernel)
  boost state support:
    Supported: no
    Active: no

```

EDIT: I have updated to the patched kernel. Before updating to BIOS 302, the trackpad was not working, but it is now. So far, there is no thermal throttling, but I will update if that changes. Leaving this here for reference.

EDIT 2: Nevermind, using the latest patched kernel does *not* solve the issue. I am using BIOS 302 with the latest patched kernel, but the thermal throttling persists. I'm completely lost. Any help?

---

### Post by andrewfer000 on 2020-06-17
Hi MemoNick,
Sorry for the long wait, If you are having trouble with the kernel patching I would suggest installing a newer kernel (5.6 or newer) that has these patches built-in you can run these in the terminal to install the prebuilt
packages from the Ubuntu Kernel Developers

**[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.6.19/]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.3/")**

Run the following in a terminal to download this kernel. This is for  AMD64 generic kernel. If you need a different kernel type go to the  webpage and copy the links and then paste them after *wget* (like seen below)[I][I]. THIS KERNEL IS AT END OF LIFE. IT IS RECOMENDED TO INSTALL KERNEL 5.7 WHEN ITS SUPPORTED!
[/I][/I]
```

mkdir kernel5.6.19 && cd kernel5.6.19

wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.6.19/amd64/linux-headers-5.6.19-050619-generic_5.6.19-050619.202006171132_amd64.deb

wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.6.19/amd64/linux-headers-5.6.19-050619_5.6.19-050619.202006171132_all.deb

wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.6.19/amd64/linux-image-unsigned-5.6.19-050619-generic_5.6.19-050619.202006171132_amd64.deb

wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.6.19/amd64/linux-modules-5.6.19-050619-generic_5.6.19-050619.202006171132_amd64.deb

sudo dpkg -i *.deb

```

Here is the newest Mainline kernel from Team Ubuntu. This will change in the future. The link will stay the same but the number after the **v** will change when newer kernels come out. Check out [kernel.org]("http://kernel.org") to see the latest mainline kernel. Nvidia currently DOES NOT work on this kernel. So I do not suggest using it yet.
**[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.3/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.3/)**
  ```

mkdir kernel5.7.3 && cd kernel5.7.3

wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.3/amd64/linux-headers-5.7.3-050703-generic_5.7.3-050703.202006171531_amd64.deb

wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.3/amd64/linux-headers-5.7.3-050703_5.7.3-050703.202006171531_all.deb

wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.3/amd64/linux-image-unsigned-5.7.3-050703-generic_5.7.3-050703.202006171531_amd64.deb

wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.3/amd64/linux-modules-5.7.3-050703-generic_5.7.3-050703.202006171531_amd64.deb

sudo dpkg -i *.deb

```

Once it's done reboot. If this kernel has issues, you can reboot into the old kernel through the advance options for Ubuntu in grub.

---

### Post by albator1932 on 2020-07-03
I've heard that NVidia drivers 440.100 that have been released recently actually do support kernel 5.7

---

### Post by albator1932 on 2020-07-06
Yes I confirm, currently running Pop!_OS 20.04 with kernel 5.7.7 and nVidia drivers 440.100 and everything is finally running flawlessly so far!
I'll keep an eye on the clock speed and temperatures for a few days but it looks like this mess is finally solved for good, fingers crossed!

```

 cedric  ~  neofetch
             /////////////                cedric@jarvis
         /////////////////////            --------------------------- 
      ///////*767////////////////         OS: Pop!_OS 20.04 LTS x86_64 
    //////7676767676*//////////////       Host: Zephyrus G GU502DU_GA502DU 1.0 
   /////76767//7676767//////////////      Kernel: 5.7.7-050707-generic 
  /////767676///*76767///////////////     Uptime: 20 mins 
 ///////767676///76767.///7676*///////    Packages: 2904 (dpkg), 4 (snap), 1 (appimaged) 
/////////767676//76767///767676////////   Shell: bash 5.0.16 
//////////76767676767////76767/////////   Resolution: 1920x1080, 1920x1080 
///////////76767676//////7676//////////   DE: GNOME 
////////////,7676,///////767///////////   WM: Mutter 
/////////////*7676///////76////////////   WM Theme: Pop 
///////////////7676////////////////////   Theme: Pop-dark [GTK2/3] 
 ///////////////7676///767////////////    Icons: Pop [GTK2/3] 
  //////////////////////'////////////     Terminal: gnome-terminal 
   //////.7676767676767676767,//////      CPU: AMD Ryzen 7 3750H with Radeon Vega Mobile Gfx (8) @ 2.300GHz 
    /////767676767676767676767/////       GPU: AMD ATI 05:00.0 Picasso 
      ///////////////////////////         GPU: NVIDIA GeForce GTX 1660 Ti Mobile 
         /////////////////////            Memory: 3602MiB / 23793MiB 
             /////////////
                                                                  




 cedric  ~  nvidia-smi
Mon Jul  6 11:54:55 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.100      Driver Version: 440.100      CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 166...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   53C    P8     6W /  N/A |    487MiB /  5944MiB |     12%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      4356      G   /usr/lib/xorg/Xorg                            80MiB |
|    0      5674      G   /usr/lib/xorg/Xorg                           155MiB |
|    0     10507      G   /usr/bin/gnome-shell                         116MiB |
|    0     34767      G   ...AAAAAAAAAAAACAAAAAAAAAA= --shared-files   123MiB |
+-----------------------------------------------------------------------------+



```

---

### Post by victor7095 on 2020-07-17
> **albator1932 said:**
> Yes I confirm, currently running Pop!_OS 20.04 with kernel 5.7.7 and nVidia drivers 440.100 and everything is finally running flawlessly so far!
I'll keep an eye on the clock speed and temperatures for a few days but it looks like this mess is finally solved for good, fingers crossed!

```

 cedric  ~  neofetch
             /////////////                cedric@jarvis
         /////////////////////            --------------------------- 
      ///////*767////////////////         OS: Pop!_OS 20.04 LTS x86_64 
    //////7676767676*//////////////       Host: Zephyrus G GU502DU_GA502DU 1.0 
   /////76767//7676767//////////////      Kernel: 5.7.7-050707-generic 
  /////767676///*76767///////////////     Uptime: 20 mins 
 ///////767676///76767.///7676*///////    Packages: 2904 (dpkg), 4 (snap), 1 (appimaged) 
/////////767676//76767///767676////////   Shell: bash 5.0.16 
//////////76767676767////76767/////////   Resolution: 1920x1080, 1920x1080 
///////////76767676//////7676//////////   DE: GNOME 
////////////,7676,///////767///////////   WM: Mutter 
/////////////*7676///////76////////////   WM Theme: Pop 
///////////////7676////////////////////   Theme: Pop-dark [GTK2/3] 
 ///////////////7676///767////////////    Icons: Pop [GTK2/3] 
  //////////////////////'////////////     Terminal: gnome-terminal 
   //////.7676767676767676767,//////      CPU: AMD Ryzen 7 3750H with Radeon Vega Mobile Gfx (8) @ 2.300GHz 
    /////767676767676767676767/////       GPU: AMD ATI 05:00.0 Picasso 
      ///////////////////////////         GPU: NVIDIA GeForce GTX 1660 Ti Mobile 
         /////////////////////            Memory: 3602MiB / 23793MiB 
             /////////////
                                                                  




 cedric  ~  nvidia-smi
Mon Jul  6 11:54:55 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.100      Driver Version: 440.100      CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 166...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   53C    P8     6W /  N/A |    487MiB /  5944MiB |     12%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      4356      G   /usr/lib/xorg/Xorg                            80MiB |
|    0      5674      G   /usr/lib/xorg/Xorg                           155MiB |
|    0     10507      G   /usr/bin/gnome-shell                         116MiB |
|    0     34767      G   ...AAAAAAAAAAAACAAAAAAAAAA= --shared-files   123MiB |
+-----------------------------------------------------------------------------+



```

I coudn`t install Pop OS :( since it fails at the end of installation. Some error about hardware. I Think it's installed but it failed at grub configuration

---

### Post by albator1932 on 2020-07-18
> **victor7095 said:**
> I coudn`t install Pop OS :( since it fails at the end of installation. Some error about hardware. I Think it's installed but it failed at grub configuration

Well it's going to be hard to solve with such information... I have installed Pop!_OS 19.10 and 20.04 several times on this machine and never had any issue with the install process.

---

### Post by ashwath998 on 2020-07-28
Hey man, I'm planning to install pop too on the same system. Did you have to do anything specified in this thread during the pop installation to get it working? Anything I should look out for?

thanks

---

### Post by marklaz on 2020-08-03
First of all, I want to thank you for this guide, literally saved my day last week and has been user-friendly enough even for a 15 years away from Linux user to understand. 

I only upgraded the kernel to 5.7.11 (as of July 29th) which also fixes nVidia Graphics, so if someone is struggling about it with 5.6 or with the patching of 5.4 (I got a lot of errors on the diff command so I went on to the latest stable kernel), this is a good option.
And if you want to update the tutorial, the 5.4 kernel patch is not working anymore (at least, it didn't for me).

```

mkdir kernel5.7.11 && cd kernel5.7.11

wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.11/amd64/linux-headers-5.7.11-050711-generic_5.7.11-050711.202007290540_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.11/amd64/linux-headers-5.7.11-050711_5.7.11-050711.202007290540_all.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.11/amd64/linux-image-unsigned-5.7.11-050711-generic_5.7.11-050711.202007290540_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.11/amd64/linux-modules-5.7.11-050711-generic_5.7.11-050711.202007290540_amd64.deb

sudo dpkg -i *.deb

```
):P

---

### Post by mussifer on 2020-08-05
Hi, i've been following this thread for a while looking for a solution on this issue. So far i haven't been able to get rid of the thermal throttle, mainly because i can't update the kernel of due to the speed of the laptop when it's throttled, so i'm looking for any linux image with kernel 5.7+ preinstalled. @albator1932: Does Pop! comes with this or you also had to update? I would appreciate any help as i need to work on my thesis on linux in this laptop. Thanks

---

### Post by nonlogin on 2020-08-26
> **andrewfer000 said:**
> There are better laptop options for maybe only $200 more. 
Hello! Sorry for off topic but can you recommend some model please? Something with a bit shorter Ubuntu instruction :)

---

### Post by g1k on 2020-12-02
Could you please share how you managed to install nvidia drivers. As i am facing gui boot issues after installing the drivers. Wifi, thermal issues got resolved with kernel 5.7.11 but it didn't solve the nvidia driver problems. 

Thank you

---

### Post by CelticWarrior on 2020-12-02
@g1k

The tutorial doesn't mention but assumes Secure Boot is disabled. Please check yours.

---

