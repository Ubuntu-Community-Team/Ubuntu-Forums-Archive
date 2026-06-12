---
title: "KitCore Deluxe 30 day demo works with fst"
date: 2011-08-22
forum: Ubuntu Studio
---

### Post by sgx on 2011-08-22
[http://www.sonomawireworks.com/store/index.php?main_page=product_info&products_id=322](http://www.sonomawireworks.com/store/index.php?main_page=product_info&products_id=322)

Those needing a good percussion plugin, I was able to run the KitCore 30 day demo (from Sonoma Wireworks),
by using the fst command. It failed at first, but terminal output indicated it needed 

msvcp80.dll

Microsoft.VC80.CRT.manifest  (an xml file)

When these were downloaded and copied to the wine system32 folder, it started right up,

fst /home/username/.wine/drive_c/Program*Files/Steinberg/VstPlugins/KitCore.dll

 and midi and audio connected fine with qjackctl.
The sounds were spread over 3 octaves of my midi keyboard.
The samples in the provided kits are excellent, 24 bit, 48kHz, and a wide variety of rythms, fills, and styles are provided. You can mix and match the sounds to form new kits.

The Deluxe version has 103 drumkits, and 3000 midi beats, and is on sale til September. The download is about 370 meg.

DrumCore is similar, but includes a ton of percussion audio files,
as well as midi. The latin percussion samples and various cymbals
are a treat! Feature comparison chart:

[http://www.sonomawireworks.com/drumcore/downloads/DrumCoreKitCoreProductMatrix.pdf](http://www.sonomawireworks.com/drumcore/downloads/DrumCoreKitCoreProductMatrix.pdf)

Cheers

---

