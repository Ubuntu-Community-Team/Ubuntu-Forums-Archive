---
title: "Howto: Ralink RT2860 (m)PCI(e) (RT2760/RT2790/RT2860/RT2890) on Intrepid"
date: 2009-01-20
forum: Tutorials
---

### Post by Fass on 2009-01-20
This is a tutorial for getting Ralink's RT2760/RT2790/RT2860/RT2890-based (m)PCI(e) cards running on Intrepid with the latest Linux drivers provided on Ralink's website. You will need a wired connection to download the pertinent files.

First you are going to need the driver package, which can be downloaded from: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

You are looking for the "RT2860PCI/mPCI/PCIe/CB(RT2760/RT2790/RT2860/RT2890)" package. Download it and save it to your home directory.

Start a terminal and install the build-essential and linux-headers packages (if you don't have them already):

```
sudo aptitude install linux-headers-`uname -r` build-essential
```

Now, in your home folder untar the Ralink package:

```
tar -xvjf 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2
```

Edit the 2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/config.mk file to allow network-manager to manage the card:

```
gedit 2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/config.mk
```

Where it says:

> # Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Manager
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Make sure that both lines have a "y" after them (by default they have an "n"), then save the file.

Now enter the 2008_0918_RT2860_Linux_STA_v1.8.0.0 directory, compile and install the driver as root:

```
cd 2008_0918_RT2860_Linux_STA_v1.8.0.0/
sudo su
make && make install
```

It is important here not to use "sudo" alone, but "sudo su" because with sudo for some reason the installation script fails to create the necessary files and folders in among others /etc. This is what caused me some trouble before I figured it out.

Now, while still root modprobe the driver module:

```
modprobe rt2860sta
```

Give it a minute to create the ra0 device node, and network manager should now be able to display all visible wireless networks in your area, meanwhile you can stop being root and make sure that the module was probed correctly by checking the output of lsmod looking for the rt2860sta module.

```
exit
lsmod | grep rt2860sta
```

It should output something like "rt2860sta 525400  1". To make sure that ra0 is up and running as it's supposed to you can run "iwconfig" which should output something like this:

```
iwconfig 
lo        no wireless extensions.

eth1      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point:   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-29 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` 

Hopefully all of this worked and your wireless card is now functional. Use network manager to set your WEP/WPA(2) or what have you and connect to your network. 

To make sure the module is loaded when you reboot, add it to the /etc/modules file:

```
sudo echo rt2860sta >> /etc/modules
```

Hopefully this will be of service to someone. :)

---

### Post by use_of_weapons on 2009-01-24
Thanks a ton! Works perfectly. I just installed Intrepid today and the wireless chip didn't show up in ifconfig or iwconfig. If the box didn't come with windows I wouldn't even know what chipset it was.

---

### Post by metlhead05 on 2009-01-25
Every time that I try to install these drivers I get

