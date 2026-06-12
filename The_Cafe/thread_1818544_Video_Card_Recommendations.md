---
title: "Video Card Recommendations"
date: 2011-08-04
forum: The Cafe
---

### Post by pkohler01 on 2011-08-04
Hi - I'm in the market for a new video card. I built my current system with a GTX 480 last November and watched as that GTX480 died. Even the one I received in exchange during the RMA process died. I now have a $400 paper weight and am using my older GTX280. 

I need a video card that's good for high end graphics/photography and 3D modeling through Blender3D as well as high quality video - both viewing and editing. I use two large LED monitors and prefer to use HDMI but might be willing to go with DVI-HDMI adapters if necessary (as was with one of the two displays on the GTX480).

I've seen a lot of reviews around the web but, after trusting a review on the GTX480, I'm kind of soured and wanted to ask the opinion of this community for input instead of relying on the opinion of people who may, for all I know, be getting paid for favorable reviews on popular hardware review sites. 

I'm currently running 10.10 and plan to move directly to 11.10 once it's released. I'm willing to spend up to around $400 for one but would prefer to go with the card with the best features for my dollar. I usually opt for NVidia stuff (I've had better experience with it over the years). 

What would you recommend? What are you currently using that's working well for you?

Thank you in advance for your input and advice!

---

### Post by Basher101 on 2011-08-04
I can't recommend you a model, but from googeling and reading myself through threads, ubuntu has higher support for NVidia cards than ATI. Hope this helps

---

### Post by papibe on 2011-08-04
> **Basher101 said:**
> ...Ubuntu has higher support for NVidia cards than ATI...
+1 
(Linux in general).

---

### Post by LowSky on 2011-08-04
480's ran really hot. im pretty sure the newer 580 run much cooler. but i think the 6 series is due out soon so why not wait

---

### Post by duanedesign on 2011-08-04
To see which NVIDIA cards are supported by the Linux Driver you can visit [this page ]("http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html")and click the Supported Products tab.

You can use [ this form]("http://support.amd.com/us/gpudownload/Pages/index.aspx") to see if the Catalyst Proprietary Linux Driver is available for a particular ATI card. Their is an open source ATI driver and a proprietary. The open source driver is good, but you will get superior performance with the proprietary driver.

Here are a couple of sites I stumbled on when looking at video cards. 
[This site]("http://www.videocardbenchmark.net/") that has some benchmarking of different cards.
[This site]("http://www.gpureview.com/show_cards.php") gives you the ability to compare different cards.
[This comparison guide]("http://www.techarp.com/showarticle.aspx?artno=88") has some useful information on almost 500 cards from several manufacturers. It is difficult to make out the Menu on this site sandwiched between the Google Ads. If you scroll down a bit, in the middle of the page you can see the manufacturers are in alternating yellow and white boxes with the links to the right.

---

### Post by JDShu on 2011-08-04
nvidia for gaming, ati for stable 2d

---

### Post by mips on 2011-08-05
> **pkohler01 said:**
> Hi - I'm in the market for a new video card. I built my current system with a GTX 480 last November and watched as that GTX480 died. Even the one I received in exchange during the RMA process died.

What brand was it?

---

### Post by kaldor on 2011-08-05
> **Basher101 said:**
> I can't recommend you a model, but from googeling and reading myself through threads, ubuntu has higher support for NVidia cards than ATI. Hope this helps

This is no longer true. Most cards will work fine for most people out of the box. Gamers will want a recent card with proprietary drivers. My new PC with a Radeon 6450 gets performance almost on par with my Win7 dual boot when playing fullscreen games on max settings.

Edit:

> **JDShu said:**
> nvidia for gaming, ati for stable 2d

Quite true. Unless you're a gamer or using a lot of high-end 3d software, you no longer "need" NVIDIA these days. AMD has awesome open source drivers.

---

### Post by el_koraco on 2011-08-05
> **kaldor said:**
> 
Quite true. Unless you're a gamer or using a lot of high-end 3d software, you no longer "need" NVIDIA these days. 

Or you don't want your laptop burning a hole through itself.

---

### Post by kaldor on 2011-08-05
> **el_koraco said:**
> Or you don't want your laptop burning a hole through itself.

That's a problem with the open source drivers. The fix for that is to install the proprietary drivers through Jockey or their official site.

---

### Post by el_koraco on 2011-08-05
> **kaldor said:**
> That's a problem with the open source drivers. The fix for that is to install the proprietary drivers through Jockey or their official site.

