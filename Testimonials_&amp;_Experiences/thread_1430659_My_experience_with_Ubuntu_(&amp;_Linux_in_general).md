---
title: "My experience with Ubuntu (&amp; Linux in general)"
date: 2010-03-15
forum: Testimonials &amp; Experiences
---

### Post by oceanside on 2010-03-15
I first started playing with Linux, starting with the Xandros distro, back in 2005. I loved Xandros at first, but then started to get more interested in trying other distros. I tried Suse and Ubuntu and was pretty happy in general but got annoyed at some hardware issues, like sound and wifi (on a laptop) as well as software incompatibilities. Around 2007 I stopped using Linux pretty much altogether. I develop software for/on windows so I didn't really need to use it and I figured it just wasn't ready for the big time yet. 

Then, in 2009 I started hearing a lot more about ubuntu, both from the internet as well as my colleagues. I have 2 colleagues in particular who now only use ubuntu at home (and they have both their wife and kids hooked on it) =). I bought a new Windows 7 laptop just before my old laptop (supposedly) died. I had been wanting to have a new linux laptop so I decided to install kubuntu 9.10 on it (since I liked what I heard about the new kde). Turned out the laptop problem was hardware related (the nvidia GPU runs very hot) which I was able to (sort of) resolve with thermal paste on the gpu's heatsink. It still runs at about 77 deg F but at least I can use the machine (I'm welcome to any ideas to get this temperature down further).

Anyway, just wanted to say that I couldn't be happier with [k]ubuntu 9.10 so far. I'm really impressed at the driver/software support which is leaps and bounds better than what it was 3-5 years ago. Everything 'just works' which is great and I'm looking forward to continuing to use this distro much in the future (and most likely installing it on my next laptop).

---

### Post by kelvin spratt on 2010-03-15
do you mean 77 deg C as 77 deg F is fairly cold.

---

### Post by oceanside on 2010-03-15
I'm sorry, yes, I do mean Celsius. Here's an nvclock output:

```
-- General info --                                     
Card:           nVidia Quadro NVS 140M
Architecture:   G86 A2
PCI id:         0x429
GPU clock:      297.000 MHz
Bustype:        PCI-Express

-- Shader info --
Clock: 594.000 MHz
Stream units: 16 (1b)
ROP units: 4 (1b)
-- Memory info --
Amount:         128 MB
Type:           128 bit DDR3
Clock:          302.400 MHz

-- PCI-Express info --
Current Rate:   16X
Maximum rate:   16X

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 78C

-- VideoBios information --
Version: 60.86.3e.00.00
Signon message: Quadro NVS 140M VGA BIOS
Performance level 0: gpu 275MHz/shader 550MHz/memory 301MHz/1.15V/100%
Performance level 1: gpu 400MHz/shader 800MHz/memory 600MHz/1.20V/100%
VID mask: f
Voltage level 0: 1.15V, VID: 2
Voltage level 1: 1.20V, VID: 4
Voltage level 2: 1.25V, VID: 0

```

---

### Post by oceanside on 2010-03-17
Thought I'd post this in case it helps somebody else: using nvclock-gtk I was able to underclock my gpu and get the temperature down to 59 C.

---

