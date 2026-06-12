---
title: "Getting a Xonar DG hooked up and working in Ubuntu"
date: 2012-01-31
forum: Ubuntu Studio
---

### Post by nazaroo2 on 2012-01-31
placed Xonar DG in PCI slot in my Dell Optiplex 330.

Physically installing the card wasn't enough:
Sound from mplayer still plays back through onboard soundcard.

I did the following, using advice from previous thread with RPx400 setup:

In a terminal I ran:
```

 ~# arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
 ~# 

```When I did this with the RPx400 installed on a USB port, it actually listed the device.
Here I seem to get nothing, or simply an unknown undefined device (?).

aplay -l gives this:

```
~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
~# 

```This just appears to be my onboard playback sound device.


amidi -l gives this:

>  ~# amidi -l
Dir Device    Name
 ~# 
That is, no MIDI device(s) are listed.

Now when I run:
cat ~/.jackdrc

 ```
 ~# cat ~/.jackdrc
/usr/bin/jackd -dalsa -r44100 -p1024 -n2 **-D -Chw:1 -Phw:0**
 ~# 
```But this looks slightly different than what I got when I ran the same command before with the RPx400 installed, with no soundcard.
That output was missing the last bits:

```
/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
```Don't know the significance of that, 
and when I ran JACK, I didn't see a way of selecting the Xonar DG card.

Does anyone know what I should do next? :frown:

---

### Post by nazaroo2 on 2012-01-31
I ran JACK, and I noticed that on booting up, the following messages appear in the JACK msg box:

```
 [COLOR=Blue]   JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
 ALSA: Cannot open PCM device alsa_pcm for capture. **Falling back to playback-only mode**
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback[/COLOR]
 [COLOR=#999933]04:21:28.024 Server configuration saved to "/root/.jackdrc".[/COLOR]
 [COLOR=#999999]04:21:28.033 Statistics reset.[/COLOR]
 [COLOR=#999999]04:21:28.428 Client activated.[/COLOR]
 [COLOR=#9999cc]04:21:28.429 JACK connection change.[/COLOR]
 [COLOR=#cc9966]04:21:28.434 JACK connection graph change.[/COLOR]

```It seems to have recompiled itself, 
then failed to find an input device, or maybe failed to initiate it (?).

"Falling back to playback-only mode"  is disturbing...

Also, [COLOR=Blue]**System Input**[/COLOR] fails to show up in **Patchage** window.

---

