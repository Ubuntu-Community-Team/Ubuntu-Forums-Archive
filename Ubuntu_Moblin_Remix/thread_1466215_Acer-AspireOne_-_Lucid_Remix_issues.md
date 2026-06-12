---
title: "Acer-AspireOne - Lucid Remix issues"
date: 2010-04-30
forum: Ubuntu Moblin Remix
---

### Post by hunter.breedlove on 2010-04-30
the issues that this netbook have after install are beyond my skill level to resolve.

Does not acknowledge SD Card reader or Microphone; turning on OSS and IHU didn't help.    I

If anyone knows more and has a workaround; please let me know .. ..

---

### Post by lou002 on 2010-05-03
I didn't notice any of that on mine; did you any issues with your battery too?

---

### Post by MetalMick on 2010-05-03
> **lou002 said:**
> I didn't notice any of that on mine; did you any issues with your battery too?

Same issue here!!!

Ubuntu only see's the battery/hardware once you have disconnected or connected from AC power.

Also the scroll on the touchpad is not working...

Both worked fine under 9.10.

Using an Acer Aspire One 50.

---

### Post by cariboo on 2010-05-03
> **hunter.breedlove said:**
> the issues that this netbook have after install are beyond my skill level to resolve.

Does not acknowledge SD Card reader or Microphone; turning on OSS and IHU didn't help.    I

If anyone knows more and has a workaround; please let me know .. ..

What is the output of dmesg when you plug in your SD card?

---

### Post by MetalMick on 2010-05-03
> **cariboo907 said:**
> What is the output of dmesg when you plug in your SD card?

I'm seeing:

[26529.696096] usb 1-5: new high speed USB device using ehci_hcd and address 8
[26529.829924] usb 1-5: configuration #1 chosen from 1 choice

---

### Post by MetalMick on 2010-05-04
> **MetalMick said:**
> Same issue here!!!

Ubuntu only see's the battery/hardware once you have disconnected or connected from AC power.


Works fine if your NOT using an encrypted home directory.

---

### Post by cataztrophe on 2010-05-05
same with me here, its make me grazy!

---

### Post by jaezcurra on 2010-05-05
The problem I am facing is with the whole sound system: no sound at all, whatever I try

---

### Post by Dorkenfarber on 2010-05-05
I have an Aspire One with UNE 10.04. I have noticed the touchpad preferences doesn't change anything. It doesn't disable when I type, and I can't set it to disable tap clicking. well I can set it, but the setting doesn't have any effect. also scroll doesn't work. 
   I use a wireless usb mouse so I don't need the touchpad at all. It just gets in the way when I try to type and accidentally bump the touchpad and it randomly clicks something.

---

### Post by jaezcurra on 2010-05-06
I guess I could be the only one Acer Aspire One with sound issues running UNE 10.04 (upgrade from UNR 9.10).

Any suggestion from anyone whose sound is OK?  Please   ;)

---

### Post by jaezcurra on 2010-05-06
Bump

---

### Post by jaezcurra on 2010-05-07
Well, I was wrong: headphones work.  So, the sound issues concern only external loudspeaker.  Any suggestion?

---

### Post by MetalMick on 2010-05-07
> **jaezcurra said:**
> I guess I could be the only one Acer Aspire One with sound issues running UNE 10.04 (upgrade from UNR 9.10).

Any suggestion from anyone whose sound is OK?  Please   ;)


Did you un-mute the sound card? It's muted by default in 10.4...

If your still having issues can you post the output from:

```
cat /dev/sndstat
```

---

### Post by MetalMick on 2010-05-07
> **jaezcurra said:**
> Well, I was wrong: headphones work.  So, the sound issues concern only external loudspeaker.  Any suggestion?

In your sound preferences.. Under the output tab, have you tied setting the connector type?

---

### Post by jaezcurra on 2010-05-07
Solved!!!
It was a matter of tuning Sound Preferences: Output Devices

Thanks, MetalMick!!!

---

### Post by Goatrancer on 2010-05-08
I too have an AspireOne (1410) and am not getting any sound. Sound Preferences: Output devices shows only one option "Summy Output stereo"

the  cat /dev/sndstat thing gave the following output:

```
Sound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)
Kernel: Linux james-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0x94500000 irq 22

Audio devices:
0: ALC269 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Intel G45 DEVCTG

```

---

