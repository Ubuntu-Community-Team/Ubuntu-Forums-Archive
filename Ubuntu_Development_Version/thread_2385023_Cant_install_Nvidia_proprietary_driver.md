---
title: "Cant install Nvidia proprietary driver"
date: 2018-02-15
forum: Ubuntu Development Version
---

### Post by linuxyogi on 2018-02-15
Hi,

When I select the Nvidia proprietary driver and click apply it quick reverts to the Nouveau driver and nothing happens.

Any solutions ?

I am using Xubuntu 18.04.

---

### Post by dino99 on 2018-02-15
which driver are you talking about ? on which graphic chip ? what is the output when you (sudo apt-get install --reinstall xxxxx) into a terminal ? what are the journalctl errors about graphic ?

---

### Post by linuxyogi on 2018-02-15
> **dino99 said:**
> which driver are you talking about ? on which graphic chip ? what is the output when you (sudo apt-get install --reinstall xxxxx) into a terminal ? what are the journalctl errors about graphic ?

This is my hardware

```
 *-display                 
       description: VGA compatible controller
       product: GK107 [GeForce GTX 650]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:123 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff


```
I am  trying to install this driver but when I select the proprietary driver and click apply changes it reverts back to the open source driver and then nothing happens. 

[ATTACH=CONFIG]278531[/ATTACH]

---

### Post by dino99 on 2018-02-15
As your screenshot is showing 2 different nvidia drivers, purge them all, then install the one you need. I wonder if you 'sometime' do some system cleaning (clean/autoclean/autoremove), but you should.

---

### Post by linuxyogi on 2018-02-15
> **dino99 said:**
> As your screenshot is showing 2 different nvidia drivers, purge them all, then install the one you need. I wonder if you 'sometime' do some system cleaning (clean/autoclean/autoremove), but you should.

I haven't installed any **proprietary **driver. This is almost a fresh install. Also, I do autoremove quite often.

---

### Post by dino99 on 2018-02-15
then, what is the output of:

sudo apt-get install --reinstall xxxxx

---

### Post by linuxyogi on 2018-02-15
> **dino99 said:**
> then, what is the output of:

sudo apt-get install --reinstall xxxxx


Sorry but what exactly is "xxxxx" ?

---

### Post by mc4man on 2018-02-15
> **linuxyogi said:**
> Sorry but what exactly is "xxxxx" ?

Basically just replace xxx with driver. do this instead

```
sudo apt purge nvidia*

```
```
sudo apt update
```

When those finish,
```
sudo apt install nvidia-384
```

Keep the terminal open & read back thru, look for errors.
If desired copy *complete* terminal out & post.

---

### Post by linuxyogi on 2018-02-16
> **mc4man said:**
> Basically just replace xxx with driver. do this instead

```
sudo apt purge nvidia*

```
```
sudo apt update
```

When those finish,
```
sudo apt install nvidia-384
```

Keep the terminal open & read back thru, look for errors.
If desired copy *complete* terminal out & post.

