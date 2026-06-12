---
title: "Intrepid on a 3 year old machine"
date: 2009-01-04
forum: Testimonials &amp; Experiences
---

### Post by diw on 2009-01-04
My computer is about 3 years old and comprises an Athlon 64 - 3700 single processor, an Asrock dual vista 939 mobo, 1 GB ram, Nvidia Geforce 6600GT graphics card and a 200GB Seagate IDE Hard Drive.  Although 3 years is a long time in computing I am a liitle disappointed that whilst its very lively under Windows XP, its starting to show its age under Ubuntu 8.10 with Nvidia drivers enabled.  In particular ripping CD's to mp3 format in Sound Juicer is quite slow, the rendering of photos in F-Spot is far from ideal, and the rendering of multipage pdf documents is horrendous.  When it comes to printing on my Epson D120, unless I am printing from within Open Office  then it is  painfully slow to the point where it takes 4 or 5 minutes to begin printing a pdf or a layout of photos from Digikam.  Once printing has begun then it is fairly quick.

I'm not sure of the reason for the above problems.  Maybe it's a hardware problem - a mobo and a graphics card that has been optimised for Windows or maybe current distros are becoming more bloated.  I find that this problem isn't just related to Ubuntu- its the same with Suse although not quite so bad with Mandriva.

What do you think?

---

### Post by wolfen69 on 2009-01-04
i have a much older computer than you and have no problems with speed. then again, i don't use any proprietary video drivers.

---

### Post by Martje_001 on 2009-01-05
> **wolfen69 said:**
> i have a much older computer than you and have no problems with speed. then again, i don't use any proprietary video drivers.
Ignorance.. When I had a Sempron 2400+ a while ago, I thought Ubuntu was freakin' fast on it. Now I have a Phenom 9550 and I think the Sempron is freakin' slow ;).

---

### Post by wolfen69 on 2009-01-05
> **Martje_001 said:**
> Ignorance.. When I had a Sempron 2400+ a while ago, I thought Ubuntu was freakin' fast on it. Now I have a Phenom 9550 and I think the Sempron is freakin' slow ;).

what's with the ignorance remark? is there a problem?

---

### Post by diw on 2009-01-05
wolfen69 wrote

> i have a much older computer than you and have no problems with speed. then again, i don't use any proprietary video drivers.

If I don't install the Nvidia drivers I have problems with frame rates eg if I drag open windows around the screen this is very jittery and viewing photos in F-Spot is terribly slow.

If I had a spare graphics card then I would try that but unfortunately I haven't

---

### Post by Martje_001 on 2009-01-05
> **wolfen69 said:**
> what's with the ignorance remark? is there a problem?
No, it was meant as a joke (like: you don't know what you're missing)..

---

### Post by 3rdalbum on 2009-01-05
XP is what; seven years old? It's quite normal to find that later operating systems and programs run slower and use more resources than earlier ones. There's always demand for new features, and with processors getting more powerful and memory getting cheaper there's less demand for efficient programming.

---

### Post by HunterK on 2009-01-05
I can say from experience that the 177 drivers are terrible (compared to the beta 180 drivers!)  Here is my PC:

MSI K8T Neo2 Mobo
Athlon64 3500+
2GB RAM
GeForce 6800GT

I did a fresh install of Intrepid and used Envy to install 177 drivers.  Things just felt SLUGGISH.  Web browsing, clicking around nautilus, playing videos, etc.  I come to find out that the new nvidia 180.XX drivers have a whole slew of updates that greatly improve the responsiveness and speed of the linux desktop.  I uninstalled 177 and installed 180.18 and it was night and day!  These drivers seemed to breathe new life into my 3 year old PC.  :D

---

### Post by diw on 2009-01-05
Hunterk wrote

> I did a fresh install of Intrepid and used Envy to install 177 drivers. Things just felt SLUGGISH. Web browsing, clicking around nautilus, playing videos, etc. I come to find out that the new nvidia 180.XX drivers have a whole slew of updates that greatly improve the responsiveness and speed of the linux desktop. I uninstalled 177 and installed 180.18 and it was night and day! These drivers seemed to breathe new life into my 3 year old PC.

Ah thanks for this.  Do the 180.18 drivers come from the canonical repositories or can you point me in the right direction.

---

### Post by HunterK on 2009-01-05
**I have to say "Your mileage may vary" "Do this at your own risk" ETC ETC ETC**

