---
title: "first time trying to setup ardour/jack/firepod i'm lost"
date: 2009-11-14
forum: Ubuntu Studio
---

### Post by extendedping on 2009-11-14
first off I have tried to follow various threads but I have been lost. my total understanding of audio/recording is about 10 hours I did learning cubase a few years ago. so...I have ubuntu 9.10 installed and all the ubuntu studio packages minus the wallpaper or desktop. I have the rt-linux kernel running. I have jack installed as well as ubuntu studio controls. I put myself in the audio group. now as a newbie I am totally lost by what is in front of me. I have tried starting jack using all the settings (alsa freebob firewire etc) but it fails giving various messages. the only time it starts is when I check start on application startup and then start ardour. if I then go to qjackctl it appears to be already started regardless of the driver I have specified in the gjackctl setup.  my presonous firepod is a firewire device and I don't even know how to check to see if ubuntu can find it. I did a lspci |less and got..

.06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

so ubuntu has at least detected my pci firewire card right? so in a nutshell, I don't know why jack keeps failing to start, I don't know how to install my firepod and on top of it I don't know how to tell if the firepod has in fact been detected. all I know is there is a red light on. also I do not know what driver and setting I should be specifying in jack in order to try to get this jack working and my device going. I am sorry for the vagueness of this post, but jack, freebob, patchbay alsa etc are all kind of new to me. I feel if I could just get the jack started with the right driver and settings and my firepod known I would be on my way to making music on linux. man I don't want to have to dual boot just to use cubase...help me PLLLEEAASSEE....

---

### Post by Stochastic on 2009-11-14
Firewire soundcards are understandably confusing for a new user, even some advanced users get fed up with it sometimes.

The way Ubuntu comes out of the box is not meant for firewire soundcards to be used.  It has to be tweaked.  There are only a handful of tweaks that need to be done, so troubleshooting is relatively straightforward.

It's good that you've added yourself to the audio group, but you should also add yourself to the video group.  Then you should open Ubuntu Studio controls and make sure that all three options are checked off.  After that, you should reboot.  Then open qjackctl and point the driver to "firewire" (this is the ffado driver), check the 'realtime' option in the settings, and then click start.

If all goes well the red light on the firepod should turn blue and you should see inputs/outputs appear in the connections window of qjackctl.  If this doesn't happen, please post the complete output of the messages window and we can step through the possible causes of the error.

---

### Post by trulan on 2009-11-14
Here's the how-to wiki page I have been working on.  Give it a look, see if it helps.
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

I wouldn't mind feedback on ways to improve it.  Let us know how it goes.

---

### Post by sgx on 2009-11-14
> **trulan said:**
> Here's the how-to wiki page I have been working on.  Give it a look, see if it helps.
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

I wouldn't mind feedback on ways to improve it.  Let us know how it goes.
Just send me your firewire devices for testing, I'll mail them back in 2012, I promise! ;)

---

### Post by extendedping on 2009-11-14
> **Stochastic said:**
> Firewire soundcards are understandably confusing for a new user, even some advanced users get fed up with it sometimes.

The way Ubuntu comes out of the box is not meant for firewire soundcards to be used.  It has to be tweaked.  There are only a handful of tweaks that need to be done, so troubleshooting is relatively straightforward.

It's good that you've added yourself to the audio group, but you should also add yourself to the video group.  Then you should open Ubuntu Studio controls and make sure that all three options are checked off.  After that, you should reboot.  Then open qjackctl and point the driver to "firewire" (this is the ffado driver), check the 'realtime' option in the settings, and then click start.

If all goes well the red light on the firepod should turn blue and you should see inputs/outputs appear in the connections window of qjackctl.  If this doesn't happen, please post the complete output of the messages window and we can step through the possible causes of the error.

holy cow, I don't have a clue what to do next...but the light is blue. based on all the reading I have done I expected this to be an absolute nightmare.

---

