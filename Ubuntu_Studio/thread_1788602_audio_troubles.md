---
title: "audio troubles"
date: 2011-06-22
forum: Ubuntu Studio
---

### Post by Flaggmann on 2011-06-22
Does anyone know if there is a decent tutorial on audio and sound with detailed information on the interactivity between jack audio, pulse audio and alsa, other than to say jack and pulse are servers and alsa is whatever you want to call it??

There seems to be a lot of duplication, patchage, connections and patchbay as one example....  are there no standards some applications/players show up right away when launched on these patch bay windows, others need to have the play button pressed. 

Why do all mixers installed affect audio? why do we not have the option top select a default single mixer? It would seem that a lot of questions asked here in this forum would be settled if there was some sort of standard; or at the very least a decent plain language tutorial that all could understand what they are doing, rather than hit and miss hacking to get something to work... or suggesting one roll back to what worked before because they really don't have an answer... if all understood clearly there is a huge supply of skill here in this forum that could easily solve a lot of problems properly and quickly.

---

### Post by sgx on 2011-06-24
Hi, it's really just about the money. A free kernel, system, and apps,
are provided, with support for a limited selection of hardware. The apps are created in spare time, often without teams of specialized coders, and little or no documentation from manufacturers.

You are best served google searching and purchasing a soundcard that is fully or almost completely supported. An older revision 2 maudio 24/96 pci card is a good choice, used for $50 is common.

Youtube videos of Ardour, hydrogen, zynaddsubfx, will often cover
the connection process in the beginning, and there will be related videos in the sidebars.
Cheers

---

### Post by Pablo_F on 2011-06-24
In the context of the announcement of AVLinux5.0, there is an interesting [forum thread in linuxmusicians]("http://www.linuxmusicians.com/viewtopic.php?f=24&t=7161") about linux audio integration. GMaq and falktx are doing a wonderful work. Check it out! 

Their work is huge but it also depends on the work of many others including debian multimedia team and, of course, upstream developers. All of them need user feedback and help. At the very least, we are supposed to be patient and understand the difficulties. 

OTOH, computer music is not a piece of cake for an absolute beginner in any platform. 

Those of us into the ever-evolving nature of free software will still have to learn some tricks, more so in ubuntustudio. AVLinux, KXstudio, Tango Studio, Dream Studio... put things easier in the audio side.

---

### Post by cchhrriiss121212 on 2011-06-24
You are never going to get a standard for anything on linux, whether it is audio systems, desktop environments, media players, package systems etc. That is just what FOSS is like, your best bet is to pick the most popular solution, then use the forums if you get stuck.

But you do have the option to install a single mixer, pulse audio can be removed if you don't like it, and then you can just use alsamixer.

---

### Post by akavir on 2011-06-24
It won't help today, but on my review site I've already got a comprehensive written/video HowTo, covering all the basics of working with audio in Linux.  I plan on releasing it in about 2 weeks.  I've seen a number of posts like yours recently, so I decided to do something about it, so future new Linux musicians can set down to work, and not spend the first week learning setup!
[http://i2productions.com/lir](http://i2productions.com/lir)

---

