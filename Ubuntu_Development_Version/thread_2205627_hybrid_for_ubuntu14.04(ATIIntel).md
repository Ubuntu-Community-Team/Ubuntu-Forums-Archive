---
title: "hybrid for ubuntu14.04(ATI/Intel)"
date: 2014-02-15
forum: Ubuntu Development Version
---

### Post by l0o0 on 2014-02-15
My laptop is acer 4745g, i have just installed ubuntu 14.04 gnome daily-build. The installation process is all right. Acer 4745g have ATI HD5650 and Intel chip, I think hybrid GPU is muxed. I want to turn on the integrated chip and turn off the discrete. I follow the steps in [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics) using vga_switcheroo.
```
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
```Turns on the GPU that is disconnected (not currently driving outputs), but does not switch outputs. 
```
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
```Connects integrated graphics with outputs. 


```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```Turns off the graphics card that is currently disconnected. 


So i want to check the status of the vga chip:
```
cat /sys/kernel/debug/vgaswitcheroo/switch
```
this is the output:
[HTML]0:DIS: :DynPwr:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
2:DIS-Audio: :Pwr:0000:01:00.1[/HTML]

I see Pwr in both IGD and DIS, so i don't know if i turn of the DIS graphics?

any helps?

---

### Post by QIII on 2014-02-15
You shouldn't need to use vga-switcheroo any more.

[This]("https://wiki.ubuntu.com/X/Config/HybridGraphics") is the word on pxpress for ATI.  It goes up through 13.10, but it should be applicable to Trusty as well.

This seems to have been the ticket to success for about half the people I have suggested it to so far.

---

### Post by l0o0 on 2014-02-15
In the hardware requirements:
**A MUXless system with an Intel or an AMD integrated card and an AMD discrete card.**

But i don't think my laptop support muxless system.

---

### Post by l0o0 on 2014-02-15
> **QIII said:**
> You shouldn't need to use vga-switcheroo any more.

[This]("https://wiki.ubuntu.com/X/Config/HybridGraphics") is the word on pxpress for ATI.  It goes up through 13.10, but it should be applicable to Trusty as well.

This seems to have been the ticket to success for about half the people I have suggested it to so far.

In the hardware requirements:
**A MUXless system with an Intel or an AMD integrated card and an AMD discrete card.**

But i don't think my laptop support muxless system.

---

### Post by martincigorraga on 2014-03-19
Same here on an HP Pavilion dv7-4287cl:
[B]
Graphics[/B]:  **Card-1**: Intel Core Processor Integrated Graphics Controller **bus-ID**: 00:02.0 **chip-ID**: 8086:0046 
**Card-2**: Advanced Micro Devices [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] **bus-ID**: 01:00.0 **chip-ID**: 1002:68c1

---

