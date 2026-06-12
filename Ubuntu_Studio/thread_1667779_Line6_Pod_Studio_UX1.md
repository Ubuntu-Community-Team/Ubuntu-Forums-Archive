---
title: "Line6 Pod Studio UX1"
date: 2011-01-15
forum: Ubuntu Studio
---

### Post by xwindowsfan on 2011-01-15
i run ubuntu studio lucid. i have Line 6 POD driver source and Line 6 POD modules for Linux installed according to synaptic. the UX1 is not detected by ubuntu. i have been unable to find info on how to troubleshoot this. any suggestions? thanks

---

### Post by gordintoronto on 2011-01-15
What does lsusb say?

---

### Post by xwindowsfan on 2011-01-16
it shows the device as line6, Inc. perhaps i should have said the pod is not being detected by sound preferences. i am also trying to connect the pod through the analog outs with a 1/4" to 1/8" y cable to the line-in on my sound card but no dice.

---

### Post by gordintoronto on 2011-01-16
> **xwindowsfan said:**
> i am also trying to connect the pod through the analog outs with a 1/4" to 1/8" y cable to the line-in on my sound card but no dice.

Can you record from a mic plugged into your sound card?  Are you using Audacity to try to record from line-in?

---

### Post by xwindowsfan on 2011-01-17
i am rather new to doing guitar with a pc. i have not tested if i can record with a mic but i can connect guitar directly to the line-in and get audio through amp software. maybe i have the wrong idea about what the pod studio does. i get the impression that it isolates what you are recording to the application. i believe i am also able to "monitor" what i am recording. right now i would just like to see that i can monitor the output and have yet to test the recording aspect of it.

the set up is basic enough. i assume i could use the usb for recording and the analog outs for sound. simultaneously or one at a time. of course it cant be tested if linux does not detect it. i think i might try m-audio as i hear it has better compatibility with linux. thanks

---

### Post by maghoxfr on 2011-01-17
> **xwindowsfan said:**
> i am rather new to doing guitar with a pc. i have not tested if i can record with a mic but i can connect guitar directly to the line-in and get audio through amp software. maybe i have the wrong idea about what the pod studio does. i get the impression that it isolates what you are recording to the application. i believe i am also able to "monitor" what i am recording. right now i would just like to see that i can monitor the output and have yet to test the recording aspect of it.

the set up is basic enough. i assume i could use the usb for recording and the analog outs for sound. simultaneously or one at a time. of course it cant be tested if linux does not detect it. i think i might try m-audio as i hear it has better compatibility with linux. thanks

