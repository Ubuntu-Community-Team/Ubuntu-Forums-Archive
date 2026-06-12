---
title: "Ralink RT73 USB Wifi Driver (patched for injection &amp; frag) + DKMS in Jaunty (9.04)"
date: 2009-07-16
forum: Tutorials
---

### Post by jasmineaura on 2009-07-16
This guide uses p_larbig's RT73 USB enhanced drivers instead of the serialmonkey drivers because p_larbigs's are based off of the serialmonkey drivers, but have been already patched for Injection & Fragmentation Attacks, so you can utilize aireplay-ng in Aircrack-ng to its fullest.
The guide also helps you build and install the module with [DKMS]("http://linux.dell.com/dkms/") (which is natively supported in Jaunty 9.04), so that if you recompile your kernel or upgrade it later, the module will be automatically rebuilt and installed for you, by [DKMS]("http://linux.dell.com/dkms/") :)

**For more info on p_larbig's RT73 USB driver sources:**
[http://homepages.tu-darmstadt.de/~p_larbig/wlan/]("http://homepages.tu-darmstadt.de/%7Ep_larbig/wlan/")

**Notes about this version (3.0.3) from the author's site:**
> Version 3.0.3 provides kernel version 2.6.29 compatibility. It uses default kernel memory allocation for devices' private data area. This may fail on 64bit platforms (according to RaLink). In previous versions the driver allocated its own memory and hacked it into the netdev structure. This hack failed in 2.6.29 and has been removed. However, the new mode works for me quite well. Please report if any problems occur.
The wireless card I tested this on is a DLink DWA-110 USB, the system I tested this on is a clean install of Ubuntu Jaunty 9.04 with all updates as of 17/7/2009 (including the stock kernel 2.6.28-13).

[B] Blacklist the mac80211-based rt73usb & rt* drivers to avoid conflicts
[/B]create a new file in /etc/modprobe.d called blacklist-rt73.conf
```

sudo nano /etc/modprobe.d/blacklist-rt73.conf

```and paste the following in it:
```

# Blacklist rt73usb (mac80211) as it's beta and conflicts with the 
#  stable ieee80211 based rt73 module
blacklist rt73usb

# Other modules that possibly conflict with rt73
blacklist rt2500usb
blacklist rt2x00lib
blacklist rt2x00usb

```**Download the latest version of the RT73 USB Enhanced Driver**
(in your home directory or in /tmp or wherever you like, it will no longer be needed after)
```
wget http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-3.0.3.tar.bz2
tar xjf rt73-k2wrlz-3.0.3.tar.bz2
cd rt73-k2wrlz-3.0.3

```you should now be in the top-level directory you just extracted ( rt73-k2wrlz-3.0.3 )

**Prepare DKMS config**
create a file in rt73-k2wrlz-3.0.3 directory, called dkms.conf
```

nano dkms.conf

```and paste the following in it:
```

PACKAGE_NAME="rt73-k2wrlz"
PACKAGE_VERSION="3.0.3"

# make sure kernel is 2.6.27 or newer, just in case
# http://homepages.tu-darmstadt.de/~p_larbig/wlan/
BUILD_EXCLUSIVE_KERNEL="2.6.(27|28|29|[3-9][0-9])"

MAKE[0]="make -C Module"
CLEAN="make -C Module clean"

BUILT_MODULE_NAME[0]="rt73"
BUILT_MODULE_LOCATION[0]="Module"
DEST_MODULE_LOCATION[0]="/kernel/drivers/net/wireless"

AUTOINSTALL="yes"

```**Create a traball archive of the source directory** (with our dkms.conf in it)
```

tar czf rt73-k2wrlz-3.0.3-dkms.tar.gz rt73-k2wrlz-3.0.3

```**Load the rt73-k2wrlz tarball to DKMS source tree**
```
sudo dkms ldtarball --archive=rt73-k2wrlz-3.0.3-dkms.tar.gz
```**Build rt73 module with DKMS**
```
sudo dkms build -m rt73-k2wrlz -v 3.0.3
```**Install rt73 module with DKMS**
```
sudo dkms install -m rt73-k2wrlz -v 3.0.3
```Insert you RT73 USB Wifi adapter and it should be automatically detected, and automatically configured for you by **NetworkManager** or **WICD** (whichever one you use) if you have either installed. I use NetworkManager, and it automatically detected my DLink DWA-110 USB soon after I plugged it in :)
Or alternatively you could install **RutilT**
```
sudo apt-get install rutilt
```Author's site: [http://bonrom.cbbknet.com/](http://bonrom.cbbknet.com/)
> RutilT is a Gtk+2 utility for Linux that helps you configure your wireless devices. It should play nicely with the "legacy drivers" from the[ rt2x00 project]("http://rt2x00.serialmonkey.com/"). I initially intended to support rt2x00 itself, however due to real life constraints, I am no longer doing much development, only maintenance. 
More info on making RutilT run in startup:
[http://ubuntuforums.org/showthread.php?t=502526](http://ubuntuforums.org/showthread.php?t=502526)

Hope this helps anyone :)

---

### Post by 10josh10 on 2009-07-20
This was extremely helpful and accurate.  Thank you!

---

### Post by dr_jk on 2009-08-01
Hi  i am a linux nubbie when i do 
# sudo dkms build -m rt73-k2wrlz -v 3.0.3 
 i get this


Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.

---

### Post by ugm6hr on 2009-08-01
My Edimax EW-7318USG uses the rt73usb device.

With the default rt73usb, I have to blacklist rt2500usb, which seems to interfere with it.  However, I have found the connection to be very unstable with rt73usb.

