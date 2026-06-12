---
title: "HOW TO: Install a broadband wireless dongle"
date: 2012-07-17
forum: Tutorials
---

### Post by giuliopepe on 2012-07-17
This guide explains how to install a broadband wireless dongle on Linux.
It lists the main problems users usually find when trying to install the dongle on a Linux OS, and provides possible solutions.
I have seen many posts about users trying to install their broadband internet and getting stuck at the same problem, or just asking how to install their specific version of their dongle, without having tried anything. I noticed that on the internet there is not much info either, even if most of installations share the same steps.

I am writing this guide in the attempt to unify, in the best possible way, the installation guides for most broadband dongles for a generic (beginner) Linux user. All the commands should work on any Linux distribution. For your information, the distribution I used to make this tutorial is Debian Squeeze with Gnome (GUI), and the broadband modem is an obscure Olivetti Olicard 200, which was only known to be not very Linux-friendly.

The only prerequisite is to know how to install software packages on your distribution. I explain any other step and provide commands. No other knowledge of Linux is assumed.

I copied this guide from my blog, here:
[http://www.greplinux.net/2012/07/everything-you-need-to-know-about.html](http://www.greplinux.net/2012/07/everything-you-need-to-know-about.html)
I wrote this guide and it is not copyrighted.



[SIZE=4]**_1. Check that your system sees the hardware_**[/SIZE]

Firstly, remove your PIN from the SIM card using a mobile phone, as it can unnecessarily complicate things.

Whenever you plug-in your usb broadband modem, the very first thing you need to check is that your systems realizes that something has been plugged-in your usb port.

I am assuming that your mobile broadband dongle is working on the first place (can check on a Windows system, if you are not sure). A flashing led should show you that the electronics are working inside.

Run this command to see if the modem is recognized as plugged-in a usb port:

```
$ lsusb
```If you see an error message, you most probably do not have installed the *usbutils* package. The output will be something similar to:

    ```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 006 Device 003: ID 04b4:0060 Cypress Semiconductor Corp.
    Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**    Bus 002 Device 028: ID 0b3c:f000 Olivetti Techcenter**
    Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```This is the list of the usb ports and what is connected to them, you should recognize your broadband dongle by the brand name. Sometimes the names do not coincide, so if you have troubles finding it in the list, disconnect it and run* lsusb* again to check which device is missing. The missing device is the broadband modem.

Take a note of the codes just before the brand name. In my case the numbers are:

```
0b3c:f000
```where **0b3c** is the **vendor code** and **f000** is the **product code**.
This product code is used for storage usb dongles. As most of mobile broadband dongles are also capable to store data, the system is not recognizing the dongle as a modem. If you have this product code as well, proceed to _Step 2_.

If you see a code like **XXXX** or **cXXX** (where X is any number from 0-9), instead, your system already recognizes your dongle as a wireless broadband modem.
You can skip Step 2 and proceed to _Step 3_.


[SIZE=4]_**2. Switch device from usb to modem**_[/SIZE]
*(this step requires an internet connection, you can gather the packages from another pc if you are not able to connect on your own)*

Your internet dongle is not recognized as such. We will use a software to let your system recognize it, called *usb-modeswitch*. You need to install two packages which are part of this program: *usb-modeswitch* and *usb-modeswitch-data*. Also install *wdial* and *modemmanager*, if for some reason are not installed already.

Once installed, you will need to type a single command to switch the mode of your internet dongle from storage usb-stick to modem.
Firstly, you will need some information:

- The **vendor code**, as found before usign *lsusb* (in my case 0b3c)
- The **product code**, as found before usign *lsusb* (in my case f000)
- A **Hex key**, associated to vendor and product code.

You already have vendor and product code, but in order to obtain the Hex key, you need to run the following command, which will retrieve the Hex key from your system.

```
$ cat /etc/usb_modeswitch.d/[vendor code]\:[product code] | grep MessageContent
```You need to substitute *[vendor code]* with your vendor code and *[product code]* with your product code. In my case, the command is:

```
$ cat /etc/usb_modeswitch.d/0b3c\:f000 | grep MessageContent
```This will print on your screen the Hex key. After you gathered this information, open the terminal and type:

```
$ sudo usb_modeswitch --default-vendor [vendor code] --default-product [product code] --message-content [hex key]
```Which in my case, for a Olicard 200, is:

```
$ sudo usb_modeswitch --default-vendor 0x0b3c --default-product 0xf000 --message-content 5553424312345678c000000080010606f50402527000000000000000000000 
```After you run this code, you should see an output of this kind:

    ```
Looking for default devices ...
     Found devices in default mode, class or configuration (1)
    Accessing device 003 on bus 001 ...
    Getting the current device configuration ...
     OK, got current device configuration (1)
    Using endpoints 0x01 (out) and 0x81 (in)
    Using endpoints 0x01 (out) and 0x81 (in)
    Inquiring device details; driver will be detached ...
    Looking for active driver ...
     OK, driver found ("usb-storage")
     OK, driver "usb-storage" detached

    SCSI inquiry data (for identification)
    -------------------------
      Vendor String: USBModem
       Model String: MMC Storage   
    Revision String: 2.31
    -------------------------

    USB description data (for identification)
    -------------------------
    Manufacturer: USBModem
         Product: HSPA Data Card
      Serial No.: 1234567890ABCDEF
    -------------------------
    Setting up communication with interface 0 ...
    Using endpoint 0x01 for message sending ...
    Trying to send message 1 to endpoint 0x01 ...
     OK, message successfully sent
    Resetting response endpoint 0x81
    Resetting message endpoint 0x01
     Device is gone, skipping any further commands
    -> Run lsusb to note any changes. Bye.

```If the command succeed, like in this case, run* lsusb*. When you do, you should note a change, as the internet dongle has now changed its product-code to "c005".

   ```
 Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 006 Device 002: ID 04b4:0060 Cypress Semiconductor Corp.
    Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 005: ID 0b3c:**c005** Olivetti Techcenter
    Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Reboot and you can now proceed to the next step.



[SIZE=4]**_3. Install your internet dongle (the normal way)_**[/SIZE]

If you are lucky enough, your broadband internet might be working already. In the GUI, click on the Network Manager icon and see if the Broadband connection is available. If it is, click on it to set up a new connection and proceed to _Step 4_.
Otherwise, try to run on a terminal:

```
$ sudo modprobe usbserial vendor=[vendor code] product=[product code]
```Which for an Olicard 200 is:

```
$ sudo modprobe usbserial vendor=0x0b3c product=0xc005
```This commands adds a loadable kernel module to recognize your device. Straight after you run it, your system should automatically detect your device and you can proceed with configuring your internet dongle.

If even this method did not work (as it did not on my Olidata 200), and your Network Manager does not recognize the device, it means that you will need to find another way to let it work, so jump this section and go to _Step 5_.

Now that you have your working dongle, you need to do some final setups before configuring it. In order to get the *modprobe* command run at every boot, you need to append the previous command to */etc/rc.local*, by running as root:

```
$ su -
``````
# sed -i '$ d' /etc/rc.local; echo 'modprobe usbserial vendor=0x0b3c product=0xc005' >> /etc/rc.local; echo 'exit 0' >> /etc/rc.local
```As usual, replace *0b3c* and *c005* with your vendor code and product code.



[SIZE=4] **_4. Connect to the internet_**[/SIZE]

You now need to set up a new connection with your broadband dongle. If a connection wizard opens, you can follow the instructions on screen and it will automatically configure your dongle.

It may happen that your dongle does not like the network manager configuration. You can get around the problem using *wvdial*.

```
$ sudo gedit /etc/wvdial.conf
```and copy the following text:

    ```
[Dialer Defaults]
    Modem = /dev/ttyUSB0
    ISDN = 0
    Modem Type = Analog Modem
    Baud = 460800
    Init1 = ATX3
    Init2 = AT&F Q0 V1 E0 S0=0 &C1 &D2 +FCLASS=0
    Init3 = at+cgdcont=1,"IP","*[APN]*"
    Phone = *99#
    Dial Attempts = 5
    Stupid Mode = on
    Dial Command = ATDT
    Idle Seconds = 7200
    Ask Passwords = 0
    Password = "*[PW]*"
    Username = "*[UN]*"
    Carrier Check = on
    New PPPD = 1
    Auto DNS = on
```You should modify* [APN]*, *[PW]*, *[UN]* to your needs.
Then, you can connect using

```
$ sudo wvdial
```Congratulations, your dongle should be working now!



[SIZE=4]**_5. Install your internet dongle (the alternative way)_**[/SIZE]

If the "normal" way to install your dongle did not work, you should consider using a very neat utility, which usually works with picky internet dongles.
It is called *Sakis 3G*.

You just need to download it and extract it:

```
$ wget http://www.sakis3g.org/versions/latest/binary-free/sakis3g.gz
$ gunzip sakis3g.gz
$ chmod +x sakis3g
```Before running it, you need to remove the *modemmanager* application which controls mobile broadband devices through the GUI Network Manager. This is because it may conflict with *Sakis 3G*.

```
$ sudo apt-get remove modemmanager
```Then you can run the application:

```
$ ./sakis3g --interactive
```And you can follow the screens to configure the dongle and connect to the internet:

- Connect with 3G
- USB Device
- Select USB Device (the name should be familiar)
- Select Interface (only one should work as modem)
- Select APN (should auto-detect)

If you see a screen informing you that the device connected: congratulations, you managed to make your internet wireless dongle work on a Linux OS!



This is my first how-to, please reply to suggest other methods, mistakes (I'm sure there will be many) or if you have any problems.
Hope it helped :wink: 

Giulio

---

