---
title: "Soundblaster mp3+"
date: 2008-06-04
forum: Ubuntu Studio
---

### Post by bm13084 on 2008-06-04
Hello,

I'm a podcaster trying to switch my show over to my linux comp... I use a soundblaster mp3+ external sound card to record from my mixer because it has rca in jacks.  Anyhow,  I can't get audacity to recognize it for playback or recording, even when the rest of my computer recognizes it for playback.  My onboard mic works ok, it's static-y when i turn it up and kind of grainy sounding (could be the crappy computer mics, though).

I have an acer 5720, and I've followed the tutorial to install sound [here]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720").  I need on board to stick around, because I use the laptop on the go a ton.  Any help is surely appreciated!

---

### Post by bm13084 on 2008-06-05
Still haven't figured it out

---

### Post by MattressVon on 2008-11-10
Update: To resolve this issue in Intrepid install the following:

1.) enable mediubuntu repositories via terminal:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

2.) Install alsa-firmawre package from either synaptic or via terminal:

sudo apt-get install alsa-firmware

3.) Install Pulse Audio Device Chooser via terminal:

sudo apt-get install padevchooser

4.) Enter the following command in a terminal:

asoundconf list

5.) Figure out what asound has the card listed as. Mine was MP3.

6.) Enter this command in the terminal to make the card default if you so desire. When you unplug the card, the awesomeness that is Ibex will automatically switch back to your old card unless you have sound applications running (Totem, VLC, Amorok, etc).

asoundconf set-default-card Name_of_your_sound_card_from_step_4

7.) restart your machine with the Sound Blaster MP3+ card plugged in. You will notice a system hang as ALSA figures it out. Now open preferences>sound and look at the available devices. You should see something like OSS USB MP3+ as one of your device options. If you aren't getting sound, check that and reboot.

8.) If it's working :guitar:, if it's not :confused:

Did me well on an Acer Aspire One Netbook that was freaking out after a kernel upgrade.

---

