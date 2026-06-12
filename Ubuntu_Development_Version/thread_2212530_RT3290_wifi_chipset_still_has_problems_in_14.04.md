---
title: "RT3290 wifi chipset still has problems in 14.04"
date: 2014-03-21
forum: Ubuntu Development Version
---

### Post by Swanyl on 2014-03-21
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466) is still a problem in 14.04

I have tried numerous patches to the official drivers none of which work with 14.04.  I am unable to get the drivers compiled and working.

Out of the box ubuntu insists on using rt2800pci drivers which do not work properly with this chipset.  

I have tried numerous linux distributions to try and get this working and have been unable to get it functioning in any of them.   It runs incredibly slowly and disconnects regularly on everything i try.

I have followed numerous guides which don't work and even tried ndiswrapper with the windows drivers which again do not work.

There appears to be quite a number of people out there with the same problem.

Please help

---

### Post by sdowney717 on 2014-03-21
Why not get a different usb wifi device that does work and very well?
RaLink 5370 off ebay for about $6.

[http://www.ebay.com/bhp/ralink-rt5370](http://www.ebay.com/bhp/ralink-rt5370)
It works plug and play and is fast.

I struggled with a mn730 legacy broadcom chip and just gave up getting it to work like it should as good speeds is apparently impossible.
Here is mine

the fast one is the ralink 5370 miniature usb wifi wlan1.

---

### Post by Swanyl on 2014-03-21
That really isn't a solution i don't want a wifi dongle hanging off my laptop and i don't want to open it up and replace a chip.

---

### Post by pqwoerituytrueiwoq on 2014-03-21
> **sdowney717 said:**
> Why not get a different usb wifi device that does work and very well?
RaLink 5370 off ebay for about $6.
seems a little much i got a internal [Intel 2230 chip](http://www.intel.com/content/www/us/en/wireless-products/centrino-wireless-n-2230.html) for $4.50, i think the lowest one is ~5.50 now

---

### Post by Swanyl on 2014-03-21
This is a problem that seemingly had a fix released 2 years ago yet is still present in 14.04.

the rt3290 is used in a lot of laptops and a quick google search shows a lot of people have the same problem as me yet every fix i've tried from these results has failed to work for me. 

buying a usb device is not a solution please stop suggesting this.

Not everyone lives in a country where it is cheap or easy to buy a wifi device,  very few want a device hanging off the side of their laptops and even fewer want to open up their laptops to swap out the wifi card.

---

### Post by sdowney717 on 2014-03-21
you may not have a choice except changing the wifi card.
[http://www.pcauthority.com.au/Feature/292597,how-to-upgrade-your-laptops-wi-fi-adapter.aspx](http://www.pcauthority.com.au/Feature/292597,how-to-upgrade-your-laptops-wi-fi-adapter.aspx)

---

### Post by sdowney717 on 2014-03-21
[http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)

did you spend time trying this?

---

### Post by Swanyl on 2014-03-21
> **sdowney717 said:**
> [http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)

did you spend time trying this?

yes the drivers do not compile when downloaded.  When changing the various files gedit os/linux/pci_main_dev.c and config.mk it does not compile.  Using various patches for the drivers including 	[https://www.dropbox.com/s/v0kaibq0f4to0k2/rt3290sta.patch](https://www.dropbox.com/s/v0kaibq0f4to0k2/rt3290sta.patch) does not let the drivers compile.

Using the random drivers from the dropbox in that post do not compile.

Using this deb file from the russian ubuntu site [http://forum.ubuntu.ru/index.php?topic=232103.0](http://forum.ubuntu.ru/index.php?topic=232103.0) does not work.  

I've spent hours trying to get this to work.  

It seems there is a debian fix for this
[https://packages.debian.org/jessie/firmware-ralink](https://packages.debian.org/jessie/firmware-ralink)

taken from here
[http://unix.stackexchange.com/questions/115958/how-do-i-get-a-ralink-rt3290-wireless-card-working-on-debian-jessie](http://unix.stackexchange.com/questions/115958/how-do-i-get-a-ralink-rt3290-wireless-card-working-on-debian-jessie)

although i have no idea how to get this on my ubuntu

There is also an AUR from archlinux
[https://aur.archlinux.org/packages/rt3290sta-dkms/](https://aur.archlinux.org/packages/rt3290sta-dkms/)

again i have no idea how to get this working on ubuntu.

I tried debian but had problems with booting my laptop and i don't fancy using arch linux.

---

### Post by cariboo on 2014-03-21
@Swanyl , you could create a feature request bug to get the firmware included in Ubuntu. [Here]("https://answers.launchpad.net/launchpad/+questions?field.sort=by%20relevancy&field.language-empty-marker=1&field.actions.search=Search&field.status=Open&field.status=Needs%20information&field.status=Answered&field.status=Solved&field.search_text=Feature%20request") are some feature request examples.

---

### Post by Swanyl on 2014-03-21
> **cariboo907 said:**
> @Swanyl , you could create a feature request bug to get the firmware included in Ubuntu. [Here]("https://answers.launchpad.net/launchpad/+questions?field.sort=by%20relevancy&field.language-empty-marker=1&field.actions.search=Search&field.status=Open&field.status=Needs%20information&field.status=Answered&field.status=Solved&field.search_text=Feature%20request") are some feature request examples.

is

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

not a feature request?

---

### Post by Swanyl on 2014-03-22
I have tried to mark it as affecting Trusty here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

But it says No items matched "Trusty Tahr".

If anyone can help i'd be grateful.

---

### Post by Swanyl on 2014-03-24
Is no one able to help me?

---

### Post by pqwoerituytrueiwoq on 2014-03-24
lets assume for a minute it is something else that is the issue
What is your distance from your router, how is your router configured for wifi (wireless N, Wireless G, Channel Width)
have you checked your area for interference? (choose the best wifi channel for your area)
my RT5390 was pretty touchy with my router's wifi settings when using my wireless N router

for some of these you will need to log into the router to find out, others can be obtained from this script
[http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)

---

### Post by Swanyl on 2014-03-25
It is a problem with the drivers.

The laptop is in the same room as the router. I have other devices using the router with no problems.  I have switched between N G and multiple channel widths.

The laptop worked fine in windows using this router.

Ubuntu reverts to rt2800pci drivers which do not work properly with this card.  

Others seem to have managed to fix their problem by compiling the mediatek drivers and installing them.  I am unable to compile these with ubuntu x64 14.04.  I have tried the different patches various people have released and various drivers from dropbox and a russian ubuntu site to no avail.

---

### Post by pqwoerituytrueiwoq on 2014-03-25
how does one attempt to compile this driver after downloading the driver from [mediatech](http://www.mediatek.com/en/downloads/rt3290-pcie/)

---

### Post by sdowney717 on 2014-03-26
If someone can figure out how to compile, then they can make a deb file.
Or they can compile it and send him the make install folder.

---

### Post by eduardosuarez-2 on 2014-04-07
Hi Swanyl,

I installed the following kernel from kernel.org on 13.10:

```
~$ uname -r
3.12.0-031200-generic

```

And the Wi-Fi works fine. The problem is that you will miss the Ubuntu Kernel updates. I've spent a lot of time trying to make it work too and finally give up.

There is another problem (I think, since I didn't try to reproduce it), after a laptop wake up, it was impossible for me to boot the system again with that kernel, so I disabled the suspend on inactivity feature.

Ok, I know I know, it doesn't solve the problem, but I think it's a pretty simple workaround for the problem. I not sure if it will work on 14.04, but probably it will (I think I'll try it today).

---

### Post by Swanyl on 2014-04-12
> **eduardosuarez-2 said:**
> Hi Swanyl,

I installed the following kernel from kernel.org on 13.10:

```
~$ uname -r
3.12.0-031200-generic

```

And the Wi-Fi works fine. The problem is that you will miss the Ubuntu Kernel updates. I've spent a lot of time trying to make it work too and finally give up.

There is another problem (I think, since I didn't try to reproduce it), after a laptop wake up, it was impossible for me to boot the system again with that kernel, so I disabled the suspend on inactivity feature.

Ok, I know I know, it doesn't solve the problem, but I think it's a pretty simple workaround for the problem. I not sure if it will work on 14.04, but probably it will (I think I'll try it today).


I gave up long ago and installed arch linux and its working fine there.  Thanks for trying to help though.

---

### Post by past-first on 2014-06-02
Hi all, 
I fixed and successfully compiled rt3290 driver for the amd64 and core 3.13 (Ubuntu 14.04)

Patched version here (mirrors):

[https://www.dropbox.com/s/x5obvb5udg6gl09/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz](https://www.dropbox.com/s/x5obvb5udg6gl09/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz)
[URL="http://shareplace.com/?09D7C3A436"]http://shareplace.com/?09D7C3A436
[/URL]
1. Unpack it to any folder
2. cd <folder in which you unpacked the archive contents>
3. sudo apt[COLOR=#339933]-[/COLOR]get update
4. sudo apt[COLOR=#339933]-[/COLOR]get install build[COLOR=#339933]-[/COLOR]essential linux[COLOR=#339933]-[/COLOR]headers[COLOR=#339933]-[/COLOR]generic 
5. sudo make
6. sudo make install

---

### Post by cariboo on 2014-06-02
> **past-first said:**
> Hi all, 
I fixed and successfully compiled rt3290 driver for the amd64 and core 3.13 (Ubuntu 14.04)

Patched version here (mirrors):

[https://www.dropbox.com/s/x5obvb5udg6gl09/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz](https://www.dropbox.com/s/x5obvb5udg6gl09/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz)
[URL="http://shareplace.com/?09D7C3A436"]http://shareplace.com/?09D7C3A436
[/URL]
1. Unpack it to any folder
2. cd <folder in which you unpacked the archive contents>
3. sudo apt[COLOR=#339933]-[/COLOR]get update
4. sudo apt[COLOR=#339933]-[/COLOR]get install build[COLOR=#339933]-[/COLOR]essential linux[COLOR=#339933]-[/COLOR]headers[COLOR=#339933]-[/COLOR]generic 
5. sudo make
6. sudo make install

With that, this thread is closed, as Trusty was released in April, and we are now discussing Utopic. Thread closed.

---

### Post by Bucky Ball on 2015-12-15
Just before we go any further, could you plug in with an ethernet cable, get online and do an update (use the Software Updater), please? Then, once the update is finished, unplug the ethernet cable and reboot the machine. Once you're back at the desktop are you told 'Wireless networks available'? If you click the network icon are there networks listed? Is Wifi and Ethernet ticked and enabled?

I'll dig some more, but if you do a search for 'RT3290 ubuntu 14' you will find plenty of clues.

---

### Post by cariboo on 2015-12-15
@Bucky Ball , this thread was closed in June of 2014, the op won't be back. :)

---

