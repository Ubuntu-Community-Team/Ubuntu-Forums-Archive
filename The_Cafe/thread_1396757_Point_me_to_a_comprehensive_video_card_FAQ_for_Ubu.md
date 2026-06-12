---
title: "Point me to a comprehensive video card FAQ for Ubuntu"
date: 2010-02-02
forum: The Cafe
---

### Post by Luke has no name on 2010-02-02
Is there a definite better video driver for a given video card? For example, if I run X1250 integrated ATI graphics, which driver performs better? What about an HD 3870? HD 4850? X800?

And nVidia? Are there open-source nVidia drivers for Karmic? What about these fabled "nouveau" drivers coming in Lucid? For a given video card, what driver should I use?

Also, use more common names (stop calling them R500/R600/Evergreen, refer to them as "HD 3xxx").

I might sound kind of ornery about this, but I hear people talking about ATI drivers a TON and I never hear what driver is better for a given card. Is there a database or table that exists to give me the info I request, or should someone make it? 

Finally, how can one tell from the command line what video card model they have?

---

### Post by cariboo on 2010-02-02
I stopped using and recommending ATI video cards years ago, as at the time they couldn't make a decent Windows driver, let alone one for Linux. It seems they have finally learned how to create good Windows drivers, but they seem to be in the same situation for Linux drivers, they may mature in an other 3-4 years. 

That being said, I do have an ATI 330M/340M/350M graphics chipset in my laptop, it uses whatever the default driver is in Karmic, I get full affects with no video tearing when watching youtube full screen.

I also have 2 systems that use Nvidia graphics adapters, one with a builtin  Geforce 6150SE chip set using the 185.16 closed source drivers, the other an Nvidia 8400GS using the closed source 190.53 drivers. Again everything works as it should.

My fourth system based on an Intel Atom 320 with 945 graphics chipset is being used as a media center pc running xbmc on top of LXDE, I'm really happy with the performance when running full screen video. It uses the i915 open source driver. This system is connected to a 32" Samsung HD LCD TV.

---

### Post by MacJack on 2010-02-02
I have several systems and can say the following cards work 100% with closed source drivers.

8600GT / 8800GT (both nVidia)

---