With this driver linked above (new RT73), my WPA router is not correctly recognised by Network Manager (seen as WEP); hence it doesn't work.

In case anyone else wants to remove it:
```
sudo dkms remove -m rt73-k2wrlz -v 3.0.3 --all
```

---

### Post by jasmineaura on 2009-08-02
> **dr_jk said:**
> Hi  i am a linux nubbie when i do 
# sudo dkms build -m rt73-k2wrlz -v 3.0.3 
 i get this


Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.

You're probably running too old of a kernel...

If you still want to ignore this and try to compile it on your old kernel, comment out the BUILD_EXCLUSIVE line in /var/lib/dkms/rt73-k2wrlz/3.0.3/build/dkms.conf

---

### Post by jasmineaura on 2009-08-02
> **ugm6hr said:**
> My Edimax EW-7318USG uses the rt73usb device.

With the default rt73usb, I have to blacklist rt2500usb, which seems to interfere with it.  However, I have found the connection to be very unstable with rt73usb.

With this driver linked above (new RT73), my WPA router is not correctly recognised by Network Manager (seen as WEP); hence it doesn't work.

In case anyone else wants to remove it:
```
sudo dkms remove -m rt73-k2wrlz -v 3.0.3 --all
```

Wow, the detachable 4dBi High Gain Aerial Antenna on that thing looks sweet, and it supports WPA2+AES :D

Anyway, this can happen a lot of times with a lot of cards with several wifi drivers.. Heck, it even happens under windows :P

Try the following:

_Method 1:_

1. Try stopping Network Manager before inserting your wireless USB
```
sudo /etc/init.d/NetworkManager stop
```
2. Insert your wireless USB, start Network Manager, and give it a few seconds to initiate and scan for your AP again
```
sudo /etc/init.d/NetworkManager start
```

If your wireless is still not showing up as WPA, try setting it to WPA manually in Network Manager. Right click your NM tray icon, click Edit Connections, go to wireless tab, add/edit your ESSID, uncheck "connect automatically" if it was previously added, go to authentication, choose WPA manually, enter your password, then connect manually.

If that doesn't cut it, try Method 2.

_Method 2 (special support):_