### Post by extendedping on 2009-11-14
hmm unfortunately the jack stops after a few minutes and the firewall goes red, then I restart jack and repeat :(

does this help???

22:26:56.422 JACK is starting...
22:26:56.422 /usr/bin/jackd -R -dfirewire -r44100 -p1024 -n3 -i2
22:26:56.425 JACK was started with PID=3255.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
SSE2 detected
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
01828317719:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
22:26:58.499 Server configuration saved to "/home/brad/.jackdrc".
22:26:58.501 Statistics reset.
22:26:58.502 Client activated.
22:26:58.504 JACK connection change.
22:26:58.508 JACK connection graph change.
SSE2 detected
cannot lock down memory for RT thread (Cannot allocate memory)
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
22:27:36.057 JACK connection graph change.
22:27:36.129 JACK connection change.
jack main caught signal 12
no message buffer overruns
22:27:36.455 Shutdown notification.
22:27:36.456 JACK is stopping...
22:27:36.456 JACK is being forced...
cannot continue execution of the processing graph (Broken pipe)
zombified - calling shutdown handler
22:27:36.657 JACK was stopped successfully.
22:27:36.657 Post-shutdown script...
22:27:36.657 killall jackd
jackd: no process found
22:27:37.072 Post-shutdown script terminated with exit status=256.

---

### Post by extendedping on 2009-11-15
> **trulan said:**
> Here's the how-to wiki page I have been working on.  Give it a look, see if it helps.
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

I wouldn't mind feedback on ways to improve it.  Let us know how it goes.

thanks I put the exact parameters from the links in the tutorial regarding jack setup (was easy considering the guy was using a firepod as well) including

driver firewire
realtime checked
priority 70 
frames/period 128
sample rate 44100
period buffers 2
port max 256
timeout (msec) 500
start delay (secs) 2
interface hw:0 ----------- changed from "default"
audio duplex
input channels 8
output  channels 8

and in ubuntu studio enabled all 3 buttons giving raw access, 50% mem (this is a 4gb system) and nice at -15. still get this :( as you can see the blue only last a minute and jack stops...

00:30:35.212 Startup script...
00:30:35.212 artsshell -q terminate
sh: artsshell: not found
00:30:35.616 Startup script terminated with exit status=32512.
00:30:35.616 JACK is starting...
00:30:35.616 /usr/bin/jackd -R -P70 -dfirewire -dhw:0 -r44100 -p128 -n2 -i8 -o8
00:30:35.620 JACK was started with PID=2888.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
00497245408:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
00:30:37.786 Server configuration saved to "/home/brad/.jackdrc".
00:30:37.787 Statistics reset.
00:30:37.789 Client activated.
00:30:37.791 JACK connection change.
00:30:37.800 JACK connection graph change.
SSE2 detected
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
00:31:55.699 JACK connection graph change.
00:31:55.732 JACK connection change.
jack main caught signal 12
no message buffer overruns
00:31:55.998 Shutdown notification.
00:31:55.999 JACK is stopping...
00:31:56.000 JACK is being forced...
cannot continue execution of the processing graph (Broken pipe)
zombified - calling shutdown handler
00:31:56.200 JACK was stopped successfully.
00:31:56.200 Post-shutdown script...
00:31:56.200 killall jackd
jackd: no process found
00:31:56.612 Post-shutdown script terminated with exit status=256.

---

### Post by sgx on 2009-11-15
I'm gonna take a guess that either another sound device, or a modem/networking device/webcam is involed. If you have a motherboard soundchip, try to disable it in the bios, if a card in a closed desktop case , find its module with the command

lsmod, and add it the textfile /etc/modprobe.d/blacklist

mine looks like this:

blacklist snd-usb-audio
blacklist snd_intel8x0
blacklist ath5k
blacklist mac80211

yours will be different, or need to be created first

In my situation, something occasionally blocks items from connecting
to jackd while I'm online, forcing a change in behaviour, and since most linux stuff is beta, and released without much cooperative testing, your previous workflow might also need to change. Its best to start an important audio session after a reboot, with nothing connected that isn't an audio device.

Cheers

and if that does not help, come back again and turn off wireless/networking/power management things in the bios temporarily. Take notes of settings you change if that process is new to you, for good luck

---

### Post by AutoStatic on 2009-11-15
Nice HowTo trulan!
Sounds silly extendedping but did you try starting up your PC with the Firepod switched on? And did you try other sample rates, like 48000 or 96000?

---

### Post by trulan on 2009-11-15
> **extendedping said:**
> 
firewire ERR: wait status < 0! (= -1)
I'm not sure if I've seen that error before but it looks like your problem.

Does the CPU usage indicator in Jack Control come up with a number, or does it not move from zero?  I had issues when I was first setting up my firepod that it would act like this:  The light would turn blue, RT would blink, but Jack would stop before the CPU numbers came up (it died in less than ten seconds).  If that is indeed how yours is acting, increase your frames/period and it should help.

Also, you might want to put a CPU scaler in gnome panel and set it to its highest number - some people have been reporting problems due to sluggish CPU scaling.

---

### Post by extendedping on 2009-11-15
> **sgx said:**
> I'm gonna take a guess that either another sound device, or a modem/networking device/webcam is involed. If you have a motherboard soundchip, try to disable it in the bios, if a card in a closed desktop case , find its module with the command

lsmod, and add it the textfile /etc/modprobe.d/blacklist

mine looks like this:

blacklist snd-usb-audio
blacklist snd_intel8x0
blacklist ath5k
blacklist mac80211

yours will be different, or need to be created first

In my situation, something occasionally blocks items from connecting
to jackd while I'm online, forcing a change in behaviour, and since most linux stuff is beta, and released without much cooperative testing, your previous workflow might also need to change. Its best to start an important audio session after a reboot, with nothing connected that isn't an audio device.

Cheers

and if that does not help, come back again and turn off wireless/networking/power management things in the bios temporarily. Take notes of settings you change if that process is new to you, for good luck

thank you (and everyone else) for your help. to the other poster, yes I did try a reboot with firepod on made no difference. I did watch my cpu in the qjackctl panel and it did not appear to go over 3.2 % when the jack/firepod crashes. I opened up my motherboard and the pci firewire card is the only pci card. I did see in the bios another built in 1394 onboard and I disabled that, I then rebooted with the fp on and it made no difference, crashed in bout 45 seconds :(

so question...since my sound  is on board, if I disable it in the bios that means no sound correct for cd's or youtube? my wife will not like that!!! as for lsmod, I don't know what I a looking for so I will post the entire thing (sorry bout that) also there are a number of files blacklist.xxxx already in /etc/modprobe.d should I be working with one of these? first /etc/modprobe.d then /etc/modprobe.d/blacklist-firewire.conf thenlsmod...

1)
brad@ubuntu:~$ cat /etc/modprobe.d/
alsa-base.conf              blacklist-modem.conf
blacklist-ath_pci.conf      blacklist-oss.conf
blacklist.conf              blacklist-watchdog.conf
blacklist-firewire.conf     libpisock9.conf
blacklist-framebuffer.conf  oss-compat.conf


2)
brad@ubuntu:~$ cat /etc/modprobe.d/blacklist-firewire.conf 
# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2


3)
Module                  Size  Used by
dv1394                 21288  0 
isofs                  36712  1 
udf                    88712  0 
crc_itu_t               2320  1 udf
binfmt_misc            10300  1 
ipt_MASQUERADE          2928  2 
iptable_nat             6672  1 
nf_nat                 23036  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      16424  5 iptable_nat,nf_nat
nf_defrag_ipv4          2192  1 nf_conntrack_ipv4
xt_state                2416  2 
nf_conntrack           82272  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT              3568  4 
xt_tcpudp               3600  8 
bridge                 57008  0 
stp                     3028  1 bridge
kvm_intel              47048  0 
kvm                   186368  1 kvm_intel
snd_hda_codec_idt      73472  1 
snd_hda_intel          31560  2 
snd_hda_codec          88048  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               9560  1 snd_hda_codec
snd_pcm_oss            45024  0 
snd_mixer_oss          19728  1 snd_pcm_oss
snd_pcm                91960  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3540  0 
snd_seq_oss            33920  0 
raw1394                29448  0 
snd_seq_midi            8448  0 
snd_rawmidi            27232  1 snd_seq_midi
snd_seq_midi_event      8656  2 snd_seq_oss,snd_seq_midi
iptable_filter          3856  1 
snd_seq                61664  10 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27000  2 snd_pcm,snd_seq
lp                     12740  0 
snd_seq_device          8484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   8376  0 
ip_tables              21152  2 iptable_nat,iptable_filter
parport_pc             37384  1 
psmouse                57460  0 
parport                41484  3 lp,ppdev,parport_pc
serio_raw               6772  0 
snd                    79496  18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
heci                   65892  0 
soundcore              10080  1 snd
snd_page_alloc         11072  2 snd_hda_intel,snd_pcm
x_tables               26680  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
fbcon                  41952  72 
tileblit                3120  1 fbcon
font                    8816  1 fbcon
bitblit                 6448  1 fbcon
softcursor              2320  1 bitblit
usbhid                 43872  0 
i915                  247336  3 
drm                   195168  3 i915
i2c_algo_bit            7060  1 i915
ohci1394               34500  1 dv1394
ieee1394              102048  3 dv1394,raw1394,ohci1394
e1000e                138752  0 
intel_agp              32816  2 i915
video                  23436  1 i915
output                  3792  1 video
brad@ubuntu:~$ 

