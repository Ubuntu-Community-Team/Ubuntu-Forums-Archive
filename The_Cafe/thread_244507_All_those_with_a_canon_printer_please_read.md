---
title: "All those with a canon printer please read"
date: 2006-08-26
forum: The Cafe
---

### Post by DoctorMO on 2006-08-26
I'm working with Markus trying to get more information about Canon printers and how they make requests for ink levels, I have an iP5000, I've managed to get results for an MP360 and an iP4000. if you would like to help with this hardware research post here and I will give you details of how to gather the information we need.

Best Regards, Martin Owens

---

### Post by rado_london on 2006-08-26
> **DoctorMO said:**
> I'm working with Markus trying to get more information about Canon printers and how they make requests for ink levels, I have an iP5000, I've managed to get results for an MP360 and an iP4000. if you would like to help with this hardware research post here and I will give you details of how to gather the information we need.

Best Regards, Martin Owens

finally someone to do do the MP360. I can help you bby testing it or givirng out some info. Just tell me what and how to get it.

---

### Post by DoctorMO on 2006-08-26
Great ok, thats 1, is anybody else willing to help?

---

### Post by grte on 2006-08-26
I've got an iP1500.  Anything I can do to make the blasted thing work.

---

### Post by DoctorMO on 2006-08-26
grte welcome, this is how it works for usb:

Install TurboPrint from [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) once installed add your printer (iP1500) using the links which should have apeared on your desktop, once printer is added: run on the command line: `sudo tpconfig`

This should present you with a text menu, 0 [enter] to select the first printer on your computer, T [enter] to select the toolbox, I [enter] to get the ink level. varify that the information is correct.

exit out using [ctrl]-C.

Now run `sudo -s 255 strace tpconfig 2> ~/Desktop/ip5000.trace` and follow the same sequence as above to print the ink levels, and quit once they've been printer to the screen.

Now send me that file, a bit complex but it does help up understand the hardware a bit more. you should also be able to print with turbo print, but it puts those horrible water marks on the paper unless you pay though :-(.

---

### Post by RRS on 2006-08-26
S750 here, Cannon doesn't seem to offer windows drivers anymore.I remember something about a "hardware failure" under Dapper so I may not be able to help much but let me know.

---

### Post by DoctorMO on 2006-08-26
RRS, you could follow the same quidlines as above since turboprint says it supports S750 too. (btw is that the one with the scanner?)

---

### Post by nalmeth on 2006-08-26
I have an older canon at home, which is out of black ink. It won't work at all without ink, let alone ask for more :-\"

When I get home I can post the model number, and any other info I can dig up

---

### Post by RRS on 2006-08-26
> .....same quidlines as above since turboprint says it supports S750 too. (btw is that the one with the scanner?)

No scanner, just a basic usb color inkjet.

Had it working pre-Ubuntu but after a windows reinstall couldn't find a replacement driver.

Had tried setting it up (with cups if I recall) some time ago and couldn't make it work, though a driver seemed to install ok and Ubuntu could see it. I'll try your suggestions later this evening or in a.m. and post back.

Thanks, hopefully we can help each other.

---

### Post by grte on 2006-08-27
> **DoctorMO said:**
> grte welcome, this is how it works for usb:

Install TurboPrint from [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) once installed add your printer (iP1500) using the links which should have apeared on your desktop, once printer is added: run on the command line: `sudo tpconfig`

This should present you with a text menu, 0 [enter] to select the first printer on your computer, T [enter] to select the toolbox, I [enter] to get the ink level. varify that the information is correct.

exit out using [ctrl]-C.

Now run `sudo -s 255 strace tpconfig 2> ~/Desktop/ip5000.trace` and follow the same sequence as above to print the ink levels, and quit once they've been printer to the screen.

Okay, I'll do that in a moment.

> Now send me that file, a bit complex but it does help up understand the hardware a bit more. you should also be able to print with turbo print, but it puts those horrible water marks on the paper unless you pay though :-(.

I classify watermarked pages as not-working, myself.

---

### Post by grte on 2006-08-27
Bit if a problem, actually.  When I enter the toolbox, there is no option to check ink levels.

---

### Post by DoctorMO on 2006-08-27
You have to run it in sudo or there won't be any ink levels. unless turboprint doesn't support inklevels for canon 1500. hmm.

---

### Post by grte on 2006-08-27
That seems to be the case.  I definately ran the command with sudo.

---

### Post by RRS on 2006-08-27
Installed and configured Turboprint as recommended but still no-go.

Turbo print seems to find/recognize the printer and it shows up in device manager with no error messages, etc. Cups maneger seems to be ok too.

When I try to print a test page I get a "device not connected" and the printers LED alternates green/yellow rather then solid green.

I'm thinking the problem is with the printer itself or maybe just a bad USB cable but don't have anymore time to troubleshoot today.

I'll try reposting later for help in the hardware section of the forum and if I get it working I'll get back to you with the info you're looking for.

Sorry I can't help with your project at the moment but thanks for the Turboprint info, would've taken me awhile to stumble on it myself.

---

### Post by DoctorMO on 2006-08-27
Not going well so far then.

grte did the printer show ink levels in windows? do you still have windows? we could do a bit of logging on windows with SnoopyPro.exe which would gather the same information.

RRS, that does seem rather odd, perhaps the printer is not responding. we've had a number of canon printers and scanners that will just freeze and refuse to do anything more without unplugging and replugging the usb cable.

---

### Post by grte on 2006-08-27
Yeah, I've got a windows partition.  Where can I get snoopypro?  I'll give it a spin.

---

### Post by DoctorMO on 2006-08-27
this is a nice this intro into snoopy pro: [http://roback.cc/projects/iRiver/howto/snoopypro/](http://roback.cc/projects/iRiver/howto/snoopypro/)

it was made for the iRiver, but you can use it. instead of opening the iriver manager (or what ever) you open up your printer tool box and press the buttons and create reports. save them and send them. you can also snoop general printing as well which will help make canon printer work in gutten print.

download here: [http://prdownloads.sourceforge.net/usbsnoop/SnoopyPro-0.22.zip?download](http://prdownloads.sourceforge.net/usbsnoop/SnoopyPro-0.22.zip?download)

---

### Post by PacShady on 2006-08-30
Hey

Thought you might use details from a MP170. I think I did it all right.

Will these files be used to make working drivers for Canon printers? TurboPrint rips off everyone being the only available driver for many of these printers, and yet I can buy a brand new printer for LESS than they charge for the privilege of using their program!

If it means preventing TurboPrint from getting money, I'm all for it!

'Shady

---

