---
title: "NVIDIA Driver 1.0-7664 Released"
date: 2005-06-02
forum: The Cafe
---

### Post by zenwhen on 2005-06-02
>  * Added OpenGL 2.0 Support.
*** Added initial support for Xinerama + OpenGL**; see APPENDIX V in the text README.
* Added support for the EXT_framebuffer_object OpenGL extension.
* Added NV-CONTROL support for manipulating DDC/CI settings; see the AllowDDCCI X config option in the text README.
*** Added support for GPU clock manipulation; see the "Coolbits" X config option** documented in Appendix D.
* Added support for NVIDIA Quadro G-Sync.
* Added support for GeForce 6200 AGP.
* Improved DPMS behavior on flatpanels.
* Removed support for legacy GPUs; please see "Chapter 1. Selecting and Downloading the NVIDIA Packages for Your System" in the README for details.
* Install NVIDIA OpenGL headers by default.

x86 - [http://www.nvidia.com/object/linux_display_ia32_1.0-7664.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7664.html)
AMD64 - [http://www.nvidia.com/object/linux_display_amd64_1.0-7664.html](http://www.nvidia.com/object/linux_display_amd64_1.0-7664.html)

README - [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt) 

They *look* great. I think I will wait for a Hoary package made by someone trustworthy before installing though.

---

### Post by gil-galad on 2005-06-02
Wow..that **does** look nice

---

### Post by sapo on 2005-06-02
Thats why i hate ATI

WHY GOD? WHY DID I BUY A 9800PRO???? WHYYYYYYYYYY??????????????  ](*,)

---

### Post by oddabe19 on 2005-06-02
[QUOTE=sapo]Thats why i hate ATI

WHY GOD? WHY DID I BUY A 9800PRO???? WHYYYYYYYYYY??????????????  ](*,)[/QUOTE]
 I installed it via nvidia-installer --update (i use the binary from their site)
so far so good, no speed increases... speaking of which...

how can i turn on fastwrites and SBA?

---

### Post by somuchfortheafter on 2005-06-03
[QUOTE=sapo]Thats why i hate ATI

WHY GOD? WHY DID I BUY A 9800PRO???? WHYYYYYYYYYY??????????????  ](*,)[/QUOTE]
i was thinking the same thing about my 9600xt but i found someone who traded their 5600ultra which even though its slightly slower it still owns in linux lol.

---

### Post by poofyhairguy on 2005-06-03
[QUOTE=somuchfortheafter]i was thinking the same thing about my 9600xt but i found someone who traded their 5600ultra which even though its slightly slower it still owns in linux lol.[/QUOTE]

I traded a pro in for that. It is slower in XP...but its a lot better in Windows. Go ebay.

---

### Post by poofyhairguy on 2005-06-03
[QUOTE=somuchfortheafter]i was thinking the same thing about my 9600xt but i found someone who traded their 5600ultra which even though its slightly slower it still owns in linux lol.[/QUOTE]

I traded a pro in for that. It is slower in XP...but its a lot better in linux. Go ebay.

---

### Post by somuchfortheafter on 2005-06-03
hmm i tried to upgrade and well its not working of course i am on the k7 kernel and that probably has somthing to do with it, as nothing seems to like this kernel except default ubuntu stuff...

---

### Post by wolovids on 2005-06-03
Does it fix this [bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=7183)?

---

### Post by oddabe19 on 2005-06-03
[QUOTE=somuchfortheafter]hmm i tried to upgrade and well its not working of course i am on the k7 kernel and that probably has somthing to do with it, as nothing seems to like this kernel except default ubuntu stuff...[/QUOTE]
 ```
sudo apt-get install linux-headers-`uname -r`
```

just like that.

That should install the headers. I use a k7 kernel myself and i have NO problems with anything i try to do.

---

### Post by Kyral on 2005-06-03
SCORE! Overclocking! BUt yah, I'm gonna wait for a package :D

---

