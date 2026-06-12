---
title: "Umm... What? (GPU Oddness)"
date: 2011-04-03
forum: Testimonials &amp; Experiences
---

### Post by Techrocket9 on 2011-04-03
I have an HP laptop. It has a 9600GT. I have found oddness:

On Windows 3D games regularly make it overheat. Speedfan reads 97C for the GPU and the laptop actually burns my skin if I touch it incorrectly (read: touch it anywhere but the keys on the keyboard). Eventually it black screens and I have to hard reset it and let it cool for a few hours.

On Ubuntu the temperature never exceeds 76C. I have never burned myself on the machine and the fan is not pinned at 100% all the time like it is on Windows.

???

Besides the generic "Duh, Linux is better", I'm curious how is it possible for different OSes to generate different amounts of heat doing the same graphical chores (OpenGL games).


(btw Windows isn't loaded with bloatware from the manufacturer, I reinstalled to clean it out)

---

### Post by arunb on 2011-04-04
I think its something to about heat sensors in the CPU and the hard disk, probably WIndows is not reading the sensors correctly and hence allows the laptop to run at a higher temperature. 

Did the laptop came pre-installed with Windows ?, its possible you may not be the only one with this problem. In any case get it checked with the HP support people if the laptop is under warranty...

Does the fan run in Windows, while you are playing the games ??

thanks
a

---

### Post by Techrocket9 on 2011-04-04
It came with Vista. I installed 7 (clean install) a while ago. It's long out of warranty. It dates back to the great nVidia GPU recall where virtually every laptop GPU nVidia made except the 9600GT was recalled.

The fan runs more and harder in Windows than Ubuntu.

btw, this isn't a help request. I'm mostly amused and wondering what could be causing the disparity between OSes.

---

### Post by gradinaruvasile on 2011-04-04
This is surely related to drivers or power management options.

Did you install the driver for it from the manufacturer site on Windows? Bear in mind that some manufacturers might have customized hardware.

Then check the power management settings. Maybe the card is forced to run on the maximim speed all the time. There is a nice hardware information tool here that usually shows the GPU speed and temps (works on most hardware anyway):

[http://rh-software.com/downloads/siv.zip](http://rh-software.com/downloads/siv.zip)

---

### Post by mastablasta on 2011-04-04
> **gradinaruvasile said:**
> Did you install the driver for it from the manufacturer site on Windows? Bear in mind that some manufacturers might have customized hardware.
 
 
yes, you probably need drivers from HP.

---

### Post by 3Miro on 2011-04-04
What kind of games are you playing? Nvidia 9xxx usually supports DirectX 10, while wine usually runs on DirectX 9. It is possible that the game under Windows is trying to get more effects using additional instructions that cause the GPU to overheat.

Try running some OpenGL benchmarks under Linux, and I mean benchmarks that will test all capabilities of the GPU. Look at:

[http://unigine.com/download/](http://unigine.com/download/)

---

### Post by Techrocket9 on 2011-04-04
Mostly the gaming that I do is Minecraft (an OpenGL game).

Also, I have all the necessary drivers from HP, except the GPU drivers which are direct from nVidia (HP's last release for this laptop dates to 2008).

---

