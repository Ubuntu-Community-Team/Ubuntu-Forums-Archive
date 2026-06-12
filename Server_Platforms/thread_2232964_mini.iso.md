---
title: "mini.iso"
date: 2014-07-05
forum: Server Platforms
---

### Post by hbc2 on 2014-07-05
Hi,

Does the mini iso install a minimum server system? From what I understand the mini iso just doesn't have much in the way of packages and then proceeds to download them.  So I guess you would end up with the same system as you would with the "full" iso (and then doing an update after the install from the "full" iso).  Is that correct?

---

### Post by Bucky Ball on 2014-07-05
mini.iso installs the Ubuntu kernel. That's it. You can set it up to be a server, among other things, when you get to that part of the install. What are you looking for, exactly?

If you don't tick anything when you get to the section which asks what kind of system you are after, it boots back into a CLI login. Login and install what you want, and I mean starting from the desktop environment, if you want one. I only use mini installs and go something like this at that first cursor:

```
sudo apt-get install xfce4 xfwm4 lightdm synaptic xorg lxterminal gdm
```

That is generally enough to get you going. You can, of course, do what you like. For more info, see here:

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Explanation of minimal installs and examples:
[https://help.ubuntu.com/community/Installation/LowMemorySystems#XFCE](https://help.ubuntu.com/community/Installation/LowMemorySystems#XFCE)

Definitely a course worth pursuing, but I recommend some research, sitting down with a beverage of choice and a pencil and paper before leaping in. Get it right. I'd never go back. I like it just so ... ;)

---

### Post by hbc2 on 2014-07-06
Hi,

Thanks for your reply!  The links you gave were helpful.
I played around with installing from the mini iso many many times today.



[COLOR=#000000]"mini.iso installs the Ubuntu kernel. That's it. You can set it up to be a server, among other things, when you get to that part of the install. "[/COLOR]


Right.  During the expert install option there is a screen that allows you to choose which kernel you would like.  I don't know enough on how to look at what is complied into the various kernels.  Would you happen to know if the ALC892 audio drivers are included?  In   ./usr/src/linux-headers-3.13.0-30/sound (generic kernel) which came with my install there seem to be quite a few drivers but not mine specifically shown.  

"[COLOR=#000000]What are you looking for, exactly?"
[/COLOR]
I'd like to get a simple install of linux to play around with.  Ultimately I would like to setup Xen so I can then play around with linux distros in virtual environments without toasting my main rig.   However, Xen is further down the road.


Right now I would like to run some sort of audio software that is remote controlled from my Android phone.  I want to run it from the base install (dom0 when I get Xen going)  so I don't have to deal with PCI passthrough. However, just getting command line audio going is turning into an odyssey and I'm still not there yet. 


Do you have any suggestions on which forum or options I should try next?  


Here is where I'm at:


Right after my fresh install of ubuntu from the mini iso (with only the ssh option chosen) I did the following.




Checked to see my install could see my hardware.  (it does)
-----------------------------
[FONT=arial]root@ubuntu:/# lspci | grep Audio[/FONT]
[FONT=arial]00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)[/FONT]
[FONT=arial]00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]root@ubuntu:/# cat /proc/asound/card*/codec* | grep Codec[/FONT]
[FONT=arial]Codec: Intel Haswell HDMI[/FONT]
[FONT=arial]Codec: Realtek ALC892[/FONT]
[FONT=arial]-----------------------------

[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Then I installed alsa  (everything went fine and I think it installed a few other packages.)[/FONT]
[FONT=arial]-----------------------------

[/FONT]
[FONT=arial]sudo apt-get install alsa alsa-tools [/FONT]
[FONT=arial]-----------------------------




Then I ran speaker-test but it failed
-----------------------------



[/FONT]
[FONT=arial]root@ubuntu:/# speaker-test[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]speaker-test 1.0.27.2[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Playback device is default[/FONT]
[FONT=arial]Stream parameters are 48000Hz, S16_LE, 1 channels[/FONT]
[FONT=arial]Using 16 octaves of pink noise[/FONT]
[FONT=arial]ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave[/FONT]
[FONT=arial]Playback open error: -2,No such file or directory[/FONT]
[FONT=arial]-----------------------------

[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I googled around and found some page that suggested to look at what alsa had to work with.[/FONT]
[FONT=arial]It seems to see my hardware ok.[/FONT]
[FONT=arial]-----------------------------

[/FONT]
[FONT=arial]root@ubuntu:/# aplay -l[/FONT]
[FONT=arial]**** List of PLAYBACK Hardware Devices ****[/FONT]
[FONT=arial]card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0][/FONT]
[FONT=arial]  Subdevices: 1/1[/FONT]
[FONT=arial]  Subdevice #0: subdevice #0[/FONT]
[FONT=arial]card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1][/FONT]
[FONT=arial]  Subdevices: 1/1[/FONT]
[FONT=arial]  Subdevice #0: subdevice #0[/FONT]
[FONT=arial]card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2][/FONT]
[FONT=arial]  Subdevices: 1/1[/FONT]
[FONT=arial]  Subdevice #0: subdevice #0[/FONT]
[FONT=arial]card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog][/FONT]
[FONT=arial]  Subdevices: 1/1[/FONT]
[FONT=arial]  Subdevice #0: subdevice #0[/FONT]
[FONT=arial]card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital][/FONT]
[FONT=arial]  Subdevices: 1/1[/FONT]
[FONT=arial]  Subdevice #0: subdevice #0[/FONT]
[FONT=arial]-----------------------------









[/FONT]
[FONT=arial]I tried mpg123 but that needed pulseaudio which I installed but that turned mess by loading 50+ other packagews.  Not only did it not work it also removed alsa-base.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I'll reinstall ubuntu from the mini iso and start over since I think i've wrecked things by now.  But I'm not really sure what to try next.  Any suggestions?[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]

---

### Post by Bucky Ball on 2014-07-06
For audio you are probably going to want to install 'ubuntu-restricted-extras'. That will drag in some third-party codecs and other things. I did see a thread the other day about controlling audio on Linux box via phone, so it is possible.

As your original issue regarding mini-isos seems to be answered, I'd mark this thread as solved and start a new one with a descriptive title in '***Multimedia & Video***' regarding your audio questions. That will increase your chances of getting help.

Post a link to it here if you like and good luck. ;)

---

### Post by ibjsb4 on 2014-07-06
The mini.iso is what I use to install anything or everything.  Works great on a cd or flash drive.  What do you want to achieve of this?  A full install or a custom install?

---

### Post by Bucky Ball on 2014-07-06
> **ibjsb4 said:**
> What do you want to achieve of this?  A full install or a custom install?

Please re-read post three. OP explains what they are aiming for. ;)

---

### Post by ibjsb4 on 2014-07-06
Just like to hear it again :)

---

