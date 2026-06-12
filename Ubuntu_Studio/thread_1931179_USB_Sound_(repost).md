---
title: "USB Sound (repost)"
date: 2012-02-25
forum: Ubuntu Studio
---

### Post by clruwe on 2012-02-25
Hello community, just thought I'd give this another try in case circumstances have changed.  [FONT=Verdana]I'm having a hard time trying to get sound out of  my external USB sound card. It does not show up in Preferences>Sound  or in aplay -l. However, it does appear in lsusb.

The interface itself is called AKAI EIE Pro and it's USB 2. I don't need it to do anything but playback[/FONT].

Any help is highly appreciated!

```

lsusb:

Bus 008 Device 002: ID 045e:00dd Microsoft Corp.  Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 007 Device 003: ID 0944:010f KORG, Inc.  Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 002: ID 046d:c52b Logitech, Inc.  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 002 Device 010: ID 09e8:0010 AKAI  Professional M.I. Corp.  Bus 002 Device 009: ID 2702:2702   Bus 002 Device 008: ID 0944:010d KORG, Inc.  Bus 002 Device 007: ID 088e:5036   Bus 002 Device 006: ID 0819:0101   Bus 002 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub Bus 002 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC.  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
``````


aplay -l

**** List of PLAYBACK Hardware Devices **** card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]   Subdevices: 1/1   Subdevice #0: subdevice #0 card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]   Subdevices: 1/1   Subdevice #0: subdevice #0 
``````


sudo lshw -C multimedia

  *-multimedia UNCLAIMED          description: Audio device        product: nVidia Corporation        vendor: nVidia Corporation        physical id: 0.1        bus info: pci@0000:02:00.1        version: a1        width: 32 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list        configuration: latency=0        resources: memory:fbbfc000-fbbfffff   *-multimedia        description: Audio device        product: 82801JI (ICH10 Family) HD Audio Controller        vendor: Intel Corporation        physical id: 1b        bus info: pci@0000:00:1b.0        version: 00        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list        configuration: driver=HDA Intel latency=0        resources: irq:22 memory:f9ff8000-f9ffbfff 
```[CODE]
lsmod | grep snd

snd_hda_codec_realtek   279104  1 
snd_usb_audio          92747  0 
snd_hda_intel          25805  0 
snd_usb_lib            19193  1 snd_usb_audio
snd_hda_codec          85791  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71283  14 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm

---

### Post by jejeman on 2012-02-25
You have a mistake in the last command, it should be
```
lsmod | grep snd
```

---

### Post by sgx on 2012-02-25
Hi, if you can turn off the nvidia audio in the bios, it might help.

I have my unused Intel audio in  /etc/modprobe.d/blacklist
Its entry is

blacklist snd_intel8x0

as found in the output of lsmod

After doing that, I would power off, unplug the unit, reboot, run some commands

arecord -l && aplay -l

cat /proc/asound/cards

then insert the unit, and run the commands again.
look for the changes in the output. Use all the usb ports.
There is no law that motherboard makers implement everything correctly.

On my setup, I can insert the items listed in brackets from
arecord -l && aplay -l  output,
into qjackctl Input and Output devices
click the  >  widgets to access the entries
Cheers

---

### Post by clruwe on 2012-02-25
> **sgx said:**
> Hi, if you can turn off the nvidia audio in the bios, it might help.

I have my unused Intel audio in  /etc/modprobe.d/blacklist
Its entry is

blacklist snd_intel8x0

as found in the output of lsmod

After doing that, I would power off, unplug the unit, reboot, run some commands

arecord -l && aplay -l

cat /proc/asound/cards

then insert the unit, and run the commands again.
look for the changes in the output. Use all the usb ports.
There is no law that motherboard makers implement everything correctly.

On my setup, I can insert the items listed in brackets from
arecord -l && aplay -l  output,
into qjackctl Input and Output devices
click the  >  widgets to access the entries
Cheers