finally just to give the experts everything...uname -a, free, cpuinfo

brad@ubuntu:~$ uname -a
Linux ubuntu 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 13:22:24 UTC 2009 x86_64 GNU/Linux

brad@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3887        921       2966          0         35        377
-/+ buffers/cache:        508       3379
Swap:         9703          0       9703

brad@ubuntu:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping	: 6
cpu MHz		: 1596.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 4261.89
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping	: 6
cpu MHz		: 1596.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 4261.69
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

sorry to dump all this in one message I just want to provide as much info for troubleshooting as possible. I will now go disable onboard sound to my wife's dismay...thanks for the help...

---

### Post by extendedping on 2009-11-15
ok I disabled on board sound and now get this upon starting jack which crashes after a few seconds. funny thing is not even without jack running firepod light remains blue...

10:45:13.289 Patchbay deactivated.
10:45:13.363 Statistics reset.
10:45:13.383 Could not open ALSA sequencer as a client. ALSA MIDI patchbay will be not available.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
10:45:26.712 Startup script...
10:45:26.712 artsshell -q terminate
sh: artsshell: not found
10:45:27.115 Startup script terminated with exit status=32512.
10:45:27.115 JACK is starting...
10:45:27.115 /usr/bin/jackd -R -P70 -dfirewire -dhw:0 -r44100 -p128 -n2 -i8 -o8
10:45:27.118 JACK was started with PID=2988.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
01041344855:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 0.
firewire ERR: Could not start streaming threads: -1
DRIVER NT: could not start driver
cannot start driver
no message buffer overruns
10:45:28.840 JACK was stopped successfully.
10:45:28.841 Post-shutdown script...
10:45:28.841 killall jackd
jackd: no process found
10:45:29.167 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
10:45:33.158 Post-shutdown script terminated with exit status=256.

oh and this in the popup window...

Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.

if you thought I was lost before...so frustrating because i really want to cut the windows cord...jack now crashes immediately while firepod remains blue...

---

### Post by AutoStatic on 2009-11-15
You should disable the "ondemand" service which is now scaling your CPU down to 1,59 Ghz while it should run at 2.13 Ghz. You could also, as trulan suggested, install the CPU Frequency Scaling Applet (right click on your Gnome panel and add this applet) and select "Performance".

---

### Post by extendedping on 2009-11-15
> **AutoStatic said:**
> You should disable the "ondemand" service which is now scaling your CPU down to 1,59 Ghz while it should run at 2.13 Ghz. You could also, as trulan suggested, install the CPU Frequency Scaling Applet (right click on your Gnome panel and add this applet) and select "Performance".

