---
title: "Really Nice Digital Oscilloscope Package"
date: 2007-11-01
forum: The Cafe
---

### Post by ramjet_1953 on 2007-11-01
Just thought that I'd share a really nice Digital Oscilloscope package that I found.

It is called osqoop and you can get it from here:

[http://lsn.unige.ch/osqoop/](http://lsn.unige.ch/osqoop/)

There is an Ubuntu package that was compiled for Dapper, but it works fine under Gutsy.

Of course, if you want to "roll your own", the source code is there also.

It works fine under GNOME.

Regards,
Roger :cool:

---

### Post by mustang on 2007-11-01
Hmm very cool. What kind of hardware/acquisition unit do you have? Any recommendations for a basic no-frills oscilloscope?

---

### Post by ramjet_1953 on 2007-11-01
You can use your sound card for audio input, or an external pre-scaler unit for higher frequencies.

Regards,
Roger 8)

---

### Post by ubunteira on 2008-01-27
How do I install osqoop?

---

### Post by geppetto on 2008-02-27
Authors should write an HOWTO_install, if they care for the success of this product, which is useful for a demo in a secondary school :popcorn:.

Easiest way to install on Ubuntu is 

wget [http://lsn.unige.ch/osqoop/deb/binary/osqoop_1.0.0_i386.deb](http://lsn.unige.ch/osqoop/deb/binary/osqoop_1.0.0_i386.deb)
sudo dpkg -i osqoop_1.0.0_i386.deb

Your milage may vary depending on Ubuntu Version, and updating the sources.list may not work. Above command lines tested in Ubuntu 7.04 with success, while source.list update fails.

Not tested with other distributions: unsure if converting the package in rpm or tgz works, but I would try this _before_ trying to recompile. In that case the howto-dev is of no help :confused:.

---

### Post by ubunteira on 2008-10-13
I suggest a freeware for windows which can run using Wine (some small emulation bugs exist in some cases).
For those who want extra-frills and then some, this is it.
Is called "Visual Analyser" at:
[http://www.sillanumsoft.org/download.htm](http://www.sillanumsoft.org/download.htm)
Using Sound card.
Is not only oscilloscope but also frequency analyser and audio frequency generator.
Tons of parameters
Ultra fast
Dual input and output(for frequency generator)
Built-in frequency meter
Built-in Volt meter
Is worth to try.

---

### Post by eespjl on 2008-11-13
osqoop did not work for me (crashed). 

But xoscope is in the hardy packages and worked a treat.

PJ

---

### Post by yasir.elsharif on 2009-11-09
I used this program **xoscope** - Digital Oscilloscope, it's on the ubuntu repository. It's a very useful tool for secondary schools demos. It can be used with just normal microphone. I highly recommend this one

---

