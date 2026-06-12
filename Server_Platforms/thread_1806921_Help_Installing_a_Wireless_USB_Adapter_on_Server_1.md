---
title: "Help Installing a Wireless USB Adapter on Server 10.04"
date: 2011-07-18
forum: Server Platforms
---

### Post by BlueVark on 2011-07-18
Hi Good Folks,

I'm having a hard time installing a TP-Link Wireless USB Adapter (Model TL-WN722N) on my Ubuntu Server, version 10.04.  I know the adapter uses a newer driver (ath9k_htc) that is not available in 10.04, but when I try to install the driver I continue to get errors and the driver will not load correctly.  

The adapter is recognized as:  
Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc.

I have tried installing numerous packages from compat-wireless and none have worked so far.  The main problem seems to occur when I run the "make" command I get the following errors: 

make[1]: *** [_module_/home/mike/compat-wireless-2.6.32] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
make: *** [modules] Error 2

Then the "make install" command will not run correctly and the adapter continues to be unrecognized.  I'm not sure how to fix this error.  

Any help you can provide would be greatly appreciated as I an at the end of my Ubuntu Server knowledge.  

Thanks...Mike

---

### Post by Entilza on 2011-07-18
So you have the new drivers source?  Are you trying to compile the kernel with the driver as a module or are you just going into the new driver's directory and typing make?

---

### Post by BlueVark on 2011-07-18
Here is the way I have been doing it:

Download package from compat-wireless,unpack it and then run the following:

cd compat-wireless-2.26.32
./scripts/driver-select ath9k
make
sudo make install

---

### Post by Wayne_V on 2011-07-18
2.6.32-24 is pretty old.  are you sure that's your kernel (uname -a)

---

### Post by Entilza on 2011-07-18
That is his kernel I believe you have the 10.04.00 LTS.

Anyway I compiled this driver with no problems.  I am assuming you are missing some compiling development tools.

Try getting some of these tools:

sudo apt-get install fakeroot kernel-wedge build-essential makedumpfile kernel-package libncurses5 libncurses5-dev

Maybe get the kernel source too if the make still complains.

Also afterwards make sure you rmmod the old driver in memory check with lsmod to see if it's already loaded before you load the new one.

---

### Post by BlueVark on 2011-07-18
OK...making some progress.  Thanks to Entilza I loaded the following tools:

sudo apt-get install fakeroot kernel-wedge build-essential makedumpfile kernel-package libncurses5 libncurses5-dev

and now the "make" command runs fine and the "sudo make install" runs fine.  However, after a reboot the adapter is still not being activated and/or recognized.  

Any ideas on where to go now?

---

### Post by Entilza on 2011-07-18
Cool, you're almost there.. Did you try modprobe drivername?  Find out where it installed it.  

Also as I said earlier make sure you don't have the old one in memory check by doing lsmod and see what's listed.

if you see an old driver there remove it with rmmod drivername.

read up on these commands:  lsmod, rmmod, modprobe

---

### Post by BlueVark on 2011-07-18
OK...it appears the driver is loaded.  Here's the "lsmod":

Module                  Size  Used by
ath9k                 306333  0
mac80211              205146  1 ath9k
ath                     7611  1 ath9k
cfg80211              126517  3 ath9k,mac80211,ath
led_class               2864  1 ath9k
fbcon                  35102  71

My driver is "ath9K" and there is no conflicts that I can see.  However, the adapter is not being activated and "iwconig" still show "no wireless extensions"

Any ideas?  

Thanks so much for your help!!!

---

### Post by Wayne_V on 2011-07-18
check dmesg for any errors.

