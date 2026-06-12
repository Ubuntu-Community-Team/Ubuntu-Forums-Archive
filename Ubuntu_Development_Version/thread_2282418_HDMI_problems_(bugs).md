---
title: "HDMI problems (bugs?)"
date: 2015-06-14
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-06-14
Hello,
I have a Toshiba [C855-2J5]("http://www.toshiba.it/discontinued-products/satellite-c855-2j5/") notebook with Xubuntu 15.10. I'm encountering 2 problems when connecting the PC to my Samsung SmartTV via HDMI.

1- When the notebook is connected via HDMI and I boot Xubuntu the login screen doesn't appear. I can only see (in both screens) a black screen with the cursor in the center of it. If I write the password and press "Enter" the Desktop appears and the OS works fine. Sometimes, If i left-click on the black screen the login screen correctly shows. It seems like a bug related to the login-screen. 

2-The Audio is not transmitted via HDMI. When I start a video, I see the video on the TV but the audio is reproduced on the notebook. I cant' understand if pulse-audio manager's settings are ok. I see:

"Turks/Whistler HDMI Audio"
Port: "HDMI / Display Port"

"Audio interno Stereo analogico" (Internal stereo audio):
Port: "Altoparlanti" (Speakers) 
or 
"Cuffie analogiche (unplugged)" (Headphones)



Any idea to help me? Should I report the first problem in launchpad?

---

### Post by grahammechanical on 2015-06-14
I am not using Xubuntu but Ubuntu and for the first time I see in Sound Settings>Output

HDMI/DisplayPort 2
*GT 216 HDMI audio controller*

Digital Output (S/PDIF)
*Built-in audio*

May be I should be more observant but I do not think that I could get HDMI sound output from the graphic adapter in Ubuntu 14.10 or earlier. Or perhaps the option only appears if we use a HDMI connection. 

But now I get that option. We need to select it. I am using a Sharp TV as monitor with HDMI connection and I get sound out of the TV's speakers. If I plug in headphones, I also get

Headphones
*Built-in audio*

Make sure that HDMI/DisplayPort is selected.

Regards.

---

### Post by P-I H on 2015-06-14
I use Ubuntu with Unity. With PulseAudio Volume Control you get more in information and some more settings are available.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=262591&d=1434289944&thumb=1&stc=1[/IMG]
The computer is connected to an AVR with hdmi and the AVR is connected to the display with hdmi.
This configuration works OK with Chrome and Kodi.

---

### Post by enricobe on 2015-06-14
> **P-I H said:**
> I use Ubuntu with Unity. With PulseAudio Volume Control you get more in information and some more settings are available.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=262591&d=1434289944&thumb=1&stc=1[/IMG]
The computer is connected to an AVR with hdmi and the AVR is connected to the display with hdmi.
This configuration works OK with Chrome and Kodi.

Thank you. In the following image you can see my settings. In "Advanced" I've checked/unchecked all the options but It still doesn't work. I have a Radeon HD7610M
[ATTACH=CONFIG]262592[/ATTACH]


EDIT: Posting the image above I have seen the green checkbox at the top of each output device: "Set as fallback". I've solved the problem activating that option, now the HDMI audio works fine! Thank you!

Now I only need to understand why the login screen doesn't show when the notebook is connected via HDMI

---

### Post by enricobe on 2015-06-20
Should I report the black login-screen as a bug in Launchpad? Which program should I target with "ubuntu-bug" to report that bug?

---

### Post by P-I H on 2015-06-20
My configuration also misbehaves at boot.
- the grub menu does not show after boot. The first I see is the login screen
- In case I want to turn off and on the display by only turning off and on the AVR, it takes about a minute or more before the screen is back
- In case I use this sequence to turn off and on the display, AVR, display, display, AVR, it takes in most cases about 20 sec before the screen is back
However in case I first start BIOS, the grub menu is shown.
After the linux upgrade the other day, the grub menu was shown at two reboots. When I rebooted a third time to see if the problem was fixed, there was no grub menu.
It is hard to define the program that misbehaves, kernel, radeon driver, llightdm, systemd or a race condition.

---

### Post by cariboo on 2015-06-20
> **P-I H said:**
> My configuration also misbehaves at boot.
- the grub menu does not show after boot. The first I see is the login screen
- In case I want to turn off and on the display by only turning off and on the AVR, it takes about a minute or more before the screen is back
- In case I use this sequence to turn off and on the display, AVR, display, display, AVR, it takes in most cases about 20 sec before the screen is back
However in case I first start BIOS, the grub menu is shown.
After the linux upgrade the other day, the grub menu was shown at two reboots. When I rebooted a third time to see if the problem was fixed, there was no grub menu.
It is hard to define the program that misbehaves, kernel, radeon driver, llightdm, systemd or a race condition.

This depends on how your system is set up, If you only have one distribution on you computer, you'll never see grub, unless you hold down the shift key. It would help if you told us how you have your system set up.

---

### Post by P-I H on 2015-06-20
> **cariboo said:**
> This depends on how your system is set up, If you only have one distribution on you computer, you'll never see grub, unless you hold down the shift key. It would help if you told us how you have your system set up.

I have both Ubuntu 15.10 and Ubuntu 15.04 on the computer. In case I connect the display with DVI, it works as expected and grub is shown.
The problem might be related to signalling between AVR and display, as the display changes between stand by and active several times.
I also tried with fglrx, but there was no change.

---

