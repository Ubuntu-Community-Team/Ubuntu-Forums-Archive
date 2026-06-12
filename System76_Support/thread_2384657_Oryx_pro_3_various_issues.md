---
title: "Oryx pro 3 various issues"
date: 2018-02-09
forum: System76 Support
---

### Post by meyer-ant on 2018-02-09
Hey folks,
I received my new oryxp3 to replace my old gazelle and am facing a few disagreements which you may be able to help me with (hopefully).

-Trackpad lag:
The reactivity of the trackpad is way slower than on my previous machine. It just seems laggish when you move the cursor around. Anyone faced that? I understood this trackpad needs a specific driver, is this something that should be updated in some way? 

-Fans running pretty much constantly:
I got the gtx1070 and 3.9 gigHz CPU. The fans are running pretty much all the time even when I'm not doing much and that's annoying as hell! I've removed all the fancy unity animations and such to ease the gpu. I've tried to play with the nvidia settings but can't find a way to manually control the fan speed. Is this something possible at all?  
I've got irq/132-nvidia process eating a little bit of the cpu pretty much all the time. Is that normal?
[ATTACH=CONFIG]278488[/ATTACH][ATTACH=CONFIG]278489[/ATTACH]

Not super happy overall about that machine :\

---

### Post by overlord.gaurav on 2018-03-30
> -Fans running pretty much constantly:
I have Oryx Pro3 with GTX 1070 as well, and the fans are indeed noisy. From what I have noticed, if there is any application consuming about ~10% CPU continuously, then the fans kick in and it's disturbing. However, that doesn't really happen all the time, and the processes consuming that much CPU can be killed. 
> I've got irq/132-nvidia process eating a little bit of the cpu pretty much all the time. Is that normal?
I have a similar process running, but that seems to be consuming 0-1% of CPU

From the images, I can see your GPU temperature is just 43 degrees. That's almost the lowest temperature I see my GPU at. Usually, my GPU is at about 50-53 degrees.

---

### Post by carlosw on 2018-04-11
Hey! Same 3 Issues here with my new Oryx Pro with GTX 1070. I complained about the fan noise and System 76 replaced the cooling fan and the heatsink. The noise is exactly the same as before... which is extremely annoying... The cooling fan kick in very hard even when browsing with a single tab on a google search page..... The temperature of my cores vary between 45 and 55 C or even more sometimes. I am also experiencing lag times with the trackpad.... Please let me know if you find a solution to any of this..

By the way, I've tried Ubuntu, Debian (Gnome) and POP OS and the problems remain the same.

---

### Post by monkeybrain20122 on 2018-04-12
> **meyer-ant said:**
> Hey folks,
I received my new oryxp3 to replace my old gazelle and am facing a few disagreements which you may be able to help me with (hopefully).

-Trackpad lag:
The reactivity of the trackpad is way slower than on my previous machine. It just seems laggish when you move the cursor around. Anyone faced that? I understood this trackpad needs a specific driver, is this something that should be updated in some way? 

-Fans running pretty much constantly:
I got the gtx1070 and 3.9 gigHz CPU. The fans are running pretty much all the time even when I'm not doing much and that's annoying as hell! I've removed all the fancy unity animations and such to ease the gpu. I've tried to play with the nvidia settings but can't find a way to manually control the fan speed. Is this something possible at all?  
I've got irq/132-nvidia process eating a little bit of the cpu pretty much all the time. Is that normal?
[ATTACH=CONFIG]278488[/ATTACH][ATTACH=CONFIG]278489[/ATTACH]

Not super happy overall about that machine :\

I have also the Oryx pro with GTX1070 and am super happy about it, have none of your problems but then there may be some differences in specs. Which driver are you using 390.30 and 390.48 both work great here

It seems that no one from system76 actually reads these threads, better open a support ticket at their site.

P.S I don't think unity and fancy desktop animations have anything to do with the gpu, check nvidia-smi it is always 0% unless I am doing cuda stuffs.

---

### Post by overlord.gaurav on 2018-04-15
That's interesting! I assumed that the fan is going to be noisy, no matter what.
My current nVidia driver version is 384.111

I will try updating after a week from now and share the results here.

---

### Post by overlord.gaurav on 2018-05-09
> **overlord.gaurav said:**
> That's interesting! I assumed that the fan is going to be noisy, no matter what.
My current nVidia driver version is 384.111

I will try updating after a week from now and share the results here.

Update: No change after updating to nvidia driver v 396

---

### Post by jadetr on 2019-02-19
Hello,

I was able to control both CPU and GPU Fan for my Oryx Pro 3 b.

#you can look at the exact System76 computer version you have here
cat /sys/class/dmi/id/product_version    # oryp3-b

I've cloned this repo locally and then performed compilation (without install)
[https://github.com/davidrohr/clevo-indicator](https://github.com/davidrohr/clevo-indicator)

sudo apt-get install libappindicator3-dev libgtk-3-dev
git clone [https://github.com/davidrohr/clevo-indicator.git](https://github.com/davidrohr/clevo-indicator.git)
[COLOR=#005CC5]cd[/COLOR] clevo-indicator
make
sudo su
#Set CPU Fan to 50%
bin/clevo-indicator set 50
#Set GPU Fan to 50% (less noisy)
bin/clevo-indicator setg 50
I didn't experience much with the clevo-indicator lib. Setting the uid=root didn't work and I was unable to have it in the ubuntu top bar.

But this is a proof of concept that we can use low level EC functions to control both fans.

---

### Post by undecidable on 2019-04-11
However, if you manually control your fans, you need to watch the cpu temp.
I have had overheating shudowns on Kubuntu 14.04 running hte HWE kernel with the first version of the OryxPro.
No overheating issues with Xubuntu 18.04.
I keep a terminal window open running:
```
watch -n 8 sensors
```

I agree the fans are annoying.
Agree it seems to be related to the nvidia cards - and it is much worse with external lcds attached.
The same load on a Galago does not cause fan noise.

---

