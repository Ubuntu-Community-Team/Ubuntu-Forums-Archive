---
title: "Jaunty, Firepod, headaches. :("
date: 2009-10-06
forum: Ubuntu Studio
---

### Post by x7shadesofblackx on 2009-10-06
ALLLLLrighty then. Let's just say I'm a n00b at this whole Linux/Ubuntu thing. I looked into Ubuntu as an alternative to the suck-tacular Windows Vista that came on my Toshiba Laptop, especially because I do a nice bit of multi-media work (mostly music and graphical) and I wanted something that would be more stable and less CPU intensive (and without annoying background programs, etc)

Unsure of all of this, I installed Ubuntu via Wubi (I figured it would be a nice way to experiment) and I've been toying with it for a few days - I like it, but theres just one problem.

My PreSonus FirePod (my SINGLE piece of audio interface, really how hard could ONE piece of equipment be to configure?) doesn't appear to be recognized by Jack, Ardour, anything. I've tried various "definitive guides" to installing FirePods that I've found, and I've scoured forums and have even restarted Ubuntu through Wubi about three times trying to make it work. Considering I bought my laptop solely for the purpose of recording, and Vista is unreliable and Ubuntu doesn't seem to be giving me much love at the moment, I'm quite flustered.

I've also been considering Ubuntu Studio - apparently from what I hear it already has all of the drivers and firewire permissions or whatever already installed, and I've heard from some sources that it's also not the most reliable tool in the shed. 

Ah, and just in case, I'm running an AMD64 system as well, if that makes any difference. 

SO, in short - is there anyone who can help me with my FirePod problems, or should I just nuke my entire hard drive and clean install UbuntuStudio?

Thanks!!!

---

### Post by Jive Turkey on 2009-10-06
If you dont have a lot invested in configuration time on your current install, I would definitely explore the ubuntu studio option based on what you plan to use the laptop for.  If you really know for sure that vista will not suit your needs go ahead and format the HDD.  It is advisable to make multiple partitions, particularly one for your "/home" directory and less space for your "/" directory about 6-10GB should be fine.  Later you can install whatever linux distro or version you want on the / partition without erasing your home directory.

I dont know anything about firepod, but good luck.

---

### Post by Stochastic on 2009-10-06
Well the first question I have is, what's the output of qjackctl (Jack Control) in the messages window when you try to start jack (assuming you've changed the driver in the qjackctl settings window to 'ffado')?

I should let you know that Ubuntu Studio really doesn't differ that much from regular ubuntu in it's setup or drivers.  You can get Ubuntu installed on your current Ubuntu install by following these directions: [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy) (although it was written for Hardy, it applies to Jaunty equally) and it won't even harm your current Ubuntu install.  The instability that people talk about is the RT (realtime) kernel that comes with the ubuntustudio-audio package; in 9.04 many people found it froze randomly on them, but the upcoming 9.10 release (at the end of October) will have a much stabler RT kernel.  The RT kernel allows for very low latency communication with the soundcard, so most recommend it be used in an audio-centric setup (though plain 9.04 did boast some relatively low latency results).

I also have a Presonus firepod, and it works great on Ubuntu (well I'm running Ubuntu Studio, but it's essentially the same, just tailored for multimedia production), and I'm happy to help get yours up and running for you.  One easy method for setting things up is through the Ubuntu Studio Controls application.  Just install the [ubuntustudio-controls]("apt:ubuntustudio-controls") package, open it up (in System->Administration->Ubuntu Studio Controls), and check off each feature.  Here's an easy walkthrough: [https://help.ubuntu.com/community/UbuntuStudioControls](https://help.ubuntu.com/community/UbuntuStudioControls)

Finally you'll need to make sure Jack (the only audio server that will work with firewire cards out of the box at the moment - this will change in the future, but for now you're stuck with jack) is configured to use the ffado driver.  In qjackctl open the settings window and change the driver to ffado.  If you're running an RT kernel then it's okay (and recommended) to check off the realtime box, but if you're not, then make sure it's not checked.  Click okay, then start jack.

