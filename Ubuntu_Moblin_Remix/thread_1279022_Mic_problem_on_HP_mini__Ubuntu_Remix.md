---
title: "Mic problem on HP mini / Ubuntu Remix"
date: 2009-09-30
forum: Ubuntu Moblin Remix
---

### Post by marconibra on 2009-09-30
I bought a Notebook HP Mini (1gb ram / HD 16gbSD ) and it came with a pre-installed WinXp. Tired of the same Xperience, I installed (I'm a new linux user) HP MIE Linux and it worked perfectly. All out of the box.

However, this linux version was not what I was looking for. It gave few options and restricted me to do many things. Then, I decided to run Ubuntu Remix. I installed this version from my USB drive and, everything seemed to be fine: Video, sound etc.

However, since then I noticed my built-in mic does not work. I tried everything. I googled it. Edit many files. But still cannot get my mic to work neither with skype nor with any audio recorder.

Can anyone help me to fix this? Thanks in advance!

---

### Post by marconibra on 2009-10-03
Thanks everybody for not responding. You guys were very helpful.

Here it goes the guidelines to fix this problem:

           - First, check that you have this packages installed (sudo apt-get install package_name):
 patch, gettext, libncurses5-dev, xmlto, xmltoman
- Use this script:
 cd ~
mkdir soundtmp
cd soundtmp
 wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.19.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.19.tar.bz2)
 tar xjf alsa-driver-1.0.19.tar.bz2
tar xjf alsa-lib-1.0.19.tar.bz2
tar xjf alsa-utils-1.0.19.tar.bz2
 cd alsa-driver-1.0.19
./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
make
sudo make install
cd ..
 cd alsa-lib-1.0.19
./configure
make
sudo make install
cd ..
 cd alsa-utils-1.0.19
./configure --disable-nls
make
sudo make install
 - Change your alsa-base.conf file (sudo gedit /etc/modprobe.d/alsa-base.conf) adding these lines:
 options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-m4
options snd-hda-intel enable_msi=1
 - Go to System>Preferences>Sound and change first 4 options to ALSA
 - Reboot!
 - After reboot you should hear login sound...
 - In volume control, you'll want to set the input sources to "line" and "front mic" for the HDA Intel (Alsa mixer). Make sure your volumes are not set too low after a reboot, you're off and running (thanks to jasonq).
 Built in speakers work, headphones and internal mic. Magic blue keys works too, and i'm not having issues about playing from 2 different sources at the same time (youtube in firefox and mp3 in rhytmbox). However, I didn't test external mic.
 Maybe between kernel updates you have to do all this process again.
 

Thanks brian!
[http://ubuntu.bryanludvigsen.com/?p=240](http://ubuntu.bryanludvigsen.com/?p=240)

---

### Post by helmingstay on 2010-01-08
For reference, tt appears this was an alsa issue.  Bug fixes have been incorporated as backports. A very simple fix is here:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/458302](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/458302)

---

### Post by gmarcotte on 2011-01-10
I just got hp mini and first thing I did was to install ubuntu 10.04 wiping out the winblows OS.  everything worked until I tried to skype call and found the internal mic didn't work

Got this procedure from [http://ubuntuforums.org/showthread.php?t=1279022](http://ubuntuforums.org/showthread.php?t=1279022) and with these modifications got it to work with 10.04


- First, check that you have this packages installed (sudo apt-get install package_name):
patch, gettext, libncurses5-dev, xmlto, xmltoman

- Use this script:
cd ~
mkdir soundtmp
cd soundtmp
#
# down load latest files from alsa-project.org  alsa-driver, alsa-lib, alsa-utils to soundtmp directory
#
tar xjf alsa-driver-1.0.23.tar.bz2 
tar xjf alsa-lib-1.0.23.tar.bz2 
tar xjf alsa-utils-1.0.23.tar.bz2
cd alsa-driver-1.0.23
./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
make
sudo make install
cd ..
cd alsa-lib-1.0.23
./configure
make
sudo make install
cd ..
cd alsa-utils-1.0.23
./configure --disable-nls
make
sudo make install


- Change your alsa-base.conf file (sudo gedit /etc/modprobe.d/alsa-base.conf) adding these lines:
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-m4
options snd-hda-intel enable_msi=1
- Go to System>Preferences>Sound and change first 4 options to ALSA &#8592; couldn't do this part there was no first 4 options …

- Reboot!
- After reboot you should hear login sound...

click on speaker icon and then pick preferences there you can adjust the volumes.

then install skype if not already installed and check the options. you should see options for the sound card in the sound devices hardware now. In my case I also had a web cam plugged in with its own mic and this shows up as an option now. 

do a skype test call record your message and you should here it come back.

---

### Post by slw0000 on 2011-02-10
Penitence is something that enervates our spirit, causing a greater loss than loss itself and making a bigger mistake than mistake itself, so never regret.

---

### Post by SigmaKS on 2011-03-17
I had mic not working problem with the HP mini 110 that I just installed 10.10 netbook remix on. I just went to applications / Sound / Input and there the mic was set to mute! I unchecked the mute box and adjusted the input volume slider and then it worked! I am glad that's all it took for me because I am still trying to learn all the CLI syntax and commands.

---

### Post by imatworkallday on 2011-04-01
> **sigmaks said:**
> i had mic not working problem with the hp mini 110 that i just installed 10.10 netbook remix on. I just went to applications / sound / input and there the mic was set to mute! I unchecked the mute box and adjusted the input volume slider and then it worked! I am glad that's all it took for me because i am still trying to learn all the cli syntax and commands.

+1

---

### Post by cdoebbler on 2011-04-10
I am running Xubuntu (which I think is based on a Ubuntu 10.10 build) with xfce 4) on a hp mini 110c and cannot get the internal or plugged-in microphone to work. Speakers (both internal and plugged-in) work fine, but it just will not record or transmit my voice or any sounds.

I tried the fix suggested her but it does not work. One problem is that Xubuntu does not seem to have a Preferences>Sound link...so I can't set it, but I did follow the patch install and make instructions.

Any help appreciated...please ask if you need more information.

---

### Post by FANUTI on 2011-04-21
I ran into the same problem on my HP Mini 1010NR, running Ubuntu 10.10 (netbook install.) 

Thanks to SigmaKS' insight, I too discovered the checked MUTE button being the first issue to address.

I made several more test calls to Skype, only to discover the mic not working.  

I clicked on the speaker icon in the top toolbar, then selected "Sound Preferences."
Selected the Input tab and then scrolled through all of the possibilities in the "Connector:" drop down field.  

I kept an eye on the Input Level and when I saw "Line-In/Microphone" lighting up the input level, I finally got the mic working.

Another call to my British Skype test call girlfriend, and I finally got a recording back.

So in short: 
[B]Go to Sound Preferences>Uncheck Mute>Scroll through each Connector:
HP Mini 1010NR netbook mic is Line-In/Microphone.[/B]

Hope this helps and good luck!

---

