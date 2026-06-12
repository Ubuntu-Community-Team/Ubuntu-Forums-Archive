---
title: "Starling and Ubuntu 10.04"
date: 2010-04-16
forum: System76 Support
---

### Post by Eyore15 on 2010-04-16
Do we anticipate the same problems upgrading the Starling to 10.04 as we had when [trying] to upgrade to 9.10?

---

### Post by thomasaaron on 2010-04-16
Unfortunately, the wireless driver for the Starling didn't make it into Lucid, which just means once you upgrade (or do a fresh install), you will need to download/install/run your System76 Driver.

Other than that, though, we're not seeing any other issues with the Starling.

And remember, most of the hosed upgrades I *do* see are from the initial rush upgrade on release day.

---

### Post by gamerchick02 on 2010-04-16
I've already upgraded to Lucid, and I don't see a problem with wireless (right now).

No issues using it in my bedroom (upstairs in my house), or anywhere else in my house, for that matter.

I've also upgraded on the Pangolian, and I haven't seen any issues either.

Just my two cents...

Amy

---

### Post by HotShotDJ on 2010-04-16
> **gamerchick02 said:**
> I've already upgraded to Lucid, and I don't see a problem with wireless (right now).

No issues using it in my bedroom (upstairs in my house), or anywhere else in my house, for that matter.

I've had a similar experience with my friend's Starling.  No issues with wireless.  BUT, I've only tried it here in my little apartment.  I'm not sure how it would work with a public access point, such as a coffee house or hotel.

> **gamerchick02 said:**
> I've also upgraded on the Pangolian, and I haven't seen any issues either.Which Pangolin do you have?  On my PanP5 with the default Lucid installation, ACPI events don't get handled, leaving my Bluetooth stuck off, my Wifi stuck on, and the lid status switch broken.  However, there is a patch for this that will probably make it into Lucid final (once they work out a pretty bad regression that the patch causes on some systems - it seems to have caused a "divide by zero" error on some computers - OOPS! -- I'm currently back-porting and testing the latest patch that purports to correct that regression... so we shall see...  see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/526354](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/526354) if you wish to follow that bug)

---

### Post by gamerchick02 on 2010-04-16
@HotShotDJ:

I have a PanP5.  I don't use anything Bluetooth, so I shut that bit off.

*shrug* Different needs.  Thanks for the bug link.

Amy

---

### Post by bvandev on 2010-04-18
For the record, I added Lucid to my Starling as a dual boot option a few weeks ago.  The wireless worked out of the box, but poorly.  After running the System76 driver the wireless does not work at all.  The light does not go on.

Please note, I'm not complaining.  System76 has made it clear we should wait for them to update the driver.

---

### Post by thomasaaron on 2010-04-19
I don't think the System76 driver messed up your wireless in Lucid, as we've not released one that will even run on Lucid yet. Are you sure you are running Lucid?

Press the toggle switch on the front-right-leading edge of your computer ONCE to the right and restart. Does your wireless LED come on?

---

### Post by bvandev on 2010-04-19
Yes, I'm running Lucid.  I followed a forum entry that told how to override the driver restrictions in the config file.  

Since I posted, I reinstalled Lucid, still as a dual boot option.  As others have reported, the wireless is running fine out of the box.  Don't know why it seemed poor the first time.

So, I join the group happily running Lucid on the Starling.  The mic doesn't work, but that's all I've found that doesn't.

Thanks and sorry for the confusion.

---

### Post by pemadorje on 2010-04-28
I was just wondering if there was an estimate on when the Lucid System 76 Driver would be released. I tried a fresh install on my Starling. It seemed to work fine at first but then it turns out the wireless connections are unstable. It will connect fine but the connection drops after a period of time and you have to keep reconnecting.

---

### Post by pqwoerituytrueiwoq on 2010-04-28
You may have to disable (blacklist) the default driver for the manufacture's to work also make sure the manufactures driver is not blacklisted.
Talking about wireless drivers right?

---

### Post by pemadorje on 2010-04-28
I actually didn't install the System 76 driver. I saw that wifi was working for some 'out of the box' and thought I'd give it a shot. As I understand it, the current System 76 driver can't be installed on Lucid anyway (without some tweaking).

---

### Post by thomasaaron on 2010-04-29
You will get short-range wifi without the driver. To get maximum range, though, you will need the driver.

The 2.4.7 version of the System76 Driver is ready. You can get it from [**here**]("http://planet76.com/repositories"). Click the second link on the bottom to download it.

---

### Post by superfrogman94 on 2010-04-29
> **thomasaaron said:**
> You will get short-range wifi without the driver. To get maximum range, though, you will need the driver.

