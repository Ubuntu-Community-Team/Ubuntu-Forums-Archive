---
title: "Still no wireless with latest updates"
date: 2013-03-12
forum: Ubuntu Development Version
---

### Post by tajreed on 2013-03-12
/software sources/additional drivers shows 'BCM 4318(Airforce...' available but not usable. It also shows as an option '802.11 STA...'. When I try to activate the latter, it stalls halfway thru. 

I've tried 'bcmwl-kernel-source' from the respository. The install script claims that it has been installed but then I get a seg fault. And lose my Lan connection and all package management systems, synaptic, terminal, software updater are locked-up.

Anyone having any ideas on how to get the proper driver installed-bcm 4318

Acer laptop upon which I haven't had this problem for the past 4 or 5 releases.

---

### Post by varunendra on 2013-03-12
Please post -
```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by tajreed on 2013-03-12
```
duke@duke-Aspire-5610:~$ sudo lspci -nnk | grep -iA2 net
[sudo] password for duke: 
06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0090]
	Kernel driver in use: b44
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
	Kernel driver in use: b43-pci-bridge
```

```
duke@duke-Aspire-5610:~$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek    63791  1 
joydev                 17097  0 
coretemp               13131  0 
acer_wmi               27592  0 
sparse_keymap          13658  1 acer_wmi
b43                   351829  0 
pcmcia                 39544  0 
bcma                   39645  1 b43
snd_hda_intel          38307  2 
snd_hda_codec         117303  2 snd_hda_codec_realtek,snd_hda_intel
i915                  535498  5 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
mac80211              526481  1 b43
drm_kms_helper         47545  1 i915
yenta_socket           27095  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
microcode              18286  0 
drm                   228750  6 i915,drm_kms_helper
lpc_ich                16925  0 
pcmcia_rsrc            18191  1 yenta_socket
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
cfg80211              436177  2 b43,mac80211
i2c_algo_bit           13197  1 i915
snd_timer              24411  2 snd_pcm,snd_seq
psmouse                76364  0 
serio_raw              13031  0 
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37420  0 
snd                    56485  13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
soundcore              12600  1 snd
wmi                    18590  1 acer_wmi
video                  18894  2 i915,acer_wmi
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
b44                    31137  0 
sdhci_pci              18158  0 
ssb                    50628  2 b43,b44
sdhci                  31824  1 sdhci_pci
duke@duke-Aspire-5610:~$ z
```

---

### Post by varunendra on 2013-03-12
> **tajreed said:**
> 
```
duke@duke-Aspire-5610:~$ lsmod
Module                  Size  Used by
....
....
**ssb**                    50628  2 **[COLOR="#FF0000"]b43,b44[/COLOR]**
sdhci                  31824  1 sdhci_pci
duke@duke-Aspire-5610:~$ z
```
Looks like the infamous "Me first!" contest here..

I don't remember the exact solution for it, but let's try -
```
sudo modprobe -rfv b43
sudo modprobe -rfv b44
sudo modprobe -rfv ssb
sudo modprobe -v b43
```
Are there any errors? Does the wireless work?

**PS:**
Please use 'Code' tags while posting command outputs. Follow the "Code Tags example" link in my signature to see how.

---

### Post by tajreed on 2013-03-12
> **varunendra said:**
> Looks like the infamous "Me first!" contest here..

I don't remember the exact solution for it, but let's try -
```
sudo modprobe -rfv b43
sudo modprobe -rfv b44
sudo modprobe -rfv ssb
sudo modprobe -v b43
```
Are there any errors? Does the wireless work?

**PS:**
Please use 'Code' tags while posting command outputs. Follow the "Code Tags example" link in my signature to see how.

duke@duke-Aspire-5610:~$ sudo modprobe -rfv b43
[sudo] password for duke: 
rmmod b43
rmmod mac80211
rmmod cfg80211
rmmod bcma
duke@duke-Aspire-5610:~$ sudo modprobe -rfv ssb
FATAL: Module ssb is in use.
duke@duke-Aspire-5610:~$ sudo modprobe -rfv b43
duke@duke-Aspire-5610:~$ 

b43 shuts off the lan.

Thank-you, I'll check the tags.

---

### Post by tajreed on 2013-03-12
And still no wireless.

---

### Post by varunendra on 2013-03-12
> **tajreed said:**
> 
**FATAL: Module [COLOR="#FF0000"]ssb[/COLOR] is in use.**
..
b43 shuts off the lan..

I think you mean **b44**, yes, it is supposed to shut off the lan. Only then **ssb** will be released and will be properly loaded again with **b43**.

Please try them all exactly in the sequence I posted. If it doesn't help, re-connect the lan with-
```
sudo modprobe -v b44
```

and do -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install b43-fwcutter firmware-b43-installer
```

Then repeat the process in my previous post.

Don't worry about the lan. The modprobe command loads/unloads the modules only temporarily (till a restart). If it makes wireless work, we can make both wifi and lan work with some tweaking.

---

### Post by tajreed on 2013-03-13
That did it. Both lan and wireless working. 

I truly appreciate your help. You seem quite an expert. 

Last time I upgraded to a new distribution at alpha 2 or later, I saved the Broadcom firmware to a usb stick before hand and than simply reinstalled in the new dist. Worked fine. This time I forgot.

Thanks again.

---

### Post by varunendra on 2013-03-13
> **tajreed said:**
> That did it. Both lan and wireless working. 
So now they both work simultaneously without any tweaking? That's great!

I remember we needed a one-line script in rc.local file to force the loading sequence to be b43 first and b44 later. Guess it's fixed now.

Thanks for the confirmation :)

---

