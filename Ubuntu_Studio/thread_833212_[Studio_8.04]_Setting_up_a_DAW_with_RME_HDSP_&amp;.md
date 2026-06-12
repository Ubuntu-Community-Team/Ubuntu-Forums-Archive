---
title: "[Studio 8.04] Setting up a DAW with RME HDSP &amp; Jack?"
date: 2008-06-18
forum: Ubuntu Studio
---

### Post by userfriendly on 2008-06-18
Hopefully I'm not being impudent here, but after several previous attempts at getting this thing to work, I decided to start anew and get some advice from the experienced folks here. I posted my previous troubles with Jack in this thread: [http://ubuntuforums.org/showthread.php?t=819943&page=2](http://ubuntuforums.org/showthread.php?t=819943&page=2)

I want to set up this machine mainly as a digital audio workstation, and although I'd also like to do other stuff with it, like 2D/3D content creation and PHP/Actionscript development, the first thing I'm going to try setting up is a hickup-free DAW workflow.

Problems during my last attempt seemed to be:

[LIST]
[*] udev switched the indices for the audio devices, meaning that the HDSP was hw:3 at one time, hw:2 at another. I had to change the Jack setup after every reboot to account for this. Specifying it in /etc/modprobe.d/alsa-base (like "options snd-hdsp index=0") didn't seem to help, but rather removed the device from /proc/asound/modules instead. I might have frakked that up, though.
[*] When Jack was running, it didn't do so in a solid manner, except when I was only playing back audio files with Totem, which worked fine for hours ongoing. Everything else had pops 'n crackles, no matter how much I played with buffers & timeout settings, and led to Jack disconnecting after an arbitrary amount of time, sometimes a couple minutes, sometimes half an hour.
[/LIST]

Alright. New attempt. Here's what I did so far:

