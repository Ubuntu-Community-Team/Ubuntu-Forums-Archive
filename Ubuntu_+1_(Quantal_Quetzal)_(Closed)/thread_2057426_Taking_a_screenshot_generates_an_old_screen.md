---
title: "Taking a screenshot generates an old screen"
date: 2012-09-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-09-13
This is the oddest thing I've ever seen. When I take a screenshot of a window or my desktop, I instead receive an older copy of the window or screenshot. What I mean, is that once I take a screenshot using gnome screenshot tool, I will forever get that screenshot when I try and take another. I'm running with the open drivers, under and amd/ati card. This happens using shutter, pressing 'printscreen', or using gnome screenshot tool.

If I use the import command (from imagemagick) on the command line, I get the proper screenshot. I'll try and post a video so you can see what I mean.

Has anyone come across this bizarre issue?

---

### Post by sammiev on 2012-09-13
Seems to work good here. Here is a copy of your post from a pic.

---

### Post by balloons on 2012-09-13
> **guitara said:**
> This is the oddest thing I've ever seen. When I take a screenshot of a window or my desktop, I instead receive an older copy of the window or screenshot. What I mean, is that once I take a screenshot using gnome screenshot tool, I will forever get that screenshot when I try and take another. I'm running with the open drivers, under and amd/ati card. This happens using shutter, pressing 'printscreen', or using gnome screenshot tool.

If I use the import command (from imagemagick) on the command line, I get the proper screenshot (well kind of, it's missing borders, and sometimes has old window artifacts). I'll try and post a video so you can see what I mean.

Has anyone come across this bizarre issue?

WOW! So more details emerge! This happens after running a wine program. Whatever my last screenshot was is forever ingrained. I took a video demonstrating everything, and guess what? It's 2 mins of the screenshot image -- no motion captured.. No video at all.

It *seems* like the xwindow buffer gets stuck and anything that images against it only gets that snapshot in time. I'm really at a loss.

Try running something in wine, then using your screenshot tools. Be sure to take a screenshot before running the wine program!

---

### Post by ventrical on 2012-09-13
All is well here running:

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)

---

### Post by sammiev on 2012-09-13
I do not run wine and it's not installed so I really can't test that function at this time. :(

---

### Post by ventrical on 2012-09-13
I installed wine, ran a program and still cannot emulate that bug.

---

### Post by Elfy on 2012-09-14
> **ventrical said:**
> I installed wine, ran a program and still cannot emulate that bug.

So did I.

---