1. Install RutilT
```
sudo apt-get install rutilt
```
2. Stop Network Manager
```
sudo /etc/init.d/NetworkManager start
```
3. Bring up your interface (you can also do this in step #4 from within RutilT itself after you switch to priviliged mode to be able to toggle "interface up/down"
```
sudo ifconfig rausb0 up
```
4. Start RutilT from the menu, or from command line `rutilt`
5. Click the tray icon for RutilT, choose your rausb0 interface if it pops up (happens usually if you have another wifi interface built-in/connected) asking you to choose interface (it should say something like "special support" next to it)
6. Go to the "Site Survey" tab and click scan, and see if your AP ESSID shows up with the correct Auth/Cipher..
7. Add a profile for it, which should show up in Profiles tab, and choose that to connect to your AP with that profile (dont rembember exactly the steps, as I'm not at my laptop right now)

Screenshots:
[]("http://www.fam.tuwien.ac.at/%7Eschamane/_/_media/screens:wusb54g_rutilt_xubuntu.png")[IMG]http://www.fam.tuwien.ac.at/%7Eschamane/_/_media/screens:wusb54g_rutilt_xubuntu.png[/IMG]

[IMG]http://img73.imageshack.us/img73/3040/rutiltprofilesfo4.png[/IMG]

[IMG]http://img133.imageshack.us/img133/3259/rutiltfirstxg8.png[/IMG]

[IMG]http://img73.imageshack.us/img73/5741/rutiltrt73nc7.png[/IMG]


Hope this helps...

---

### Post by ugm6hr on 2009-08-02
> **jasmineaura said:**
> Hope this helps...

Thanks for the work. But...

NM still only sees it as WEP, irrespective of what I try.

Rutilt sees WPA, and connects correctly.  However, the connection is even more unstable than NM + rt73usb driver :(

Still looking at other options.  Ralink have an RT2501 driver here: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
But this doesn't appear any better either (so far).

---

### Post by Bergschaf on 2009-08-02
Great post. Got the RT 73 driver installed with jasmineaura's description. Wicd Manager finds now the WLan. If I try to connect, it try's to get an IP from the DHCP but is not successful. I tried to connect manually via the terminal. And I got finally after several attempts : No IP offered by DHCP. However, if I connect wired to the router, then there are no problems. If I connect wired or wireless from Windows, again no problem to get IP from DHCP.

Not sure what the problem is.

Here is what I get from ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:21:3c:c9
          inet6 addr: fe80::20a:e4ff:fe21:3cc9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1159204 (1.1 MB)  TX bytes:239846 (239.8 KB)
          Interrupt:10

eth1      Link encap:Ethernet  HWaddr 00:04:23:75:c0:ce
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xc000 Memory:e0203000-e0203fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6960 (6.9 KB)  TX bytes:6960 (6.9 KB)

rausb0    Link encap:Ethernet  HWaddr 00:1f:1f:31:cb:cb
          inet6 addr: fe80::21f:1fff:fe31:cbcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:543570 (543.5 KB)  TX bytes:489662 (489.6 KB)

---

### Post by jasmineaura on 2009-08-06
> **ugm6hr said:**
> Thanks for the work. But...

NM still only sees it as WEP, irrespective of what I try.

Rutilt sees WPA, and connects correctly.  However, the connection is even more unstable than NM + rt73usb driver :(

Still looking at other options.  Ralink have an RT2501 driver here: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
But this doesn't appear any better either (so far).

Did you try the USB adapter under windows? does it work any better?
Have you considered the fact that it might be defective?

---

### Post by jasmineaura on 2009-08-06
> **Bergschaf said:**
> Great post. Got the RT 73 driver installed with jasmineaura's description. Wicd Manager finds now the WLan. If I try to connect, it try's to get an IP from the DHCP but is not successful. I tried to connect manually via the terminal. And I got finally after several attempts : No IP offered by DHCP. However, if I connect wired to the router, then there are no problems. If I connect wired or wireless from Windows, again no problem to get IP from DHCP.


Never really used WICD, but I suspect it's a WICD specific issue.. Try installing RutilT as described above, stop WICD temporarily, and see if RutilT resolves your issue... If it worked, you might want to investigate why it didn't work with WICD...

---

### Post by ugm6hr on 2009-08-06
> **jasmineaura said:**
> Did you try the USB adapter under windows? does it work any better?
Have you considered the fact that it might be defective?

Sorry - meant to post back.

I think it is a hardware problem.

Thanks for the help though...

---

### Post by Truthseekernz on 2009-08-11
My Dlink DWA-110 USB wi-fi adatptor worked fine on Jaunty 9.04 up to and including kernel 2.6.27-14. Kernels/module combos since don't work. But as these later kernels provide me with no obvious benefits, I continue to boot 2.6.27-14. 

If the DWA-110 USB W-Fi adaptor will be once again automagically functional with kernel 2.6.29.....I'll wait for that rather than try to implement the various solutions outlined above. If I had NO connectivity, I'd be in, boots and all, but at this point - for me - the simplest, most rational thing to do is keep booting the last kernel that worked out of the box with the one device I need to talk to any other thing on this planet. :-)

---

### Post by jasmineaura on 2009-08-12
> **Truthseekernz said:**
> My Dlink DWA-110 USB wi-fi adatptor worked fine on Jaunty 9.04 up to and including kernel 2.6.27-14. Kernels/module combos since don't work. But as these later kernels provide me with no obvious benefits, I continue to boot 2.6.27-14. 

If the DWA-110 USB W-Fi adaptor will be once again automagically functional with kernel 2.6.29.....I'll wait for that rather than try to implement the various solutions outlined above. If I had NO connectivity, I'd be in, boots and all, but at this point - for me - the simplest, most rational thing to do is keep booting the last kernel that worked out of the box with the one device I need to talk to any other thing on this planet. :-)

It worked fine for me in 2.6.28-13-generic in Jaunty 9.04, and worked fine with my custom compiled (and stripped down) 2.6.30 kernel from the [Ubuntu kernel PPA]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa")

For it to compile on Kernel 2.6.29, 2.6.30, etc.., in case you custom compile 2.6.30 like I did, you need to make sure you have the following kernel config option enabled:

"Networking Options" -> "Enable older network device API compatibility"
```
CONFIG_COMPAT_NET_DEV_OPS=y
```2.6.30 kernel seems to run a bit faster than the stock 2.6.28, especially if it has been stripped down a bit (and optimized for the particular CPU on your system).

I also upgraded the nvidia-graphics-drivers from the [Nvidia Vdpau Team PPA]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa") (185.18.x) and I can say it's pretty good...
Moreover, a lot of people noted they had much snappier video response with the 2.6.30 kernel update and the 185.18.x nvidia-graphics-drivers.. You can search the ubuntu forums for the Jaunty 9.04 users who upgraded to 2.6.30 (and nvidia drivers) to see for yourself..

I just have all my drivers (madwifi-hal 0.10.0, nvidia-185.10.x, rt73-k2wrlz-3.0.3, etc..) in dkms tree and they all build and install out of the box with my 2.6.30 upgrade (and recompiles if ever needed)

If you do use make-kpkg to build debs of your linux-headers and linux-image (in /usr/src) to use for upgrading your kernel, like so (you need to add your user to the "src" group and logout and relogin first to be recognized in the "src" group before untarring linux-source-2.6.30.tar.gz in /usr/src):
```

$ cd /usr/src/linux-source-2.6.30
$ make menuconfig
$ fakeroot make-kpkg --initrd --revision=1.0 --append=-custom1 kernel-headers kernel-image
$ cd ..
$ sudo dpkg -i linux-*-2.6.30-custom1_1.0.deb

```... MAKE SURE that you either _delete (or rename)_ the "/usr/src/linux-source-2.6.30" directory _before installing the debs you created_, otherwise the debian-based system will make the infamous mistake of pointing the symlink from "/lib/modules/2.6.30-custom1/build" to "/usr/src/linux-source-2.6.30" (instead of symlinking it to "/usr/src/linux-headers-2.6.30-custom1" as it should), which means _hell_ if your sources ever get tampered with and you need to recompile some module(s) or install new module(s)..

hope this helps anyone, as it costed me a lot of time (and cpu power) before :)

---

### Post by The Funkbomb on 2009-08-12
How can I remove the RT73 enhanced drivers?  I installed them and I don't want them.

Nothing I try can get rid of them.

Thanks.

---

### Post by jasmineaura on 2009-08-14
> **The Funkbomb said:**
> How can I remove the RT73 enhanced drivers?  I installed them and I don't want them.

Nothing I try can get rid of them.

Thanks.

Do this to uninstall the module(s) that were installed by DKMS and have it removed from the DKMS tree so it will not be automatically built for your kernel builds again:

```
sudo dkms remove -m rt73-k2wrlz -v 3.0.3 --all
```

For more information, see:
[Manpage of DKMS]("http://linux.dell.com/dkms/manpage.html")
[Kernel Korner - Exploring Dynamic Kernel Module Support (DKMS)]("http://www.linuxjournal.com/article/6896")

---

### Post by selfdz87 on 2009-09-18
> **jasmineaura said:**
> This guide uses p_larbig's RT73 USB enhanced drivers instead of the serialmonkey drivers because p_larbigs's are based off of the serialmonkey drivers, but have been already patched for Injection & Fragmentation Attacks, so you can utilize aireplay-ng in Aircrack-ng to its fullest.
The guide also helps you build and install the module with [DKMS]("http://linux.dell.com/dkms/") (which is natively supported in Jaunty 9.04), so that if you recompile your kernel or upgrade it later, the module will be automatically rebuilt and installed for you, by [DKMS]("http://linux.dell.com/dkms/") :)

