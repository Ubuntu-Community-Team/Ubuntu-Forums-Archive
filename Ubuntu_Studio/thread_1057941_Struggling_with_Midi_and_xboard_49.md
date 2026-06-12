---
title: "Struggling with Midi and xboard 49"
date: 2009-02-02
forum: Ubuntu Studio
---

### Post by leftishmiddle on 2009-02-02
Hi everyone! I am a relative linux newbie, so be gentle with me...
I have been using ubuntu for the last year, and have generally been very happy with it... but have struggled getting some audio-visual stuff going.

I have an Asus p5k-vm motherboard, and am using onboard sound and graphics (but would be willing to add hardware if it would help). I have managed to get Jack working (although not reliably), but would really like to get working with my Xboard49. However i have not been able to get Midi working at all... Is this because I don't have hardware support for it?

Also, would it make it any easier if i switched to Ubuntu Studio? Would I lose any files if i did install it?

Any advice would be very welcome!

---

### Post by sgx on 2009-02-02
> **leftishmiddle said:**
> Hi everyone! I am a relative linux newbie, so be gentle with me...
I have been using ubuntu for the last year, and have generally been very happy with it... but have struggled getting some audio-visual stuff going.

I have an Asus p5k-vm motherboard, and am using onboard sound and graphics (but would be willing to add hardware if it would help). I have managed to get Jack working (although not reliably), but would really like to get working with my Xboard49. However i have not been able to get Midi working at all... Is this because I don't have hardware support for it?

Also, would it make it any easier if i switched to Ubuntu Studio? Would I lose any files if i did install it?

Any advice would be very welcome!
Hi, if  you unplug it, reboot, then start jackd/qjackctl, and see if anything shows up. Xboards can be fiddly  with various OS usb implementations. If you have a desktop pc, an m-audio 24/96 pci soundcard
is around $80, and well worth it, working great in linux. This has real non-usb midi ports, cable those to the xboards real midi ports, and you may have better luck.
Ubuntu Studio 8.04 is a good choice, and can be set up in synaptic as a
repository, but a fresh install might help you more, and quicker, since you are new, and the hard work has been done by those who created that distro. As an excellent interim, alternative, you can purchase a Proteus 2000 era rackmount synth, or any other midi hardware synth/sound module, and control that directly from the xboard, annd record the modules output with ardour, audacity, or other well suppoted recording tool, or external recording gear. 
The software that ships with the xboard, Proteus VX or
ProteusX etc, probably won't work in linux, I have tried, and hope someone else has better skills/luck, so hang on to windows if you want or need that software!
Post details of your system, as others will need details for more in depth help :)

---

### Post by leftishmiddle on 2009-02-03
Hi! Thanks for all the advice... I had got that far - in fact, Jack recognises my keyboard in the 'Alsa' tab of my Jack 'connect' dialogue... but i can't make the keyboard control anything... and even if i could, i've had no joy in midi playback anyway.

If i were to get a new audio interface, i'd like it to have at least a jack input, if not xlr... preferrably external (but i know that usb interfaces generally have problems with linux).

If i install Ubuntu Studio in full, will it wipe my existing files?

---

### Post by thorgal on 2009-02-03
if your keyboard shows up in the ALSA tab of qjackctl, it has nothing to do with jackd itself. The Qjackctl's primary developer added the ALSA tab as a convenience since at the time he created the app, the jack MIDI interface was not ready. What you see in the ALSA tab is the ALSA handling of your MIDI layer. You need now to connect a MIDI intrument (soft synth like amsynth or zynaddsubfx or fluidsynth or ... there are tns of them) to your keyboard. Let's try amsynth:

apt-get it
fire it up

it should now show up in the ALSA tab as well. It has a MIDI in socket (right hand side window of the qjackctl ALSA tab). Connect your keyboard output socket (left hand side window of the ALSA tab).

Now go to the audio tab. amsynth must have audio outputs that you connect to your system outputs (same thing here: sockets on the left hand side sends audio to the sockets on the right hand side which will process the signal).

It's very easy in essence:

keyboard is MIDI controller: sends MIDI events to soft synth which will map these incoming MIDI events to sound samples / other type of audio signal, which you redirect to your speakers, or a recorder, or an effect filter, whatever jack client that can receive audio in fact.

