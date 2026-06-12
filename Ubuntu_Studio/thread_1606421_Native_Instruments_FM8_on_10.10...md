---
title: "Native Instruments FM8 on 10.10?.."
date: 2010-10-26
forum: Ubuntu Studio
---

### Post by ansionnachcliste on 2010-10-26
Hey guys,

I'm just wondering if it's possible to run FM8 on Ubuntu 10.10? I've got Wine but haven't had much luck with using it with other programs.

Sometimes Wine doesnt read the CD.

So is it possible to install FM8 on Ubuntu?

Thanks for any help guys.

---

### Post by sgx on 2010-10-27
> **ansionnachcliste said:**
> Hey guys,

I'm just wondering if it's possible to run FM8 on Ubuntu 10.10? I've got Wine but haven't had much luck with using it with other programs.

Sometimes Wine doesnt read the CD.

So is it possible to install FM8 on Ubuntu?

Thanks for any help guys.
I have the demo working here, usually the NI installer will work in
wine, as well as their Service Center app. If its already installed on a windows dual-boot partition, you can also copy all the folders to their wine equivalents. If you have not yet purchased it, and you do original music, you'll find zynaddsubfx and its extra sounds collections, and 16 layers, is a more flexible and better sounding instrument. There is a great free synth called augur

[http://rekkerd.org/patches/plug-in/augur/](http://rekkerd.org/patches/plug-in/augur/)

a good soundset for it is here:

[http://ann.sounds.free.fr/](http://ann.sounds.free.fr/)

Cobalt is an excellent instrument for $35, these work fine using
Reaper to host them in wine, with the wineasio driver.

Phasex is also a little known, but excellent linux instrument, and
has great sound potential.
Cheers

---

### Post by ansionnachcliste on 2010-10-27
Sweet man, just checked that out.

Edit: I was also wondering if you could help me set up the outputs for FM8 on Ubuntu?
I don't get an option to select ALSA but get one for DS default.

Thanks.

---

### Post by sgx on 2010-10-28
Hi, wineasio will be needed, after installing it with synaptic, run the command

regsvr32 wineasio.dll

You can run FM8 as a standalone app with wine, 

wine /home/user/.wine/drive_c/Program*Files/Native*Instruments/FM8/FM8.exe


The FM8 File menu has a midi options entry, and there you can
choose you midi keyboard.

If you have a vst host app like reaper, there is a little more
basic configuration to do, in reaper, the Options -->Preferences menu
has areas for Device (choose wineasio), midi Devices, and VST
The vst path you need is

/home/user/.wine/drive_c/Program Files/Steinberg/VstPlugins 

and reaper needs to scan that folder for vsts after they are installed.

The fst command and qjackctl can be used to run FM8 and many other vst plugins.

fst /home/user/.wine/drive_c/Program*Files/Steinberg/VstPlugins/FM8.dll

Once the instrument appears,
use the qjackctl gui to connect it. Press the Connect button, and in both the audio and alsa tabs, connect the instrument, audio for your soundcard, alsa for your midi keyboard.

There is a gui for fst called festige which can help. And an app called
patchage is an alternative for qjackctl. Qtracktor is a sequencer app that
may be good to use.
Cheers
Also, the Ni Komplete 7 Elements includes many excellent Reaktor synths, and a
$60 voucher which could obtain the excellent Prizm Reaktor synth, very good
value for $99 or less.

---