**For more info on p_larbig's RT73 USB driver sources:**
[http://homepages.tu-darmstadt.de/~p_larbig/wlan/]("http://homepages.tu-darmstadt.de/%7Ep_larbig/wlan/")

**Notes about this version (3.0.3) from the author's site:**
The wireless card I tested this on is a DLink DWA-110 USB, the system I tested this on is a clean install of Ubuntu Jaunty 9.04 with all updates as of 17/7/2009 (including the stock kernel 2.6.28-13).

[B] Blacklist the mac80211-based rt73usb & rt* drivers to avoid conflicts
[/B]create a new file in /etc/modprobe.d called blacklist-rt73.conf
```

sudo nano /etc/modprobe.d/blacklist-rt73.conf

```and paste the following in it:
```

# Blacklist rt73usb (mac80211) as it's beta and conflicts with the 
#  stable ieee80211 based rt73 module
blacklist rt73usb

# Other modules that possibly conflict with rt73
blacklist rt2500usb
blacklist rt2x00lib
blacklist rt2x00usb

```**Download the latest version of the RT73 USB Enhanced Driver**
(in your home directory or in /tmp or wherever you like, it will no longer be needed after)
```
wget http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-3.0.3.tar.bz2
tar xjf rt73-k2wrlz-3.0.3.tar.bz2
cd rt73-k2wrlz-3.0.3

```you should now be in the top-level directory you just extracted ( rt73-k2wrlz-3.0.3 )

**Prepare DKMS config**
create a file in rt73-k2wrlz-3.0.3 directory, called dkms.conf
```

nano dkms.conf

```and paste the following in it:
```

PACKAGE_NAME="rt73-k2wrlz"
PACKAGE_VERSION="3.0.3"

# make sure kernel is 2.6.27 or newer, just in case
# http://homepages.tu-darmstadt.de/~p_larbig/wlan/
BUILD_EXCLUSIVE_KERNEL="2.6.(27|28|29|[3-9][0-9])"

MAKE[0]="make -C Module"
CLEAN="make -C Module clean"

BUILT_MODULE_NAME[0]="rt73"
BUILT_MODULE_LOCATION[0]="Module"
DEST_MODULE_LOCATION[0]="/kernel/drivers/net/wireless"

AUTOINSTALL="yes"

```**Create a traball archive of the source directory** (with our dkms.conf in it)
```

tar czf rt73-k2wrlz-3.0.3-dkms.tar.gz rt73-k2wrlz-3.0.3

```**Load the rt73-k2wrlz tarball to DKMS source tree**
```
sudo dkms ldtarball --archive=rt73-k2wrlz-3.0.3-dkms.tar.gz
```**Build rt73 module with DKMS**
```
sudo dkms build -m rt73-k2wrlz -v 3.0.3
```**Install rt73 module with DKMS**
```
sudo dkms install -m rt73-k2wrlz -v 3.0.3
```Insert you RT73 USB Wifi adapter and it should be automatically detected, and automatically configured for you by **NetworkManager** or **WICD** (whichever one you use) if you have either installed. I use NetworkManager, and it automatically detected my DLink DWA-110 USB soon after I plugged it in :)
Or alternatively you could install **RutilT**
```
sudo apt-get install rutilt
```Author's site: [http://bonrom.cbbknet.com/](http://bonrom.cbbknet.com/)
More info on making RutilT run in startup:
[http://ubuntuforums.org/showthread.php?t=502526](http://ubuntuforums.org/showthread.php?t=502526)

Hope this helps anyone :)


sorry for Asking guys...
im new in linux...
im using linksys wusb54gc that using RT2573 chipset...
can i use all this commands in backtrack 4 beta??
im completely noob in this!!!:confused: 
thanks 4 ur help guys...
im really appreciate it...:-)

---

### Post by Gourgi on 2009-09-22
anyone tried this in 2.6.31 kernel? (karmic maybe?)
does it still work?

---

### Post by sudo apt-get install on 2009-09-22
great tutorial dude :)

 thank you

---

### Post by jasmineaura on 2009-09-22
> **selfdz87 said:**
> sorry for Asking guys...
im new in linux...
im using linksys wusb54gc that using RT2573 chipset...
can i use all this commands in backtrack 4 beta??
im completely noob in this!!!:confused: 
thanks 4 ur help guys...
im really appreciate it...:-)

First, please dont quote an entire tutorial when replying..

Secondly, your question is off-topic for this thread, as this thread is clearly titled for RT73 USB only..

Nevertheless, if you have followed the link to p_larbig's site, which is mentioned at the very top of the tutorial, you would've quickly realized he also makes a RaLink RT2570USB Enhanced driver which may in fact work for you... But newb + lazy + can't read = a pity..
****

---