I don't understand what you want to do but, if you have the UX1 and it's not detected then you can't record anything. Maybe [this]("http://ubuntuforums.org/showthread.php?t=1163608") helps (?)
You also have to make sure you are using jack and not pulseaudio. Then in qjackctl choose the input and output devices (this being your audio interface if it's detected) then route the signals according to what you want to do, for this you can use patchage for a easier visual way or qjackctl's conections window.

---

### Post by xwindowsfan on 2011-01-18
> **maghoxfr said:**
> I don't understand what you want to do but, if you have the UX1 and it's not detected then you can't record anything. Maybe [this]("http://ubuntuforums.org/showthread.php?t=1163608") helps (?)
You also have to make sure you are using jack and not pulseaudio. Then in qjackctl choose the input and output devices (this being your audio interface if it's detected) then route the signals according to what you want to do, for this you can use patchage for a easier visual way or qjackctl's conections window.

i want to set it up to record but i also need to hear what i am doing. i have my sound card running through my home stereo via s/pdif. i would also like to use pod farm. i have determined so far the imput for the usb through jackd is plughw but all i get is distortion. i have tried checking realtime and hw monitor.

---

### Post by AutoStatic on 2011-01-18
Could you post the output of **cat /proc/asound/cards** with the UX1 connected?

---

### Post by sgx on 2011-01-18
> **xwindowsfan said:**
> i run ubuntu studio lucid. i have Line 6 POD driver source and Line 6 POD modules for Linux installed according to synaptic. the UX1 is not detected by ubuntu. i have been unable to find info on how to troubleshoot this. any suggestions? thanks

I would get a Fender Mustang usb digital guitar amp, $99, or less on sale,
works by simple usb in most any linux, no source or driver hunting. Its wonderful sound can be sent to rakarrack, guitarix, jack-rack etc
to defy limitations.

It has 24 presets, 16 savable without a computer, but its Fuse software
editor is well done, allowing deep edit/creations on windows/mac only, so far, since Msoft Silverlight and .net framework are its dependencies.
It may be the best bargain out there for guitarists. 

The Pod Farm software plugin might run in Reaper in Puppy Studio 3.2,
there is a PODxt sighting in one of the screengrabs at the link, Reaper
is preinstalled in the 390 meg iso for a liveCD to try.

qjackctl setup page:

Input Device >
Output Device >

click the > to see if your UX1 is listed. Usb hubs will defeat this,
some usb ports on computers are less than perfect. Get the amp! ;)

---

### Post by xwindowsfan on 2011-01-18
> **AutoStatic said:**
> Could you post the output of **cat /proc/asound/cards** with the UX1 connected?

 0 [CMI8788        ]: CMI8788 - C-Media CMI8788
                      C-Media Oxygen HD Audio (rev 2) at 0xbc00, irq 16


> **sgx said:**
> I would get a Fender Mustang usb digital guitar amp, $99, or less on sale,
works by simple usb in most any linux, no source or driver hunting. Its wonderful sound can be sent to rakarrack, guitarix, jack-rack etc
to defy limitations.

It has 24 presets, 16 savable without a computer, but its Fuse software
editor is well done, allowing deep edit/creations on windows/mac only, so far, since Msoft Silverlight and .net framework are its dependencies.
It may be the best bargain out there for guitarists. 

The Pod Farm software plugin might run in Reaper in Puppy Studio 3.2,
there is a PODxt sighting in one of the screengrabs at the link, Reaper
is preinstalled in the 390 meg iso for a liveCD to try.

qjackctl setup page:

Input Device >
Output Device >

click the > to see if your UX1 is listed. Usb hubs will defeat this,
some usb ports on computers are less than perfect. Get the amp! ;)

i may consider alternatives eventually but for now i will stick with this type of interface. 
nice reference though. 
the > does not specify the ux1. "lsusb" does show line6, inc. 

thank you for all the replies.

---

### Post by AutoStatic on 2011-01-18
> **xwindowsfan said:**
> ```
0 [CMI8788        ]: CMI8788 - C-Media CMI8788
                      C-Media Oxygen HD Audio (rev 2) at 0xbc00, irq 16
```No Line6 device there. Try **sudo modprobe line6usb** on the command line, reconnect your UX1 and try a **cat /proc/asound/cards** again.

---

### Post by xwindowsfan on 2011-01-18
> **AutoStatic said:**
> No Line6 device there. Try **sudo modprobe line6usb** on the command line, reconnect your UX1 and try a **cat /proc/asound/cards** again.

