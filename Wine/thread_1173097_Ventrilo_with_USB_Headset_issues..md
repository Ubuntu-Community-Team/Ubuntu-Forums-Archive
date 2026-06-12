---
title: "Ventrilo with USB Headset issues."
date: 2009-05-29
forum: Wine
---

### Post by jellytot on 2009-05-29
Hi, 
 I use Ventrilo and have got it set up and working fine TO LISTEN through my speakers only. However, I have set my USB Headset (OSS) to be my playback default and my USB Headset (ALSA) for my Recording. On the "Test" in the sound preferences, they both work fine and work properly.

 Now then, in Ventrilo, the sound comes out of my speakers, not my headset, and I cannot for the life of me work out how to get my headset microphone to work on it. I've tried other options before, including re-installing it on Windows CrossOver (which failed completely, including no sound).

 Any help on how to get my microphone to work on Ventrilo under WINE would be massivley helpful :) 

Thanks, 
Jamie.

P.S. I am using the latest Version of WINE and I always update it when a new version is out.


EDIT: Am using Ubuntu 8.10.

---

### Post by cspack on 2009-05-29
This is how I do it, I'm sure there are better solutions but maybe it will get you going.  

Find the names of your sound card and headset:

$ asoundconf list
NVidia
Headset

Then I have a script to start ventrilo.  It sets my default sound card to my headset, starts vent, then sets default sound back to my speakers.

asoundconf set-default-card Headset
wine "$HOME/.wine/drive_c/Program Files/Ventrilo/Ventrilo.exe" &
sleep 3
asoundconf set-default-card NVidia

Hope that helps.

---

### Post by jellytot on 2009-05-29
Results of
> **cspack said:**
> 
asoundconf set-default-card Headset
wine "$HOME/.wine/drive_c/Program Files/Ventrilo/Ventrilo.exe" &
sleep 3
asoundconf set-default-card NVidia

asoundconf set-default-card Headset - Did nothing

wine "$HOME/.wine/drive_c/Program Files/Ventrilo/Ventrilo.exe" &
sleep 3 - Gave a massive error and opened Ventrilo (microphone still didn't work)

asoundconf set-default-card NVidia - Did nothing


I can post the error if you like.

---

### Post by cspack on 2009-05-29
What is the output for you from the following command? (assuming your USB headset is plugged in)

$ asoundconf list

---

### Post by jellytot on 2009-05-29
Names of available sound cards:
Intel
default

---

### Post by cspack on 2009-05-29
You'd have to figure out which of those 2 is your headset (if any), and replace my names with yours.  Neither of those look like your headset to me though.  What kind of headset is it?

---

### Post by jellytot on 2009-06-17
sorry for long reply.

 Its a Logitech headset, with the jacks plugged into a USB control-box. it shows up on my system as C-Media USB Headset.

---

### Post by executorvs on 2009-06-24
I was going to give a response but it's already written at [http://ubuntuforums.org/showthread.php?t=1184923&highlight=C-Media](http://ubuntuforums.org/showthread.php?t=1184923&highlight=C-Media)

it fixes the blacklisting of usb audio devices.

---

### Post by Ventrilo Host on 2009-07-12
I've found a fix, although it's pretty dumb. 

Turns out the issue is caused by some other conflicting usb device, the issue manifests after a reboot. The fix is to boot the machine with the headset unplugged. And then connect the headset after bootup.

---

### Post by Curtis12 on 2009-07-30
so, i have tried all that was suggested here, with no avail. I am able to hear other speaking. Now for some reason, i have to enter the setup and redo my PTT. it is still set just i have to change it and then change it back for vent to recognize i just keyed up. then after i key up i dont hear the 'unclick' sound nor does the speaker un-light up from green. When i do speak while keyed up, others hear a lot of static and barly make out that it is my voice. 

any suggestions or need for more info? if you need more info, what is it you need?

---

