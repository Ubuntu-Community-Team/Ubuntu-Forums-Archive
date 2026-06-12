---
title: "internal microphone doesn't pick up voice"
date: 2021-06-04
forum: Ubuntu/Debian BASED
---

### Post by optmed on 2021-06-04
hi everyone, 

Pop! OS Linux here on HP Zbook G2 (Intel® Core&#8482; i7-4810MQ CPU @ 2.80GHz / NVIDIA Corporation GK107GLM [Quadro K1100M] / Quadro K1100M/PCIe/SSE2 / Linux 5.11.0-7614-generic). Pauvcontrol and Alsamixer are installed - hope it's ok if I ask for advice on this forum? 

The HP's internal microphone is detected (plz see screenshot) but doesn't pick up my voice. It only occasionally responds to loud sounds - like clapping very near the mic itself. It used to work in Windows 10. I don't have a headset mic. I tried to "tweak" Pauvcontrol - as in "unlock/lock channels together">"silence front left or front right", to no avail.

I don't really know if the following is relevant, but I"ll post it here anyway - can you please help? thanks!

```
~$ inxi -Fxz
System:
  Kernel: 5.11.0-7614-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.7 Distro: Pop!_OS 20.04 LTS 
  base: Ubuntu 20.04 LTS Focal 
Machine:
  Type: Laptop System: Hewlett-Packard product: HP ZBook 15 G2 
  v: A3009DD10303 serial: <filter> 
  Mobo: Hewlett-Packard model: 2253 v: KBC Version 03.12 serial: <filter> 
  BIOS: Hewlett-Packard v: M70 Ver. 01.26 date: 03/03/2020 
Battery:
  ID-1: BAT0 charge: 65.5 Wh condition: 65.5/65.5 Wh (100%) 
  model: Hewlett-Packard Primary status: Full 
CPU:
  Topology: Quad Core model: Intel Core i7-4810MQ bits: 64 type: MT MCP 
  arch: Haswell rev: 3 L2 cache: 6144 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 
  bogomips: 44698 
  Speed: 1098 MHz min/max: 800/3800 MHz Core speeds (MHz): 1: 1098 2: 1107 
  3: 1062 4: 898 5: 898 6: 939 7: 948 8: 1107 
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics 
  vendor: Hewlett-Packard driver: i915 v: kernel bus ID: 00:02.0 
  Device-2: NVIDIA GK107GLM [Quadro K1100M] vendor: Hewlett-Packard 
  driver: nvidia v: 460.73.01 bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.9 driver: modesetting,nvidia 
  unloaded: fbdev,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: Quadro K1100M/PCIe/SSE2 v: 4.6.0 NVIDIA 460.73.01 
  direct render: Yes 
Audio:
  Device-1: Intel 8 Series/C220 Series High Definition Audio 
  vendor: Hewlett-Packard driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Device-2: NVIDIA GK107 HDMI Audio vendor: Hewlett-Packard 
  driver: snd_hda_intel v: kernel bus ID: 01:00.1 
  Sound Server: ALSA v: k5.11.0-7614-generic 
Network:
  Device-1: Intel Ethernet I217-LM vendor: Hewlett-Packard driver: e1000e 
  v: kernel port: 6080 bus ID: 00:19.0 
  IF: enp0s25 state: down mac: <filter> 
  Device-2: Intel Wireless 7260 driver: iwlwifi v: kernel port: 5000 
  bus ID: 3d:00.0 
  IF: wlp61s0 state: up mac: <filter> 
Drives:
  Local Storage: total: 476.94 GiB used: 48.01 GiB (10.1%) 
  ID-1: /dev/sda vendor: Kingfast model: N/A size: 476.94 GiB 
Partition:
  ID-1: / size: 464.01 GiB used: 47.87 GiB (10.3%) fs: ext4 dev: /dev/dm-1 
  ID-2: /boot size: 466.4 MiB used: 141.4 MiB (30.3%) fs: ext4 
  dev: /dev/sda1 
  ID-3: swap-1 size: 4.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-2 
Sensors:
  System Temperatures: cpu: 53.0 C mobo: 49.0 C gpu: nvidia temp: 49 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 376 Uptime: 1h 35m Memory: 15.52 GiB used: 3.45 GiB (22.2%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38 
```

---

### Post by jeremy31 on 2021-06-04
Moved to Ubuntu/Debian based

---

### Post by TheFu on 2021-06-04
In the volume control, the microphone is set really low.  Move the sliders to have more gain and ensure nothing is disabled or muted.
No need for alsamixer anymore with PulseAudio.

If you want more controls, use **pavucontrol**. Start with the tabs on the right and work left to ensure the stuff you want is enabled.  Set everything at 100%, then when your program that outputs or does recording it running, use the "Playback" and "Recording" tabs to control the levels.

---

### Post by optmed on 2021-06-05
thanks but that didn't work - all i get by increasing the volume/moving the slide up and down is at best a lot of background noise or total silence. My voice isn't picked up at all...

it looks like I can't attach an mp3 file here - anyway, I used AudioRecorder but also tried Audacity and Jitsi Meet online, same result. 

any idea?

---

### Post by TheFu on 2021-06-05
I've posted some shell commands around pacmd and pactl here.  Search for those posts and give them a try.  I recently switched from using a webcam built-in mic to a $9 lapel (for 2-pak) mic for weekly meetings. I'm assuming the audio controls and hardware are all working.  
```
# ###### Speakers ######
$ pactl list short sinks
```

```
# ###### Microphones ######
$ pactl list short sources
```

Take the "name" from the output above and use that with parecord to record a wave file. Here's an example command:
```
$ parecord -d alsa_**input**.pci-0000_0a_00.3.analog-stereo -r saved.file.wav
```

While running that command, use **pavcontrol** to monitor the levels and change as needed.  In the list created from the list of sources, microphones are "SUSPENDED" when not in active use. Also, don't choose any "monitor" source.

---

### Post by optmed on 2021-06-06
[I]$ pactl list short sinks
1    alsa_output.pci-0000_00_1b.0.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
xxx:~$ pactl list short sources
1    alsa_output.pci-0000_00_1b.0.analog-stereo.monitor    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
2    alsa_input.pci-0000_00_1b.0.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
xxx:~$ parecord -d alsa_input.pci-0000_00_1b.0.analog-stereo -r saved.file.wav[/I]

this produces a "saved.file.wav". The recording/result isn't any different from the mp3 file I described above: changing the recording levels on pavcontrol only leads to a lot of background noise, etc - my voice doesn't get picked up (see screenshots). 

all audio controls and hardware is working just fine - except for the webcam (as first tested on Kubuntu - plz see [https://ubuntuforums.org/showthread.php?t=2461004](https://ubuntuforums.org/showthread.php?t=2461004) - and now on Pop OS). 

i did find a lot of people with similar issues on a variety of forums (along the lines of [https://askubuntu.com/questions/1230283/internal-micrphone-is-not-working-in-ubuntu-20-04](https://askubuntu.com/questions/1230283/internal-micrphone-is-not-working-in-ubuntu-20-04)), and tried out a few of the "solutions" there suggested (without really knowing what I' doing...as an absolute beginner), but none of them seem to work. Could it be perhaps a driver issue of some kind? How can I verify this?

---

### Post by TheFu on 2021-06-06
**The front-right mic input is muted.**  What would happen if that was the actual input used by the microphone?

Please show the "Configuration" tab with the microphone device. 

Until recently, I would have said to just get a USB mic.  I've never had issues with those, provided they were well supported. Just plug them in and start recording.

If you are interested in USB microphones, here are a few that I know work.  If you are not, stop reading.
Have a **Samson GoMic** which is really excellent for $30 I paid 6+ yrs ago. It just works. Looks like COVID has that mic around $45 now.
Also have a Plantronics 7xx  gaming headset, think this was about $30 too.  It just works but the fancy surround sound stuff doesn't work on Linux. Output in stereo works fine. This is a full "can" type headset.

There are 3 microphones connected to my system now. Two USB and 1 analog:
```
$ pactl list short sources
0       alsa_output.pci-0000_0a_00.3.analog-stereo.monitor      module-alsa-card.c      s16le 2ch 44100Hz       SUSPENDED
1       alsa_input.pci-0000_0a_00.3.analog-stereo       module-alsa-card.c      s16le 2ch 44100Hz       SUSPENDED
2       alsa_output.usb-Plantronics_Plantronics_GameCom_780-00.analog-stereo.monitor    module-alsa-card.c      s16le 2ch 44100Hz     SUSPENDED
3       alsa_input.usb-Plantronics_**Plantronics_GameCom_780**-00.analog-stereo     module-alsa-card.c      s16le 2ch 44100Hz       SUSPENDED
4       alsa_input.usb-**Samson_Technologies_Samson_GoMic**-00.analog-stereo        module-alsa-card.c      s16le 2ch 44100Hz       SUSPENDED
```

The Samson condenser mic is great for recording 2 people talking across a table. It does pick up some surrounding noise. It is bi-directional. If you need higher quality, most people spend 3x more and get a Blue Yeti.
I wouldn't recommend the Plantronics, though it does work. When buying something that advertises 7 channel audio, I expect it to work with Linux on all 7 channels. On {that other OS}, it works great. When playing FPS games, I can here someone behind me clearly before a knife kills my character.
Also have a Logitech USB mono mic and mono headset from the SOCOM PS2 game. It works too. Just plug it in.

Whenever a USB mic is plugged in, many PulseAudio setups will automatically switch to that newly connected device. That makes one of the easiest things to pick a new mic is by just re-plugging in the device.  Can't really do that with internal microphones. ;(

Checked my records. The lapel mic using a 3.5mm input was bought as a 3-pak for $9. It is very directional.  I was trying to get a mic that would plug into smartphones and allow meeting speakers to be recorded with clear audio. My audio-fu was poor when trying to make this work in 2015. Back then, I failed and gave up.  It was purely a whim last month that got me to try the lapel mic again.

---

### Post by optmed on 2021-06-07
many thanks TheFu for the wealth of info! will have a look at the usb mics you mentioned - or "simply" use an android tablet/smartphone next to my pc (I hoped I wouldn't have to do that...). 

i tried both front-right and front-left and both - nothing works. I also tried every option in the "configuration" (plz see screenshot), to no avail. 

I'm still hoping that it might be a driver/kernel issue or that getting the right configuration might solve the problem :)

---

### Post by TheFu on 2021-06-07
In pavcontrol, Configuration on my AMD system, "Analog Stereo Duplex" is selected, but it doesn't say "Built-in Audio" - it lists the **Family 17h (...) Audio Controller**.

On an Intel G3258 system, the "Built-in Audio" is shown, but because it is hooked up to an "Analog Surround 5.1 Output" system, there isn't any microphone allowed.  In the 5.1 output mode, about 5 plugs of each color are connected in the back of the PC.  It doesn't have an analog mic input jack on the front, so I can only connect USB devices - which always work.

I'll power up an Intel Laptop in a few hours and see what I can see there.  It is an 8th Gen Core i5.  I have a Haswell laptop somewhere, but can't boot it.  I bricked it during a keyboard swap. ;(  BIOS was very picky and didn't like my custom firmware after losing battery power for a few hours. ;)

---

