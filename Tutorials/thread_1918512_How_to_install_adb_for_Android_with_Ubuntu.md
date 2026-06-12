---
title: "How to install adb for Android with Ubuntu"
date: 2012-02-01
forum: Tutorials
---

### Post by kevdog on 2012-02-01
This guide addresses how to install adb (Android Device Bridge) for Android Devices.

This guide is currently written using Ubuntu 11.10.  It will be updated periodically for changes within the Android SDK and any changes the would accompany future Ubuntu releases.

This guide is directed for individuals interested in rooting their Android device or those interested in flashing custom ROMs, software development, or theme alterations or just about any other activity that would necessitate use of adb or fastboot for device modification.

**[SIZE="3"]1. Install the Android SDK and Download the Platform Tools Package from within the Android SDK Manager[/SIZE]**

Grab the Android SDK for linux: [**_Google Android SDK_**]("http://developer.android.com/sdk/index.html") 

Place the file within your home directory.
Unpack the sdk within the your users home directory:
```

cd ~ 
tar -zxvf android-sdk_r16-linux.tgz  

```
***Android-sdk version number may vary depending on version of the SDK downloaded.


Within the ~/android-sdk-linux/tools subfolder is an executable called **android**.  Despite the non-descript name, the executable **android** is actually the **Android SDK Manager**.  Launch the Android SDK Manager.
```

./~/android-sdk-linux/tools/android

```
Select Android SDK Tools and Android SDK Platform-tools.(Screen shot provided below).  Any additional packages may be downloaded as well.  Go grab a bite to eat!!

The platform tools package contains both the adb and fastboot executables.  These programs will be located within the newly created directoy ~/android-sdk-linux/platform-tools

**[SIZE="3"]2. Modify your PATH environment variable to include the adb and fastboot executables.[/SIZE]**
The PATH environment variable may be either modified within ~/.profile (or ~/.bash_profile) or within ~/.bashrc. (The ~/.profile file is read upon login for all interactive shells, and the ~/.bashrc file is read upon all non-interactive shells (i.e sftp).  In most cases and by default the ~/.profile file imports all settings from the ~/.bashrc file). The PATH statemnt must be altered to include the /android-sdk-linux/tools and /android-sdk-linux/platform-tools directories.  

I modified my PATH statment within gedit by adding the following to the bottom of the ~/.bashrc file:
```

export PATH=${PATH}:${HOME}/android-sdk-linux/tools:${HOME}/android-sdk-linux/platform-tools

```

**[SIZE="3"]3. Create udev rules for Ubuntu to correctly identify the device when it is plugged into the USB port[/SIZE]**

This is the most difficult part of the entire process.
First plug in the device to the usb port, then execute the following command:  

```
lsusb
```

This should produce output similar to the following:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 063: ID 04e8:6860 Samsung Electronics Co., Ltd

In my working example, my device was correctly identified:
**Bus 001 Device 063: ID 04e8:6860 Samsung Electronics Co., Ltd**

The statement above can be deciphered:
**Bus 001 Device 063**: This information helps us determine the name of the device node.  The device node's name is: /dev/bus/usb/**001**/**063**  
**04e8**: The vendorID 
**6860**: The productID

Using device node's name (/dev/bus/usb/001/063), its possible to query the device and discover its attributes.  Discovery of these attributes is necessary since udev matches the device based on specific criteria.  We need to right a ruleset that udev can use to match the device.  The first step of this process is discovering criteria that can be plugged into our ruleset.  This can be done in one of two ways, each are acceptable.  The output of either of these methods generates the information for us to construct the udev rule for the device. The query program we are using for this method is known as [**_udevadm_**]("http://linux.die.net/man/8/udevadm") 

**Query Method #1**
```
udevadm info -q all -n <name of device node>
```

In my particular situation, the name of my device node is: /dev/bus/usb/001/063, so hence my command would be:
**udevadm info -q all -n /dev/bus/usb/001/063**