First of all thank you very much for your help! I disabled the soundcard from the bios and when I logged back in and ran cat /proc/asound/cards I got:

--- no soundcards ---

However, when I do lsusb I can see the card there:

Bus 008 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 012: ID 09e8:0010 AKAI  Professional M.I. Corp. **
Bus 002 Device 011: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 002 Device 007: ID 088e:5036  
Bus 002 Device 006: ID 0819:0101  
Bus 002 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I did try several different ports all the same result. I'm affraid to try anything else since Ubuntu is not recognizing the Akai as a soundcard. Any other ideas? 

Thanks again!

---

### Post by clruwe on 2012-02-25
> **clarkpkgm said:**
> You have a mistake in the last command

Yes I edited/fixed it, thank you!

---

### Post by sgx on 2012-02-25
Try a live-dvd of AVLinux and RemixOS, both have just released
new versions, so the kernels may have better support for modern hardware.

RemixOS takes you to a Russian hosting site, so it's a bit of an
arcade game to pick the download link,
google translate might help :)

You probably need the Akai power supply, I doubt bus power would
be enough.

There are lots of google topics to enable/disable nvidia hdmi audio,
but it looks like thats not blocking what the system itself can't yet find. Run the command ps ux
and if pulse-anything appears, run the command

killall pulseaudio   and edit /etc/pulse/client.conf and change from "; autospawn = yes" to "autospawn = no"

log out, and test again. Is this device working OK in windows?
Is the video on the motherboard, or a card?

edit>  some devices fail when both usb, and regular midi cables are connected.
Since you are wanting audio output, I would disconnect any 5-pin mid cables
for now. But it would be worth testing the 5-pins, with the usb cable not connected
just for for knowing a bit more.

install a2jmidid and run

a2jmidid -j defalt

and look in qjackctl middle midi tab.

---

### Post by clruwe on 2012-02-25
> **sgx said:**
> Try a live-dvd of AVLinux and RemixOS, both have just released
new versions, so the kernels may have better support for modern hardware.

RemixOS takes you to a Russian hosting site, so it's a bit of an
arcade game to pick the download link,
google translate might help :)

You probably need the Akai power supply, I doubt bus power would
be enough.

There are lots of google topics to enable/disable nvidia hdmi audio,
but it looks like thats not blocking what the system itself can't yet find. Run the command ps ux
and if pulse-anything appears, run the command

killall pulseaudio   and edit /etc/pulse/client.conf and change from "; autospawn = yes" to "autospawn = no"

log out, and test again. Is this device working OK in windows?
Is the video on the motherboard, or a card?

edit>  some devices fail when both usb, and regular midi cables are connected.
Since you are wanting audio output, I would disconnect any 5-pin mid cables
for now. But it would be worth testing the 5-pins, with the usb cable not connected
just for for knowing a bit more.

install a2jmidid and run

a2jmidid -j defalt

and look in qjackctl middle midi tab.

Thank you SGX! I think I'll give RemixOS a go since it's 64 bit whereas the other one isn't. Should be finished downloading in about an hour.

I am using the Akai with its power supply, always have been, don't think it would work otherwise.

When I disabled the soundcard in the bios I didn't get any sound out of my monitors, don't really care, I wouldn't use it. Just thought I'd mention it. 

