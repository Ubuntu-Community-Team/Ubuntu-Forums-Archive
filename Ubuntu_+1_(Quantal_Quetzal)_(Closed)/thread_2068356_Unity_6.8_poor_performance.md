---
title: "Unity 6.8 poor performance"
date: 2012-10-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by janderson91z on 2012-10-08
Hi, I'm playing around with the 12.10 on my Q6600 OC'd to 3.0ghz and I've noticed that Unity is really sluggish. Now I know my CPU is getting a little long in the tooth but it shouldn't have problems with Ubuntu. I thought Unity 6.8 was supposed to increase performance? Would installing the AMD proprietary drivers help anything? Thanks.

---

### Post by sacridex on 2012-10-09
First of all, the Unity performance does NOT depend on your CPU.
What GPU do you have?

---

### Post by janderson91z on 2012-10-09
Amd 4850

---

### Post by TenPlus1 on 2012-10-09
Replacing the open-source radeon drivers with the proprietary one's should make a big difference in speed...

---

### Post by VinDSL on 2012-10-09
You might find this thread illuminating...

LINKAGE:  [http://ubuntuforums.org/showthread.php?t=2064664](http://ubuntuforums.org/showthread.php?t=2064664)

---

### Post by philinux on 2012-10-09
On my acer aspire 1410 I get 20 seconds from gtkperf using 100 test rounds.

How does this compare.

---

### Post by exploder on 2012-10-09
Unity itself seems a little slower but applications like games seem to run much better. I am using the proprietary ATI drivers on an HP DV6 laptop.

---

### Post by DisappearingOak on 2012-10-09
I'm on Ubuntu's Gnome Shell with open source drivers on Radeon 4250, and it can be a little sluggish at some places as well. Could this be related as Unity is based on the same code?
On 100 rounds I get this:
```
GtkPerf 0.40 - Starting testing: Tue Oct  9 18:30:35 2012

GtkEntry - time:  0.07
GtkComboBox - time:  1.28
GtkComboBoxEntry - time:  1.01
GtkSpinButton - time:  0.18
GtkProgressBar - time:  0.20
GtkToggleButton - time:  0.26
GtkCheckButton - time:  0.09
GtkRadioButton - time:  0.09
GtkTextView - Add text - time:  0.11
GtkTextView - Scroll - time:  0.17
GtkDrawingArea - Lines - time:  1.04
GtkDrawingArea - Circles - time:  0.79
GtkDrawingArea - Text - time:  0.46
GtkDrawingArea - Pixbufs - time:  0.23
 --- 
Total time:  5.96

```

no idea what this means though.

---

### Post by fjgaude on 2012-10-09
> **VinDSL said:**
> You might find this thread illuminating...

LINKAGE:  [http://ubuntuforums.org/showthread.php?t=2064664](http://ubuntuforums.org/showthread.php?t=2064664)

On my Intel based box, see signature, I get using gtkperf **3.1** with the default OpenGL CCSM setting on 12.10; **4.6** on 12.04. Removing the default settings, gtkperf is **2.89** on 12.10. (Didn't test for 12.04.)

I would say Unity keeps getting quicker, at least with Intel video graphics.

---

### Post by godhika on 2012-10-09
> **DisappearingOak said:**
> Could this be related as Unity is based on the same code?

This has not been true for quite a while now. Only in it's very first incarnation Unity used to be a Mutter plugin (like Gnome-shell is still today). Unity is now (well for a few cycles in fact) a Compiz plugin.

---

### Post by mc4man on 2012-10-09
In lieu of any real/useful 2d or 3d benchmarking I'd say unity/compiz has gotten slower based on real use experience, at least with nvidia & as supplied.
(glxgears is worthless, glxperf not far behind

---

### Post by fjgaude on 2012-10-09
> **mc4man said:**
> In lieu of any real/useful 2d or 3d benchmarking I'd say unity/compiz has gotten slower based on real use experience, at least with nvidia & as supplied.
(glxgears is worthless, glxperf not far behind

I think what we are observing is Ubuntu developers have ready access to Intel software and always make sure the updates work correctly and take advantage to what Intel is doing, improving.

My box is snappy, and getting better with each Intel upgrade. It's still Sandy Bridge, HD3000, but come the new year will upgrade to Ivy Bridge.

---

### Post by jrog on 2012-10-09
> **fjgaude said:**
> I think what we are observing is Ubuntu developers have ready access to Intel software and always make sure the updates work correctly and take advantage to what Intel is doing, improving.

My box is snappy, and getting better with each Intel upgrade. It's still Sandy Bridge, HD3000, but come the new year will upgrade to Ivy Bridge.
Same here, and I'm using Ivy Bridge (HD 4000).

---

### Post by TenPlus1 on 2012-10-10
Agreed, Intel seems to be improving in leaps and bounds with graphic speeds on the desktop where Nvidia/Amd work towards 3D performance for gaming...

My 10 year old Compaq m2000 laptop with Intel Extreme 2 graphics runs the desktop quicker than my 1 year old Acer Aspire using Nvidia Ion Rev.2...

---

### Post by VMC on 2012-10-10
> **mc4man said:**
> In lieu of any real/useful 2d or 3d benchmarking I'd say unity/compiz has gotten slower based on real use experience, at least with nvidia & as supplied.
(glxgears is worthless, glxperf not far behind

Same here. AMD + nvidia. that's why i removed compiz and all of its cousins and went back to gnome classic. Now its very snappy. I don't need any of that 3D effects.

---

### Post by kyleabaker on 2012-10-10
I've got to agree with the other AMD & Nvidia users here. Unity is becoming more and more sluggish and frustrating to work with. Are Unity developers not testing anything other than Intel and assuming everything else is fine?

---

### Post by mc4man on 2012-10-10
> **kyleabaker said:**
> I've got to agree with the other AMD & Nvidia users here. Unity is becoming more and more sluggish and frustrating to work with. Are Unity developers not testing anything other than Intel and assuming everything else is fine?

I'd think it's known, will likely take time to address
(& by then there will be more changes, additions so more 'items' to address. - one step forward, half (or more) step back

A quick search of just compiz - tag performance shows 17 new
[https://bugs.launchpad.net/compiz/+bugs?field.tag=performance](https://bugs.launchpad.net/compiz/+bugs?field.tag=performance)
Some more with tag gdebugger
[https://bugs.launchpad.net/compiz/+bugs?field.tag=gdebugger](https://bugs.launchpad.net/compiz/+bugs?field.tag=gdebugger)

Also am noticing some new issues with nouveau, maybe kernel related but in any event will add to user problems as user base increases

It's also well known how bad llvmpipe is going to be for most hardware requiring - the changelog for current compiz pretty much says so though "slow ui" is likely an understatement
> 
* debian/patches/unity_support_test.patch:
    - force llvmpipe in the unity profile if we are in the grey zone, meaning:
      the card and drivers have opengl support, however, it doesn't met unity
      requirements (opengl < 1.4, no vertex shaders support…). Thanks duflu
      (LP: #1039155)
      Note that we already discourage them to upgrade from precise to quantal
      with a warning before the upgrade, however let's get a slow ui rather
      than none on the iso as well.

---

### Post by Welly Wu on 2012-10-13
I have the Intel Core i5-3210M with Intel HD Graphics 4000 and Ubuntu Unity 6.8.0 is faster than in Ubuntu 12.04.1 64 bit LTS.

---

### Post by fjgaude on 2012-10-13
> **Welly Wu said:**
> I have the Intel Core i5-3210M with Intel HD Graphics 4000 and Ubuntu Unity 6.8.0 is faster than in Ubuntu 12.04.1 64 bit LTS.

Same here, but with HD3000 and Intel i5-2405S, a very low power CPU but still fast when it called to action.

---

### Post by screaminj3sus on 2012-10-15
> **fjgaude said:**
> I think what we are observing is Ubuntu developers have ready access to Intel software and always make sure the updates work correctly and take advantage to what Intel is doing, improving.

My box is snappy, and getting better with each Intel upgrade. It's still Sandy Bridge, HD3000, but come the new year will upgrade to Ivy Bridge.

I have intel ironlake (one generation before sandybridge). The unity dash is *incredibly* slow in both 12.04 and 12.10. Doing things like dragging an icon from dash to launcher is super laggy, if I open the dash when I have a video playing the dash takes forever to open and is super laggy (can see the icons all VERY slowly loading in) its pretty ridiculous. The same chip runs gnome-shell totally smoothly, and even kwin (with kwin's active blur too).

Every since they introduced blur in the dash its been like this, its very poorly optimized. Kwin's active blur has no such performance hit. Of course you can disable the blur, but that makes the dash unreadable, and static blur is just ugly :/. I really like unity, but they need to speed up the dash, a lot.

---

### Post by bird1500 on 2012-10-15
> **mc4man said:**
> In lieu of any real/useful 2d or 3d benchmarking I'd say unity/compiz has gotten slower based on real use experience, at least with nvidia & as supplied.
(glxgears is worthless, glxperf not far behind

Yes, Canonical better release a new compiz/unity version **soon** since it's a slow experience for Nvidia users (despite using a modern video card).

I'm using Ubuntu since 2007 and it's the first time I decided to defer the upgrade.

---

