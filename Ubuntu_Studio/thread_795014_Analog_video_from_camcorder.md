---
title: "Analog video from camcorder"
date: 2008-05-15
forum: Ubuntu Studio
---

### Post by Luke3026 on 2008-05-15
My setup:
P4 3.4GHz
1.5GB RAM
ATI Radeon X600 Video Card (using 3rd party accelerate ATI graphics driver)

Old Canon Hi8 Camcorder


I'm desperately trying to get the analog video from the camcorder into the PC to edit. Camera only has component outs (3.5mm jack to red/white/yellow component). I have these connected to the video card's component in's.

I've tried mencoder but haven't had much success cutting and pasting some of the commands I've found in the forums. I've only been running Ubuntu for about a week and am still feeling my way around.

Is there any way to do this?

---

### Post by Luke3026 on 2008-05-15
Messing around more with mencoder.  I've been playing with this command

$ mencoder -oac mp3lame -ovc lavc -lameopts mode=1:vbr=2:q=4 -lavcopts vcodec=mpeg4 -tv driver=v4l2:norm=ntsc:input=4:adevice=/dev/dsp:width=640:height=480 -af volume=-10 -o vid.avi tv://

And this in turn returns this-->

MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.40GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Hauppauge WinTV PVR-150
 Tuner cap:
 Tuner rxs:
 Capabilites:  video capture  VBI capture device  tuner  audio  read/write
 supported norms: 0 = PAL-BGH; 1 = PAL-DK; 2 = PAL-I; 3 = PAL-M; 4 = PAL-N; 5 = PAL-Nc; 6 = SECAM-BGH; 7 = SECAM-DK; 8 = SECAM-L; 9 = SECAM-L'; 10 = NTSC-M; 11 = NTSC-J; 12 = NTSC-K;
 inputs: 0 = Tuner 1; 1 = S-Video 1; 2 = Composite 1; 3 = S-Video 2; 4 = Composite 2;
 Current input: 2
 Current format: unknown (0x4745504d)
v4l2: current audio mode is : MONO
tv.c: norm_from_string(ntsc): Bogus norm parameter, setting default.
Audio block size too low, setting to 8192!
v4l2: ioctl request buffers failed: Invalid argument
v4l2: ioctl set mute failed: No such device
v4l2: 0 frames successfully processed, 0 frames dropped.
Segmentation fault


Any ideas?

---

### Post by bartvdm75 on 2009-03-21
hello,

i'm searching too in how to capture my old 8mm videos on my Ubuntu 8.04 pc.

How do i do this ??

i'm using the whit,red,yellow jack too..
this is my TV card :
description: 	Multimedia controller
product: 	SAA7134/SAA7135HL Video Broadcast Decoder
vendor: 	Philips Semiconductors
physical id: 	
b
bus info: 	
pci@0000:02:0b.0
version: 	01
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	saa7134
latency	=	64
maxlatency	=	255
mingnt	=	255
module	=	saa7134

Can somebody help me please ?
I just want to put the old videos on pc.

Thanks !

---

### Post by cotcot on 2009-03-22
Your card is pretty common, so I think it is supported.
I use a PVR 150. 
Generally I keep record of what I do to get things worked. Hereunder is what I noted to get my PVR 150 working. I hope you will get some inspiration. 
> Capture VHS with Hauppauge PVR150
The solution is to place the variable in /etc/environmentvlc will appear in your "Multimedia" packages list.* Click it to run it.* Use "File>Open Capture Device" and then click the "PVR" tab to get to your PVR settings.* Set "Norm" to "NTSC" (if you're in the USA, or "PAL" if Europe), and if you're using Channel 3 for the VCR output, then set the frequency to 61250.* Then click the "Advanced" button to open the rest of the needed settings.
What video input is my PVR150 currently using
As you probably already know, the PVR150 can capture off it's build in TV tuner (input 0), a SVIDEO source (input 1), or a COMPOSITE video source (input 2). You can always see what video input the PVR-150 is currently using by running the command:
v4l2-ctl -I
In which case you will probably see an output like this:
Video input : 0 (Tuner 1)
Step 2:Changing the capture input
To switch your PVR-150 to use the SVIDEO input run the command:
v4l2-ctl -i 1
If you are using the composite video input on your PVR-150 you will want to run:
v4l2-ctl -i 2
There are more inputs you can use. To get a listing of all of them and what number they correspond to run:
v4l2-ctl -n
If this sort of thing excites you you can find many more detail about v4l2-ctl at: [http://www.ivtvdriver.org/index.php/V4l2-ctl](http://www.ivtvdriver.org/index.php/V4l2-ctl)

In terminal 
cat /dev/video0 > test.mpg 

play deinterlaced
mplayer -vf pp=lb /dev/video0 

---