I've also found that you need to have the firepod turned on and connected to the computer at boot time for everything to get recognized (firewire soundcard support is still a growing feature in Ubuntu, soon it should be hot-pluggable).

So, if after that, you're still seeing errors from jack please post them.  There are many people on these forums who have working firepods so it's likely at least one has seen the same error before.

Hope that helps.

---

### Post by x7shadesofblackx on 2009-10-06
Ah, I see. Funny thing is, I haven't seen ANY of that in ANY of the places I've looked in for how to get this thing running. LOL  And everywhere I've found before has said to set Jack to FreeBob or Firewire. Hm, maybe I was just looking at something for other versions of Ubuntu perhaps? I'll go and try all of this as soon as I post this. :P

One question, however - Lord only knows the dumb changes I've made to my system settings trying to get this thing to work - In case this doesn't work for me, is there anyway to get everything back to defaults without having to nuke Ubuntu AGAIN? LOL

---

### Post by x7shadesofblackx on 2009-10-06
Foiled again! I don't seem to have ffado in my Jack options. :(
I'm guessing I should find some way of installing it, huh?

---

### Post by Stochastic on 2009-10-06
Whoops, you're right, the FFADO drivers are listed in qjackctl as 'firewire' rather than 'ffado' - this is what you should select.  

Freebob is the earlier version of this driver it should be considered obsoleted by ffado.

---

