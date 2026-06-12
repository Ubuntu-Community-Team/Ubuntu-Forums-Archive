---
title: "Ratel Value no wireless"
date: 2010-02-16
forum: System76 Support
---

### Post by Sean-Michael on 2010-02-16
I upgraded our 2nd system76 computer, a Ratel Value to 9.10.

When I finished the upgrade this morning the wireless would no longer connect to the router. :(

I have 2 other computers connecting fine.

I did have to re-enter the security code for the router connection but still no connection...

I'm hoping this is a common problem with a fix, things like this are why I waited to upgrade lol

Meanwhile I will drag the computer to another room to hook up to the router with a cord anticipating that it will needed.

Thanks in advance,
Sean-Michael.

---

### Post by thomasaaron on 2010-02-17
Hey, Sean.

Good to hear from you again. It's been a while.

So, it's *seeing* your AP and *trying* to connect. Could you please unplug your Access Point and let it sit for a minute, then plug it back in and see if that helps?


If it doesn't work, make an attempt to connect. As soon as that attempt fails, make a note of the time on your system clock (which will help me find the correct section in the logs) and go to System > Administration > System76 Driver > Support > Create and attach the logs it creates here.

---

### Post by kfries6 on 2010-02-17
I wonder if it is the same problem I came here looking for that is occurring on my Starling.  I can connect without problems to any public, unencrypted network.  But not to many encrypted ones.  For example, I can not connect to my WRT54G at home with either TKIP or AES encryption enabled.  But if I leave the network open, it connects just fine.

Same problem at work.

Atlanta Bread, Panara, to JoikuSpot running on my E71 phone, the Belmar Library, etc... no problem, connects right up.

Could this be a supplicant problem?

Kevin Fries

---

### Post by Sean-Michael on 2010-02-17
The problem seems to be that the wireless functions of the card are not being recoginized... there is no wireless network option when I right click the icon, "Enable Wireless" is not there.

I remimber running a command that returned that there where no wireless extensions if that helps any.

I tried to see if it was a driver issue but when I goto the "Hardware Drivers" there is now only one driver and that is for the graphics card, if I remimber correctly there was 2 drivers for the graphics card and 2 for the network card before the upgrade?

I wired connection was working last nite just fine, checked for updates and made sure the system76 driver was installed.

I will have to move the computer around again a lil later and get that log for you.

kfries6 thank you for sharing, I have the same exact router here at home WT54G and will try to connect without encryption... but I fear the wireless it's self is not functioning at all yet.

Thanks,
Sean-Michael.

---

### Post by Sean-Michael on 2010-02-17
Here's the log you requested.

It's like the card is not being recognized at all, the power light blinks but not the activity light.

Still no driver for it when I look under hardware drivers.

EDIT: Taken at 12:42 computer time.

---

### Post by thomasaaron on 2010-02-17
Hi, Sean.

Well, there's nothing in the log pertaining to wireless at all.

I'm checking, but I'm pretty sure there were no extra drivers for that wireless card. It is a D-link, and I believe it just works out of the box with Ubuntu using included modules. (But I might be wrong.)

In the mean time, can you tell me the output of these commands...

```
lsmod
```
```
ls /etc/modprobe.d
```
```
cat /etc/network/interfaces
```

---

### Post by Sean-Michael on 2010-02-17
```
sudo lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
iptable_nat             6656  0 
nf_nat                 22164  1 iptable_nat
nf_conntrack_ipv4      16376  3 iptable_nat,nf_nat
dm_crypt               14888  0 
nf_conntrack           80832  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          2400  1 nf_conntrack_ipv4
iptable_mangle          4192  0 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_seq_dummy           3460  0 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3872  0 
snd_timer              26992  2 snd_pcm,snd_seq
ip_tables              21200  3 iptable_nat,iptable_mangle,iptable_filter
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               25832  2 iptable_nat,ip_tables
soundcore               9088  1 snd
fglrx                2234552  32 
psmouse                57124  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
serio_raw               6596  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
r8169                  38884  0 
mii                     6368  1 r8169
video                  23612  0 
output                  3680  1 video
intel_agp              32816  0

sean-michael@ubuntu:~$ ls /etc/modprobe.d
alsa-base.conf          blacklist-firewire.conf     blacklist-watchdog.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  dkms.conf
blacklist.conf          blacklist-modem.conf        libpisock9.conf
blacklist-fglrx.conf    blacklist-oss.conf
sean-michael@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by Sean-Michael on 2010-02-17
The more I google and search the more I see things pointing to the ndiswrapper?

What Driver should I have for this card?

---

### Post by thomasaaron on 2010-02-17
You DEFINITELY shouldn't have to use ndiswrapper. ndiswrapper is used to wrap a windows driver, which isn't necessary with the dlink cards.


I've got a Ratel with the dlink wireless sitting here on the bench, and it shows no proprietary drivers in use. If your system has nVidia, then you would have an nVidia driver, but that should be about it. (Or you might have an ati driver.)

If you got your wireless card from System76, it should be using the ath5k module, and that's not showing up in lsmod. So, most likely, that's the problem.

Try running...

sudo modprobe ath5k

...and see if your wireless springs to live after a few seconds.

---

### Post by Sean-Michael on 2010-02-17
> **thomasaaron said:**
> You DEFINITELY shouldn't have to use ndiswrapper. ndiswrapper is used to wrap a windows driver, which isn't necessary with the dlink cards.


I've got a Ratel with the dlink wireless sitting here on the bench, and it shows no proprietary drivers in use. If your system has nVidia, then you would have an nVidia driver, but that should be about it. (Or you might have an ati driver.)

If you got your wireless card from System76, it should be using the ath5k module, and that's not showing up in lsmod. So, most likely, that's the problem.

Try running...

sudo modprobe ath5k

...and see if your wireless springs to live after a few seconds.

the command worked like a charm and things sprung to life in 1.5 seconds. :)

How ever the change does not stick after a shutdown/restart... how do I make it permanent?

Thanks again,
Sean-Michael.

---

### Post by thomasaaron on 2010-02-18
What did that guy on A-Team always say? Something like... 
"I love it when a plan comes together." :popcorn:

Run...
sudo gedit /etc/init.d/wireless-module-insertions.sh

Then make the script look like this...

```
#!/bin/bash
modprobe ath5k
```

Then save the file and close gedit.

sudo chmod a+x /etc/init.d/wireless-module-insertion.sh
sudo update-rc.d /etc/init.d/wireless-module-insertion.sh defaults

Then reboot and see if it worked.

(It might also be worth looking through the files in /etc/modprobe.d to make sure none of them contains this line...
```

blacklist ath5k
```
)

---

### Post by Sean-Michael on 2010-02-18
**/etc/modprobe.d/blacklist-ath_pci.conf contains the line, blacklist ath5k.**

I will await doing the first instructions in case this blacklist entry is the root of the problem.

---

### Post by thomasaaron on 2010-02-18
Yep, open that file with...

sudo gedit /etc/modprobe.d/blacklist-ath_pci.conf 

...and put a...

#

...in front of...

blacklist ath5k

...and then save and reboot.

---

### Post by Sean-Michael on 2010-02-18
Worked like a charm, even looks like we get 15% better connection then before the upgrade.

Weird reading the description that this would have been blacklisted since we do not use the madwifi thing...

Well now it's off for me to get Apache running again, but I think I have this one covered! :)

Thanks again thomas for all the help,
Sean-Michael.

---

