---
title: "Ubuntu Server is Incapable of Connecting to Wifi; Very Confused"
date: 2016-12-24
forum: Server Platforms
---

### Post by cook150 on 2016-12-24
I have absolutely no idea why my Ubuntu Server just won't connect to Wifi, or even the internet. The server also refuses to connect to a wired connection. It is a Toshiba Satellite M55-S135. I have attempted to see what was going on, but I'm getting really confused. What should I try?

I do know that the Ethernet Controller is a Qualcomm Atheros AR2413/AR2414 and that its Kernel driver and Kernel module(s) is ath5k, which appeared to have caused problems with others on other Linux forums, but other than that, I haven't gotten the faintest idea of what's going on.

---

### Post by lisati on 2016-12-24
In general, I'd recommend using a wired connection where possible for a machine you're using as a server, as it is usually more reliable.

[This thread]("https://ubuntuforums.org/showthread.php?t=370108") has some suggestions that might help you provide us with some information that could help troubleshoot your connection.

---

### Post by cook150 on 2016-12-24
The wired connection doesn't work at all either.

---

### Post by wildmanne39 on 2016-12-24
Hi, welcome to the forum! 
> Ethernet Controller is a Qualcomm Atheros AR2413/AR2414
That is your wifi connection, are you using network manger? do you have a destop on the sever?
Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
cat /etc/network/interfaces
rfkill list all
cat /etc/network/interfaces
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by cook150 on 2016-12-24
I'm not sure if I have a network manager on my server, and no, I don't have a desktop on the server (due to the lack of internet).

```
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
Linux millenniumse 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:06:14 UTC 2016 i686 i686 i686 GNU/Linux

lspci -nnk | grep -iA2 net
06:02.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
               Subsystem: Askey Computer Corp. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [144f:7094]
               Kernel driver in use: ath5k
               Kernel modules: ath5k

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
iwconfigcat /etc/network/interfaces
iwconfigcat: command not found

rfkill list all
The program 'rkkill' is currently not installed. You can install it by typing:
sudo apt install rfkill

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
                   
               source /etc/network/interfaces.d/*

               # The loopback network interface
               auto lo
               iface lo inet loopback

lsmod
Module               Size               Used by
arc4               16384               2
ppdev               20480               0
drbg               28672               1
ansi_cprng               16384               0
xts               16384               1
gf128mul               16384               1 xts
dm_crypt               24576               1
ath5k               139264               0
ath               24576               1 ath5k
mac80211               659459               1 ath5k
input_leds               16384               0
snd_intel8x0               36864               0
joydev               20480               0
pcmcia               57344               0
snd_ac97_codec               106596               1 snd_intel8x0
serio_raw               16384               0
ac97_bus               16384               1 snd_ac97_codec
snd_pcm                94208               2 snd_ac97_codec,snd_intel8x0
cfg80211               499712               3 ath,ath5k,mac80211
snd_timer               32768               1 snd_pcm
yenta_socket               45056               0
lpc_ich               20480               0
snd               69632               4 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm
pcmcia_rsrc               20480               1 yenta_socket
soundcore               16384               1 snd
pcmcia_core               24576               3 pcmcia,pcmcia_rsrc,yenta_socket
irda               176128               0
toshiba_bluetooth               16384               0
crc_ccitt               16384               1 irda
8250_fintek               16384               0
parport_pc               32768               0
parport               45056               2 ppdev,parport_pc
mac_hid               16384               0
ib_iser               45056               0
rdma_cm               49152               1 ib_iser
iw_cm               36864               1 rdna_cm
ib_cm               45056               1 rdma_cm
ib_sa               36864               2 rdma_cm,ib_cm
ib_mad               49152               2 ib_cm,ib_sa
ib_core               98304               6 rdma_cm,ib_cm,ib_sa,iw_cm,ib_mad,ib_iser
ib_addr               16384               2 rdma_cm,ib_core
iscsi_tcp               20480               0
libiscsi_tcp               20480               1 iscsi_tcp
libiscsi               49152               3 libiscsi_tcp,iscsi_tcp,ib_iser
scsi_transport_iscsi               86016               4 iscsi_tcp,ib_iser,libiscsi
autofs4               40960               2
btrfs               1003520               0
raid10               49152               0
raid456               106496               0
async_raid6_recov               16384               1 raid456
async_memcpy               16384               2 raid456,async_raid6_recov
async_pq               16384               2 raid456,async_raid6_recov
async_xor               16384               3 async_pq,raid456,async_raid6_recov
async_tx               16384               5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
xor               28672               2 btrfs,async_xor
raid6_pq               102400               4 async_pq,raid456,btrfs,async_raid6_recov
libcrc32c               16384               1 raid456
raid1               36864               0
raid0               20480               0
multipath               16384               0
linear               16384               0
i915               1130496               1
i2c_algo_bit               16384               1 i915
drm_kms_helper               131072               1 i915
syscopyarea               16384               1 drm_kms_helper
pata_acpi               16384               0
sysfillrect               16384               1 drm_kms_helper
psmouse               118784               0
ahci               36864               0
sysimgbit               16384               1 drm_kms_helper
libahci               32768               1 ahci
fb_sys_fops               16384               1 drm_kms_helper
drm               311296               3 i915,drm_kms_helper
f jes               28672               0
video               36864               1 i915

```