thanks did that it did not make a difference still crashing :(

11:57:58.934 Patchbay deactivated.
11:57:59.003 Statistics reset.
11:57:59.106 ALSA connection graph change.
11:57:59.329 ALSA connection change.
11:58:15.094 Startup script...
11:58:15.094 artsshell -q terminate
sh: artsshell: not found
11:58:15.496 Startup script terminated with exit status=32512.
11:58:15.496 JACK is starting...
11:58:15.496 /usr/bin/jackd -R -P70 -dfirewire -dhw:0 -r44100 -p128 -n2 -i8 -o8
11:58:15.499 JACK was started with PID=2922.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
01599041499:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
11:58:17.556 Server configuration saved to "/home/brad/.jackdrc".
11:58:17.557 Statistics reset.
11:58:18.141 Client activated.
11:58:18.142 JACK connection change.
11:58:18.144 JACK connection graph change.
SSE2 detected
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
11:58:20.473 JACK connection graph change.
11:58:20.545 JACK connection change.
jack main caught signal 12
no message buffer overruns
11:58:20.705 Shutdown notification.
11:58:20.706 JACK is stopping...
11:58:20.706 JACK is being forced...
cannot continue execution of the processing graph (Broken pipe)
zombified - calling shutdown handler
11:58:20.906 JACK was stopped successfully.
11:58:20.906 Post-shutdown script...
11:58:20.906 killall jackd
jackd: no process found
11:58:21.342 Post-shutdown script terminated with exit status=256.

---

### Post by sgx on 2009-11-15
Hi, jackd is for audio device connections, independant of the blue firewire light. 

this portion from lsmod

snd_hda_codec_idt 73472 1 
snd_hda_intel 31560 2 
snd_hda_codec 88048 2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep 9560 1 snd_hda_codec
snd_pcm_oss 45024 0 
snd_mixer_oss 19728 1 snd_pcm_oss
snd_pcm 91960 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 3540 0 
snd_seq_oss 33920 0 
raw1394 29448 0 
snd_seq_midi 8448 0 
snd_rawmidi 27232 1 snd_seq_midi
snd_seq_midi_event 8656 2 snd_seq_oss,snd_seq_midi
iptable_filter 3856 1 
snd_seq 61664 10 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 27000 2 snd_pcm,snd_seq
lp 12740 0 
snd_seq_device 8484 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
ppdev 8376 0 
ip_tables 21152 2 iptable_nat,iptable_filter
parport_pc 37384 1 
psmouse 57460 0 
parport 41484 3 lp,ppdev,parport_pc
serio_raw 6772 0 
snd 79496 18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_ hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_os s,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
heci 65892 0 
soundcore 10080 1 snd
snd_page_alloc 11072 2 snd_hda_intel,snd_pcm

is the various audio-related sound modules, each lines lists a module, and what other modules it interracts with, some using more than others.

snd_hda_intel 31560 2  This is probably the onboard soundchip, mine is
blacklisted to avoid conflicts and configuration hassles with my pci soundcard.

If you have both onboard, and pci based firewire, have you tried the firepod in the onboard firewire when the pci card is not installed?
If you can do that, compare the output to the ones you have now. Also,
start the computer with the firepod absent, plug it in, check the output,
then reboot with the device still in, and then compare that output, a notebook is handy at this point. And of course, test audio in each scenario. Cheers

---

### Post by extendedping on 2009-11-15
> **sgx said:**
> Hi, jackd is for audio device connections, independant of the blue firewire light. 

this portion from lsmod

snd_hda_codec_idt 73472 1 
snd_hda_intel 31560 2 
snd_hda_codec 88048 2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep 9560 1 snd_hda_codec
snd_pcm_oss 45024 0 
snd_mixer_oss 19728 1 snd_pcm_oss
snd_pcm 91960 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 3540 0 
snd_seq_oss 33920 0 
raw1394 29448 0 
snd_seq_midi 8448 0 
snd_rawmidi 27232 1 snd_seq_midi
snd_seq_midi_event 8656 2 snd_seq_oss,snd_seq_midi
iptable_filter 3856 1 
snd_seq 61664 10 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 27000 2 snd_pcm,snd_seq
lp 12740 0 
snd_seq_device 8484 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
ppdev 8376 0 
ip_tables 21152 2 iptable_nat,iptable_filter
parport_pc 37384 1 
psmouse 57460 0 
parport 41484 3 lp,ppdev,parport_pc
serio_raw 6772 0 
snd 79496 18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_ hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_os s,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
heci 65892 0 
soundcore 10080 1 snd
snd_page_alloc 11072 2 snd_hda_intel,snd_pcm

is the various audio-related sound modules, each lines lists a module, and what other modules it interracts with, some using more than others.

snd_hda_intel 31560 2  This is probably the onboard soundchip, mine is
blacklisted to avoid conflicts and configuration hassles with my pci soundcard.

If you have both onboard, and pci based firewire, have you tried the firepod in the onboard firewire when the pci card is not installed?
If you can do that, compare the output to the ones you have now. Also,
start the computer with the firepod absent, plug it in, check the output,
then reboot with the device still in, and then compare that output, a notebook is handy at this point. And of course, test audio in each scenario. Cheers

thanks I'll do that tomorrow. beginning to look like the firepod doesn't fly straight with ubuntu :(

if I can't get it working should I be looking for usb or pci? I'd even consider trading the firepod (it works fine on windows with cubase) for a linux card that is known to work if there are any takers...) I just don't want to use window period, especially when from what I have read, there are many good programs to work with/learn once a solid soundcard is in place.

---

### Post by AutoStatic on 2009-11-16
Does the Firepod come with a power adapter? If so, are you using it? May seem a silly question but my Focusrite doesn't work when the adapter is not attached, I even recall JACK spitted out the same error message then (firewire ERR: wait status < 0! (= -1)).

---

### Post by extendedping on 2009-11-16
> **AutoStatic said:**
> Does the Firepod come with a power adapter? If so, are you using it? May seem a silly question but my Focusrite doesn't work when the adapter is not attached, I even recall JACK spitted out the same error message then (firewire ERR: wait status < 0! (= -1)).

yes and I am using it, there are no silly questions (I have used them all up myself)
:}

---

