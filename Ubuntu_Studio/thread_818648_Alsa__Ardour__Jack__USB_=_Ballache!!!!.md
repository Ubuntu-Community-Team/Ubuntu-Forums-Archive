---
title: "Alsa / Ardour / Jack / USB = Ballache!!!!"
date: 2008-06-04
forum: Ubuntu Studio
---

### Post by Shugs81 on 2008-06-04
I decided in the Behringer U-control as my recording device as somewhere to start learning how to use adrour and jack....

just one thing.... I've no Idea how to get it to work... it says i've got alsa installed but it still doesn't pick it up through jack... tried changing the sound settings so that sound input was usb device but when it does the testing thing it still doesn't pick it up... when i select ALSA it gives an error of "Device is being used by another application" when running jack.... otherwise does nothing....

looking at jack i'm using the QT Gui interface and when clicking on alsa i get Midi through port 0 and Ardour (if it's running)

I tried reading the ardour manual and it doesn't really give any info on how to set things up... the only guide i've seen for this device so far is a puppy linux forum post... [http://www.murga-linux.com/puppy/viewtopic.php?t=15188](http://www.murga-linux.com/puppy/viewtopic.php?t=15188) and it mentions changing the alsaconf... I looked for it and it wasn't where they said... and when i run whereis it doesn't find it... When going through synaptic it says that I've got the alsa core programs installed and a few other related bits and pieces...

can someone please at least guide me in the right direction??? or at least tell me how to install alsa properly...:confused::confused::confused:

---

### Post by Shugs81 on 2008-06-04
forgot to add....

Dell Inspiron 1525
1.6ghz Dual Core
2gb RAM (4gb when it arrives!! cheaper than desktop ram... madness!!)
Behringer USB U-Control UCA202
Sound is running from Guitar amp Line out (coming through in mono... will check cables or does this come through mono anyway? one channel out.... doh! answered that one myself!!!)
Running Feisty upgraded to Latest version of Ubuntu studio.... would that cause a problem??

umm... anything else you guys need??

---

### Post by prismatic7 on 2008-06-04
OK. Changing the output in the general Ubuntu sound settings won't help you. jackd has a seperate configuration. There's a few things you need to know:

First, Ubuntu (and most Linux variants, I think) evaluate USB sound devices at boot, in order of discovery. This means that the node number of your card can change across reboots. There is a way to fix this, but it's a bit beyond the scope of what you need right now! I'll document it on the wiki sometime this month, I hope.

For the moment, open a terminal window and enter

```
cat /proc/asound/cards 
```

This will show you the node numbers of your ALSA devices. The UCA202 (which I have) should be described as a 'Burr-Brown' device. Note the node number.

Second, open qjackctl. In the 'Setup' window, set 'Interface' to 'hw:<node number>'. Don't fuss with latency settings just yet - start jack and see if you get anywhere.

Once you're up and running, make tweaks to the jack setup until you're happy with the sound!

---

### Post by Shugs81 on 2008-06-05
cool beans!!!

will try that tonight....

---

### Post by Shugs81 on 2008-06-11
reet... i know it's nearly a week... damn animals!!!wont go into it....

using the command give i get that it's hw:1,0

>  0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 19
 1 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:1d.1-1, full s


i have got that right haven't i? and the u-control... i've got headphones plugged in the monitor socket and it's all coming through... even the sound output... but I can't tell if it's getting picked up as a input source... cause obviously i'm hearing the guitar straight through... and i know that jack is connecting to ardour (i know... jumping ahead again....) but still nothing... and jack has started freezing up on me know too... using qjackctl and at least the frontend is freezing...

bah.... heads hurting need sleep... as much info as poss would be useful...

cheers in advance....

---

