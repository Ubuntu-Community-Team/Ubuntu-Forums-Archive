---
title: "Apple LED Display - USB Audio Prob - Tricky System"
date: 2012-08-22
forum: Ubuntu Studio
---

### Post by catfsh on 2012-08-22
Hi there everyone.

I've decided to use Ubuntu Studio for primarily electronic music production, having run out of money to spend on expensive Mac apps...

However I have a rather mad setup. I have around 10 genuine Apple Macs... including an old Quad G5 and a Mac Pro 3,1 with two hacked GPUs and two Apple displays (30" and 27") - and 8 cores with 10 GB of RAM. It's not exactly 'underpowered'...

My Linux box, however, blows the Mac Pro away - even with only one CPU. I built it to prove I still had my old Linux skillz (I only moved to OS X because it was Unix with MS Office... and Apple's continued restrictions have kept me at Snow Leopard, and pushing me towards Linux for new workstations).

It's based on an Intel i5-2500 overclocked mildly to 3.6 GHz with a silly cooler. 16 GB of RAM, booting off a 128 GB SSD (all I had lying around that was fast enough) and two 500 GB mechanical drives for volume storage. The logic board is a Gigabyte P67A-D3-B3 with onboard Intel HDA audio.

Just to make things complicated, I've installed two single-slot XFX brand ATI Radeon HD5770 graphics cards (the ones with Mini DisplayPort outputs...) and connected them together using a Crossfire bridge.

I've used the Ubuntu Studio 12.04 distro package for the AMD proprietary driver and then hacked up an xorg.conf file to enable Crossfire on the two GPUs. If this is actually quite difficult, and anyone wants to know my methodology, email me at lex at catfsh dot com.

Anyway the graphics are fast - running the same resolution and quality settings on Red Eclipse (random OpenGL game used for testing - I'm not much of a gamer any more - too old!), the Linux box blows away the Mac Pro. The Mac Pro has the Lion OpenGL kext because it has an EFI-hacked Radeon HD6870 card and another HD5770 installed. If the Linux box was running the single 5770 then the Mac Pro's 6870 theoretically *should* be quicker. It's not. Not by a long shot - but it was quicker before I finally got Crossfire working on the Linux box.

Note that my 3 hour constant Red Eclipse fullscreen @ 1920x1080 burn-in on the Linux box eventually screwed up the textures... but returning to the Ubuntu Studio desktop showed no problems. Temperatures were well within spec.

The reason I chose the XFX single-slot HD5770 was due to the Mini DisplayPort output, because I've got the Linux box hooked up to an Apple 24" LED Cinema Display, using the native Mini DisplayPort and the USB plugged into the back of the Gigabyte logic board.


My problem is that the USB peripherals in the Apple screen don't work. The Ubuntu Studio setup procedure, just like the standard Xubuntu 12.04 setup, notes the webcam in the display, and offers to take a photo... it activates the device (green LED on display lights up) but nothing is shown and no photo can be taken. Equally, I cannot use the Apple USB Display Audio.

Now I'm not bothered about the microphone because I've got a Blue Eyeball 2.0 for that (and I hope that Ubuntu Studio recognises it... it's the best quality mic I've got). But for the time being, for testing purposes I'd really like to use the display audio output to put some tunes together.

I could pull the harman/kardon soundsticks from the Mac Pro but it's my main 'leisure' machine and I've only got one set of Soundsticks. I don't have any external audio interface for the Linux box yet - and using the logic board's integrated Intel HDA audio via the headphone / line out jacks is noisy as hell and, frankly, unacceptable.


Are there any drivers available for the Apple LED Cinema Display range of USB devices? I'm using the Mini DisplayPort output on one GPU card (the other Crossfire'd in) but even on my Apple hardware, the Display Audio is controlled through the USB cable, *NOT* the DisplayPort (even if the spec supports audio). I get two audio controllers from the two graphics cards (presumably for HDMI output, but neither card has an HDMI output socket!) but neither 'miraculously' feed through the Mini DisplayPort.

Since Apple themselves operate the speakers, microphone and webcam on their LED Cinema Displays (both sizes) via the USB port on the octopus cable, is there any way of achieving this in Linux?

Or am I going to have to buy an external audio interface for the Linux box (not ideal - as extra money may as well buy me Ableton Live on the Mac Pro, for example...)?


I'd appreciate tips from those who have successfully used Apple display audio with Ubuntu Studio. I love Ubuntu Studio - it 'feels' as good as OS X - but I'm aware that I'm already pushing the boundaries with Crossfire'd dual ATI Radeons in the first place, esp. using the Mini DisplayPort outs! Am I being too ambitious here for my first 'big' Linux box?

---

### Post by jejeman on 2012-08-22
If I undestood correctly that LED display has inside usb sound card? If true, connect it with usb cable and give us output from
```
lsusb
```

---

### Post by smartboyhw on 2012-08-22
> **catfsh said:**
> Hi there everyone.
 
I've decided to use Ubuntu Studio for primarily electronic music production, having run out of money to spend on expensive Mac apps...
 
However I have a rather mad setup. I have around 10 genuine Apple Macs... including an old Quad G5 and a Mac Pro 3,1 with two hacked GPUs and two Apple displays (30" and 27") - and 8 cores with 10 GB of RAM. It's not exactly 'underpowered'...
 
My Linux box, however, blows the Mac Pro away - even with only one CPU. I built it to prove I still had my old Linux skillz (I only moved to OS X because it was Unix with MS Office... and Apple's continued restrictions have kept me at Snow Leopard, and pushing me towards Linux for new workstations).
 
It's based on an Intel i5-2500 overclocked mildly to 3.6 GHz with a silly cooler. 16 GB of RAM, booting off a 128 GB SSD (all I had lying around that was fast enough) and two 500 GB mechanical drives for volume storage. The logic board is a Gigabyte P67A-D3-B3 with onboard Intel HDA audio.
 
Just to make things complicated, I've installed two single-slot XFX brand ATI Radeon HD5770 graphics cards (the ones with Mini DisplayPort outputs...) and connected them together using a Crossfire bridge.
 
I've used the Ubuntu Studio 12.04 distro package for the AMD proprietary driver and then hacked up an xorg.conf file to enable Crossfire on the two GPUs. If this is actually quite difficult, and anyone wants to know my methodology, email me at lex at catfsh dot com.
 
Anyway the graphics are fast - running the same resolution and quality settings on Red Eclipse (random OpenGL game used for testing - I'm not much of a gamer any more - too old!), the Linux box blows away the Mac Pro. The Mac Pro has the Lion OpenGL kext because it has an EFI-hacked Radeon HD6870 card and another HD5770 installed. If the Linux box was running the single 5770 then the Mac Pro's 6870 theoretically *should* be quicker. It's not. Not by a long shot - but it was quicker before I finally got Crossfire working on the Linux box.
 
Note that my 3 hour constant Red Eclipse fullscreen @ 1920x1080 burn-in on the Linux box eventually screwed up the textures... but returning to the Ubuntu Studio desktop showed no problems. Temperatures were well within spec.
 
The reason I chose the XFX single-slot HD5770 was due to the Mini DisplayPort output, because I've got the Linux box hooked up to an Apple 24" LED Cinema Display, using the native Mini DisplayPort and the USB plugged into the back of the Gigabyte logic board.
 
 
My problem is that the USB peripherals in the Apple screen don't work. The Ubuntu Studio setup procedure, just like the standard Xubuntu 12.04 setup, notes the webcam in the display, and offers to take a photo... it activates the device (green LED on display lights up) but nothing is shown and no photo can be taken. Equally, I cannot use the Apple USB Display Audio.
 
Now I'm not bothered about the microphone because I've got a Blue Eyeball 2.0 for that (and I hope that Ubuntu Studio recognises it... it's the best quality mic I've got). But for the time being, for testing purposes I'd really like to use the display audio output to put some tunes together.
 
I could pull the harman/kardon soundsticks from the Mac Pro but it's my main 'leisure' machine and I've only got one set of Soundsticks. I don't have any external audio interface for the Linux box yet - and using the logic board's integrated Intel HDA audio via the headphone / line out jacks is noisy as hell and, frankly, unacceptable.
 
 
Are there any drivers available for the Apple LED Cinema Display range of USB devices? I'm using the Mini DisplayPort output on one GPU card (the other Crossfire'd in) but even on my Apple hardware, the Display Audio is controlled through the USB cable, *NOT* the DisplayPort (even if the spec supports audio). I get two audio controllers from the two graphics cards (presumably for HDMI output, but neither card has an HDMI output socket!) but neither 'miraculously' feed through the Mini DisplayPort.
 
Since Apple themselves operate the speakers, microphone and webcam on their LED Cinema Displays (both sizes) via the USB port on the octopus cable, is there any way of achieving this in Linux?
 
Or am I going to have to buy an external audio interface for the Linux box (not ideal - as extra money may as well buy me Ableton Live on the Mac Pro, for example...)?
 
 
I'd appreciate tips from those who have successfully used Apple display audio with Ubuntu Studio. I love Ubuntu Studio - it 'feels' as good as OS X - but I'm aware that I'm already pushing the boundaries with Crossfire'd dual ATI Radeons in the first place, esp. using the Mini DisplayPort outs! Am I being too ambitious here for my first 'big' Linux box?
 
Wait, you mean the Apple Thunderbolt Displays?
 
Please give us the model name and number of your display.
 
Well, it's good to pushing the boundaries:)
 
Regards,
Howard Chan
Ubuntu Studio Team Member in [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