### Post by nazaroo2 on 2012-01-31
I thought maybe I had to deactivate my onboard sound through the BIOS,
so I did a Cold Boot (otherwise I don't get to the DELL BIOS editor):

Then I deactiveated "integrated audio" from the BIOS.
When I rebooted, I got the following result:

(1)  Alsa mixer shows no sliders at all.

(2)  Gnome mplayer will play a song, but no sound comes out of either onboard or the Xonar card.

(3)  Headphone jack on front also does not play sound.

(4)  Running JACK gives the following startup error Dialog:

```
  p, li { white-space: pre-wrap; }  Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info.

```The output in the JACK message box looks like this:

 ```
    [COLOR=Blue]no message buffer overruns[/COLOR]
[COLOR=Blue]JACK compiled with System V SHM support.[/COLOR]
[COLOR=Blue]loading driver ..[/COLOR]
[COLOR=Blue]apparent rate = 44100[/COLOR]
[COLOR=Blue]creating alsa driver ... hw:0|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit[/COLOR]
[COLOR=Blue]control device hw:0[/COLOR]
[COLOR=Blue]control open "hw:0" (No such file or directory)[/COLOR]
[COLOR=Blue]ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card[/COLOR]
[COLOR=Blue]ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card[/COLOR]
[COLOR=Blue]ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[/COLOR]
[COLOR=Blue]cannot load driver module alsa[/COLOR]
 [COLOR=#999999]04:53:26.493 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]04:53:26.494 Post-shutdown script...[/COLOR]
 [COLOR=#990099]04:53:26.494 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]04:53:26.910 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]04:53:27.959 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```

I'm going to put back the "integrated audio" in the BIOS with another Cold Boot...

---

### Post by nazaroo2 on 2012-01-31
Okay 'integrated audio' restored in BIOS,

(1)  ALSA mixer appears normal.

(2)  Gnome mplayer plays mp3s to headphone jack (onboard sound).

(3)  Audacious produces no sound.

(4)  JACK is back to "NORMAL", i.e., shows the default onboard audio output and no input....

(5)  Xonar appears undetected.

---

### Post by jejeman on 2012-01-31
First we need to see if the card is detected
```

lspci
```

---

### Post by nazaroo2 on 2012-01-31
Thank you!  for helping:

Okay I typed lspci into the terminal:

```
 
 ~# lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 0a)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 0a)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express (rev 02)
[COLOR=Blue][B]03:02.0 Multimedia audio controller: 
C-Media Electronics Inc CMI8788 [Oxygen HD Audio][/B][/COLOR]
 ~#  

```

Wow!  that last one must by my card.
Thats the best news so far...
I hope I can use this info.  
Is the thing in brackets the name/codename/handle to reference the device?

---

### Post by nazaroo2 on 2012-01-31
by the way, there seems to be two different programs in Ubuntu with the same name(!):

**Gnome Alsamixer** shows a white/gray window with sliders,
but [COLOR=Blue]***alsamixer in the terminal***[/COLOR] opens a window with a black background, which seems to have more options.  That is odd.

In the terminal version of **alsamixer,**
if I hit F2 [System Information], and from the blue dialogue window I select /proc/asound/cards, 
another blue dialog box opens that tells me I have:
```
 
0 [Intel  1: HDA-Intel - HDA Intel
                  HDA Intel at 0xdfffc000 irq 16  
```- but I suspect this is just the onboard soundcard, and that alsamixer doesn't recognise the new Xonar sound card.
Am I right?

***I also tried*** typing in the bracketed name in the listing above, [[COLOR=Blue]Oxygen HD Audio[/COLOR]], 
into the 'select sound card' option on F6, but that failed.

What am I doing wrong here?

---

### Post by jejeman on 2012-01-31
Now, lets see in which state are the modules
```
sudo lshw -C multimedia
```

---

### Post by nazaroo2 on 2012-01-31
okay :

```
~# sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:dfffc000-dfffffff
  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: CMI8788 [Oxygen HD Audio]
       vendor: C-Media Electronics Inc
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=24 mingnt=2
       resources: ioport:cc00(size=256)
~# 

```hmmmm...how come the onboard card is 64 bits [!] and my new awesome card is only 32 [!?!]
...and shouldn't the latency be 0 for the new card, and crappy for the onboard?

---

### Post by jejeman on 2012-01-31
Try now to load modules mannualy as root
```
modprobe snd-oxygen ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

```

---

### Post by nazaroo2 on 2012-01-31
Okay I executed the following in a terminal. 
Looks like nothing happened.

```
 ~# modprobe snd-oxygen ; modprobe snd-pcm-oss ; 
modprobe snd-mixer-oss ; modprobe snd-seq-oss
 ~# 

```i.e., ***no error msgs*** or any msgs at all in the terminal.

...also, nothing different when I run **alsamixer in a terminal**:
 same options, seems to be no 2nd card or choice for soundcard.

**JACK** looks the same too...

---

### Post by MoreOrLess on 2012-01-31
Nvm, see next post.

---

### Post by MoreOrLess on 2012-01-31
You're going to need alsa driver 1.0.24 for the card to work. alsa 1.0.25 was supposed to fix the ouput routing, but the front headphone jack still doesn't work on my system (sound still comes out of speakers when FP Headphones is selected in alsamixer).

---

### Post by nazaroo2 on 2012-02-01
> **MoreOrLess said:**
> You're going to need alsa driver 1.0.24 for the card to work. alsa 1.0.25 was supposed to fix the ouput routing, but the front headphone jack still doesn't work on my system (sound still comes out of speakers when FP Headphones is selected in alsamixer).


Thanks for your reply:

How do I switch out one driver and switch in the other?
Is there a way to specify what version of alsadriver that I want?

---

### Post by sgx on 2012-02-01
When a command is entered, no response usually means success.
An error will gladly follow if there was a problem.

use the lsmod command to view your kernel modules, and which ones
they interact with. Those made available by the modprobe command,
will be in the list.

What are the available devics in the dropdown lists from qjackctl

Input Device >
Output Device >
?

install alsamixergui, and scroll horizontal or stretch the gui as needed
Cheers

---

### Post by nazaroo2 on 2012-02-01
[I][COLOR=Blue]use the lsmod command to view your kernel modules, and which ones
they interact with. Those made available by the modprobe command,
will be in the list.
[/COLOR][/I]

**lsmod gives this**:

```

# lsmod
Module                  Size  Used by
snd_oxygen              5042  0 
snd_oxygen_lib         28806  1 snd_oxygen
snd_mpu401_uart         5617  1 snd_oxygen_lib
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_intel8x0           25652  0 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  5 snd_oxygen,snd_oxygen_lib,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  13 snd_oxygen,snd_oxygen_lib,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usblp                  10481  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
parport_pc             25962  1 
joydev                  8740  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
dell_wmi                1793  0 
dcdbas                  5422  0 
psmouse                63677  0 
serio_raw               3978  0 
nvidia               9961216  38 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
intel_agp              24375  0 
agpgart                31724  2 nvidia,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
tg3                   109324  0 
ahci                   32360  2 
 # 


```[I][COLOR=Blue]

[/COLOR][/I][COLOR=Black][B]Are these items (kernel modules) names or handles by which I can access the soundcard?

Like do I define an output by typing in and using a name on this list somewhere?
[/B][/COLOR][I][COLOR=Blue]


-------------------------------------


What are the available devics in the dropdown lists from qjackctl

Input Device >
Output Device >
?[/COLOR][/I]


OMG!  Are you kidding me? --> to the programming world:

I can't copy, cut or paste the drop-down list from JACK, 
AND I can't copy it by hand into a textfile, because it deselects itself and closes whenever its not the active window!
ALSO, I can't even snapshot it either, *because it deselects itself and closes whenever its not the active window!*

@!#$%^^&*()_+
This is the 21st century?

I happen luckily to have however a 15th century device called a pencil...

[COLOR=Blue]**Input Device:**
hw:1 
(default)
hw:0
plughw:0
/dev/audio
/dev/dsp

**Output Device:**
 (default)
hw:0
plughw:0
/dev/audio
/dev/dsp[/COLOR]

---

### Post by nazaroo2 on 2012-02-01
tried various things in JACK, got some errors.

I try  ***aplay -l ***and*** arecord -l***, and get told I have no soundcards.

But when I type*** lspci***, the card is sitting there. 

 
```

#** aplay -l**
[COLOR=Red]aplay: device_list:223: no soundcards found...[/COLOR]
 #
 
```

 ```

**# lspci**
...
[COLOR=Blue]03:02.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio][/COLOR]
 
```


**[COLOR=Blue]*install alsamixergui, and scroll horizontal or stretch the gui as needed*[/COLOR]**

> 
** # install alsamixergui**
install: missing destination file operand after `alsamixergui'
Try `install --help' for more information.
 # 



I admit I don't know how to install alsamixergui.... can you give me a hand on that?

---

### Post by nazaroo2 on 2012-02-01
Okay, did a little checking.

According to **Synaptic Package Manager** I already had ***alsamixergui ***installed.
So, I marked it for reinstallation, and reinstalled it.
the version before was 2-1-9, and the version now is the same, **0.9orc.2-1-9**.


Now typing ***alsamixer*** from a terminal just gives a [COLOR=Red]***no such file or dir***[/COLOR] error.  Doing that used to work a day or so ago.

running [COLOR=Blue]***alsamixer[COLOR=Red]gui[/COLOR]***[/COLOR] from a terminal gives a sad picture:

 [IMG]http://3.bp.blogspot.com/-wj6OfdYdhX4/TykhrKHHGHI/AAAAAAAAAzU/o8C5LXPzgEg/s1600/Screenshot.png[/IMG]


No amount of expanding causes any more sliders to appear.

(before disabling my onboard audio in the BIOS, one version of the alsamixer looked like this below:
[IMG]http://4.bp.blogspot.com/-_dcXZha5WNM/TyC85Ya3pyI/AAAAAAAAAvs/f1ZFeEUxuhg/s640/alsamixer1.png[/IMG]

---

### Post by nazaroo2 on 2012-02-01
> **MoreOrLess said:**
> 
You're going to need alsa driver 1.0.24 for the card to work.
 alsa 1.0.25 was supposed to fix the ouput routing, 
but the front headphone jack still doesn't work on my system 
(sound still comes out of speakers when FP Headphones is selected in alsamixer).

Where can I get a copy of this important fie, and how do I install it instead of the newest alsadriver?

---------
_**Quick Update:**_


Okay, I googled this and found this page: [[FONT=Lucida Sans]**Update ALSA driver for Ubuntu**[/FONT]]("http://www.stchman.com/alsa_update.html")

I copied the** alsa_setup.sh** file to /root [?]  
and did the two commands in the terminal (chmod... and sudo ...)

There was a long list of compiling msgs and warnings, then machine rebooted itself. 
Nothing seems to have been harmed (more than it was).

I now assume I have the latest version of the **alsadriver** (apparently a different thing than the **alsamixergui**).

So now all I have to do is

(1)   figure out what version was actually installed,  (presumably its now alsa 1.0.25  or higher).

(2)   find the earlier version and install that instead. (presumably alsa driver 1.0.24 )

[B]I have no idea how to do either (1) or (2)...


-------------------------------

UPDATE 2:

uh oh, Now running JACK gives this error:

[/B]>   Could not open ALSA sequencer as a client.
  ALSA MIDI patchbay will be not available.
In the boot dialog box JACK says:

>     [COLOR=#999999]06:50:16.214 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]06:50:16.301 Statistics reset.[/COLOR]
 [COLOR=#ff0000]06:50:16.302 Could not open ALSA sequencer as a client. ALSA MIDI patchbay will be not available.[/COLOR]
 ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
...looks like JACK got broken by the installation of alsadriver...

Now what should I do?

---

### Post by MoreOrLess on 2012-02-01
That script is really old. Try this instead. [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

This command shows the version of the alsa kernel module:
```
cat /proc/asound/version
```

---

### Post by nazaroo2 on 2012-02-01
Okay, maybe I should have gone to ALSA site for this.
Here is their page[?]:
[URL="http://www.atoztoa.com/2010/01/install-alsa-latest-version-in-ubuntu.html"]
Install ALSA latest Version in Ubuntu[/URL]

They report the latest stable version of alsadriver (or alsa-driver?) is 1.0.25.

Only I can't get off the ground here, because I can't check the version as they instruct:

executing  $ **[COLOR=Red]cat /proc/asound/version[/COLOR]**
in a terminal just gives me a directory not found error:

```
# cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
  #
```I apparently don't have things in the same folder as I'm supposed to,
and I have no idea what to do next.
I could use their script to reinstall the latest, but since even the folders are in question, 
won't this be futile, and dangerously stupid?

---

### Post by nazaroo2 on 2012-02-01
> **MoreOrLess said:**
> That script is really old. Try this instead. [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

This command shows the version of the alsa kernel module:
```
cat /proc/asound/version
```

Yes, I've seen that thread before, and didn't understand it.
But I noted the warning at the top:

>                                                    [COLOR=Red]**Disclaimer: Don't use this script unless you know what it's really doing**[/COLOR]..which seemed to fit my case, because not only couldn't I understand what was going on,
I couldn't tell which versions or edits of the script(s) were the most recent, from all the posts and changes.

Its just not fair to point a newbie at a thread like that, let them loose,
and expect them to install complex subsystems in OS software.
Come on, give me a break here. 
If I'm supposed to execute a script from that thread, where is it? No, wait:
 better, can you please paste the CORRECTED working version here?

Also, how does this help, since there is nothing there to tell me how to install
the PREVIOUS version, which you are recommending?

Could you provide the working commands to follow your advice?
Thank you in advance.  There's simply no way I can do this on my own here.

As explained in my previous post, the [COLOR=Blue]**"cat /proc..."**[/COLOR] command doesn't work.

---

### Post by nazaroo2 on 2012-02-01
Look, to recap:

(1a) I had installed the music software from some page somewhere telling me how to install everything. 

(1) I was using the onboard soundcard to playback (Dell 330), 
         and a Digitech RPx400 (USB output) to record some guitar on computer.  That was sort of working.

(2) I wanted a better quality A/D converter (24 bit, 48/96 kHz) for recording vocals, and playback.

(3) I installed an ASUS Xonar DG soundcard, intending to use it for both playback and record.

(4) I disabled the onboard soundcard in the Dell BIOS.

(5)  Now I have nothing except my son's kazoo, for sound.

Did I just waste $60 on a useless soundcard?

If this is how things end with a supported card, what would happen with an unsupported unit?
Maybe I should buy another box, install Windoze, and plug the card in there to record sounds.
That would only set me back $500 of my food money.
Please shoot me.

---

### Post by MoreOrLess on 2012-02-01
You had no issue using a script which installed an ancient version of alsa (1.0.16) and messed up your system, but you can't use the other script?

> Did I just waste $60 on a useless soundcard?
$60? On a Xonar DG?

Try a LiveCD of Ubuntu 11.10 and the card should work well. 11.04 is too old to support it and you seem to be having issues upgrading alsa.

---

### Post by sgx on 2012-02-01
> **nazaroo2 said:**
> 
Did I just waste $60 on a useless soundcard?

Please shoot me.
Hi, relax, try the other distros, and to be honest, I gave you the
best option at the price range, an maudio audiophile 24/96 pci

but if you can't get the card you have working in other distros,
sell or trade it, and get the maudio card. It is actually
very common for linux people to try several devices, before finding
a good fit.

use a filemanager to see the contents of the folder /proc/asound
a text file called version should be nearby. You can read it in
an editor like gedit, kwrite, leafpad etc I list the contents of the files in my asound folder, and other folders with more files
are also there.

bash-4.1$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23

bash-4.1$ cat /proc/asound/cards
 0 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xac00, irq 17

bash-4.1$ cat /proc/asound/devices
  1:        : sequencer
  2: [ 0- 0]: raw midi
  3: [ 0- 0]: digital audio playback
  4: [ 0- 0]: digital audio capture
  5: [ 0]   : control
 33:        : timer

bash-4.1$ cat /proc/asound/pcm
00-00: ICE1712 multi : ICE1712 multi : playback 1 : capture 1

bash-4.1$ cat /proc/asound/timers
G0: system timer : 1000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE

bash-4.1$ cat /proc/asound/modules
 0 snd_ice1712

the lsmod    command show that snd_ice1712 in its output, its
the support module for maudio pci soundcards.
Cheers

---

### Post by nazaroo2 on 2012-02-02
[SIZE=3]**Thanks **[/SIZE]for everyone's help in this thread.

Here is my update:

I took the advice of **MoreOrLess **here:

> **Try a LiveCD of Ubuntu 11.10** and the card should work well. 
11.04 is too  old to support it and you seem to be having issues upgrading alsa.     I have a partial success:
[COLOR=Red][B]
I installed 11.10 [/B][/COLOR]overtop my earlier Ubuntu.

I lost my dual screens, and had a few problems getting ROOT to work as a logon.

I spent all night re-installing it, as I had trouble with the **Nvidia drivers **(tried a few, and ROOT kept hanging after login.)

I have given up on the dual-screen idea for now, and decided I was trying to do too much at once.

I'll save dual screens for a later project.

Right now I'm completely disoriented with the latest GUI, and it took me a couple of hours just to find the Terminal AHHHHHH!
I'm over that now. 

I was going to install the UbuntuStudio disk, but then realised it would again overwrite my OS!

So instead, since I only want AUDIO, 
I just installed JACK(cntrl), Ardour, Hydrogen, Rakkarack, and Patchage.

Surprisingly, (since I disabled the onboard sound in the BIOS already), 
[SIZE=2]**the sound playback works now through the ASUS Xonar card!   Y**[/SIZE]AY!

This alone is amazing!

Although I currently have a crappy Yamaha receiver with old Mission 717 speakers for playback,
I'm hoping that eventually I will appreciate the 24 bit playback of the Xonar card soon.
I have been playing back mp3s through Banshee Media Player, which automatically attaches itself to the JACK system Output if you run it AFTER running JACk.


However, I have one remaining problem with the Xonar DG card:
I can't seem to put any INPUT into the LineIn on the top/back minijack on the card.

If I hook the System Input (in Patchage/JACK) to the Output, no sound is heard.

I have looked at the JACKctrl, and the Xonar seems to be listed as HD:0., for both Input and Output.

Can anyone help me get the inputs working?

---

### Post by nazaroo2 on 2012-02-02
> **MoreOrLess said:**
> You had no issue using a script which installed an ancient version of alsa (1.0.16) and messed up your system, but you can't use the other script?


Well, keep in mind I am just guessing about how to 'execute' what I am reading.
Usually I just cut and paste whatever someone posts, and says will work. 
I cross my fingers, and hope it applies to my box / OS. 
Sometimes it works, sometimes not...

> 

$60? On a Xonar DG?


This is Canada, where we pay 2x for everything we have to import, 
because our glorious leaders had all the local industry relocate to China.

> 

Try a LiveCD of Ubuntu 11.10 and the card should work well. 11.04 is too old to support it and you seem to be having issues upgrading alsa.

Done!  Thanks for this!
But I haven't yet got RECORD/INPUT working, and my dual screens are gone at the moment....
Can you help?
Sounds like you got your card working

---

### Post by sgx on 2012-02-02
> **nazaroo2 said:**
> 

This is Canada, where we pay 2x for everything we have to import, 
because our glorious leaders had all the local industry relocate to China.


Your country chose to form an elite socialist political class,
with exorbitant pensions, benefits and salaries, that mismanages
your healthcare, energy, and everything else, while funding themselves with luxury and secure employment. The massive tax burden placed on you, and your businesses, forced many to relocate, or fail. Business exists to generate profits, not to fund freedom crushing control freak politicians.

In the qjackctl dropdown menus at the setup page

Input device  >
Output device  >

are the available choices the same in each one? Normally
you would choose the same device name in each one, unless
you needed a specific device that is an input-only device,
like my guitar interface.

If the available choices don't work, I would place the text
found in the brackets of the    aplay -l   output in the dropdown,
without the brackets

bash-4.1$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My card has two titles in the brackets, and both are listed as
shown above, in qjackctl dropdown. Hope this also works for you!
Cheers

---

### Post by nazaroo2 on 2012-02-02
Okay here is what aplay says:

```

 # aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: DG [Xonar DG], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 # 


```


Not that I know what that means...

And here is what JACKcntrl has in each dropdown:

Input[Output] Device:

[B]hw:0
(default)
plugwh:0
/dev/audio
/dev/dsp[/B]

(both Input and Output are the same).

I'm thinking they are "working", except maybe the Xonar volume is set to zero for the input devices (A/D converters)..just a guess.

Somewhere I read that this card (unlike the more expensive ones) is lacking a volume control or something. Maybe there is a special initialization that has to happen for it to work.

---

### Post by nazaroo2 on 2012-02-02
> **sgx said:**
> Your country chose to form an elite socialist political class,
with exorbitant pensions, benefits and salaries, that mismanages
your healthcare, energy, and everything else, while funding themselves with luxury and secure employment. The massive tax burden placed on you, and your businesses, forced many to relocate, or fail. Business exists to generate profits, not to fund freedom crushing control freak politicians.

  

...only the tip of the iceberg.
You forgot to mention that the 'socialist elite' is made up of lesbians and queers.
But thats another sad story.

---

### Post by sgx on 2012-02-02
> **nazaroo2 said:**
> Okay here is what aplay says:

```

 # aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: DG [Xonar DG], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 # 


```


Not that I know what that means...

And here is what JACKcntrl has in each dropdown:

Input[Output] Device:

[B]hw:0
(default)
plugwh:0
/dev/audio
/dev/dsp[/B]

(both Input and Output are the same).

I'm thinking they are "working", except maybe the Xonar volume is set to zero for the input devices (A/D converters)..just a guess.

Somewhere I read that this card (unlike the more expensive ones) is lacking a volume control or something. Maybe there is a special initialization that has to happen for it to work.
Substitute  Xonar DG
for hw:0  logout and back in, and test, and re-check alsmixergui,
which should find new ports as the system recognizes them.

and repeat the process for plughw:0

My mAudio card also lacks a mixer, which is not a problem,
gnome, kde, and other mixers all find the available channels.
Cheers

edit, also use   Digital    as replacement for hw0: etc if the above don't work,
to cover the known possibilities.

---

### Post by nazaroo2 on 2012-02-03
> **sgx said:**
> Substitute  Xonar DG
for hw:0  logout and back in, and test, and re-check alsmixergui,
which should find new ports as the system recognizes them.

and repeat the process for plughw:0

My mAudio card also lacks a mixer, which is not a problem,
gnome, kde, and other mixers all find the available channels.
Cheers

edit, also use   Digital    as replacement for hw0: etc if the above don't work,
to cover the known possibilities.

I tried typing in Xonar DG, but it seemed to make no difference. 

What is plughw:0?  

If I don't need a 'mixer' like alsa-mixer, then what exactly do I need to get JACK to use the new soundcard?

Is "Digital" the output or the input section of the soundcard?

---

### Post by nazaroo2 on 2012-02-03
Okay to update:

JACK seems to be running again...I think,
and I can run patchage and ardour.

Also, the sound from Ardour will go to the System Output through JACK /Patchage. 
Yet still I am getting no sound coming in from the Analog input, which should be wired by JACK,
to be the System Input.
Why is JACK able to use the card for System out, but not System in?
(I was using (default) in the JACK Setup dialog.)

---

### Post by nazaroo2 on 2012-02-03
As a secondary A/B test,

I have also plugged in the RPx400 USB A/D footpedal.

Previously, I was able to assign this to the System Inputs.

The computer now has onboard soundcard disabled in BIOS,
the Xonar DG in a PCI slot,
and the RPx400 in a USB port.

Here is the result of aplay and arecord -l in the terminal:

```
~# arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@ben-OptiPlex-330:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DG [Xonar DG], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@ben-OptiPlex-330:~# 

```

However, these don't seem to be showing up in JACK.

Yet they do show up in the secondary list (-> right arrow) beside Input/Output Device boxes in Jack Setup:

[COLOR=Blue]_**Input: **_
hw:0 Xonar DG
hw:0,0 Multichannel [i.e., 7 channel output?]
hw:1  RPx400
hw:1,0 USB Audio
hw:1,1 USB Audio #1

_**Output:**_
hw:0 Xonar DG
hw:0,0 Multichannel  
**hw:0,1 Digital**
hw:1  RPx400
hw:1,0 USB Audio
hw:1,1 USB Audio #1[/COLOR]

The OUTPUT seems to have one extra listing, but I don't know why.

---

### Post by nazaroo2 on 2012-02-03
```
~# modprobe snd-oxygen ; modprobe snd-pcm-oss ; 
FATAL: Module snd_pcm_oss not found.
root@ben-OptiPlex-330:~# modprobe snd-mixer-oss ; modprobe snd-seq-oss
FATAL: Module snd_mixer_oss not found.
FATAL: Module snd_seq_oss not found.
root@ben-OptiPlex-330:~# 


```With the new Ubuntu 11.10, these commands also seem to fail. 
Before they gave no error at least.

Only modprobe snd-oxygen seems to work.

Does this mean anything?
Am I using Alsa, or Pulse? and which should I be using?
[B]
Updat[/B][B]e:
Plugging in the RPx400 is detected,[/B] but I can't get the guitar to be picked up by the system, like it did in Ubuntu 10.00..!!!!

I tried assigning hw:0 to System Output (that works, I can hear previously recorded stuff in Ardour).
and hw:1 to System Input (hoping for guitar on RPx400/USB), but that gives no sound.

In a way this is good, because it seems to indicate there is nothing wrong with the soundcard, 
since Ubuntu 11.10 can't record from the RPx400 either!


So, having Ubuntu 11.10 detects input devices, but won't seem to take sound from them for recording...

If I can't get ANY input device to work in Ubuntu 11.10, I may have to go back to banging on bongos and grunting.

[IMG]http://3.bp.blogspot.com/-Zdr04WSvW6g/Tyw0twmvWgI/AAAAAAAAAzc/9NPjZe9Q7vA/s1600/Screenshot1.png[/IMG]

---

### Post by jejeman on 2012-02-03
Why are you root man? Are you even in the audio group?

---

### Post by nazaroo2 on 2012-02-03
> **jejeman said:**
> Why are you root man? Are you even in the audio group?

What is an "audio group"? 

I've always run root, because I can't stand not having access to my own files,
and having to fuss and fiddle with security crap I have never needed and never will.
I just spent a day and a half installing this 11.10 crap, and it sure is,
but I did this (and lost Firefox bookmarks, fonts, games, hundreds of programs, 
just to have 24/96 digital sampling. 
If this "thing", they call the new Ubuntu can't even do that,
then I'm going back to Ubuntu 10 forever, and cursing the idiots who wrecked this distro.

---

### Post by jejeman on 2012-02-03
> Am I using Alsa, or Pulse? and which should I be using?You are always using alsa, and you are using pulse if you didn't shut it down.

You have to many questions and threads. You need to slow down. You've reinstalled 3 systems so far, and no one knows what you are doing, what have you done etc.

If you don't use ubuntu studio you need to do this steps to make rt priority work
[https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time_Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time_Support)

If you are root, maybe you don't, I don't know. It is totally unnessesary to be root.
Everything can be set as you want to use it as a regular user.

---

### Post by nazaroo2 on 2012-02-04
> . It is totally unnessesary to be root.
Everything can be set as you want to use it as a regular user. 	

Sure.  But maybe I don't want to waste time setting up all these accounts, when I'm only one person, and my time is precious.

Put another way, the ONLY necessary thing is Root.
Everything else is a dinosaur holdover from the Germans,
 who were thinking of controlling the world in the 1980s through UNIX. 
The only thing all these layers of B.S. and security are good for, 
is to prevent this:
[COLOR=Blue]
c:\ FORMAT C: 
? Are you sure you want to format C:?  All files and data will be lost. (Y/N) ?
Y
About to format C:.  Press ^C to ABORT NOW, and back up files: (Y/N) ? 
Y
.....formating C:...
[/COLOR]

Its natural for different people to have different philosophies.
Mine center around my own productivity.

> You need to slow down.

See line two above.
I've already calculated that I have about 5,000 useful hours of productivity left, before I die.
I don't want hundreds wasted, waiting around.

> You have to many questions and threads. 

This is a forum where people can connect with others who might have answers.
How can there be two many questions?
Its expected that a person might not know the answer in one sub-forum,
but someone else in another who doesn't read the first sub-forum might know it.
If I can't get an answer from one group, why not ask another group of people?

**BOTTOM LINE:**

There should be a simple set of instructions to get this Xonar card working in EITHER Ubuntu 10 or 11.
I should be able to go over this list, check off the things I have done, or have working, 
and figure out exactly what I need to do next to have the card working. 
It should in fact be a 'sticky', so that others can just look at it and do it.
Where are the steps, or what have I left off?

_**DONE:**_
(1) Disabled onboard sound. 
(2) Installed Ubuntu 11.
(3) created ROOT account.
(4) restored Firefox bookmarks.
(5) Installed JACK, Patchage, Ardour, 
(6) tested and found OUTPUT works, but not INPUT on Xonar card.
(7) ... ?

---

### Post by sgx on 2012-02-04
> **nazaroo2 said:**
> I tried typing in Xonar DG, but it seemed to make no difference. 

What is plughw:0?  

If I don't need a 'mixer' like alsa-mixer, then what exactly do I need to get JACK to use the new soundcard?

Is "Digital" the output or the input section of the soundcard?

Some soundcards have a hardware mixer interface, some don't, but
software mixers still are used to adjust volume.

Linux coders don't get much help from soundcard manufacturers, so we piece things together. The items in the brackets are the labels the linux kernel or modules extracts in the hardware detection process.
You can try them as I mentioned.

hw0:   is like  saying 'car', while  Xonar DG is like saying
Porsche Carerra   both work, but one is more descriptive. When the
name is used, the system will find it consistently. Removable
usb and firewire interfaces benefit more from this.

Digital in the brackets may refer to the optical S/PDIF output, which you could check if you have a device with S/PDIF inputs, to connect with. There is a header for digital hdmi output on the board, not its back panel, and a header to connect a front panel headphone jack, as found in some computer cases.

Cheers

---

### Post by sgx on 2012-02-04
[http://www.remix-os.org/](http://www.remix-os.org/)

this is a linux for audio production, a new version last month,
so maybe a newer alsa. You can burn the iso to a dvd, and reboot
using the computer early-boot menu. Ifthings work, you can then
install. External usb drives can be used, cases for them are about
$25 usd, at/ata/sata drives can be had from old second-hand computers recycled or donated to Goodwill stores. iMicro is a good brand.

Cheers

---

### Post by jejeman on 2012-02-04
> **nazaroo2 said:**
> (6) tested and found OUTPUT works, but not INPUT on Xonar card.Give us a screenshot of alsamixer for capture faders. Alsamixer from terminal. Expand the window so they all fit.

---

### Post by nazaroo2 on 2012-02-04
> **sgx said:**
> [http://www.remix-os.org/](http://www.remix-os.org/)

this is a linux for audio production, a new version last month,
so maybe a newer alsa. You can burn the iso to a dvd, and reboot
using the computer early-boot menu. Ifthings work, you can then
install. External usb drives can be used, cases for them are about
$25 usd, at/ata/sata drives can be had from old second-hand computers recycled or donated to Goodwill stores. iMicro is a good brand.

Cheers

Went to the direct download, and got a page of Russian.
The page tried to open a popup and/or install some malware...
I gave up on that.
I don't want to install Torrent just to get an ISO image. 
There should be a simple download page.  One potential client moves on.

---

### Post by nazaroo2 on 2012-02-04
> **jejeman said:**
> Give us a screenshot of alsamixer for capture faders. Alsamixer from terminal. Expand the window so they all fit.
[IMG]http://1.bp.blogspot.com/-i87GG4atvLI/Ty3AKIvbIbI/AAAAAAAAAzk/bMBW6h7PJ_U/s640/Screenshot002.png[/IMG]

This appears to be all the sliders that exist on this screen anyway.
For all I know there are more screens and more sliders somewhere, 
but I can't INTUITIVELY GUESS what the programmer wants me to do

---

### Post by jejeman on 2012-02-04
I said capture faders that is on F4. Everything is written on screen.
But anyway, when you turn up this "Analog input monitor" do you here input sound? This should be regardles of jack, pulse.

---

### Post by nazaroo2 on 2012-02-04
> **jejeman said:**
> I said capture faders that is on F4. Everything is written on screen.
But anyway, when you turn up this "Analog input monitor" do you here input sound? This should be regardles of jack, pulse.

I've only just discovered (no thanks to whoever laid alsamixer out)
that there are more sliders and pages, which don't show up normally.
Here is how my screen now looks.

[IMG]http://4.bp.blogspot.com/-fIOaDm_e_LM/Ty3L08WW5kI/AAAAAAAAAzs/WHDeFVl8jm8/s640/Screenshot003.png[/IMG]



I can now see a LINE (in / capture ) as the 3rd column.
I have the volume up on this slider (many of the other sliders don't function with up/dn arrows).

I then immediately tried to see if input to the card was getting into JACK.

(1) I shut down all the JACK stuff (patchage, ardour, etc.).
(2) I reran JACK checking and selecting hw:0 (Xonar card) for Input and output.
(3) JACK seems to start more or less without errors.
(4) Ardour and the meters can be hooked up to the System Input in Patchage.
(5) Unfortunately, nothing is showing up at the System Input to record.

I have a CD player playing constantly sending a signal to the physical Inputs of the card,
in case it turns on.  

No sound seems to be coming through, whether or not JACK is running.
I can hear sound directly from the CD player through its own headphone jack, so I know it is really playing to its own output.

I have not physically found and/or connected the leads from the front of the desktop box (front mic/phones) to the internal secondary connectors on the Xonar card.
I thought it would be simpler to just use the outputs at the back.

---

### Post by nazaroo2 on 2012-02-04
Having rebooted in Ubuntu 11.10, I find that the Xonar soundcard functions as an Output device.

(1)  Youtube Flash in Firefox plays sound over the card. 

(2)  Ardour under JACK plays sound into the card.  

(3)  plugging in the RPx400 shows up, at least the MIDI ports over the USB.

(4)  the system recognizes the RPx400, and its an option in JACK Configure.

(5)  Selecting the RPx400 (already assigned hw:1) as input gives no results however. 

Formerly, (in Ubuntu 10) the RPx400 produced sound. 

Again this seems to indicate something is wrong with Ubuntu 11.10, not the xonar card, or the RPx400.

aplay -l in a terminal gives:

 ```
~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DG [Xonar DG], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 #
```arecord -l gives:

```
  # arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 :~# 
```

---

### Post by sgx on 2012-02-04
RPx400

USB Audio #1

try each of those in the qackctl     Input Device  >

the command    ps ux
will show running processes. If anything with  pulse  in
its name is running, use

killall pulseaudio

the restart qjackctl, and test again

Cheers

---

### Post by sgx on 2012-02-05
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

this lists the steps to update the alsa drivers,
which may help, if they are newer than what you have.

edit  if there is a newer alsa-firmware package in synaptic,
that should also be installed, just in case

---

### Post by sgx on 2012-02-05
@audi0          -       rtprio           99
@audio          -       nice             -19
@audio          -       memlock          unlimited
# End of file

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

scroll down to the Real-time Support, Alsa, and Pulseaudio sections

In realtime is a mention of establishing your 'user' in the
audio group, by using yoursystem administration utility.

The nice and memlock entries can be added by hand. The three
column spacing is probably required.

---

### Post by sgx on 2012-02-05
someone else with this sound card posted their lsmod output,
part of which:

snd_oxygen          16214  3
snd_oxygen_lib      30589  1   snd_oxygen
snd_pcm             74368  5   snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_oxygen_lib
snd_timer           19544  2   snd_pcm
snd_page_alloc      7121   2   snd_hda_intel,snd_pcm
snd_mpu401_uart     6011   1   snd_oxygen_lib
snd_rawmidi         19458  1   snd_mpu401_uart
snd_seq_device      5300   1   snd_rawmidi
snd                 58362  17  snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_oxygen,snd_oxygen_lib,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device


it looks as if you'll need snd_oxygen, a kernel module for your card.
If your kernel has that, the way to activate it would be the commands

modprobe snd_oxygen

modprobe snd_oxygen_lib

No response after the command means success. Re-run  lsmod  to check.

If an error occurs saying only root can do that, then

sudo modprobe snd_oxygen    a failed attempt perhaps looking a bit
like this:

bash-4.1$ modprobe snd_oxygen  (enter)
FATAL: Error inserting snd_oxygen (/lib/modules/2.6.38.8-YourKernel/kernel/sound/pci/oxygen/snd-oxygen.ko.gz): Operation not permitted

Repeat the command with sudo

---

### Post by nazaroo2 on 2012-02-05
Okay, I just tried this.  Here is the result:

```
 # modprobe snd_oxygen
 # modprobe snd_oxygen_lib

```Looks like this wasn't installed, and it went in ok without errors [?].
(I'm still ROOT thank God.)

Quick question:  Do I have to do this everytime I boot up, or just once?

Should I assume the card should be working now? 


Here is the output from lsmod:
```


 # lsmod
Module                  Size  Used by
snd_seq_dummy          12686  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
vesafb                 13489  1 
binfmt_misc            17292  1 
nvidia              10390874  42 
snd_usb_audio         100930  0 
snd_hwdep              13276  1 snd_usb_audio
snd_usbmidi_lib        24558  1 snd_usb_audio
ppdev                  12849  0 
joydev                 17393  0 
dcdbas                 14098  0 
snd_oxygen             20034  3 
snd_oxygen_lib         39903  1 snd_oxygen
snd_pcm                80435  4 snd_usb_audio,snd_oxygen_lib
snd_page_alloc         14108  1 snd_pcm
snd_mpu401_uart        13865  1 snd_oxygen_lib
snd_seq_midi           13132  0 
snd_rawmidi            25241  3 snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  9 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63474  0 
serio_raw              12990  0 
snd                    55902  17 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_oxygen,snd_oxygen_lib,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
parport_pc             32114  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  4 
libahci                25761  1 ahci
tg3                   132972  0 
 :~# 

```I don't know what I'm looking at here, so any explanation would be appreciated.

---

### Post by nazaroo2 on 2012-02-05
> **sgx said:**
> RPx400

USB Audio #1

try each of those in the qackctl     Input Device  >

the command    ps ux
will show running processes. If anything with  pulse  in
its name is running, use

killall pulseaudio

the restart qjackctl, and test again

Cheers

Okay I just tried this too:

```
# ps ux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3308  1844 ?        Ss   Feb04   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Feb04   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Feb04   0:00 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    Feb04   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    Feb04   0:00 [migration/1]
root         9  0.0  0.0      0     0 ?        S    Feb04   0:00 [ksoftirqd/1]
root        11  0.0  0.0      0     0 ?        S<   Feb04   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S<   Feb04   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S<   Feb04   0:00 [netns]
root        15  0.0  0.0      0     0 ?        S    Feb04   0:00 [sync_supers]
root        16  0.0  0.0      0     0 ?        S    Feb04   0:00 [bdi-default]
root        17  0.0  0.0      0     0 ?        S<   Feb04   0:00 [kintegrityd]
root        18  0.0  0.0      0     0 ?        S<   Feb04   0:00 [kblockd]
root        19  0.0  0.0      0     0 ?        S<   Feb04   0:00 [ata_sff]
root        20  0.0  0.0      0     0 ?        S    Feb04   0:00 [khubd]
root        21  0.0  0.0      0     0 ?        S<   Feb04   0:00 [md]
root        23  0.0  0.0      0     0 ?        S    Feb04   0:00 [khungtaskd]
root        24  0.0  0.0      0     0 ?        S    Feb04   0:00 [kswapd0]
root        25  0.0  0.0      0     0 ?        SN   Feb04   0:00 [ksmd]
root        26  0.0  0.0      0     0 ?        SN   Feb04   0:00 [khugepaged]
root        27  0.0  0.0      0     0 ?        S    Feb04   0:00 [fsnotify_mark]
root        28  0.0  0.0      0     0 ?        S    Feb04   0:00 [ecryptfs-kthr]
root        29  0.0  0.0      0     0 ?        S<   Feb04   0:00 [crypto]
root        37  0.0  0.0      0     0 ?        S<   Feb04   0:00 [kthrotld]
root        38  0.0  0.0      0     0 ?        S    Feb04   0:00 [scsi_eh_0]
root        39  0.0  0.0      0     0 ?        S    Feb04   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S    Feb04   0:00 [kworker/u:2]
root       183  0.0  0.0      0     0 ?        S    Feb04   0:00 [scsi_eh_2]
root       184  0.0  0.0      0     0 ?        S    Feb04   0:00 [scsi_eh_3]
root       185  0.0  0.0      0     0 ?        S    Feb04   0:00 [scsi_eh_4]
root       187  0.0  0.0      0     0 ?        S    Feb04   0:00 [scsi_eh_5]
root       189  0.0  0.0      0     0 ?        S    Feb04   0:00 [kworker/u:4]
root       232  0.0  0.0      0     0 ?        S    Feb04   0:00 [jbd2/sdb6-8]
root       233  0.0  0.0      0     0 ?        S<   Feb04   0:00 [ext4-dio-unwr]
root       287  0.0  0.0   2648   608 ?        S    Feb04   0:00 upstart-udev-br
root       291  0.0  0.0   3100  1476 ?        Ss   Feb04   0:00 udevd --daemon
root       512  0.0  0.0      0     0 ?        S<   Feb04   0:00 [kpsmoused]
root       599  0.0  0.0   2652   356 ?        S    Feb04   0:00 upstart-socket-
root       766  0.0  0.0   6864  2800 ?        S    Feb04   0:00 /usr/sbin/modem
root       768  0.0  0.1  26856  4728 ?        Ssl  Feb04   0:00 NetworkManager
root       778  0.0  0.0  24420  3656 ?        Sl   Feb04   0:00 /usr/lib/policy
root       825  0.0  0.0   1968   548 tty4     Ss+  Feb04   0:00 /sbin/getty -8
root       834  0.0  0.0   1968   556 tty5     Ss+  Feb04   0:00 /sbin/getty -8
root       840  0.0  0.0   1968   556 tty2     Ss+  Feb04   0:00 /sbin/getty -8
root       841  0.0  0.0   1968   556 tty3     Ss+  Feb04   0:00 /sbin/getty -8
root       843  0.0  0.0   1968   556 tty6     Ss+  Feb04   0:00 /sbin/getty -8
root       851  0.0  0.0   1984   704 ?        Ss   Feb04   0:00 acpid -c /etc/a
root       855  0.0  0.0   3420   620 ?        Ss   Feb04   0:04 /usr/sbin/irqba
root       856  0.0  0.0   2428   900 ?        Ss   Feb04   0:00 cron
root       879  0.0  0.0  41160  3824 ?        Ssl  Feb04   0:00 lightdm
root       882  0.0  0.0   7304  2908 ?        Ss   Feb04   0:00 /usr/sbin/cupsd
root       911  0.0  0.0   4496  1552 ?        Ss   Feb04   0:00 /usr/sbin/bluet
root       918  0.0  0.0      0     0 ?        S<   Feb04   0:00 [l2cap]
root       923  0.0  0.0      0     0 ?        S<   Feb04   0:00 [krfcommd]
root       937  1.1  1.1  62524 45916 tty7     Ss+  Feb04   5:48 /usr/bin/X :0 -
root      1006  0.0  0.0      0     0 ?        S    Feb04   0:00 [flush-8:16]
root      1007  0.0  0.0   2736  1224 ?        S    Feb04   0:00 /sbin/dhclient
root      1049  0.0  0.0   1968   548 tty1     Ss+  Feb04   0:00 /sbin/getty -8
root      1105  0.0  0.0  15768  3400 ?        Sl   Feb04   0:00 /usr/lib/accoun
root      1112  0.0  0.0  27812  3316 ?        Sl   Feb04   0:00 /usr/sbin/conso
root      1217  0.0  0.0  26968  3684 ?        Sl   Feb04   0:00 /usr/lib/upower
root      1356  0.0  0.0  41232  3548 ?        Sl   Feb04   0:00 /usr/bin/gnome-
root      1365  0.0  0.2  49784  8548 ?        Ssl  Feb04   0:00 /usr/bin/gnome-
root      1406  0.0  0.0   3856   180 ?        Ss   Feb04   0:00 /usr/bin/ssh-ag
root      1409  0.0  0.0   3748   488 ?        S    Feb04   0:00 /usr/bin/dbus-l
root      1411  0.0  0.0   6532  3020 ?        Ss   Feb04   0:13 //bin/dbus-daem
root      1413  0.0  0.0  10372  2380 ?        S    Feb04   0:00 /usr/lib/gvfs/g
root      1417  0.0  0.0  31588  2304 ?        Ssl  Feb04   0:00 /usr/lib/gvfs//
root      1431  0.0  0.3 133416 14316 ?        Sl   Feb04   0:04 /usr/lib/gnome-
root      1438  0.0  0.0  10636  2948 ?        S    Feb04   0:00 /usr/lib/libgco
root      1440  0.0  0.0  47464  3880 ?        Sl   Feb04   0:00 /usr/lib/gnome-
root      1442  1.4  3.4 248416 139104 ?       Sl   Feb04   7:30 compiz
root      1444  0.0  0.1  39896  8016 ?        Sl   Feb04   0:00 /usr/bin/gnome-
root      1451  0.0  0.0  31232  2408 ?        Sl   Feb04   0:00 /usr/lib/d-conf
root      1456  0.0  0.0   9428  1984 ?        S    Feb04   0:00 /usr/lib/gvfs/g
root      1457  0.0  0.5 112740 21656 ?        Sl   Feb04   0:04 nautilus -n
root      1458  0.0  0.1  46636  7368 ?        Sl   Feb04   0:00 /usr/lib/gnome-
root      1460  0.0  0.1  29644  6276 ?        Sl   Feb04   0:00 /usr/lib/policy
root      1463  0.0  0.2  92720 11572 ?        Sl   Feb04   0:00 nm-applet
root      1465  0.0  0.2  71068  9612 ?        Sl   Feb04   0:00 bluetooth-apple
root      1471  0.0  0.0  28700  3780 ?        S    Feb04   0:00 /usr/lib/gvfs/g
root      1476  0.0  0.0  23064  3652 ?        Sl   Feb04   0:01 /usr/lib/udisks
root      1477  0.0  0.0   6320   732 ?        S    Feb04   0:02 udisks-daemon: 
root      1483  0.0  0.3  58540 12988 ?        Sl   Feb04   0:00 /usr/lib/notify
root      1492  0.0  0.0  20540  2244 ?        Sl   Feb04   0:01 /usr/lib/gvfs/g
root      1495  0.0  0.0  10456  2184 ?        S    Feb04   0:00 /usr/lib/gvfs/g
root      1497  0.0  0.0  11024  3264 ?        S    Feb04   0:00 /usr/lib/gvfs/g
root      1501  0.0  0.0  10404  2516 ?        S    Feb04   0:00 /usr/lib/gvfs/g
root      1511  0.0  0.0   2040   512 ?        Ss   Feb04   0:00 /bin/sh -c /usr
root      1512  0.0  0.2  24492 10012 ?        S    Feb04   0:03 /usr/bin/unity-
root      1515  0.0  0.2  47816  9628 ?        Sl   Feb04   0:01 /usr/lib/bamf/b
root      1526  0.0  0.6  98540 27932 ?        Sl   Feb04   0:14 /usr/lib/unity/
root      1533  0.0  0.1  62256  6280 ?        Sl   Feb04   0:00 /usr/lib/indica
root      1537  0.0  0.1  64880  5464 ?        Sl   Feb04   0:00 /usr/lib/indica
root      1538  0.0  0.1  49700  4132 ?        Sl   Feb04   0:00 /usr/lib/indica
root      1539  0.0  0.1  71376  5116 ?        Sl   Feb04   0:00 /usr/lib/indica
root      1541  0.0  0.1 133556  6044 ?        Sl   Feb04   0:00 /usr/lib/indica
root      1567  0.0  0.0   7732  2340 ?        S    Feb04   0:00 /usr/lib/geoclu
root      1570  0.0  0.0  26492  3512 ?        Sl   Feb04   0:00 telepathy-indic
root      1572  0.0  0.0   9116  3080 ?        S    Feb04   0:00 /usr/lib/telepa
root      1577  0.0  0.1  23744  7740 ?        S    Feb04   0:00 /usr/lib/gnome-
root      1580  0.0  0.1  51096  5096 ?        Sl   Feb04   0:00 zeitgeist-datah
root      1586  0.0  0.3  35328 14472 ?        Sl   Feb04   0:00 /usr/bin/python
root      1587  0.0  0.0   5504   508 ?        S    Feb04   0:00 /bin/cat
root      1597  0.0  0.4  39700 17288 ?        S    Feb04   0:00 /usr/bin/python
root      1609  0.0  0.1  60520  6848 ?        Sl   Feb04   0:00 /usr/lib/unity-
root      1612  0.0  0.1  53844  4148 ?        Sl   Feb04   0:00 /usr/lib/unity-
root      1613  0.0  0.1  53428  4304 ?        Sl   Feb04   0:00 /usr/lib/unity-
root      1648  0.0  0.0  52208  2888 ?        Sl   Feb04   0:00 /usr/lib/unity-
root      1672  0.0  0.0  33400  3400 ?        Sl   Feb04   0:00 /usr/lib/deja-d
root      1693  0.0  2.2 107076 90768 ?        SLsl Feb04   0:10 /usr/bin/jackdb
root      1748  0.0  0.0      0     0 ?        S    Feb04   0:00 [jbd2/sda1-8]
root      1749  0.0  0.0      0     0 ?        S<   Feb04   0:00 [ext4-dio-unwr]
root      1755  0.0  0.0      0     0 ?        S    Feb04   0:00 [jbd2/sdb1-8]
root      1756  0.0  0.0      0     0 ?        S<   Feb04   0:00 [ext4-dio-unwr]
root      1994  0.0  0.0  39308  3924 ?        Sl   Feb04   0:00 /usr/lib/gvfs/g
root      2018  0.0  0.0   3096   820 ?        S    Feb04   0:00 udevd --daemon
root      2019  0.0  0.0   3096   820 ?        S    Feb04   0:00 udevd --daemon
root      2349  3.7  4.1 461648 167948 ?       Sl   04:08   1:23 /usr/lib/firefo
root      2451  0.0  0.4  38216 19156 ?        S    04:14   0:00 /usr/bin/python
root      2520  0.0  0.0      0     0 ?        S    04:17   0:00 [kworker/1:2]
root      2536  0.0  0.0   2040   512 ?        S    04:18   0:00 /bin/sh /usr/bi
root      2542  0.0  0.0   9804  1776 ?        S    04:18   0:00 /usr/bin/pasusp
root      2543  0.5  2.7 208744 112708 ?       SLl  04:18   0:08 /usr/lib/qjackc
root      2570  0.8  2.6 161548 105560 ?       SLl  04:19   0:13 /usr/bin/patcha
root      2579  0.0  0.0   6616  1392 ?        S    04:20   0:00 bash /usr/bin/b
root      2585  6.3  4.0 352764 163504 ?       SLl  04:20   1:36 banshee /usr/li
root      2642  0.0  0.0      0     0 ?        S    04:20   0:00 [kworker/0:1]
root      2658  0.0  0.0      0     0 ?        S    04:35   0:00 [kworker/0:0]
root      2667  0.2  0.3  77296 14404 ?        Rl   04:37   0:00 gnome-terminal
root      2672  0.0  0.0   2212   720 ?        S    04:37   0:00 gnome-pty-helpe
root      2673  0.0  0.0   6984  1860 pts/0    Ss   04:37   0:00 bash
root      2688  0.0  0.0      0     0 ?        S    04:39   0:00 [kworker/1:1]
root      2693  0.0  0.0      0     0 ?        R    04:40   0:00 [kworker/0:2]
root      2697  0.0  0.0   6232  1128 pts/0    R+   04:45   0:00 ps ux
root@ben-OptiPlex-330:~# 

```I don't see anything with pulse in it... but then my eyes are getting bleary now.
What am I looking at again?

Just to clarify and satisfy my need for tidiness,
 is** JACK** the same as ** qjackctl, **or are they separate programs?

---

### Post by jejeman on 2012-02-05
> is JACK the same as qjackctl, or are they separate programs? They are separate programs. Qjakctl is gui fornt end for jack server. You don't need Qjacktl to run jack. You can run it directly from terminal.

This is one big messy thread.

For now maybe is best for you to turn off pulseaudio.
Open /etc/pulse/client.conf and change this line
; autospawn = yes
to
; autospawn = no
and then kill it with
```
pulseaudio --kill
```After that try to set jack.

---

### Post by nazaroo2 on 2012-02-05
> **jejeman said:**
> They are separate programs. Qjakctl is gui fornt end for jack server. You don't need Qjacktl to run jack. You can run it directly from terminal.

This is one big messy thread.

For now maybe is best for you to turn off pulseaudio.
Open /etc/pulse/client.conf and change this line
; autospawn = yes
to
; autospawn = no
and then kill it with
```
pulseaudio --kill
```After that try to set jack.

Okay I successfully edited the file (in ROOT, in case there's separate versions in every user[!])

I executed your line in the terminal:

```
~# pulseaudio --kill
E: [pulseaudio] main.c: Failed to kill daemon: No such process
 ~# 
```Actually, I just noticed I'm still getting a minor bootup error with JACK in its msg box:

```
 [COLOR=#999999]05:13:05.811 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]05:13:05.877 Statistics reset.[/COLOR]
 [COLOR=#cccc99]05:13:05.937 ALSA connection change.[/COLOR]
 [COLOR=#999999]05:13:06.303 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = [COLOR=Red]**No such file or directory**[/COLOR]
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]05:13:06.312 ALSA connection graph change.[/COLOR]

```Do I need to create some folders for JACK to work?

---

### Post by jejeman on 2012-02-05
> Do I need to create some folders for JACK to work?I don't know. I was never root. You are on your own on that.

---

### Post by nazaroo2 on 2012-02-05
I tried using Multichannel  /  hw:0,0  in JACK SETUP for input, no sound on input.

I went back to "Xonar DG" for Input, no sound still. 

The bootup msg for JACK is as follows, which 'seems legit'...

```
   [COLOR=#999999]Sun Feb  5 05:23:08 2012: Starting jack server...[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: JACK server starting in realtime mode with priority 10[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: control device hw:0[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: control device hw:0[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012:[COLOR=Black]** Acquired audio card**[/COLOR] Audio0[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: [COLOR=Black]**creating alsa driver **[/COLOR]... hw:0|hw:0|1024|2|44100|2|0|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: control device hw:0[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: **configuring for 44100Hz**, period = 1024 frames (23.2 ms), buffer = 2 periods[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: ALSA: final selected sample format for capture: 32bit integer little-endian[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: ALSA: use 2 periods for capture[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: ALSA: final selected sample format for playback: 32bit integer little-endian[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: ALSA: use 2 periods for playback[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: graph reorder: new port 'system:capture_1'[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: New client 'system' with PID 0[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: graph reorder: new port 'system:capture_2'[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: graph reorder: new port 'system:playback_1'[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: graph reorder: new port 'system:playback_2'[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: graph reorder: new port 'system:playback_3'[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: graph reorder: new port 'system:playback_4'[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: graph reorder: new port 'system:playback_5'[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:08 2012: graph reorder: new port 'system:playback_6'[/COLOR]
 [COLOR=#9999cc]05:23:11.046 JACK connection change.[/COLOR]
 [COLOR=#999933]05:23:11.047 Server configuration saved to "/root/.jackdrc".[/COLOR]
 [COLOR=#999999]05:23:11.048 Statistics reset.[/COLOR]
 [COLOR=#999999]05:23:11.058 Client activated.[/COLOR]
 [COLOR=#cc9966]05:23:11.089 JACK connection graph change.[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:23:11 2012: New client 'qjackctl' with PID 1807[/COLOR]
 [COLOR=#66cc99]05:24:06.515 ALSA connection graph change.[/COLOR]
 [COLOR=#cc9966]05:24:09.241 JACK connection graph change.[/COLOR]
 [COLOR=#66cc99]05:24:09.279 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:24:09 2012: New client 'Patchage' with PID 1923[/COLOR]
 [COLOR=#cc9966]05:24:13.514 JACK connection graph change.[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:24:13 2012: [COLOR=Black]**Connecting 'system:capture_1' to 'system:playback_1'**[/COLOR][/COLOR]
 [COLOR=#cc9966]05:24:17.531 JACK connection graph change.[/COLOR]
 [COLOR=#999999]Sun Feb  5 05:24:17 2012: **Connecting 'system:capture_2' to 'system:playback_2'**[/COLOR]

```Thats me at the end, connecting the Input to Output in Patchage, with a CD player pouring into the card.
Still no sound...

---

### Post by nazaroo2 on 2012-02-05
> **sgx said:**
> someone else with this sound card posted their lsmod output,
part of which:

snd_oxygen          16214  3
snd_oxygen_lib      30589  1   snd_oxygen
snd_pcm             74368  5   snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_oxygen_lib
snd_timer           19544  2   snd_pcm
snd_page_alloc      7121   2   snd_hda_intel,snd_pcm
snd_mpu401_uart     6011   1   snd_oxygen_lib
snd_rawmidi         19458  1   snd_mpu401_uart
snd_seq_device      5300   1   snd_rawmidi
snd                 58362  17  snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_oxygen,snd_oxygen_lib,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device


it looks as if you'll need snd_oxygen, a kernel module for your card.
If your kernel has that, the way to activate it would be the commands

modprobe snd_oxygen

modprobe snd_oxygen_lib

No response after the command means success. Re-run  lsmod  to check.
  

I just tried this on the Ubuntu 10. install (dual boot with grub). worked with no errors,
and here is the result of lsmod:

BEFORE running modprobe:

```
~# lsmod
Module                  Size  Used by
dm_crypt               11331  0 
snd_hda_codec_analog    59467  1 
snd_hda_intel          20959  0 
snd_hda_codec          87096  2 snd_hda_codec_analog,snd_hda_intel
snd_pcm_oss            34603  0 
snd_mixer_oss          13961  1 snd_pcm_oss
snd_usb_audio          84223  0 
snd_seq_dummy           1498  0 
snd_hwdep               5668  2 snd_hda_codec,snd_usb_audio
snd_pcm                71934  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_usb_audio
snd_usbmidi_lib        16369  1 snd_usb_audio
snd_seq_oss            27658  0 
snd_seq_midi            4621  0 
binfmt_misc             6587  1 
snd_rawmidi            19141  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                48106  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18710  2 snd_pcm,snd_seq
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
snd                    56719  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_seq_dummy,snd_hwdep,snd_pcm,snd_usbmidi_lib,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             26250  1 
nvidia               9962496  46 
soundcore               6620  1 snd
snd_page_alloc          7236  2 snd_hda_intel,snd_pcm
joydev                  8740  0 
dell_wmi                1793  0 
dcdbas                  5490  0 
psmouse                63677  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36206  0 
hid                    67288  1 usbhid
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
intel_agp              24671  0 
ahci                   32712  2 
tg3                   109580  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
agpgart                31788  2 nvidia,intel_agp


```


AFTER running modprobe:

```





 # modprobe snd_oxygen
 # modprobe snd_oxygen_lib
 # lsmod

Module                  Size  Used by
[B]snd_oxygen              6193  0 
snd_oxygen_lib         29378  1 snd_oxygen
snd_mpu401_uart         5905  1 snd_oxygen_lib[/B]
dm_crypt               11331  0 
snd_hda_codec_analog    59467  1 
snd_hda_intel          20959  0 
snd_hda_codec          87096  2 snd_hda_codec_analog,snd_hda_intel
snd_pcm_oss            34603  0 
snd_mixer_oss          13961  1 snd_pcm_oss
snd_usb_audio          84223  0 
snd_seq_dummy           1498  0 
snd_hwdep               5668  2 snd_hda_codec,snd_usb_audio
snd_pcm                71934  5 snd_oxygen_lib,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_usb_audio
snd_usbmidi_lib        16369  1 snd_usb_audio
snd_seq_oss            27658  0 
snd_seq_midi            4621  0 
binfmt_misc             6587  1 
snd_rawmidi            19141  3 snd_mpu401_uart,snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                48106  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18710  2 snd_pcm,snd_seq
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
snd                    56719  19 [B]snd_oxygen,snd_oxygen_lib,snd_mpu401_uart,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_seq_dummy,snd_hwdep,snd_pcm,snd_usbmidi_lib,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
[/B]parport_pc             26250  1 
nvidia               9962496  46 
soundcore               6620  1 snd
snd_page_alloc          7236  2 snd_hda_intel,snd_pcm
joydev                  8740  0 
dell_wmi                1793  0 
dcdbas                  5490  0 
psmouse                63677  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36206  0 
hid                    67288  1 usbhid
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
intel_agp              24671  0 
ahci                   32712  2 
tg3                   109580  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
agpgart                31788  2 nvidia,intel_agp
root@unknown:~#
```

---

### Post by jejeman on 2012-02-05
If you need to start modules for the sound card, then put them in here /etc/modules they will be started automaticly with the system.

---

### Post by nazaroo2 on 2012-02-05
> **jejeman said:**
> If you need to start modules for the sound card, then put them in here /etc/modules they will be started automaticly with the system.

no such directory **/etc/modules**

could you be a little more detailed in your explanation/instructions?
What are modules?  Are they programs?  Do I have to put their names later in a startup script?
I'm more used to DOS 3.3 on an Apple IIe.

---

### Post by sgx on 2012-02-05
now that new kernel modules are on board,
and see if aplay -l   and arecord -l  
have different names within the brackets,
and use them in qjackctl.  The names cannot be
mixed with hw:0 type identifiers for one device,

but for example, Output Device >  could have a hw:0
while Input Device > had the Xonar DG, or other name
found withinin brackets. 


As to the difference between root (sudo) and
a regular user,

sudo can view and modify the whole system

user can view and modify
1. only /home/username and contents
2. things that sudo grants permission to view and modify

folders like /etc  and /usr/share  have things you will need
to modify, add to, or delete.  sudo is required

/usr/bin  and /usr/lib  are where softwares are installed
sudo is required.

jackd is a system application that the user uses.
So sudo installs it, but the user configures it, and runs it,
from a command line, or from a gui. 

.jackdrc is the text of a command
that is saved by the gui qjackctl, and is found in /home/username

You can copy it to a terminal to start jackd when you want to.

Because sudo is king, all apps can be run bu sudo. For audio,
all apps must be run by just ONE user, it matters little which one,
but if sudo launches jackd or qjackctl, all other audio apps
using jackd in that session must also be started by sudo.

This is sometimes done to diagnose permissions problems
in a users configuration.

Normally, the user starts all apps, except for
system administration tasks.
--------------------------------------------------------------

Looking at your ps ux output, you should do a clean boot,
with all network, bluetooth and communications software
off. Unplug any modem and ethernet if they are connected.

In qjackctl setup, the top-right tab is Misc.
In that tab, untick the option to start jackd automatically,
and quit qjackctl.

For the remainder of testing, start jackd with this command

jackd -d alsa -r 44100   which should have something this near the end of its output:

ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

Then start qjackctl, which will see jackd is running, and be happy,
and you can test the inputs again using what is gathered from
aplay -l  and arecord -l

---

### Post by jejeman on 2012-02-05
/etc/modules is a file not directory. In that file there is explenation how to use it.

Modules are programs, you my now them as drivers for hardware.

---

### Post by fiber3 on 2012-02-10
This might be a bit obvious.. but make sure you have the audio in the correct output.  I installed alsa on Ubuntu 10.04 and it set my output to a different port than it did in 11.10.

---

### Post by nazaroo2 on 2012-02-11
> **fiber3 said:**
> This might be a bit obvious.. but make sure you have the audio in the correct output.  I installed alsa on Ubuntu 10.04 and it set my output to a different port than it did in 11.10.

This is interesting:  how did you find this out, how can I check it, and how did you resolve this problem?

---

### Post by sgx on 2012-02-13
I think he means that when testinging 5.1 or 7.1 surround sound,
to check each and every jack on the card for output, because limited alsa devs don't always get it right. A few companies loan or give them cards to use, some even some basic documentation, not always enough to get everything as perfect as they would like, or as their time allows.
Cheers.

---

### Post by Jripe on 2012-02-24
I'm a little late to this, hopefully you are still watching this thread. The ALSA does not currently support the recording from the Xonar DG, nor does it support the front panel inputs.

---

### Post by sgx on 2012-02-27
Alsa 1.0.25 Xonar fixes from the release notes:

"CMI8788 (Oxygen) driver

    ALSA: virtuoso: Xonar DS: fix polarity of front output 
    ALSA: virtuoso: add S/PDIF input support for all Xonars 
    ALSA: virtuoso: fix Essence ST(X) S/PDIF input 
    ALSA: virtuoso: fix silent analog output on Xonar Essence ST Deluxe 
    ALSA: firewire-speakers, oxygen, ua101: allow > 10 s periods 
    ALSA: oxygen: fix output routing on Xonar DG"

Good that work is being done to improve use of these cards :popcorn:

---

### Post by FulciLives on 2012-03-14
I have an Asus Xonar DG and just installed Ubuntu 12.04 Beta 1

I'm only now finding out that it doesn't support input (which I need).

So does anyone recommend a decent cheap card that works well with Ubuntu? I need to be able to do input at 24-bit 96k

Have to say this card works awesome on Windows (especially the headphone amp).

Such a shame it is so broken under Linux *sigh*

---

### Post by sgx on 2012-03-14
I use an maudio24/96 pci for years, no problems, great sound.
Analog, digital, and midi i/o
kernel module snd_ice1712
mixer envy24control (or mudita version of the same)
Max new price is $99 so look for used or sale prices.
Cheers

---

### Post by FulciLives on 2012-03-15
> **sgx said:**
> I use an maudio24/96 pci for years, no problems, great sound.
Analog, digital, and midi i/o
kernel module snd_ice1712
mixer envy24control (or mudita version of the same)
Max new price is $99 so look for used or sale prices.
Cheers
I guess this is the one you are talking about:
[http://www.m-audio.com/products/en_us/Audiophile2496.html]("http://www.m-audio.com/products/en_us/Audiophile2496.html")

---

### Post by sgx on 2012-03-16
Yes, that's the one! Six years and counting :guitar:

---

