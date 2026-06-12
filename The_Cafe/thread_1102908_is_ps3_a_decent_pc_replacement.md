---
title: "is ps3 a decent pc replacement?"
date: 2009-03-22
forum: The Cafe
---

### Post by KhaaL on 2009-03-22
I've been going and thinking for a long time about selling my desktop computer and put my hands on a PS3 instead. However since I barely touched a PS3 I have a lot of questions in mind:

* How well does linux work on it? as i understand, hardware acceleration is disabled, so is video playback remotely possible without tearing?

* How is switching between the console and the OS, do you have to "reboot" in order to play PS3 games or is switching quick as fast-user switching here in ubuntu?

* last but not least, will i be able to use my PC keyboard and mouse with the ps3?


If you've had a PS3 for a while, slease do tell your experience with it!

---

### Post by CK05 on 2009-03-22
PS3 is an entertainment unit. It's best as a TV recorder, Game Console (obviously) and a Media receiver. 

Not a PC!


- PS3 Media Streamer....enough said. Don't boot into linux to play videos. Use this software, truly amazing program. You can even stream web TV, internet radio, picture blogs everything, you are free to add or delete channels. Should be essential with a PS3!
- Never tried installing so I can't comment on booting between different OS's. Maybe look at Youtube for demos.
- You can use Keyboard with PS# when you browse, but I haven't used a mouse for browsing but I'm most positive that you can since some games support kb+m.

---

### Post by LiamWilson on 2009-03-22
Seconded. Linux works well on the PS3, but's it's not an ideal replacement for a Desktop.

---

### Post by KhaaL on 2009-03-22
Care to tell **why** its not a good pc replacement?

---

### Post by insane_alien on 2009-03-22
same reason a chest of drawers isn't a good PC replacement. it was never designed to BE a PC replacement.

---

### Post by FLMKane on 2009-03-22
I think that since it uses Cell processors most applications wont work on it. Not sure though

---

### Post by hyperdude111 on 2009-03-22
I have tried ubuntu on ps3 and it is nothing compared to ubuntu on pc.

1. Very poor application support! The ps3 is the same architecture as Powerpc you will only find 1 in 100 apps with ps3 support. None of my desktop apps that are not pre-installed have a .deb for ps3/powerpc you will be stuck with the default apps.

2. SLOW! with only 256 mb of RAM and a slow cpu the ps3 is slow as it comes and with limited hard drive space Swap has to be kept to a minimum.

3. Resolution. Because it is on a TV and not a monitor you will be stuck with a rather irritating screen resolution and a 1.5 inch (3.81cm) black border all around the edge of the screen.

To switch back to ps3 os you need to re-boot

You need to go to the ps3 os for Games

Video does work fine just no 3d support.

No support for ps2 keyboard and mouse, they must be usn.


To conclude: Don't bother, the ps3 has native support for most video formats and music and comes packed with its own Web browser. Although it was a fun thing to do it was just a waste of time. PS3 ubuntu is so limited, your better off sticking to your desktop.

---

### Post by mamamia88 on 2009-03-22
like people said it works but is relatively slow. you are limited to 10gb memory and i don't believe you get acess to the video card

---

### Post by Swagman on 2009-03-22
Yellow Dog is the recommended alternate Os for Ps3.

---

### Post by tsali on 2009-03-22
It's terrible as PC. Basic web media (flash) isn't supported.

I bought mine with the intent of having an internet station...bluetooth keyboard and everything...only to be SORELY disappointed.

It is an excellent blueray player and streams networked Windows Media wonderfully.

---

### Post by hyperdude111 on 2009-03-23
> **tsali said:**
> It's terrible as PC. Basic web media (flash) isn't supported.

I bought mine with the intent of having an internet station...bluetooth keyboard and everything...only to be SORELY disappointed.

It is an excellent blueray player and streams networked Windows Media wonderfully.

Flash does work use " sudo apt-get install ubuntu-restricted-extras"

---

### Post by gletob on 2009-03-23
IIRC the only reason Sony included that feature was to get around some tax in Europe.

---

### Post by solitaire on 2009-03-24
Think Linux in a PS3 is more like a Nettop (desktop version of a netbook!) than a desktop replacement.

Good for simple stuff, nothing thats GPU intensive...

---

### Post by Neo_The_User on 2009-03-24
I've been a Playstation 3 developer for about 2 1/2 years now and a Playstation 3 as a replacement for a computer is a definite No. Dispite the fact the CPU is clocked at 3.2 GHz (which could easily do 3.6 or 3.7 GHz hands down) it feels incredibly slow unless you tear down the hypervisor, which I'm not going to explain how. The only way if you want to use a PS3 as a replacement for a PC is to re-flash the BIOS, get rid of the hypervisor, and set the linux shell on 7 cores rather than just 5. It feels like a Pentium I processor out of the box on linux. Then you have to install the nvidia drivers for the 3d accleration. Since the RSX is based on the GeForce 7000 series arcitecture, it would work as long as the hypervisor doesn't interfere. It's an extremely complex process and you'll need to fetch a ton of datasheets including the one for the Actel PROASIC 3 A3P060.

---

