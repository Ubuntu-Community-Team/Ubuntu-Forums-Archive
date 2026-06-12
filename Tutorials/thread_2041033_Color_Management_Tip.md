---
title: "Color Management Tip"
date: 2012-08-11
forum: Tutorials
---

### Post by Rallg on 2012-08-11
Ubuntu (and some other Linux distros) now has color management capability. This is important to those who wish to print color pictures.

The general topic of color management is discussed on many sites devoted to photography, so I'm only going to provide a tip for Ubuntu users, particularly those who dual-boot with Windows, and maybe use an inexpensive laptop. My own is an ASUS 1005HA. It uses an Intel graphics card, which is typical of such consumer devices.

My computer was calibrated to create an *.icc profile for the monitor, using Windows. Making it "work" in Windows is a long story (merely selecting it does not work). But when I got it to work, the result was beautiful.

My Ubuntu desktop (12.10, now in dev) was always beautiful. To my surprise, when I used Ubuntu's color management, it was worse!

After investigation, I learned that on the Windows side, the graphics system has some functionality custom-added (probably at the factory) for Windows. When the *.icc monitor profile was made, it was with that functionality enabled. However, Ubuntu does not load that graphics functionality. As a result, the monitor *.icc profile that is correct for Windows, is very wrong for Ubuntu.

My point: If you are using color management with a monitor profile calibrated for Windows (or perhaps Mac), it may be wrong in Ubuntu. The *.icc file can still be read, but it's color table may be wrong.

On my speciic computer, Ubuntu looks good without any monitor profile applied (that is, generic sRGB can be applied).

This does not apply to color management files for output devices (printers). Those should be the same in any operating system, as long as the printer itself works.

---

