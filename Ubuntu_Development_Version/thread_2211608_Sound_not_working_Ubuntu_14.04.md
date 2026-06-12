---
title: "Sound not working Ubuntu 14.04"
date: 2014-03-16
forum: Ubuntu Development Version
---

### Post by Jeremy_King on 2014-03-16
Sound was working for a while, but when I tried to listen to music today there was no sound. In the sound settings there shows no drivers at all, not even a dummy output. Any help would be greatly appreciated.

---

### Post by Yellow Pasque on 2014-03-16
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Jeremy_King on 2014-03-16
I'm not sure what I am supposed to give you. 
is it this?> [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh)

---

### Post by Yellow Pasque on 2014-03-16
No, you're supposed to run those commands and give me the link to your info (after you choose to upload the information).

Example: [http://www.alsa-project.org/db/?f=7dea94edb648f4ca474498b4c38ee41ea4830bb8](http://www.alsa-project.org/db/?f=7dea94edb648f4ca474498b4c38ee41ea4830bb8)

---

### Post by Jeremy_King on 2014-03-16
I didnt get any prompt to upload info (at least I dont think I did, I am somewhat new to Linux based systems).
Here is the output from the terminal:

jeremy@jeremy-Aspire-5253:~$ cd ~/
jeremy@jeremy-Aspire-5253:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.s
--2014-03-16 17:22:44--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org) ([www.alsa-project.org](www.alsa-project.org))... 77.48.224.243
Connecting to [www.alsa-project.org](www.alsa-project.org) ([www.alsa-project.org)|77.48.224.243|:80](www.alsa-project.org)|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh) [following]
--2014-03-16 17:22:45--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh)
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Connecting to git.alsa-project.org (git.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-sh]
Saving to: &#8216;alsa-info.sh&#8217;

    [  <=>                                 ] 27,678       114KB/s   in 0.2s   

2014-03-16 17:22:47 (114 KB/s) - &#8216;alsa-info.sh&#8217; saved [27678]

bash: alsa-info.s: No such file or directory

---

### Post by Yellow Pasque on 2014-03-16
> bash: alsa-info.s: No such file or directory 

It's alsa-info.s**h**

---