### Post by jasmineaura on 2009-09-22
> **Gourgi said:**
> anyone tried this in 2.6.31 kernel? (karmic maybe?)
does it still work?

From my [post #13]("http://ubuntuforums.org/showpost.php?p=7772586&postcount=13") above, if you cared to read it at all:

> For it to compile on Kernel 2.6.29, 2.6.30, etc.., in case you custom compile 2.6.30 like I did, you need to make sure you have the following kernel config option enabled:

"Networking Options" -> "Enable older network device API compatibility"
```
CONFIG_COMPAT_NET_DEV_OPS=y
```So it *should* work in 2.6.31, since I've tested it with 2.6.30 with the above added kernel config option.

If you're running a generic 2.6.31 kernel in karmic, check to see if it is enabled by default. For instance:

```
grep CONFIG_COMPAT_NET_DEV_OPS /boot/config-2.6.31-10-generic
```If it's not in there, then you will have to compile a new kernel to add it.
See: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
and: [http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/](http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/)

Good luck..

---

### Post by imaginatelo on 2009-10-02
Tengo instalado ubuntu 9.10 y al seguir tutorial en el paso 

sudo dkms build -m rt73-k2wrlz -v 3.0.3Me dice 

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-11-generic -C Module"....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.31-11-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/rt73-k2wrlz/3.0.3/build/ for more information.

se puede compilar con esta version

---

### Post by Gourgi on 2009-10-02
> **jasmineaura said:**
> From my [post #13]("http://ubuntuforums.org/showpost.php?p=7772586&postcount=13") above, if you cared to read it at all:

So it *should* work in 2.6.31, since I've tested it with 2.6.30 with the above added kernel config option.

If you're running a generic 2.6.31 kernel in karmic, check to see if it is enabled by default. For instance:

```
grep CONFIG_COMPAT_NET_DEV_OPS /boot/config-2.6.31-10-generic
```If it's not in there, then you will have to compile a new kernel to add it.
See: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
and: [http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/](http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/)

Good luck..

thanks for the answer.
karmic's kernel doesn't have CONFIG_COMPAT_NET_DEV_OPS enabled so custom kernel is required.
thanks for the kernel compilation links
:popcorn:

---

### Post by ijpatterson on 2009-10-05
Hi there

this is the best tutorial for installing this driver i have found so far but i still can't get it to work. I'm a complete ubuntu noob so bear with me.
i have created the dkms.conf file but i'm not sure i **Created a traball archive of the source directory **correctly becauce when i enter the code 

sudo dkms ldtarball --archive=rt73-k2wrlz-3.0.3-dkms.tar.gz 

i get sudo: dkms: command not found

I don't really understand any of this :( so i'd really apprieciate some help, thanks

Edit: erf sorry DKMS isn't installed, that's why it's not working >_< but I have a new problem now, when i type

sudo apt-get install dkms

it comes up with

E: Couldn't find package dkms

---

### Post by jasmineaura on 2009-10-06
> **ijpatterson said:**
> 
Edit: erf sorry DKMS isn't installed, that's why it's not working >_< but I have a new problem now, when i type

sudo apt-get install dkms

it comes up with

E: Couldn't find package dkms

Try:

```
sudo aptitude update
```

then

```
sudo aptitude install dkms
```

---

### Post by jasmineaura on 2009-10-06
> **imaginatelo said:**
> Tengo instalado ubuntu 9.10 y al seguir tutorial en el paso 

sudo dkms build -m rt73-k2wrlz -v 3.0.3Me dice 

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-11-generic -C Module"....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.31-11-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/rt73-k2wrlz/3.0.3/build/ for more information.

se puede compilar con esta version

Mira esto:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/292606](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/292606)

probablemente relacionadas :)

---

### Post by xtornado on 2009-11-16
can anyone build a modified kernel for karmic 9.10 x64 and x86 with
 
CONFIG_COMPAT_NET_DEV_OPS
and upload to rapidshare , so can this problem be solved forever???  and ofcourse to be in .deb  .

---

### Post by jasmineaura on 2009-11-17
> **xtornado said:**
> can anyone build a modified kernel for karmic 9.10 x64 and x86 with
 
CONFIG_COMPAT_NET_DEV_OPS
and upload to rapidshare , so can this problem be solved forever???  and ofcourse to be in .deb  .

you can report it as a bug against generic kernel in karmic on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux](https://bugs.launchpad.net/ubuntu/+source/linux)

this way the option can be included by default in future generic kernel builds :)

Feel free to post link to your bug report here afterward.

cheers

---

### Post by EnGeLMaN on 2009-11-18
Hi jasmineaura:

Im having the same build problem of imaginatelo, and i have checked the discussion you stated in [https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/292606](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/292606).

So far i have undestood that i have to add "1>&2" in my /etc/kernel/postinst.d/dkms file. The problem is that i don't know exactly where putting it.

my dkms file looks like this:

```
#!/bin/bash

# We're passed the version of the kernel being installed
inst_kern=$1

if [ -x /etc/init.d/dkms_autoinstaller ]; then
    if which invoke-rc.d >/dev/null 2>&1 ; then
        invoke-rc.d dkms_autoinstaller start $inst_kern
    else
        /etc/init.d/dkms_autoinstaller start $inst_kern
    fi
fi
exit 0
```

Would you mind to point me out me where do i have to add the "1>&2" ??

Really aprecciated. And sorry for my english.