This gives output similar to the following:
$ udevadm info -q all -n /dev/bus/usb/001/063
P: /devices/pci0000:00/0000:00:1d.7/usb1/1-8
N: bus/usb/001/063
S: libmtp-1-8
S: GalaxyNexus
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-8
E: MAJOR=189
E: MINOR=62
E: DEVNAME=/dev/bus/usb/001/063
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=4e8/6860/216
E: TYPE=0/0/0
E: BUSNUM=001
E: DEVNUM=063
E: SUBSYSTEM=usb
E: ID_MTP_DEVICE=1
E: ID_MEDIA_PLAYER=samsung_galaxy-s2
E: ID_VENDOR=samsung
E: ID_VENDOR_ENC=samsung
E: ID_VENDOR_ID=04e8
E: ID_MODEL=Galaxy
E: ID_MODEL_ENC=Galaxy
E: ID_MODEL_ID=6860
E: ID_REVISION=0216
E: ID_SERIAL=samsung_Galaxy_0146B06501005018
E: ID_SERIAL_SHORT=0146B06501005018
E: ID_BUS=usb
E: ID_USB_INTERFACES=:ffff00:ff4201:
E: DEVLINKS=/dev/libmtp-1-8 /dev/GalaxyNexus
E: TAGS=:udev-acl:

Criteria that we will be using for matching are those lines starting with E: -  E=ENV=Device Property value


**Query Method #2**

```
udevadm info -a -p $(udevadm info -q path -n <name of device node>)
```
In my particular situation, the name of my device node is: /dev/bus/usb/001/063, so hence my command would be:
**udevadm info -a -p $(udevadm info -q path -n /dev/bus/usb/001/063)**

This command gives output similar to:

$ udevadm info -a -p $(udevadm info -q path -n /dev/bus/usb/001/063)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb1/1-8':
    KERNEL=="1-8"
    SUBSYSTEM=="usb"
    DRIVER=="usb"
    ATTR{configuration}==""
    ATTR{bNumInterfaces}==" 2"
    ATTR{bConfigurationValue}=="1"
    ATTR{bmAttributes}=="80"
    ATTR{bMaxPower}=="500mA"
    ATTR{urbnum}=="29"
    ATTR{idVendor}=="04e8"
    ATTR{idProduct}=="6860"
    ATTR{bcdDevice}=="0216"
    ATTR{bDeviceClass}=="00"
    ATTR{bDeviceSubClass}=="00"
    ATTR{bDeviceProtocol}=="00"
    ATTR{bNumConfigurations}=="1"
    ATTR{bMaxPacketSize0}=="64"
    ATTR{speed}=="480"
    ATTR{busnum}=="1"
    ATTR{devnum}=="63"
    ATTR{devpath}=="8"
    ATTR{version}==" 2.00"
    ATTR{maxchild}=="0"
    ATTR{quirks}=="0x0"
    ATTR{avoid_reset_quirk}=="0"
    ATTR{authorized}=="1"
    ATTR{manufacturer}=="samsung"
    ATTR{product}=="Galaxy"
    ATTR{serial}=="0146B06501005018"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="1403"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0300"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.0.0-14-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x27cc"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x3010"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

Criteria that we will be using for matching are those lines starting with ATTRS  -- ATTRS-Device Attributes

Using either ENV or ATTRS, we can construct a ruleset for udev. Full information how to construct rules can be found [**_here_**]("http://www.reactivated.net/writing_udev_rules.html#basic"), I'll provide examples on how to use the criteria to construct the ruleset.

By arbitrary convention, the ruleset file will be called 51-android.rules.
```
gksu gedit /etc/udev/rules.d/51-android.rules
```

The following are examples of rulesets that can be placed within the file (**only [SIZE="3"]one(1)[/SIZE] ruleset is needed** - Each should be only 1 line):
SUBSYSTEM=="usb", ENV{ID_VENDOR_ID}=="04e8", ENV{ID_MODEL}=="Galaxy", MODE="0666", SYMLINK+="GalaxyNexus"

