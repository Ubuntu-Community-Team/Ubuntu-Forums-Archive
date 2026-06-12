---
title: "Tascam us-122"
date: 2010-05-30
forum: Ubuntu Studio
---

### Post by psy-man on 2010-05-30
greetings all,
I am trying to persuade my old tascam us-122 usb audio interface to work with my laptop running lucid.
I am following the procedure as detailed here 
[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

I have done this on my desktop machine which is running ubuntu studio 9.10 and then upgraded to 10.04 no problems there.
 But the laptop is running ubuntu 9.10 with the real-time kernel and audio meta-packages added, I upgraded to 10.04 and then ran through the installation procedure.

The output of  cat /proc/asound/cards
 0 [PCI            ]: Maestro3 - ESS Maestro3 PCI
                      ESS Maestro3 PCI at 0xd800, irq 5
 1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 002/003)
seems to me to show the device has been recognized, but lights are not lighting. Any thoughts or suggestions would be much appreciated.

---

### Post by zettberlin on 2010-05-31
What do you get from the following command in a terminal:

alsamixer -c1

?

---

### Post by psy-man on 2010-05-31
alsamixer -c1 
brings up alsa mixer controls, as you can see the tascam is shown in the control panel ,but this device has no soft mixer built in, the knobs on on top are a hardware mixer, I understand from the docs in the alsa firmware that the other tascams (224 & 428 do have software controls for mixing.

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: TASCAM US-X2Y                                  F1:  Help               &#9474;
&#9474; Chip:                                                F2:  System information &#9474;
&#9474; View: F3: Playback  F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item:                                                Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                This sound device does not have any controls.                 
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
further to this subject the alsa firmware package has been updated since the help instruction were written the latest version being alsa-firmware-1.0.23. 
I have of course tried installing this latest package and still the tascam remains off. It is recieving power via the usb port as the phantom power,,,aahhh when I switch the phantom power on with the alsa mixer open, the mixer tells me the device has been unplugged with a rather amusing message

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: (unplugged)                                    F1:  Help               &#9474;
&#9474; Chip: -                                              F2:  System information &#9474;
&#9474; View: F3: Playback  F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item:                                                Esc: Exit               &#9474;
&#9474;                In the midst of the word he was trying to say,                &#9474;
&#9474;                  In the midst of his laughter and glee,                      &#9474;
&#9474;                He had softly and suddenly vanished away---                   &#9474;
&#9474;                  For the Snark was a Boojum, you see.                        &#9474;
&#9474;                                                                              &#9474;
&#9474;                (Lewis Carroll, "The Hunting of the Snark")                   &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                       The sound device was unplugged.                        &#9474;
&#9474;                    Press F6 to select another sound card.                    &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;

So now I'm thinking maybe this is a usb power issue. Having set this machine up as a dual boot I will try how the device behaves under windoze....
V interesting under win xp the tascam lights up but when I switch on the phantom power ...poor windoze locks up. This happens when the tascam is connected to a PCMCIA usb2 card, however when the tascam is connected to the built in usb1 port it behaves as it should under winXP. So I conclude that part of this is a usb power issue. Now with tascam connected to built in usb and alsa mixer open in a terminal switching the phantom power does not cause the alsa mixer to tell me the snark was a Boojum!
 also
 $ cat /proc/asound/cards is showing the tascam is connected to the built in usb bus
~$ cat /proc/asound/cards
 0 [PCI            ]: Maestro3 - ESS Maestro3 PCI
                      ESS Maestro3 PCI at 0xd800, irq 5
 1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 001/002)
reassuring me that       /etc/udev/rules.d/55-tascam.rules is doing its job.
                                                                                                 still no green light though

---

### Post by johnharris on 2010-05-31
i am new to linux and have been trying to sort out my us-122.  after tinkering with it for a while i finally got the green light to come on for some reason or another, i'm not sure if this was but i think it was only after i plugged in a midi cable to the keyboard.  i only have one midi cable right now so i didn't send and return so i can't confirm that it was fully functioning.

---

### Post by psy-man on 2010-05-31
Hi John,
If the green light comes on, your Tascam is working. The firmware is uploaded to the tascam which sets up the sample frequency, bit rate and switches the light on. 
This is a puzzle to me. as I know the tascam works connected to my desktop PC which is a full ubuntu studio install running a real time kernel. I now know the tascam works when connected to this laptop when it is running under windows. Right now I have booted a live debian CD I am going to try installing the firmware loader on this. 

I'm wondering if there is some software control to the 5volt supply of the usb bus. I have seen many reports that machines run cooler under linux.....


So I tried installing the firmware loader on  a 64studio live session but that is not working properly as the repositories are not working and maybe I just dont have enough ram to do the job in a live environment.

---

### Post by sgx on 2010-05-31
There are newer versions of us122 that have fewer/different chips than early releases, manufactures cost cutting. But the new ones don't work. This is also reported to be the case with revised maudio 24/96 pci cards.
Cheers

