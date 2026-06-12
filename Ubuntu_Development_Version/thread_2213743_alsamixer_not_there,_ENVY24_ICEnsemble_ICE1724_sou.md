---
title: "alsamixer? not there, ENVY24 ICEnsemble ICE1724 sound card"
date: 2014-03-28
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-28
```
scott875@scott875-desktop:~$ alsamixer
cannot open mixer: No such file or directory
scott875@scott875-desktop:~$ 

```

---

### Post by ventrical on 2014-03-28
gnome-alsamixer

alsamixergui

---

### Post by sdowney717 on 2014-03-28
gnome-alsamixer gives me a white screen with nothing inside.
my other ubuntu pc I can run 'alsamixer'

I want to select multi channel sound which is only in alsamixer.

---

### Post by sdowney717 on 2014-03-28
[http://askubuntu.com/questions/294807/ubuntu-12-04-alsamixer-not-found](http://askubuntu.com/questions/294807/ubuntu-12-04-alsamixer-not-found)

apparently happens.

Trying this, I do show an 'alsamixer' program but I cant run it??
```
scott875@scott875-desktop:~$ alsamixer
cannot open mixer: No such file or directory

scott875@scott875-desktop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

scott875@scott875-desktop:~$ ls -l /usr/bin | grep alsamixer
-rwxr-xr-x 1 root root       59672 Jan 16 23:21 alsamixer
-rwxr-xr-x 1 root root       48244 Oct 28  2011 alsamixergui
-rwxr-xr-x 1 root root       55640 Jul 21  2013 gnome-alsamixer

scott875@scott875-desktop:~$ /usr/bin/alsamixer
cannot open mixer: No such file or directory
scott875@scott875-desktop:~$ 

```

---

### Post by sdowney717 on 2014-03-28
I dont have a hidden .asound file as the info says delete if you have.
alsamixer is in usr/bin
How do I run it?

```
scott875@scott875-desktop:/usr/bin$ ls a*
a2p                   apport-cli            as
aconnect              apport-collect        as10k1
acpi_listen           apport-unpack         asciitopgm
activity-log-manager  appres                aseqdump
add-apt-repository    apropos               aseqnet
addpart               apt                   aspell
addr2line             apt-add-repository    aspell-import
alacarte              apt-cache             assistant
alsaloop              apt-cdrom             atktopbm
alsamixer             apt-config            atobm
alsamixergui          aptdcon               avahi-browse
alsaucm               apt-extracttemplates  avahi-browse-domains
amidi                 apt-ftparchive        avahi-publish
amixer                apt-get               avahi-publish-address
amuFormat.sh          apt-key               avahi-publish-service
animate               apt-mark              avahi-resolve
animate.im6           apt-sortpkgs          avahi-resolve-address
anytopnm              apturl                avahi-resolve-host-name
apg                   ar                    avahi-set-host-name
apgbfm                arch                  average
aplay                 arecord               awk
aplaymidi             arecordmidi           axi-cache
applycal              arm2hpdl
apport-bug            arping

scott875@scott875-desktop:/usr/bin$ alsamixer
cannot open mixer: No such file or directory
scott875@scott875-desktop:/usr/bin$ 

```

---

### Post by sdowney717 on 2014-03-28
claims alsamixer no such file?

but it exists and is executable.

```
scott875@scott875-desktop:~$ alsamixer
cannot open mixer: No such file or directory

scott875@scott875-desktop:~$ ./usr/bin/alsamixer
bash: ./usr/bin/alsamixer: No such file or directory

scott875@scott875-desktop:~$ sudo su
[sudo] password for scott875: 

root@scott875-desktop:/home/scott875# ./usr/bin/alsamixer
bash: ./usr/bin/alsamixer: No such file or directory
root@scott875-desktop:/home/scott875# cd ..
root@scott875-desktop:/home# cd ..
root@scott875-desktop:/# cd usr
root@scott875-desktop:/usr# cd bin
root@scott875-desktop:/usr/bin# alsamixer
cannot open mixer: No such file or directory

root@scott875-desktop:/usr/bin# ./alsamixer
cannot open mixer: No such file or directory

root@scott875-desktop:/usr/bin# alsamixer
cannot open mixer: No such file or directory
root@scott875-desktop:/usr/bin# 

```

---

### Post by ventrical on 2014-03-28
I got it here . All I did was open filemanager/preferences/behaviour and then tic off 'run executable text files' and then run alsamixer in terminal.

---

### Post by sdowney717 on 2014-03-28
Hi, I changed it logged out and in and still nothing.
Do you need to reboot?
```
scott875@scott875-desktop:~$ alsamixer
cannot open mixer: No such file or directory
scott875@scott875-desktop:~$ alsamixer
cannot open mixer: No such file or directory
scott875@scott875-desktop:~$ 
```

---

### Post by ventrical on 2014-03-28
> **sdowney717 said:**
> Hi, I changed it logged out and in and still nothing.
Do you need to reboot?
```
scott875@scott875-desktop:~$ alsamixer
cannot open mixer: No such file or directory
scott875@scott875-desktop:~$ alsamixer
cannot open mixer: No such file or directory
scott875@scott875-desktop:~$ 
```

Nope. No reboot.  I was just trying to emulate your bug. I didn't have to download any files from synaptic. It was already there in directory you specified. I just opened terminal and entered the command and it came up.

  I have to ask you .. what  hardware do you have for sound? It may be a blacklist?


lspci

---

### Post by ventrical on 2014-03-28
> **sdowney717 said:**
> Hi, I changed it logged out and in and still nothing.
Do you need to reboot?
```
scott875@scott875-desktop:~$ alsamixer
cannot open mixer: No such file or directory
scott875@scott875-desktop:~$ alsamixer
cannot open mixer: No such file or directory
scott875@scott875-desktop:~$ 
```

```


cd /usr/bin

```

in terminal,then..

alsamixer

regards..

---

### Post by sdowney717 on 2014-03-28
> **ventrical said:**
> ```


cd /usr/bin

```

in terminal,then..

alsamixer

regards..

still nothing

scott875@scott875-desktop:~$ alsamixer
cannot open mixer: No such file or directory

scott875@scott875-desktop:~$ cd /usr/bin
scott875@scott875-desktop:/usr/bin$ alsamixer
cannot open mixer: No such file or directory
scott875@scott875-desktop:/usr/bin$

---

### Post by ventrical on 2014-03-28
again.. what hardware are you using?

---

### Post by bapoumba on 2014-03-28
May be something along these lines : [https://wiki.archlinux.org/index.php/Alsa#Installation](https://wiki.archlinux.org/index.php/Alsa#Installation), having this in mind : [https://wiki.ubuntu.com/Audio/TheAudioGroup](https://wiki.ubuntu.com/Audio/TheAudioGroup)

```
~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse

```
alsamixer opens fine here too.

---

### Post by sdowney717 on 2014-03-28
```
scott875@scott875-desktop:/usr/bin$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse,scott875
scott875@scott875-desktop:/usr/bin$ 
```

I added myself to the audio group because it was suggested here
[http://askubuntu.com/questions/294807/ubuntu-12-04-alsamixer-not-found](http://askubuntu.com/questions/294807/ubuntu-12-04-alsamixer-not-found)

and then it worked for him.

---

### Post by sdowney717 on 2014-03-28
> **ventrical said:**
> again.. what hardware are you using?

envy24 aound card

```
scott875@scott875-desktop:/usr/bin$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV630 PRO [Radeon HD 2600 PRO AGP]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV630 HDMI Audio [Radeon HD 2600 Series]
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
[COLOR="#FF0000"]**03:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)**[/COLOR]
03:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)
scott875@scott875-desktop:/usr/bin$ 

```

curious, what is this audio device? That is a video card. Does it have audio something?
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV630 HDMI Audio [Radeon HD 2600 Series]

---

### Post by bapoumba on 2014-03-28
> **sdowney717 said:**
> ```
scott875@scott875-desktop:/usr/bin$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse,scott875
scott875@scott875-desktop:/usr/bin$ 
```

I added myself to the audio group because it was suggested here
[http://askubuntu.com/questions/294807/ubuntu-12-04-alsamixer-not-found](http://askubuntu.com/questions/294807/ubuntu-12-04-alsamixer-not-found)

and then it worked for him.

Hmm, yes, but on 12.04. Did you do that because alsamixer was not working or for other reasons ?

---

### Post by ventrical on 2014-03-28
> **sdowney717 said:**
> envy24 aound card

```
scott875@scott875-desktop:/usr/bin$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV630 PRO [Radeon HD 2600 PRO AGP]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV630 HDMI Audio [Radeon HD 2600 Series]
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
[COLOR=#FF0000]**03:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)**[/COLOR]
03:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)
scott875@scott875-desktop:/usr/bin$ 

```

curious, what is this audio device? That is a video card. Does it have audio something?
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV630 HDMI Audio [Radeon HD 2600 Series]

Thankyou.

My assumption is that there is an interrupt conflict between the two audio-chip sets and I think you can disable the onBoard Audio and it may work then (unless you have two PCI cards in there - one of them has to go). I know .. other programs seem to work just fine .. etc.. but this is dev cycle so there may be some missing parts at this stage of the game. Of course after you disable onBoard chipset (or remove card) you would have to go into GRuB, choose recovery mode and let that play out, then boot normally. (only my advice- may not work).

regards..

edit:

That looks like an old MoBo. I have always had sound probs with Via Tech after Precise release, but some will work . other will not.

---

### Post by sdowney717 on 2014-03-28
> **bapoumba said:**
> Hmm, yes, but on 12.04. Did you do that because alsamixer was not working or for other reasons ?

Oh, just trying anything.

---

### Post by sdowney717 on 2014-03-28
> **ventrical said:**
> Thankyou.

My assumption is that there is an interrupt conflict between the two audio-chip sets and I think you can disable the onBoard Audio and it may work then (unless you have two PCI cards in there - one of them has to go). I know .. other programs seem to work just fine .. etc.. but this is dev cycle so there may be some missing parts at this stage of the game. Of course after you disable onBoard chipset (or remove card) you would have to go into GRuB, choose recovery mode and let that play out, then boot normally. (only my advice- may not work).

regards..

edit:

That looks like an old MoBo. I have always had sound probs with Via Tech after Precise release, but some will work . other will not.

It is an old intel server board. 
There is no built in onboard audio.
It has the Dynex Via envy 5.1 PCI sound card.
It has an HD2600 Pro AGP video card.

It might be that the video card has DVI audio capability? Passing audio stream through DVI to HDMI adapter.

BUT STILL, unable to run a program from terminal? Saying not found, does that mean something else, no such file or directory? Is it talking not about itself, alsamixer, but about some kind of missing file for the envy 24 5.1 sound card which also has spdif?

---

### Post by sdowney717 on 2014-03-28
aplay -l shows this

```
scott875@scott875-desktop:/usr/bin$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICE1724 [ICEnsemble ICE1724], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
scott875@scott875-desktop:/usr/bin$ 

```

---

### Post by sdowney717 on 2014-03-28
[https://apps.ubuntu.com/cat/applications/oneiric/mudita24/](https://apps.ubuntu.com/cat/applications/oneiric/mudita24/)

What is this? Worth trying?
ALSA GUI control tool for Envy24 (ice1712) soundcards

---

### Post by bapoumba on 2014-03-28
> **sdowney717 said:**
> Oh, just trying anything.

Sorry, I'm not sure I understand correctly. alsamixer was not working prior to adding your user to the audio group or after ?

---

### Post by sdowney717 on 2014-03-28
> **bapoumba said:**
> Sorry, I'm not sure I understand correctly. alsamixer was not working prior to adding your user to the audio group or after ?

alsamixer never worked.

I just installed that mudita24, but it is for 1712 card and I have 1724

Installing that way is not user friendly. Asks to open with a program and you got to know its name in usr/bin

```
scott875@scott875-desktop:~$ mudita24
No ICE1712 cards found
scott875@scott875-desktop:~$ 

```

I do have sound, I was going to run alsamixer to expand stereo profile to 5.1 (6 channels in alsamixer)
This card will play 5.1 channel sound in windows 7. The PC dual boots.

---

### Post by bapoumba on 2014-03-28
Can you try with **alsamixer -d 0** (or 1), see **man alsamixer**. You seem to have the same card nb for 2 different device nb in aplay -l (post #20).

---

### Post by sdowney717 on 2014-03-28
> **bapoumba said:**
> Can you try with **alsamixer -d 0** (or 1), see **man alsamixer**. You seem to have the same card nb for 2 different device nb in aplay -l (post #20).

sure.

```
scott875@scott875-desktop:~$ alsamixer -D 1
ALSA lib control.c:953:(snd_ctl_open_noupdate) Invalid CTL 1
cannot open mixer: No such file or directory
scott875@scott875-desktop:~$ alsamixer -D 0
ALSA lib control.c:953:(snd_ctl_open_noupdate) Invalid CTL 0
cannot open mixer: No such file or directory
scott875@scott875-desktop:~$ 

```

---

### Post by sdowney717 on 2014-03-28
I got it running with 

alsamixer -c 1

---

### Post by sdowney717 on 2014-03-28
It does not show channels like on another board where I could select 2 through 6.

But it does show the 5.1 sound channels.

I wonder if they work. The sound properties control in Ubuntu, only shows stereo.
So is something wrong? That I have to run alsamixer -c 1 for it to come up?

---

### Post by sdowney717 on 2014-03-28
> **bapoumba said:**
> Can you try with **alsamixer -d 0** (or 1), see **man alsamixer**. You seem to have the same card nb for 2 different device nb in aplay -l (post #20).


You led me to the solution, thanks for the help. Although I wonder why I have to use extra arguments.

---

### Post by Elfy on 2014-03-28
Now you've got it to open - F6 to see the other channels and use those perhaps to find the other option. 

Something is definitely up if alsamixer doesn't work - no idea what though

---

### Post by sdowney717 on 2014-03-28
> **Elfy said:**
> Now you've got it to open - F6 to see the other channels and use those perhaps to find the other option. 

Something is definitely up if alsamixer doesn't work - no idea what though

F6 simply shows card 1, nothing else. I tried default and get nothing but red text.

---

### Post by sdowney717 on 2014-03-28
Even though it shows various surround channels, front, surround, center, LFE, only stereo plays. The black mini jack plays same sound as the front green minijack. Maybe due to the sound profile in ubuntu sound settings does not show anything for 5.1 sound?

seeing these things, makes me wonder the driver is incomplete for this chipset.

I have a dolby 5.1 sound test files I downloaded from dolby web site. Channel check etc...

---

### Post by bapoumba on 2014-03-28
> **sdowney717 said:**
> I got it running with 

alsamixer -c 1

OK, that is what I tried here (although with -c 0 as I have only one card).
In the previous command, man says -d and not -D, not sure it makes any difference.

Glad to see you got something working, may be you can play around with the different options :)

---