### Post by Jeremy_King on 2014-03-16
Okay got it. [http://www.alsa-project.org/db/?f=347652a8be4a4c4207a55365bd944ff5e13cbecd](http://www.alsa-project.org/db/?f=347652a8be4a4c4207a55365bd944ff5e13cbecd)

---

### Post by Yellow Pasque on 2014-03-16
> !!Sound Servers on this system
!!----------------------------
No sound servers found.

That's... odd. Did you remove pulseaudio?

---

### Post by Jeremy_King on 2014-03-16
I did, another person suggested I remove it, then reinstall it.

---

### Post by Yellow Pasque on 2014-03-16
So did you reinstall it?
```
sudo apt-get install pulseaudio
```

---

### Post by Jeremy_King on 2014-03-16
I did. I guess it didn't work the first time, but I tried it again and it installed properly. Here is the new info: [http://www.alsa-project.org/db/?f=921a706d676570237a952de3778d0a20aa166115](http://www.alsa-project.org/db/?f=921a706d676570237a952de3778d0a20aa166115)

Despite doing that, my problem remains. Now when I try to go to my sound settings, they wont even open.

---

### Post by lisati on 2014-03-16
*Thread moved to **Ubuntu +1**.*

---

### Post by Yellow Pasque on 2014-03-17
Run:
```
rm -r ~/.config/pulse
```
Log out and back in. Better?

---

### Post by tobyjfirth on 2014-03-31
I have been using 14.04 for a while but today the audio stopped working. After looking through several solutions of which none of them worked I re-installed 14.04 but the audio is still not working. I don't think it is a hardware issue as when I booted into windows the audio was fine.
Having looked at another thread I have run the alsa info script and here are the results:
[http://www.alsa-project.org/db/?f=ac837e0d871d7d550bbce55edb761addd4860bc3](http://www.alsa-project.org/db/?f=ac837e0d871d7d550bbce55edb761addd4860bc3)

Thanks for any help.

---

### Post by estamets on 2014-04-03
Mine stopped working also. Although it started today. It looks to me like we're both running stock intel hardware. I'll see what I can dig up.

I've tried (and you can too)  pulseaudio --kill *This kills the process*
                                       pulseaudio   *This restarts the process*

As far as what I've read, both of these command can be run as user.. Not root.

Still no luck but I'll keep digging.

---

### Post by uhop on 2014-04-03
I have the same problem --- 14.04 no sound at all.  I have a Sound applet, which shows only one output: Dummy Output. In reality I have a built-in on-motherboard "sound card", and an external USB-based DAC. Both worked before the upgrade. I collected the info here: [http://www.alsa-project.org/db/?f=250b0e9909e40f15aaca7de7629d1db20b1ad108](http://www.alsa-project.org/db/?f=250b0e9909e40f15aaca7de7629d1db20b1ad108), pulseaudio is installed, and I never messed with it,  and I unsuccessfully tried to remove ~/.config/pulse. Nothing helps so far.

---

### Post by cariboo on 2014-04-03
merged two similar threads.

---

### Post by mamamia88 on 2014-04-03
Mine just stopped working as well in xubuntu 14.04

---

### Post by lowlymarine2 on 2014-04-03
Having the same issue. Everything was working fine a few hours ago, then I ran some updates and rebooted to no sound and a "Dummy Output." Looking through the apt logs, it seems the only potentially relevant packages that changed were related to systemd, specifically these:
[http://packages.ubuntu.com/trusty/systemd-services](http://packages.ubuntu.com/trusty/systemd-services)
[http://packages.ubuntu.com/trusty/libpam-systemd](http://packages.ubuntu.com/trusty/libpam-systemd)

---

### Post by xREDEMPTIONx on 2014-04-03
Was having the same problem a few days ago after upgrading to 14.04 from  13.10, lost all sound. I did manage to get it working again and I believe the issue was with pulseaudio. Although  I'm not really sure what it was that made it start working I do remember some things.
Verify first your card is recognized and are getting sound through alsa
```
aplay -l
```
```
aplay /usr/share/sounds/alsa/Front_Center.wav
```
In my case my onboard card (HDA Intel MID) and (HDA Nvidia) HDMI were being recognized and I was able to hear the 'front center' voice.
I also remember purging pulseaudio 
```
sudo apt-get purge pulseaudio
```
 and it giving an error about some dir not being empty so it was not removed. I manually deleted the files and directories it gave messages about
then delete your local config files,
```
rm -r ~/.pulse ~/.asound* ~/.pulse-cookie
```
 re-install pulseaudio
```
sudo apt-get install pulseaudio
```
reboot just incase
hope for sound! 

I also remeber not having a sound indicator at one point, if this happens make sure the package "indicator-sound" is installed.
 Not being to hear the test sounds in the sound panel, make sure "libcanberra-pulse" is installed.

---

### Post by irishbandit2 on 2014-04-04
Can confirm no sound after updates of last night.
To tired to work on it now.

---

### Post by bug67 on 2014-04-04
Count me in for 2 machines.  Can also confirm the shutdown issue stated in [this thread.]("http://ubuntuforums.org/showthread.php?t=2214941")

---

### Post by rimez on 2014-04-04
I have a similar issue after updating 14.04 this morning. It seems any application that requires root cannot be run from the desktop anymore (including pulseaudio).

---

### Post by grumblebum2 on 2014-04-04
Seems to be fixed with the latest round of systemd related updates.
```
sudo apt-get update && sudo apt-get upgrade
```
Then...
```
sudo reboot
```

---

### Post by bug67 on 2014-04-04
> **grumblebum2 said:**
> Seems to be fixed with the latest round of systemd related updates.
```
sudo apt-get update && sudo apt-get upgrade
```
Then...
```
sudo reboot
```

That appears to have patched things up, however, I am unable to add the volume indicator back to my panel.  Tried reinstalling to no avail.  Any ideas?

---

### Post by 23dornot23d on 2014-04-04
Now have sound back again

  148  aptitude install pulseaudio
  149  aptitude install pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils

---

### Post by sparhawkthesecond on 2014-04-04
I fixed it before I got  these upgrades, which might be helpful to others. It seemed I was removed from the audio group for some reason.


```
         $ alsamixer
        alsamixer cannot open mixer: No such file or directory
        $ sudo alsamixer # works
        $ groups
        sparhawk adm cdrom sudo dip plugdev lpadmin sambashare bumblebee
        $ sudo usermod -a -G audio sparhawk
        $ sudo groups sparhawk # confirms I've been added
        
```
Then log out and back in.

---

### Post by grumblebum2 on 2014-04-04
> **sparhawkthesecond said:**
> I fixed it before I got  these upgrades, which might be helpful to others. It seemed I was removed from the audio group for some reason.


```
         $ alsamixer
        alsamixer cannot open mixer: No such file or directory
        $ sudo alsamixer # works
        $ groups
        sparhawk adm cdrom sudo dip plugdev lpadmin sambashare bumblebee
        $ sudo usermod -a -G audio sparhawk
        $ sudo groups sparhawk # confirms I've been added
        
```
Then log out and back in.

By default you are not in the **audio** group in 13.10 or 14.04
and don't need to be for sound to work.
With the recent updates to systemd, sound should now work without adding yourself to the audio group.

---

### Post by frank18 on 2014-04-04
I don't know how you guys have sound problems! i've been running Ubuntu 14.04 for a while now and never had sound problems or other problems for that matter,It must be either the way  the  install is made or hardware compatibility.
First  if you using  12.04LTS should never upgrade to any of the testing editions always wait to the next LTS. then if you want to run 13.04,13.10,
just make an iso of those editions,never upgrade to 14.04 from 13.04 or 13.10, just make an iso of 14.04  and install,of course you can do it from any edition but you're bound to serious problems,i have learned my lesson,i tried all the above testing upgrades and failed most of the time.I know that i can get my present install of Ubuntu14.04 to become LTS edition ,but when April 17 comes i will make another  Clean install of Ubuntu 14.04LTS and i know that i will have no software issues.

---

### Post by grumblebum2 on 2014-04-04
> **frank18 said:**
> I don't know how you have sound problems! i've been running Ubuntu 14.04 for a while never had sound problems or other problems for that matter,
You just aren't trying hard enough. :P

---

### Post by QIII on 2014-04-04
As stated above, there was some sort of mix up on the packages included in yesterday's update, including systemd.

I reported a bug on launchpad for Kubuntu about the same time as someone posted the same for Ubuntu.  It was resolved in less than two hours.

If you are still getting errors with app indicators, check Launchpad to see if it has been reported.  I'm thinking there were a lot more messed up packages and they fixed some of the critical ones last night and are still working on others.

By the way, I was hit with problems with logout, sound and networkmanager's app indicator, all of which were in the pile of corrected stuff by about 1:00am Pacific time.

---

### Post by frank18 on 2014-04-04
> **grumblebum2 said:**
> You just aren't trying hard enough. :P

I don't know what you mean! but if it's the usage of sound! let me tell you, few people use the sound as much as me, i use my Pc for audio and streaming mostley and music composing since i'm a musician.

---

### Post by grumblebum2 on 2014-04-04
> **frank18 said:**
> I don't know what you mean! but if it's the usage of sound! let me tell you, few people use the sound as much as me, i use my Pc for audio and streaming mostley and music composing since i'm a musician.

Relax Frankie, it was a joke ....hence the little funny icon. :rolleyes:
Often used phrase....**"If it ain't broke, you're not trying hard enough."**

---

### Post by uhop on 2014-04-04
The latest update fixed the problem for me without doing anything special --- updated & rebooted.

---

### Post by sparhawkthesecond on 2014-04-04
> **grumblebum2 said:**
> By default you are not in the **audio** group in 13.10 or 14.04
and don't need to be for sound to work.
With the recent updates to systemd, sound should now work without adding yourself to the audio group.

Okay. I just thought I'd post my solution up just in case it was a different cause for the same problem. What's interesting is that *without* the systemd upgrades, adding myself to the audio group *did* work.

==EDIT==
Having said that, I removed myself from the audio group and logged back in, and everything is fine.

---

### Post by corey10 on 2014-04-17
I updated ubuntu today from 13.10 to 14, now I have no sound, I tried what was suggested by poster #20 and had to reinstall sound indicator. still nothing. should I just do a fresh install? when I go to sound settings it goes to system settings. when I type aplay -l this is what I get 
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by delorin on 2014-04-19
here is mine [http://www.alsa-project.org/db/?f=1789445647b53099375ee326fda29b166fa00d0e](http://www.alsa-project.org/db/?f=1789445647b53099375ee326fda29b166fa00d0e)

---

### Post by oldos2er on 2014-04-19
Since 14.04 is now a regular release, please post any questions or problems in the regular support areas of the forum.

Closed.

---