EDIT: BTW my make.log is: 
```

DKMS make.log for rt73-k2wrlz-3.0.3 for kernel 2.6.31-14-generic-pae (i686)
mié nov 18 16:22:47 CET 2009
make: se ingresa al directorio `/var/lib/dkms/rt73-k2wrlz/3.0.3/build/Module'
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-14-generic-pae'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-14-generic-pae'
rt73.ko failed to build!
make: *** [module] Error 1
make: se sale del directorio `/var/lib/dkms/rt73-k2wrlz/3.0.3/build/Module'
```

EDIT2: Ok, I've re-read all the post again and I realized about the missing options on 2.6.31 kernels. Will try  to compile my own kernel when I find the time. The thing is, that I have made my rt73USB injects in previous versions of ubuntu, but not in newer ones. I'm bookmarking the post, just in case ;)

---

### Post by jason50146 on 2009-11-19
I am also interested in exactly where to put the "1>&2".  I've been trying to install the newest kernel from kernel.org and keep running into this problem.  I've tried putting th "1>&2" in lots of places, but can't seem to hit the sweet spot.

Thanks

---

### Post by jasmineaura on 2009-11-20
> **jason50146 said:**
> I am also interested in exactly where to put the "1>&2".  I've been trying to install the newest kernel from kernel.org and keep running into this problem.  I've tried putting th "1>&2" in lots of places, but can't seem to hit the sweet spot.

Thanks

I dunno what to say really... i mean, i quoted u guys the bug, but u cant read? :(

Again, the bug link:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/292606](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/292606)

Mike Stroyan in comment #17:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/292606/comments/17](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/292606/comments/17)

>  Adding "1>&2" to the invocation of /etc/init.d/dkms_autoinstaller keeps stdout clean.

meaning, find the line that invokes `/etc/init.d/dkms_autoinstaller` and add "1>&2" at the end of that  line (without the quotes) :D

enjoy :p

---

### Post by xtornado on 2009-11-21
i have start compile kernel 2.6.31 in karmic . ih had enter in "Networking Options  but CAN`T SEE 
Enable older network device API compatibility   ..  please look my video i show you....