```
$ sudo apt purge nvidia*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-325-updates' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-binary' for glob 'nvidia*'
Note, selecting 'nvidia-331-dev' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-384-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-384-updates' for glob 'nvidia*'
Note, selecting 'nvidia' for glob 'nvidia*'
Note, selecting 'nvidia-driver' for glob 'nvidia*'
Note, selecting 'nvidia-367-updates' for glob 'nvidia*'
Note, selecting 'nvidia-modprobe' for glob 'nvidia*'
Note, selecting 'nvidia-texture-tools' for glob 'nvidia*'
Note, selecting 'nvidia-387-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-349-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-310-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-dev' for glob 'nvidia*'
Note, selecting 'nvidia-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-346-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-smi' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-313-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-334-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-prime' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-dev' for glob 'nvidia*'
Note, selecting 'nvidia-nsight' for glob 'nvidia*'
Note, selecting 'nvidia-common' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-current-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-355-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs-nonglvnd' for glob 'nvidia*'
Note, selecting 'nvidia-375-dev' for glob 'nvidia*'
Note, selecting 'nvidia-current' for glob 'nvidia*'
Note, selecting 'nvidia-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-375-updates' for glob 'nvidia*'
Note, selecting 'nvidia-337-updates' for glob 'nvidia*'
Note, selecting 'nvidia-358-updates' for glob 'nvidia*'
Note, selecting 'nvidia-367-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs' for glob 'nvidia*'
Note, selecting 'nvidia-378-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-319-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-dev' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-visual-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-persistenced' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-361-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings-binary' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-367' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-375' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-384' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-doc' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-dev' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-cg-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cg-doc' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-381-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-367' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-375' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-gdb' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-310' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-313' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-319' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-325' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-331' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-334' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-337' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-340' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-343' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-346' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-349' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-352' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-355' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-358' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304-dev' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-361' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-364' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-367' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-375' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-378' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-381' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-387' for glob 'nvidia*'
Note, selecting 'nvidia-343-updates' for glob 'nvidia*'
Note, selecting 'nvidia-364-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304' for glob 'nvidia*'
Note, selecting 'nvidia-310' for glob 'nvidia*'
Note, selecting 'nvidia-313' for glob 'nvidia*'
Note, selecting 'nvidia-319' for glob 'nvidia*'
Note, selecting 'nvidia-325' for glob 'nvidia*'
Note, selecting 'nvidia-331' for glob 'nvidia*'
Note, selecting 'nvidia-334' for glob 'nvidia*'
Note, selecting 'nvidia-337' for glob 'nvidia*'
Note, selecting 'nvidia-340' for glob 'nvidia*'
Note, selecting 'nvidia-343' for glob 'nvidia*'
Note, selecting 'nvidia-346' for glob 'nvidia*'
Note, selecting 'nvidia-349' for glob 'nvidia*'
Note, selecting 'nvidia-352' for glob 'nvidia*'
Note, selecting 'nvidia-355' for glob 'nvidia*'
Note, selecting 'nvidia-358' for glob 'nvidia*'
Note, selecting 'nvidia-361' for glob 'nvidia*'
Note, selecting 'nvidia-364' for glob 'nvidia*'
Note, selecting 'nvidia-367' for glob 'nvidia*'
Note, selecting 'nvidia-375' for glob 'nvidia*'
Note, selecting 'nvidia-378' for glob 'nvidia*'
Note, selecting 'nvidia-381' for glob 'nvidia*'
Note, selecting 'nvidia-384' for glob 'nvidia*'
Note, selecting 'nvidia-387' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for glob 'nvidia*'
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-vdpau-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-vdpau-driver' is not installed, so not removed
Note, selecting 'nvidia-384' instead of 'nvidia-smi'
Package 'nvidia-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-driver' is not installed, so not removed
Package 'nvidia-legacy-304xx-driver' is not installed, so not removed
Package 'nvidia-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-340xx-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-304xx-kernel-dkms' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-367-updates' is not installed, so not removed
Package 'nvidia-experimental-367' is not installed, so not removed
Package 'nvidia-375-updates' is not installed, so not removed
Package 'nvidia-experimental-375' is not installed, so not removed
Package 'nvidia-378' is not installed, so not removed
Package 'nvidia-378-updates' is not installed, so not removed
Package 'nvidia-experimental-378' is not installed, so not removed
Package 'nvidia-381' is not installed, so not removed
Package 'nvidia-381-updates' is not installed, so not removed
Package 'nvidia-experimental-381' is not installed, so not removed
Package 'nvidia-384-updates' is not installed, so not removed
Package 'nvidia-experimental-384' is not installed, so not removed
Package 'nvidia-387' is not installed, so not removed
Package 'nvidia-387-updates' is not installed, so not removed
Package 'nvidia-experimental-387' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-driver-libs' is not installed, so not removed
Package 'nvidia-driver-libs-nonglvnd' is not installed, so not removed
Package 'nvidia-prime' is not installed, so not removed
Package 'nvidia-settings' is not installed, so not removed
Package 'nvidia-304' is not installed, so not removed
Package 'nvidia-304-dev' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-304-updates-dev' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-dev' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-331-updates-dev' is not installed, so not removed
Package 'nvidia-331-updates-uvm' is not installed, so not removed
Package 'nvidia-331-uvm' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-340-updates-dev' is not installed, so not removed
Package 'nvidia-340-updates-uvm' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-dev' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-346-updates-dev' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-dev' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-352-updates-dev' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-361-dev' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-361-updates-dev' is not installed, so not removed
Package 'nvidia-367' is not installed, so not removed
Package 'nvidia-367-dev' is not installed, so not removed
Package 'nvidia-375' is not installed, so not removed
Package 'nvidia-375-dev' is not installed, so not removed
Package 'nvidia-384' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-dev' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-current-updates-dev' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-experimental-304-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-304' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-libopencl1-304' is not installed, so not removed
Package 'nvidia-libopencl1-304-updates' is not installed, so not removed
Package 'nvidia-libopencl1-331' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-libopencl1-340-updates' is not installed, so not removed
Package 'nvidia-libopencl1-346' is not installed, so not removed
Package 'nvidia-libopencl1-346-updates' is not installed, so not removed
Package 'nvidia-libopencl1-352' is not installed, so not removed
Package 'nvidia-libopencl1-352-updates' is not installed, so not removed
Package 'nvidia-libopencl1-361' is not installed, so not removed
Package 'nvidia-libopencl1-361-updates' is not installed, so not removed
Package 'nvidia-libopencl1-367' is not installed, so not removed
Package 'nvidia-libopencl1-375' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-304-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-331' is not installed, so not removed
Package 'nvidia-opencl-icd-331-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-340-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-346' is not installed, so not removed
Package 'nvidia-opencl-icd-346-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-352' is not installed, so not removed
Package 'nvidia-opencl-icd-352-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-361' is not installed, so not removed
Package 'nvidia-opencl-icd-361-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-367' is not installed, so not removed
Package 'nvidia-opencl-icd-375' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.


```