It appears to be that someone else also has my problem too.

[http://askubuntu.com/questions/776525/wireless-not-working-on-16-04-qualcomm-atheros-ar2413-ar2414-wireless-adapter](http://askubuntu.com/questions/776525/wireless-not-working-on-16-04-qualcomm-atheros-ar2413-ar2414-wireless-adapter)

However, there is no network manager detectable on the computer, and I can't connect to the internet to get one from apt...

---

### Post by wildmanne39 on 2016-12-24
Sorry I have been out for family fun for Christmas.

Do you want to run your server with a desktop if so then it will make more sense to install network manager if not then we will try to create a file to connect to the internet, if you have no experience with the terminal then you probably want to install the desktop in that case tell me which one you want to use.

---

### Post by cook150 on 2016-12-24
> **wildmanne39 said:**
> Sorry I have been out for family fun for Christmas.

Do you want to run your server with a desktop if so then it will make more sense to install network manager if not then we will try to create a file to connect to the internet, if you have no experience with the terminal then you probably want to install the desktop in that case tell me which one you want to use.

Without internet, the server can't get desktop. It doesn't have it either. Therefore, let's attempt to create the file.

---

### Post by wildmanne39 on 2016-12-25
It does not show you even have an ethernet connection, the one it is showing is your wifi card and this is one of the few wifi cards that shows as an ethernet card, go into your bios and make sure your ethernet and wifi is turned on if you have those options. 

If you have windows also check and make sure your wifi is on in windows and see if ethernet works.

Please post the output of:
```
ps aux | egrep 'Network|wicd'
lspci -nnk
```
copy and paste to a flash drive then use a computer with internet to paste here on the forum.
This setting should help with the driver for that card:
```
echo "options ath5k nohwcrypt=y" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Watch for errors, also post the output of:
```
iwconfig
```
This information will help me determine if we are ready for creating the file.

Did ethernet ever work
Thanks

---

### Post by cook150 on 2016-12-25
```
ps aux | egrep 'Network|wicd'
lanavas+  3270  0.0 0.1  4668  832 tty1   S+   13:10  0:00 grep -E --color=auto Network|wicd

iwconfig
wlp6s2   IEEE 802.11bg  ESSID:off/any
            Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
            Retry short limit:7   RTS thr:off   Fragment thr:off
            Power Management: on

lo          no wireless extensions.
enp2s0   no wireless extensions.
```

The attached thumbnails partly overlap.

```
sudo iwlist scan
wlp6s2   Interface doesn't support scanning : Network is down
lo   Interface doesn't support scanning.
enp2s0   Interface doesn't support scanning.
```

---

### Post by wildmanne39 on 2016-12-25
Let's create the file, please do:
```
sudo nano /etc/network/interfaces
```
```
auto lo
iface lo inet loopback

auto wlp6s2
iface wlp6s2 inet dhcp
    wpa-ssid yourssidhere
    wpa-psk yourpasshere
```
save and close the editor.

To restart networking do:
```
sudo ifdown wlp6s2 && sudo ifup -v wlp6s2
```
I always use gedit to edit a text file but I doubt that you can without a desktop installed so you will have to read the help file or man pages for the editor that is used in the terminal.

---

### Post by cook150 on 2016-12-25
As of now, after all of those commands have been done, the computer stubbornly responds:

```
Unknown interface wlp6s2
```

---

### Post by wildmanne39 on 2016-12-25
Please post the content of the file you edited and remove sensitive information first.

Also the output of:
```
ls -al /etc/network/interfaces
iwconfig
```
Thanks

---

### Post by cook150 on 2016-12-25
```
ls -al /etc/network/interfaces
-rw-r--r-- 1 root root 314 Dec 24 15:28 /etc/network/interfaces


iwconfig

```

iwconfig output is exactly the same as last time, with the exception of ```
Tx-Power=off
```

---

### Post by wildmanne39 on 2016-12-25
Let's change the permission of the file:
```
sudo chmod 644 /etc/network/interfaces
```
Then do:
```
sudo ifdown wlp6s2 && sudo ifup -v wlp6s2
```
```
ping -c3 www.google.com
```
Does it work?

---

### Post by cook150 on 2016-12-25
It does not work.

My Server really hates me this Christmas.

---

### Post by wildmanne39 on 2016-12-25
Please post the output of:
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlp6s2 -e etork | tail -n55
```
When you say it does not work does not help us I need to know if there are error messages.

---

### Post by cook150 on 2016-12-25
```
grep: firmware: No such file or directory
```

---

### Post by wildmanne39 on 2016-12-25
I kind of expected that, did the rest of the command have output?

---

### Post by cook150 on 2016-12-25
That was all the output.

---

### Post by wildmanne39 on 2016-12-25
Try the command this way:
```
sudo cat /var/log/syslog | grep -e ath -e wpa -e wlp6s2 -e etork | tail -n55
```

---

### Post by cook150 on 2016-12-25
Got a lengthly output. Attached images overlap slightly.

---

### Post by darkod on 2016-12-25
Is it possible your wired connection is faulty or disabled in bios or something? It seems not detected at all. If I were you I would focus more on that, than trying to make the wifi work. For servers wired connection is always preferred. And I wouldn't install any GUI or Network Manager even when you get the internet working...

Try making ubuntu desktop live cd/usb too and boot the computer with it in live mode (Try Ubuntu). Does that detect the wired interface correctly? Do other live linux distros detect the interface?

Before installing ubuntu server did you have windows on this computer? Did the wired interface work correctly all the time?

Ubuntu Server is very good at detecting wired interfaces and it is strange not to have a driver that it needs. So, the missing interface might be because of driver or it might be because of HW failure...

---

### Post by cook150 on 2016-12-25
I have two other laptops, one running Windows 10 and the other running Elementary OS. They both detected the wired Ethernet perfectly.

The laptop that has Ubuntu Server used to have Windows XP, but I didn't test its network capabilities before I downloaded Ubuntu.

I'll try getting Ubuntu 16.04 LTS Desktop on a LiveUSB and see the results...

I can confirm that Wired Connection 1 works on the trouble laptop on Ubuntu 14.04 LTS Desktop Edition. Internet is accessible on the trouble laptop.

---

### Post by darkod on 2016-12-25
I would check the network card model (chipset) with:
```
lspci
sudo lshw -short | grep network
```

And then try to google if you need to add any driver for 16.04 server to detect it.

---

### Post by cook150 on 2016-12-25
Should I search for the Fast Ethernet Controller or the Wireless Network Adapter?

I got some very interesting output...

```
iwconfig
```

yielded the exact same output, with the exception of ```
Tx-Power=20 dBm
``` and ```
Power Management:off
```.

Another thing I found out was that the troubled laptop connected to ethernet nicely, but wouldn't connect to wifi. Also, when connected, my laptop that had Elementary OS disconnected from wifi and refused to reconnect to ANYTHING until the troubled laptop was disconnected.

---

### Post by wildmanne39 on 2016-12-25
Did you go into the bios and make sure your ethernet was turned on like I asked you too in one of my first posts? When you installed the server edition of ubuntu you did not do a minimal install did you?

Do:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo ifdown wlp6s2 && sudo ifup -v wlp6s2
iwconfig
sudo iwlist scan
ping -c3 www.google.com
```
Does wifi ping or come on?

Did you run these commands:
```
echo "options ath5k nohwcrypt=y" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
sudo chmod 644 /etc/network/interfaces
```
the perform a function, they are not meant to show output.

Please check your bios and make sure the ethernet is on if necessary reset the bios unless it is UEFI then do not try to rest it.

I have family activities going on so I will be on and off today.
Thanks

---

### Post by cook150 on 2016-12-25
Hooray!

After during the boot-up, when a message said "A Start job is running for Raise network interfaces," the internet works!

Apparently, running Ubuntu 14.04 LTS Desktop Edition might've jumpstarted the Ethernet Controller to work for Ubuntu, so it now works in the server.

I'd like to thank wildmanne39 and darkod for being such helpful tech supporters and helping me to find a solution to my problem.

Problem: SOLVED.

---

### Post by wildmanne39 on 2016-12-25
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags. So we can see what it looks like now that it is working.
Thanks

---

### Post by cook150 on 2016-12-25
Here are the first 5 attachments; 10 more are coming...

Here are the next 4 attachments.

Here are the next two Attachments. (IMG_55 and IMG 63 are still not attached yet.)

Here is the next Attachment. (IMG 55 and IMG 63 are still not attached.)

[http://i68.tinypic.com/2ltlrlu.jpg](http://i68.tinypic.com/2ltlrlu.jpg)

[http://i64.tinypic.com/2h3pmqt.jpg](http://i64.tinypic.com/2h3pmqt.jpg)

Here are the last two images, though they are out of place. All images should be looked at in numerical order.

---

### Post by wildmanne39 on 2016-12-25
Please use thumbnails or url's when posting images because many people have slow connections and can not load pages with large images.

Your wifi showed connected but I suspect it will take a little more tuning for it to have internet, you can disconnect the ethernet cable and see if wifi works. It is scanning and the output showed connected, but in dmesg it looked like it just kept trying to connect, of course that is a vast improvement.

---

### Post by cook150 on 2016-12-26
I'll most likely not bother with the server's wifi anymore, as I'm moving on to configuring the server as a web server...

Also, the server connects perfectly with apt and is accessible through my home's local network, so I believe that for now, everything is alright.

---

### Post by wildmanne39 on 2016-12-26
Thanks for posting the information it was more for my learning then anything else, it is good to know that creating the file and changing the settings has the wifi scanning,
Enjoy your server!:)

---

