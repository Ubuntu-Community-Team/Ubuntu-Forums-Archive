---
title: "Overall Performance  in GNOME 3"
date: 2011-10-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kaldor on 2011-10-16
I'm wondering if anyone else has the same performance problems that I do across any GNOME 3 distro. I'm using the proprietary NVIDIA drivers since Nouveau has heat/battery life problems. I have laggy scrolling, laggy transitions (Activites menu on Shell, Dash on Unity), and overall it just doesn't feel smooth. Fallback mode and Unity 2d work fine. Further, I know my drivers are working fine because I can get a lot of power in 3D games. I have way more than enough to run GNOME 3 and Ubuntu smoothly. KDE4 with all sorts of eyecandy enabled gives a perfectly smooth experience, whereas a simple Unity desktop is a mess for me.

I've been using GNOME 3 on this machine for months and I've always just kind of lived with it. I assumed that since it's the first release I could expect issues like this. Will these sorts of issues eventually be sorted out, and are there any bug trackers I could follow? I don't want to have this sort of issue when I start using the LTS :(

Thanks.

---

### Post by effenberg0x0 on 2011-10-16
It would depend on which Nvidia card you have. I can tell you, from my personal experience, those standard cards like GeForce 9500GT, 9600GT are more than enough for simultaneous 1080p video + 3D desktop + 2 monitors on Oneiric right now (Unity with many Compiz stuff enabled tested extensively). I can only imagine that Gnome-shell wouldn't possibly be heavier than that. 

If you put these card sensors on screen, you see that rarely the hardware is under real stress. Generally CPU/GPU/MEM are underclocked, etc. 

I like (and use as main hardware) GTS500 and it is much faster than those two in specs, but honestly, its overkill: you see no difference in desktop performance. I had it SLI before but I removed one... you just can't find a situation where you need that setup.

We all know that it means **** as benchmark but, just so you have an idea, the GTS500 puts out 10.000fps easily here on Unity. If I set it to performance mode, disable high quality antialiasing, texture sharpening, anisotropic filtering, set compiz OpenGL to Fast (instead of Best), etc, it easily goes to 14000fps. The 9500/9600 puts out something like 3.000fps on glxgears easily. 

The thing is, you underclock either of them untill glxgears gives you something like 800fps and still you see no lag on my setup (Unity, Compiz, Video,2 monitors, etc). 

So I really think any of these standard card is more than capable of being used on Gnome-shell. Can't believe it would be that heavier in terms of OpenGL.



PS: All my experience is with Nvidia Proprietary Drivers. I know nothing about Nouveau.

---

### Post by mc4man on 2011-10-16
@ kaldor
you may wish to look at this recent post I have, may be similar to what you see, may not  - I'd think more concerning laptops if that's what you have (posts 10 & 11
[http://ubuntuforums.org/showthread.php?p=11350941#post11350941](http://ubuntuforums.org/showthread.php?p=11350941#post11350941)

---

### Post by sgage on 2011-10-16
> **kaldor said:**
> I'm wondering if anyone else has the same performance problems that I do across any GNOME 3 distro. I'm using the proprietary NVIDIA drivers since Nouveau has heat/battery life problems. I have laggy scrolling, laggy transitions (Activites menu on Shell, Dash on Unity), and overall it just doesn't feel smooth. Fallback mode and Unity 2d work fine. Further, I know my drivers are working fine because I can get a lot of power in 3D games. I have way more than enough to run GNOME 3 and Ubuntu smoothly. KDE4 with all sorts of eyecandy enabled gives a perfectly smooth experience, whereas a simple Unity desktop is a mess for me.

I've been using GNOME 3 on this machine for months and I've always just kind of lived with it. I assumed that since it's the first release I could expect issues like this. Will these sorts of issues eventually be sorted out, and are there any bug trackers I could follow? I don't want to have this sort of issue when I start using the LTS :(

Thanks.

No such issues here (GeForce 8500 GT). In fact, I find Gnome Shell to be very smooth and fast. What nvidia card do you have?

---

### Post by kaldor on 2011-10-16
It's an Nvidia GeForce 8400m GS. It's only GNOME 3 stuff that this happens with. Fallback mode, Unity 2d, KDE (full compositing), Compiz in 11.04, etc, all work without any issue.

I always install drivers using Jockey. It's not Ubuntu-specific as it happens on other distros using GNOME 3 as well. Nouveau drivers are much smoother but cause battery life and heat problems for me.

I do hope that this is fixed in time for the LTS since it gives the perceived feeling of sluggishness.

---

### Post by fedexnman on 2011-10-16
I have a 9800gtx or what ever running the latest ubuntu drivers not 173 and  i noticed in gnome3 or shell  it hickups when i click on applications  or other parts of the gui , the gui doesnt seem to move as quick as in reg unity or unity2d ?  i dont blame the drivers or the nvidia card , it s gotta be something with gnome3/shell  or how its packaged for ubuntu 11.10 .

---

### Post by mc4man on 2011-10-16
> **kaldor said:**
> It's an Nvidia GeForce 8400m GS. It's only GNOME 3 stuff that this happens with. Fallback mode, Unity 2d, KDE (full compositing), Compiz in 11.04, etc, all work without any issue.

I always install drivers using Jockey. It's not Ubuntu-specific as it happens on other distros using GNOME 3 as well. Nouveau drivers are much smoother but cause battery life and heat problems for me.

I do hope that this is fixed in time for the LTS since it gives the perceived feeling of sluggishness.

Simple to test - 
open up nvidia-settings > powermizer
set the Preferred Mode to "Prefer Full Performance"
If the lag disappears then you know the cause

---

### Post by kaldor on 2011-10-16
> **mc4man said:**
> Simple to test - 
open up nvidia-settings > powermizer
set the Preferred Mode to "Prefer Full Performance"
If the lag disappears then you know the cause

This seems to have helped. However, will this impact my battery life?

---

### Post by mc4man on 2011-10-16
> **kaldor said:**
> This seems to have helped. However, will this impact my battery life?
Certainly will

For the moment I'm 'fixing' AC performance,  & living with what is on battery with an xorg entry.
In my case this new poor behavior is only seen in 11.10 with  unity/compiz-0.9, everything else is fine as is  11.04 & all earlier releases

Am setting nvidia to use max perf. on Ac & adaptive on battery with this as an xorg
```
Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
EndSection

```
Because this laptop has a joke of a cooling 'system' have been checking the temps with AC on max perf. - so far is ok.

Have an older bug I've re-opened, currently against unity/compiz because not sure where else to blame. May add a few more sources - throw enough * against the wall, ect
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/843383](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/843383)

---

### Post by fjgaude on 2011-10-16
> **kaldor said:**
> I'm wondering if anyone else has the same performance problems that I do across any GNOME 3 distro. I'm using the proprietary NVIDIA drivers since Nouveau has heat/battery life problems. I have laggy scrolling, laggy transitions (Activites menu on Shell, Dash on Unity), and overall it just doesn't feel smooth. Fallback mode and Unity 2d work fine. Further, I know my drivers are working fine because I can get a lot of power in 3D games. I have way more than enough to run GNOME 3 and Ubuntu smoothly. KDE4 with all sorts of eyecandy enabled gives a perfectly smooth experience, whereas a simple Unity desktop is a mess for me.

I've been using GNOME 3 on this machine for months and I've always just kind of lived with it. I assumed that since it's the first release I could expect issues like this. Will these sorts of issues eventually be sorted out, and are there any bug trackers I could follow? I don't want to have this sort of issue when I start using the LTS :(

Thanks.

I use Intel integrated graphics, GMA HD, and Oneiric is 30% faster than Natty using **gtkperf** test. That just means that Intel has better drivers for the latest issue of Ubuntu. gtk3 and gnome3 rock!

I don't game and don't use Nvidia anymore.

---

### Post by collisionystm on 2011-10-16
> **fjgaude said:**
> I use Intel integrated graphics, GMA HD, and Oneiric is 30% faster than Natty using **gtkperf** test. That just means that Intel has better drivers for the latest issue of Ubuntu. gtk3 and gnome3 rock!

I don't game and don't use Nvidia anymore.


Intel rocks!! By far the best choice of hardware if you want to use Ubuntu or linux in general. Intel drivers are provided for the Linux Kernel by INTEL. Every kernel update means the potential for updated Intel drivers.

I don't think KDE uses Compiz. It uses something else to render window effects.

---

### Post by tista on 2011-10-16
> **fjgaude said:**
> I use Intel integrated graphics, GMA HD, and Oneiric is 30% faster than Natty using **gtkperf** test. That just means that Intel has better drivers for the latest issue of Ubuntu. gtk3 and gnome3 rock!

I don't game and don't use Nvidia anymore.

Hi fjgaude,

Agreed... ;)

mine scores here:
```
GtkPerf 0.40 - Starting testing: Mon Oct 17 10:38:26 2011

GtkEntry - time:  0.03
GtkComboBox - time:  0.71
GtkComboBoxEntry - time:  0.55
GtkSpinButton - time:  0.09
GtkProgressBar - time:  0.03
GtkToggleButton - time:  0.09
GtkCheckButton - time:  0.08
GtkRadioButton - time:  0.14
GtkTextView - Add text - time:  0.37
GtkTextView - Scroll - time:  0.21
GtkDrawingArea - Lines - time:  0.68
GtkDrawingArea - Circles - time:  0.72
GtkDrawingArea - Text - time:  0.61
GtkDrawingArea - Pixbufs - time:  0.10
 --- 
Total time:  4.41
```

That showed on Gnome-Shell/Mutter environments, today I won't run compiz since 2D rendering seemed to be horrible!! :/

Finally I'm concerning to scratch gtkperf to employ gtk3 toolkit to estimate the performance of purely gtk3...

cheers.

---

### Post by buzzmandt on 2011-10-17
> **collisionystm said:**
> Intel rocks!! By far the best choice of hardware if you want to use Ubuntu or linux in general. Intel drivers are provided for the Linux Kernel by INTEL. Every kernel update means the potential for updated Intel drivers.

I don't think KDE uses Compiz. It uses something else to render window effects.

Correct. Kde uses their own effects engine called kwin.

---

### Post by VinDSL on 2011-10-17
> **kaldor said:**
> I'm wondering if anyone else has the same performance problems that I do across any GNOME 3 distro. [...]
I don't have the same identical performance problem(s) as you, but yes, Gnome 3 has definitely been hammering this system (see my sig).

My performance issues have centered around the trend toward hardware acceleration in Adobe Flash, and various browsers.

Disabling hardware acceleration, wherever I can find it, has made a huge difference in usability.  I was actually getting hard locks and screen blurring in Opera-Next, playing online flash games, before I disabled hardware acceleration.

The other thing that made a difference was tweaking some swappiness settings.

Here's my current config (/etc/sysctl.conf)...

```
# Cannot leave things alone
vm.overcommit_memory = 1
vm.overcommit_ratio = 95
vm.dirty_ratio = 5
vm.swappiness = 1
```

Gotta say, everything is working nicely now - as well as can be expected, anyway.  

Guess I'll need to upgrade my hardware, one of these days.  ;)

---

### Post by kaldor on 2011-10-17
> **collisionystm said:**
> Intel rocks!! By far the best choice of hardware if you want to use Ubuntu or linux in general. Intel drivers are provided for the Linux Kernel by INTEL. Every kernel update means the potential for updated Intel drivers.

While Intel is an excellent choice, they only have OSS drivers available. This is no problem for basic use or on netbooks.

However, I think that with desktop machines AMD cards are the best choice these days for a good mix between compatibility and performance. The open source Radeon drivers are comparable to Intel's and they share many of the same components. 

The stigma against AMD is largely unjustified now. If you need proprietary drivers, then yes, AMD tends to be a huge POS. But ever since 2008 AMD's OSS drivers have improved drastically. In Ubuntu 8.04 I couldn't get an old Radeon card to work properly. By 9.04 I had compositing. By 10.10 I could play 3d games. 

Nutshell: Intel and AMD cards are both very great for basic usage. For proprietary drivers, AMD is still evil. But unlike Intel, AMD actually has the proprietary drivers available.

---

### Post by screaminj3sus on 2011-10-17
> **collisionystm said:**
> Intel rocks!! By far the best choice of hardware if you want to use Ubuntu or linux in general. Intel drivers are provided for the Linux Kernel by INTEL. Every kernel update means the potential for updated Intel drivers.

I don't think KDE uses Compiz. It uses something else to render window effects.

Yeah I have been very happy since I moved from ati to intel :) Now compiz, mutter and kwin all perform great.

---

### Post by fjgaude on 2011-10-17
> **tista said:**
> Hi fjgaude,

Agreed... ;)

mine scores here:
```
GtkPerf 0.40 - Starting testing: Mon Oct 17 10:38:26 2011

GtkEntry - time:  0.03
GtkComboBox - time:  0.71
GtkComboBoxEntry - time:  0.55
GtkSpinButton - time:  0.09
GtkProgressBar - time:  0.03
GtkToggleButton - time:  0.09
GtkCheckButton - time:  0.08
GtkRadioButton - time:  0.14
GtkTextView - Add text - time:  0.37
GtkTextView - Scroll - time:  0.21
GtkDrawingArea - Lines - time:  0.68
GtkDrawingArea - Circles - time:  0.72
GtkDrawingArea - Text - time:  0.61
GtkDrawingArea - Pixbufs - time:  0.10
 --- 
Total time:  4.41
```

That showed on Gnome-Shell/Mutter environments, today I won't run compiz since 2D rendering seemed to be horrible!! :/

Finally I'm concerning to scratch gtkperf to employ gtk3 toolkit to estimate the performance of purely gtk3...

cheers.

Thanks, Tista, for the data!

I just ran gtkperf on Unity3D and Gnome both coming in at about 8. It was 12 on 11.04, if you remember.

Now with 2D, Gnome Classic No Effects, and Gnome Classic, it's about 5.

Good show for Intel!

---

