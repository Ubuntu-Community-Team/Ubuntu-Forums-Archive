---
title: "Got Emagic Unitor/AMT8 and Echo Mia running under Ubuntu Studio"
date: 2009-05-12
forum: Ubuntu Studio
---

### Post by BrianK on 2009-05-12
Because I've not found much in the way of documentation for getting the AMT8 running & only one or two posts on the Echo Mia, I figure I'll post here for all future googlers:

Both devices are controlled by ALSA.

The vanilla ALSA that comes with Ubuntu Studio has support for the AMT, but not the Mia.  Compiling ALSA to work with the mia (at least in the docs I found online) breaks the AMT.  The solution is pretty simple in practice, but finding the right combo with zero documentation is difficult, sooooo....

download the latest firmware (optional) & driver for alsa ( [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) ).  For the record, I'm using 1.0.19 at the moment.  Whatever you use, be consistent, so if you download everything from the alsa project, be sure you get highest common version number.

**Compilation**

firmware is a simple 

untar
./configure
make
sudo make install


driver is:

untar
./configure --with-cards=mia,serialmidi,usb-audio
make -j2
sudo make install

you can use -j<number of procs> to make the compile faster. 

Be sure to watch the output for the ./configure step in both instances.  Quite often, something important will be missing, configure will tell you, but it will get lost in the sea of output, so you don't notice it, don't correct it & wonder why something isn't working.  If you see a "checking for XXX.... no" - go install XXX (especially XXX-dev if it's available) and rerun ./configure before moving on.

To be honest, I don't know if you need the last two --with-cards option args, but you don't want any other options.  The other docs I found had something like "--with-oss" and "--with-sequencer" - neither of which worked with the AMT8.

There's probably a more friendly, dpkg-build way to get the compiled source into your package list which will allow it to be upgraded... if someone else wants to add that, feel free.  With this method, you'll be responsible for your own alsa updates.

After compilation, **reboot**.

**Configuration**

For the Mia:
I have an "echo mixer" application.  I can't recall if I compiled that or if it's a package (I'll try to verify & post a correction when I get home, but I'll probably forget ;)).  Once you reboot, keep in mind that your sound is TURNED ALL THE WAY DOWN BY DEFAULT & must be turned up before you hear anything.  Simply open the echo mixer & turn up the volume.  There's a way to do it from the command line, but I don't remember what that is... I'm sure googling will help (or someone else can chime in).

For the AMT8:
verify it works by using the command:

amidi -l

that should give a list of the MIDI devices on your system.  It should be obvious that you have an AMT8 attached.  If you see no output, then your AMT is not recognized.  amidi is one of the alsa midi tools.  If you don't have it, search synaptic for name and description of "amidi" (it will be in the description, I think the package is called something else... again, I'll update when I get home if I remember)

I haven't exhaustively tested this, but I know that under Windows, my AMT would not work unless it was powered on before the computer was powered on.  This may be true in Linux as well, so be sure to turn it on first.

Now, in Rosegarden, the AMT8 is listed as one of the midi devices & controls all my external synths as expected.

Feel free to move this post if it's better served elsewhere.


Now you can enjoy the wonder of 80's technology & hear it too!

---

### Post by hungryforbread on 2013-03-11
If you're still around, could you tell me just how you got the AMT8 to work? Is there a driver I can get somewhere? What do I need to do?

I have a Unitor8 mk1 (serial port interface) and a fresh install of Ubuntu Studio 12.04. For those unfamiliar, the Unitor 8 and the AMT8 are basically two different versions of the same interface. Mine is the older mk1 without USB connection. 

While I have figured out that the serial port is active, the system does not see the Unitor. I am brand new to Linux as a refugee from Windows. I don't know how to even install a driver, though I haven't been able to find one for the Unitor either- only confusing and esoteric how-tos elsewhere on the web about serial midi.

I have read some people saying that the Unitor got recognized immediately with zero effort. I'm afraid this has not been my experience.

My Echo Gina20 PCI soundcard did get picked up right away though.

The puter is an old Pentium 4 system, socket 478, with 2gb of memory and an Asus P4SDX motherboard.

If anyone can offer suggestions on what to do next, I'm open to your input.

Many thanks.

---

### Post by wildmanne39 on 2013-03-14
Old thread closed!

---