...BUT, here is how I did it. Mind you this was all on a very fresh install of 8.10. I dont know if I was lucky, or if this will harm things later down the road (automatic kernel updates breaking my drivers?), but, for now, its working great:

Since I used EnvyNG to install the 177 driver, I used it to uninstall the driver.  (I'm guessing you can just remove anything nvidia-xxxxx using synaptic if you didnt use Envy?)

I downloaded the drivers from nvidia's ftp site (pkg1 or whatever is highest):

[ftp://download.nvidia.com/XFree86/Linux-x86/180.18/](ftp://download.nvidia.com/XFree86/Linux-x86/180.18/)

After that I started a new session CTRL+ALT+F1 and ended the X server by using the code:

```
sudo /etc/init.d/gdm stop
```

I then made sure I was in the correct directory where I downloaded the drivers (cd Desktop) and simply ran:

```
sudo sh NVIDIA-Linux-x86-180.18-pkg1.run
```

I let it automatically try to download kernel modules, when it didn't find them, it built them on its own.  Also, I let it configure X automatically, too.  After that, I did

```
sudo reboot
```

and everything was great from there. I hope this helps.  This is just my experience, so good luck.  I got most of my info from this thread: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by pataphysicianu on 2009-01-05
> **diw said:**
>  In particular ripping CD's to mp3 format in Sound Juicer is quite slow,

Try installing Lame from Synaptic package manager. After the installation of lame, Sound Juicer went from 3.5x rate to over 16x rate for me, not sure why since the lame libraries seemed to be already installed, but not the full package. Anyway after doing this, mostly because I needed the lame command line and to get K3b to do mp3 extraction, sound juicers performance dramatically improved.

hope this helps you

---

### Post by wandalalakers on 2009-01-05
I have an Athlon 950 on my 2nd pc and I have Kubuntu 8.04.1 and I'm pleased.  I downgraded from 640mb to 512mb because of bad ram and it still runs fine.  I also have an Nvidia card in this desktop and use EnvyNG.

---

### Post by kevinws on 2009-01-06
> **pcdoctor said:**
> I have an Athlon 950 on my 2nd pc and I have Kubuntu 8.04.1 and I'm pleased.  I downgraded from 640mb to 512mb because of bad ram and it still runs fine.  I also have an Nvidia card in this desktop and use EnvyNG.

What type of Nvidia card do you have on the 950? I have an older Athlon basd pc with a fx5700 card. Everytime I install the nvidia drivers and restart I end up with a black screen. I have to reboot and restore x from the recovery panel.

Thanks
kws

---

### Post by iheartubuntu on 2009-01-07
> **HunterK said:**
> **I have to say "Your mileage may vary" "Do this at your own risk" ETC ETC ETC**

...BUT, here is how I did it. Mind you this was all on a very fresh install of 8.10. I dont know if I was lucky, or if this will harm things later down the road (automatic kernel updates breaking my drivers?), but, for now, its working great:


Thanks for the tip. I'll try it at work tomorrow. I hope Regnum Online kicks MORE butt with the new drivers :) There is a serious Realm war going on and I have to defend Syrtis!!!

---

### Post by diw on 2009-01-07
Kevinws wrote:

> What type of Nvidia card do you have on the 950? I have an older Athlon basd pc with a fx5700 card. Everytime I install the nvidia drivers and restart I end up with a black screen. I have to reboot and restore x from the recovery panel.


I think I've read somewhere(could have been linux format) that the next Nvidia drivers will not be supporting graphics cards prior to the fx5900 series.  This could be your problem

---

### Post by diw on 2009-01-07
HunterK - Thanks for the info regrading the updated NVidia drivers.  Its almost like having a new pc!

---

### Post by wandalalakers on 2009-01-11
> **kevinws said:**
> What type of Nvidia card do you have on the 950? I have an older Athlon basd pc with a fx5700 card. Everytime I install the nvidia drivers and restart I end up with a black screen. I have to reboot and restore x from the recovery panel.

Thanks
kws

I used to have an Nvidia TNT2 M64 32mb 4X video card (agp) in this pc with an AMD 950 and I had no problems with Kubuntu 7.10.  I'm double checking now.  I now have an Nvidia GeForce FX 5200 in this desktop.  I recently installed Linux Mint 5 and I'm using EnvyNG driver 96.43.05 on this 2nd desktop.

---