```
$ sudo apt update
Get:1 http://archive.ubuntu.com/ubuntu bionic InRelease [235 kB]
Hit:2 http://APT.spideroak.com/ubuntu-spideroak-hardy release InRelease
Hit:3 http://archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:4 http://archive.ubuntu.com/ubuntu bionic-backports InRelease
Hit:5 http://archive.ubuntu.com/ubuntu bionic-security InRelease
Get:6 http://archive.ubuntu.com/ubuntu bionic-proposed InRelease [235 kB]
Get:7 http://archive.ubuntu.com/ubuntu bionic/main amd64 DEP-11 Metadata [455 kB]
Get:8 http://archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64 Icons [254 kB]
Get:9 http://archive.ubuntu.com/ubuntu bionic/universe amd64 DEP-11 Metadata [2,955 kB]
Get:10 http://archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64 Icons [8,173 kB]              
Get:11 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 DEP-11 Metadata [40.7 kB]          
Get:12 http://archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64 Icons [204 kB]              
Get:13 http://archive.ubuntu.com/ubuntu bionic-proposed/universe amd64 DEP-11 Metadata [112 kB]    
Get:14 http://archive.ubuntu.com/ubuntu bionic-proposed/universe DEP-11 64x64 Icons [110 kB]       
Get:15 http://archive.ubuntu.com/ubuntu bionic-proposed/main amd64 DEP-11 Metadata [168 kB]        
Get:16 http://archive.ubuntu.com/ubuntu bionic-proposed/main DEP-11 64x64 Icons [61.4 kB]          
Fetched 13.0 MB in 28s (463 kB/s)                                                                  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
49 packages can be upgraded. Run 'apt list --upgradable' to see them.
```