And the official drivers suck major time. Gnome Shell anybody? Lol, it took them until 11.6 to get everything halfway decent with Compiz.

---

### Post by kaldor on 2011-08-05
> **el_koraco said:**
> And the official drivers suck major time. Gnome Shell anybody? Lol, it took them until 11.6 to get everything halfway decent with Compiz.

Really? Everything's smooth on this end. Sometimes there is lag when moving windows, etc, but nothing too much.

What improvements/changes came with 11.6? I assume Natty still uses 11.4

---

### Post by 3Miro on 2011-08-05
I had ATI 4xxx with FOSS driver on my work machine and it was great. Full support for video and compiz. However, to get 3D performance for gaming, you need an Nvidia. I am happy with my GTX260, but you probably need a higher model. GTX580 should do the trick for you (if you have the money).

---

### Post by el_koraco on 2011-08-05
> **kaldor said:**
> Really? Everything's smooth on this end. Sometimes there is lag when moving windows, etc, but nothing too much.

What improvements/changes came with 11.6? I assume Natty still uses 11.4

Until 11.4 there was no tear fee desktop option. So every compositing effect produced screen tearing. Gnome Shell doesn't work with fglrx at all, four months in - bugs have been filed, a guy from AMD said "we only respond when we're releasing a fix or need more info". 

I understand the desire to support AMD for partially releasing their specs, but the fact of the matter is, their driver suck, the open source drivers can't do power management or 3D effects properly, and unless a machine comes with optimus, Nvidia is a much better choice. 

btw, this is with fglrx, and Transmission running: 

```
[15:19:43 ~] sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +62.0°C  (crit = +200.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +61.5°C  (high = +70.0°C, crit = +97.0°C)  


```

big lol.

---

### Post by kaldor on 2011-08-05
I guess it's a matter of "your mileage may vary" because for me, I'm having awesome luck with the proprietary drivers. 


Also, currently running a few programs and Urban Terror (minimized):

```
$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +19.5°C  (high = +70.0°C) 
```

Edit: Turned off Urban Terror:

```
$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +15.0°C  (high = +70.0°C) 
```

---

### Post by ratcheer on 2011-08-05
My old systems had nVidia cards (9400GT and GT-430) and they had great support with Ubuntu almost all the time. Sometimes things got dicey when xorg releases were being made.
 
My new system has an ATI card (6770) and support is usually ok, but I am currently having a lot of trouble with Unity on the Oneiric development release. Unity 2D runs ok. The ATI driver is the problem. This is to be expected with development releases and I am confident that it will be worked out, eventually.
 
Tim

---

### Post by del_diablo on 2011-08-05
kaldor: What card do you have? And what motherboard?

---

### Post by kaldor on 2011-08-05
> **del_diablo said:**
> kaldor: What card do you have? And what motherboard?

I have an AMD Radeon HD 6450 card. It's the lowest-end card in the 6000 series, but great nonetheless. I didn't build the PC myself, but I believe the motherboard is a Foxconn 2ab1.

---

### Post by medic2000 on 2011-08-05
Buy Nvidia 560 Ti. It's great. Performance nearly great as 570.But for a much more cheap price.

---

### Post by desktorp on 2011-08-05
> **mips said:**
> What brand was it?
Yeah I have a 480 (Asus) in the other room that hasn't seen much use and now I'm all concerned about it crapping out.  :O  Braaaand.

---

### Post by CharlesA on 2011-08-05
> **medic2000 said:**
> Buy Nvidia 560 Ti. It's great. Performance nearly great as 570.But for a much more cheap price.

+1. I have had one for about a month now and it's still running strong. Gets kinda hot, but it's a Fermi... :P

Who needs a space heater! ;)

---

### Post by JDShu on 2011-08-05
> **el_koraco said:**
> Or you don't want your laptop burning a hole through itself.

He's in the market for a new video card, not a laptop.

---

### Post by kaldor on 2011-08-05
Point is, the "ATI doesn't work with Linux" stigma needs to die now. lol

---

### Post by pkohler01 on 2011-08-05
> **mips said:**
> What brand was it?

This particular GTX480 was an EVGA which was surprising to me since I had such great experiences with so much of their non-video card hardware.

Thank you everyone for all of this great information! You've given me a lot to consider. I really appreciate all of you taking the time to reply to this thread!

---

