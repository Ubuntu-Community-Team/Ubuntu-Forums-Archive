---
title: "HOWTO:Compilling and installing RTL8188CE Driver on Ubuntu 11.10 Oneiric Ocelot"
date: 2012-02-23
forum: Tutorials
---

### Post by Osalot on 2012-02-23
Here are some steps for those of us who have a Wireless Card with RTL8188CE Chip set or RTL8192CE,RTL8191SE/RTL8192SE,RTL8192DE for Realtek. Are also new to Ubuntu and the terminal, don't know how to compile or how to install a diver on Ubuntu for it.


First we need to download the diver from Here

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Then you will need to put it on the desktop from the downloads folder. Then extract it with Archive Manger by right clicking it and putting it in the Home folder witch is on the left side of the desktop in the top part of the unity dock.

You will need to rename the extracted folder to something sorter like rtldriver

Now open a terminal window by pressing these 3 keys at once Ctrl & Alt & T on the keyboard

In the terminal put

```
sudo su
```It will ask for your password. In the terminal put

```
apt-get install gcc build-essential
```That will down load all the needed files to compilie the driver. Once its done put this in to the terminal

```
cd /home/Your Name/rtldriver
```Heres what mine looks like

```
cd /home/osalot/rtldriver 
```Now you should have somthing that looks similar to this in the terminal

```
root@osalot-Rampage-Extreme:/home/osalot/rtldriver#
```Now put this in the terminal

```
make 
```Once thats done put this in the terminal

```
Make install
```Now we need to start the driver. Put this in to the terminal

```
modprobe rtl8192ce
```If your WIFI shows up with the other connections that means the driver was compiled correctly.Now to get it to stay that way even after a reboot. We will need to open gedit with root privileges for the next bit. In the terminal put

```
gksudo gedit /etc/modules
```It should look like this in gedit
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

```Now we need to put this rtl8192ce.ko in it so it loads up on start.Once done should look like this

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtl8192ce.ko
```Now save, close, and reboot Ubuntu and you should now have a working RTL8188CE WIFI card in a Ubuntu.

[SIZE=2]_**If there are any errors or mistakes in the post let me know**_[/SIZE]

***Here are some other posts/documentation***

[U]Supported wireless cards and Info in Ubuntu

[/U][https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)[U]

Another How to for [SIZE=1]**Rosewill RNX-N150PC PCI Ralink 3060 **[/SIZE][/U][U]wireless cards

[/U][http://ubuntuforums.org/showthread.php?t=1608095&highlight=rt3562sta](http://ubuntuforums.org/showthread.php?t=1608095&highlight=rt3562sta)[U]

Information on root/sudo usage

[/U][https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)[U]

Information on wireless trouble shooting/how to set up ndiswrapper[/U]

[https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-disabled](https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-disabled)

---

### Post by prtchrdbill on 2012-06-13
Hi,
I have ubuntu 12.04 as a  OS with win7 on a Toshiba netbook NB 510. Wireless works ok on win7 but is unreliable on ubuntu. I tried a netgear usb wireless which works. I have followed your instructions re a linux driver but encounter an error after make. I also get the  same error when using the realtek automated command. The terminal output is shown below.Do you have any suggestions?
william@william-netbook:~$ sudo su
[sudo] password for william: 
root@william-netbook:/home/william# cd /home/william/driver/driver2
root@william-netbook:/home/william/driver/driver2# apt-get install gcc build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
root@william-netbook:/home/william/driver/driver2# make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-24-generic-pae/build M=/home/william/driver/driver2  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic-pae'
  CC [M]  /home/william/driver/driver2/cmd/rtl871x_cmd.o
In file included from /home/william/driver/driver2/include/drv_types.h:70:0,
                 from /home/william/driver/driver2/cmd/rtl871x_cmd.c:24:
/home/william/driver/driver2/include/rtl871x_cmd.h:107:25: error: field ‘event_tasklet’ has incomplete type
In file included from /home/william/driver/driver2/include/drv_types.h:72:0,
                 from /home/william/driver/driver2/cmd/rtl871x_cmd.c:24:
/home/william/driver/driver2/include/rtl871x_xmit.h:355:24: error: field ‘xmit_tasklet’ has incomplete type
In file included from /home/william/driver/driver2/include/drv_types.h:73:0,
                 from /home/william/driver/driver2/cmd/rtl871x_cmd.c:24:
/home/william/driver/driver2/include/rtl871x_recv.h:205:24: error: field ‘recv_tasklet’ has incomplete type
make[2]: *** [/home/william/driver/driver2/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/william/driver/driver2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic-pae'
make: *** [modules] Error 2
root@william-netbook:/home/william/driver/driver2# Make install
No command 'Make' found, did you mean:
 Command 'fake' from package 'fake' (universe)
 Command 'rake' from package 'rake' (main)
 Command 'cake' from package 'cakephp-scripts' (universe)
 Command 'make' from package 'make' (main)
Make: command not found
root@william-netbook:/home/william/driver/driver2#

---