```
$ sudo apt install nvidia-384
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-384 : Depends: lib32gcc1 but it is not going to be installed
              Depends: libc6-i386 but it is not going to be installed
              Depends: libgl1
              Depends: xorg-video-abi-11 but it is not installable or
                       xorg-video-abi-12 but it is not installable or
                       xorg-video-abi-13 but it is not installable or
                       xorg-video-abi-14 but it is not installable or
                       xorg-video-abi-15 but it is not installable or
                       xorg-video-abi-18 but it is not installable or
                       xorg-video-abi-19 but it is not installable or
                       xorg-video-abi-20 but it is not installable or
                       xorg-video-abi-23
              Depends: xserver-xorg-core but it is not going to be installed
              Recommends: nvidia-settings (>= 331.20) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by dino99 on 2018-02-16
Is your sig uptodate ? because it seems your graphic is 'Intel'. So why do you think installing 'nvidia' will help and appropriate ? :confused:

---

### Post by linuxyogi on 2018-02-16
> **dino99 said:**
> Is your sig uptodate ? because it seems your graphic is 'Intel'. So why do you think installing 'nvidia' will help and appropriate ? :confused:

Sorry for the confusion. I have modified my signature.

---

### Post by dino99 on 2018-02-16
Is your install a 64 bits ?  [https://askubuntu.com/questions/41332/how-do-i-check-if-i-have-a-32-bit-or-a-64-bit-os](https://askubuntu.com/questions/41332/how-do-i-check-if-i-have-a-32-bit-or-a-64-bit-os)

---

### Post by linuxyogi on 2018-02-16
> **dino99 said:**
> Is your install a 64 bits ?  [https://askubuntu.com/questions/41332/how-do-i-check-if-i-have-a-32-bit-or-a-64-bit-os](https://askubuntu.com/questions/41332/how-do-i-check-if-i-have-a-32-bit-or-a-64-bit-os)

```
$  uname -i
x86_64 
```

Yes its 64 bits.

---

### Post by dino99 on 2018-02-16
hm, i'm missing some fresh ideas ;)
is 'proposed' archive activated ? Which errors are exposed into 'journalctl -b' ? (focus on 'red' words line)

---

### Post by linuxyogi on 2018-02-16
> **dino99 said:**
> hm, i'm missing some fresh ideas ;)
is 'proposed' archive activated ? Which errors are exposed into 'journalctl -b' ? (focus on 'red' words line)

Yes proposed is enabled. 

This is the output of journalctl -b

[https://paste2.org/BALLfcAX](https://paste2.org/BALLfcAX)

---

### Post by dino99 on 2018-02-16
Well, the log is clean at first glance.
To resume:
- cpu is : i3 with hd530 igpu (can works via xserver-xorg-video-intel)
- graphic card gtx650: does not know how they works together (the card needs some cpu power)

Does not know neither how i3 support hardware acceleration (mainly required by games, but not much elsewhere); so intel video seems the best choice for classic use.

If you want/need the nvidia driver installed, you also need 'dkms' 'linux-libc-dev' & the 2 kernel's headers installed first.
[https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu](https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu)
[https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux)

---

### Post by mc4man on 2018-02-16
Having -proposed enabled during dev is a poor idea unless used for a specific upgrade.
In this case you won't be able to install nvidia drivers with the -proposed mesa libs which may also spill over to xserver.

---

### Post by linuxyogi on 2018-02-16
I got really frustrated with 18.04 and installed 16.04.

---

### Post by #&amp;thj^% on 2018-02-16
> **mc4man said:**
> with the -proposed mesa libs which may also spill over to xserver.
+1
It makes a mess out of your system:(

---

### Post by wangji on 2018-07-03
bionic selects automatically nvidia-390 even if you had chosen nvidia-384

There seems to be missing info about proprietary stuffs ; Let me clarify. When you test nvidia graphic using a benchmark like glxsheres64 ( or geek3D GpuTest ) it can use the nvidia card in 2 ways

  1  it fully uses nvidia proprietary libraries including OpenGL stuffs  .This is the case for nvidia-384  on ubuntu xenial 16.04  .It does give the fastest rendering performance

  2  It uses nvidia.ko module but for all OpenGL libraries it uses free OpenGL, not that ones compiled by nvidia company . The rendering performance is lower but still far better than with intel integrated graphic card .

  It seems to me that ubuntu's nvidia-390 package only allow the 2nd case at least for graphic rendering ( since cuda is fully nvidia 's libraries computation won't be affected )

   In any case 

Here is a live iso xubuntu-bionic with nvidia-390.48 and prime from MathieuGras-TimRichardson

It switched correctly on live testing with Acer VN7 laptop 4GB

[https://sourceforge.net/projects/toysbox/files/bionic-nvidia/xubuntu-18.04-4.15.0-24-nvidia.iso](https://sourceforge.net/projects/toysbox/files/bionic-nvidia/xubuntu-18.04-4.15.0-24-nvidia.iso)

  Screenshots + Logs are on the site

 xubuntu@xubuntu:~$ cat /proc/cmdline BOOT_IMAGE=(loop)/casper/vmlinuz iso-scan/filename=/iso/xubuntu-18.04-4.15.0-24-nvidia0.iso file=/cdrom/preseed/xubuntu.seed waitusb=5 boot=casper

xubuntu@xubuntu:~$ uname -a
Linux xubuntu 4.15.0-24-generic #26-Ubuntu SMP Wed Jun 13 08:44:47 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

xubuntu@xubuntu:~$ inxi -G
Graphics:
Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
Card-2: NVIDIA GM107M [GeForce GTX 860M]
Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting,nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1920x1080@60.02hz
OpenGL: renderer: GeForce GTX 860M/PCIe/SSE2 version: 4.6.0 NVIDIA 390.48

xubuntu@xubuntu:~$ xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x23a cap: 0x1, Source Output crtcs: 0 outputs: 0 associated providers: 1 name:NVIDIA-0
Provider 1: id: 0x44 cap: 0x6, Sink Output, Source Offload crtcs: 3 outputs: 2 associated providers: 1 name:modesetting

xubuntu@xubuntu:~$ glxinfo | grep NVIDIA
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation OpenGL core profile version string: 4.6.0 NVIDIA 390.48 OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL version string: 4.6.0 NVIDIA 390.48
OpenGL shading language version string: 4.60 NVIDIA
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 390.48

xubuntu@xubuntu:~$ glxgears
Running synchronized to the vertical refresh. The framerate should be approximately the same as the monitor refresh rate.
 69297 frames in 5.0 seconds = 13859.334 FPS
 68090 frames in 5.0 seconds = 13617.823 FPS

xubuntu@xubuntu:~$ glxspheres64 Polygons in scene: 62464 (61 spheres * 1024 polys/spheres) Visual ID of window: 0xa8 Context is Direct OpenGL Renderer: GeForce GTX 860M/PCIe/SSE2
1914.953887 frames/sec - 2137.088538 Mpixels/sec
1964.035952 frames/sec - 2191.864122 Mpixels/sec


   happy testing

---

### Post by cariboo on 2018-07-03
Bionic has been released, we are now testing Cosmic. Thread closed.

---

