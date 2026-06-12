---
title: "Can't change my monitor refresh rate to anything other than 48hz and 60hz"
date: 2023-10-21
forum: Ubuntu/Debian BASED
---

### Post by bumita on 2023-10-21
Hi, I'm trying to overclock my monitor to 90hz.
I've successfully done it on Windows 10 using this setting:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292895&stc=1[/IMG]
When I tried doing it with xrandr and [this calculator]("https://www.epanorama.net/faq/vga2rgb/calc.html"), it gave this error:
```

[FONT=monospace][COLOR=#54ff54]**bumita@bumita-latitude3500**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ xrandr --newmode "960x540_90"   55.44   960 1008 1040[/COLOR]
 1120   540 543 548 550  +hsync  
[COLOR=#54ff54]**bumita@bumita-latitude3500**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ xrandr --addmode eDP-1 960x540_90 [/COLOR]
[COLOR=#54ff54]**bumita@bumita-latitude3500**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ xrandr --output eDP-1 --mode 960x540_90 [/COLOR]
xrandr: Configure crtc 0 failed
[/FONT]
```
I also found out that I can't change the refresh rate to anything other than 48hz and 60hz.
```

[FONT=monospace][COLOR=#54ff54]**bumita@bumita-latitude3500**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cvt 960 540 55 [/COLOR]
# 960x540 54.69 Hz (CVT) hsync: 30.62 kHz; pclk: 36.75 MHz 
Modeline "960x540_55.00"   36.75  960 992 1080 1200  540 543 548 560 -hsync +vsync 
[COLOR=#54ff54]**bumita@bumita-latitude3500**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ xrandr --newmode "960x540_55.00"   36.75  960 992 108[/COLOR]
0 1200  540 543 548 560 -hsync +vsync 
[COLOR=#54ff54]**bumita@bumita-latitude3500**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ xrandr --addmode eDP-1 960x540_55.00 [/COLOR]
[COLOR=#54ff54]**bumita@bumita-latitude3500**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ xrandr --output eDP-1 --mode 960x540_55.00 [/COLOR]
xrandr: Configure crtc 0 failed
[/FONT]
```
How do I fix this?

---