[LIST]
[*] I ran memtest+ first. Luckily it doesn't report any errors.
[*] In the BIOS, I disabled everything except the onboard LAN. Meaning now there's no onboard audio, no gameport, no serial port etc.
[*] Installed a fresh Ubuntu Studio 8.04 on a partition that I formatted as ext2 (after reading that Jack doesn't seem to like ext3 much). Its kernel version is 2.6.24-16-rt.
[*] I left all language settings at default (English) instead of setting them to German (after getting some weird errors in Ardour with the germanised version).
[*] Selected all software except the video creation/editing stuff.
[*] My audio device (RME Hammerfall DSP Multiface + PCI Card) is plugged into the 2nd PCI slot. All other PCI slots are empty. The mainboard is an Asrock 4CoreDual-VSTA with a Via chipset. The graphics adapter is an ATI HD2600XT - apparently that one has HDMI capabilities which means it also counts as an audio device (which I'd like to have disabled, since I don't use it anyway - any hints on how to do that are greatly appreciated).
[/LIST]

From /proc/asound/modules I can gather that I now have only two audio devices in that system, the actual audio device that I want to use, the HDSP (snd_hdsp, currently hw:1), and this darn Intel HDMI thingie on the ATI graphics adapter (which is listed as snd_hda_intel, currently hw:0).

So... I'm going to document every step I take, for easier rollback in case I frak something up (which is all too likely). I'd very much appreciate advice on DO's & DO NOT's.

I suppose updating the whole thing won't hurt, right? Meaning, running the update manager and let it update itself to kernel 2.6.24-19-rt and other updated stuff. Which is what I'm going to do next. If that is a DO NOT, don't hesitate to say so. I haven't done enough to feel bad about rolling back again yet.

After that, I was planning on removing Jack, checking out the latest SVN code and compiling it. Running some quick tests with VLC & Totem, meaning playing around with buffers and stuff while playing back large *.mkv video files and some *.wav & *.mp3 audio files, seeing how many XRUN's I get and if Jack behaves the way I'd like it to (meaning, being rather unobtrusive instead of killing Gnome like during my last attempts).

Additional questions I have:
[LIST]
[*] Do I better go with pulseaudio than with ALSA? Or might this be a problem regarding drivers for the HDSP, since it's supported pretty well in ALSA, no idea about that kind of thing with pulseaudio.
[*] As opposed to the version that comes with Ubuntu Studio 8.04, which is Ardour 2.3, the latest SVN code of Ardour has MIDI sequencing stuff built in, right?
[*] Do you have any articles, how-to's and similar stuff that I should read before proceeding? My intention is to learn as much as I can - having done my music creation stuff solely under Windows before, I'm a complete newbie when it comes to audio under Linux. Not a complete newbie with Linux in general, though, since I've been using it for years for web development and the run-of-the-mill stuff people do with computers.
[/LIST]

Thanks in advance, this is a great forum, and I'm pretty confident that I'll be able to ditch Windows completely soon. Will be reporting back in a couple hours.

---

### Post by userfriendly on 2008-06-18
i ran the system update, installed the restricted driver for my ati graphics card and ran aticonfig to get my dual monitor setup running. all fine so far. i'm currently making a complete backup of this partition ([http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)), which is what i'm going to do after every significant step.

next on my list is getting a current version of jack up and running. first i'll get the latest code from their svn repo and compile it, then i'll follow these instructions: [http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

will report back soonish.

---

### Post by thorgal on 2008-06-18
a few comments :

1- VIA chipset ? that's bad news. I remember some comments on ardour's website about hardware to avoid. VIA was at the top of the list due to flawed DMA operations.

2- intel-hda stuff : you can blacklist an alsa module in /etc/modprobe.d/blacklist

3- graphics : get another PCI card for graphics (nvidia should be OK, a GeForce FX 5200 is cheap and should do the job) and disable the ATI thing. This reminds me : it is not necessarily a good idea to use your DAW for 3D modeling ... 
In fact, as far as my DAW is concerned, I had to disable both 3D and 2D acc. I use an intel GPU which uses PCI access for these operations. I want the PCI bus to be for my HDSP.

4- look at IRQs. You can set a very low priority to some IRQ threads. You can first get a script called rtirq and tweak its configuration to maximize priorities where needed (hdsp IRQ thread, soft-timer threads, etc). You should read about it! I don't have any link at hand for you but you can google around rtirq.

good commands to know regarding IRQs :

cat /proc/interrupts : gives you the list of IRQs and associated kernel module. 
ps xa | grep IRQ : list the IRQ thread processes
chrt -p `pgrep IRQ-x` : outputs the scheduling policy and priority of IRQ-x process
chrt -f <prio> -p <pid> : sets scheduling policy to SCHED_FIFO at priority 'prio' to process ID pid. 

exemple : if the HDSP IRQ is 23 (from /proc/interrupts), it will correspond to a thread process called IRQ-23. You can then check and set the scheduling policy and priority level. You can also do so for other IRQ threads and set the SCHED_OTHER policy (non realtime), e.g. for the network or USB IRQs.

---

### Post by userfriendly on 2008-06-19
alright, thank you. :) i also had a look at the ardour website and skimmed some of the forum posts there.

1- i just went and bought a new mainboard. well, not so new, an asus p5b, it has the i965 chipset (same as yours, but sans integrated graphics). thought that VIA scare was a thing of the past, but i must admit i never fully trusted that asrock board anyway. my last DAW had an asus p4g8x with an intel i7205 and that one was rock stable. under windows, though.

2- thanks, that sounds exactly like what i was looking for.

3- don't you mean pci-express, not pci? since, if i want the pci bus for the hdsp, i probably shouldn't throw a pci card onto that bus, too, right? also, i understand you're telling me not to use the restricted driver? okay, but how do i get my dual monitor setup working without aticonfig? loved how simple that was, just a line typed into the shell. *sigh*

4- will take a very close look at IRQ stuff this time around. thanks for the hints, that will take me a long way. :)

will report back in a couple hours.

---

