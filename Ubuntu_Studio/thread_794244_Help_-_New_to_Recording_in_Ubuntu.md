---
title: "Help - New to Recording in Ubuntu"
date: 2008-05-14
forum: Ubuntu Studio
---

### Post by wylroberts on 2008-05-14
Questions:

1. How does Ardour compare to Adobe Audition 3.0?
2. Do most USB/Firewire interfaces that don't need drivers in Windows work in Ubuntu?
3. Is UbuntuStudio necessary or can I just install audio apps on Ubuntu 8.04 64-bit?
4. Disregarding iLok, can I use my Waves VST plugins in Ubuntu?

I've searched this forum and read the websites of the software in question. I'm just looking for a short answer from someone who's actually tried these things.

---

### Post by Stochastic on 2008-05-14
1. Ardour isn't a wave editor, but it's multi-channel mixing capabilities are excellent!!!  Audition does have some feature that are pretty neat, but overall Ardour's power and flexibility in things like bus sends, plugin inserts, and automation make it much better than Audition (IMHO, YMMV).  For wave editing you'll need a different app such as Rezound or Audacity or SND or WaveSurfer or GLAME (here's a bigger list: [http://apps.linuxaudio.org/apps/categories/general_audio_editors](http://apps.linuxaudio.org/apps/categories/general_audio_editors))

2. Really there's USB/Firewire soundcards that don't need drivers in windows?  I've never heard of such things.  As for cards that work in Ubuntu, it all depends on the manufacturer's openness with Linux driver developers.  What models are you thinking of?  (here's a listing of supported firewire devices [http://www.ffado.org/?q=devicesupport/list](http://www.ffado.org/?q=devicesupport/list) and here's where to search for USB [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main))

3. It's possible to just use regular Ubuntu, but you'll run into a lot more troubles.  Ubuntu Studio can also be installed as additional application on top of your Ubuntu install.  Ubuntu Studio has basically fixed a lot of issues with audio processing that were present in regular Ubuntu.

4. VSTs are tricky beasts in Linux as developers rarely consider it as a platform (though this is changing).  Also the Steinberg license doesn't allow Linux to distribute its binaries and therefore developers can't write support into their programs - out of the box.  That being said, VSTs are workable if you're willing to compile a few things yourself.  Check out [http://ladspavst.linuxaudio.org/](http://ladspavst.linuxaudio.org/) for an unofficial list of VSTs that work in linux.
There are essentially two ways to run VSTs: with FST [http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/) or with dssi [http://dssi.sourceforge.net/](http://dssi.sourceforge.net/)

One of these days I'll rewrite my old howto on getting VSTs into Ubuntu.

---

### Post by warbread on 2008-05-15
The only thing I can add to this is that firewire support is not as solid as USB in Linux.  If you're looking to buy an external sound card, I suggest you go for USB.

---

### Post by ethanay on 2008-05-27
USB is cheaper, but the Universal Serial Bus is shared by many devices and can cause trouble.  Firewire is more expensive, but generally high performance and more reliable.  Linux soon will have good firewire support with ffado, just make sure that you are buying a card that is fully supported or that will be guaranteed to be fully supported soon.

my card, an Echo Audiofire2 is listed as fully supported already, but there are also a handful of others from companies that have either volunteered support (like Echo and FocusRite, I believe) or that have been hacked (like MOTU).  Also, the Audiofire2's bigger sibblings, the 4, 8 and 12 will be supported soon (if they aren't already) because they are based on the same standards and the developers have the cards and specs to work with.

although, to be honest, I haven't compiled and installed the ffado driver yet!  but as soon as I do I will report back with my experiences (hopefully no troubles...).

I am new to recording/audio work in Linux, too.  I recommend having a low-latency setup that is completely separate (i.e., dual boot system with a 2nd operating system installed on a completely separate partition) from your normal OS environment.  I use Hardy 32-bit (for generic computer tasks) and 64studio 2.1 32-bit (for low-latency audio tasks).  IMHO, it may sound like a lot of work, but it is very helpful for avoiding many unnecessary headaches into the future...I speak from my personal experience!

As for VST compatiblity, check out the link that Stochastic provided -- it is a good general resource.  I have Pianoteq working well as a vst using dssi-vst 0.7 and jackd.  The only issue has to do with some GUI animations, but it isn't really important...

---

### Post by ethanay on 2008-05-28
ps

I was curious and looked up iLok...what a horrible, horrible thing!  and they couch it in language such as "easy" and "convenient"

"now it is easier than ever to make software less accessible than ever!"

i generally don't like it when people pirate software from small, independent developer companies, but this is ridiculous.

now i am doubly glad that i am on Linux :) :)

---

