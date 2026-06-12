---
title: "Nvclock 0.8"
date: 2005-08-31
forum: Requests
---

### Post by psoleko on 2005-08-31
Requesting the new Nvclock .8 Beta, old one never worked for me.  ](*,) 

New functionality includes:
GeforceFX/6/7 support (experimental overclocking: Coolbits + low-level)
Pipeline modding for NV4x cards
Smartdimmer support for 6200Go based laptops
Hardware monitoring for LM99/MAX6659/F75375S/W83L785R chipsets
Support for internal NV43/NV44/NV47 temperature sensor
Ability to enable disabled temperature sensors used on NV43/NV44/NV47 boards
Fanspeed adjustment for FX5900/6600GT/6800GT boards and F75375S/W83L785R sensors OpenGL options using NV-CONTROL extension
Rewritten GTK2 interface
Bios parsing (GeforceFX/6/7) X86-64 support
Windows support for debugging purposes

---

### Post by anacron on 2005-09-03
first of all, download the file from [NVclock homepage](http://www.linuxhardware.org/nvclock/) and then extract it(I did that in nautilus by right clicking) Open up the console and then in the folder you extracted the files, just type:
```

./configure --prefix=/usr/local
```
then:
```
make
```
and finally:
```
sudo checkinstall
```
note: if you don't have checkinstall, you can get it by typing "sudo aptitude install checkinstall", (you can also use "make install", but i've heard that check install is much better, don't ask me why!. same with the "aptitude", use "apt-get" or "synaptic" if you wan't) 

i'll hope this help  ;-)

---

### Post by jamo on 2005-09-04
If you want the qt-frontend, you have to specify the correct qt-path which is /usr/share/qt3. Otherwise it will not be build. 
I prefere to compile both, so the complete command to invoke configure should be:

```
./configure --prefix=/usr -with-qtdir=/usr/share/qt3
``` 
Have fun :)

---

