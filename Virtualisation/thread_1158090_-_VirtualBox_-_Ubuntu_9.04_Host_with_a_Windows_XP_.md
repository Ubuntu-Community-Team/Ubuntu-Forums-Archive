---
title: "- VirtualBox - Ubuntu 9.04 Host with a Windows XP Guest = No Sound"
date: 2009-05-13
forum: Virtualisation
---

### Post by Langr on 2009-05-13
As the title implies, I'm trying to run a Windows XP home guest on a Linux Ubuntu 9.04. The linux uses my Realtek HD Audio card just fine, no problems, which makes me praise Linux for it's ease from having to locate drivers for stuff like printers and such. However, I'm trying to get Windows XP to have sound. I'm also wondering if I'll be able to use the microphone in the Windows XP guest. Thanks for your consultation in advance.

---

### Post by heroidi on 2009-05-13
did you mount the audio on the virtualbox?

---

### Post by u-slayer on 2009-05-14
Enable the audio before you launch the virtual machine.

---

### Post by chocobanana on 2009-05-18
You may also want to consider installing the VirtualBox Guest Additions.

---

### Post by Langr on 2009-05-27
Ugh, It refuses to work even now, I have the audio enabled and set to ALSA using the AC'97 driver or whatever it is, I go to SYSTEM > PREFERENCES > SOUND and make sure that ALSA plays a test sound which it does. I boot up the VM, which does have guest additions, and still no sound, i tried installing the AC'97 driver from realtek and Windows BSOD-ed on me.

Going to Device Manager in Windows shows a speaker with a exclamation mark saying "Multimedia Audio Controller"

Any Ideas?


Update: I uninstalled the Multimedia Audio Controller. Re-ran guest additions and restarted. This time there was a message saying new hardware found, I chose to have it check the disk drives, floppy, etc. It recognizes it as AC'97 and when it tries to install it asks to insert the Realtek AC97 Audio Driver Disk

---

### Post by maino82 on 2009-05-31
I have the same problem with 9.04 as the host and XP as the guest. I'm trying to use it for the Rosetta Stone, which is pretty useless without sound. I found elsewhere that people recommended going to realtek.com and downloading the latest driver and installing that, so you may want to give that a shot. It didn't work for me, and actually ended up making my Windows install blue screen every time I booted, so I had to go into safe mode and roll back the driver, but hey, it may work better for you.

I have the add-ons installed and I've tried changing the audio driver from pulse audio to alsa (this crashes windows the instant it tries to play a sound) to oss to the null driver. None of them seems to work at all for me.

Any suggestions people have would be greatly appreciated.

---

### Post by diodeman on 2009-05-31
oh man, I'm having the same issue with my laptop. I have not been able to figure this out and would love to get XP fully up and running. I too have installed VM + guest and everything is good except the sound. I have tried updating the driver manually in windows xp, and like you, I keep getting BSOD. Hope someone can help us out.

---

### Post by maino82 on 2009-06-05
OK, so I think I've found drivers that work! Actually, someone else found them, I just thought I'd pass along the info. According to [this post]("http://ubuntuforums.org/showpost.php?p=7343970&postcount=2") there's an older version of the drivers that work and don't crash XP. I am now happily running Rosetta Stone in VirtualBox with sound on both XP and Ubuntu. Hope this helps!

---

### Post by Jose Catre-Vandis on 2009-06-07
My pleasure :)

---

### Post by sandman3838 on 2009-06-17
I hope this helps!

Like you I have come accross some sound issues and just not with Vbox!
MS WMV files wouldn't play and neither would DVD movies.

I don't know if you need all this but I just want to make sure your at the same piont I was.
I got all this from this site after doing some reading around in here.

What I did to get Vbox running is in the last step!
Like you Ubuntu is the Host with XP as the Guest.
Mind you my issue was either it failed and no sound or it was really choppy.

Right now everything is working just fine.


*****  To get the DVD playing in Ubuntu ***** 

GETTING DVD TO PLAY

Did you do this:

Quote:
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Quote:
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Quote:
sudo apt-get install libdvdcss2

Quote:
sudo apt-get install w32codecs

Quote:
sudo apt-get install libdvdread4

Quote:
sudo /usr/share/doc/libdvdread4/install-css.sh

Quote:
sudo apt-get install ubuntu-restricted-extras 




******  To get the WMV files working  in Ubuntu ********** 

LSO FROM ANOTHER WMV ISSUE:
sudo apt-get install mozilla-mplayer

NEXT For MPLAYER
Turn the Video tab and change the Available drivers: to x11 X11 (XImage/Shm).

At the Codecs & demuxer tab set Video codec family to 
RealVideo decoder 
and the Audio codec family to 
FFmpeg/libavcodec audio decoders.



****** VBOX fix in Winxp ******** (this was from Vbox forum site)

With pulseaudio on Ubuntu 9.04, the daemon dies because of CPU overload. It's a bug in the dependency libraries of PulseAudio. You can avoid this by editing

/etc/pulse/daemon.conf

and put this in it, or edit the already existing line to match.

Code: 
    no-cpu-limit = yes


Now PulseAudio won't get killed because of CPU overload and you have sound in the Guest, but it does add additional CPU load, because until the VM is closed, PA will run on 100% on one core all the time. The VM will shut down normally so you don't have to kill it and once the VM is closed, the CPU usage will go down.
For more information on this issue, check [https://bugs.launchpad.net/ubuntu/+sour](https://bugs.launchpad.net/ubuntu/+sour) ... bug/373450 which also has a fix, somewhat.

There is an alternative to all this. You can set up PulseAudio on the Guest too. There is a version for Windows. Check their website, [www.pulseaudio.org](www.pulseaudio.org). You can set the VM to use NULL Audio, with the AC'97, install PA and set it to hook itself to the Host PA server. You may need to change a few settings on the Host to accept remote connections.
All audio should then go to the Host.

*******************  

I hope this helps & good luck!

---

### Post by Josueped on 2009-06-20
Can you explain how to setup pulseaudio that way?

---