The 2.4.7 version of the System76 Driver is ready. You can get it from [**here**]("http://planet76.com/repositories"). Click the second link on the bottom to download it.

So This Means Starling Owners Are Clear To Upgrade Or Clean-Install?

---

### Post by thomasaaron on 2010-04-29
> So This Means Starling Owners Are Clear To Upgrade Or Clean-Install?

Yepper.

---

### Post by jediborger on 2010-04-29
Sadly I have to report that wireless is not working on my starling. I just did a fresh install as I was running 9.04. At first I had a wireless network listing but the connection was too weak to connect. Although now after installing the System76 driver and restoring I have no wireless whatsoever. The wireless LED is on though. I have flipped the switch in the front a few times to no avail. Ifconfig does not list the wireless interface at all. Something else I noticed is that Fn+F2 is not recognized anymore which makes me think that might be the issue. Does anyone know what command the wireless toggle button runs? Then I could manually set it. 

Anyways here's some output you might find useful:

```
matthew@netMatt:/var/log$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:8b:aa:fe:ac  
          inet addr:128.54.224.92  Bcast:128.54.231.255  Mask:255.255.248.0
          inet6 addr: fe80::223:8bff:feaa:feac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5437109 (5.4 MB)  TX bytes:274555 (274.5 KB)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1936 (1.9 KB)  TX bytes:1936 (1.9 KB)

```
Here's the output from pressing Fn+F2:
```
matthew@netMatt:/var/log$ tail /var/log/messages
Apr 29 13:51:29 netMatt kernel: [  718.136635] atkbd.c: Use 'setkeycodes e026 <keycode>' to make it known.
Apr 29 13:57:33 netMatt kernel: [ 1081.237097] CE: hpet increasing min_delta_ns to 15000 nsec
Apr 29 13:57:53 netMatt kernel: [ 1102.187945] atkbd.c: Unknown key pressed (translated set 2, code 0xa6 on isa0060/serio0).
Apr 29 13:57:53 netMatt kernel: [ 1102.187961] atkbd.c: Use 'setkeycodes e026 <keycode>' to make it known.
Apr 29 13:57:54 netMatt kernel: [ 1102.342733] atkbd.c: Unknown key released (translated set 2, code 0xa6 on isa0060/serio0).
Apr 29 13:57:54 netMatt kernel: [ 1102.342749] atkbd.c: Use 'setkeycodes e026 <keycode>' to make it known.
Apr 29 13:57:55 netMatt kernel: [ 1103.230831] atkbd.c: Unknown key pressed (translated set 2, code 0xa6 on isa0060/serio0).
Apr 29 13:57:55 netMatt kernel: [ 1103.230847] atkbd.c: Use 'setkeycodes e026 <keycode>' to make it known.
Apr 29 13:57:55 netMatt kernel: [ 1103.351051] atkbd.c: Unknown key released (translated set 2, code 0xa6 on isa0060/serio0).
Apr 29 13:57:55 netMatt kernel: [ 1103.351066] atkbd.c: Use 'setkeycodes e026 <keycode>' to make it known.

```
Here's the all the rtl modules currently loaded:
```
matthew@netMatt:/var/log$ modprobe -l|grep rtl
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/net/usb/rtl8150.ko
kernel/drivers/staging/rtl8187se/rtl8187se.ko
kernel/drivers/staging/rtl8192su/r8192s_usb.ko
kernel/drivers/staging/rtl8192e/r8192_pci.ko
kernel/ubuntu/rtl8192se/r8192se_pci.ko

```

---

### Post by thomasaaron on 2010-04-29
The module that *should* be in there is r8187. So, it's not being loaded... probably because it isn't compiled.

Forgive me for asking, but did you *run* the driver once you installed it by clicking the restore tab and the restore button?

If so, please run the System76 Driver from the terminal...
```

system76-driver

```
...and post the output here.

---

### Post by jediborger on 2010-04-29
Haha, yes I did run restore from the program. After running it in the terminal I noticed that it failed to compile the module. Guess why? No, gcc. 

Perhaps gcc should be installed from the repos during this procedure.

I will repost back once I get gcc installed and the driver built to see where that gets me.

```
matthew@netMatt:~$ system76-driver
Connecting to www.planet76.com|64.13.254.166|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 145 [text/plain]
Saving to: `/etc/apt/sources.list.d/system76.list'

     0K                                                       100% 3.30M=0s

