---
title: "Wine resolution or font size issue????"
date: 2009-01-06
forum: Wine
---

### Post by Immolatus on 2009-01-06
I'm having trouble configuring Wine. I recall a while ago setting the resolution but.... The deal is that the configuration window is too big to fit in the wine desktop so I can't see all of the options or even save the changes that I can make. Any Ideas on how to fix this?

P.S. I tried uninstalling and reinstalling Wine but it came back with the same settings.

---

### Post by hikaricore on 2009-01-06
> wine explorer /desktop=hikaricorerocksmysocks,1024x768 winecfg

^_^

You'll be able to edit your setting after running it this way.
Other than that you'd have to edit wine's "registry" files stored in your home dir under **.wine**

Incidently you can also lanuch any single program under WINE this exact same way and save yourself future headaches.

Example:

> wine explorer /desktop=Title,800x600 programname.exe

---

### Post by Immolatus on 2009-01-06
Nope, no dice. I'm guessing I wasn't just supposed to copy and paste that but I did find this in the usr.reg in .wine:
"CaptionHeight"="18"
"CaptionWidth"="18"
"MenuFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,90,01,00,00,00,\
  00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,20,00,\
  44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"MenuHeight"="18"
"MenuWidth"="18"
I'm thinking that those 18's should be more like 10's but I don't wont to just start mucking about. What do you think?

---

### Post by Immolatus on 2009-01-06
Well it appears I was looking at the wrong thing altogether. The fix was to alter a line in ~/.wine/system.reg.
It had some ridiculous number there and I changed it to 60 dpi just to be safe. here is what it looks like now:

[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts] 1225516090
"FIXEDFON.FON"="vgafix.fon"
"FONTS.FON"="vgasys.fon"
"LogPixels"=dword:00000060
"OEMFONT.FON"="vgaoem.fon"

Much better, I hope this helps someone out there.:guitar:

---

### Post by hikaricore on 2009-01-07
Sorry bout that, I guess I thought you meant the font size and the screen res were two seperate issues. ^_^

Glad you got it fixed anyways.

---

### Post by Bladeforger on 2009-01-21
> **Immolatus said:**
> Well it appears I was looking at the wrong thing altogether. The fix was to alter a line in ~/.wine/system.reg.
It had some ridiculous number there and I changed it to 60 dpi just to be safe. here is what it looks like now:

[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts] 1225516090
"FIXEDFON.FON"="vgafix.fon"
"FONTS.FON"="vgasys.fon"
"LogPixels"=dword:00000060
"OEMFONT.FON"="vgaoem.fon"

Much better, I hope this helps someone out there.:guitar:
It did help someone else out there... ME!  Thanks.  This helped me fix the problem of turning the screen resolution up way too high to see all of the screen... just as described in the original post.

---

### Post by SilverPotato on 2009-01-22
This is easy!

If you have a separate boot for Windows (2K, XP, or Vista) you just copy the fonts from the *C:\Windows\Fonts\* folder into your Wine's *windows\fonts\* folder.

Simple as that.

---

### Post by deebocean on 2009-10-09
> **Immolatus said:**
> Well it appears I was looking at the wrong thing altogether. The fix was to alter a line in ~/.wine/system.reg.
It had some ridiculous number there and I changed it to 60 dpi just to be safe. here is what it looks like now:

[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts] 1225516090
"FIXEDFON.FON"="vgafix.fon"
"FONTS.FON"="vgasys.fon"
"LogPixels"=dword:00000060
"OEMFONT.FON"="vgaoem.fon"

Much better, I hope this helps someone out there.:guitar:

Thanks, it helped me a lot

---

