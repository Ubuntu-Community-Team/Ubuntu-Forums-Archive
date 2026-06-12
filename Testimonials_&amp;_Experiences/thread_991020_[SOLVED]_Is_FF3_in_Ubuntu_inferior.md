---
title: "[SOLVED] Is FF3 in Ubuntu inferior"
date: 2008-11-23
forum: Testimonials &amp; Experiences
---

### Post by ellalan on 2008-11-23
I am wondering whether FF3 provides an inferior product to Ubuntu than Vista. The reason is the fonts in Ubuntu is not up to the standard of that in Vista, this is only my opinion and there are many of you would differ from my observation and I am not going to argue about it as its a personal preference.
I have also noticed there are few themes provided by FF3 are exclusively for Vista.
Is there a way to make the fonts very much the same as vista's quality.

---

### Post by michaelzap on 2008-11-23
Just change the fonts used by Firefox in Edit -> Preferences -> Content (I use DejaVu fonts myself). If you generally don't like the way that fonts are displayed on your screen try modifying the settings in System -> Preferences -> Appearance -> Fonts. And if you specifically want Microsoft fonts on your system, you can install the msttcorefonts package via Synaptic or just copy the ones that you have on your Windows system to the hidden .fonts directory in your home folder.

---

### Post by steveneddy on 2008-11-23
> **michaelzap said:**
> Just change the fonts used by Firefox in Edit -> Preferences -> Content (I use DejaVu fonts myself). If you generally don't like the way that fonts are displayed on your screen try modifying the settings in System -> Preferences -> Appearance -> Fonts. And if you specifically want Microsoft fonts on your system, you can install the msttcorefonts package via Synaptic or just copy the ones that you have on your Windows system to the hidden .fonts directory in your home folder.

Yeah - msttcorefonts and sub pixel smoothing helped my fonts.

---

### Post by ellalan on 2008-11-23
Thank you for the responses, I have msttcorefonts installed, sub pixel smoothing enabled as well. As I am operating Intrepid using Wubi I could see the difference in certain web pages.
michaelzap, you mentioned copying Windows Fonts but I am unable to paste anywhere so that I can transfer to my .fonts in Intrepid. Could you please help me how can I achieve this.TIA.

---

### Post by michaelzap on 2008-11-23
> **ellalan said:**
> 
michaelzap, you mentioned copying Windows Fonts but I am unable to paste anywhere so that I can transfer to my .fonts in Intrepid. Could you please help me how can I achieve this.TIA.

You should be able to copy files to the .fonts directory, and fonts are just files like any other. You'd need to open the Fonts folder in your Windows installation and then copy them to .fonts. If you are trying to copy and paste and for some reason that's not working, just drag and drop instead (I've never tried Wubi, but Windows treats its Fonts folder differently from others so I expect that your issues are more getting the fonts selected in Windows than copying them to Ubuntu).

---

### Post by ellalan on 2008-11-23
Thanks michaelzap, it looks much better with the windows fonts and I am quite pleased about it,Thanks for your help again.

---