SUBSYSTEM=="usb", ENV{ID_VENDOR_ID}=="04e8", ENV{ID_MODEL_ID}=="6860", MODE="0666", SYMLINK+="GalaxyNexus"

SUBSYSTEM=="usb", ATTR{idVendor}=="04e8", ATTR{idProduct}=="6860", ATTR{product}=="Galaxy" MODE="0666", SYMLINK+="GalaxyNexus"

As written above, these rules which listed matching criteria (SUBSYSTEM, ENV,ATTR) will only modify the mode of the device (0666=rw-rw-rw-) and create the symbolic GalaxyNexus link at /dev/GalaxyNexus. Additional actions however can be assigned to the device, such as activities to perform when the device is plugged in, or removed.  These activites could be specified as follows:
ACTION=="add", RUN+="<name of action>"
ACTION==”remove”, RUN+="<name of action>"

****IMPORTANT**** 
[LIST]
[*]Each ACTION statement must be listed on its own line. 
[*]The path to the program must be the full qualified path. 
[*]There may also be multiple action lines or multiple add/remove statements
[/LIST].

Example:
ACTION=="add", RUN+="/usr/local/bin/NexusMount.sh"
ACTION==”remove”, RUN+="/usr/local/bin/NexusUnmount.sh"

It would be possible for example to play a sound or .mp3 file when the device is inserted or ejected (similar to windows).

Once done constructing the rule, save the /etc/udev/rules.d/51-android.rules file.

**Testing the ruleset**
Its often a good idea to test the ruleset before executing it.  Its very easy to make errors writing the ruleset so I would encourage this simple process to verify the ruleset is correct.  This can be done using the udevadm tool.  

```
udevadm test --action=<"Copy entire ruleset here"> <path to device node>
```

The ruleset is the contents of the entire 51-android.rules file. 
The path to the device node can be discovered using: 
**udevadm info -q path -n d=<device name>**  
In the example above the name of my device was: /dev/bus/usb/001/063 (Which was discovered using the lsusb statement).

Putting this altogether as an example:
udevadm test --action="SUBSYSTEM=="usb", ENV{ID_VENDOR_ID}=="04e8", ENV{ID_MODEL}=="Galaxy" MODE="0666", SYMLINK+="GalaxyNexus"" $(udevadm info -q path -n /dev/bus/usb/001/063)

Although the output is rather long, two lines in the output correctly identify the ruleset actions are to be applied correctly:
udev_rules_apply_to_event: MODE 0666 /etc/udev/rules.d/51-android.rules:1
udev_rules_apply_to_event: LINK 'GalaxyNexus' /etc/udev/rules.d/51-android.rules:1

Once verifying the ruleset is correct, restart the udev service:
```
sudo service udev restart
```

[SIZE="3"]**4. Log out and then log back into computer.**[/SIZE]
With the device plugged in, adb should work similar to the following:
$ adb devices
List of devices attached 
0146B06501005018	device

fastboot can also be ran, however this is only valid if the device has booted into fastboot mode:
$ fastboot devices
????????????    fastboot

**[SIZE="2"]***References[/SIZE]**

---

### Post by Jonny87 on 2012-05-18
This is a great tutorial and so far so good, I am however stuck on one small little issue. I'm not sure what to put in the rule set for the "SYMLINK+="?

Here is my following out put information;
```
jonny@jonny-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 003: ID 04f3:0230 Elan Microelectronics Corp. 3D Optical Mouse
Bus 002 Device 004: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 002 Device 005: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 002 Device 006: ID 19d2:0112 ZTE WCDMA Technologies MSM 
```

