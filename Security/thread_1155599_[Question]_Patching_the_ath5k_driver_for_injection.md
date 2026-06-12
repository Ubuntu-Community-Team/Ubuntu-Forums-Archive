---
title: "[Question] Patching the ath5k driver for injection"
date: 2009-05-10
forum: Security
---

### Post by Ninja2k on 2009-05-10
Well First time posting.

   Well, I just got myself a new netbook today. It's an Acer Aspire AOA150-1555 and have installed Ubuntu 9.04 on to it. Basically what I want to do is patch my wireless card for better injection, But that's where I'm hitting a wall. 

```
owner@ubuntu:~$ lsmod
Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
arc4                    9856  2 
ecb                    10752  2 
snd_seq_dummy          10756  0 
uvcvideo               63240  0 
snd_seq_oss            37760  0 
compat_ioctl32          9344  1 uvcvideo
snd_seq_midi           14336  0 
ath5k                 107008  0 
snd_rawmidi            29696  1 snd_seq_midi
videodev               41600  1 uvcvideo
psmouse                61972  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
v4l1_compat            21764  2 uvcvideo,videodev
serio_raw              13316  0 
mac80211              217208  1 ath5k
acer_wmi               24260  0 
pcspkr                 10496  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
led_class              12036  2 ath5k,acer_wmi
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
cfg80211               38032  2 ath5k,mac80211
video                  25360  0 
intel_agp              34108  1 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                 11008  1 video
agpgart                42696  3 drm,intel_agp
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
owner@ubuntu:~$ 

```I have downloaded the driver to patch it from the aircrack-ng site. (ath5k-injection-2.6.27-rc2.patch), but now I'm stuck as I'm not sure where the Ath5k sources are at on the system. This was easier on my old sylvania g netbook as there were a lot of tutorials on how to patch the r8187 driver. but running ls -a /usr/src/linux-headers-2.6.28-11/drivers/net/wireless/ath5k/ I get

```
owner@ubuntu:~$ ls -a /usr/src/linux-headers-2.6.28-11/drivers/net/wireless/ath5k/ 
.  ..  Kconfig  Makefile
```I was wondering were the sources are or better yet if a tutorial was avaiable about how to patch the ath5k drivers on ubuntu 9.04.

Thanks in advance to anyone who can help me with this issue

---

### Post by justatemptest on 2009-05-11
I have a very similar problem. Did you find a solution so far?

---

### Post by Imperial.mack@gmail.com on 2009-06-14
did anyone solve how to patch this driver??

---

### Post by nicedude on 2009-06-19
Well I have not posted on these forums for a minute, but felt I should help you out since I figured this one out for myself after much head scratching :-)


You will need to get source code for a package called compat-wireless - Just google compat-wireless and the first hit is it.

Get the latest stable release of that and then you must get the proper aircrack patch for ath5k injection rates,  ath5k-injection-2.6.27-rc2.patch seems to work fine. So google aircrack patches and get that one.

Once you untar the source for compat-wireless you will find the ath5k source in compat-wireless-2.6.30/drivers/net/wireless/ath5k . Before compileing the compat-wireless code you must patch the ath5k driver source with the aircrack patch mentioned above.

To do that you use the patch command like so in a terminal 

patch -Np0 -i <name of the patch file>

Now the patch file will point to a different location than the source is in so it will ask you for what file you want to patch, you need to give it the full path to the source code as well as the source code filename

Example from a terminal prompt with patch in same folder as prompt is.
patch -Np0 -i ath5k-injection-2.6.27-rc2.patch 

This returns that it cant find the file to be patched and prompts for file name & location

So I enter the following for source file location ( via paste ) 
/home/tech/CUSTOM-SOFT/compat-wireless-2.6.30/drivers/net/wireless/ath5k/base.c

where base.c is the source code to patch and the rest is the path to where I have placed the source, you can put your source code to compile in any directory you want etc. I am no Ubuntu expert at doing it the right way - I am good at makin it work though as that is all I care about.

Once you patch the driver its just these commands in the compat-wireless source directory.

make
sudo make install

Then you will also need to deal with blacklisting any unwanted atheros madwifi modules previously in use etc. So if you don't know how to do that just search here on the forums as it is well covered.

I also remove Jockey & Network Manager while installing WICD as a GUI replacement that seems to cause less interference than network manager can :-)


GOOD LUCK ALL AND POST IF YOU GET YOURS TO WORK ):P

---

### Post by Imperial.mack@gmail.com on 2009-06-22
If you have jaunty and ath5k comes working out the box, do you have to get compact wireless still or just patch the one thats with the system?

> **nicedude said:**
> Well I have not posted on these forums for a minute, but felt I should help you out since I figured this one out for myself after much head scratching :-)


