---
title: "Is the main difference with Ubuntu Studio the kernel? And do I really need it?"
date: 2010-09-16
forum: Ubuntu Studio
---

### Post by QwUo173Hy on 2010-09-16
I've been using Ubuntu Studio since Karmic. I understand that the kernel is real-time, but since my sound card has a latency of 16ms anyway, does it even make a difference?

I'm considering installing Ubuntu 10.10 (in spite of the adage 'if it ain't broke ...') now and I'm not sure whether to go for a default Ubuntu install and just install Ardour on top, or actually put in Ubuntu studio.

Can someone help me make an informed decision?

Many thanks!
Jarlath

---

### Post by Jormeliini on 2010-09-16
With rt kernel it's less likely to get xruns under heavy processor load. It's better to have rt kernel in music production but it is not necessary unless you need to get the most out of your system. Ubuntu Studio is not that different from Ubuntu. Basically it is just different selection of packages from Ubuntu repositories and either can be easily turned into the other. Rt kernel is there and can be installed with the following command:

```
sudo apt-get install linux-image-2.6.31-11-rt
```

Then you'll need to configure GRUB to boot to that kernel or select it from the GRUB menu every time you want to use it. If you need help with that just ask.

My suggestion is that go with the version that is closer to your needs and install the extra stuff you need. Ubuntu Studio is a bit easier as everything needed for music production should be there by default. With Studio way you may also avoid doing some configuring that would be necessary with Ubuntu.

--

Oops, I thought you used Lucid. Not sure what rt kernel is available in 10.10 but there should be one.

---

### Post by snowpine on 2010-09-16
You can install both kernels and choose between them from the GRUB boot menu, to obtain a definitive answer which works better on your specific hardware.

---

### Post by QwUo173Hy on 2010-09-16
Good advice, thank you both. I think I'll go ahead with Studio and use the standard kernel if I come across issues with the rt one.

---

### Post by maghoxfr on 2010-09-16
I have Lucid with both kernels installed, you can read [this awesome thread]("http://ubuntuforums.org/showthread.php?t=1543109") to get the idea of what you should tweak on the kernel. I'm currently using the 2.6.31-10-rt, but for example I was having compatibility problems with the graphics card drivers; they work great on the rt-kernel but not on the generic one (or viceversa depending on the driver version I picked) but as I'm only using the rt I'm not putting much effort in solving that right now.

There's really only one thing I didn't like Ubuntu Studio: I had lots of unused software. Once you pass the exploration period in Ubuntu and you are pretty sure of what programs you like and need, you can easily install them yourself from synaptic adding the correct PPA's. Here's a couple of great musician oriented PPA's that are extremely useful for me (they include kernels too).

[http://ppa.launchpad.net/falk-t-j/lucid/ubuntu](http://ppa.launchpad.net/falk-t-j/lucid/ubuntu)
[http://ppa.launchpad.net/autostatic/ppa/ubuntu](http://ppa.launchpad.net/autostatic/ppa/ubuntu)
[http://ppa.launchpad.net/bojo42/rt/ubuntu](http://ppa.launchpad.net/bojo42/rt/ubuntu)
[http://ppa.launchpad.net/philip5/extra/ubuntu](http://ppa.launchpad.net/philip5/extra/ubuntu)

[http://ppa.launchpad.net/falk-t-j/lucid-latest/ubuntu](http://ppa.launchpad.net/falk-t-j/lucid-latest/ubuntu) **This one for new stuff**

Hope this helped, I'm just too comfortable with Ubuntu and this is what works for me, you'll find out what suits best for you and that flexibility is what makes linux so great.

Cheers

---

### Post by QwUo173Hy on 2010-09-17
maghoxfr, thank you for the ppas! Yes, I also found that I didn't use most of the audio software in Ubuntu Studio. Mainly because I didn't know how, or because my needs were different. Now I just use Ardour, Audacity and Hydrogen - and that's it! Maybe I'll get into rosegarden too someday.

Thanks again!
Jarlath

---

### Post by maghoxfr on 2010-09-17
Glad I was of any help. Give [Qtractor]("http://qtractor.sourceforge.net/qtractor-index.html") a try, it's simple but powerful, it looks good and it supports audio/midi**That's what I'm using right now**. Maybe you'll like LMMS too. 

I have lotsa lot of audio software installed, I use most of it, but it's the ones I picked after trying lots of them, I don't think I have many unused programs occupying HDD space. It also depends on what instrument you play or how you make music.

see you

---

### Post by QwUo173Hy on 2010-09-17
Qtractor looks great! I'll definitely give that a go. Ardour was great, but I was exporting all my midi tracks to .wav so Ardour could import them. Qtractor looks a little more simple and the midi support is great.

---

