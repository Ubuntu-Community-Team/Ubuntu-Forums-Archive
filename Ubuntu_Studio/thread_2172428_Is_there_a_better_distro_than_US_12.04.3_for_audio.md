---
title: "Is there a better distro than US 12.04.3 for audio recording/editing?"
date: 2013-09-04
forum: Ubuntu Studio
---

### Post by louh2 on 2013-09-04
Everyday there is a new problem with my current setup.  No matter how I set Jack when I reboot I have to go back and reset until I can monitor and record, not to mention the xruns factor which can be in the 20,000's within minutes](*,).  I spend about 90% of my time fixing, or trying to fix or reading about a fix, problems and the 10% of the time that things are working I'm too tired or way past uninspired to write/record songs:-(.  So is there a distro that is better adapted to audio enthusiasts like myself or do I just need to give this linux business a rest and go on back to MS?  Please believe I am trying to explore new territory but if you have to spend the time I spend fixing then what's the point?

Athlon II X4 645 quad
Foxconn A74MX-K mobo
2GB DDR2 1066
Ubuntu Studio 12.04.3 low latency kernel
Hydrogen
Ardour
QSynth

Externals:
BOSS DR-5 --> midi ports, audio --> Xenyx mixer for eq and boost --> Tapco Mix100
Tapco mixer --> analog ins
audio out --> Realistic 32-1200B mixer for headphone monitoring (live in an apartment so no amps or speakers)
Don't have any digital equipment so not using S/PDIF

---

### Post by jejeman on 2013-09-05
I find 12.10 little smoother than 12.04. But, I don't have problems with any (now). Using 12.10 on laptop with USB soundcard Maya44, much better performance than internal card. 12.04 on desktop with both internal and firewire card, no trouble. When I say "no trouble" I mean: latency <10ms no xruns.
Try AVLinux, it is the most optimised distro I tried. Had to use it on laptop with firewire card, because UbuntuStudio gave me trouble.
Also consider to turn off wifi and all that you don't really need.

I don't know, never had a Maudio PCI card, but they are usally recomended by users. Did you analize IRQ assigments?
```
cat /proc/interrupts
```Maybe it's sharing with something.
On my desktop motherboard firewire (whole PCI section) is shared with PCIe, so it gives me lower performance.
Also on laptop firewire is shared with nvidia, which is no good. AVlinux manage to give me good performance, but if I turn on wifi everything goes to s***.
```
16:      76955      81662   IO-APIC-fasteoi   uhci_hcd:usb3, mmc0, firewire_ohci, nvidia
18:      16746      28127   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb8, ath9k
19:    5935902    2948805   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb5, uhci_hcd:usb7

```See, I got lucky USB card is on IRQ 19. But firewire is on 16 with nvidia.
Also, I uninstalled pulse-jack sink. Turned off jackdbus. On desktop (12.04) had to disable pulseaudio all together.

---

### Post by tgalati4 on 2013-09-05
Give this a spin:  [http://www.dynebolic.org/](http://www.dynebolic.org/)

---

### Post by su:bhatta on 2013-09-06
As suggested by jejeman, AV Linux is a good alternative. 

Also you can checkout linuxaudio.org, they list some OS that are for audio work only. There is an Argentianian Distro, I am forgettin the name, which is good as reviewed.

TangoStudio or Tango Studio Debian-way are others that I've tried. 

But my theory is that you can build up your own system with your own specific hardware related solutions if you really want to tweak.
A barebones Debian/Ubuntu install & then  add to it including a RT/Preemptive kernel.

Also, 4Gb ram may help you.

---

### Post by cub on 2013-09-06
"Better" we can probably debate for a long time, but other distributions that might work better with your setup and workflow yes. Ubuntu Studio 13.04. ;)

AVlinux has already been mentioned. Other than that you can also try out [http://dreamstudio.dickmacinnis.com/](http://dreamstudio.dickmacinnis.com/) and [http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/) .

Then again, if you feel you always need to tweak instead of being creative in the different linux distros but everything just work in Windows, perhaps Windows is the best choice after all. Use what works for you to keep the creative flow!

---

### Post by louh2 on 2013-09-07
Thanks for the replies, I will look into all of the suggestions to see if there is a better fit.  As for the idea about tweaking software my take is that tweaking implies that it is already working albeit not like I'd like it to.  Getting it to work properly for more than a boot cycle would be nice.  There is a lot of debate about this issue in here.  One side thinks that it has all to do with pulse audio while another opinion is that the whole audio portion of Linux needs a rework.  So far this venture into it and the one before, I did try it out a few years back, suggests the latter.  While I might not have the enormous power of the latest and greatest machine it should be no slouch to running all the tools I want to run.  The suggestion about turning wireless off is a good one.  In windows I have a vb script that will turn it off then turn it back on at the next double click.  I need to find something like that it in here, I'm sure it can be done with some terminal commands.  Anyhow I have work to do so will entertain other ideas if they come, thanks again for all the ideas.

---

### Post by mikeh789 on 2013-09-07
"better" will always be a matter of opinion. the tools ubuntustudio uses are very similar, if not exactly the same as the major tools that are used in other major distro repositories. try some other distros live and see.. there are many great ones, KXstudio and AVlinux being my favorites. the performance is quite similar with all of these *and* ubuntu with my current hardware and configuration. i would try and rule out hardware support issues from the equation, even to the point of buying hardware with linux support in mind (which i do). cheers and good luck...

---

### Post by CrocoDuck on 2013-09-08
Hi! You may be interested in this little "tutorial" I wrote: [http://linuxmusicians.com/viewtopic.php?f=19&t=10837](http://linuxmusicians.com/viewtopic.php?f=19&t=10837) . Is just a brief note of useful tips to tune a Linux installation for audio perfomances, not a real tutorial... but you find useful links. There I'm speaking about Archbang, but the tips are almost general. You also find a script to disable the unwanted services, WIFI too, I use it under US 12.04 too, that is on dual boot with Archbang in the same laptop computer. On that hardware I use the same jack setup, but Archbang is more and more stable.

In my opinion any distro, if properly tuned, is good for audio. The best choices for me are Debian based and Arch based distros, because the massive documentation and big packages databases!. Quickscan is a good tool for tuning, [https://github.com/raboof/realtimeconfigquickscan](https://github.com/raboof/realtimeconfigquickscan) . I use it everytime just after a new installation. Here a little further reading on Arch [http://openavproductions.com/real-time-latency-tuning/](http://openavproductions.com/real-time-latency-tuning/) . You may want to edit the rtirq configuration file on Ubuntu too. Around those links the keyword seems "latency", but this is not the whole story. Here a good reading: [http://apps.linuxaudio.org/wiki/jack_latency_tests](http://apps.linuxaudio.org/wiki/jack_latency_tests) .

A friend of mine solved all his audio issues with US using this: [http://www.ap-linux.com/](http://www.ap-linux.com/) ... It may fit your needings!

---

### Post by su:bhatta on 2013-09-09
> **CrocoDuck said:**
> Hi! You may be interested in this little "tutorial" I wrote: [http://linuxmusicians.com/viewtopic.php?f=19&t=10837](http://linuxmusicians.com/viewtopic.php?f=19&t=10837) . Is just a brief note of useful tips to tune a Linux installation for audio perfomances, not a real tutorial... but you find useful links. There I'm speaking about Archbang, but the tips are almost general. You also find a script to disable the unwanted services, WIFI too, I use it under US 12.04 too, that is on dual boot with Archbang in the same laptop computer. On that hardware I use the same jack setup, but Archbang is more and more stable.

In my opinion any distro, if properly tuned, is good for audio. The best choices for me are Debian based and Arch based distros, because the massive documentation and big packages databases!. Quickscan is a good tool for tuning, [https://github.com/raboof/realtimeconfigquickscan](https://github.com/raboof/realtimeconfigquickscan) . I use it everytime just after a new installation. Here a little further reading on Arch [http://openavproductions.com/real-time-latency-tuning/](http://openavproductions.com/real-time-latency-tuning/) . You may want to edit the rtirq configuration file on Ubuntu too. Around those links the keyword seems "latency", but this is not the whole story. Here a good reading: [http://apps.linuxaudio.org/wiki/jack_latency_tests](http://apps.linuxaudio.org/wiki/jack_latency_tests) .

A friend of mine solved all his audio issues with US using this: [http://www.ap-linux.com/](http://www.ap-linux.com/) ... It may fit your needings!

Thanks for sharing those great links CrocoDuck...

---

### Post by louh2 on 2013-09-13
Thanks Crocoduck, lots of things to try now and, dude, you rock as a musician too.  Thanks again man!

---