You will need to get source code for a package called compat-wireless - Just google compat-wireless and the first hit is it.

Get the latest stable release of that and then you must get the proper aircrack patch for ath5k injection rates,  ath5k-injection-2.6.27-rc2.patch seems to work fine. So google aircrack patches and get that one.

Once you untar the source for compat-wireless you will find the ath5k source in compat-wireless-2.6.30/drivers/net/wireless/ath5k . Before compileing the compat-wireless code you must patch the ath5k driver source with the aircrack patch mentioned above.

To do that you use the patch command like so in a terminal 

patch -Np0 -i <name of the patch file>

Now the patch file will point to a different location than the source is in so it will ask you for what file you want to patch, you need to give it the full path to the source code as well as the source code filename

Example from a terminal prompt with patch in same folder as prompt is.
patch -Np0 -i ath5k-injection-2.6.27-rc2.patch 

This returns that it cant find the file to be patched and prompts for file name & location

So I enter the following for source file location ( via paste ) 
/home/tech/CUSTOM-SOFT/compat-wireless-2.6.30/drivers/net/wireless/ath5k/base.c

where base.c is the source code to patch and the rest is the path to where I have placed the source, you can put your source code to compile in any directory you want etc. I am no Ubuntu expert at doing it the right way - I am good at makin it work though as that is all I care about.

Once you patch the driver its just these commands in the compat-wireless source directory.

make
sudo make install

Then you will also need to deal with blacklisting any unwanted atheros madwifi modules previously in use etc. So if you don't know how to do that just search here on the forums as it is well covered.

I also remove Jockey & Network Manager while installing WICD as a GUI replacement that seems to cause less interference than network manager can :-)


GOOD LUCK ALL AND POST IF YOU GET YOURS TO WORK ):P

---

### Post by Th3_uN1Qu3 on 2009-06-22
Since the default install does not include the wireless driver sources, yes you need to get compat-wireless.

I have followed the guide and it worked for me. :D

---

### Post by magusjonny42 on 2009-07-22
Ok I got some specific questions to throw at you nicedude, great info thus far, it has helped me learn more about Linux.

> **nicedude said:**
> 
Once you untar the source for compat-wireless you will find the ath5k source in compat-wireless-2.6.30/drivers/net/wireless/ath5k.


Does it have to be 2.6.30?

> **nicedude said:**
> 
Then you will also need to deal with blacklisting any unwanted atheros madwifi modules previously in use etc. So if you don't know how to do that just search here on the forums as it is well covered.


Ive searched around but I cant seem to find a thread that explains it in depth. Can you please point me to a good one?

> **nicedude said:**
> 
I also remove Jockey & Network Manager while installing WICD as a GUI replacement 

How can you make sure that Network Manager is uninstalled?


Thats it from me, thanks for all the help thus far regarding patching these drivers.

---

### Post by xiphos45 on 2009-08-02
Well, I completed the patch and compiled the patched compat install, then made the install to kernel 2.6.28-14-generic. Now, for whatever reason it does not load. I was able to boot using 2.6.28-11-generic however. The new kernel just hangs after the ubuntu splash screen.

I am not sure what happened. It all seemed to run smoothly, no errors. I saved the log information of the install. It seems that I have killed that kernel.:confused:

Sweet.

---

### Post by Ninja2k on 2009-08-18
Yeah, Injection Works out of the box so to speak, about 500 pps!

---

### Post by jessiebrownjr on 2009-09-17
I would also like to know if it HAS to be 2.6.30 ? I am using 2.6.28 and I don't want a dead kernel like the poster before me :-) thanks in advance!

---