### Post by userfriendly on 2008-06-19
okay, result of the first quick tests: no more dying jack, just a couple xruns with a buffer lower than 256. maybe i can still tune that a bit, but you're right, since i can use the multiface box for monitoring purposes, ultra-low latency isn't that high a priority.

two things are different from my last attempt: Intel chipset instead of Via, and no restricted driver for the Ati card. going to install the latter and see if it changes anything for the worse. in case it does, i'll roll it back. then i'm going to take a look at the IRQ stuff for fine-tuning.

---

### Post by thorgal on 2008-06-19
hey userfriendly,

Glad you're progressing :)

you're right about PCI! was too fast in writing ... But the intel GPU does use PCI access for h/w acc.

I do have a dual monitor setup with this GPU (I don't remember the name of the intel GPU, something X3000 whatever, it's part of the i965). The trick is to get an SVDO extension card. It takes a PCIexpress slot. So I've got one monitor on VGA, the other on this SVDO extension which provides a DVI port. Then I use xrandr to place the screens as I want. X11 thinks I only have one screen of 3360x1050. Xrandr sees both ports and lets you place one screen on the left or right hand side (or up or down) the other screen. It takes one commad line that I automated at KDE startup. As simple as this :)

---

### Post by userfriendly on 2008-06-19
ah, yes - i suppose the PCI bus gets used by all and everything. <_< poor thing. anyway :D this ati pci-express card i have brings two DVI ports with it, which was pretty much the reason i bought it. had DVI+VGA before, and i must say i do like DVI+DVI a lot better, was never quite fond of making a digital signal analogue for its transit over a cable just to make it digital again at its destination. two needless convertions and the picture is, compared to DVI, a mess. well, of course, that might be my cheap monitors, or rather the cheap converters in them. still have to use DVI+VGA at work <_< unless i can convince my boss to buy me a new graphics card. come to think of it, i'll probably suggest that next week when i get back to the office.

the restricted driver didn't seem to do anything to worsen the performance, though, so i think i'm gonna keep it for now. thanks again for that tip with the chipset. i just *love* my new mainboard. when i started using computers for making music, i had an asus p2b, followed by a p3b. now the p5b is kinda like coming home... well, kinda. ;) i guess the p4g8x somewhat messed up the neat line of nomenclature succession. and i'll never mention that asrock board here again - probably going to get me a cheap little celeron and make a new mini-server out of it. my old Via Epia has always been annoyingly slow, what with the 533 mhz and all.

also, that blacklisting the hdmi audio module worked wonderfully - now there's only the HDSP, it's listed as hw:0, jack doesn't complain, the flash plugin plays back videos loud and clear, and my large video files are the enjoyable treats they're supposed to be. pretty much like my old ubuntu install, just with the added rt-kernel sexy. :D

i suppose this thread's solution can be summed up with "Don't buy Via if you want to build a DAW" - some things probably never change. >_>

many, many thanks for your help. :) i'll report back with more news later this weekend.

---

### Post by thorgal on 2008-06-20
great :)
now to the IRQs, and then you should be rocking! :guitar: 

by the way, I have different jackd setups (all at 96kHz):

I have an 
- RT mode : buffer length of 64 (latency of 0.7 ms!! that's quite crazy but with this mode, using the PC as a guitar effect rack becomes a real pleasure :) )
- Default mode : 256
- Lazy mode : 1024
- Mastering mode : 1024 + playback only (no full duplex)

I wish more jack apps were like ardour, which is able to disconnect from jack by a simple click. This lets you switch qjackctl presets without having to close every app ... Lash is supposed to help but I never used (not all apps support it, ardour for one does not).

---

### Post by angelsguitar on 2008-07-22
Hi userfriendly! How is it going with your new setup?

---

### Post by userfriendly on 2008-10-31
it's been great, thanks to thorgal. at the moment i'm playing around with reaper on wine, waiting for ardour 3 to pop up in the packet manager. 

bought a new guitar and been using windows less and less. really love ubuntu studio. :)

---