```
make -C tools
make[1]: Entering directory `/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/tools'
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.o
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_giwscan’:
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: error: too few arguments to function ‘iwe_stream_add_event’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: error: too few arguments to function ‘iwe_stream_add_event’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: error: too few arguments to function ‘iwe_stream_add_point’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: error: too few arguments to function ‘iwe_stream_add_event’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: error: too few arguments to function ‘iwe_stream_add_event’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: error: too few arguments to function ‘iwe_stream_add_event’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: error: too few arguments to function ‘iwe_stream_add_point’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: error: too few arguments to function ‘iwe_stream_add_value’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: error: too few arguments to function ‘iwe_stream_add_point’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: error: too few arguments to function ‘iwe_stream_add_point’
make[2]: *** [/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.o] Error 1
make[1]: *** [_module_/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [LINUX] Error 2
root@Sweetums:/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0# 



```

I'm running Xubuntu 8.10 fully updated.

```
patrick@Sweetums:~$ lspci | grep  -i network
02:00.0 Network controller: RaLink RT2800 802.11n PCI
patrick@Sweetums:~$ 

```

Any help would be appreciated!

---

### Post by benedictducky on 2009-01-30
I Created an account to thank you :)

I didn't see this particular line of code in all the other forum i've read: modprobe rt2860sta

Wireless Worked perfectly after running that command at the full N Speeds too!  VERY Happy

My Wireless card is a ASUS WL-130N  With a rt2860 chipset (Written in other places with a rt2800 but it's incorrect confirmed by it working and by RA-Link)  

Finally Thank you Tass! It's saved me hours of messing about with it. :)

---

### Post by benedictducky on 2009-01-31
> **metlhead05 said:**
> Every time that I try to install these drivers I get

```
make -C tools
make[1]: Entering directory `/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/tools'
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.o
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_giwscan’:
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: error: too few arguments to function ‘iwe_stream_add_event’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: error: too few arguments to function ‘iwe_stream_add_event’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: error: too few arguments to function ‘iwe_stream_add_point’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: error: too few arguments to function ‘iwe_stream_add_event’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: error: too few arguments to function ‘iwe_stream_add_event’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: error: too few arguments to function ‘iwe_stream_add_event’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: error: too few arguments to function ‘iwe_stream_add_point’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: error: too few arguments to function ‘iwe_stream_add_value’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: error: too few arguments to function ‘iwe_stream_add_point’
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: error: too few arguments to function ‘iwe_stream_add_point’
make[2]: *** [/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.o] Error 1
make[1]: *** [_module_/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [LINUX] Error 2
root@Sweetums:/home/patrick/Desktop/2008_1225_RT3070_Linux_STA_v2.0.1.0# 



```

I'm running Xubuntu 8.10 fully updated.

```
patrick@Sweetums:~$ lspci | grep  -i network
02:00.0 Network controller: RaLink RT2800 802.11n PCI
patrick@Sweetums:~$ 

```

Any help would be appreciated!

Just a guess.  But the driver package you are trying to install is actually the wrong one for the card. Your trying to install a RT3070 driver when you should be trying to install a RT2860 Driver...?

---

### Post by metlhead05 on 2009-01-31
> **benedictducky said:**
> Just a guess.  But the driver package you are trying to install is actually the wrong one for the card. Your trying to install a RT3070 driver when you should be trying to install a RT2860 Driver...?

you are 100% right, I must have clicked the wrong link. Thanks!

---

### Post by InfinityCircuit on 2009-01-31
Am I missing something? Does the upstream Debian source not work?

```
aptitude install module-assistant
wget -c ftp://ftp.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb
dpkg -i rt2860-source_1.8.0.0-3_all.deb
m-a a-i rt2860
```

---

### Post by benedictducky on 2009-02-08
> **InfinityCircuit said:**
> Am I missing something? Does the upstream Debian source not work?

```
aptitude install module-assistant
wget -c ftp://ftp.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb
dpkg -i rt2860-source_1.8.0.0-3_all.deb
m-a a-i rt2860
```

Your telling me i went through all that and there's a complied version.  Aww....Sad :(

---

### Post by grumpyglenn on 2009-02-21
Thankyou or Mahalo as we say in Hawaii!

Your instructions worked on my new Asus eee box PC which came with a very limited version of Linux on it. I got a ziped version of the tar file from the RT site. So had to figure how to get it out.  I am over 70 so I am not good with all these commands. But after a lot of cd commands I did it!  The networkmanger informed me that it was connecting to my router.  I am running Umbuntu 8.10 which I got at the book store as a magazine by that name. After the updates and trying to download other networking programs I also got my um175 Verizon cellular modem to work.  I very much appreciate all you help in getting this going.

Grumpy

---

### Post by tomtheguvnor on 2009-02-22
Great post - worked first time. Thanks.

---

### Post by autocrosser on 2009-02-22
Just so everyone knows--in Jaunty, the ralink drivers are compiled in--so things like this will no longer be needed......I'm on the current testing Jaunty & worked with the kernel team to get the drivers included.....

---

### Post by InfinityCircuit on 2009-02-23
rt2860sta is also mainlined in vanilla 2.6.29 now.

---

### Post by PimPamPum on 2009-03-01
Hi ppl, i'm having a problem, when i do the make command i get this :



make
make -C tools
make[1]: Entering directory `/home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools'
/home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.o
/home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.c: In function ‘rt_ieee80211_if_setup’:
/home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.c:672: error: ‘struct net_device’ has no member named ‘nd_net’
make[2]: *** [/home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.o] Error 1
make[1]: *** [_module_/home/einar/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [LINUX] Error 2


I dont understand what is this, can anyone help ?

---

### Post by koriande on 2009-03-12
for RT2860, RT2760 there is a .deb package here:
[INDENT][https://launchpad.net/%7Estgraber/+archive/ppa/+files/rt2860-source_1.8.0.0-0ubuntu1~ppa2_all.deb]("https://launchpad.net/%7Estgraber/+archive/ppa/+files/rt2860-source_1.8.0.0-0ubuntu1~ppa2_all.deb")[/INDENT]

more information (in German):[INDENT][http://wiki.ubuntuusers.de/WLAN/Ralink]("http://wiki.ubuntuusers.de/WLAN/Ralink")[/INDENT]

or detailed description (in German):[INDENT][http://forum.ubuntuusers.de/topic/wlan-mit-zepto-notebook-zpro2-karte/]("http://forum.ubuntuusers.de/topic/wlan-mit-zepto-notebook-zpro2-karte/")[/INDENT]

---

### Post by Akita on 2009-03-28
> **autocrosser said:**
> Just so everyone knows--in Jaunty, the ralink drivers are compiled in--so things like this will no longer be needed......I'm on the current testing Jaunty & worked with the kernel team to get the drivers included.....

Great, too bad they don't work. At least not with WPA/WPA2. I just upgraded from Intrepid to Jaunty and although I can "see" wireless networks, the connection fails.

*sigh*

It's always RALink and something is always broken. I'm to the point where I'll go out of my way to buy anything from anybody else (even Broadcom's proprietary crap that at least WORKS .. without needing 2 years of continuous screwing around).

Sorry, my frustration at YetAgain<tm> having to dig up a solution to a problem that was fixed, then wasn't, then was (for some), then wasn't .. ad nauseum is peaking out.

---

### Post by autocrosser on 2009-03-29
> **Akita said:**
> Great, too bad they don't work. At least not with WPA/WPA2. I just upgraded from Intrepid to Jaunty and although I can "see" wireless networks, the connection fails.

*sigh*

It's always RALink and something is always broken. I'm to the point where I'll go out of my way to buy anything from anybody else (even Broadcom's proprietary crap that at least WORKS .. without needing 2 years of continuous screwing around).

Sorry, my frustration at YetAgain<tm> having to dig up a solution to a problem that was fixed, then wasn't, then was (for some), then wasn't .. ad nauseum is peaking out.


Well--I'm using the driver in Jaunty & it works very well...I did make a /etc/Wireless/RT2860  with a modified .dat in it & I use WPA2.

The .dat is the one that came stock with the driver & I did as recommended---add the bit in /etc & edited the .dat for what I wanted---the info you need is in the Driver Info.tar I posted--I'll post the mod .dat if you want also....it's for N networks only, but it only takes a bit of modifying to work with B & G too...

---

### Post by Akita on 2009-03-29
Thanks autocrosser, I'll give it a try. 

If you've followed the last year's saga on launchpad you'll notice that the dat file should not be needed. And what ever happened to "It just works" .. I can't see your average Joe Blow screwing around with a cryptic config file.

FYI I nuked the kernel module on one of my broken machines and replaced it with Adam McDaniel's 1.7.1.1 DKMS module and WPA/WPA2 work without the dat just like they did before some (expletive deleted) decided to ship a broken-yet-again one. So it SHOULDN'T be needed if somebody upstream would actually leave the fixes in the code and/or regresssion test before shipping his latest cool idea.

Sorry, but this driver has over a year of screwing around behind it, and I've lost count of the times somebody has "upgraded" it and left out a fix or re-broken something. Somebody should be really ashamed that this junk is what got shipped when there was a working version.

---

### Post by jeffdp78 on 2009-04-14
Hi there!

Just want to share that this procedure works ***flawlessly*** on my [B][U]ENLWI-N
802.11n Wireless PCI Adapter[/U][/B]

[IMG]http://i41.tinypic.com/2ed8sgm.jpg[/IMG]

[http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_2&pid=269]("http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_2&pid=269")


I'm using **linux-headers-386 meta package** ...just the same anyway ;)

```
$ sudo apt-get install linux-headers-386
$ sudo apt-get install build-essential
```

**driver: **[2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2]("http://www.ralinktech.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2")

[IMG]http://i43.tinypic.com/9iye7q.jpg[/IMG]

...

[IMG]http://i40.tinypic.com/aynhut.jpg[/IMG]

...

[IMG]http://i39.tinypic.com/2j1nzme.jpg[/IMG]

Thanks a lot! :KS

Xubuntu/8.10 (intrepid)
Pentium4 HT

---

### Post by wangsuda on 2009-04-14
You can also try this installation procedure:

[https://bugs.launchpad.net/linux/+bug/210725/comments/152](https://bugs.launchpad.net/linux/+bug/210725/comments/152)

- Download rt2860-source_1.8.0.0-3_all.deb from

[http://packages.debian.org/sid/all/rt2860-source/download](http://packages.debian.org/sid/all/rt2860-source/download)

wget [http://http.us.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb](http://http.us.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb)

- install source .deb:

sudo dpkg -i rt2860-source_1.8.0.0-3_all.deb

- compile
sudo aptitude install debhelper module-assistant
sudo module-assistant auto-install rt2860

- install the module
sudo modprobe rt2860sta
this should activate the new wireless interface without reboot

- to load the module automatically on each reboot, add rt2860sta to /etc/modules

sudo gedit /etc/modules

- add the following line to the end of the /etc/modules file:
rt2860sta

- reboot and retest wireless

---

### Post by skovy on 2009-04-22
> **Fass said:**
> This is a tutorial for getting Ralink's RT2760/RT2790/RT2860/RT2890-based (m)PCI(e) cards running on Intrepid with the latest Linux drivers provided on Ralink's website. You will need a wired connection to download the pertinent files.

First you are going to need the driver package, which can be downloaded from: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

You are looking for the "RT2860PCI/mPCI/PCIe/CB(RT2760/RT2790/RT2860/RT2890)" package. Download it and save it to your home directory.

Start a terminal and install the build-essential and linux-headers packages (if you don't have them already):

```
sudo aptitude install linux-headers-`uname -r` build-essential
```

Now, in your home folder untar the Ralink package:

```
tar -xvjf 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2
```

Edit the 2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/config.mk file to allow network-manager to manage the card:


ok i have a few questions, as i am new to ubuntu, and already feel over my head, i have gotten this far but it opened a new window that is blank, called [*config.mk , what should i do to this window?  i have tried to put the codes down with edits to the newest driver name, but nothing seems to work right.

i am using jaunty, if that means anything

---

### Post by Surge1337 on 2009-07-12
Linksys wmp110 pcicard

Thank you, worked perfectly.

---

### Post by iClouseau88 on 2010-02-02
Hello everyone,

This works perfectly and easily with the latest Linux driver version 2.3.0.0 dated January 29, 2010 from Ralink site. I replaced Netgear WN511T with Airlink101 AWLC6080 PCMCIA wireless adapter to work in my triple-boot laptop. 

I am wondering if I can use it for openSUSE 11.2 on my triple-boot XP Pro/Karmic/openSUSE Toshiba laptop, ie. copying over instead of building and compiling driver from source again, because I don't quite understand the build instruction given in the README file of Ralink's Linux driver file. Specifically, I don't know how to "define the GCC and LD (?) of the target machine, and define the compiler flags CFLAGS(?), modify your need (?)", etc. I already have gcc, cpp and make installed on the Ubuntu and openSUSE parts of my machine. 

I did try ndiswrapper but it doesn't work for the Windows version of the latest Ralink driver (error: invalid driver rt2860.inf).

Look forward to your suggestions, and thanks in advance.

---

### Post by thumphri on 2010-02-22
Thanks for this guide. It worked instantly first time.

---

### Post by alliance1975 on 2010-03-05
Thank you for the guide. Are there any required modifications for installation on Karmic 9.10. I will be installing a Sparklan WMIR-215GN w/RT2860 wireless nic into a HPdv5000 laptop. The 2010_01_29_RT2860_Linux_STA_v2.3.0.0 README_STA suggests additional configuration steps not included in this guide. Has anyone tested on Karmic?

---

### Post by iClouseau88 on 2010-03-06
Hi,
I just installed Ralink's RT2860STA driver on my Ubuntu Karmic pc and wireless works fine. You just need to change the 2 lines that have WPA SUPPLICANT in config.mk from "n" (NO) to "y" (YES) then save the file.  Ignore the suggestions in the README file.

---

### Post by alliance1975 on 2010-03-06
Regrettably, my attempt to install the SparkLan Wmir-215gn wireless N card with the Railink rt2860 chip was a complete failure. i tried installing the card first with the intention of installing the drivers when powered up and the card refused to be recognized. A blue screen of death appeared with a text block explaining that an unsupported wireless network device was installed and further action was halted. remove the device and restart. I installed th eold card and proceeded to install the drivers thinking that would cure it but to no avail. I followed Fass's procedure exactly andthis time failure was so complete I couldn't get it to recognize my old card. Ultimately I reinstalled Ubuntu which enabled my old broadcom card and here I am. Anybody got any ideas on how to get past the "Unsupported Device" screen?

---

### Post by bgiannes on 2010-03-26
Just some info:

this card works with my Dell 8100 laptop SparkLAN WMIR-215GN (chip-set rt2860) you just need to add the /etc/Wireless/RT2860STA/RT2860STA.dat file for N speeds, i didn't need to do anything else.  The WLAN is wpa2 mixed speed.  This card is a mini pci type IIIB, (so check your PC's port type)

I have another rt2860 on a atom mythfront-end (airlink mini pci-e) with two ext. antennas and get full HD, (only have one G device which is almost always off, so i get no G speed limits).  There are two walls and about 15ft of air to the dd-wrt router

The rt2860 chip-set is a winner in my book, 9.10 kernel includes the drivers :D

---

### Post by bornagainpenguin on 2010-04-14
I just wanted to echo my thanks, as this worked for me in Lucid, even though there were a few errors here and there...

--bornagainpenguin

---

### Post by score100 on 2010-04-15
> **Fass said:**
> 
Now, while still root modprobe the driver module:

```
modprobe rt2860sta
```Give it a minute to create the ra0 device node, and network manager should now be able to display all visible wireless networks in your area, meanwhile you can stop being root and make sure that the module was probed correctly by checking the output of lsmod looking for the rt2860sta module.



I'm installing this on my eeepc 1008ha and I get stuck here. when i type the modprobe, I only get "WARNING: all config files need to be conf." etc ****, no creation of ra0device. And iwconfig shows no sign of a ra0.

Any advice for a linux newbie like me?

---

### Post by score100 on 2010-04-17
I'm workinging 9.10 btw, still trying to figyure it out.

---

### Post by grouchomrx on 2010-04-22
It worked in Lucid beta too.

Thank you

---

### Post by scorptig on 2010-04-30
I am having issues, I see my Network, I entered my coordinates, I try and connect and the beacon keeps flashing, in previous Ubuntu version 9.10, 9.04 I had no issues. So I cannot connect to my Wireless Network.

Using the RC1 of Lucid Lynx, I noticed an issue, but upon reboot, I was connected to Wireless.

Now I am using the latest Lucid Lynx 10.04 LTS 64 bit Ubuntu.

and I just installed Lucid Lynx today, Friday 30th of April, 2010. 

So Terminal Open ```
uname -a 
Linux ubuntu64 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
```

Wireless RaLink RT2760

```
lsmod | grep rt2860sta
rt2860sta             879881  1 
```

```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:-64 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


First in your original thread, the URL for RaLink has changed.
[http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2")

Then the 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2 is no longer listed,
I chose the closest one to your description

2010_01_29_RT2860_Linux_STA_v2.3.0.0.tar.bz2

I followed your procedure exactly to the letter, final results it did not succeed.

So this is not Only an issue for my workstation, I have at least 4 other friends with the same identical card. I am expected soon to install same on their pcs, so this is really an issue, for many Ubuntu users.

It was an non-issue for me in 9.04 and in 9.10 it simply worked One Step.

Thank you for your Feedback.

---

### Post by Strange_Movement on 2010-05-01
This has also become a problem with me since installing Lucid Lynx LTS and finding that there is no replacement kernel available from array.org for my eee901.

I to have downloaded 2010_01_29_RT2860_Linux_STA_v2.3.0.0.tar.bz2 and installed it. I now have ra0 instead of wlan0 but I still can't connect to my hidden SSID access point that is configured to use WPA & WPA2 with TKIP & AES. This wasn't a problem with the 9.04 kernel from array.org that was using the 1.7.1.1 driver.

Maybe someone could tell us where to download the array.org version of the 1.7.1.1 driver from.

Here's hoping.....

---

### Post by Strange_Movement on 2010-05-01
...OK I've found the eee specific driver that RALink released at:

[http://www.itwriting.com/DPO_RT28xx_60_LinuxSTA_V1.7.0.0_2008_07_15.tgz]("http://www.itwriting.com/DPO_RT28xx_60_LinuxSTA_V1.7.0.0_2008_07_15.tgz")

and I've tried to compile it but I get the following after typing **make && make install**

[SIZE="1"]make -C tools
make[1]: Entering directory `/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/tools'
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/md5.o
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/mlme.o
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/mlme.c:4170: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/action.o
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/ba_action.o
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_data.o
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_data.c: In function ‘RTMP_FillTxBlkInfo’:
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_data.c:889: warning: label ‘FillTxBlkErr’ defined but not used
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_info.o
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_info.c: In function ‘RTMPIoctlGetSiteSurvey’:
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_info.c:1921: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_info.c:1921: error: (Each undeclared identifier is reported only once
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_info.c:1921: error: for each function it appears in.)
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_info.c:1921: error: implicit declaration of function ‘signal_pending’
/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_info.c:1921: error: implicit declaration of function ‘schedule_timeout’
make[2]: *** [/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux/../../common/cmm_info.o] Error 1
make[1]: *** [_module_/home/strange/Downloads/DPO_RT28xx_60_LinuxSTA_V1.7.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [LINUX] Error 2[/SIZE]

...which I assume means it hasn't compiled successfully. There are some patches listed for Intrepid kernel 2.6.27 for allowing a successful compilation on the array.org site:

[http://launchpadlibrarian.net/17440207/dkms-rt2860-wext_compat.patch]("http://launchpadlibrarian.net/17440207/dkms-rt2860-wext_compat.patch")
[http://launchpadlibrarian.net/17440214/dkms-rt2860-nd_net.patch]("http://launchpadlibrarian.net/17440214/dkms-rt2860-nd_net.patch")

...but I don't understand what they are all about or if and how to use them. I'm way outside my comfort zone now and just hoping someone else will see this and go "Oh hey that's easy, all you need to do is....", and then give us some concise instructions. 

I really want the wireless on my eee 901 to work on **ALL** network configurations flawlessly again, like it did in 9.04 with the array.org kernel before I installed 10.04 with the default kernel.

---

### Post by scorptig on 2010-05-01
OK in my original post yesterday, I forgot to mention I used EXT4 file system.

For whatever reason, I find this most interesting, today I installed again Lucid Lynx, but EXT3 FS was used, First Time attempt, it worked, no issue with wireless, 2nd time, after reboot, it worked, third time, it stalled, and since 4th reboot, no problem. 

I am not saying this solves all issues with RT2760, but certainly in my situation, using EXT3 File system has resolved this issue, in the interim.

Is this an EXT4 File system issue in this release, 10.04 Lucid Lynx affecting RaLink RT2760? 

More feedback required.

---

### Post by ctbarker32 on 2010-05-01
Hi. 

I have written up a tutorial specifically aimed at getting the Ralink RT2860 chipset working with wifi and WPA security for Ubuntu 10.04. I think I have made it understandable for the novice. I am not a Linux expert by any means so that's where I'm coming from. 

Hope this helps.

[RT2860 and Ubuntu 10.04 wireless tutorial]("http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html")

-CB

---

### Post by Strange_Movement on 2010-05-02
I tried your method ctbarker32 but I'm afraid still no success :(

In fact with that new driver with the alterations that you suggested I can't even maintain a link to a completely open access point, which seems strange considering the changes that you suggested seemed to only be referring to the WPA/WPA2 bit of the driver.

May be it's all because I have no idea what I'm doing !

Oh please, to have a fully functioning wireless network card in my eee 901 again...

help!

---

### Post by PhilGil on 2010-05-02
I'm successfully using Ricardo Salveti's custom kernel from the launchpad bug report, post #53: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093)

If compiling the driver or using the custom kernel doesn't work, it's possible your problem might not be driver related.

---

### Post by scorptig on 2010-05-04
> **scorptig said:**
> OK in my original post yesterday, I forgot to mention I used EXT4 file system.

For whatever reason, I find this most interesting, today I installed again Lucid Lynx, but EXT3 FS was used, First Time attempt, it worked, no issue with wireless, 2nd time, after reboot, it worked, third time, it stalled, and since 4th reboot, no problem. 

I am not saying this solves all issues with RT2760, but certainly in my situation, using EXT3 File system has resolved this issue, in the interim.

Is this an EXT4 File system issue in this release, 10.04 Lucid Lynx affecting RaLink RT2760? 

More feedback required.

Ok here I am a few days later, sometimes I have an issue with connecting,
I disable Wireless wait a few seconds, reconnect then all is well, this however occurs every 3rd or 4th time I log in..I don't remember any issue in 9.10. However in 10.04 this is an issue.

---

### Post by jeebustrain on 2010-07-20
has anyone tried using the newest (07/16/2010) drivers from Ralink's website? Either I'm an idiot or all of the files listed to download are currupted. I can't get them to unpack on any machine (tried several Ubuntu machines and 2 windows machines using winzip). 

I get the same error whether I use the tar command or right click/extract here.
```

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

```


I moved my RT2760 nic to a new machine I was putting together for my son and never bothered to save the old drivers I downloaded.

Anyone have a working copy that they might want to post for download (or send me)?

---

### Post by stlouisubntu on 2010-07-27
> **jeebustrain said:**
> has anyone tried using the newest (07/16/2010) drivers from Ralink's website? Either I'm an idiot or all of the files listed to download are currupted. I can't get them to unpack on any machine (tried several Ubuntu machines and 2 windows machines using winzip). 

I get the same error whether I use the tar command or right click/extract here.
```

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

```


I moved my RT2760 nic to a new machine I was putting together for my son and never bothered to save the old drivers I downloaded.

Anyone have a working copy that they might want to post for download (or send me)?

Hey friend (and fellow stlouisian), I also got the same error you mentioned when I tried to extract from nautilus but it worked fine when I entered the following from the command line:

$  tar -xzvf 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2

Further, when I compiled, I used sudo checkinstall instead of sudo make install so I have a nice beautiful .deb (to share I suppose.)  I can also share the tarball source though if needed.  I compiled this on my Asus eeepc 1000 (straight 1000 8 + 32 GB SSDs 1.6 Ghz Intel Atom)

---

### Post by SaberX01 on 2010-07-30
Had the same issue with the Driver not being a BZ2, but tar sorted it out.

Was stuck solid on this problem, RT2760. Downloaded the RT2860 driver Set, compiled as stated ( I think the sudo su is key ). and it was connected to WPA faster than I could check the status.

Well done on the How-Too. If only all Ubuntu WIFI issues were this straight forward ::D

Time to buy a stack of cheap 20.00 dollar WiFI cards now :p
.

---

### Post by dadsy on 2010-07-31
Thanks very much for this how-to. I adapted it to the RT3060 used in the D-Link DWA-525 I just purchased and seems to be working well.

Thanks again.

---

### Post by edday on 2010-08-03
When will this find its way into the kernel?  I really tire of having to redo this every time the os is updated.

Perhaps someone could advise as to how a script could be written to do all this automatically.

---

### Post by stlouisubntu on 2010-08-11
> **edday said:**
> When will this find its way into the kernel?  I really tire of having to redo this every time the os is updated.

Perhaps someone could advise as to how a script could be written to do all this automatically.

I agree, friend.  It would at least be nice if a dkms module would be available for this so it would automate the process.  My plan is to lock my kernel version (frankly I am not even sure how many of these steps to repeat at each kernel update.)

---

### Post by daibak on 2010-08-13
> **edday said:**
> When will this find its way into the kernel?  I really tire of having to redo this every time the os is updated.

Perhaps someone could advise as to how a script could be written to do all this automatically.
10.04 Lucid Lynx not functioning out of-the-box for Ralink RT2860 wireless adapter on an Asus Eee PC 1000H Netbook pre-loaded WinXP SP3 finally drove me to what will sound to many like a absurdly exaggerated solution. Using free VMware Player 3.1.1 I've never since had to worry about kernel updates for Ubuntu or even re-booting to switch between Windows XP (host OS) and Ubuntu 10.04 (one of several guest OSes installed) as I work wirelessly - one of the tricks of virtualization is to virtualize the host's network adapters, wired and Wi-Fi, so the Linux-Ralink RT2860 tragedy is a non-event. VMware Player also a wonder in that unlike in typical dual-boot scenarios where one has to re-boot to launch another OS this is merely a Ctrl+Alt or mouseclick away in the virtualized world.

It takes about 45 minutes to install the Ubuntu 10.04 Netbook Edition ISO as a new virtual machine. I'd allow another ten to fifteen minutes to tweak system timezone, keyboard layout, language support, screensaver and amplify the sound settings. Ubuntu 10.04 is connected to the Internet wirelessly (Wired network connection 'Auto eth0' active is what you see if you hover your mouse over the Active Network Connections icon in the bar at the top of your Ubuntu screen) as soon as it's installed and launches for the first time, and Update Manager will probably notify you to download 200 to 300 updates as it did to me including Linux kernel updates.

I've been amazed how fast and responsive Ubuntu 10.04 Netbook Edition has performed with a mere Intel Atom N270 processor on this ASUS Eee PC but  installed as a virtual machine. I accepted VMware Player 3.1.1 recommended defaults where to install Ubuntu including only 512MB RAM but increased the disk space from 20GB to 25GB. The total 2GB RAM on this WinXP Eee PC allows Windows to run as well as it did when it was the sole OS installed.

---

### Post by edday on 2010-08-13
There are a lot of goodies in virtualization.  One of those is the fact that the hardware depends on the host system.  In your case, windows xp.  So, 10.04 is not really using the OS to access the rt2860.

My preference is just not to have to bother with windows of any flavor.  Since the rt2860 is so ubiquitous on the eeepc, I just don't understand why Ubuntu would not do whatever is necessary to make this automatic.  Apparently it was not a problem in 9.x.

---

### Post by ribico on 2010-09-03
Great.. it worked immediately !

I had an issue with drivers, the link you report is broken.
the new link from Ralink is:

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

from this page choose
RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)

the archive downloaded seems to be corrupted, at list not recognized as bz2 as it should.
It seems impossible to uncompress it..

by chance I discovered the utility mount archives was able to read it.


So, after downloading the driver package in Lucid Lynx NBR, right click on it and chose "open with mount archives" (not sure if the translation is correct).
This will provide a new virtual disk on your system containing the archive content.

hope this may help.

---

### Post by Tommu_Borgir on 2010-10-16
Im getting to the part where i need to untar the folder and it comes up with:
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
i was reading Page 5 and someone said to try a different code, but it doesnt work for me,

Im running an eeepc 1000Ha with a 500gb hdd if that helps anyone to know what ive done wrong lol

---

### Post by edday on 2010-10-18
Really sounds like you have a corrupted file.  Try downloading again and check the checksum.

---

### Post by Viciou§ on 2010-11-05
Hi!

I have followed this guide twice.
Some time ago I installed Lucid and followd this guide.
Everything worked perfectly! I could connect to my WPA2 secured SSID and got a link speed of ~270mbps.
I could transfer files at ~9-11 MB/s from my Win7 desktop.

A week ago I reinstalled Lucid on the same computer but on a larger, newer, faster SATA drive.

I followed this guide once more but now my transfer speeds max out at ~2.5 MB/s :(
Link speed is still at ~270mbps but signal drops to low when transferring files (only the "dot" and one "bar" in NM-applet).

I reconnected the old SATA drive and transfered some files and behold! The old install still reaches speeds up to 11-12 MB/s!
Signal is max in nm-applet, sometimes drops to max -1 "bar".
The average transfer speed is ~9.3 MB/s on the old install and in the new install ~2.5 MB/s, peak 4 MB/s :(

I can't figure out what could be the difference between theese two installs, could anyone please point me in the right direction or give some tips on how to troubleshoot this?

---

### Post by w2vy on 2010-11-05
> **Viciou§ said:**
> 
A week ago I reinstalled Lucid on the same computer but on a larger, newer, faster SATA drive.
(snip)
I can't figure out what could be the difference between theese two installs, could anyone please point me in the right direction or give some tips on how to troubleshoot this?

See above, THAT is the difference.

Try getting a stronger signal and see if it makes a difference.
Maybe the new drive is spewing out more RF noise

Tom

---

### Post by Viciou§ on 2010-11-05
The router is ~3m from the computer, concrete wall in between.
The new drive was formerly a USB connected external drive which I have taken apart, since I didn't need 2 TB external storage and wasn't happy with 160GB internal :P
(only have one SATA connector on MB)

Point is, this drive used to sit on top of the computer, connected through USB when i received higher throughput.
Sure it could be that by removing the casing and putting it inside of the computer it produces more RF noise but it seems far fetched to me :/

I will test later to see if the signal and throughput improves when moving the disk further from the antennas.

Edit: Seems to be a problem with the motherboards PCI bus. Other MB and all is well.

---

### Post by LaJuan on 2011-11-10
Hi,

I've been trying to install since 10.10 and nothing seems to work!!!!!!!!!! In the beginning of this thread, there's a how to install but, the link the users gives, the company doesn't offer any more. I downloaded this: 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2. I also did a iwconfig and I get no wireless extension. I even tried to install it using wine from off the CD and nothing!!!!!!!!!!! I've been using Ubuntu since 8.10 and now I'm using 11.04. I still new to this Linux. Please!!!!!!!!! Could anybody offer a simple user some hel pon how to fix this issue? Any help would be great!!!!!!!!!!

Thanks,
:confused::confused::confused::confused::confused:
LaJuan

---

### Post by LaJuan on 2011-11-10
I would like to thank ALL who posted this "How To"!!!!!!!!!! I love Ubuntu and thanks again for the support!!!!!!!!! My car is work at full and now I can remove the 15ft CAT6e running from my wireless router to my desktop!!!!!!!!! LOL:lolflag::lolflag::lolflag:
:guitar::guitar::guitar::guitar: You guys ROCK!!!!!!!!

---

