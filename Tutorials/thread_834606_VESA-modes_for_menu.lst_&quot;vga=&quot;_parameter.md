---
title: "VESA-modes for menu.lst &quot;vga=???&quot; parameter"
date: 2008-06-19
forum: Tutorials
---

### Post by Alirio on 2008-06-19
Since I expirienced some problems with my grub boot splash screen not appearing/ not centered / being in a wrong resolution on my ASUS MW201U Widescreen 1680x1050, I decided to write a little resume on what I found out. 

It seems that I am not the only trying to finde the right VESA-mode number for their resolution, so thats the table of what I have found:


The Source of the info:
[HTML]gentoo-wiki.com/HOWTO_fbsplash#Can.27t_find_the_required_video_mode_for_your_resolution_.28vesafb.29.3F[/HTML]
[HTML]wiki.ubuntuusers.de/Konsolen-Aufl%C3%B6sung[/HTML]
[HTML]www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html[/HTML]

Formfactor:	Resolution:
4x3		640x480 	800x600 	1024x768 

Color-	 4 bit	???		770		???	
depth:	 8 bit	768/769		771		773	
	15 bit	784		787		790	
	16 bit	785		788		791	
	24 bit	786		789		792	
	32 bit	???		???		???	

Formfactor:	Resolution:
4x3	 	1280x1024 	1152x864 	1600x1200

Color-	 4 bit	???		???		???
depth:	 8 bit	775		353		796/800
	15 bit	793		354		???/801
	16 bit	794		355		798/802
	24 bit	795		???		799/803
	32 bit	???		356		???

Formfactor:	Resolution:
16X10		1280x800	1440x900	1680x1050

Color-	 4 bit  ???		???		???
depth:	 8 bit 	867		864		864
	15 bit	???		865		???
	16 bit	868		866		865
	24 bit	869		867		866
	32 bit  ???		???		???

The ??? means I dont know/have not found, so please if anyone does know, feel free to add it to the list, there are many lucky newbees like me waiting for this.

the xxx/xxx means that I have found two diffrent codes for the same specific constelation. Better to have two than none...

for the ones who don't know how to change the VESA-mode do this:

first change usplash.conf:
```
sudo gedit /etc/usplash.conf
```

you get something like that: (my screen is 1680x1050)

# Usplash configuration file
xres=1680
yres=1050

Adjust the values according to your screen. Save and exit.

Now you must edit menu.lst
```
sudo gedit /boot/grub/menu.lst
```

Search for "vga=" in the lower section of the file and change the value according to the table. For me it's "vga=864". Save and exit.

Now you can restart and it should work.

---

### Post by teknowill on 2011-04-19
[COLOR=#000055][FONT=monospace]/boot/grub/menu.lst  

as of grub 2 is: 

[/FONT][/COLOR]/etc/default/grub.cfg

[https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)
[COLOR=#000055][FONT=monospace]
colors shouldn't matter in the terminal...

you should only change this if you "work" in the real terminal i.e. tty1-6

but in case of older Ubuntu or even openSuse 11.3:

_direct answer to tread topic:_
24/32 bit are the same for terminal/grub.

you can use hwinfo to find out what your cards codes are.
  
if you don't have it:
(Debian/Ubuntu)

sudo apt-get install hwinfo 
  
(openSuse)

sudo yast2 -i hwinfo

then:

sudo hwinfo --framebuffer

Source: [https://wiki.archlinux.org/index.php/GRUB](https://wiki.archlinux.org/index.php/GRUB)

if you want the decimal code #, hex # should work though.. 
[http://www.easycalculation.com/hex-converter.php](http://www.easycalculation.com/hex-converter.php)

i.e. 
0x0300 = 768 [/FONT][/COLOR][COLOR=#000055][FONT=monospace]640x400, 8 bits[/FONT][/COLOR]
[COLOR=#000055][FONT=monospace]0x0361 = 865 [/FONT][/COLOR][COLOR=#000055][FONT=monospace]1280x800, 24 bits[/FONT][/COLOR]
[COLOR=#000055][FONT=monospace]
Hope this helps complete your table.

-Bill

here's my list:

  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048, 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768, 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits

[/FONT][/COLOR]

---

### Post by Raymi.H on 2012-05-25
Someone might find this useful:

[HTML]http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers[/HTML]

---