### Post by x7shadesofblackx on 2009-10-06
Alright then, even THAT doesn't seem to be working. I just set the interface option in the Jack Options to default, I don't know if thats what it should be or not. This is the error i got. 

 p, li { white-space: pre-wrap; }  [COLOR=#999999]14:21:16.883 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]14:21:17.067 Statistics reset.[/COLOR]
 [COLOR=#66CC99]14:21:17.090 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]14:21:17.836 ALSA connection change.[/COLOR]
 [COLOR=#999999]14:22:32.140 Startup script...[/COLOR]
 [COLOR=#990099]14:22:32.141 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]14:22:32.542 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]14:22:32.542 JACK is starting...[/COLOR]
 [COLOR=#990099]14:22:32.543 /usr/bin/jackd -R -P70 -dfirewire -r96000 -p128 -n2 -i10 -o10[/COLOR]
 [COLOR=#999999]14:22:32.560 JACK was started with PID=6101.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 SSE2 detected
 [COLOR=#FF0000]14:22:32.626 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 02990962412:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 05:33:49
 firewire ERR: Error creating FFADO streaming device
 02990963036: [31mError (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
 This usually means:
  a) The device-node /dev/raw1394 doesn't exists because you don't have a
     (recognized) firewire controller.
   b) The modules needed aren't loaded. This is not in the scope of ffado but of
     your distribution, so if you have a firewire controller that should be
     supported and the modules aren't loaded, file a bug with your distributions
     bug tracker.
   c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
     shows the device-node with its permissions, make sure you belong to the
     right group and the group is allowed to access the device.
 [0mcannot load driver module firewire
 no message buffer overruns
 [COLOR=#999999]14:22:32.893 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]14:22:32.894 Post-shutdown script...[/COLOR]
 [COLOR=#990099]14:22:32.894 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]14:22:33.302 Post-shutdown script terminated with exit status=256.[/COLOR]

[COLOR=#999999][/COLOR]

[COLOR=#999999][/COLOR]

[COLOR=#999999][/COLOR]
[COLOR=Black]I don't know if this has anything to do with any of those blind changes I did in my past attempts to get it to work, maybe I knocked something out of whack?[/COLOR]

---

### Post by ItsAlwaysSunnyIn... on 2009-10-06
hey,

I'm in the same boat. Recently decided to switch to Ubuntu for some multi-track recording with my Presonus Firepod. I have alot of experience recording in Xp and old faithful Windows 98 SE. Anyway on a new Dell XPS Studio laptop, I installed Ubuntu 9.04 on a new partition (i will still need vista for some other things). I installed the -rt kernel but I am have a terrible time getting my external lcd monitor working on the -rt (i need the external cause it's only a 13" screen). The generic works fine. I'm thinking of installing Ubuntu Studio instead but not sure if will make a difference. All my time has been spent conifiguring these effing NVIDIA drivers (9500M not well supported yet for some reason). Once I get some time with the Firepod I'll post my experiences. Anyway I will be posting here with some problems/fixes that I come across. Hopefully we can help each other out. 

CD

---

### Post by x7shadesofblackx on 2009-10-07
Alrighty, so NEW ATTEMPT!
I restarted EVERYTHING, even my Vista, to out of the box specs.
And I installed Ubuntu via Wubi once more.
I did what Stochastic said to get Studio and set the studio controls and what have you. 
and that's ALL of the changes I've made - nothing more nothing less.
And JACK STILL doesn't recognize my FirePod. 
This is the new message. 

 p, li { white-space: pre-wrap; }  [COLOR=#999999]22:18:27.440 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:18:27.441 Statistics reset.[/COLOR]
 [COLOR=#66cc99]22:18:27.535 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]22:18:27.733 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:18:29.330 Startup script...[/COLOR]
 [COLOR=#990099]22:18:29.331 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]22:18:29.733 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]22:18:29.733 JACK is starting...[/COLOR]
 [COLOR=#990099]22:18:29.734 /usr/bin/jackd -R -dfirewire -r44100 -p1024 -n3[/COLOR]
 [COLOR=#999999]22:18:29.736 JACK was started with PID=4015.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread 1402287856, from thread 1402287856] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]22:18:29.959 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]22:18:29.960 Post-shutdown script...[/COLOR]
 [COLOR=#990099]22:18:29.960 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]22:18:30.385 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]22:18:31.794 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.'[/COLOR]


[COLOR=#ff0000][COLOR=Black]It appears the Ubuntu God does not favor me. :( [/COLOR]
[/COLOR]

---

### Post by trulan on 2009-10-08
Here's the thread that got me going with my firepod in Jaunty:
[http://ubuntuforums.org/showthread.php?t=1129383&highlight=1394+issues](http://ubuntuforums.org/showthread.php?t=1129383&highlight=1394+issues)

Follow the steps that Stochastic went through with mypetjaws.  Sometimes Ubuntu Studio Controls messes up, and this will help you figure out where the problem is.  Pay special attention to post 24.

Oh, wait.  That may not be your problem.  Your Jack output says you do not have permission to use real-time scheduling.  That's a different problem.  Now, if I could just remember how to fix it...

This setting should be /etc/security/limits.conf.  Ubuntu Studio controls should be adding a few lines at the bottom, saying something like rtprio and memlock.  Is anything there?

Oh, by the way, hang in there.  A firepod in Linux is a beautiful thing!

---

### Post by x7shadesofblackx on 2009-10-08
Hm, there's nothing there. The only option that I haven't seen mentioned anywhere yet is one that says "Enable X Restart shortcut," and I've left it unchecked thus far...

And if ANYONE could figure out how to fix that real-time scheduling thing, if that really IS my one and only problem... LOL

---

### Post by Stochastic on 2009-10-08
what's the output of ```
uname -r
```and ```
groups
```

If the first (uname -r) outputs a kernel name that ends in -RT (or -rt) then that's a good thing.

If the second (groups) contains both "audio" and "video" then that's also a good thing.

I'm betting that one of those is not the case in your current setup.

---

### Post by x7shadesofblackx on 2009-10-08
Hmmm nope, I have neither of them. How would I go about doing that???
This is what I get with those codes, by the way. 


christian@ubuntu:~$ uname -r
2.6.28-15-generic
christian@ubuntu:~$ groups
christian adm dialout cdrom plugdev lpadmin admin sambashare

---

### Post by Stochastic on 2009-10-09
> **x7shadesofblackx said:**
> Hmmm nope, I have neither of them. How would I go about doing that???
This is what I get with those codes, by the way. 


christian@ubuntu:~$ uname -r
2.6.28-15-generic
christian@ubuntu:~$ groups
christian adm dialout cdrom plugdev lpadmin admin sambashare

Okay, first step is to go to System->Administration->Users & Groups Click 'unlock' at the bottom of the window, then click on Manage Groups.  In that new window you should create both an audio and video group and add your user (christian) to them both.  After this step, it's a good idea to log out then back in.

Second, a disclaimer about the RT kernel: It's not that stable in 9.04 and it's not essential for using the firepod.  It's purpose is to get low latency recording capabilities.

To get the RT kernel installed simply install the [ubuntustudio-audio]("apt:ubuntustudio-audio") package OR just the [linux-rt]("apt:linux-rt") package.  Once it's installed, at boot time in your Grub menu (the black and white listing of operating systems at boot time) there should be an entry that ends in "-RT", select that entry and you're running the RT kernel.

If you do run the RT kernel, then in qjackctl's properties window you can check off the "realtime" option.  If you don't run the RT kernel, then in qjackctl's properties window, make sure that option is turned off.

After making those changes, post the errors again.  It's also good to turn verbose messages on in qjackctl's properties window to see clearer error messages.

---

### Post by x7shadesofblackx on 2009-10-09
Alright, I installed the real time kernel and I'm running it now. 
I started up JACK, and it's reading the FirePod - the light on the FirePod changed to blue, and it's reading the inputs/outputs and SPDIF. But JACK decides he doesn't wanna go all the way, apparently. Here's the new error message. It's a long one this time.

 p, li { white-space: pre-wrap; }  [COLOR=#999999]17:26:23.410 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:26:23.424 Statistics reset.[/COLOR]
 [COLOR=#66cc99]17:26:23.439 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]17:26:23.637 ALSA connection change.[/COLOR]
 [COLOR=#999999]17:26:42.704 Startup script...[/COLOR]
 [COLOR=#990099]17:26:42.704 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]17:26:43.107 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]17:26:43.107 JACK is starting...[/COLOR]
 [COLOR=#990099]17:26:43.108 /usr/bin/jackd -v -R -dfirewire -r96000 -p128 -n3 -i10 -o10[/COLOR]
 [COLOR=#999999]17:26:43.130 JACK was started with PID=4895.[/COLOR]
 getting driver descriptor from /usr/lib/jack/jack_freebob.so
 getting driver descriptor from /usr/lib/jack/jack_oss.so
 getting driver descriptor from /usr/lib/jack/jack_firewire.so
 no message buffer overruns
 getting driver descriptor from /usr/lib/jack/jack_alsa.so
 getting driver descriptor from /usr/lib/jack/jack_dummy.so
 getting driver descriptor from /usr/lib/jack/jack_net.so
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 server `default' registered
 registered builtin port type 32 bit float mono audio
 registered builtin port type 8 bit raw midi
 clock source = system clock via clock_gettime
 loading driver ..
 start poll on 3 fd's
 new client: firewire_pcm, id = 1 type 1 @ 0x2543a80 fd = -1
 SSE2 detected
 new buffer size 128
 00825608395:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 05:33:49
 00826505925: Debug (bebob_mixer.cpp)[ 126] addElementForAllFunctionBlocks: Adding elements for functionblocks...
 firewire MSG: Streaming thread running with Realtime scheduling, priority 10
 firewire MSG: Registering audio capture port C0_dev0_Input 1L
 registered port system:capture_1, offset = 512
 firewire MSG: Registering audio capture port C1_dev0_Input 2R
 registered port system:capture_2, offset = 1024
 firewire MSG: Registering audio capture port C2_dev0_Input 3L
 registered port system:capture_3, offset = 1536
 firewire MSG: Registering audio capture port C3_dev0_Input 4R
 registered port system:capture_4, offset = 2048
 firewire MSG: Registering audio capture port C4_dev0_Input 5L
 registered port system:capture_5, offset = 2560
 firewire MSG: Registering audio capture port C5_dev0_Input 6R
 registered port system:capture_6, offset = 3072
 firewire MSG: Registering audio capture port C6_dev0_Input 7L
 registered port system:capture_7, offset = 3584
 firewire MSG: Registering audio capture port C7_dev0_Input 8R
 registered port system:capture_8, offset = 4096
 firewire MSG: Registering audio capture port C8_dev0_S/PDIF Input 9L
 registered port system:capture_9, offset = 4608
 firewire MSG: Registering audio capture port C9_dev0_S/PDIF Input 10R
 registered port system:capture_10, offset = 5120
 firewire MSG: Registering midi capture port C10_dev0_MIDI 1
 registered port firewire_pcm:C10_dev0_MIDI 1, offset = 512
 firewire MSG: Registering audio playback port P0_dev0_Output 1L
 registered port systemplayback_1, offset = 0
 firewire MSG: Registering audio playback port P1_dev0_Output 2R
 registered port systemplayback_2, offset = 0
 firewire MSG: Registering audio playback port P2_dev0_Output 3L
 registered port systemplayback_3, offset = 0
 firewire MSG: Registering audio playback port P3_dev0_Output 4R
 registered port systemplayback_4, offset = 0
 firewire MSG: Registering audio playback port P4_dev0_Output 5L
 registered port systemplayback_5, offset = 0
 firewire MSG: Registering audio playback port P5_dev0_Output 6R
 registered port systemplayback_6, offset = 0
 firewire MSG: Registering audio playback port P6_dev0_Output 7L
 registered port systemplayback_7, offset = 0
 firewire MSG: Registering audio playback port P7_dev0_Output 8R
 registered port system:playback_8, offset = 0
 firewire MSG: Registering audio playback port P8_dev0_S/PDIF Output 9L
 registered port systemplayback_9, offset = 0
 firewire MSG: Registering audio playback port P9_dev0_S/PDIF Output 10R
 registered port systemplayback_10, offset = 0
 firewire MSG: Registering midi playback port P10_dev0_MIDI 1
 registered port firewire_pcm : P10_dev0_MIDI 1, offset = 0
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now firewire_pcm active ? 1
 client firewire_pcm: internal client, execution_order=0.
 -- jack_rechain_graph()
 -- jack_sort_graph
 libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 1.
 libiec61883 warning: iec61883_cmp_create_p2p_input: Failed to set the iPCR[0] plug for node 1.
 firewire ERR: Could not start streaming threads: -1
 DRIVER NT: could not start driver
 cannot start driver
 starting server engine shutdown
 stopping driver
 unloading driver
 00826947093: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_Volume_1...
 00826947112: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_LRBalance_1...
 00826947124: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_Volume_2...
 00826947135: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_LRBalance_2...
 00826947145: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_Volume_3...
 00826947156: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_LRBalance_3...
 00826947167: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_Volume_4...
 00826947177: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_LRBalance_4...
 no message buffer overruns
 freeing shared port segments
 stopping server thread
 stopping watchdog thread
 last xrun delay: 0.000 usecs
 max delay reported by backend: 0.000 usecs
 freeing engine shared memory
 max usecs: 0.000, engine deleted
 WARNING: 1 message buffer overruns!
 cleaning up shared memory
 cleaning up files
 unregistering server `default'
 [COLOR=#999999]17:26:44.691 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]17:26:44.691 Post-shutdown script...[/COLOR]
 [COLOR=#990099]17:26:44.692 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]17:26:45.101 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]17:26:45.185 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

### Post by trulan on 2009-10-10
> **x7shadesofblackx said:**
> 
 [COLOR=#999999]17:26:43.107 JACK is starting...[/COLOR]
 [COLOR=#990099]17:26:43.108 /usr/bin/jackd -v -R -dfirewire -r96000 -p128 -n3 -i10 -o10[/COLOR]
 [COLOR=#999999]17:26:43.130 JACK was started with PID=4895.[/COLOR]
 [COLOR=#ff0000][/COLOR]
You're almost there.  You just have your latency set a bit too tight.  Either decrease your sampling rate (from 96000 to 48000 or 44100) or increase your buffer frames/period to 256.   If the firepod still fails to stay blue, increase the buffering again.  If it gets too huge there is a problem.  But it sounds to me like you almost have it working!

---