### Post by Ubu-freak on 2010-02-13
I followed the steps above and when i make compat-wireless i get the following output
```
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.31-19-generic/build M=/home/user/Desktop/compat-wireless-2.6.30 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  LD      /home/user/Desktop/compat-wireless-2.6.30/drivers/misc/eeprom/built-in.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/misc/eeprom/eeprom_93cx6.o
  LD      /home/user/Desktop/compat-wireless-2.6.30/drivers/net/usb/built-in.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/usb/cdc_ether.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/usb/rndis_host.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/usb/usbnet.o
  LD      /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/built-in.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/at76c50x-usb.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/rndis_wlan.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/adm8211.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/mwl8k.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/mac80211_hwsim.o
  LD      /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ar9170/built-in.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ar9170/usb.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ar9170/main.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ar9170/cmd.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ar9170/mac.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ar9170/phy.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ar9170/led.o
  LD [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ar9170/ar9170usb.o
  LD      /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/built-in.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/caps.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/initvals.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/eeprom.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/gpio.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/desc.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/dma.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/qcu.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/pcu.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/phy.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/reset.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/attach.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/base.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/led.o
  LD [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath5k/ath5k.o
  LD      /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/built-in.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/hw.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/eeprom.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/mac.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/calib.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/ani.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/phy.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/regd.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/beacon.o
  CC [M]  /home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.o
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c: In function &#8216;ath_rfkill_poll&#8217;:
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1201: error: storage size of &#8216;state&#8217; isn&#8217;t known
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1204: error: &#8216;RFKILL_STATE_SOFT_BLOCKED&#8217; undeclared (first use in this function)
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1204: error: (Each undeclared identifier is reported only once
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1204: error: for each function it appears in.)
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1205: error: &#8216;RFKILL_STATE_HARD_BLOCKED&#8217; undeclared (first use in this function)
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1208: error: &#8216;RFKILL_STATE_UNBLOCKED&#8217; undeclared (first use in this function)
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1219: error: implicit declaration of function &#8216;rfkill_force_state&#8217;
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1201: warning: unused variable &#8216;state&#8217;
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c: At top level:
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1227: warning: &#8216;enum rfkill_state&#8217; declared inside parameter list
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1227: warning: its scope is only this definition or declaration, which is probably not what you want
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1227: error: parameter 2 (&#8216;state&#8217;) has incomplete type
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c: In function &#8216;ath_sw_toggle_radio&#8217;:
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1232: error: &#8216;RFKILL_STATE_SOFT_BLOCKED&#8217; undeclared (first use in this function)
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1238: error: &#8216;RFKILL_STATE_UNBLOCKED&#8217; undeclared (first use in this function)
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c: In function &#8216;ath_init_sw_rfkill&#8217;:
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1257: error: implicit declaration of function &#8216;rfkill_allocate&#8217;
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1258: warning: assignment makes pointer from integer without a cast
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1266: error: dereferencing pointer to incomplete type
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1267: error: dereferencing pointer to incomplete type
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1268: error: dereferencing pointer to incomplete type
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1269: error: dereferencing pointer to incomplete type
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1269: error: &#8216;RFKILL_STATE_UNBLOCKED&#8217; undeclared (first use in this function)
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1270: error: dereferencing pointer to incomplete type
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c: In function &#8216;ath_start_rfkill_poll&#8217;:
/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1298: error: implicit declaration of function &#8216;rfkill_free&#8217;
make[4]: *** [/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.o] Error 1
make[3]: *** [/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless/ath9k] Error 2
make[2]: *** [/home/user/Desktop/compat-wireless-2.6.30/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/user/Desktop/compat-wireless-2.6.30] Error 2
make: *** [modules] Error 2

```
what's weird is that the error has to do ath9k drivers, buy i'm using ath5k.

---

### Post by wannadumpwindows on 2010-05-12
I'm trying to get this working, but every time I run the patch, I get this:

```
patch -Np0 -i ath5k-injection-2.6.27-rc2.patch
patching file b/drivers/net/wireless/ath5k/base.c
Hunk #1 FAILED at 1219.
1 out of 1 hunk FAILED -- saving rejects to file b/drivers/net/wireless/ath5k/base.c.rej
```

I have no clue how to fix this. Any help would be greatly appreciated.

---

### Post by carvell on 2010-05-31
I get this problem too.  It looks like the compat-wireless drivers have been updated so the patch no longer works.

Either that or I have a kernel version that isn't compatible.  I have 2.6.32-21-generic and I'm trying to patch the ath5k drivers for injection.

---

### Post by Djamel MB on 2010-05-31
I have an Ath5k I've instaled without patch and it works perfectly with injection. Just try without it gonna work.
What kind of laptop or uc you have?

---

### Post by carvell on 2010-05-31
Injection didn't work for me out the box.

I did get it working though, the way to get it working is to manually apply the patch.  I.e., open up base.c, look for the line:
```
if (info->flags & IEEE80211_TX_CTL_NO_ACK)
```and replace it with:
    ```
if (info->flags & IEEE80211_TX_CTL_NO_ACK ||
       (info->flags & IEEE80211_TX_CTL_INJECTED &&
       !(ieee80211_has_morefrags(((struct ieee80211_hdr *)skb->data)->frame_control))))

```Hope this helps someone.

---

### Post by carvell on 2010-05-31
Note that in order that data capturing works properly (in 2.6.32 and newer), you also need to apply the following patch to the compat-wireless source:
[http://patches.aircrack-ng.org/fix_ath5k_no_data_in_monitor_mode.patch](http://patches.aircrack-ng.org/fix_ath5k_no_data_in_monitor_mode.patch)

---

