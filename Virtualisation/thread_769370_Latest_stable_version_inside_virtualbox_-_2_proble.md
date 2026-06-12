---
title: "Latest stable version inside virtualbox - 2 problems"
date: 2008-04-26
forum: Virtualisation
---

### Post by gottabeandrew on 2008-04-26
I have done search after search on here, on the virtualbox forums and on google but i have found absolutely nowhere with a working tutorial to solve these 2 problems. Today, i downloaded the latest version of ubuntu and i'm running it as a virtual machine inside virtualbox. My main operating system is vista.

Problem 1: I can't get the screen resolution to mine. I've installed guest additions but when i go in the file that it tells you to in tutorials (xorg.conf), i assume the file has been changed because the screen resolutions are nowhere to be seen and i therefore can't add to them or change them.

Problem 2: The windows mouse shows on top of the ubuntu mouse. How do i get rid of it?

---

### Post by pixel :-) on 2008-04-26
I would recoment to download an already installed VM.That way everything is setuped nicelly for you.

For the resolution,if it doesn't exist it ,simply means that the default values are taken,you can try the gui tool,it should have the same effect.

heres an example of the relevant section

Section "Monitor"
	Identifier   "Built-in LCD"
	HorizSync    31.5 - 48.5
	VertRefresh  60.0 - 60.0
EndSection

copy this and adapt it to your needs.Before you do anything,take a snap shot,in case it doesn't work.

---

### Post by jmcwb on 2008-04-27
all that you have to do for the xorg.conf after running Install Guest Additions is:  

Section "Device"
	Identifier	"Configured Video Device"
	**Driver		"vboxvideo"**
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection	"Display"
		Modes	"1152x864"
	EndSubSection
EndSection

NOTE: I added the "Display" SubSection since the default size appears to be 1024x768 and I like mine a little larger at 1152x864.

Sorry that I can't help you with the mouse question.

---

