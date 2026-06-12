---
title: "Install Ubuntu Server on a Raspberry Pi 2, 3 or 4"
date: 2020-01-17
forum: Server Platforms
---

### Post by toodumb2figureout on 2020-01-17
[h=1]Install Ubuntu Server on a Raspberry Pi 2, 3 or 4 [https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)[/h]I made it to step "First boot tips" I installed all 3 desktops, rebooted after installing each one and it just boots to the really fast blinking prompt _ 

How do I get to a Desktop? 

I went to the wiki [https://wiki.ubuntu.com/ARM/RaspberryPi#Packages](https://wiki.ubuntu.com/ARM/RaspberryPi#Packages) but the page never loads.

Thanks in advance

---

### Post by bunny9000 on 2020-01-17
[https://wiki.ubuntu.com/ARM/RaspberryPi](https://wiki.ubuntu.com/ARM/RaspberryPi)

That link works for me.

Ubuntu server doesn't have a graphical ui by default so it will drop you into the terminal.

You'll either have to install a graphical ui like gnome or install web management tools.

---

### Post by toodumb2figureout on 2020-01-17
[B]I already installed 3 different GUI's listed on the below page

Install Ubuntu Server on a Raspberry Pi 2, 3 or 4 [https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)[/B]

I  made it to step "First boot tips" I installed all 3 desktops, rebooted  after installing each one and it just boots to the really fast blinking  prompt _ 

Edit, cant type anything at the blinking prompt but the 3 finger salute still works..


Thanks

---

### Post by mastablasta on 2020-01-20
how did you flash the card? is the downloaded image good (run md5sum check)?

---

### Post by toodumb2figureout on 2020-01-21
> **mastablasta said:**
> how did you flash the card? is the downloaded image good (run md5sum check)?

I flashed the card with USB Image Writer that comes with Linux Mint have use this method to flash at least a dozen other cards without fail I think you need to download and install it yourself so you can understand at what point I am stuck at. 

How do I change the Style of this forum the orange makes my eyes bleed, you’d think someone who tries to avoid eye strain setting at a computer would pick colors that does not hurt the eyes...

Thanks

---

### Post by mastablasta on 2020-01-21
so you first successfully installed the ARM server image? then, after that is installed you logged in and installed the desktop? and then it didn't work? and all you got was a blinking cursor? i had a similar thing when i installed nvidia card and drivers. it looked like the monitors EDID wasn't recognised by the GUI. at least that was what i was told . i never managed to troubleshoot it fully.


i don't think you can change the style. i would reduce contrast on monitor first. the orange i have here and at home are quite soft.

---

### Post by toodumb2figureout on 2020-02-01
> **mastablasta said:**
> so you first successfully installed the ARM server image? then, after that is installed you logged in and installed the desktop? and then it didn't work? and all you got was a blinking cursor? i had a similar thing when i installed nvidia card and drivers. it looked like the monitors EDID wasn't recognised by the GUI. at least that was what i was told . i never managed to troubleshoot it fully.


i don't think you can change the style. i would reduce contrast on monitor first. the orange i have here and at home are quite soft.

Again [B]I installed 3 different GUI's listed on the below page

Install Ubuntu Server on a Raspberry Pi 2, 3 or 4 [https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)[/B]

I  made it to step**[SIZE=4] "First boot tips"[/SIZE]** I installed all 3 desktops,  rebooted  after installing each one and it just boots to the really fast  blinking  prompt _ 

Edit, cant type anything at the blinking prompt but the 3 finger salute still works.. 

I have never had to change the contrast settings on any monitor so a web page will not make my eyes burn in 30 years.

Seems anything connected to Ubuntu is either annoying or not commonsensical FORCING eye straining colors, no email alert for replies to your topics, email address over a username to login to name a few I encountered just replying to this comment.

Thanks again

---

### Post by toodumb2figureout on 2020-02-01
Here we go I found the mobil app switch and it KILLED all the eye strain 100% and found the notify by email option

---

### Post by larrytx on 2020-02-14
I understand. When he said, "I made it to step "First boot tips" I installed all 3 desktops, rebooted  after installing each one and it just boots to the really fast blinking  prompt ," that can be really difficult to understand. What was there about installing three desktops that you failed to understand? Or are you saying that he needs to install a fourth?

---

### Post by mastablasta on 2020-02-17
no, one desktop is enough actually. desktop needs de manager to load. assuming it was installed, then the GPU chip needs to recognise the monitor at boot to set proper resolution. this can also be done manually.

the current information form user is not enough to know what is wrong or what is going on. information for troubleshooting can be found in logs. they can be accessed form command line mode (CLI). at boot first switch to CLI, then go to /var/log and check the old logs. you can see what happened and why the monitor didn't get picture. 

we don't magically know what the issue is if there is only blinking cursor on screen. especially if it works fine for everyone else and they do not get the blinking cursor. by this we can deduce and suspect the following:
1. monitor is not sending the correct EDID information to GPU chip. 
2. OS image was not made correctly

we can also conclude (since in large user sample all works well) that:
1. it is not the OS fault that the cursor is blinking
2. that fault is hardware (old monitor?!) or wrong setup done by user

you could also try Raspbian if Ubuntu us not working.  that one should work out of the box. and you can image it with default desktop.

---