```
jonny@jonny-laptop:~$ udevadm info -q all -n /dev/bus/usb/002/006
P: /devices/pci0000:00/0000:00:1d.7/usb2/2-3
N: bus/usb/002/006
E: BUSNUM=002
E: DEVNAME=/dev/bus/usb/002/006
E: DEVNUM=006
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-3
E: DEVTYPE=usb_device
E: DRIVER=usb
E: ID_BUS=usb
E: ID_MODEL=ZTE_HSUSB_Device
E: ID_MODEL_ENC=ZTE\x20HSUSB\x20Device
E: ID_MODEL_ID=0112
E: ID_REVISION=0100
E: ID_SERIAL=ZTE_Incorporated_ZTE_HSUSB_Device
E: ID_USB_INTERFACES=:ffffff:
E: ID_VENDOR=ZTE_Incorporated
E: ID_VENDOR_ENC=ZTE\x20Incorporated
E: ID_VENDOR_ID=19d2
E: MAJOR=189
E: MINOR=133
E: PRODUCT=19d2/112/100
E: SUBSYSTEM=usb
E: TYPE=0/0/0
E: UDEV_LOG=3
E: USEC_INITIALIZED=1783943325

```

```
jonny@jonny-laptop:~$ udevadm info -a -p $(udevadm info -q path -n /dev/bus/usb/002/006)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3':
    KERNEL=="2-3"
    SUBSYSTEM=="usb"
    DRIVER=="usb"
    ATTR{configuration}==""
    ATTR{bNumInterfaces}==" 1"
    ATTR{bConfigurationValue}=="1"
    ATTR{bmAttributes}=="a0"
    ATTR{bMaxPower}=="500mA"
    ATTR{urbnum}=="9"
    ATTR{idVendor}=="19d2"
    ATTR{idProduct}=="0112"
    ATTR{bcdDevice}=="0100"
    ATTR{bDeviceClass}=="00"
    ATTR{bDeviceSubClass}=="00"
    ATTR{bDeviceProtocol}=="00"
    ATTR{bNumConfigurations}=="1"
    ATTR{bMaxPacketSize0}=="64"
    ATTR{speed}=="480"
    ATTR{busnum}=="2"
    ATTR{devnum}=="6"
    ATTR{devpath}=="3"
    ATTR{version}==" 2.00"
    ATTR{maxchild}=="0"
    ATTR{quirks}=="0x0"
    ATTR{avoid_reset_quirk}=="0"
    ATTR{authorized}=="1"
    ATTR{manufacturer}=="ZTE Incorporated"
    ATTR{product}=="ZTE HSUSB Device"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="46"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0302"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.2.0-24-generic-pae ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2836"
    ATTRS{subsystem_vendor}=="0x1025"
    ATTRS{subsystem_device}=="0x0136"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""
    ATTRS{uframe_periodic_max}=="100"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

And so far this is what I have for my ruleset;
```
SUBSYSTEM=="usb", ENV{ID_VENDOR_ID}=="19d2", ENV{ID_MODEL}=="ZTE_HSUSB_Device", MODE="0666", SYMLINK+=" "

SUBSYSTEM=="usb", ENV{ID_VENDOR_ID}=="19d2", ENV{ID_MODEL_ID}=="0112", MODE="0666", SYMLINK+=" "

SUBSYSTEM=="usb", ATTR{idVendor}=="19d2", ATTR{idProduct}=="6860", ATTR{product}=="ZTE HSUSB Device"" MODE="0666", SYMLINK+=" "
```
 could someone please check over all of this and help me out? I really need to get this working so that I can attempted to fix my phone that is no longer working.

---

### Post by Jonny87 on 2012-05-19
OK I think I have it worked out but my phone still won't show in the adb devices.

Any help please?

---

### Post by rmjones85 on 2012-05-20
If you're trying to run adb from a shell why don't you just:
```
cd <android-sdk directory>
``````
cd platform-tools
``````
./adb kill-server
``````
./adb start-server
``````
./adb shell
```I you see a # sign then you're in.

---

### Post by Lisiano on 2012-05-20
Won't it be easier to just use the Vendor ID without the Model, Device ID and Symlink?

I use this 51-android.rules list and it works ideally for me.
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0409", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0471", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0482", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0489", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="04da", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="04dd", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="04e8", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0502", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="05c6", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="091e", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0930", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0955", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0b05", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0bb4", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0fce", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="1004", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="109b", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="10a9", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="12d1", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="17ef", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="18d1", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="19d2", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="1d4d", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="1f53", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="2080", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="2116", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="2207", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="2257", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="22b8", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="24e3", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="413c", MODE="0660", GROUP="plugdev"

```
Most IDs are taken from [here]("http://developer.android.com/guide/developing/device.html").

