---
title: "Control panel for sound card required"
date: 2009-10-11
forum: Ubuntu Studio
---

### Post by StephenHartley on 2009-10-11
Hi,

I have a Asus Xonar Essence STX PCI-E audio card installed.  Output is fine but the card has an header to connect to the case chassi for earphones out and mike in.  But the card needs telling which output, speakers or fp earphones, to use.  When installed in Windows a control panel is installed to enable easy switching.  Is a panel or similar available for 9.04 Jaunty or 9.10 Karmic x64?

---

### Post by StephenHartley on 2009-10-11
PS I'm using alsamixer in terminal but ideally would like a GUI that could be placed on the panel

---

### Post by StephenHartley on 2009-10-11
Got it sorted thanks

---

### Post by raboofje on 2009-10-11
> **StephenHartley said:**
> Got it sorted thanks

What was your solution, so others can take advantage of it?

---

### Post by StephenHartley on 2009-10-13
> **raboofje said:**
> What was your solution, so others can take advantage of it?


I've only managed to "sort it" for Jaunty (9.04).

When I initially installed the sound card it wasn't detected at all and followed the instructions from  
[SIZE=2][COLOR=navy][U]
**[COLOR=Black]Comprehensive Sound Problem Solutions Guide v0.5e[/COLOR]**[/U][/COLOR][/SIZE] an Ubuntu forum guide at this address,

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)   and the sound card worked.
[COLOR=Black]
I then updated to the latest version of ALSA,  (1.0.21) by following the instructions from [/COLOR]_**[SIZE=2][COLOR=Black][Upgrade Alsa (1.0.21) on Ubuntu Jaunty 9.04        ]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/")[/COLOR][/SIZE]**_

[COLOR=Black]http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/

Now, when I go in to 'Volume Control' I select the Alsa Mixer as the device and in the 'Options' tab I can select speaker, headphones or FP Headphones.

I'm trying for a similar result with 9.10 and will post back when I find a solution.  The above hasn't worked for me on 9.10, I still end up with Oxygen HD as the device.
[/COLOR]

---

