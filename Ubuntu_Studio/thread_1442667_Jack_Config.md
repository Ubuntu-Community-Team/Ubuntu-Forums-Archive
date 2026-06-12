---
title: "Jack Config"
date: 2010-03-30
forum: Ubuntu Studio
---

### Post by mdrake36 on 2010-03-30
1.Jack is noisy through my sound card. ATI IXP rev 0 with AD1981B Sound Card Notebook style:popcorn:note: if Ardour GTK is idle then then card is as quiet as a baby
I have tried several setups( like every combo)
note: jack is cool on my other boxes like es1371 or C-media both PCI cards:D

2. How do I effectively use the Patch bay and multiple scripts at start up in qjackctl?
here is my scheme;)

Hexter via QMIDIarp and a Keyboard controller.

I can get the setup working great but have to reconfigure on every use.

---

### Post by DerickX on 2010-03-30
2. [http://www.rncbc.org/drupal/node/76](http://www.rncbc.org/drupal/node/76)

Here you find some info how to setup jack properly
[http://www.openstudioproductions.org/tutorials](http://www.openstudioproductions.org/tutorials)

---

### Post by mdrake36 on 2010-03-30
thank you. this is what i needed. wow cool:p

---

### Post by Scott L on 2010-04-03
You may also find these helpful:

[https://help.ubuntu.com/community/What%20is%20JACK](https://help.ubuntu.com/community/What%20is%20JACK)

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

---

### Post by sgx on 2010-04-05
Hi, hexter should be able to fit in recallable sessions based on lashd

linux
audio
session
handler

[http://www.nongnu.org/lash/lash-manual.html](http://www.nongnu.org/lash/lash-manual.html)

so having hexter, hydrogen and zynaddsubfx reload in your desired configuration should work, as well as any apps with dssi support. lashd/liblash2 may be
installed already, or at least an easy find in the repositories.

and  for potential hexter newcomers, its a flat Yamaha DX7 that can load the vast ocean of sysex files from here:

[http://www.maths.abdn.ac.uk/~bensondj/html/dx7.html#patches](http://www.maths.abdn.ac.uk/~bensondj/html/dx7.html#patches)

Cheers

---