did you follow the steps here:  [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

---

### Post by BlueVark on 2011-07-18
> **Wayne_V said:**
> check dmesg for any errors.

did you follow the steps here:  [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

Thanks Wayne,

What am I looking for when I run the "dmesg"?  There don't appear to be any errors.  

Yes, I have followed the directions at the above website.  That is how I got to this point.  But I can't get the adapter to activate or be recognized.  

Does it matter what file I download from "linuxwireless"?  My current Kernal is Linux 2.6.32-33-generic-pae on i686.  FYI...I have already tried the latest compat-wireless file and an older one for the 2.6.32 kernal.

---

### Post by Entilza on 2011-07-18
Check the Unloading and Loading sections in that walkthrough

Does it match the walkthrough?

Try unloading and loading them manually and see if any errors show.

---

### Post by Wayne_V on 2011-07-18
first, try:

# modules="cfg80211 mac80211 ath9k"
# for i in $modules; do sudo modprobe -l $i; done

and make sure the path is to the new driver.

Then, try to 'modprobe -v ath9k'.  If there are errors they should show up at the end of the dmesg output.

---

### Post by BlueVark on 2011-07-18
> **Wayne_V said:**
> first, try:

# modules="cfg80211 mac80211 ath9k"
# for i in $modules; do sudo modprobe -l $i; done

and make sure the path is to the new driver.

Then, try to 'modprobe -v ath9k'.  If there are errors they should show up at the end of the dmesg output.

OK...followed suggestion above.  Here's the end of the "dmesg":
[ 1583.148067] usb 1-1: USB disconnect, address 2
[ 1585.932020] usb 1-1: new high speed USB device using ehci_hcd and address 3
[ 1586.081740] usb 1-1: configuration #1 chosen from 1 choice

Does this tell you anything?  Looks like the there is a "new high speed USB device..."  What next?

---

### Post by Entilza on 2011-07-18
Don't forget to unload any old ones.. you tried restarting the network and nothing in iwconfig??  what about ifconfig

---

### Post by BlueVark on 2011-07-18
> **Entilza said:**
> Don't forget to unload any old ones.. you tried restarting the network and nothing in iwconfig??  what about ifconfig

Yep...tried all the above.  There are no other drivers loaded.  I restarted the network.  Command "ifconfig" only shows my wired eth0 connection.  Command "iwconfig"  shows "no wireless extensions".

---

### Post by BlueVark on 2011-07-18
OK...real progress.  I got the right driver loaded, the adapter is activated and ready to connect to my router.  :D:D:D

Next question...How do I connect to the WiFi router and input my WPA password via the command line?  

Thanks again for all the help...I'm getting close to solving this one.

---

### Post by Wayne_V on 2011-07-19
you should be able to use iwconfig with the essid and key options to connect.

you can also configure /etc/network/interfaces to bring it up on boot.  See 'man interfaces',  'man wireless'  and/or here:  [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by BlueVark on 2011-07-19
Thanks for all your help.  

Finally, I got this to work.  After getting the correct driver to load, I had to load and set-up wpa supplicant and then edit the etc/network/interfaces file and now it works perfectly.  

FYI...Setting up this adapter was not easy to figure out.  The documentation was difficult to follow and spread out over many different locations.   I had to spend many hours sorting through Google searches before finding something that would work for my situation.  I estimate that it took me at least 8 to 10 hours (over 3 days) of working on this before I finally got the answer.  But, I learned a lot and I'm thankful for the good folks on this forum who offer their time and expertise to help novices like me.  :):):)

---

### Post by albun on 2012-03-05
I think I found an "easier" way after fighting for a day with the ath9k_htc driver  install. This driver is needed for the TL-WN722N adapter to function,  and I had no luck trying to compile ath9k_htc from all kinds of  "wireless backports" packages.

This card's chipset (Atheros  AR9271) is supported out of the box in the later Linux kernel versions,  so I upgraded my "native" 10.04 2.6.32-37 generic kernel version to the  latest available for Ubuntu Lucid LTS (kernel 3.0.0-15-generic),  downloaded and installed firmware v. 1.3 for AR9271 and the adapter  started working after a reboot.

Here are the steps:

Note: I  have an Nvidia video card that was using a "non-free" driver, so I  first had to disable that driver via System -> Administration ->  Hardware Drivers


Checked what kernel version I had installed
Applications -> Accessories -> Terminal

```

uname -r

```

It showed "2.6.32-37-generic", so that told me that I needed to upgrade to a "generic" kernel version.

Installed  the latest backported Oneiric kernel (version 3.0) using System ->  Administration -> Synaptic Package Manager by selecting and  installing linux-headers-generic-lts-backport-oneiric and  linux-image-generic-lts-backport-oneiric. These two packages pulled with  them the latest available 3.x generic kernel and headers.

Downloaded to the Downloads directory htc_9271.fw and htc_7010.fw firmware files (both of them just in case :grin:) from [http://wireless.kernel.org/download/htc_fw/1.3/](http://wireless.kernel.org/download/htc_fw/1.3/) using Firefox and installed (copied) them to /lib/firmware/ directory via Terminal

```

cd
cd Downloads
sudo cp *.fw /lib/firmware

```

Next, rebooted with the TL-WN722N adapter plugged in and that was it.

I  hope this may help some people to stay out of trouble since this  TP-Link TL-WN722N adapter is so popular. This should also work if you  have any other adapter based on the Atheros AR9271 chipset.

P.S. For my Nvidia card I had to also get the latest Nvidia driver from the [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") PPA (ppa:ubuntu-x-swat/x-updates). It got installed just fine with the new kernel.

---

