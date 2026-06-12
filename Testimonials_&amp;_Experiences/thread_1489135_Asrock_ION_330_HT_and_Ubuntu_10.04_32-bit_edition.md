---
title: "Asrock ION 330 HT and Ubuntu 10.04 32-bit edition"
date: 2010-05-20
forum: Testimonials &amp; Experiences
---

### Post by terrrorr on 2010-05-20
Hello all,

My latest investment is a Asrock's ION 330HT nettop machine. I did make some research about its possibilities and I thought it could be my silent HTPC with low power consumption, and how wrong I was.

Machine itself is great but if you think you could run some HD video files, think again. I tested three different kind of HD files (720p) which this machine is supposed to handle with ease. Best result was avg. 17 frames per second. First I thought that the main reason was in my media player, so... I tested with VLC and XMBC, but results was as bad as previously. I even removed all desktop effects but still my movie experience was poor.

So what is my conclusion. This is a great machine if you want to do some simple and easy task witch does not need so much processing power. But if  you want to use it as your hardcore media center, think again.

Details:
Computer: Asrock ION 330HT
Memory: 2 GB
HD: 320 5400 rpm 2,5"
OS: Ubuntu 10.04 Desktop 32-bit
GPU drivers: Latest drivers from NVidia
Display: Samsung 40" Full HD flat tv
Display settings: 1920x1080

---

### Post by armandh on 2010-05-21
a great video card/drivers in a slower machine worked well for me for a long time. trouble starts [IMHO] when an inadequate video [card/chip/driver] pushes decoding work on to an inadequate processor. this is exacerbated by ever newer and more complex codec/file format.

---

### Post by gballard on 2010-06-11
I have two of these ASRock Ion 330HT boxes and they run XBMC 9.14 like a champ...not a hiccup...skip...or jump.

---

### Post by 3rdalbum on 2010-06-11
Turn off Compiz.

---

### Post by kerry_s on 2010-06-11
i think you should update the hard drive to a faster 1, that slow drive could be a bottleneck.

gnome-mplayer with a large cache, can help play things like that smooth.

```
-lavdopts skiploopfilter=all -cache-min 75
```

i play 720p & 1080p just fine.

specs:
foxconn rs233
Atom 230 1.6ghz
1gb ram
7200 rpm 80gb hd (sata 3.0)
Intel GMA 950 video

i bought it from newegg for $80:
[http://www.newegg.com/product/product.aspx?Item=N82E16856119011](http://www.newegg.com/product/product.aspx?Item=N82E16856119011)

ps: i run compiz just fine, so that don't matter.

---

### Post by terry_gardener on 2010-06-12
i dont have the asrock but have the acer revo which is very similar and i am able to play 720p files smoothly. 
a friend of mine has the same pc as me and watches 1080p smoothly. 

make sure that vdpau is activated and in use. easiest way is to use xbmc and change the display setting to it.

---

### Post by 3rdalbum on 2010-06-14
Compiz *does* cause lower frame rates when playing intensive video. IIRC it forces video to be indirectly rendered after passing through the compositing step, whereas with a non-compositing window manager it just gets written directly to video memory. I also recall seeing some Phoronix benchmarks regarding this too.

And finally, I've noticed a frame rate increase with Compiz turned off.

---

### Post by xhaos on 2010-06-16
Does the remote control work under ubuntu?

---

### Post by terry_gardener on 2010-06-16
yes remote works, the solution is in the following link.

[http://forum.xbmc.org/showthread.php?p=550045&highlight=working+remote#post550045]("http://forum.xbmc.org/showthread.php?p=550045&highlight=working+remote#post550045")

---

### Post by JEDIDIAH on 2010-07-16
> **terrrorr said:**
> Hello all,

My latest investment is a Asrock's ION 330HT nettop machine. I did make some research about its possibilities and I thought it could be my silent HTPC with low power consumption, and how wrong I was.

Machine itself is great but if you think you could run some HD video files, think again. I tested three different kind of HD files (720p) which this machine is supposed to handle with ease. Best result was avg. 17 frames per second. First I thought that the main reason was in my media player, so... I tested with VLC and XMBC, but results was as bad as previously. I even removed all desktop effects but still my movie experience was poor.

So what is my conclusion. This is a great machine if you want to do some simple and easy task witch does not need so much processing power. But if  you want to use it as your hardcore media center, think again.

Details:
Computer: Asrock ION 330HT
Memory: 2 GB
HD: 320 5400 rpm 2,5"
OS: Ubuntu 10.04 Desktop 32-bit
GPU drivers: Latest drivers from NVidia
Display: Samsung 40" Full HD flat tv
Display settings: 1920x1080

Flash is the only reason that an Asrock 330 might not cut it as a "hardcore media center". The machine can decode bluray disks. There's plenty of support for it's specialized hardware features. The only real problems come from p*sspoor decoders from companies that don't want to put any effort into their Linux versions of proprietary software.

Zareason has a similar box but with a C2D if you've got an interest in something like Hulu.

With either box you need to make sure that the latest proprietary drivers are installed and your software fully supports them.

The thing to look for is "VDPAU".

---

