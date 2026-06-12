---
title: "Grays are more orange in colour"
date: 2012-09-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by CrByte on 2012-09-09
Hello,

So I am testing ubuntu 12.10 64bit on my computer, using Intel HD 3000.

one thing I have notice and want to know if anyone else has noticed but gray colours have an orange tinge to them. 

EG: 
on Windows and ubuntu 12.04 the top header is a light gray, on Ubuntu 12.10 its orange gray colour.

[http://www.google.com.au/search?client=ubuntu&channel=fs&q=ubuntuforums&ie=utf-8&oe=utf-8&redir_esc=&ei=W11NUOPUCPCYiAf3tIHABg](http://www.google.com.au/search?client=ubuntu&channel=fs&q=ubuntuforums&ie=utf-8&oe=utf-8&redir_esc=&ei=W11NUOPUCPCYiAf3tIHABg)

---

### Post by dino99 on 2012-09-10
every release has its own little changes into themes. Note that theming is one of the latest tweaks made before final release.

---

### Post by CrByte on 2012-09-11
> **dino99 said:**
> every release has its own little changes into themes. Note that theming is one of the latest tweaks made before final release.

It seems very silly having the system change the standard Hex/RGB colour scheme., I am a web developer when i want something to use #F1F1F1 i want it to look gray not orange. really hoping it changes for final release.

---

### Post by coffeecat on 2012-09-11
> **CrByte said:**
> It seems very silly having the system change the standard Hex/RGB colour scheme., I am a web developer when i want something to use #F1F1F1 i want it to look gray not orange. really hoping it changes for final release.

I very much doubt the system has changed any colours. #F1F1F1 looks to be grey on my fully updated Quantal system with Mobile 4 series Intel graphics, and the greys generally look much as they have done before. I can see no orange tinge to the greys.

> **CrByte said:**
> 
EG: 
on Windows and ubuntu 12.04 the top header is a light gray, on Ubuntu 12.10 its orange gray colour.

What do you mean by top header? If you are using the default Ambiance theme, the menu bar and upper parts of app windows are dark grey. With radiance, the menu bar comes out light grey for me without a hint of orange.

Try installing gcolor2 and picking the affected grey colours to see what hex values you are getting.

---

### Post by effenberg0x0 on 2012-09-11
Are you using the correct ICC profile and adjustments for your monitor / VGA Card? (see Dash / Color)

I'm not a professional or a designer like you but I have recently purchased some professional monitors and I had to get a proper ICC profile from [http://www.tftcentral.co.uk/articles/icc_profiles.htm](http://www.tftcentral.co.uk/articles/icc_profiles.htm). 

I know nothing about it but there are many tutorials online. I followed a few and managed to adjust Brightness/Contrast/Gama, correct White/Black levels, etc. Then I asked a friend that is a photographer to test/adjust my monitors using a professional screen calibrator. 

I have borrowed a Pantone chart to compare to my screen and it looks pretty close now in Ubuntu 12.10, and better than it does on W7 (with default settings - no ICC profile). 

Also, I've been told you can't trust colors when using standard VGA cables: You have to be in DVI/HDMI to calibrate properly (digital signal is the exact RGB, while analog signal is not).

Regards,
Effenberg

---

### Post by CrByte on 2012-09-11
> **coffeecat said:**
> 


What do you mean by top header? If you are using the default Ambiance theme, the menu bar and upper parts of app windows are dark grey. With radiance, the menu bar comes out light grey for me without a hint of orange.

I am talking on the website like on Ubuntu forums looking at all the Gary background they are more orange.

> **effenberg0x0 said:**
> Are you using the correct ICC profile and adjustments for your monitor / VGA Card? (see Dash / Color). 


I am using HDMI to connect my screen, I'll have a look at the ICC profile when I get to the computer.

---

### Post by CrByte on 2012-09-13
When i open up the Color program the button to calibrate it is not clickable and when i hover over it a message saying my screen does not support it?

EDIT: BTW the screen is a BenQ 27" GL2750, Also could it be the HDMI as i was using VGA before when using ubuntu 12.04 but then again in windows its fine with HDMI. :S

---

### Post by effenberg0x0 on 2012-09-13
> **CrByte said:**
> When i open up the Color program the button to calibrate it is not clickable and when i hover over it a message saying my screen does not support it?

The "Calibrate" button in gnome-control-center color is disabled for me too. The two profile buttons (Add/Remove) are activated, as well as "View details". Maybe the Calibrate option is still in development,  I really don't know. 
> **CrByte said:**
> 
EDIT: BTW the screen is a BenQ 27" GL2750, Also could it be the HDMI as i was using VGA before when using ubuntu 12.04 but then again in windows its fine with HDMI. :S

I am not sure, I don't play much with Windows anymore. Maybe when it detects your monitor it downloads software for it via Windows Update? 

We know Windows, Macs use different gamma levels as default. I imagine Ubuntu probably does it too. But if I were a Monitor manufacturer I would make sure my colors look right on Windows OS, considering most of my products would be implemented in systems using this OS. 

Other people seem to be interested in fixing colors in Ubuntu, have a look [here]("http://www.ubuntufieldmanual.com/?q=node/38") for example.
 
When I installed my monitors I had 0 knowledge about it, which is not so different from my situation now. I just felt colors were weird and Google'd Monitor Calibration. I was already using high quality Dual DVI Cables, so I could disregard many hits. I went through the simple stuff like [this]("http://displaycalibration.com/"). When I finally got to test some ICC profiles and found the complicated stuff ([here - look at the charts]("http://www.tftcentral.co.uk/reviews/dell_u2412m.htm")) I realized I was out of my league and not in the mood to become a monitor expert - not useful for me. So I called a friend that has a spectrophotometer/colorimeter, knows what to do with it and thinks this is the most important thing ever, to do the work for me :)

I couldn't find a BenQ G**L** 2750 at TFTCentral.co.uk ICC profiles, but I did find 2 profiles for G**W**2750. Maybe you could give them a try. 
 
Regards,
Effenberg

---

### Post by CrByte on 2012-09-13
Fix the issues,

Done the reset all on the monitor its self, when it came on the screen saying auto, all the colours came good :D

---