[http://www.youtube.com/watch?v=LLp6H48RvZI](http://www.youtube.com/watch?v=LLp6H48RvZI)

:(

---

### Post by eliazebe on 2009-11-21
I don't hunderstand the position when add 1>&2.... 

Can you copy the code with the changes?

---

### Post by eliazebe on 2009-11-23
> **eliazebe said:**
> I don't hunderstand the position when add 1>&2.... 

Can you copy the code with the changes?


?????????????????????

---

### Post by blackmoon105 on 2009-12-21
A .deb package for Ralink RT73 Wireless Lan USB Enhanced Driver (**rt73-k2wrlz**) for Karmic 9.10 is available here: [https://edge.launchpad.net/~marco/+archive/ppa/+packages]("https://edge.launchpad.net/%7Emarco/+archive/ppa/+packages")

---

### Post by jasmineaura on 2009-12-22
> **eliazebe said:**
> I don't hunderstand the position when add 1>&2.... 

Can you copy the code with the changes?

The bug has been fixed in the package dkms - 2.1.1.0-0ubuntu1
Please check this bug thread for more info: [https://bugs.launchpad.net/bugs/292606](https://bugs.launchpad.net/bugs/292606)

> **blackmoon105 said:**
> A .deb package for Ralink RT73 Wireless Lan USB Enhanced Driver (**rt73-k2wrlz**) for Karmic 9.10 is available here: [https://edge.launchpad.net/~marco/+archive/ppa/+packages]("https://edge.launchpad.net/%7Emarco/+archive/ppa/+packages")

Great, thanks!
That'll save a lot of people who use the generic kernel from having to compile custom kernel just for this :)
Guess the "Enable older network device API compatibility" kernel option (and custom compilation) is no longer needed, per this:
[http://launchpadlibrarian.net/37024890/rt73-k2wrlz_3.0.3-2~ppa0~karmic_source.changes](http://launchpadlibrarian.net/37024890/rt73-k2wrlz_3.0.3-2~ppa0~karmic_source.changes)
> * Support for the new net_device_ops API (tpark patch)

Though the interface has now been renamed to ralan, ugh..

---

### Post by blackmoon105 on 2009-12-22
> **jasmineaura said:**
> Guess the "Enable older network device API compatibility" kernel option (and custom compilation) is no longer needed
Yes, no custom kernel compilation is needed :)

> Though the interface has now been renamed to ralan, ugh..Yes, the interface name now is "ralan".

---

### Post by Gourgi on 2009-12-23
> **blackmoon105 said:**
> A .deb package for Ralink RT73 Wireless Lan USB Enhanced Driver (**rt73-k2wrlz**) for Karmic 9.10 is available here: [https://edge.launchpad.net/~marco/+archive/ppa/+packages]("https://edge.launchpad.net/%7Emarco/+archive/ppa/+packages")

thanks and many kisses!
much appreciated ;)

---

### Post by Adam_AU on 2009-12-25
Im Running Backtrack 4 through vmware workstatin 7.0


Getting some errors guys, help would be very much appreciated.

```
apt-get install dkms
```

The following packages have unmet dependencies:
  dkms: Depends: linux-headers but it is not installable
E: Broken packages

```
sudo aptitude update
```

All Good, Then i tried

```
sudo aptitude install dkms 
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages are BROKEN:
  dkms
The following partially installed packages will be configured:
  postgresql postgresql-8.3
0 packages upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 55.5kB of archives. After unpacking 381kB will be used.
The following packages have unmet dependencies:
  dkms: Depends: linux-headers which is a virtual package.
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  dkms
The following partially installed packages will be configured:
  postgresql postgresql-8.3
0 packages upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 55.5kB of archives. After unpacking 381kB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  dkms: Depends: linux-headers which is a virtual package.
Resolve these dependencies by hand? [N/+/-/_/:/?]   

postgresql is screwing me round here, anyone ran across this before?

---

### Post by jasmineaura on 2009-12-26
> **Adam_AU said:**
> Im Running Backtrack 4 through vmware workstatin 7.0


Getting some errors guys, help would be very much appreciated.

[...]

postgresql is screwing me round here, anyone ran across this before?

That question would be better asked in backtrack forum
[http://forums.remote-exploit.org/](http://forums.remote-exploit.org/)

---

### Post by Adam_AU on 2009-12-27
> **jasmineaura said:**
> That question would be better asked in backtrack forum
[http://forums.remote-exploit.org/](http://forums.remote-exploit.org/)

Im aware, they have sent me here =P. Backtrack 4 is Ubuntu. This thread is "Patched for Injection etc..." Im pretty sure it applies to what im after.

---

### Post by jasmineaura on 2009-12-27
BlackMoon

postgres has nothing to do with dkms... it just a "by the way" thing that apt-get / aptitude tells you every time you run them....

Notice:
> The following partially installed packages will be configured:
  postgresql postgresql-8.3

Keyword here is "partially installed"... If you're not using postgres, you can safely:
```
sudo aptitude remove psotgresql postgresql-8.3
```

Now, what is relevant is:
> dkms: Depends: linux-headers which is a virtual package.
Unable to resolve dependencies!  Giving up...


Of course dkms needs the kernel headers (linux-headers package)... It should've been installed automatically, but... seems like you might have an outdated apt-cache

First do this:
```
sudo aptitude update
```

then:
```
sudo aptitude safe-upgrade
```

then:
```
sudo aptitude install linux-headers
```

then finally:
```
sudo aptitude install dkms
```

Good luck

---

### Post by Adam_AU on 2009-12-29
When i try to install the linux headers i get these errors.

```
sudo aptitude install linux-headers
```

The following NEW packages will be installed:
  libssh2{a}
The following packages will be REMOVED:
  libncp{u} libssh2-1{u}
The following partially installed packages will be configured:
  medusa
0 packages upgraded, 1 newly installed, 2 to remove and 4 not upgraded.
Need to get 0B/309kB of archives. After unpacking 1294kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 226036 files and directories currently installed.)
Unpacking libssh2 (from .../libssh2_1.2.2-bt0_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libssh2_1.2.2-bt0_all.deb (--unpack):
 trying to overwrite `/usr/lib/libssh2.so.1', which is also in package libssh2-1
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libssh2_1.2.2-bt0_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of medusa:
 medusa depends on libssh2; however:
  Package libssh2 is not installed.
dpkg: error processing medusa (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 medusa
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

---

### Post by strongman on 2010-01-09
I installed the .deb package from this page [https://edge.launchpad.net/~marco/+archive/ppa/+sourcepub/908504/+listing-archive-extra]("https://edge.launchpad.net/%7Emarco/+archive/ppa/+sourcepub/908504/+listing-archive-extra") and my wireless won't connect to internet anymore. I checked the dkms version and it's the same as it was before install, 2.1.0.1. I'm using Karmic 9.10. Anybody know what happened and how to fix it?

---

### Post by strongman on 2010-01-10
I fixed the problem by deleting 
```

/usr/src/rt73-k2wrlz-3.0.3.dkms.tar.gz
/usr/share/doc/rt73-k2wrlz-source
/etc/modprobe.d/rt73.conf
/etc/modprobe.d/blacklist-rt73.conf

```

then running ubuntu 9.10 live CD, after this i rebooted and wireless was back. I still don't have injection though.

---

### Post by blackmoon105 on 2010-01-11
Someone else have encountered the same problem of strongman?

---

### Post by ryandigweed on 2010-01-15
> **jasmineaura said:**
> Try:

```
sudo aptitude update
```

then

```
sudo aptitude install dkms
```
Hey, im new here.. im using BACKTRACK3 live cd with a dlink DWa-110 usb.. using this chip. i i type these comands and i get errors.. saying command not found.. what should i do?

---

### Post by ryandigweed on 2010-01-15
> **blackmoon105 said:**
> A .deb package for Ralink RT73 Wireless Lan USB Enhanced Driver (**rt73-k2wrlz**) for Karmic 9.10 is available here: [https://edge.launchpad.net/~marco/+archive/ppa/+packages]("https://edge.launchpad.net/%7Emarco/+archive/ppa/+packages")

ok.. no longer BT3 live cd.. now installed Bt4 final to the harddrive.. and installed DKMS 2.0 from softpedia linux. and all goes well till i go to build the dkms.. it says cannt be found in dkms tree.. or dkms tree cant be found in source...for rt73 and iwl4956 chipsets are there any .debs to install to get them working??.. is there anyone who has it all loaded.. and who could just share it as a file which i could install?.. thank you.. :)

---

### Post by trevelyn on 2010-03-21
no.  the actual option in the kernel tree is gone.  RT73 is dead if you are using 2.6.31+ The tutorial from page one yields:

```
bad exit status 2
```

after trying to compile code as user nobody.

I downloaded the source for the linux kernel and after running make menuconfig, I can confirm that: 

CONFIG_COMPAT_NET_DEV_OPS

is gone.  Can you possibly patch rt73usb to inject?  And the 'usb' in the device name is not just Wireshark, that is libpcap that ***** itself, I have seen that happen in the past while using it in C.  I have had to use things like udev to rename the devices that contained usb to something else before.

Maybe we [2.6.31+] just have to wait for a new rt73 driver. :(

---

### Post by trevelyn on 2010-03-21
whoopsy, I guess you can inject with rt73usb right out of the box!

[IMG]http://weaknetlabs.com/temp/inject.png[/IMG]

I simply used airmon-ng after install "iw" 

```

apt-get install iw
airmon-ng start <device>

```

This makes a VAP (in my case it was labeled "mon0")

and then authenticated and associated and then plugged into router via ethernet and got IP, pinged something that didn't exist: 1.1.1.1 and poof! I got ARP replay attack working flawlessly.

I am kinda old school and have no faith in out-of-the-box injection so i never even tried it.  Awesome.  2.6.31-14 generic works.

EDIT: according to aircrack-ng.org: "This fix is already included in 2.6.31 and newer kernels, so this patch should only be used up to 2.6.30." (pertaining to patches for drivers to inject)

~douglas

---

### Post by jasmineaura on 2010-03-22
Doug,

This tutorial only dealt with the legacy ieee80211 version of the RT73 driver (p_larbig/ASPj mods), hence why we needed to blacklist the mac80211 driver version.

The driver bundled with karmic is the mac80211 based one (which depends on rt2x00usb & rt2x00lib). That's why you needed to install the tool "IW" (needed for stacks-mac80211 interface management)

To understand the differences, see [mac80211 versus ieee80211 stacks]("http://www.aircrack-ng.org/doku.php?id=install_drivers#mac80211_versus_ieee80211_stacks") write-up.

I have not tested the mac80211 driver's monitor mode and injection capabilities, so you may have to try both and see which works best. I did have some stability problems with the mac80211-based rt73usb driver (the default in karmic) with network-manager (specifically frequent AP drops, and /var/log/daemon.log flooding) and had to make a switch to "wicd" (replaces network-manager) to get a stable wifi connection just for general use.

Having said that, it is **possible** to build the (legacy) driver covered in this tutorial, version 3.0.3, on a 2.6.31 kernel, but you need a temporary workaround to be able to build it successfully until a new version is released (hopefully soon).
See [this thread]("http://forum.aircrack-ng.org/index.php?topic=1824.msg33360#msg33360") for a workaround.

Cheers

---

### Post by trevelyn on 2010-03-31
Oh that link about the stacks was a nice read! :) Thanks!  

I was simply having troubles with installing the older driver for injection.  I used the same driver from serialmoney for injection for years and finally with karmic it wouldn't compile at all.  I saw the older API missing from the kernel config and tested the rt73usb which injected right out of the box.  

The stability of said driver was not tested, I was only concerned with injection.  I don't use network-manager or WICd any longer.  I simply do it by hand, shell scripts or Perl GUI applications (for friends and relatives).  

I don't add anything to my kernels either.  Doing so seems harder to switch between drivers.  When I compile my kernels I make them all modules, so one can drop (via modprobe), say ath5k, and use madwifi-ng for AirPWN, etc.  I was quite pleased with rt73usb's injection performance!

Thanks again! :D

---

### Post by T3sla on 2010-05-31
I tried several times but they all fail at this point : ```
sudo dkms install -m rt73-k2wrlz -v 3.0.3
``` with the following error :
```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.32-22-generic -C Module....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.32-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/rt73-k2wrlz/3.0.3/build/ for more information.
0
0
ERROR: binary package for rt73-k2wrlz: 3.0.3 not found

```I have the same issue with 9.04, 9.10 and 10.04.I can't figure out what i'm doing wrong, i followed the guide carefully.

---

### Post by jasmineaura on 2010-06-05
> **T3sla said:**
> I tried several times but they all fail at this point : ```
sudo dkms install -m rt73-k2wrlz -v 3.0.3
``` with the following error :
```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.32-22-generic -C Module....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.32-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/rt73-k2wrlz/3.0.3/build/ for more information.
0
0
ERROR: binary package for rt73-k2wrlz: 3.0.3 not found

```I have the same issue with 9.04, 9.10 and 10.04.I can't figure out what i'm doing wrong, i followed the guide carefully.

Check my post [#50]("http://ubuntuforums.org/showpost.php?p=9011231&postcount=50")
and the previous post #49

You're running 2.6.32
The patch covered in this tutorial only works up to kernel 2.6.30
2.6.31 onwards incorporates mac80211 driver which has injection support

good luck

---

### Post by blastw on 2011-11-27
Hello, I really sorry for up this topic but I have the same problem. 

I follow all steps and get stuck at:

```
sudo dkms build -m rt73-k2wrlz -v 3.0.3
```When I try I get this response:

```

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.38 -C Module....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.38 (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/rt73-k2wrlz/3.0.3/build/ for more information.
0
0
ERROR: binary package for rt73-k2wrlz: 3.0.3 not found
```Looking at the make.log:

```
DKMS make.log for rt73-k2wrlz-3.0.3 for kernel 2.6.38 (x86_64)
Sun Nov 27 23:31:47 BRST 2011
make: Entering directory `/var/lib/dkms/rt73-k2wrlz/3.0.3/build/Module'
make[1]: Entering directory `/usr/src/linux-source-2.6.38'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.38/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-source-2.6.38'
rt73.ko failed to build!
make: *** [module] Error 1
make: Leaving directory `/var/lib/dkms/rt73-k2wrlz/3.0.3/build/Module'
```I take a look in the workaround and unfortunately dont find any .o  or .ko file in the Module directory. 

I using Backtrack 5. 
Please, any help is appreciated. 
Thanks.

---