---

### Post by Jonny87 on 2012-05-21
> **rmjones85 said:**
> If you're trying to run adb from a shell why don't you just:
```
cd <android-sdk directory>
``````
cd platform-tools
``````
./adb kill-server
``````
./adb start-server
``````
./adb shell
```I you see a # sign then you're in.

"./adb shell" didn't work.

---

### Post by Jonny87 on 2012-05-21
> **Lisiano said:**
> Won't it be easier to just use the Vendor ID without the Model, Device ID and Symlink?

I use this 51-android.rules list and it works ideally for me.
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0409", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0471", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0482", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0489", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="04da", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="04dd", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="04e8", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0502", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="05c6", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="091e", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0930", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0955", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0b05", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0bb4", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0fce", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="1004", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="109b", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="10a9", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="12d1", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="17ef", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="18d1", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="19d2", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="1d4d", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="1f53", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="2080", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="2116", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="2207", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="2257", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="22b8", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="24e3", MODE="0660", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="413c", MODE="0660", GROUP="plugdev"

```
Most IDs are taken from [here]("http://developer.android.com/guide/developing/device.html").

Will give your method a try in case it works better. I still couldn't get it working on adb devices but managed to get it to sho up under fastboot. will try your method though.

---

### Post by kevdog on 2012-05-22
adb list-devices

This command should list your device attached. If no device is listed the adb shell command isn't going to work.  You should also ideally add the platform tools directory to your PATH statement.

Your SYMLINK+= statement can be anything. It just makes a symbolic link to the device at /dev/SYMLINK so it can be accessed. This is a symbolic link to the actual device node which is /dev/bus/usb/..... it's not a totally necessary however it just makes mounting easier.

---

### Post by darrenn on 2012-05-27
If my phone is stuck in fastboot mode will these commands work to fix it once I install adb?   

"**fast boot mode started udc_start()**" 

fastboot erase recovery

fastboot flash recovery recovery.img

fastboot reboot

---

### Post by PivotalEpiphany on 2012-05-28
> **darrenn said:**
> If my phone is stuck in fastboot mode will these commands work to fix it once I install adb?   

"**fast boot mode started udc_start()**" 

fastboot erase recovery

fastboot flash recovery recovery.img

fastboot reboot
[B]=====================================

[/B]I've successfully posted as:

[B]List of devices attached 
[/B](Shows Device Number)**    device**

[I]How would I go about updating the baseband of a phone from this point?
I'm using terminal, in hopes that I can simply[/I] _#push V20G_00.kdz_.
[CENTER](Note: *this was also posted in xda forums. Getting perspective from both Android and Linux Devs*.)
[/CENTER]

---

### Post by mmesantos1 on 2012-05-28
Very nice work thank you for sharing.

---

### Post by kevdog on 2012-05-28
> **PivotalEpiphany said:**
> [B]=====================================

[/B]I've successfully posted as:

[B]List of devices attached 
[/B](Shows Device Number)**    device**

[I]How would I go about updating the baseband of a phone from this point?
I'm using terminal, in hopes that I can simply[/I] _#push V20G_00.kdz_.
[CENTER](Note: *this was also posted in xda forums. Getting perspective from both Android and Linux Devs*.)
[/CENTER]

I thought the baseband was updated by *22899 or something similar to that.  I've never seen a file with a .kdz extension.

---

### Post by REAPtheWHIRLWIND on 2012-06-10
> **PivotalEpiphany said:**
> [B]=====================================

[/B]I've successfully posted as:

[B]List of devices attached 
[/B](Shows Device Number)**    device**

[I]How would I go about updating the baseband of a phone from this point?
I'm using terminal, in hopes that I can simply[/I] _#push V20G_00.kdz_.
[CENTER](Note: *this was also posted in xda forums. Getting perspective from both Android and Linux Devs*.)
[/CENTER]

**EXACTLY WHAT I WANT TO KNOW!!** I was able to get to the point where it showed my device information, and I can get the KDZ Updater to open with WINE, but "PHONE NOT FOUND"....

I've read through the GOOGLEs but never really found any way of doing this...

I suppose reading the man for adb could work, but it doesn't mention SPECIFICALLY ***kdz files..***

Have you any update on this?

The KEY for me, is getting the phone in a safe state to push the update. The KDZ Updater puts the device into emergency mode...but I wouldn't know how it's done from adb.

---

### Post by RomPirate on 2012-07-08
Thank you! Worked for me :D Now I can fix my phone.

---

### Post by atpat on 2012-10-11
At first the installation didn't work for me, then I found [this]("http://www.hackersgarage.com/adb-no-such-file-or-directory.html") which suggests installing ia32-libs...

---

### Post by Whoopie on 2012-10-11
Starting with Ubuntu Quantal, you can install the packages android-tools-adb and android-tools-fastboot.
This is interesting because you also get a native amd64 package.

---

### Post by ssj71 on 2012-11-02
Thanks for the tutorial. I actually just wimped out and didn't make the udev rule. Just go to the platform-tools folder in a terminal and run ```
./adb shell
``` or whichever adb command you want. Works better for me because I'm just doing a one time thing on a borrowed device.

---

### Post by lessless on 2013-01-21
can't get it working with htc vivid
here is my info:
> udevadm info -q all --path /sys/bus/usb/devices/2-3P: /devices/pci0000:00/0000:00:1d.7/usb2/2-3
N: bus/usb/002/023
E: BUSNUM=002
E: DEVNAME=/dev/bus/usb/002/023
E: DEVNUM=023
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-3
E: DEVTYPE=usb_device
E: DRIVER=usb
E: ID_BUS=usb
E: ID_MODEL=Android_1.0
E: ID_MODEL_ENC=Android\x201.0
E: ID_MODEL_ID=0ff0
E: ID_REVISION=0100
E: ID_SERIAL=htc__Inc_Android_1.0_HT1ASVJ25491
E: ID_SERIAL_SHORT=HT1ASVJ25491
E: ID_USB_INTERFACES=:ff4203:
E: ID_VENDOR=htc__Inc
E: ID_VENDOR_ENC=htc\x2c\x20Inc
E: ID_VENDOR_ID=0bb4
E: MAJOR=189
E: MINOR=150
E: PRODUCT=bb4/ff0/100
E: SUBSYSTEM=usb
E: TYPE=0/0/0
E: UDEV_LOG=3
E: USEC_INITIALIZED=2423343578


and command   udevadm test --action=SUBSYSTEM=="usb", ENV{ID_VENDOR_ID}=="0bb4",ENV{ID_MODEL_ID}=="0ff0", MODE="0666" gives me an error:
unable to open device '/sysENV{ID_VENDOR_ID}==0bb4,ENV{ID_MODEL_ID}==0ff0,'

please, help me with udev rule!

---

### Post by ProJerem on 2013-02-04
> **rmjones85 said:**
> If you're trying to run adb from a shell why don't you just:
```
cd <android-sdk directory>
``````
cd platform-tools
``````
./adb kill-server
``````
./adb start-server
``````
./adb shell
```I you see a # sign then you're in.

Looks easy, but I always receive an error - device not found


My Problem is, the device has NO NAME, if I send an lsusb command, I only receive for my android-device the line: 

Bus 001 Device 016: ID 2207:290a

and nothing more ... but every time I need to connect new, the Device-Number grows higher (first it was 005 ... now 016 ...)

How can I connect this device with NO NAME ???

The problem is, as device-name there is **nothing**, but can you help me, how I can connect **nothing** to use **nothing** with adb ... ???    :lolflag:

But I can not laugh about it, because this fu... android-tablet with no name cannot be found in adb, not with OS Ubuntu, nor under Windows :-(

Only with the RKBatchtool under Windows I can see it and I can flash the original Rom :-(

but I want to root it ............ can anybody help me with my EasyPix EasyPad EP750 ... its everything else than easy :-(


Don't know if my udev-rules work:   SUBSYSTEM=="usb", ENV{ID_VENDOR_ID}=="2207", ENV{ID_MODEL_ID}=="290a", MODE="0666"

---

### Post by mrcpuhead on 2014-01-24
I followed this process on my Ubuntu 12.04 LTS box, and when I try to run adb, I get the old "no such file or directory".  Permissions appear OK on adb (-rwxrwxr-x).  What gives?

---

### Post by New00Folder on 2014-02-02
If your Ubuntu is 64 bit, you'll need 32 bit compatibility libraries to run adb.

---

### Post by stefan16 on 2014-02-15
Hi there!

I am new to Android and adb. And I am so much of a linux-hacker, but using Ubuntu 12.04 LTS with pride. ;-)

I installed adb according to your description, but "adb devices" will not list any devices.

When I do a "ls -l /dev/<symlink_of_device>" I see, the symlink is pointing to the node it should according to "lsusb".

This happens with two different tablets.


Any suggestions, where to look for the mistake?

Many thanks in advance for helpfull answers!

Stefan

---

### Post by stefan16 on 2014-02-16
Another question came into my mind, tonight:

Do I need special software for adb on Android?

The debugging-option is activated on both tablets.

---

### Post by andrew103 on 2014-03-17
got an htc desire 300 that is stuck in boot logo. what can i do?

---

### Post by mrcpuhead on 2014-11-27
> **ProJerem said:**
> Looks easy, but I always receive an error - device not found


My Problem is, the device has NO NAME, if I send an lsusb command, I only receive for my android-device the line: 

Bus 001 Device 016: ID 2207:290a

and nothing more ... but every time I need to connect new, the Device-Number grows higher (first it was 005 ... now 016 ...)

How can I connect this device with NO NAME ???

The problem is, as device-name there is **nothing**, but can you help me, how I can connect **nothing** to use **nothing** with adb ... ???    :lolflag:

But I can not laugh about it, because this fu... android-tablet with no name cannot be found in adb, not with OS Ubuntu, nor under Windows :-(

Only with the RKBatchtool under Windows I can see it and I can flash the original Rom :-(

but I want to root it ............ can anybody help me with my EasyPix EasyPad EP750 ... its everything else than easy :-(


Don't know if my udev-rules work:   SUBSYSTEM=="usb", ENV{ID_VENDOR_ID}=="2207", ENV{ID_MODEL_ID}=="290a", MODE="0666"

That vendor id is same as my RCA RCT6378W2 tablet, and it appears the rules test worked, but "adb devices" comes back blank - no devices found.  Argh!  BTW, my tablet won't boot (stuck at flashing RCA logo) but will start in recovery mode.

---

### Post by kamhagh on 2014-12-05
why not a simple sudo apt-get install -android tools or something adb !

---

### Post by Brinstar on 2015-06-28
Only part that needs adding to the OP is that 

```
sudo udevadm trigger --action=change
```

should be run after adding the correct rules

---

### Post by wasia on 2015-11-17
One IMPORTANT remark.
Make sure that in [FONT=verdana][LEFT]~/.android there's an adb_usb.ini file. If not create one and add a line with your device vendor id.
In my case [FONT=verdana][LEFT]adb_usb.ini[/LEFT][/FONT] consist of one line:
0x2717
Do NOT forget about "0x" even if it's not displayed as a part of your phone's vendor id.
Without [FONT=verdana][LEFT]adb_usb.ini my list of devices was empty despite udev rule working perfectly.
[/LEFT][/FONT]
[/LEFT][/FONT]

---

### Post by Daniel_west on 2015-12-20
i keep getting an error message "cannot download, this feature isnt avaible on your phone" please help me

---