2010-04-29 17:39:40 (3.30 MB/s) - `/etc/apt/sources.list.d/system76.list' saved [145/145]

OK
Hit http://planet76.com ./ Release.gpg
Ign http://planet76.com/repositories/ ./ Translation-en_US                                                                  
Hit http://planet76.com ./ Release                                                                                          
Ign http://planet76.com ./ Packages                                                                                         
Ign http://planet76.com ./ Packages                                            
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://planet76.com ./ Packages                                  
Hit http://us.archive.ubuntu.com lucid Release.gpg                   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid Release 
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
system76-driver is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
options snd-hda-intel model=acer-aspire
blacklist rtl8187
--2010-04-29 17:39:44--  http://planet76.com/drivers/star1/rtl8187B.tar.gz
Resolving planet76.com... 64.13.254.166
Connecting to planet76.com|64.13.254.166|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 530571 (518K) [application/x-gzip]
Saving to: `rtl8187B.tar.gz'

     0K .......... .......... .......... .......... ..........  9% 1.00M 0s
    50K .......... .......... .......... .......... .......... 19% 2.63M 0s
   100K .......... .......... .......... .......... .......... 28% 3.02M 0s
   150K .......... .......... .......... .......... .......... 38% 3.52M 0s
   200K .......... .......... .......... .......... .......... 48% 9.51M 0s
   250K .......... .......... .......... .......... .......... 57% 3.76M 0s
   300K .......... .......... .......... .......... .......... 67% 9.88M 0s
   350K .......... .......... .......... .......... .......... 77% 5.25M 0s
   400K .......... .......... .......... .......... .......... 86% 11.9M 0s
   450K .......... .......... .......... .......... .......... 96% 9.91M 0s
   500K .......... ........                                   100% 11.3M=0.1s

2010-04-29 17:39:44 (3.60 MB/s) - `rtl8187B.tar.gz' saved [530571/530571]

make -C /lib/modules/2.6.32-21-generic/build M=/opt/system76/system76-driver/src/rtl8187B/rtl8187 CC=gcc modules
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
/usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  CC [M]  /opt/system76/system76-driver/src/rtl8187B/rtl8187/r8187_core.o
/bin/sh: gcc: not found
make[2]: *** [/opt/system76/system76-driver/src/rtl8187B/rtl8187/r8187_core.o] Error 127
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: *** [_module_/opt/system76/system76-driver/src/rtl8187B/rtl8187] Error 2
make: *** [modules] Error 2

```

---

### Post by WarLokk on 2010-04-29
I'm having the same issue.  I am more of a noob so excuse my question but what is gcc ?  Any luck with getting wireless to go?

---

### Post by jediborger on 2010-04-29
Yes, I can confirm that the missing gcc dependency was the issue. Running System76-Driver again built the driver and now wireless works great. This is rather a major issue though since all fresh installs do not include gcc by default. The driver program should go ahead and install gcc when it does the update check.

For those of you with the same issue, gcc is a C/C++ code compiler.
Anyways running this command in the terminal will install it, or you can use synaptic and search for the package gcc

```
sudo apt-get install gcc
```

Then just run the System76-Driver program again and it will correctly install the wireless driver.

---

### Post by WarLokk on 2010-04-29
Thanks for the quick reply

---

### Post by bvandev on 2010-04-29
Thanks to jediborder for the gcc tip.

Wireless now works fine, but alas the SD card reader does not.  It worked in 9.10 just fine.  I also tested the card before  upgrading tonight.  It worked fine.

---

### Post by Tart on 2010-04-29
I'm having problem with wireless. I followed instructions, and also installed gcc. I run system76-driver in terminal, clicked restore system and didn't see any error messages. But my starling just wont see any wireless networks (it could see them right before I installed system76 drivers). 

Any hits?
Thanks

ps. I did fresh install

