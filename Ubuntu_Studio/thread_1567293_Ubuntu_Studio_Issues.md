---
title: "Ubuntu Studio Issues"
date: 2010-09-03
forum: Ubuntu Studio
---

### Post by sheehanje on 2010-09-03
I've been using Ubuntu Studio for a while on my desktop.  My setup there was a 9.10 distribution that I manually upgraded with the studio packages, and then upgraded to 10.04.  I had good luck using ffado with a presonus FP10, but I would get multiple xruns when I would plug in my axiom 49 keyboard.  While this wasn't too big of a deal, I also just recently got a TubeFire 8 (excellent unit by the way, really gives a warm sound to mic'd insruments and vocals, much warmer than the Presonus)...  With the arrival of this unit, I figured I'd rework my Studio setup at the same time.... I'm begging for trouble, I know...

So, I decided to experiment with my laptop.  I have a business class laptop from Dell (latitude e6500).  It's a decent system with a dual core 2.8Ghz processor, 4GB of RAM, 7200 rpm 250 gig HD, and it has a mini firewire adapter, which I just happened to actually have a cable for.

After installing Ubuntu Studio 10.04, I had some normal annoyances (permissions, CPU scaling that I didn't have on the desktop), and then some intermediate hiccups (nvidia drivers, etc.)  I compile a kernel, then follow multiple tips from different threads, using Trulan's brilliant post as a base guide for setting up 10.04 with a RT kernel.

Lo and behold, the FP10 works..  128 frames, 2 period/buffers,  44 Sample rate.  Works really good on the laptop...

Now the problem parts...

Plugging in the Axiom 49 gives me xruns... Not nearly as bad as before, maybe 4 an hour compared to 100 or more an hour on the old system... It's still not acceptable for recording with...  More than recording with it, I want to use it as a control surface of sorts, and my main reason for purchasing it to begin with...  I get these xruns with just the minimum loaded to work the unit: jackd and qsynth...  
Is anyone else having issues with usb midi devices and firewire devices running at the same time?

My next problem, and I honestly haven't worked on this much yet, so it's more of a question right now than a problem...

Can I daisy chain the TubeFire 8 and Presonus?  I see the devices using ffado-test ListDevices ...  But I see nothing when I load jackd..

I've seen a bunch of daisy chaining two FP10's, or two of the same devices, but not so much when it comes to different devices...  Has anyone had luck with this?

It would be a huge boost to be able to move the drums/vocals to the tubefire 8, and use the presonus for line devices, like the podxt for the guitars...  If I do manage to get both working, will I need an external word clock or anything else to keep them in sync, or will jackd do that for me?

Thanks in advance for any advice/suggestions/comments.

---

### Post by AutoStatic on 2010-09-03
> **sheehanje said:**
> Is anyone else having issues with usb midi devices and firewire devices running at the same time?Hello sheehanje, no issues here. I'm running jackd with 64 frames, 2 period/buffers and 48 Khz sample rate and about 4 or 5 MIDI USB devices. What prio do you give JACK? And do you use rtirq? And what do **lsusb** and **cat /proc/interrupts** in a terminal output?

---

### Post by sheehanje on 2010-09-03
> **AutoStatic said:**
> Hello sheehanje, no issues here. I'm running jackd with 64 frames, 2 period/buffers and 48 Khz sample rate and about 4 or 5 MIDI USB devices. What prio do you give JACK? And do you use rtirq? And what do **lsusb** and **cat /proc/interrupts** in a terminal output?

I'm at work right now, so from memory, jackd is running at 70 for priority.

I am still a little confused about the rtirq script, so do I use the one that comes with ubuntu studio, or the updated one?

I will run lsusb and cat /proc/interrupts as soon as I get home... 

One thing I will say, I am intent on using Compiz with Ubuntu Studio.  I know you advocate against it, but I find it can be very useful.  I used to think of the Desktop Cube as just an eye candy thing, until I started using Linux/Ubuntu for studio work.  It's invaluable to have my mixers, mastering interface, midi stuff, etc on different cube faces, and to actually see them working in real time as I'm rotating the cube.  So, keep in mind, I am running compiz and would like to find a way to keep it running with my setup.  If I have to ditch it, I will..

As a side note, thanks for replying.  I've been on here for 2 years, and while I don't post much, I always appreciate Trulan and your input to the Ubuntu Studio Community...  Hopefully I can return the favor some day when I'm not changing so many diapers and working 12 hour shifts...

---

### Post by AutoStatic on 2010-09-03
> **sheehanje said:**
> I'm at work right now, so from memory, jackd is running at 70 for priority.That should be alright.

> **sheehanje said:**
> I am still a little confused about the rtirq script, so do I use the one that comes with ubuntu studio, or the updated one?Lucid comes with the updated script.

> **sheehanje said:**
> One thing I will say, I am intent on using Compiz with Ubuntu Studio.  I know you advocate against it, but I find it can be very useful.  I used to think of the Desktop Cube as just an eye candy thing, until I started using Linux/Ubuntu for studio work.  It's invaluable to have my mixers, mastering interface, midi stuff, etc on different cube faces, and to actually see them working in real time as I'm rotating the cube.  So, keep in mind, I am running compiz and would like to find a way to keep it running with my setup.  If I have to ditch it, I will..Compiz uses a lot of resources. If you want to have a stable set-up with the least chance of running into xruns then Compiz doesn't really fit in. But if your PC can handle it, why not?

> **sheehanje said:**
> As a side note, thanks for replying.  I've been on here for 2 years, and while I don't post much, I always appreciate Trulan and your input to the Ubuntu Studio Community...  Hopefully I can return the favor some day when I'm not changing so many diapers and working 12 hour shifts...Appreciate the props, thanks!

---

### Post by sheehanje on 2010-09-04
Ok, last night I had the band over... Nothing but issues with the new setup at first. 

I made sure ohci1394 was added to the rtirq script in the proper places.

 I got both devices recognized by jackd by supplying the guid of both devices.  As a side note the syntax:

```
jackd -P70 -dfirewire -d "guid:0x123456789;guid:0x123456789"
```Did not work with the latest packages.  For some reason I had to drop the second -d and use:

```
jackd -P70 -dfirewire "guid:0x12345689;guid:0x12345689"
```But I do get both devices working using this from the command line...  Getting it to work in the GUI is another chore because it insists on appending the second -d  ....

I set CPU scaling to performance for both cores, then I opened up my usual programs.

Patchage, ArdourVST, rakarrack, qsynth

On the presonus fp10, I had the drums (electric set, stereo) and the rhythm guitar (podxt live, stereo).  

On the TubeFire I had the lead guitar and vocals.  Both mono, and both benefit from the tube preamp.  The lead guitar comes in mono, then I put the signal into rakarrack, go out stereo to ardour.

At this point, I had one drop... Not a big deal...  

We were good for about 20 minutes or so, then all of a sudden everything kept cutting out, then getting weird sounds.  I looked at the screen and noticed the drops were shooting up fast, abotu 1500 or so in 30 seconds.  I noticed that the cpu scaling reverted back to 800Mhz, instead of the top end of 2.54ghz.  

So, I reset everything...  Same thing...  I noticed the laptop was HOT ...  I also noticed rakarrack eating up cpu cycles like crazy....  

So, to get through the rest of practice, I shut everything down.  I hooked up just the presonus fp10.  I also set the cpu scaling to 1.60Ghz...  I also disabled Compiz...  We made it through the session, but the CPU was being pegged fairly high at ~65% throughout.  

After the guys left, I did a little experimenting with the programs, and noticed rakarrack really eats up CPU with the convolution mod on.  I disabled this, as it really didn't do too much for the sound.  I also got compiz working again, and the system ran stable with just the firepod.  The CPU was stable at about 15 - 18% utilization.   I am afraid to put the scaling back at performance, I don't want to fry the laptop...  But I think I can push it to about 2.2ghz without adverse effects..  How to I get it so I can set it, and keep it at that setting on boot?

I am also going to try and throw the tubfire back in the mix, as it will be a great boost.  When I had it up and going, the vocals definitely sounded better, and the guitar using rakarrack had a much warmer sound to it.  It almost sounded like it was going through a real tube amp..

Without further ado, I am posting the output of lsusb and cat /proc/interrupts..  I really want to get this fine tuned so I can record anywhere with just the laptop and the Presonus FP10/ART Tubefire 8 combo.

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0763:0199 Midiman Axiom 49
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0566:4002 Monterey International Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 413c:8149 Dell Computer Corp. 
Bus 001 Device 004: ID 0c45:63f8 Microdia Sonix Integrated Webcam
Bus 001 Device 002: ID 0424:2512 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sheehanje@john-studio:~$ cat /proc/interrupts 
            CPU0       CPU1       
   0:    2540971    1870640   IO-APIC-edge      timer
   1:       9781          2   IO-APIC-edge      i8042
   8:          1          0   IO-APIC-edge      rtc0
   9:         99       1379   IO-APIC-fasteoi   acpi
  12:        651         54   IO-APIC-edge      i8042
  16:       1228        744   IO-APIC-fasteoi   nvidia
  17:          1    2319329   IO-APIC-fasteoi   ohci1394
  18:          0          0   IO-APIC-fasteoi   mmc0
  19:          0          0   IO-APIC-fasteoi   yenta
  20:      20532          7   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb6
  21:         26         19   IO-APIC-fasteoi   uhci_hcd:usb4, uhci_hcd:usb7
  22:         43         65   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
  28:         54       6630   PCI-MSI-edge      eth0
  29:      47277       1379   PCI-MSI-edge      ahci
  30:        255        273   PCI-MSI-edge      hda_intel
 NMI:          0          0   Non-maskable interrupts
 LOC:     780360     981945   Local timer interrupts
 SPU:          0          0   Spurious interrupts
 PMI:          0          0   Performance monitoring interrupts
 PND:          0          0   Performance pending work
 RES:     151787      34269   Rescheduling interrupts
 CAL:        994         91   Function call interrupts
 TLB:        363        464   TLB shootdowns
 TRM:          0          0   Thermal event interrupts
 THR:          0          0   Threshold APIC interrupts
 MCE:          0          0   Machine check exceptions
 MCP:          7          7   Machine check polls
 ERR:          1
 MIS:          0

```One last note, I disabled wireless on the laptop as suggested elsewhere in the forums.  I also re-enabled compiz and it really doesn't seem to eat up too much CPU.  With jackd running connected to both devices, and compiz enabled, CPU is stable at less than 4% ..  That's with scaling set to 1.60Ghz.

John

---

### Post by sheehanje on 2010-09-04
Ok, problems again with running both the Presonus and the TubeFire, daisy chained.

I was stable for about 10 minutes then started getting:

JackAudioDriver::ProcessAsync: read error, skip cycle
JackFFADODriver::ffado_driver_wait - unhandled xrun
firewire ERR: wait status < 0! (= -1)


This just keeps repeating.  Everything looks like it is still patched in, but no sound once this start...  Going to try just the TubeFire 8 for a while to see what happens.

---

### Post by Pablo_F on 2010-09-04
Well done! 

The other day I helped a friend with a firewire audio device (edirol FA66 IIRC). He had a expresscard firewire card, from Texas Instruments. He had this setting in the conf file of rtirq:

RTIRQ_NAME_LIST="rtc0 ohci1394"

However, he had a few xruns so we checked the ffado wiki[1]:

and took a look at "cat /proc/interrupts", "lspci -nn" and the PCI ID list[2]


There was a "mmc0" or similar, that was the expresscard controller in our case.

In your case it could be both "yenta" and "mmc0". Try to figure out. Then edit again the rtirq conf file so the controller gains a higher priority than ohci1394, in RTIRQ_NAME_LIST. 

Maybe:

RTIRQ_NAME_LIST="rtc0 yenta ohci1394"

or

RTIRQ_NAME_LIST="rtc0 yenta mmc0 ohci1394"

I am not sure, try and see


Once the conf file saved, launch the script:

sudo /etc/init.d/rtirq start

And see/hear what happens. The script will be launched at boot, automagically. 


""""""""""""""""""""""""""""""""""""""""""""

If you want to check the priorities, use the ps command or htop.

I use htop on terminator (just another terminal emulator).

sudo apt-get install terminator htop
## Launch terminator
htop

## F2 --> Display options. Unmark "Hide kernel threads". F10 (done).  (This F10 does not work in gnome-terminal, that is why I use terminator and BTW it is cool to open new windows inside the main window).

## F6 --> Sort by PRI.


"""""""""""""""""""""""""""""""""""""""""

Regarding CPU freq scaling:

You don't want CPU freq scaling "ondemand". Keep it at a fixed value. If "performance" is too hot, try another mode. As long as freq does not change automatically, it is better than "ondemand".

I use a script, before starting jackd, with these lines:

sudo cpufreq-set -c 0 -g performance
sudo cpufreq-set -c 1 -g performance 

but I need that sudo cpufreq-set can be executed without a password. So I edited /etc/sudoers and allowed my user to run this command as a user command.

I strongly recommend this reading[3]

"""""""""""""""""""""""""""""""""""""""""""""

I did not know you can have two firewire cards working at the same time with jack, this is amazing. 

Cheers! Pablo

[1] [http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)

[2] [http://pciids.sourceforge.net/v2.2/pci.ids](http://pciids.sourceforge.net/v2.2/pci.ids)

[3] [http://www.linuxmusicians.com/viewtopic.php?f=27&t=844&p=4038&hilit=cpu+freq+scaling](http://www.linuxmusicians.com/viewtopic.php?f=27&t=844&p=4038&hilit=cpu+freq+scaling)

---

### Post by sheehanje on 2010-09-04
Thanks for the response Pablo.  I did some digging myself.  Seems mmc0 is the SD Card reader.  Yenta it seems is the cardbus controller.  I also saw how to give usb ports higher priority and decided to add the port my Axiom is plugged into a higher priority...
 
So I have:
 
"rtc yenta ohci1394 uhci_hcd:usb7"
 
as my priority chain....
 
Interesting stuff...
 
Unfortunately, I can't test too much tonight, but I will give it a good run through tomorrow.
 
I was thinking that if I can't get both devices to work well, I can get by with just using the tubefire 8 on the laptop, then using the FirePod on the desktop...  Maybe I'll fool around with netjack, because I'm a glutton for punishment.
 
Also, with the CPU scaling, I only have the options of 2.54GHz, 2.53GHz (go figure), 1.60Ghz and 800MHz..  So I will stick with 1.60Ghz.  Should be fine with dual core processor for what I need to do...  I will eventually build a dedicated rig.
 
I'll post my experiences with my tests tomorrow.

---

### Post by sheehanje on 2010-09-05
Ok, some quick results...
 
Loaded jackd with 64 Frames, 48KHz Sample, 2 Periods/Buffers ...  CPU Scaling set to 1.60GHz .. Only hooked up the ART Tubefire 8
 
Loaded what I absolutely need:  Ardour, Rakarrack, Patchage (I know not absolutely needed, but handy none the less)...
 
Setup the stereo tracks for 2 guitars, drums, bass, vocals...
 
0 xruns.
Loaded qsynth ... added a stereo track, and patched in my Axiom 49...
 
0 xruns.
 
enabled generic Midi as a control surface, patched in Axiom 49 to Ardour midi capture..
 
Was good until I started to assign the controls...  the VST part of Ardour crashed, and I got 1 xrun..
 
So I abbandoned ArdourVST in favor of plain old Ardour...  still had issues with the control surfaces...  Odd thing was that the keyboard would get distorted and stay distorted until I reloaded qsynth.  I would experience a xruns when restarting qsynth, but nothing major...
 
I decided to ditch the control surfaces and try again...  didn't experience xruns until I decided to push a little further and loaded hydrogen...  I got 13 xruns quickly, then it stabilized for a while, but the keyboard would again get distorted...
 
CPU didn't seem to be a problem, it was at 35% at most with everything running...
 
So, things are looking better in the fact I can run at 64 Frames with no xruns if I don't add MIDI into the equation...  With that in mind, I'm gonna focus tomorrow on tweaking qsynth/fluidsynth  .. I think that's where my troubles are pointing to right now.  I will also try easing back the frames to 128, which is where I usually have it set...
 
Finally, once I get a stable setup with the Tubefire, I will then add in the Presonus FP10 as a daisy chained device...

---

### Post by transmogrifox on 2010-09-05
> After the guys left, I did a little experimenting with the programs, and noticed rakarrack really eats up CPU with the convolution mod on. I disabled this, as it really didn't do too much for the sound.

This is sort of an aside to most of your post, but there are some things worth mention about Rakarrack and CPU usage just for the sake of anybody reading this post.  Effects to look out for are as follows:
Convolotron
Reverbtron
Harmonizer, Shifter, and pitch shifting modes in Sequence
Vocoder (not too bad, but still has a fair CPU load)

These can be helped immensely, and even brought into a reasonable amount by going to 
Settings->Preferences, Audio tab.

Here you can set "Downsample" parameter for each of the high CPU usage effects.  This will make a huge difference in CPU consumption in Rakarrack presets using any of the above effects. I suggest starting at 22000 for Reverbtron and Convolotron, then adjust from there as needed to suit response quality and CPU requirements.  I use 16000 on both for my laptop with results that are acceptable to me.  If you use distortion, you definitely need to set the Down quality parameter to "Fastest", which is actually "Fastest Sinc", which means...well basically it means it won't sound like the recording has gone through a cheap wireless telephone set.  Don't ever use Linear or Zero Order for the Down direction parameter if a distortion effect comes first in line.  You can read the help if you want to know more about why...or search the term "digital aliasing" with your search engine of choice.

Convolotron uses wav file impulse responses from various different amps, and you can actually load your own.  Most presets have the "Safe" switch enabled which reduces the convolution length to something almost useless.  If you're interested in amp cabinet modeling it may be worth  reading help and trying it the right way before dismissing it completely.  If you're not into amp cabinet modeling, then Convolotron is not for you and it is better to just disable it.  A Parametric EQ can go a long way in getting good frequency balance in the tone.

I'm not one to say "RTFM" so I won't frown on anybody who does not, but we Rakarrack devs have put a lot of work into documenting things, so the Help (F1) is really worthwhile to (at least) browse.  At the same time I realize many users aren't interested in much more than a few of the "meat 'n' potatoes" functions of the program, and then there is not much worth learning once you know what you need to know :)

I hope that tidbit will be of some use to somebody ;)  Cheers

---

### Post by AutoStatic on 2010-09-05
Hydrogen and Qsynth are two apps I have problems too with xrun-wise, especially at low latencies (I'm using practically the same JACK settings as you do). Try raising your latency a bit maybe.
```
firewire ERR: wait status < 0! (= -1)
```Could you also post the rest if possible? Did you check your FireWire cables? Quality cables could improve stability.

---

### Post by sheehanje on 2010-09-05
transmogrifox --
 
Thanks for the tips.  I just started using rakarrack as we just added a new guitarist.  I normally use the podxt live for myself, which does a good job.  The funny thing is, I'm really impressed with rakarrack.  I used an older version on my last setup and wasn't overly impressed.  However, in a pinch I had to set this up for the new guitarist because he showed up with just a noise gate and a really bad sounding distortion pedal...  I was blown away by the sound this thing can produce, and I got a really nice tone without too much tweaking..
 
So I will probably go through the help file as you suggested.  I did read about the downsampling already ....  Thing is, I've been so impressed with this version, I may want to try it for myself and either try and get two instances running (is that possible?), or just let the other guitarist use my line 6.  I will definately need to find some kind of MIDI controller to use for A)  Switching channels, and B) wah-wah/volume pedal...  Any suggestions there?
 
Autostatic,
 
   I am going to try a couple tests...  First with 64 Frames, 3 Periods for 4 msec, and the second with 128 Frames, 2 Periods for 5.33msec ...  5msec is usually the sweetspot for the human ear not to be able to detect the delay so that's what I'm shooting for...  I'll post my results tonight...

---

### Post by sheehanje on 2010-09-05
Ok...  The good news...
 
I have a stable recording platform...  64 Frames, 3 Periods, 48KHz.  
 
I can use my keyboard as a control surface.
 
With hydrogen, rakarrack, qsynth, patchage, ardour, jackd, compiz running, I am at ~35% CPU load, which is actually great considering I scaled back both cores to 1.6GHz from 2.54GHz ...
 
0 Drop Outs with this once everything is loaded.  I tested for a good half hour of recording..  I still get a drop out once in a while when first loading programs... especially qsynth.  
 
The bad news...
 
I still get some type of corruption with the keyboard and qsynth where I have to reload the fluidsynth engine to get the keyboard clean again.  The control surface piece doesn't seem to be affected, it's just qsynth.  So, I'm gonna focus on getting that piece resolved next...  Then maybe I'll get daring and try to use my FP10 in the mix as well..
 
John

---

### Post by AutoStatic on 2010-09-05
Good to hear that it works! Don't get your hopes up high you'll get Qsynth in line, I'm having the exact same issues. Maybe you could give the FluidSynth DSSI plugin a try?

---

### Post by transmogrifox on 2010-09-05
> **sheehanje said:**
> transmogrifox --
 

So I will probably go through the help file as you suggested.  I did read about the downsampling already ....  Thing is, I've been so impressed with this version, I may want to try it for myself and either try and get two instances running (is that possible?), or just let the other guitarist use my line 6.  I will definately need to find some kind of MIDI controller to use for A)  Switching channels, and B) wah-wah/volume pedal...  Any suggestions there?
 


Two instances running:  This is possible, and it's encouraged.  Each instance saves its own settings.  So for example, you can have a completely different appearance for the two different instances (diff bgnd image, colors, fonts...), and more importantly, different up/down sampling and jack connection settings. Of course, you would need to coordinate your presets and MIDI map between the instances so they work together with MIDI commands (or leave MIDI disconnected from one of the instances).  MIDI learn in recent development (0.6.0) stepped up a notch as you can right click a parameter to assign an incoming MIDI message.

Another thing I may note on the topic of multiple instances, is Guitarix works well as a complementary unit with Rakarrack.  Guitarix is more like a virtual amp and recent versions have an FX send/return loop in jack so you can use it with LADSPA plugins or something like Rakarrack, which is designed more like a virtual multi-FX board.  Guitarix has a much more advanced tube amp emulation system, from the tube models through tone stacks and internal EQ.  It is really a model of an amp.  The convolution engine is also more efficient...different trade-offs, but overall faster algorithm than what I have chosen for Rakarrack.

Channel switching & wahwah--I use the Behringer FCB1010.  It's excellent for everything but the expression pedals...the pedals do the job, but they're sort of low profile and have a short range of motion so it's really hard to use one as a volume pedal...it's pretty workable as a wah wah since I rarely try to stick it at a specific place.  It sure would have been nice if they had put an external exp pedal jack on this thing.

Anyway I'm glad the more recent version has been to your liking ;)  0.6.0 development has kept the momentum so it just keeps improving ;).

---

### Post by sheehanje on 2010-09-07
Autostatic,

   Still banging my head against the wall trying to get midi to properly work.  I tried the fluidsyth dssi with Rosegarden and it works for maybe 10 minutes, then just starts hanging the whole computer...

    I really haven't had the time to test every nuance yet, but when I get a day to just wrap my brain around it, I'm going to try and single out what is actually causing the problem.  It seems that as a control surface, it works fine.  Once fluidsynth gets invovled, problems start occurring.

transmogrifox,

    I haven't played around with rakarrack much this week as I'm first trying to stabilize my system with MIDI.  Thanks for the type with Guitarix, I'll have to try it out.  I'm assuming when I patch this stuff in, I will go rakarrack --> guitarix --> ardour --> system out... 

     Any plans of making this an insert that I can use with ardour?  Then I can record the clean signal and monitor/adjust the track in ardour...  I guess I could just be creative with routing and do the same thing and even record both the rakarrack and clean channel at the same time...

---

### Post by AutoStatic on 2010-09-07
> **sheehanje said:**
> Autostatic,

   Still banging my head against the wall trying to get midi to properly work.  I tried the fluidsyth dssi with Rosegarden and it works for maybe 10 minutes, then just starts hanging the whole computer...That's not good :( But does MIDI not work at all or is it just FluidSynth? There is a new release of FluidSynth available, FalkTX already packaged it for Lucid: [https://launchpad.net/~falk-t-j/+archive/lucid](https://launchpad.net/~falk-t-j/+archive/lucid)

---

### Post by sheehanje on 2010-09-07
Midi works, just not for long...  Now I'm having a bigger issue.

For some reason, out of the blue, I can't get my devices recognized...  It just hangs when I start jackd... 

I ran the following:

[CODE}sheehanje@john-studio:~$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.0.0
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x344fc000381f4de1  0x00344FC0  0x00000000   Linux - ohci1394  - 
[/CODE]

This is with the ART TubeFire 8 on, and that also just hangs.  I tried reseting everthing and I got nothing..  Just to check the unit, I hooked it up to my windows desktop, and it gets recognized fine..

I don't understand.  I didn't change anything or run updates...  This was working, the last problem I had was when I used the fluidsynth dssi and the system hung.

If I didn't like the Ardour/jackd combo so much, I would've quit by now :P

John

---

### Post by sheehanje on 2010-09-07
Ok, problem with the hang up solved.  The cable came loose from the laptop.  It's one of those mini jacks, so it's not the most stable connection...

MIDI is still giving me issues.  I have MIDI working great on a dell mini 9 netbook.  I think I may see if I can use netjack somehow to push MIDI over a wired connection.  Will be interesting to say the least...

John

---

### Post by Pablo_F on 2010-09-08
Hi, 

A shot in the dark because I suppose you have it right but make sure that rtc has the highest priority. In ubuntu karmic we had to change the default "rtc" to "rtc0" in the rtirq configuration file. 

Check with htop or

ps -eLo pid,cls,rtprio,cmd | grep -i "irq"

and look for irq/8

50 is bad. You need ninetysomething.

See:
[http://www.rncbc.org/drupal/node/107](http://www.rncbc.org/drupal/node/107)

There are some other tweaks that can help. See
 [http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki](http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki)

Some discussions in
[http://www.linuxmusicians.com/viewforum.php?f=27](http://www.linuxmusicians.com/viewforum.php?f=27)

Cheers! Pablo

---

### Post by AutoStatic on 2010-09-08
> **Pablo_F said:**
> Hi, 

A shot in the dark because I suppose you have it right but make sure that rtc has the highest priority. In ubuntu karmic we had to change the default "rtc" to "rtc0" in the rtirq configuration file.Not necessary anymore for Lucid, Lucid comes with the latest version of the rtirq script. But do check its prio, so if possible could you (sheehanje) post the outcome of **ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i -e "irq" -e "jack"**?
And some more info here: [http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)

---

### Post by sheehanje on 2010-09-08
I had that hang issue when doing ffado-test ListDevices ...  So maybe it's not the firewire cable after all...  Took 3 reboots of the laptop, power cycles on the TubeFire to get it recognized again.

Autostatic, following is the process list as you requested.  I also am pasting other relevant parts of my system info just in case something sticks out as wrong...

I just started to setup 10.04 studio on my Desktop, but I'm having ATI issues with that install.  I'm thinking maybe the firewire chip in this laptop just isn't cut out for this...

For your consumption:

```
sheehanje@john-studio:~$ lspci | grep 'FireWire'
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)

sheehanje@john-studio:~$ ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i -e "irq" -e "jack"
    4  FF     49  89   - [sirq-high/0]
    5  FF     49  89   - [sirq-timer/0]
    6  FF     49  89   - [sirq-net-tx/0]
    7  FF     49  89   - [sirq-net-rx/0]
    8  FF     49  89   - [sirq-block/0]
    9  FF     49  89   - [sirq-block-iopo]
   10  FF     49  89   - [sirq-tasklet/0]
   11  FF     49  89   - [sirq-sched/0]
   12  FF     49  89   - [sirq-hrtimer/0]
   13  FF     49  89   - [sirq-rcu/0]
   18  FF     49  89   - [sirq-high/1]
   19  FF     49  89   - [sirq-timer/1]
   20  FF     49  89   - [sirq-net-tx/1]
   21  FF     49  89   - [sirq-net-rx/1]
   22  FF     49  89   - [sirq-block/1]
   23  FF     49  89   - [sirq-block-iopo]
   24  FF     49  89   - [sirq-tasklet/1]
   25  FF     49  89   - [sirq-sched/1]
   26  FF     49  89   - [sirq-hrtimer/1]
   27  FF     49  89   - [sirq-rcu/1]
   45  FF     50  90   - [irq/9-acpi]
   74  FF     50  90   - [irq/22-ehci_hcd]
   75  FF     50  90   - [irq/20-ehci_hcd]
   76  FF     50  90   - [irq/20-uhci_hcd]
   77  FF     84 124   - [irq/21-uhci_hcd]
   78  FF     50  90   - [irq/22-uhci_hcd]
   79  FF     50  90   - [irq/20-uhci_hcd]
   80  FF     83 123   - [irq/21-uhci_hcd]
   81  FF     50  90   - [irq/22-uhci_hcd]
   82  FF     50  90   - [irq/12-i8042]
   83  FF     50  90   - [irq/1-i8042]
   84  FF     90 130   - [irq/8-rtc0]
  393  FF     50  90   - [irq/18-mmc0]
  395  FF     86 126   - [irq/17-ohci1394]
  397  FF     50  90   - [irq/29-ahci]
  930  FF     50  90   - [irq/28-eth0]
  960  FF     88 128   - [irq/19-yenta]
 1059  FF     50  90   - [irq/30-hda_inte]
 1420  FF     50  90   - [irq/16-nvidia]
 2032  TS      -  19   0 grep --color=auto -i -e irq -e jack


sheehanje@john-studio:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0763:0199 Midiman Axiom 49
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0566:4002 Monterey International Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 413c:8149 Dell Computer Corp. 
Bus 001 Device 004: ID 0c45:63f8 Microdia Sonix Integrated Webcam
Bus 001 Device 002: ID 0424:2512 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sheehanje@john-studio:~$ uname -a
Linux john-studio 2.6.33-29-realtime #1-Ubuntu SMP PREEMPT RT Wed Aug 4 17:22:37 UTC 2010 x86_64 GNU/Linux

sheehanje@john-studio:~$ cat /proc/interrupts 
            CPU0       CPU1       
   0:     401700     418072   IO-APIC-edge      timer
   1:        710          5   IO-APIC-edge      i8042
   8:          0          1   IO-APIC-edge      rtc0
   9:        104        405   IO-APIC-fasteoi   acpi
  12:        920         55   IO-APIC-edge      i8042
  16:        281        136   IO-APIC-fasteoi   nvidia
  17:         36         38   IO-APIC-fasteoi   ohci1394
  18:          0          0   IO-APIC-fasteoi   mmc0
  19:          0          0   IO-APIC-fasteoi   yenta
  20:      13781          3   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb6
  21:         25          8   IO-APIC-fasteoi   uhci_hcd:usb4, uhci_hcd:usb7
  22:         38         66   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
  28:         25        832   PCI-MSI-edge      eth0
  29:      10628       1330   PCI-MSI-edge      ahci
  30:        243        315   PCI-MSI-edge      hda_intel
 NMI:          0          0   Non-maskable interrupts
 LOC:      79385      68792   Local timer interrupts
 SPU:          0          0   Spurious interrupts
 PMI:          0          0   Performance monitoring interrupts
 PND:          0          0   Performance pending work
 RES:       2341       3023   Rescheduling interrupts
 CAL:       1014         68   Function call interrupts
 TLB:        253        253   TLB shootdowns
 TRM:          0          0   Thermal event interrupts
 THR:          0          0   Threshold APIC interrupts
 MCE:          0          0   Machine check exceptions
 MCP:          2          2   Machine check polls
 ERR:          1
 MIS:          0


sheehanje@john-studio:~$ ls /dev/raw1394 -l
crw-rw---- 1 root audio 171, 0 2010-09-08 21:50 /dev/raw1394


sheehanje@john-studio:~$ groups
sheehanje adm dialout fax cdrom floppy tape audio video plugdev fuse lpadmin netdev admin sambashare

sheehanje@john-studio:~$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.0.0
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x344fc000381f4de1  0x00344FC0  0x00000000   Linux - ohci1394  - 
   1       0x0016050058826308  0x00001605  0x00010067   ART - ART Firewire 
no message buffer overruns

sheehanje@john-studio:~$ lsmod
Module                  Size  Used by
binfmt_misc             8024  1 
ppdev                   6876  0 
snd_hda_codec_idt      63285  1 
joydev                 11017  0 
snd_hda_intel          26333  0 
snd_hda_codec          90834  2 snd_hda_codec_idt,snd_hda_intel
snd_usb_audio          94822  0 
snd_seq_dummy           1782  0 
snd_pcm_oss            41576  0 
snd_mixer_oss          17467  1 snd_pcm_oss
snd_pcm                87203  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_hwdep               7056  2 snd_hda_codec,snd_usb_audio
snd_usb_lib            20415  1 snd_usb_audio
snd_seq_oss            31659  0 
snd_seq_midi            6092  0 
snd_rawmidi            23533  2 snd_usb_lib,snd_seq_midi
lp                     11001  0 
snd_seq_midi_event      7367  2 snd_seq_oss,snd_seq_midi
video                  21370  0 
uvcvideo               63273  0 
psmouse                61024  0 
videodev               42506  1 uvcvideo
pcmcia                 35124  0 
parport                37802  2 ppdev,lp
v4l1_compat            16385  2 uvcvideo,videodev
snd_seq                58020  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
output                  2535  1 video
serio_raw               5143  0 
nvidia              11087375  44 
yenta_socket           23093  1 
rsrc_nonstatic         10304  1 yenta_socket
dv1394                 18990  0 
raw1394                25376  0 
pcmcia_core            39995  3 pcmcia,yenta_socket,rsrc_nonstatic
v4l2_compat_ioctl32    11113  1 videodev
snd_timer              23980  2 snd_pcm,snd_seq
dell_laptop             2922  0 
dell_wmi                3348  0 
intel_agp              28865  0 
dcdbas                  7110  1 dell_laptop
snd_seq_device          6850  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    72910  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_usb_lib,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          8820  2 snd_hda_intel,snd_pcm
soundcore               8625  1 snd
usbhid                 41274  0 
hid                    84004  1 usbhid
ohci1394               31283  1 dv1394
sdhci_pci               7549  0 
sdhci                  17868  1 sdhci_pci
ricoh_mmc               3480  0 
led_class               3764  1 sdhci
ieee1394               96276  3 dv1394,raw1394,ohci1394
ahci                   37936  2 
e1000e                139692  0 
```

---

### Post by AutoStatic on 2010-09-09
> **sheehanje said:**
> I'm thinking maybe the firewire chip in this laptop just isn't cut out for this...You could be right:

> **sheehanje said:**
> ```
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
```[http://subversion.ffado.org/wiki/HostControllers](http://subversion.ffado.org/wiki/HostControllers)

> Seems to not work for most people (Exceptions - Scott reports 100% success with FFADO-2-RC1 UBS 8.10 on Jan 14th 2009. 100% success with FFADO-2-RC1 in Fedora 10. Pedro reports good performance (128x3) with ffado-svn (as of Nov 2009), kernel 2.6.31.6-rt19/Debian testing on a Lenovo T400 laptop and cpufreq governor set to performance):

```
FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (prog-if 10 [OHCI])
```

So your controller doesn't seem to work for most people. You could try my FFADO svn packages though, maybe they yield better results: [https://launchpad.net/~autostatic/+archive/ffado](https://launchpad.net/~autostatic/+archive/ffado)

The rest looks good as far as I can see.

---

### Post by sheehanje on 2010-09-09
I'll give it a shot.  I have the band coming over tonight...
 
I tried installing Ubuntu 10.04 Studio on my desktop, but my video shuts off on boot (monitor goes into powersave mode)...  Don't know what that's all about...  While I understand that once I get a stable system, it will be rock solid, I can understand why a lot of people give up on this endeavour.  It can be frustrating to say the least...  I'm not a studio person, I'm just a guitarist for a band who got tasked with home recording..  Not that I mind too much, it's a good thing to learn.  It's just getting to the part where I can actually sit down an learn ardour, midi, mastering, etc. without having to worry about firewire, irqs, and what hardware will play nice ;) 
 
I will keep pressing on though, and eventually I will build a rig that will do what I need it to.  Tonight, I can hopefully get just the tubefire working and skip the midi, at least for recording rehearsal.
 
Thanks for all your help so far with this...

---

### Post by sheehanje on 2010-09-09
> **AutoStatic said:**
> You could be right:

[http://subversion.ffado.org/wiki/HostControllers](http://subversion.ffado.org/wiki/HostControllers)



So your controller doesn't seem to work for most people. You could try my FFADO svn packages though, maybe they yield better results: [https://launchpad.net/~autostatic/+archive/ffado]("https://launchpad.net/%7Eautostatic/+archive/ffado")

The rest looks good as far as I can see.


I tried ffado from your repository and got worse results.  xruns galore, especially with MIDI, plus the MIDI was very distorted....  I think I'm giving up on the laptop, hopefully a newer version will fix my issues, but for now it's a bit fruitless..

Now I just gotta figure out why my desktop install is black screening on boot.

---

### Post by sheehanje on 2010-09-09
Ok...  Did a little experimentation...

I decided to load jack/qsynth/patchage on a mini laptop that I have... 

Plugged the axiom into the netbook, loaded netjack with the alsa driver, qsynth, patchage --  patched the axiom to qsynth...

started jack on my laptop, then used jack_netsource

What a surprise... It works... and simple at that...

Now granted, I'm not pushing midi data through, just the sound, but it's glorious sound ....  no distortion, no dropouts, just pure playing...

I will play tomorrow to see if I can get midi coming over, if just for the control surface...

I actually like this idea, because now I can have my keyboard anywhere.  The mini is easy enough to plop anywhere with the keyboard, then I just need cat 5 to get it to my laptop, either through a switch, or with a crossover.

I knew there was a reason I was sticking with this setup... All frustration aside, there's always more than one way to skin a cat with this stuff.

---

### Post by sheehanje on 2010-09-15
I think I finally have a stable system.

I tried KXStudio for a while, and while I like a lot of the ideas, I just can't get used to KDE.  Espeically the fact that it doesn't look as good at higher resolutions, and I'm not too fond of the CPU Scaling utility compared to Gnome.

So, I reinstalled Ubuntu Studio, and got looking at the [Wiki at LinuxMusicians]("http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki=723baafebcfe3d1bb85a69b45019822d") and I found a little piece I was missing to stabilize MIDI...

From the Wiki:

> **hardware timers**

     MIDI sequencers and such will benefit from being able to use hardware timers like the [real-time clock]("http://en.wikipedia.org/wiki/Real-time_clock") (/dev/rtc) or the [High Precision Event Timer]("http://en.wikipedia.org/wiki/High_Precision_Event_Timer") (/dev/hpet). Make sure the 'audio' group has read permissions on it. 
   A simple 'chown' might not be persistent across reboots - to make the  change last, create a new 40-timer-permissions.rules file in  /etc/udev/rules.d with the following lines:  
 KERNEL=="rtc0", GROUP="audio" KERNEL=="hpet", GROUP="audio"    … and reboot. See also: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/306458](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/306458) 
   This step is verified by realTimeConfigQuickScan.pl. 
  


So a fresh install of Ubuntu Studio, and following what I've learned in this thread along with the Wiki and Linux Musicians has me a stable, portable solution for recording.

I will note that I still haven't worked on getting the Tubefire 8 and Presonus FP10 working in tandem via daisy chain.  I haven't even attempted it again since getting the base system stable has been my goal.  So what I have right working now:

Art Tube Fire 8, M-Audio Axiom 49 over firewire to Dell E6500 Laptop.

I am running:  JackD, Patchage, Qsynth, rakarrackX2, Ardour

System is stable.  ~30% of both CPU cores are utilized, running them at 1.6Ghz

I still haven't tried a few other apps I want to dig into (Rosegarden, Hydrogen), I will post my results this weekend as I will be playing around all week.  I'm just happy I have what I need to record the band straight up this week.

---

### Post by AutoStatic on 2010-09-15
Cool! Weird that I didn't mention this udev rule earlier, I modified it like 2 weeks ago in the LinuxMusicians Wiki and added the hpet part.
Great that it works! Unfortunately forumite trulan doesn't seem to come here that often anymore, I think he could've helped you setting up daisy-chained devices. It does work on the command-line or not? Then it should work in QjackCtl too.

---

### Post by sheehanje on 2010-09-15
I think I posted on it earlier in the thread. 

I can get them recognized using the guid through the command line, but I was having major lockups and xrun issues while using both of them.

I haven't tried since tweaking my setup, so I will give it another go.

---

### Post by sheehanje on 2010-09-16
Well, seems I can get both of them working at the same time.  I have to use the command line to do it...
 
```

jackd -P70 -dfirewire "guid:0x1234567890;guid:0x123456790" -r48000 -p128 -n2

```
 
That does the trick.  
 
If I add the guid's to qjackctl it wants to append another -d before the "guid" line:
 
```

jackd -P70 -dfirewire -d"guid:0x123456790;guid:0x123456890" -r48000 -p128 -n2

```
 
I was able to record audio from both interfaces without much of a problem.  Tomorrow night is band practice, so I may try and put it through it's paces with a full load.
 
So far the results look promising though.  I recorded 6 stereo audio tracks, with qsynth and rakarrack going.  I also had all my control surfaces binded the way I want them (hopefully they save, cause thats always been touch and go with Ardour for me)..
 
 No xruns (except when loading qsynth, once loaded it settles down). CPU maxed out at about 20% ...  That's with it scaled down to 1.6Ghz per core.
 
I'm afraid to turn anything off now...

---

### Post by AutoStatic on 2010-09-16
You have to enter the guids in QjackCtl without the quotes: [http://ubuntuforums.org/showpost.php?p=9097463&postcount=28](http://ubuntuforums.org/showpost.php?p=9097463&postcount=28)

---

### Post by sheehanje on 2010-09-16
Even without the quotes it is failing for me.  It does not want the second '-d'  ...
 
Something must have changed with ffado and how it wants the arguments...

---

### Post by AutoStatic on 2010-09-16
Forumite trulan is using 10.04 in that example afaics (JACK 0.118 and FFADO 2.0.0). Weird stuff because the second -d does work in his case apparently. Weird stuff. Unfortunately I don't have two Firewire devices to daisychain otherwise I would've loved to help out.
Good luck with the recordings!

---

### Post by War Tribe on 2013-01-24
I'm running the 64 bit version of Ubuntu Studio on my laptop and I downloaded banshee for my media player and banshee will not automatically detect and rip CDs even though I have the options set in banshee. Also, I went into the system settings manager and set the option for Ubuntu Studio to automatically mount removable media and it still does nothing. What else am I missing?

---

### Post by Sylos on 2013-01-25
> **War Tribe said:**
> I'm running the 64 bit version of Ubuntu Studio on my laptop and I downloaded banshee for my media player and banshee will not automatically detect and rip CDs even though I have the options set in banshee. Also, I went into the system settings manager and set the option for Ubuntu Studio to automatically mount removable media and it still does nothing. What else am I missing?

I dont know anything about your specific issue but I suggest that you open a new thread specific to your problem. Your more likely to get the help you need from an appropriately titled new thread. And this thread will soon be closed for necromancy....

3.... 2..... 1......

---