### Post by AutoStatic on 2009-11-16
And did you try both the Via and the TI Firewire cards? What brand is the Texas Instruments Firewire card?

---

### Post by trulan on 2009-11-16
You're describing exactly how my Dell Inspiron e1505 behaves when I try to use it with a firewire express card.  The light will turn blue, but jack crashes, with the light staying blue.  It only works with the built-in Ricoh firewire chip.  Then, when things are working properly, if the system is overloaded and Jack crashes, the light turns red again.

 I have not figured it out yet, except that it doesn't like something about the express card slot.  My express card has the TI chip.  My firepod will not work on the express card under Windows either (That's why I ended up here on Ubuntu - my computer would not play well with the firepod for anything on Windows XP, internal chip or express card.)

Also, mine is picky about which cable I use - I bought a cheap firewire cable off ebay which simply does not work for audio (It runs a video camera just fine so I gave it to somebody else.)

---

### Post by Stochastic on 2009-11-17
extendedping, I have never seen that particular error before "firewire ERR: wait status < 0! (= -1)" so I went to the #ffado IRC channel and asked for more experienced eyes to look at this thread.  One user replied that you should post the output of ```
grep 1394 /var/log/messages
```in order to see messages from the kernel drivers (i.e. the ffado kernel links, me thinks).

Can you post the output of that?

---

### Post by extendedping on 2009-11-17
here is is...

brad@ubuntu:~$ grep 1394 /var/log/messages
Nov 15 08:48:09 ubuntu kernel: [    0.962001] ohci1394 0000:06:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Nov 15 08:48:09 ubuntu kernel: [    1.033099] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[e0004800-e0004fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 15 08:48:09 ubuntu kernel: [    1.040208] ohci1394 0000:06:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 15 08:48:09 ubuntu kernel: [    1.092099] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[e0004000-e00047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 15 08:48:11 ubuntu kernel: [    8.309751] ieee1394: raw1394: /dev/raw1394 device initialized
Nov 15 09:48:55 ubuntu kernel: [    7.794662] ieee1394: raw1394: /dev/raw1394 device initialized
Nov 15 09:55:22 ubuntu kernel: [    0.937092] ohci1394 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 15 09:55:22 ubuntu kernel: [    0.997021] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[e0000000-e00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 15 09:55:25 ubuntu kernel: [    8.108592] ieee1394: raw1394: /dev/raw1394 device initialized
Nov 15 10:28:46 ubuntu kernel: [    0.988024] ohci1394 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 15 10:28:46 ubuntu kernel: [    1.048018] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[e0000000-e00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 15 10:28:46 ubuntu kernel: [    8.553195] ieee1394: raw1394: /dev/raw1394 device initialized
Nov 15 11:01:09 ubuntu kernel: [    0.945964] ohci1394 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 15 11:01:09 ubuntu kernel: [    1.001102] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[e0000000-e00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 15 11:01:09 ubuntu kernel: [    7.320869] ieee1394: raw1394: /dev/raw1394 device initialized
Nov 15 11:31:43 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1394" x-info="http://www.rsyslog.com"] (re)start
Nov 15 11:31:43 ubuntu kernel: [    0.963030] ohci1394 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 15 11:31:43 ubuntu kernel: [    1.019102] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[e0000000-e00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 15 11:31:45 ubuntu kernel: [    8.408224] ieee1394: raw1394: /dev/raw1394 device initialized
Nov 16 10:36:21 ubuntu kernel: [    0.957053] ohci1394 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 16 10:36:21 ubuntu kernel: [    1.019774] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[e0000000-e00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 16 10:36:22 ubuntu kernel: [    7.716864] ieee1394: raw1394: /dev/raw1394 device initialized
Nov 17 08:29:00 ubuntu kernel: [    0.930933] ohci1394 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 17 08:29:00 ubuntu kernel: [    0.986113] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[e0000000-e00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 17 08:29:00 ubuntu kernel: [    7.113942] heci: Intel(R) Management Engine Interface - version 5.0.0.31
Nov 17 08:29:00 ubuntu kernel: [    7.113945] heci: Copyright (c) 2003 - 2008 Intel Corporation.
Nov 17 08:29:00 ubuntu kernel: [    7.575771] ieee1394: raw1394: /dev/raw1394 device initialized

---

### Post by Stefan Richter on 2009-11-17
I was the one who suggested to look for possibly interesting kernel messages in the log file.  There are some expected messages missing which could be a hardware problem (unlikely, since there are two controllers and at least the one which is not connected to the FirePod should show this certain message which is absent from the log file) or simply due to how the system log is configured at Ubuntu.  Since I do not have Ubuntu, I can only guess.

Anyway, please try instead:

    dmesg | grep 1394

This will obtain log messages directly from the kernel instead via the system logger.

---

### Post by extendedping on 2009-11-17
> **Stefan Richter said:**
> I was the one who suggested to look for possibly interesting kernel messages in the log file.  There are some expected messages missing which could be a hardware problem (unlikely, since there are two controllers and at least the one which is not connected to the FirePod should show this certain message which is absent from the log file) or simply due to how the system log is configured at Ubuntu.  Since I do not have Ubuntu, I can only guess.

Anyway, please try instead:

    dmesg | grep 1394

This will obtain log messages directly from the kernel instead via the system logger.

I'll do that quick question should the firepod by attached on on for this? if so I will plug in an do a reboot, if not here is the output...

[    0.968494] ohci1394 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.024018] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[e0000000-e00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.295318] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00110666455556b7]
[    8.047285] ieee1394: raw1394: /dev/raw1394 device initialized

---

### Post by Stefan Richter on 2009-11-17
> **extendedping said:**
> I'll do that quick question should the firepod by attached on on for this? if so I will plug in an do a reboot,

Yes please.  (You don't need to reboot for this purpose though, unless you are currently running something else than Linux of course.)

> **extendedping said:**
> if not here is the output...

[    0.968494] ohci1394 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.024018] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[e0000000-e00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.295318] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00110666455556b7]
[    8.047285] ieee1394: raw1394: /dev/raw1394 device initialized

Aha, the "Host added" message is the one which I was looking for.  This shows that some basic initialization of the controller was successful at least.  When a device is plugged in/ switched on, there should be a similar "Node added" message.

And while you are at it, also post the output of

grep . /sys/bus/ieee1394/devices/*/*

after you plugged in/ switched on the FirePod.

---

### Post by extendedping on 2009-11-17
> **Stefan Richter said:**
> Yes please.  (You don't need to reboot for this purpose though, unless you are currently running something else than Linux of course.)



Aha, the "Host added" message is the one which I was looking for.  This shows that some basic initialization of the controller was successful at least.  When a device is plugged in/ switched on, there should be a similar "Node added" message.

And while you are at it, also post the output of

grep . /sys/bus/ieee1394/devices/*/*

after you plugged in/ switched on the FirePod.

ok I rebooted (cause I had in external hard drive in the firewire which I removed before rebooting) and after reboot turned on the firepod

brad@ubuntu:~$ dmesg | grep 1394
[    0.171394] pci 0000:00:1c.0: setting latency timer to 64
[    0.945580] ohci1394 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.000389] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[e0000000-e00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.266316] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00110666455556b7]
[    7.847094] ieee1394: raw1394: /dev/raw1394 device initialized
[  622.465180] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[  623.393181] ieee1394: Error parsing configrom for node 0-00:1023
[  623.393253] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[  625.260339] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000a9200c5031301]

and 

brad@ubuntu:~$ grep . /sys/bus/ieee1394/devices/*/*
/sys/bus/ieee1394/devices/000a9200c5031301-0/address:0x0000fffff0000438
/sys/bus/ieee1394/devices/000a9200c5031301-0/ignore_driver:0
/sys/bus/ieee1394/devices/000a9200c5031301-0/length:0
/sys/bus/ieee1394/devices/000a9200c5031301-0/model_id:0x010066
/sys/bus/ieee1394/devices/000a9200c5031301-0/model_name_kv:PreSonus FIREPOD
/sys/bus/ieee1394/devices/000a9200c5031301-0/specifier_id:0x00a02d
/sys/bus/ieee1394/devices/000a9200c5031301-0/version:0x010001
/sys/bus/ieee1394/devices/000a9200c5031301/bus_options:IRMC(1) CMC(1) ISC(1) BMC(1) PMC(0) GEN(2) LSPD(2) MAX_REC(128) MAX_ROM(1) CYC_CLK_ACC(100)
/sys/bus/ieee1394/devices/000a9200c5031301/capabilities:0x0083c0
/sys/bus/ieee1394/devices/000a9200c5031301/guid:0x000a9200c5031301
/sys/bus/ieee1394/devices/000a9200c5031301/guid_vendor_id:0x000a92
/sys/bus/ieee1394/devices/000a9200c5031301/nodeid:0xffc0
/sys/bus/ieee1394/devices/000a9200c5031301/vendor_id:0x000a92
/sys/bus/ieee1394/devices/000a9200c5031301/vendor_name_kv:Presonus
/sys/bus/ieee1394/devices/00110666455556b7/bus_options:IRMC(1) CMC(1) ISC(1) BMC(0) PMC(0) GEN(3) LSPD(2) MAX_REC(2048) MAX_ROM(2) CYC_CLK_ACC(100)
/sys/bus/ieee1394/devices/00110666455556b7/capabilities:0x0083c0
/sys/bus/ieee1394/devices/00110666455556b7/guid:0x00110666455556b7
/sys/bus/ieee1394/devices/00110666455556b7/guid_vendor_id:0x001106
/sys/bus/ieee1394/devices/00110666455556b7/nodeid:0xffc1
/sys/bus/ieee1394/devices/00110666455556b7/vendor_id:0x001106
/sys/bus/ieee1394/devices/00110666455556b7/vendor_name_kv:Linux - ohci1394
/sys/bus/ieee1394/devices/fw-host0/in_bus_reset:0
/sys/bus/ieee1394/devices/fw-host0/is_busmgr:0
/sys/bus/ieee1394/devices/fw-host0/is_cycmst:1
/sys/bus/ieee1394/devices/fw-host0/is_irm:1
/sys/bus/ieee1394/devices/fw-host0/is_root:1
/sys/bus/ieee1394/devices/fw-host0/node_count:2
/sys/bus/ieee1394/devices/fw-host0/nodes_active:2
/sys/bus/ieee1394/devices/fw-host0/selfid_count:2
/sys/bus/ieee1394/devices/fw-host0/uevent:DRIVER=nodemgr

---

### Post by Stefan Richter on 2009-11-17
OK, thanks for obtaining the additional diagnostics.

All of this looks fine, i.e. the kernel drivers have no difficulty so far to communicate with the FirePod.  Alas this means that we still don't know why ffado/ jack are not as successful.

---

### Post by extendedping on 2009-11-17
> **Stefan Richter said:**
> OK, thanks for obtaining the additional diagnostics.

All of this looks fine, i.e. the kernel drivers have no difficulty so far to communicate with the FirePod.  Alas this means that we still don't know why ffado/ jack are not as successful.

too bad cause the external harddrive worked with the firewire so I dont think it is the cable :(

---

### Post by extendedping on 2009-11-19
I guess that is that and I will start looking for a usb (edirol ua25??) used, thanks everyone for trying with me...

---

### Post by extendedping on 2009-11-19
hmm in a last ditch effort I scoured the closets and found this card [http://cgi.ebay.com/sound-blaster-audigy-2-z5-pci-sound-card-audigy-2-ZS_W0QQitemZ280425868875QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item414aaf2e4b](http://cgi.ebay.com/sound-blaster-audigy-2-z5-pci-sound-card-audigy-2-ZS_W0QQitemZ280425868875QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item414aaf2e4b)

plugged it into my pci after removing the firewire card, (it has 3 notches one overhangs my pci slot but what the heck it fits) and plugged the firepod in to the 1394 port. the firepod has had a blue light for 10 minutes (that is 9 minutes longer then it every lasted before and jack is up...) hope springs eternal???

---

### Post by AutoStatic on 2009-11-19
Don't get your hopes up high... :(
That same card came with the PC we use with the band. The Focusrite Firewire soundcard refused to work with it so I bought a Belkin PCI Firewire card with TI chipset and ditched the Audigy.
Firewire soundcards can be very picky when it comes to the Firewire chipsets they have to communicate with. But maybe the Presonus does work with the Audigy :)

---

### Post by extendedping on 2009-11-19
ok this should possibly be a new newbie thread, but here is where I am at...guitar into zoom g9.2tt plugged into firepod firepod into the sb card 1394 port and I started jack. 

I then opened ardour and hit new track. it called itself audio 1. I then hit shift space and began strumming the guitar plugged into the zoom. I see a wave forming which I think means I recorded something. however after stopping and unchecking the record button and hitting the play button I can not hear anything (I have my headphones in the firepod). I fiddled around and saw that monitoring was through hardware devices. so I do not know if I recorded something I then took a look at the jack window patchbay and connections which made me depressed as I did not understand one thing...here is what I saw...

I don't understand the connections or patchbay windows, but the output of the patchbay shows some stuff. the left side (ouput plugs) shows system, firewire_pcm, mide through, sb audigy 2zs (sb03350).

right  side says input  socets/plugs and has system, firewire_pcm, midi through, sb audigy 2 zs (sb0350), emu10k1 wave table, timidity. 

I have no idea what any of this stuff means on the left (output) system has capture 1 through capture 10, on the right (input) it has playback 1-10.

left (output) firewire says c10_dev0_mido 1 while right (input) says -10_dev0_midi 1

both left and right midi through say midi through port-0

both left and right sb audigy 2xs (sbo350) say audiry mpu-401 \(uart\), audigy mpu-401 #2

then the 2 additional categories on input say 
(emu10k1 wave table) --- emu10k1 port 0 through port 3

(timidity) timidity port 0 through port 3

I have NO clue what any of this means

my connections window is equally cryptic to me the left says readable clients and the right says writable clients. 
the left has 2 categories ardour and system, ardout says audio 1/out1, autioner /out 1 autitioner/out 2 click/out1 click/out2
left under system has capture-1 through 10

the right (writable clients) under ardour says audio 1/in 1 and under system has playback_1 through 10. 

there are also midi and also tabs but I am too afraid to look at them...

---

### Post by trulan on 2009-11-19
System Capture is you firepod inputs.  System Playback is your firepod outputs.  Hook up the two Master Outs in the Ardour box to System Playback 1 and System Playback 2, and your track should play back through the headphone jack on the firepod - provided the mixer knob on the firepod is turned to 'playback'.

Patchage will give you a clearer picture of what is going on, if it works for you.  Currently Patchage is barfing for me and I am thinking about starting another thread about those difficulties.

Good job on getting it working!  Hang in there!

---

### Post by extendedping on 2009-11-19
> **trulan said:**
> System Capture is you firepod inputs.  System Playback is your firewire outputs.  Hook up the two Master Outs in the Ardour box to System Playback 1 and System Playback 2, and your track should play back through the headphone jack on the firepod - provided the mixer knob on the firepod it turned to 'playback'.

Good job on getting it working!

ok I hear something, went into the mixer (could not find another way) and did as you said well close but the result was the same. I put input as 1 and output I did "add" it then gave 2 boxes and I clicked on the ardour tab (looks like I should have hit system) and selected the audio 1/in 1 and audio 2/in 1. well anyway the result is that now when I open out and edit in the mixer for the track it says under out one "system:playback_1 and under out 2 "system:playback_2 which is I guess what I need...how exciting. thanks so much for all the help I am still lost as I don't understand audio and routing inputs/busses but I did get it to make a sound. thanks forum...

---

### Post by sgx on 2009-11-19
For simplified quality recordings, just install timemachine, and record with it, (you just click in its window to begin recording!), to sort things, use a hydrogen looping beat for a constant sound source. When you make the right connections in the patchbay, you'll see the drums activity in the timemachine gui.

in qjackctl audio tab, hydrogen should automatically connect itself to
your sound system when it starts, you'll see the line between things in the audio tab, just connect it to timemachine by selecting both, and pressing the connect button. Start a demo song or make a beat, and let it keep looping. Click in the timemachine gui, it will change color, and be recording. The recording will be titled something like this:   tm-2009-01-01T10:42:06.w64 
You can import this into audacity for editing and wav/mp3/ogg etc  conversion. With ample disk space, you can just play with timemachine recording til you get a take you like, and edit out the rest.

The alsa tab should also have a hydrogen entry, connect it to the proper source on the opposite side of the tab, and you can play drums on your qwerty keyboard, or midi controller. Same deal for softsynth zynaddsubfx, audio tab connects your sound system to zyn, alsa tab connects devices like midi keyboards, qwerty keyboards to play the notes

For the zoom, lean the guitar by your computer so you can strum as you make various connections to timemachine searching for the magic one.

Take notes as to which are the connections you will use, for times you  start ardour, and use them, noting extra steps like selecting and arming tracks to record, may be needed in ardour and other multitrack recording software.

Cheers!

---

### Post by extendedping on 2009-11-19
thanks everyone now if I could just get the one track to a wav file I will post it (like anyone cares) so you can hear the zoom with the firepod....I don't know how to do that I have a vague memory in cubase of putting markings around the recording and "exporting" but I can't see how to do that here...

---

### Post by extendedping on 2009-11-19
hmm so I moved the markers I see on either side of the track and then I go to export...I can only export the entire session and I end up with a .wav file in my sessionname/exports folder. however the wav does not make any sound in mplayer or rhythmbox. I wonder is this is a ubuntu issue or if I just don't know my *** from my elbow and am doing something dumb...

---

### Post by trulan on 2009-11-19
Sounds like you sent Audio 1 to System Playback.  That will make sound, yes.  But it's more useful to do it this way:
In Ardour's mixer window, send the output of your track (Audio 1) to Master Out (Send all your tracks there).  Then send the output of the Master bus to System playback - that way all your tracks will be controlled by the master volume level in Ardour.

To export your song as a wav, set your start and end markers (they're little triangles just above the waveforms of your tracks) and select export in Ardour's file menu.  You'll have to check a box to send Master 1 to left and another box to send Master 2 to right (otherwise you'll export a blank wav ;) - been there done that) and you're good to go.

Edit: (was writing while you posted) It's not a matter of distinguishing body parts, just getting the right boxes checked.  You'll get the hang of it.

---

### Post by extendedping on 2009-11-19
> **trulan said:**
> Sounds like you sent Audio 1 to System Playback.  That will make sound, yes.  But it's more useful to do it this way:
In Ardour's mixer window, send the output of your track (Audio 1) to Master Out (Send all your tracks there).  Then send the output of the Master bus to System playback - that way all your tracks will be controlled by the master volume level in Ardour.

To export your song as a wav, set your start and end markers (they're little triangles just above the waveforms of your tracks) and select export in Ardour's file menu.  You'll have to check a box to send Master 1 to left and another box to send Master 2 to right (otherwise you'll export a blank wav ;) - been there done that) and you're good to go.

Edit: (was writing while you posted) It's not a matter of distinguishing body parts, just getting the right boxes checked.  You'll get the hang of it.

first thanks for all the help..I have the mixer opened and I do not see master out anywhere...

---

### Post by trulan on 2009-11-19
The master channel - should be on the far right of Ardour's mixer window.

I'm working on a how-to here but it's not complete yet.

[https://help.ubuntu.com/community/UbuntuStudio/HowToJackArdour](https://help.ubuntu.com/community/UbuntuStudio/HowToJackArdour)

Your questions give me good info for what should be included.

---

### Post by extendedping on 2009-11-19
here is the mp3 (found out bout sound converter too) just some chords for a song I have...there my first linux recording...

[www.soundclick.com/thekidfromperu](www.soundclick.com/thekidfromperu)

first one neptune ave...

---

### Post by trulan on 2009-11-19
Hey sounds good!  Way to go!

---

### Post by extendedping on 2009-11-19
> **trulan said:**
> The master channel - should be on the far right of Ardour's mixer window.

I'm working on a how-to here but it's not complete yet.

[https://help.ubuntu.com/community/UbuntuStudio/HowToJackArdour](https://help.ubuntu.com/community/UbuntuStudio/HowToJackArdour)

Your questions give me good info for what should be included.

good start on that sheet...I do not see anything in the ardour mixer for master channel I am probably just missing it :(

---

### Post by AutoStatic on 2009-11-20
Good to read that it's working! And nice songs on your soundclick page! I know close to nothing about Ardour so I'm reading with you ;)

---

### Post by extendedping on 2009-11-20
> **AutoStatic said:**
> Good to read that it's working! And nice songs on your soundclick page! I know close to nothing about Ardour so I'm reading with you ;)

thanks I a sure you know more then I do, audio is really its own language I see and there is a lot of assumed knowledge out there.

---

### Post by trulan on 2009-11-20
> **extendedping said:**
> I do not see anything in the ardour mixer for master channel I am probably just missing it. I guess it's possible you created a project without a master channel.  You can always make one - Add a track/bus, make it a stereo bus (2 channels), name it 'master', and route the outputs of all your tracks into that.  Then route the outputs of that to system playback 1 and 2.  It should put a master bus there by default though when you create a new project when opening Ardour.  Does your Ardour mixer look at all like the one on the how-to I linked?  You could post a screenshot of it if you'd like, I'll take a look at it.

---

### Post by extendedping on 2009-11-22
> **trulan said:**
> I guess it's possible you created a project without a master channel.  You can always make one - Add a track/bus, make it a stereo bus (2 channels), name it 'master', and route the outputs of all your tracks into that.  Then route the outputs of that to system playback 1 and 2.  It should put a master bus there by default though when you create a new project when opening Ardour.  Does your Ardour mixer look at all like the one on the how-to I linked?  You could post a screenshot of it if you'd like, I'll take a look at it.

thanks I'll check that this week as I try to learn hydrogen as well and make an actual song.

---