pps```
ilya@la5fn:~$ tail /var/log/messages
Apr 29 23:01:14 la5fn kernel: [   11.577820] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 29 23:01:14 la5fn kernel: [   11.613810] rtl8187B: rtl8187_open process failed because radio off
Apr 29 23:01:14 la5fn kernel: [   11.677973] rtl8187B: rtl8187_open process failed because radio off
Apr 29 23:01:14 la5fn kernel: [   11.964844] ppdev: user-space parallel port driver
Apr 29 23:02:27 la5fn kernel: [   84.816934] rtl8187B: GPIO Polling Methord Will Turn Radio On
Apr 29 23:02:27 la5fn kernel: [   84.817921] rtl8187B: Now Radio ON!
Apr 29 23:02:29 la5fn kernel: [   86.817027] rtl8187B: GPIO Polling Methord Will Turn Radio Off
Apr 29 23:02:29 la5fn kernel: [   86.818520] rtl8187B: Now Radio OFF!
Apr 29 23:02:43 la5fn kernel: [  100.976805] r8169: eth0: link up
Apr 29 23:02:43 la5fn kernel: [  100.977636] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

---

### Post by pemadorje on 2010-04-30
jediborger, thank you so very much for the tip about gcc. I had the same issue after a fresh install and was quite disheartened to have no wireless after running the driver installation.

---

### Post by jediborger on 2010-04-30
Tart: You see that message about the GPIO polling turning the radio off. Move the switch in the front right once to the right and let it go. Look at the messages again, and it should say GPIO polling radion on. Then you should have your wireless. The starling can support a 3G card and this switch for going between them, although  most people don't have a 3G modem installed.

---

### Post by Tart on 2010-04-30
When I turn the computer on this is what I get
```
tail /var/log/messages
Apr 30 05:51:01 la5fn kernel: [   11.293902] type=1505 audit(1272621061.100:10):  operation="profile_load" pid=793 name="/usr/bin/evince-thumbnailer"
Apr 30 05:51:01 la5fn kernel: [   11.358504] type=1505 audit(1272621061.164:11):  operation="profile_load" pid=817 name="/usr/lib/cups/backend/cups-pdf"
Apr 30 05:51:01 la5fn kernel: [   11.549749] rtl8187B: EEPROM Customer ID: 00
Apr 30 05:51:01 la5fn kernel: [   11.552053] rtl8187B: Driver probe completed
Apr 30 05:51:01 la5fn kernel: [   11.552157] usbcore: registered new interface driver rtl8187B
Apr 30 05:51:01 la5fn kernel: [   11.554771] rtl8187B: GPIO Polling Methord Will Turn Radio Off
Apr 30 05:51:01 la5fn kernel: [   11.610075] udev: renamed network interface wlan0 to wlan1
Apr 30 05:51:01 la5fn kernel: [   11.622728] rtl8187B: rtl8187_open process failed because radio off
Apr 30 05:51:01 la5fn kernel: [   11.629501] rtl8187B: rtl8187_open process failed because radio off
Apr 30 05:51:01 la5fn kernel: [   12.030372] ppdev: user-space parallel port driver

```

and no wireless. I pull switch to right hold and let go, and this is the printout 
```
tail /var/log/messages
Apr 30 05:51:01 la5fn kernel: [   11.629501] rtl8187B: rtl8187_open process failed because radio off
Apr 30 05:51:01 la5fn kernel: [   12.030372] ppdev: user-space parallel port driver
Apr 30 05:52:13 la5fn kernel: [   83.376315] r8169: eth0: link up
Apr 30 05:52:13 la5fn kernel: [   83.377144] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 30 05:53:27 la5fn kernel: [  157.556801] rtl8187B: GPIO Polling Methord Will Turn Radio On
Apr 30 05:53:27 la5fn kernel: [  157.557812] rtl8187B: Now Radio ON!
Apr 30 05:53:33 la5fn kernel: [  163.556972] rtl8187B: GPIO Polling Methord Will Turn Radio Off
Apr 30 05:53:33 la5fn kernel: [  163.558457] rtl8187B: Now Radio OFF!
Apr 30 05:54:17 la5fn kernel: [  207.556964] rtl8187B: GPIO Polling Methord Will Turn Radio On
Apr 30 05:54:17 la5fn kernel: [  207.557950] rtl8187B: Now Radio ON!
```

Still no wireless, little light never lights up.

---

### Post by Tart on 2010-04-30
wohooo working now. After playing with button and restarting couple of times. It works now. Thanks

---

### Post by flukeairwalker on 2010-05-01
Thanks. Installing gcc before installing drivers did the trick for me too.

---

### Post by PantherFarber on 2010-05-05
the driver program should install gcc because i am probably not the only one who has had this problem. . . and i am pretty sure there are lots of people who havent come here to read this which if they are a newbie to linux they probably didnt. . or if they are like my mom they just called me and yelled about the update breaking her computer till i found the fix here.

---

### Post by thomasaaron on 2010-05-18
The System76 Driver is supposed to require build-essential, which contains gcc. We're fixing this in the driver right now.

---

### Post by why on 2011-03-18
I tried the latest driver (2.6.1), but it locks up my star1 netbook (see [http://ubuntuforums.org/showthread.php?p=10572594#post10572594]("http://ubuntuforums.org/showthread.php?p=10572594#post10572594")). Has anyone seen this before - any suggestions on how to get the driver to work?

thanks...
...Graeme

---

### Post by why on 2011-06-07
11.04 has the correct driver by default (ie system76 does not require any special drivers)!

---