sudo modprobe line6usb
FATAL: Error inserting line6usb (/lib/modules/2.6.32-27-generic/kernel/sound/usb/line6usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by AutoStatic on 2011-01-18
> **xwindowsfan said:**
> sudo modprobe line6usb
FATAL: Error inserting line6usb (/lib/modules/2.6.32-27-generic/kernel/sound/usb/line6usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)Looks like a bug, got the same result here. Could you try booting with an older kernel if you still have older kernels installed and try **sudo modprobe line6usb** again?

---

### Post by Zimmer on 2011-01-18
You might want to consider VirtualBox to run a Virtual Win machine for your Line6 hardware.
It is what I have resorted to in order to use a PodXTLive and Variax with Gearbox and Variax Workshop software..

---

### Post by xwindowsfan on 2011-01-18
> **AutoStatic said:**
> Looks like a bug, got the same result here. Could you try booting with an older kernel if you still have older kernels installed and try **sudo modprobe line6usb** again?

im current with linux kernel 2.6.32-27
im on linux kernel 2.6.32-26-generic right now
it looks like sudo modprobe line6usb was successful as the prompt returned
with no output
**cat /proc/asound/cards  **still only shows the c-media card
still not showing under > in jackd
still only static

---

### Post by AutoStatic on 2011-01-18
> **xwindowsfan said:**
> im on linux kernel 2.6.32-26-generic
it looks like sudo modprobe line6usb was successful as the prompt returned
with no outputThat's expected behaviour.
> **xwindowsfan said:**
> **cat /proc/asound/cards  **still only shows the c-media card
still not showing under > in jackd
still only staticYou might have to unplug the UX1 and plug it back in.

I've filed a bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/704542](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/704542)

---

### Post by xwindowsfan on 2011-01-18
> **AutoStatic said:**
> That's expected behaviour.
You might have to unplug the UX1 and plug it back in.

I've filed a bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/704542](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/704542)

same results all around.

thanks for the bug report

---

### Post by AutoStatic on 2011-01-19
xwindowsfan, do you have any alsa-backports packages installed by any chance? I'm now at my machine at the office and over here the line6usb kernel module loads fine.

---

### Post by xwindowsfan on 2011-01-19
i had upgraded alsa to 1.0.23 using a script. 
i know it was dirty and cant remember which website. 
it utilized downloads from the official alsa site. 
i also cant remember why i upgraded it. 
thats the only thing ive done with alsa.
i just checked with synaptic and no backports are installed.

---

### Post by xwindowsfan on 2011-01-19
on a side note this is all good for the usb connection but what about the analog outs through a y cable to the line-in on my sound card?
shoul'nt that be picked up just like it is when i plug the guitar directly into the line-in, which works.

---

### Post by sgx on 2011-01-19
Hi, a proper line out level should be received by any line input.
A guitar needs some pre-amp boost to match line level for best results. Some gear has a headphone out, that is a boosted line level, and the quality
of these vary, some add  more noise than others. The headphone/line hybrid on the Mustang Amp is very clean, and the volume level is adjustable by its knob on the amp. Its usb volume must be adjusted by software. Perhaps the ux-1 is similar. 

Running your line6 software in standalone mode, rather than
using pod-farm as a vst plugin, may result in routing differences,
you'll have to read the docs. If you plug in headphones to the
ux-1, is it dry in plugi-in mode, and effected in standalone mode?
In Plugin mode, you would likely host pod-farm plug-in in Reaper, using wineasio, and hear the fx from the soundcard output.

If using wineasio, use winecfg, and make sure alsa is chosen in the audio tab, instead of jackd.
Cheers

---

### Post by xwindowsfan on 2011-01-20
could the fact that i installed the line6 drivers from cd with wine interfere with the linux drivers?
i have also tried the line in instead of guitar in on the pod, no luck
im also trying to get the ux1 working on fedora 14 but no success and little info available.
thanks so far
maybe amazon will take it back with out the box...

---

### Post by sgx on 2011-01-20
You can rename the .wine folder to wineOLD or whatever,
then run winecfg to get a fresh .wine folder, and set things up,
reinstall all the linux line6 items, and hope it works.

I would recommend getting the puppy studio live CD, as
it is largely based on ubuntu repos, and has all this stuff
preconfigured, RT kernel, wine, Reaper for vsts, 

[http://www.murga-linux.com/puppy/viewtopic.php?t=60483](http://www.murga-linux.com/puppy/viewtopic.php?t=60483)

hw1: PODxt-live  is shown listed in qjackctl in the screengrabs.
The 380 meg iso burns to a bootable live CD, so testing won't install
anything without your permission. If you like it, you can save settings
in a .sfs file at shutdown, prompted step by step.

Cheers

---

### Post by sgx on 2011-01-20
Another possibility, if you dual-boot with windows, and you can locate where the windows installer put all the line6 items, you can use symbolic links to matching locations in wine, these locations are listed in a winecfg tab. This works for Native Instruments apps, which get scattered in many locations in a windows partition. Should be a log file somewhere.
Cheers

---

### Post by xwindowsfan on 2011-01-20
> **sgx said:**
> You can rename the .wine folder to wineOLD or whatever,
then run winecfg to get a fresh .wine folder, and set things up,
reinstall all the linux line6 items, and hope it works.

I would recommend getting the puppy studio live CD, as
it is largely based on ubuntu repos, and has all this stuff
preconfigured, RT kernel, wine, Reaper for vsts, 

[http://www.murga-linux.com/puppy/viewtopic.php?t=60483](http://www.murga-linux.com/puppy/viewtopic.php?t=60483)

hw1: PODxt-live  is shown listed in qjackctl in the screengrabs.
The 380 meg iso burns to a bootable live CD, so testing won't install
anything without your permission. If you like it, you can save settings
in a .sfs file at shutdown, prompted step by step.

Cheers

i dont want to reset wine as i have alot of programs and configs under wine i dont want to redo. 
however i went ahead and uninstalled podfarm and the line6 drivers under wine unist. which i installed before the synaptic package.
i also manualy installed the sorceforge drive following simular instructions as
 
[http://www.ubuntugeek.com/howto-install-line6-guitarport-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-line6-guitarport-in-ubuntu.html)

but i dont know how to uninstall that.

no luck so far:popcorn:

---

### Post by xwindowsfan on 2011-01-20
i could not delete, sorry

---

### Post by AutoStatic on 2011-01-20
> **xwindowsfan said:**
> i had upgraded alsa to 1.0.23 using a script.That's where your issues come from probably. And these kind of scripts usually don't come with an uninstall option so it's kind of a hassle to reinstate the system as it was before the update. You could try reinstalling the **linux-image-generic** package. If that doesn't help could you then post the content or location of the script you used?

---

### Post by xwindowsfan on 2011-01-20
i reinstalled the package with synaptic but did not reboot, no luck
i believe the instructions i used were exactly the same as ubuntugeek.

---

### Post by sgx on 2011-01-21
You can rename .wine, as I mentioned, reinstall wine, and manually copy the things you like from the renamed folder. For instance, my entire
Steinberg/VstPlugins folder has been copied after many system upgrades,
wine upgrades, and new distros using the existing /home partition.
In the drive_c and Program Files folder, I just copy back non-linux items that I had installed previously. This keeps both the newer wine elements, and my personal software installs intact.

If you are lucky, line6 installer will keep its files in just 2 or 3 locations.

I always save my .wine folders to dvd and hard-disk for convenience

a lot of system changes do require a reboot, some just a logout/login

usb was never carved instone, nor mastered by Msoft/apple, so try the
ux-1 in all ports, especially with no other usb devices installed.

Cheers

---

### Post by xwindowsfan on 2011-01-21
i think the UX1 is on its way back to amazon.
i need an alternative.
can i get a dry signal from the fender mustang through usb? is it suitable for recording? is it compatible with popular amp modeling programs through wine?
i see the m-audio fast track usb 2 has only usb as output. is it compatible with modeling software.
the most important thing for me is to be able to record but also hear what im doing at the same time or separately. especially when run through a modeling program.
thanks for all the help.

---

### Post by maghoxfr on 2011-01-21
> **xwindowsfan said:**
> i think the UX1 is on its way back to amazon.
i need an alternative.
can i get a dry signal from the fender mustang through usb? is it suitable for recording? is it compatible with popular amp modeling programs through wine?
i see the m-audio fast track usb 2 has only usb as output. is it compatible with modeling software.
the most important thing for me is to be able to record but also hear what im doing at the same time or separately. especially when run through a modeling program.
thanks for all the help.

Some interfaces allow direct monitoring, that way you're going to listen to your dry input signal (that is unprocessed). Others allow you to hear the procesed signal coming from the computer. Be sure to checik if the interface runs on linux before purchasing it to avoid waste of time and headaches.

[http://www.linux-sound.org/hardware.html](http://www.linux-sound.org/hardware.html)

---

### Post by sgx on 2011-01-21
> **xwindowsfan said:**
> i think the UX1 is on its way back to amazon.
i need an alternative.
can i get a dry signal from the fender mustang through usb? is it suitable for recording? is it compatible with popular amp modeling programs through wine?
i see the m-audio fast track usb 2 has only usb as output. is it compatible with modeling software.
the most important thing for me is to be able to record but also hear what im doing at the same time or separately. especially when run through a modeling program.
thanks for all the help.
The Mustang lets you save presets, in my case one of them is clean, and the other 23 represent a range of tones and fx suited to what I like. It is great for recording by usb, no drivers or firmware, as its a Mac/windows class compliant usb device. You can also use the hybrid headphone/line output if it suits your needs, its very clean. Using the amp with rakarrack, Calf Plugins, jack-rack, and Guitarix is fabulous, just turn the amps preset knob, and you get 24 different versions of each rakarrack or other fx! 

Out of the box, you can modify presets 9-24, using the amp models and fx
from the amp controls. There are a couple dozen demos on youtube, so take a listen, keeping in mind the extra versatility of using it in linux. 

The Fuse software has been updated, so you would download the latest version, rather than the one on the DVD, (which also includes a light version of Fender Amplitube, which runs in linux via reaper/wineasio, to further your sonic options) and you can use Fuse in windows/mac for access to more fx and amp models, and edit and resave the first 8 presets as desired. The gui and options are well done, even bias/SAG options on a couple of the amp models, and some superior fx options. On screen, they are drawn as either stompboxes before the amp model, or rack devices, if placed after the model, with plenty of options and controls.

You can sometimes find a 10% or 15% gear coupons, so the $99 price (or $199 for one with a larger speaker) can get a bit lower.The smaller version is surprisingly loud, although I usually am using it in software.

I don't work for Fender, but this is a no-brainer, for linux guitarists ;)

I have used the amp with Guitar Rig, several versions of Amplitube, Shred, and LePou plugins, since it is hardware, it sends its 24 presets wherever you desire.

In case you're a high-gain maniac, LePou does the worlds best high gain amp modeling, so that great output can be achieved inside Reaper/wineasio, then routed into a linux fx chain, with qjackctl. Doesn't get any better than that!

Cheers

---

### Post by sgx on 2011-01-21
:p I'm a dinosaur! A whole new lineup of Mustang amps appeared :D
I really must get out of the studio more often ;)

[http://www.musiciansfriend.com/navigation?q=mustang+amp](http://www.musiciansfriend.com/navigation?q=mustang+amp)

---

### Post by xwindowsfan on 2011-01-22
im not a real big fender fan but i am considering it.
how about the marshall sound design mg10cd line out to a mixer if nessessary to the line in on my sound card.?\\:D/

---

### Post by AutoStatic on 2011-01-22
What's wrong with the UX1? I'd stick with that one and get it to work. Did you try with a LiveCD?

---

### Post by xwindowsfan on 2011-01-22
its a done deal.sorry man
i gave up on the ux1.
again thanks to everybody for the help.
linux vs hardware compatibility, i guess hardware wins this one...

---

### Post by sgx on 2011-01-22
> **xwindowsfan said:**
> im not a real big fender fan but i am considering it.
how about the marshall sound design mg10cd line out to a mixer if nessessary to the line in on my sound card.?\\:D/
Mustang is not a tube amp, so if you preferred other tube amps over Fender, its not really in play, sound wise. To me, the simplicity of having 24 instantly available versions of any sound the digital-guitar universe can supply (and more variations from nudging the fx knobs) is an irresistible force. And that it simply connects by usb or line, is
icing on the cake. Looks like the spendier versions have 100 presets, instead of 24, for those who feel the need.

The line-out on any gear should be tested for clarity and signal strength,
since such standards are not implemented equally, or enforced in court. If you can test gear side by side, its always the best way. If shops are
in the distance, make a fun overnighter trip, it will protect your future sanity and your budget ;)
Cheers

---

### Post by ghstridr on 2011-01-23
> **xwindowsfan said:**
> i run ubuntu studio lucid. i have Line 6 POD driver source and Line 6 POD modules for Linux installed according to synaptic. the UX1 is not detected by ubuntu. i have been unable to find info on how to troubleshoot this. any suggestions? thanks

Can you point me to where you found the source for the drivers? I have a UX2 and am quite familiar with linux and would like to try this.  I might be able to help.

---

### Post by AutoStatic on 2011-01-23
**sudo apt-get install line6-usb-source**
The drivers are in the standard repository and the line6usb kernel module is part of the standard kernel. So no need to download the source somewhere and compile it yourself. Then a **sudo modprobe line6usb** should load them, unless you upgraded ALSA, either by having installed a backports package or if you upgraded it manually.

---

### Post by xwindowsfan on 2011-01-23
> **AutoStatic said:**
> What's wrong with the UX1? I'd stick with that one and get it to work. Did you try with a LiveCD?

i tried it with ubuntu-10.10-desktop-i386.iso, the "try ubuntu" option.

i added repository 
deb [http://*ubuntu*]("http://%3Ci%3Eubuntu%3C/i%3E")*.*[mirror.pnl.gov/ubuntu/]("http://mirror.pnl.gov/ubuntu//pool/universe/l/line6-usb/line6-usb-source_0.8.0+svn551-1_all.deb") maverick main universe

i installed it through ubuntu softaware center.

i ran sudo modprobe line6usb it went through.

the ux1 did not show under cat /proc/asound/cardsit did show under lsusb

i unpluged and plugged back in the usb.

i tried it with jackd and rakarrack plughw0 and default as input.

[LEFT]Nothing. i could swear when i plugged the cord into the instrument plug in on the ux1 i could hear it through the speakers but other wise not even a sqeek.

on a side note i failed to mention, the ux1 did show under input options under 'wave' in vsthost but when i set it to dsline6ux1, vsthost froze.
i downloaded a fresh copy of vsthost and it does the same, seems it kept the settings. now when i try to use it ,it just freezes. thank you
[/LEFT]

---

### Post by xwindowsfan on 2011-01-23
> **sgx said:**
> Mustang is not a tube amp, so if you preferred other tube amps over Fender, its not really in play, sound wise. To me, the simplicity of having 24 instantly available versions of any sound the digital-guitar universe can supply (and more variations from nudging the fx knobs) is an irresistible force. And that it simply connects by usb or line, is
icing on the cake. Looks like the spendier versions have 100 presets, instead of 24, for those who feel the need.

The line-out on any gear should be tested for clarity and signal strength,
since such standards are not implemented equally, or enforced in court. If you can test gear side by side, its always the best way. If shops are
in the distance, make a fun overnighter trip, it will protect your future sanity and your budget ;)
Cheers

can i just ask, am i am to mute the output to the amp speaker when i send it through the usb so the only output is from the system.

i dont think i could deal with clean comming from the amp and distorted comming from pc speakers

i guess i could always pull the speaker forks off.

thanks

---

### Post by sgx on 2011-01-23
:p just turn the volume knob down to silence the speaker ;) the usb is totally internal, hence its pristine quality, you can't use the volume knob on the amp to adjust that usb circuit, so you would use your linux mixer, or volume controls on rakarrack, guitarix, or if a DAW like Reaper is used in wine, its track volume controls, and/or volumes in Guitar Rig, 
Amplitube, LePou etc 

If you choose to connect the headphone/line out to your soundcard
line-in, then you >would use the volume knob on the amp to set the
input gain, and to silence the speaker if desired, plug in an earbud, or a dummy/adaptor jack.

The amp case is a closed back custom design, to maximize output,
its pretty amazing considering its not heavy. The 24 stock presets
are based on 8 fender amp models, in three groups of 8, colored LEDs
indicate which group you are in, green yellow red, and in the last two groups, you can change fx/eq, and saving the new version is just a button push. 4 more amp models, and more fx can be accessed using the Fuse software in win/mac. and saving the first 8 presets when edited is possible. I got used to drawing the Fuse controls for my
favorites in a notebook, and jot down ampsim combos I like to use them on.

Its nice to play using headphones at night, without waking anyone, and
it has a line in for mp3/CD player input, just for practice or live output, its not affected by the fx, or sent by the usb.

Cheers :)

---

### Post by xwindowsfan on 2011-03-02
i went with Yamaha's Audiogram 6 and am very happy with it.

thanks again for all the feedback.

:guitar:

---

### Post by sgx on 2011-03-03
Hey, that Yamaha is some nice looking gear! First time I hear of it,
so thanks for posting your results. I would be careful when using the buttons to change mic input levels when the unit is powered on, as some competing products have fried the circuits when doing that. So to be safe, make changes before the unit is powered up.

Cheers :)

---

### Post by xwindowsfan on 2011-03-03
of course my technical level is that of the end-user, so it's mostly opinion.

the unit is usb powered, so it's in an "always-on" state.

i have not had any problems so far adjusting all levels including turning on and off the phantom power button, while playing. no heavy use so far but at least an hr or two at a time.

one dinosaur to another, now you've got me paranoid i'm going to burn out my active pickups with the phantom power. i've got the guitar plugged into a direct box and the mic out plugged into the audiogram channel 1

but let me say again the unit is very soild and stable, unlike the pod studio that feels like an empty plastic shell. in the good old fashioned sense of it I would say "she can take it". but its always better safe then sorry.

short of failure, just as a side note: the setup cranks.

---

### Post by fabioleitao on 2011-06-29
Sorry for the UP. I have a Line6 UX1 for a couple of years now, and I have been really frustrated for the lack of linux support (with many complains to line6 and not even a decent response).

Since Natty, it has been working fine from the standard installation, or kind of, both in 32 and 64 bits... 

But I can only get it to input from the XLR MIC (what is good for vocal or acoustic guitar, and my skype sessions never sounded better) but Pulse/Alsa and any program that relies on them (such as Audacity) does not even show the Instrument P10 input as alternative, so I cannot get the electrical guitar to record in Ubuntu yet

Is there any adjust I can try to force it to change the input from hw 1:0 to 1:1 (or whatever combination the Instrument input may be)?

---

### Post by Element0s on 2011-07-18
Hey folks, I'm a total Ubuntu/Linux newbie and I'm trying to get my Line 6 UX1 to run as an input. I installed the drivers as directed by an older thread and it seemed to go smoothly, it shows up in my hardware list under sound preferences and it's listed under both "Input" and "Output". Output works fine, but Input has nothing. I've tried using my guitar and I've tried using my condensor mic, but it's not picking up any signal. I'm also pretty clueless when it comes to using the "Jack" program.

If anyone can offer some advice and tips to a total newbie that's only slightly computer-savvy, I'd really appreciate it!

---

### Post by M1szcz on 2012-08-18
> **Element0s said:**
> Hey folks, I'm a total Ubuntu/Linux newbie and I'm trying to get my Line 6 UX1 to run as an input. I installed the drivers as directed by an older thread and it seemed to go smoothly, it shows up in my hardware list under sound preferences and it's listed under both "Input" and "Output". Output works fine, but Input has nothing. I've tried using my guitar and I've tried using my condensor mic, but it's not picking up any signal. I'm also pretty clueless when it comes to using the "Jack" program.

If anyone can offer some advice and tips to a total newbie that's only slightly computer-savvy, I'd really appreciate it!


I found solution for that problem- you need to use alsamixer command(of course if you use alsa) next press f6 and chose your Line6 Card and then on the another screen in the midle there is an option "PCM  Capture Source". Chose there "Instrument". You should be now able to hear you guitar... or whatever your instrument is...

ps. i know this topic is old - but problem is acctual for many of POD Linux users.
ps2. sorry for my english :)

