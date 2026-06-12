---
title: "ubuntu 16.04 | Headphone problem"
date: 2015-12-23
forum: Ubuntu Development Version
---

### Post by ebenash on 2015-12-23
Hey guys,

I've installed ubuntu (gnome)16.04 on my dell inspiron 13 (7359) laptop. Everything is working except headphone. 
Please help me to fix it.

Thanks.

P.S. : I'm aware that ubuntu 16.04 is still in development, but I had similar issues with (ku|xu|ubuntu 15.10) along with nonfunctional wireless. 
P.P.S. : If you need any additional logs please

---

### Post by QDR06VV9 on 2015-12-24
Have you yet tried in the terminal 'alsamixer' to see if there is any volume or even muted?

---

### Post by MikeMecanic on 2015-12-24
Work in all cases* in xubuntu (Dec. 21st build)
Work in all cases in Ubuntu Gnome (Dec.23rd build), except in Firefox


*Goggle Chrome audio streaming, Audio CD, MP3

---

### Post by grahammechanical on 2015-12-24
With the headphones plugged in Sound Settings will let you select headphones as an output option. With the headphones not plugged in there will be no option to select headphones as the output.

Regards.

---

### Post by ebenash on 2015-12-25
Thanks guys.
I tried running alsamixer ( plz check attached screenshot), but I don't see headphone option in it. 
Is it because of driver?

Merry X'mas n Happy Holidays.

---

### Post by MikeMecanic on 2015-12-25
Headphone output is not detected.  Your on the Skylake chipset and many of changes that occur in Kernel 4.4 are made for Skylake. 
What Drivers do you have,is it Microcode?  Did you enable Additional Drivers in Software and Updates?  

```
ux@rc6:~$ [COLOR=#ff0000]ubuntu-drivers devices[/COLOR]
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free
ux@rc6:~$ [COLOR=#ff0000]ubuntu-drivers list[/COLOR]
intel-microcode
ux@rc6:~$ [COLOR=#ff0000]lsb_release -a && uname -r[/COLOR]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
4.4.0-040400rc6-generic
ux@rc6:~$ [COLOR=#ff0000]aplay -l[/COLOR]
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: 92HD89D3 Analog [92HD89D3 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
ux@rc6:~$
```

---

### Post by ebenash on 2015-12-25
Hey Mike,

Here's my output

> 

ash@mars:~$ ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free


