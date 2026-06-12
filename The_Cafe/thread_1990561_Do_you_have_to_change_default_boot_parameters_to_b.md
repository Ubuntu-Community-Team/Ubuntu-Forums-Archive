---
title: "Do you have to change default boot parameters to boot correctly?"
date: 2012-05-29
forum: The Cafe
---

### Post by user1397 on 2012-05-29
Just wondering how many people have to do this.  I'm talking about when you edit the kernel boot line in grub and you pass a parameter such as acpi=force or something.

I myself have to, the best parameter I've found so far for my configuration is acpi_backlight=vendor, which fixes my boot, suspend/resume, and wireless issues.

---

### Post by jonedney on 2012-05-29
Nothing to edit; run straight Ubuntu 12.04 :)

---

### Post by Bachstelze on 2012-05-29
Haven't had to do that since last century...

---

### Post by zombifier25 on 2012-05-29
Maybe someone with laptops that are not certified to run with Ubuntu may have to, but I own a good old (literally old, as in 5 years old) desktop.

---

### Post by deadflowr on 2012-05-30
I've never had to do that. However, I do have to set the nomodeset option whenever booting into a live CD on my father's HP.

---

### Post by Paqman on 2012-05-30
> **Bachstelze said:**
> Haven't had to do that since last century...

^ This.

ACPI used to be a pain, lots of mobos would require twiddling to get them to play properly, but there's been a massive improvement over the last few years.

In fact hardware support in general has got immensely better. We used to have endless problems with ACPI, sound, wifi, etc. But these days it's pretty sorted.

---

### Post by user1397 on 2012-05-30
> **Paqman said:**
> ^ This.

ACPI used to be a pain, lots of mobos would require twiddling to get them to play properly, but there's been a massive improvement over the last few years.

In fact hardware support in general has got immensely better. We used to have endless problems with ACPI, sound, wifi, etc. But these days it's pretty sorted.

Not me :(

---

### Post by Paqman on 2012-05-30
> **ubuntuman001 said:**
> Not me :(

Well, I do wonder if the fact I seem to have little trouble these days is somewhat due to the fact that I wouldn't ever buy hardware that I thought didn't work well...

---

### Post by JDShu on 2012-05-30
My old Samsung Q310 can't run 64bit operating systems without disabling acpi in the bootloader. Not OS specific though as I've seen forum posts by people trying to install 64bit Windows on it have the same problem. Samsung just doesn't support it in the BIOS apparently.

---

### Post by user1397 on 2012-05-30
> **Paqman said:**
> Well, I do wonder if the fact I seem to have little trouble these days is somewhat due to the fact that I wouldn't ever buy hardware that I thought didn't work well...

yup, I'm usually more careful, I guess I just didn't figure that an all intel lappy (i3 and intel HD graphics) would ever give me any problems, but oh well, I found a solution :) (I edited my first post)

---

### Post by ssam on 2012-05-30
yes, lenovo ideapad S12 needs nolapic_timer otherwise it will occasionally freeze until you press a key or move the touchpad. (i have not tried ubuntu 12.04 on it yet, but fedora 17 still has the issue)

---

### Post by user1397 on 2012-06-06
bump

---

### Post by Copper Bezel on 2012-06-06
No. I *did* briefly experience the 3.0 power regression bug (for me, it caused a serious heat issue) and need to add that pcie_aspm=force bit, but that was fixed rather quickly.

---

### Post by wilee-nilee on 2012-06-06
I'm lucky all my computers run with a stock cd boot or install.

On is a toshiba laptop that has a whole bunch of additional drivers needed but Ubuntu sees these and with one click it runs great.

---

### Post by phibxr on 2012-06-06
The last time I had to change my boot parameters to be able to boot correctly must have been around 2003.

I actually think I had to change them to avoid random system freezes around 2007-2008, due to bad support from a motherboard manufacturer, but since then I've been able to run with the default values. :)

---

### Post by scouser73 on 2012-06-06
Never had to do that.

---