I did ps ux and I got this:
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
claude    1815  0.0  0.0  70728  2720 ?        Sl   14:43   0:00 /usr/bin/gnome-
claude    1833  0.0  0.0 170572  7960 ?        Ssl  14:43   0:00 gnome-session
claude    1870  0.0  0.0  11936   412 ?        Ss   14:43   0:00 /usr/bin/ssh-ag
claude    1873  0.0  0.0  26260   824 ?        S    14:43   0:00 /usr/bin/dbus-l
claude    1874  0.0  0.0  24344  1788 ?        Ss   14:43   0:00 /bin/dbus-daemo
claude    1877  0.0  0.0  47508  6012 ?        S    14:43   0:01 /usr/lib/libgco
claude    1884  0.0  0.0 319340 16352 ?        Ss   14:43   0:02 /usr/lib/gnome-
claude    1886  0.0  0.0  49088  2572 ?        S    14:43   0:00 /usr/lib/gvfs/g
claude    1891  0.0  0.0  78032  2772 ?        Ssl  14:43   0:00 /usr/lib/gvfs//
claude    1896  0.8  0.2 311268 65460 ?        S    14:43   0:35 compiz
claude    1906  0.0  0.0 165128  7156 ?        S    14:43   0:00 /usr/lib/policy
claude    1907  0.0  0.0 176752  8720 ?        S    14:43   0:00 gnome-power-man
claude    1908  0.0  0.0 169948  8580 ?        S    14:43   0:00 bluetooth-apple
claude    1910  0.0  0.0 155052  3964 ?        S    14:43   0:00 /usr/lib/gvfs/g
claude    1911  0.0  0.0 257080 18236 ?        S    14:43   0:00 gnome-panel
claude    1912  0.0  0.1 669520 33096 ?        Sl   14:43   0:02 nautilus
claude    1913  0.0  0.0 237860 12452 ?        S    14:43   0:00 nm-applet --sm-
claude    1917  0.0  0.0 211024 12832 ?        Sl   14:43   0:02 avant-window-na
claude    1923  0.0  0.1 593076 49128 ?        Ssl  14:43   0:01 /home/claude/.d
claude    1936  0.0  0.0  56396  2740 ?        S    14:43   0:00 /usr/lib/gvfs/g
claude    1938  0.0  0.0  70296  2744 ?        Sl   14:43   0:00 /usr/lib/gvfs/g
claude    1953  0.0  0.0  53616  3252 ?        S    14:43   0:00 /usr/lib/gvfs/g
claude    1956  0.0  0.0   4096   584 ?        Ss   14:43   0:00 /bin/sh -c /usr
claude    1957  0.0  0.0 182280 11732 ?        S    14:43   0:00 /usr/bin/gtk-wi
claude    1983  0.0  0.0 219484  4152 ?        Ssl  14:43   0:00 /usr/lib/bonobo
claude    1989  0.0  0.0 211580 10884 ?        S    14:43   0:00 /usr/lib/gnome-
claude    1992  0.0  0.0 255540 14720 ?        S    14:43   0:01 /usr/lib/gnome-
claude    2003  0.0  0.0 325600 12892 ?        S    14:43   0:00 /usr/lib/indica
claude    2004  0.0  0.0 257588 14724 ?        S    14:43   0:00 /usr/lib/gnome-
claude    2007  0.0  0.0 342348 15464 ?        Sl   14:43   0:00 /usr/lib/indica
claude    2008  0.0  0.0 309912 16372 ?        S    14:43   0:00 /usr/lib/gnome-
claude    2012  0.0  0.0  44140  3452 ?        S    14:43   0:00 /usr/lib/gvfs/g
claude    2015  0.0  0.0 139176  4976 ?        S    14:43   0:00 /usr/lib/indica
claude    2019  0.0  0.0 147152  5144 ?        S    14:43   0:00 /usr/lib/indica
claude    2024  0.0  0.0 141964  5560 ?        S    14:43   0:00 /usr/lib/indica
claude    2032  0.0  0.0 145076  5696 ?        S    14:43   0:00 /usr/lib/indica
claude    2052  0.0  0.0 168508  7540 ?        S    14:43   0:00 /usr/lib/notify
claude    2093  0.0  0.0 235488 17964 ?        S    14:43   0:00 awn-applet -p /
claude    2095  0.0  0.0 227292 12996 ?        S    14:43   0:00 awn-applet -p /
claude    2096  0.0  0.0 244008 14052 ?        S    14:43   0:00 awn-applet -p /
claude    2097  0.0  0.0 234128 15648 ?        S    14:43   0:01 awn-applet -p /
claude    2098  0.0  0.1 268696 26868 ?        S    14:43   0:00 python /usr/sha
claude    2099  0.0  0.0 208364 12640 ?        S    14:43   0:00 awn-applet -p /
claude    2100  0.0  0.0 185292 11676 ?        S    14:43   0:00 awn-applet -p /
claude    2103  0.0  0.0 174636  3212 ?        Ss   14:43   0:00 gnome-screensav
claude    2109  0.0  0.0 177360  7960 ?        S    14:43   0:00 /usr/lib/gnome-
claude    2134  0.0  0.0 153612  7288 ?        S    14:44   0:00 /usr/lib/gnome-
claude    2137  0.0  0.0  48028  1996 ?        Ss   14:44   0:00 /usr/lib/apache
claude    2138  0.0  0.0  47892  1408 ?        S    14:44   0:00 /usr/lib/apache
claude    2139  0.0  0.0 156816  1520 ?        Sl   14:44   0:00 /usr/lib/apache
claude    2236  0.0  0.0 198568 12432 ?        S    14:44   0:00 update-notifier
claude    3030  7.6  1.3 1011764 335576 ?      Sl   15:19   2:37 /usr/lib/firefo
claude    3062  0.2  0.1 410836 36332 ?        Sl   15:19   0:05 /usr/lib/firefo
claude    3501  0.4  0.0 369688 19468 ?        Sl   15:51   0:00 transmission /t
claude    3568  2.5  0.0 208940 14324 ?        Sl   15:53   0:00 gnome-terminal
claude    3569  0.3  0.0  14488   812 ?        S    15:53   0:00 gnome-pty-helpe
claude    3570  4.3  0.0  22956  4684 pts/0    Ss   15:53   0:00 bash
claude    3590  0.0  0.0  16336  1228 pts/0    R+   15:53   0:00 ps ux
```Nothing about pulse....

I also installed a2jmidid but when I ran the command I got:

```
JACK MIDI <-> ALSA sequencer MIDI bridge, version 6 (a500771941cd42419a2418ee28259cde718a82bb) built on Thu Jan  1 01:00:00 1970
Copyright 2006,2007 Dmitry S. Baikov
Copyright 2007,2008,2009 Nedko Arnaudov

