---
title: "just installed studio and no audio production applications..."
date: 2010-05-30
forum: Ubuntu Studio
---

### Post by iochinome on 2010-05-30
Hello all,

I just installed ubuntu studio 10.04 on my gateway PC this morning, intending to do audio production with it. during the installation process, it asked me what suite of applications i would like to have installed, and i selected the audio version. now that it is installed, however, there is not a single audio production application except for sound recorder! I do not have a connection to the internet with this because of other bugs, namely the inability for it to recognize the wired connection. how can i install programs like lmms that should already be on here in the first place?

thanks!

---

### Post by Scott L on 2010-05-30
I have a few suggestions for you:

networking workaround:
[http://ubuntuforums.org/showthread.php?t=1479788](http://ubuntuforums.org/showthread.php?t=1479788)

Once that is up, use synaptic and install the ubuntustudio-audio metapackage.

If you feel very confident that you picked the 'install audio packages' from the installer, then you should file a bug in launchpad.

ScottL

---

### Post by RobertoRecordo on 2010-05-30
> **iochinome said:**
> Hello all,
 
I just installed ubuntu studio 10.04 >snip< now there is not a single audio production application except for sound recorder! 
thanks!
 
I had a flawless install, but no audio applicaitons! I selected "audio cremation and editing suite" and saw no errors. 
 
I am a baby beginner with ubuntu. If there is a bug, how will I find out what to do?

---

### Post by sgx on 2010-05-30
here you go,

sudo apt-get install zynaddsubfx qjackctl hydrogen audacity timemachine rakarrack


Copy/paste that in a terminal when online, that command download and install these, and will maybe ask to add needed extras, so say yes.

When done, you'll have 

a recorder  -timemachine
an editor -audacity
a great synth -zynaddsubfx
a great drum machine/sample sequencer -hydrogen
a great multi-fx processor -rakarrack

a gui to connect them all -qjackctl 

The 4 most recent pages in this forum contain lots of details about
setting this up, and links to more.

A talented hard-working musician could literally have a career using just these, and samples for the drum machine!
Cheers

---

### Post by RobertoRecordo on 2010-05-31
Great! I was able to install as you indicated. I do appreciate the help.

Now, how do I give feedback that will help the developers understand what went wrong? Is there an install log? I saved the terminal session - it looked like a partial install had occured 
 ~~Unpacking audacity-data (from .../audacity-data_1.3.12-2_all.deb) ...
Selecting previously deselected package libflac++6.
Unpacking libflac++6 (from .../libflac++6_1.2.1-2build2_amd64.deb) ...
Selecting previously deselected package libid3tag0.
Unpacking libid3tag0 (from .../libid3tag0_0.15.1b-10build2_amd64.deb) ...
Selecting previously deselected package libmad0.
~~~~it goes on and on ~~~~

---

### Post by sgx on 2010-05-31
> **RobertoRecordo said:**
> Great! I was able to install as you indicated. I do appreciate the help.

Now, how do I give feedback that will help the developers understand what went wrong? Is there an install log? I saved the terminal session - it looked like a partial install had occured 
 ~~Unpacking audacity-data (from .../audacity-data_1.3.12-2_all.deb) ...
Selecting previously deselected package libflac++6.
Unpacking libflac++6 (from .../libflac++6_1.2.1-2build2_amd64.deb) ...
Selecting previously deselected package libid3tag0.
Unpacking libid3tag0 (from .../libid3tag0_0.15.1b-10build2_amd64.deb) ...
Selecting previously deselected package libmad0.
~~~~it goes on and on ~~~~
I downloaded  two distros friday, one of the downloads was bad, even though the exact same size as the one that replaced it that was good.
It needed to be perfect, as in verify the .iso by the md5sum.

With a download install, lots of things can go wrong. Check in /usr/bin for things that are part of ubuntu studio, if you find any, try to start them ny name from a terminal.  fluidsynth  is a good bet, maybe ardour2, just type the name at a prompt to start them.

If they are there, but not in your menus, then that is a good bug to file.
If they are not there, try the install again, and choose to see the details on the synaptic screen, to see that things get off to a good start.

Cheers

---

### Post by zettberlin on 2010-05-31
If you want to do some more but very basic audio-editing you may want to install these also:

Ardour (HD-Recording-suite)
Rosegarden (score-setting and MIDI-sequencer)

and anything related to LV2 and LADSPA (Plugin-collections, hosts etc)

browse the available packages with synaptic:

gksu synaptic


you need to start jack with qjackctl as the first step in every session. Jack gives you precise audio-stream handling and the possibility to connect running apps with each other, making the Linux audio system the most flexible one to find. Many important apps rely on jack, so I really absolutely recommend to get familiar with it.

good luck ;-)

---

### Post by DedMoroz on 2010-06-09
Ardour is excellent. Its very much like ProTools if you are familiar with that.

I also like LMMS a lot... Linux Multi Media Studio.

Agreed you need the JACK controls "qjackctl" installed and running.

---