---

### Post by smartboyhw on 2012-08-19
> **M1szcz said:**
> I found solution for that problem- you need to use alsamixer command(of course if you use alsa) next press f6 and chose your Line6 Card and then on the another screen in the midle there is an option "PCM Capture Source". Chose there "Instrument". You should be now able to hear you guitar... or whatever your instrument is...
 
ps. i know this topic is old - but problem is acctual for many of POD Linux users.
ps2. sorry for my english :)
 
Thanks for your solution. It helps everybody:)
 
Regards,
Howard Chan
Ubuntu Studio Team Member at [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by sgx on 2012-08-21
> **M1szcz said:**
> I found solution

ps. i know this topic is old - but problem is actual for many of POD Linux users.
ps2. sorry for my english :)

The more good solutions are shared, the more likely that next year
someone will google this, and soon be enjoying a line6 product,
or be able to look for a bargain, with confidence it will be useful.
Cheers :popcorn:

---

### Post by 7Artist on 2013-08-04
> **sgx said:**
> The more good solutions are shared, the more likely that next year
someone will google this, and soon be enjoying a line6 product,
or be able to look for a bargain, with confidence it will be useful.
Cheers :popcorn:

Yep, i google this and im now here. Nice to have my UX2 on ubuntu :)
Thanks dudes!!!!!

---