---

### Post by psy-man on 2010-06-01
ah well, this laptop's internal sound is an ESS maestro 3 which works after a fashion, I guess I'll just have to be content with that. My intention is to use it run hydrogen at band rehearsals thus allowing our real-world drummer to play his horn....

---

### Post by uOpt on 2010-06-01
BTW, it is normal that these US-122s don't have mixer controls. They actually do not. They are just pretty plain DAC/ADCs from a computer standpoint.

So can you play stuff on it?

---

### Post by sgx on 2010-06-01
> **psy-man said:**
> ah well, this laptop's internal sound is an ESS maestro 3 which works after a fashion, I guess I'll just have to be content with that. My intention is to use it run hydrogen at band rehearsals thus allowing our real-world drummer to play his horn....
Rakarrack eq and fx do wonders for hydrogen, you can really dial in
a sound you like!

---

### Post by psy-man on 2010-06-02
> **uOpt said:**
> BTW, it is normal that these US-122s don't have mixer controls. They actually do not. They are just pretty plain DAC/ADCs from a computer standpoint.

So can you play stuff on it?

Simplicity appeals to me, real knobs, a sturdy case, reasonable DAC/ADCs (at least for any mic in my budget.

"Here I was going to so no I cant play stuff on it but in the process of reviewing what I understand and what I did I now have fixed it."

 It does work under windows but only when connected to built in USB1. If I use a PCMCIA usb2 card to connect and then switch the phantom power on the system locks up until I pull the card out. 
It works when connected to a ubuntu desktop. It works well on my old G3 macs as well.


Now as I understand this, firmware loading is a two stage process.
On initial power up the tascam identifies itself thus
$ lsusb 
Bus 002 Device 003:  ID 1604:8006 Tascam US-122 Audio/Midi Interface
and after firmware stage one
$ cat /proc/asound/cards gives
1 [USX2Y ]: USB US-X2Y - TASCAM US-X2Y
TASCAM US-X2Y (1604:8007 if 0 at 001/006)
 so the ID changes from 1604:8006 to 1604:8007

hence the /etc/udev/rules.d 

BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx'"

BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"
now I have 
$ lsusb
Bus 001 Device 003: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
indicating that the first stage has completed but if I run
sudo usx2yloader

I get "No USX2Y-compatible cards found"

If I do this 
 sudo ln -s /usr/share/alsa/firmware/usx2yloader /lib/firmware/usx2yloader
I get
ln: creating symbolic link `/lib/firmware/usx2yloader': File exists

So I delete the link 
sudo rm /lib/firmware/usx2yloader

and remake it
 sudo ln -s /usr/share/alsa/firmware/usx2yloader /lib/firmware/usx2yloader then rerun 

sudo usx2yloader

bingo the green light comes on........ WAHOO

---

### Post by psy-man on 2010-06-02
My last post was a bit muddled so just to recap.
My tascam US-122 wouldn't work because I must have made a mistake when running through the instructions at [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

**Step 7: TASCAM US-122  Initialization**

 The  following command should initialize the TASCAM US-122, causing the  lights on the unit to come on. 
# sudo usx2yloader
If you get a message like "No USX2Y-compatible cards  found", do the following: 
# sudo ln -s /usr/share/alsa/firmware/usx2yloader /lib/firmware/usx2yloader

I got the message and did as instructed
it still didnt work so I repeated the whole process but when I got to stage 7, ubuntu reported the link file already existed but I didn't notice.
Third time through I discovered there is a newer version of alsa tools so at stage 2

**Step 2: Download and  install ALSA Firmware**

 Download the  alsa-firmware package, unpack it and then build and install the  contents: 
# wget [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.19.tar.bz2)
# tar -xvjf alsa-firmware-1.0.19.tar.bz2
# cd alsa-firmware-1.0.19/
# ./configure --prefix=/usr && make && sudo make install

Change 
alsa-firmware-1.0.19    to      alsa-firmware-1.0.23

but still I missed the already existing link at stage 7

finally today writing the previous post and repeating the steps I deleted the pre-existing link file and remade it.
then
# sudo usx2yloader 
and hey presto the Tascam springs to life. Fantastic.
Now I shall move on to deal with jack and see if I can figure why it won't run in real-time.

As an aside, I took said lappy to rehearsal last night. After scratching around for a suitable adapter I plugged the on board sound into amp..Oh dear...Lots of digital noise..
But, when hydrogen was playing it sounded quite good, the chaps were impressed.

---

### Post by sgx on 2010-06-03
Congratulations! :) I just remembered reading where people have
sometimes fried their unit by changing the phantom power setting
when the unit was on, or plugging in a mic with phantom on, and
if it has an instrument impedance switch, that could be dangerous.
The circuits don't have protection. So make changes before starting,
especially after all your hard work!
Cheers

---

### Post by psy-man on 2010-06-03
Thanks for that advice, I shall ensrcibe that on the blue plastic bit.
Cheers

---