Qjackctl may change in the future when pure jackd MIDI handling is mature (it's already quite advanced and is better to use but many apps will only interface with the ALSA midi layer so jackd still needs some time to replace it completely)

---

### Post by sgx on 2009-02-03
> **leftishmiddle said:**
> Hi! Thanks for all the advice... I had got that far - in fact, Jack recognises my keyboard in the 'Alsa' tab of my Jack 'connect' dialogue... but i can't make the keyboard control anything... and even if i could, i've had no joy in midi playback anyway.

If i were to get a new audio interface, i'd like it to have at least a jack input, if not xlr... preferrably external (but i know that usb interfaces generally have problems with linux).

If i install Ubuntu Studio in full, will it wipe my existing files?

In qjackctl, select the items to connect in the left and right sides of the interface, then press the 'Connect' buttom, bottom left of the screen. A line should appear between any two connected items.

A full install of Ubuntu Studio (or any distro) will follow the partition
choices you make, the default will almost always wipe out everything with
a newly formatted root partition. ( mount point =  /  )  If you made a separate /home partition, and install a new  linux distro, and your data is all in /home/yourusername, you can choose custom partioning, and opt to not reformat /home, saving your   data, and keeping many configs intact, like eyecandy, and email settings etc.The root partition must be repartitioned, unless you absolutely expertly KNOW exactly a good reason not to. You can add all the contents of Ubuntu studio, as you go, keeping your current system as is. For music, the RT-kernel from 8.04, wine, wineasio, zynaddsubfx, fluidsynth, and its qsynth gui, the FluidR3    soundfont, (not related to, but used in fluidsynth) ardour2, and audacity, will get you maximum sound-making power, with fewest downloads via synaptic.
Wine and wineasio are not needed unless you have windoze vsti to use with Reaper, energyXT, Cantabile, or other working vst host.
Cheers

---

### Post by leftishmiddle on 2009-02-03
Thanks for all the help guys - you're really helping me get my head around this! I've now managed to get some of these things going (half my problem was my lack of understanding of the basic workings of Jack)... I have now got midi playing through timidity for the first time (are some of the other software midi options better than timidity?)... but still no joy with my xboard.

I have tried connecting the xboard to both timidity and straight to ZynAddSubFX (which i am using to sest this stuff), and haven't managed to get it to control anything. I think it's worth noting that I had similar problems trying to get it to work with a Mac (which was surprising), so i have a vague suspicion that the Keyboard isn't working properly. But all the lights and dials and everything are functioning, and hte computer is recognising its presence, so i'd be very surprised.

Any thoughts on getting the keyboard to 'talk' to the software?

Thanks!

---

### Post by sgx on 2009-02-07
> **leftishmiddle said:**
> Thanks for all the help guys - you're really helping me get my head around this! I've now managed to get some of these things going (half my problem was my lack of understanding of the basic workings of Jack)... I have now got midi playing through timidity for the first time (are some of the other software midi options better than timidity?)... but still no joy with my xboard.

I have tried connecting the xboard to both timidity and straight to ZynAddSubFX (which i am using to sest this stuff), and haven't managed to get it to control anything. I think it's worth noting that I had similar problems trying to get it to work with a Mac (which was surprising), so i have a vague suspicion that the Keyboard isn't working properly. But all the lights and dials and everything are functioning, and hte computer is recognising its presence, so i'd be very surprised.

Any thoughts on getting the keyboard to 'talk' to the software?

Thanks!
Hi, there will be a set procedure in the manual, for assigning xboard knobs to vst software functions, aimed at windows software, and typical windows vsts. Zyn likely won't function that way. Your best bet will be to install wine, and wineasio using synaptic. Then run these commands

wineprefixcreate
regsvr32 wineasio.dll
winecfg
These will in order, create a .wine folder  in your /home/user folder,
2. make wineasio viable
3. open a config panel  with several panes, in the Audio section, choose alsa in the very first box.
Now  download Reaper to your /home/user folder, and install it using this command:

wine reaper255-install.exe
Choose your home/user folder to install it in. Install all but the RTAS version.

In Reaper Options --> Preferences --> Device, choose asio as the driver, and choose wineasio as your 'device',
and just below that in MIDI Devices, enable the xboard as your midi hardware, and anything else that shows up!

Now use or get some windows vsts, if you have a computerMusicMagazine dvd, install Genesis, Zebra CM, Wusikstation, and CMFuzz to start, if not,
[www.ugoaudio.com](www.ugoaudio.com) has Texture 1.2, and Rez 2 for free, excellent keepers!

Start jack and qjackctl normally, then start reaper with

wine REAPER/reaper.exe

If the Reaper demo song plays, find the FX buttons in each track window,
click on one, and see the gui for the vst on that track appears, but docked, and you can see options to add, remove, or undock it. Choose to remove it, then add one of the vsts you have or downloaded. You may have to have Reaper rescan your /home/user folder, and add it to its list of paths, this is done in the
Options --> Preferences --> VST panel  A typical entry would be
/home/user/.wine/drive_c/Program Files/Steinberg/VstPlugins
That is a default most synths work fine from, if they fail to work when installed in
/home/user  Each path is separated by a ; in that Reaper preferences page.

Now, you have an arena where you can hope to assign xboard controls to software  synths. Dig out the procedure from the manual, and give it a try. Filter Cut-off and Resonance might be good ones to try assigning  xboard knobs to, keep low volume for safe starters 
Also wine command lines with spaces like 'Program Files', need to be filled in with a *    Program*Files   -many windows software installers have several gaps to fill that way!
Be patient, and keep posting results!

---