Bridge starting...
Using JACK server 'default'
Hardware ports will not be exported.
ERROR: a2j_jack_client_create: Cannot create jack client
ERROR: a2j_start: a2j_new() failed.

```Not sure if I even have pulse, it played havoc on the flash player (could only use one application with sound at a time) so I think I uninstalled it. I'll have a look and report any changes

Unfortunately the card is working on Windows (sigh!), but I don't want to use Windows! I like Ubuntu! Heh, heh, heh!

The video is on an Nvidia card, I don't think the motherboard has any video, in fact I'm pretty sure.

If RemixOS works, is there any way to transfer the Kernel to Ubuntu?

Thanks!

PD: Oh yes, the Akai is also a usb hub. I have several MIDI controllers plugged in to it and they're all detected and functional. Of course I've done all the tests without them connected.

---

### Post by sgx on 2012-02-26
Post your /home/you/.jackdrc file, there might be a clue in there.

If you have another midi i/o device you can test with, a2jmidid should work.

When installing another kernel, it will be listed in the boot display
as an option, same as if it were a dual-boot setup. Some distros
switch to Grub 2, a bit different than grub, av easy tutorial for using
Liquorix kernel in ubuntu spinoff Mint, is here

[http://community.linuxmint.com/tutorial/view/158](http://community.linuxmint.com/tutorial/view/158)

The main liquorix site is:   [http://liquorix.net](http://liquorix.net)
liquorix support forums are:

[http://techpatterns.com/forums/forum-34.html](http://techpatterns.com/forums/forum-34.html)
success/fail ratio should be revealed there

Checking for a motherboard bios update might be lucky,
and also using a older nvidia non-hdmi video card.
mAudio pci cards are excellent in linux, if things prove
impossible. :popcorn:

---