### Post by Nin-lil-izi on 2010-05-08
Working perfect on my AspireOne 150

to fix the scroll on your touchpad type:

```
sudo apt-get install xserver-org-input-synaptics
```
You have to logout/restart for it to take effect. :-)


Also, to improve handling of its fan put the following in '*/etc/modprobe.d/acerhdf.conf*'
```
options acerhdf kernelmode=1
```

( To open the file for editing )
```
gksudo gedit /etc/modprobe.d/acerhdf.conf
```

Then before restarting. Put the following in the terminal
[HTML]sudo depmod -a[/HTML]

---

### Post by cariboo on 2010-05-09
To make sure nothing is muted, open a terminal and type:

```
alsamixer
```

You have to use the arrow keys to navigate. If you find that something is muted, use the **M** to unmute. To exit the program press esc. To make the changes you have made stick, at the prompt type:

```
sudo alsactl store
```

---

### Post by Mickey G2 on 2010-05-09
Hi There,

    Is there any news on the SD card issue. I read that the card reader is ENE UB6250 and is not supported in the kernel.

Is this true and is there a module I could install to make it work?

Thanks

Mickey G2

---

### Post by Dorkenfarber on 2010-05-15
Is there any special code to disable the touchpad? Or to make the settings have some sort of effect on the touchpad? Random mouse clicks aren't fun.

---

### Post by MetalMick on 2010-05-19
> **Dorkenfarber said:**
> Is there any special code to disable the touchpad? Or to make the settings have some sort of effect on the touchpad? Random mouse clicks aren't fun.

Same issue here!

BTW:

* Touchpad scroll still not working after installing xserver-org-input-synaptics

* Big issues with battery monitor jumping from around 60% dischanged to 0% then shutting down...

---

### Post by spot-da-haze on 2010-05-19
Hi all kinda new here if had the same battery issue , thou it seams once in a while when I boot up my mouse starts spazzing out big time ultra sensitive , random clicking lift and right ... I've upgraded from 9.10 to 10.04 oh I'm using the kubuntu remix

-spot

---

### Post by itchy8me on 2010-05-24
having problems here as well, running ubuntu live goes smoothly, once installed and updated though 2 big problems surface, namely:

- battery is reported as broken and capacity is at 49%
- laptop is extremly slow and report ata read/write problems, in the end after many reboots the disk seems to be corrupted and can no longer be mounted.

for the rest it looks great, only i cannot use it installed on the harddrive :(

[I]edit: sorry i didnt read the title properly, i'm having these problems with ubuntu netbook remix. i'm guessing a bug in the kernel. the latest linux mint gives me the same problems. I scanned the laptop hard disk with KDE partition manager on my desktop and it gave me the following:

> Check and repair partition &#8216;/dev/sdb1&#8217; (111.79 GiB, ext4) 
Job: Check file system on partition &#8216;/dev/sdb1&#8217; 
Command: e2fsck -f -y -v /dev/sdb1 
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      11 inodes used (0.00%)
       0 non-contiguous files (0.0%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 1
  508179 blocks used (1.73%)
       0 bad blocks
       1 large file

       0 regular files
       2 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       2 files 
Check file system on partition &#8216;/dev/sdb1&#8217;: Success

Job: Maximize file system on &#8216;/dev/sdb1&#8217; to fill the partition 
The file system on partition &#8216;/dev/sdb1&#8217; already has the requested length of 234,436,482 sectors. 
Maximize file system on &#8216;/dev/sdb1&#8217; to fill the partition: Success
Check and repair partition &#8216;/dev/sdb1&#8217; (111.79 GiB, ext4): Success

looks good i think. moblin looks good too, going to give it a try.[/I]

---

### Post by Dorkenfarber on 2010-05-30
> **MetalMick said:**
> Same issue here!

BTW:

* Touchpad scroll still not working after installing xserver-org-input-synaptics

* Big issues with battery monitor jumping from around 60% dischanged to 0% then shutting down...

After I posted that my sister showed me that Fn+F7 disables the touchpad. lol

---

### Post by ducaati on 2010-06-11
No video in skype, java applet for currency trading no longer works- this all worked fine in 9.04. I regret the upgrade, all on an ACER aspire one.

---

### Post by MetalMick on 2010-06-13
Battery jumps to 0% (flat) more so when the CPU is under mild to heavy load!!

Bump! This sucks!

---

