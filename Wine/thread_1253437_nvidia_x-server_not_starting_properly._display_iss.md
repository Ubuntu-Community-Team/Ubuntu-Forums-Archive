---
title: "nvidia x-server not starting properly. display issues"
date: 2009-08-30
forum: Wine
---

### Post by marshall31415 on 2009-08-30
Hi.

Firstly, my X-Server Settings is set to "fixed aspect ratio scaling"

I try and run WC3 through Wine and it works perfectly- apart from the scaling.

Upon startup, if I immediately launch WC3 - it does not scale.

If I close WC3, open the "X-Server Settings" the screen goes black for a second or two, I don't modify a single thing. I close the window, open WC3 and the scaling works perfectly. Whats going on?

Is it not starting properly?

---

### Post by cariboo on 2009-08-30
A bump to move this thread to the top of the page.

---

### Post by bl33d on 2009-08-31
> **marshall31415 said:**
> Hi.

Firstly, my X-Server Settings is set to "fixed aspect ratio scaling"

I try and run WC3 through Wine and it works perfectly- apart from the scaling.

Upon startup, if I immediately launch WC3 - it does not scale.

If I close WC3, open the "X-Server Settings" the screen goes black for a second or two, I don't modify a single thing. I close the window, open WC3 and the scaling works perfectly. Whats going on?

Is it not starting properly?

What card/driver/monitor/resolution/refresh rate are you using?

---

### Post by marshall31415 on 2009-08-31
I am using an nvidia 8800GTS 512.
22" Viewsonic VX2235wm
1680x1050 res
refresh rate is set to 60Hz

i am running the nvidia drivers that linux installed for me, under "hardware drivers". I believe it said that it was 180.

I tried to update with the latest nvidia drivers but I couldn't. It would stop and tell me that "X-Server is running, please close" or something like that

---

### Post by bl33d on 2009-08-31
> **marshall31415 said:**
> I am using an nvidia 8800GTS 512.
22" Viewsonic VX2235wm
1680x1050 res
refresh rate is set to 60Hz

i am running the nvidia drivers that linux installed for me, under "hardware drivers"

I tried to update with the latest nvidia drivers but I couldn't. It would stop and tell me that "X-Server is running, please close" or something like that

Ubuntu version?

---

### Post by marshall31415 on 2009-08-31
I am running Ubuntu 9.04 32 bit

---

### Post by bl33d on 2009-08-31
> **marshall31415 said:**
> I am running Ubuntu 9.04 32 bit

so 180.35?

---

### Post by marshall31415 on 2009-08-31
180.44

---

### Post by bl33d on 2009-08-31
> **marshall31415 said:**
> 180.44

are you using vga or dvi?

---

### Post by marshall31415 on 2009-08-31
> are you using vga or dvi?

I am using DVI

---

### Post by bl33d on 2009-08-31
> **marshall31415 said:**
> I am using DVI

just checking :P

do you know how 2 install the new drivers from nVIDIAs site?

---

### Post by marshall31415 on 2009-08-31
i download the file, extract it and get it running via terminal. it then tells me that I have to stop x-server- which I have no clue how to do

---

### Post by bl33d on 2009-08-31
> **marshall31415 said:**
> i download the file, extract it and get it running via terminal. it then tells me that I have to stop x-server- which I have no clue how to do

lol k nevermind then.

---

### Post by bl33d on 2009-08-31
have you tried running war3 in a virtual desktop

---

### Post by ackanao on 2009-08-31
Have you tried to save your X-Server settings to xorg.conf file - start Nvidia control panel from terminal:


```
gksu nvidia-settings
``` 

then goto "Save to X Configuration File".

---

### Post by bl33d on 2009-08-31
> **ackanao said:**
> Have you tried to save your X-Server settings to xorg.conf file - start Nvidia control panel from terminal:


```
gksu nvidia-settings
``` 

then goto "Save to X Configuration File".

would that help?

---

### Post by ackanao on 2009-08-31
In most cases - yes; You need to configure your X-Server properly if you want to use graphic intensive applications.

---

### Post by bl33d on 2009-08-31
> **ackanao said:**
> In most cases - yes; You need to configure your X-Server properly if you want to use graphic intensive applications.

k, ive never used the save thing before

---

### Post by marshall31415 on 2009-08-31
> **ackanao said:**
> Have you tried to save your X-Server settings to xorg.conf file - start Nvidia control panel from terminal:


```
gksu nvidia-settings
```then goto "Save to X Configuration File".

I tried as you suggested but no luck.

The scaling is off from startup. I run WC3 and the image is stretched.
I exit, load "Nvidia X Server Settings"- the screen goes black for a second- i close, without modifying anything.
I load WC3 and the scaling is now perfect, 4:3 with black bars.

If I set to virtual desktop it works fine, though I would prefer to be able to play full screen.

---

### Post by bl33d on 2009-08-31
> **marshall31415 said:**
> I tried as you suggested but no luck.

The scaling is off from startup. I run WC3 and the image is stretched.
I exit, load "Nvidia X Server Settings"- the screen goes black for a second- i close, without modifying anything.
I load WC3 and the scaling is now perfect, 4:3 with black bars.

If I set to virtual desktop it works fine, though I would prefer to be able to play full screen.


isnt the max res for war3 like 10/76?

---

### Post by marshall31415 on 2009-09-01
Hi guys. thanks for the help.

I ended up swapping it with a monitor from my dads office that auto-scales to 4:3.

---