ash@mars:~$ ubuntu-drivers list
intel-microcode
ash@mars:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:        16.04
Codename:       xenial
4.3.0-5-generic
ash@mars:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20722 Analog [CX20722 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ash@mars:~$ 




How do I update my kernel to 4.4?

---

### Post by MikeMecanic on 2015-12-25
First, try to downgrade to Kernel 4.3.0.2 because  there was a bug this week with 4.3.0.5. See if you have Headphone output after?  Reboot and press the** left shift key** to load Grub menu (advanced) and boot with 4.3.0.2 generic.  Will give you the command lines for 4.4 rc6 upgrade in  moment.

---

### Post by MikeMecanic on 2015-12-25
> **ebenash said:**
> 
P.S. : I'm aware that ubuntu 16.04 is still in development, but I had similar issues with (ku|xu|ubuntu 15.10) along with nonfunctional wireless. 


**Your gonna get a weird reaction(s) in Software Updater**, you will receive a partial upgrade first, just follow the process.  
You will have to enable all canonicals and ppa's stuff in Software & Updates/Other Software/Reload(*). While your there, set the Ubuntu server to the main United States server/Reload.
(*)_You will have to check that each time (before/after) you run the updater_.  After partial updates, reboot and re-check for updates.


You may wana run Proposed for additional updates after (don't by shy).  I hope for you that this upgrade will also fix the wireless issue.  


Note that I never try it on Ubuntu Gnome.  But I try it (rc5) under ubu, ubu_TT.3, kubu,xubu and Kylin 16.04LTS in english.
It's xubuntu that gave me the best results by far:  Solid rock (second perfect week with Proposed enable).


Good luck!

**Kernel 4.4 rc6 command lines:**
```
cd /tmp
```
```
 wget \
```
```
kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc6-wily/linux-headers-4.4.0-040400rc6_4.4.0-040400rc6.201512202030_all.deb \
```
```
kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc6-wily/linux-headers-4.4.0-040400rc6-generic_4.4.0-040400rc6.201512202030_amd64.deb \
```
```
kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc6-wily/linux-image-4.4.0-040400rc6-generic_4.4.0-040400rc6.201512202030_amd64.deb
```
```
sudo dpkg -i linux-headers-4.4*.deb linux-image-4.4*.deb[
```

**Close all apps**
```
sudo reboot
```

You will boot default in Kernel 4.4 rc6 after.

You will always have the choice to boot into a lower Kernel version after (Hold LeftShift Key).  If you succeed you may wanna run it alone...

EDIT:  You will have to force updates by clicking on *Try Again*, sometime 3 times to get them.  It may take 2 days before Update Manager runs normally.  It is a long upgrading/updating process and you must be patient.

---

### Post by ebenash on 2015-12-26
Hey Mike, 

Unfortunately, it didn't work. I updated the system and installed the kernel 4.4 ( For some reasons, my touchpad has also stopped working).

---

### Post by MikeMecanic on 2015-12-26
Don't get discourage!  Xenial is under test.  Will do a fresh install of ubugnome tomorrow to see if it loads correctly. You can try rc4 next time and then load rc5 after.  Just replace rc and date as shown below.  Can you reach the grub menu? Press leftshift key when you open the computer, that will open the Grub menu.  Then choose **Advanced Options for Ubuntu** and load a lower kernel version (generic). You should have 4.3.0.2 and 4.3.0.5 plus 4.4 rc6.  It is almost impossible that you can reach the Grub menu.

_In Ubuntu Kylin I was always in a black screen on reboot (rc5 or rc4)_.  When you say your computer stop working, is it that your in a black screen?  Try to load the Grub menu to fix this issue.


rc5 tag date: 201512140221 
rc4 tag date: 201512061930

---

### Post by ebenash on 2015-12-26
Thanks for all the help mike. 
Today I tried ubuntu 15.10 just to give it a go again, and much to my surprise everything worked fine, out of box ( even wifi n headphones). 
I'm running kernel 4.2.0-22-generic ( which for some reason, is able to detect headphones).


Well, cant tag this thread as 'solved' but atleast I'm sure dell inspiron 13 is well supported in ubuntu 15.10.
Maybe I'll upgrade to 16.04, once it get innto beta

---

### Post by Dobromir on 2016-06-06
I experienced the same issue on my Dell XPS 13 9350. After upgrading from 14.04 to 16.04 the sound from the headphones disappeared while speakers were working fine. However I managed to fix it.

[SIZE=4]_Issue Context_[/SIZE]

I noticed the following suspicious lines logged in*/var/log/syslog*file that are traced when I restart *pulseaudio. *

...
Jun  6 11:58:29 miro-xps pulseaudio[5360]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/B-analog-output-headphones.conf:23] Name makes no sense in 'General'
Jun  6 11:58:29 miro-xps pulseaudio[5360]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/B-analog-output-headphones-2.conf:23] Name makes no sense in 'General'
...

To validate one have got the same issue open two terminals (Ctrl+Alt+T):
In terminal 1 run the command:
*tail -f **/var/log/syslog*file

In terminal 2 run:
[I]pulseaudio --kill
[/I]
Whe *pulseaudio *restarts it will trace error messages in *syslogfile*.

[SIZE=4]_Resolution_[/SIZE]

Delete the incorrect line from the config files:

/usr/share/pulseaudio/alsa-mixer/paths/B-analog-output-headphones.conf
/usr/share/pulseaudio/alsa-mixer/paths/B-analog-output-headphones-2.conf

1. Edit file *B-analog-output-headphones.conf*
1.1 Run command*:*[I]
sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/B-analog-output-headphones.conf 
[/I]1.2 Delete line starting with *name, e.g.:*
*name = analog-output-headphones*

2. Edit file *B-analog-output-headphones-2.conf*
1.1 Run command*:*[I]
sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/B-analog-output-headphones-2.conf 
[/I]1.2 Delete line starting with *name, e.g.:*
*name = analog-output-headphones*

3. Restart *pulseaudio *deamon by running command:
*pulseaudio --kill*

This fixed my issue. I now have sound from both: speakers and headphones. The *name* entry is reported as wrong in other config files as well (B-analog-input-*-mic.conf). I would guess that deleting it from those file would fix mic issues.

---

### Post by howefield on 2016-06-06
Thread closed.

We are on to Yakkety Yak in this forum now.

---

