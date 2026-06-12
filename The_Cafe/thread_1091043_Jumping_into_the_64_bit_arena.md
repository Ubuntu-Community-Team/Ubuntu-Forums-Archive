---
title: "Jumping into the 64 bit arena??/"
date: 2009-03-09
forum: The Cafe
---

### Post by OZFive on 2009-03-09
How is the water over here in the big pool?


Possibly a build from Dell, any feedback on it and compatibility with Ubuntu?
My Components
SYSTEM COLOR	Jet Black
PROCESSOR	Intel® Core™ 2 Duo T9550 (2.66GHz/1066Mhz FSB/6MB cache)
OPERATING SYSTEM	Genuine Windows Vista® Home Premium Service Pack 1 64 Bit
OFFICE SOFTWARE	Microsoft® Works Plus 2008
WARRANTY AND SERVICE	2Yr Ltd Hardware Warranty, InHome Service after Remote Diagnosis	
HD DISPLAY	Bright, Hi Resolution, glossy widescreen 17.0 inch RGB LED display (1920x1200)	
MEMORY	4GB Shared Dual Channel DDR2 at 800MHz
HARD DRIVE	SIZE: 250GB SATA Hard Drive (7200RPM) with Free Fall Sensor
VIDEO CARD	256MB ATI Mobility Radeon HD 3650
OPTICAL DRIVE	8X Slot Load CD / DVD Burner (Dual Layer DVD+/-R Drive)
WIRELESS CARDS	Intel®WiFi Link 5100 802.11agn Half Mini-Card
BLUETOOTH	Dell Wireless 370 Bluetooth Internal (2.1)
INTEGRATED WEBCAM	Integrated 2.0M Pixel Webcam
BATTERY OPTIONS	56 Whr Lithium Ion Battery (6 cell)
SOUND OPTIONS	High Definition Audio 2.0
KEYBOARD	Back-lit Keyboard
FINGER PRINT READER	Integrated Finger Print Reader

---

### Post by OZFive on 2009-03-09
Anyone using 64bit Ubuntu?

Anyone?

Bueller?

---

### Post by Vince4Amy on 2009-03-09
As with Most distros Ubuntu is good when it comes to the 64bit version, most of the applications are 64 bit and the ones which aren't are either closed source so cannot be compiled for x64 for example Skype or cannot possibly be compiled into x64 for example ZSNES which was written in 32-bit ASM code so it's not possible to compile an x64 build.

If you should need them 32-bit Applications will be installable using ia32-libs ```
sudo apt-get install ia32-libs
```

Adobe Flash Player has an alpha build for x64 Flash and Java as of Update 12 includes an x64 browser plugin so you should be good to go.

---

### Post by whoop on 2009-03-09
I am. Not sure what your question is. But I would recommend running a 64 bit livecd and seeing how it performs.

---

### Post by Eisenwinter on 2009-03-09
I use 64bit Arch, and it runs perfectly.

---

### Post by Chemical Imbalance on 2009-03-09
64-bit is good to go.  Everything works great (and faster in my experience).  As has been said, if you need to, you can run 32 bit apps with the proper libs

---

### Post by Thelasko on 2009-03-09
It runs wonderfully.  I've been running 64-bit since Feisty.  It just gets better and better.  I expect Jaunty will take 64-bit to a new level with native 64-bit support for Flash and Java in the repositories.

I currently have native 64-bit Flash and Java working in Hardy.  I just had to install them manually.  A few minutes in the command line (for Java only) and it works, no problem.

Even if you are afraid of the command line, Intrepid users can install 64-bit Java via OpenJDK and and 32-bit Flash with ndispluginwrapper using synaptic.

---

### Post by steveneddy on 2009-03-09
I think that's the wrong color to run 64 bit successfully.

/jk :D

I think you would be happier buying from [System76]("http://www.system76.com/").

Lots better customer service and better hardware.

Customer service at [System76]("http://http://www.system76.com/") rocks, also!

---

### Post by johnjohn2 on 2009-03-09
64 bit is only good when being used with more than 4 gig of ram i currently have 8 gig and therefore i need 64bit.

it is utterly pointless using 1 gig and having 64 bit installed.

RegardsJohn

---

### Post by johnjohn2 on 2009-03-09
nvidea alsowork alittle better than ATI

---

### Post by Vince4Amy on 2009-03-09
> **johnjohn2 said:**
> nvidea alsowork alittle better than ATI

What the heck has that got to do with the OP. It works as good as it does on 32-bit.

---

### Post by Stan_1936 on 2009-03-09
....which is not as good as NVIDIA(on 32-bit).

---

### Post by Vince4Amy on 2009-03-09
This is not an ATi vs nVidia debate.

---

### Post by Stan_1936 on 2009-03-09
> **OZFive said:**
> How is the water over here in the big pool?


Possibly a build from Dell, **any feedback on it and compatibility with Ubuntu?**
My Components
SYSTEM COLOR	Jet Black
PROCESSOR	Intel® Core™ 2 Duo T9550 (2.66GHz/1066Mhz FSB/6MB cache)
OPERATING SYSTEM	Genuine Windows Vista® Home Premium Service Pack 1 64 Bit
OFFICE SOFTWARE	Microsoft® Works Plus 2008
WARRANTY AND SERVICE	2Yr Ltd Hardware Warranty, InHome Service after Remote Diagnosis	
HD DISPLAY	Bright, Hi Resolution, glossy widescreen 17.0 inch RGB LED display (1920x1200)	
MEMORY	4GB Shared Dual Channel DDR2 at 800MHz
HARD DRIVE	SIZE: 250GB SATA Hard Drive (7200RPM) with Free Fall Sensor
**VIDEO CARD	256MB ATI Mobility Radeon HD 3650**
OPTICAL DRIVE	8X Slot Load CD / DVD Burner (Dual Layer DVD+/-R Drive)
WIRELESS CARDS	Intel®WiFi Link 5100 802.11agn Half Mini-Card
BLUETOOTH	Dell Wireless 370 Bluetooth Internal (2.1)
INTEGRATED WEBCAM	Integrated 2.0M Pixel Webcam
BATTERY OPTIONS	56 Whr Lithium Ion Battery (6 cell)
SOUND OPTIONS	High Definition Audio 2.0
KEYBOARD	Back-lit Keyboard
FINGER PRINT READER	Integrated Finger Print Reader

**There's the problem.**

---

### Post by Vince4Amy on 2009-03-09
It's not a problem.

---

### Post by Roberticus on 2009-03-09
> **johnjohn2 said:**
> 64 bit is only good when being used with more than 4 gig of ram i currently have 8 gig and therefore i need 64bit.

it is utterly pointless using 1 gig and having 64 bit installed.

RegardsJohn
Um, no. 
[http://www.linuxmint.com/rel_elyssa_x64.php#benchmark](http://www.linuxmint.com/rel_elyssa_x64.php#benchmark)

"The desktop also felt snappier and more responsive under x64, especially launching and switching between applications felt faster."

I can say the same on my laptop, Ubuntu 64bit on Acer Aspire 5520 with 2GB RAM.

---

