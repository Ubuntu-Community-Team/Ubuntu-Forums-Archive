---
title: "ALSA Upgrade Script Redux"
date: 2011-02-04
forum: Tutorials
---

### Post by Yellow Pasque on 2011-02-04
[COLOR="Red"]WARNING:[/COLOR] The ALSA script was useful back in the day, but it is now more dangerous than helpful for a majority of users, and there are usually better methods of upgrading. [COLOR="Red"]USE AT YOUR OWN RISK.[/COLOR]

> DISCLAIMER: Don't use this script unless you know what it's really doing (building vanilla ALSA from source and installing it over the older, Ubuntu-patched version on your system). Do not PM me for support as your request will go to the great bit bucket in the sky. Please do not post irrelevant support requests in this thread because the old thread had about 99% support requests and 1% people actually helping/contributing (start your own thread in Hardware or Multimedia forum). Finally, do not blame me for any problems this causes (it would be far better to find a properly packaged ALSA than using this hack). I (and hopefully others) will do our best to help you, but ultimately, if it breaks, you keep the pieces.

Ok, here's the new ALSA upgrade script for ALSA 1.0.25. The script is not in line with Debian/Ubuntu rules for package handling. It just overwrites existing files. You won't see any changes on the ALSA package-ids within Synaptic!

The script recognizes severe problems during the installation and will stop automatically. It shouldn't mess up your setup.
If the script stops with an error-message nothing should have been touched!
In the worst case scenario the -r restore option restores your old system status as good as possible. It'll reinstall kernel, kernel-headers and Alsa related packages.

Ubuntu upgrades/updates might overwrite your Alsa installation once in a while (e.g. Major upgrades, kernel-upgrades or ALSA-package upgrades).
You just need to rerun the upgrade-script using the -i option in this case (if you still have the compiled sources on the disk).

Short Alsa-Upgrade script install instructions:

0. before you begin, close all package managers (Synaptic, Muon, Software Center, etc.)
1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xzvf AlsaUpgrade-1.0.25-3.tar.gz
4. chmod +x AlsaUpgrade-1.0.25-3.sh
5. sudo ./AlsaUpgrade-1.0.25-3.sh -d
6. sudo ./AlsaUpgrade-1.0.25-3.sh -c
7. sudo ./AlsaUpgrade-1.0.25-3.sh -i
8. sudo shutdown -r 0

Logging: I recommend to log all the upgrade steps, e.g.

script -a -c "./AlsaUpgrade-1.0.25-3.sh -d" /tmp/Alsa_1.0.25-1_upgrade_download.log

You'll find a log file /tmp/Alsa_1.0.25-3_upgrade_download.log as soon as the script is finished.
You need to run this procedure for every single step. Choose whatever logfile names.

Test and Troubleshooting

After reboot you can type:

cat /proc/asound/version

This will let you know if you're running the new version.

The easiest and most reliable test to verify if Alsa is working is "aplay" - the Alsa player application. If aplay won't work -- nothing else will work. Make sure that all your channels are unmuted and volume is up!

To get ALSA apps mixed in through pulseaudio, you need to add the bolded line to /usr/share/alsa/alsa.conf
```

@hooks [
        {
                func load
                files [
                        **"/usr/share/alsa/pulse.conf"**
                        "/etc/asound.conf"
                        "~/.asoundrc"
                ]
                errors false
        }
]

```

---

### Post by DiabboVerdde on 2011-02-04
Update script sounds really great. The only bad thing to me is that both the old one and the new one are failing on the compilation step for Lucid (in which XBMCLive is built on).

Thanks for assuming the maintenance of the script!

Regards,

**DiabboVerdde**

---

### Post by Yellow Pasque on 2011-02-04
Can you post error output? I tested it on a Maverick Virtualbox install and had no issues.

---

### Post by plun on 2011-02-04
With Natty it only gives me a "Dummy Output" within Sound Prefs, also with pavucontrol... I also killed PA if something was wrong with that.

The script runs just fine.'

EDIT
> 
plun@plun-laptop:~$ aplay -l
aplay: device_list:240: no soundcards found

Something must be wrong with the isntalll

---

### Post by Yellow Pasque on 2011-02-04
Sigh.. I hope natty adopts alsa 1.0.24 and makes this script unnecessary. I have a spare install of natty. I will test it there when I have more caffeine and less alcohol flowing through me. Thanks for the heads up.

---

### Post by plun on 2011-02-05
Hehe...:lolflag:

Well, I ran the script again with no luck

The alsa-info script gives this:

[http://paste.ubuntu.com/562974/](http://paste.ubuntu.com/562974/)

dmesg gives unknown symbols.....:confused:

```
plun@plun-laptop:~/Desktop$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```


EDIT

Restarted with Ubuntus 2.6.38 kernel and it works....:guitar:

alsa-info:

[http://paste.ubuntu.com/562977/](http://paste.ubuntu.com/562977/)



EDIT AGAIN

No the driver version seems to be 1.0.23 with this.....:confused:

Reinstalled 2.6.38-RC3 (Ubuntu Mainline)  but it gave the same output as earlier.... all Ubuntu kernels works but with the 1.0.23 driver loaded.  


--

---

### Post by genail on 2011-02-05
No luck with Ubuntu 10.10 (dmesg unknown symbols) and also...

Revert script is not working correctly on Ubuntu 10.10 with 2.6.35-25-generic x86_64 kernel.
After a little research I discovered directory /lib/modules/2.6.35-25-generic/kernel/sound/modules/ which doesn't belong to any package. After removing it my old stereo (-_-) sound is working again.

---

### Post by plun on 2011-02-05
> **genail said:**
> No luck with Ubuntu 10.10 (dmesg unknown symbols) and also...

Revert script is not working correctly on Ubuntu 10.10 with 2.6.35-25-generic x86_64 kernel.
After a little research I discovered directory /lib/modules/2.6.35-25-generic/kernel/sound/modules/ which doesn't belong to any package. After removing it my old stereo (-_-) sound is working again.

I manually uninstalled from the source and then reinstalled all alsa-packages and the kernel (image and headers)

Back with 1.0.23 without any issues.

Also checked this mailing-list but its "over my head" :-\"

[http://mailman.alsa-project.org/pipermail/alsa-devel/2011-February/thread.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2011-February/thread.html)

Lets see when Temüjin wakes up..... when he feels better !

---

### Post by plun on 2011-02-07
New compile after some readings......

I changed to   **--with-oss=no**   (line 327 in the script)

Natty also got a new kernel yesterday  (2.6.38-2)

Now it works  !!  :guitar:

[http://paste.ubuntu.com/563989/](http://paste.ubuntu.com/563989/)


EDIT

One finding, I cannot control my Firefox audio stream... neither with sound prefs or pavucontrol, 
~.pulse removed,  pulseaudio also killed for a test.

Firefox streams just works with my internal speakers and I normally change to my bluetooth output.



--

---

### Post by GonzalitoUY on 2011-02-07
> **plun said:**
> New compile after some readings......

I changed to   **--with-oss=no**   (line 327 in the script)

Natty also got a new kernel yesterday  (2.6.38-2)

Now it works  !!  :guitar:

[http://paste.ubuntu.com/563989/](http://paste.ubuntu.com/563989/)


EDIT

One finding, I cannot control my Firefox audio stream... neither with sound prefs or pavucontrol, 
~.pulse removed,  pulseaudio also killed for a test.

Firefox streams just works with my internal speakers and I normally change to my bluetooth output.



--
With that modification, it also works on Maverick.
Many thanks.
EDIT:Just in case, after update, run "alsaconf".In my case, got the card recognized after rebooting, and FF and system sound were working, but media players didn't (that was fixed with alsaconf, then gstreamer-properties)

---

### Post by Yellow Pasque on 2011-02-07
Ok, I will modify it. Thanks for testing/verifying.
@plun, does this fix your Firefox issue: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by plun on 2011-02-07
> **Temüjin said:**
> Ok, I will modify it. Thanks for testing/verifying.
@plun, does this fix your Firefox issue: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

Ok... great that this also works for Maverick.

The problem is most likely this with OSS and Ubuntu baked kernels.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300)


------------------------------------------

Going to test the firefox fix, thanks !


EDIT

Works....:guitar::popcorn:


Next step is maybe compiling PA from GIT.....):P



--

---

### Post by courtjester on 2011-02-07
What happened to the script download?

---

### Post by Yellow Pasque on 2011-02-07
> **courtjester said:**
> What happened to the script download?
Oops. I took off the old version and didn't confirm the upload of new version. Fixed (thanks).

---

### Post by strange1712 on 2011-02-07
Thanks for this updated script. Had to install "manually" dependencies as I hadn't right GPG keys for some ppa's (dont know which)...
This helped me fix an issue I had with my ALC889A (Intel HDA) card in Maverick.
Thank you!
:guitar:

---

### Post by jeremybar on 2011-02-07
I am running Maverick 64 bit on a Macbook Pro 13 inches version 7,1

```
sudo dmidecode -s system-product-name
MacBookPro7,1
```

Importantly, I ran AlsaUpgrade-1.0.24-2.sh successfully.

My purpose here was to see if the new version of Alsa 1.0.24 would include a fix for enabling the microphone integrated in the iPhone headset.  The hardware supports it, as it works fine on Mac OS X, but it would be great if it would also work with my favorite distribution.

I have the following in /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=mbp55
```

Any how, I did get a benefit with the upgrade: the sensitivity of the case integrated microphone got much better.  Perhaps I can use it as a workaround, but it also catches all the ambient noise, and it might not be optimal for Skype calls :-)

Also, I noticed that suspend to RAM would hang the system after the upgrade.
```
sudo update-initramfs -u
```
Seemed to have solved the problem.  Perhaps there was a left over Alsa kernel module on the old initrd ...

---

### Post by rubish.gupta on 2011-02-08
Thanx!! ran the script as mentioned and everything is working as it was before I messed it up trying to get my headphones working.

Ran alsa-info script after AlsaUpgrade-1.0.24-2, uploaded info is at 
[http://www.alsa-project.org/db/?f=64b84d6dff840a14c6339fc37728477ea2ad0bee](http://www.alsa-project.org/db/?f=64b84d6dff840a14c6339fc37728477ea2ad0bee)

Do you have any idea about how i can get my headphones working.

Thanks Again!!

---

### Post by Yellow Pasque on 2011-02-09
@rubish: [https://bbs.archlinux.org/viewtopic.php?pid=841520#p841520](https://bbs.archlinux.org/viewtopic.php?pid=841520#p841520)

---

### Post by plun on 2011-02-10
> **plun said:**
> 

Next step is maybe compiling PA from GIT....

--

OT !

Well up and running with both Alsa 1.0.24 and PulseAudio 1.0

PA from GIT is real "****" to compile, manually changed the makefile for two "breakers".

Up and running  :D

[[IMG]http://i.imgur.com/SGUFhs.jpg[/IMG]](http://imgur.com/SGUFh)

---

### Post by Wandang on 2011-02-10
used ur script yesterday. now i dont have any sound anymore. (wanted to get the mic to work)

i am using ubuntu 10.10 maverik 32bit
but dont bother, i am going to reinstall the whole system.

keep up the good work (that script helped me in the past many times ;))

---

### Post by ethan1701 on 2011-02-10
This script failed for me during compilation:
```
/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libasound_module_pcm_a52.la] Error 1
make[2]: Leaving directory `/opt/Alsa-1.0.24/alsa-plugins-1.0.24/a52'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/Alsa-1.0.24/alsa-plugins-1.0.24'
make: *** [all] Error 2

```
I don't have a /usr/local/lib/libavcodec.a file...

Running 10.10 with 2.6.35-25 kernel.

-Ethan

---

### Post by Yellow Pasque on 2011-02-10
@ethan: Do you have a different/upgraded installation of ffmpeg than the one from the repository?

---

### Post by ethan1701 on 2011-02-11
Yes, I believe I have.
How might I see the version of ffmpeg I have installed?

-Ethan

---

### Post by ethan1701 on 2011-02-12
```
ffmpeg -version 
``` tells me what version I have. duh.

```
FFmpeg version SVN-r25712, Copyright (c) 2000-2010 the FFmpeg developers
  built on Nov 10 2010 00:51:59 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.33. 0 / 50.33. 0
  libavcore      0.12. 1 /  0.12. 1
  libavcodec    52.94. 4 / 52.94. 4
  libavformat   52.84. 0 / 52.84. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.59. 0 /  1.59. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
FFmpeg SVN-r25712
libavutil     50.33. 0 / 50.33. 0
libavcore      0.12. 1 /  0.12. 1
libavcodec    52.94. 4 / 52.94. 4
libavformat   52.84. 0 / 52.84. 0
libavdevice   52. 2. 2 / 52. 2. 2
libavfilter    1.59. 0 /  1.59. 0
libswscale     0.12. 0 /  0.12. 0
libpostproc   51. 2. 0 / 51. 2. 0
```

So how does this effect the sound?

-Ethan

---

### Post by amsama on 2011-02-16
```
amsama@ubuntu:~/Downloads$ sudo ./AlsaUpgrade-1.0.24-1.sh -d
[sudo] password for amsama: 
sudo: ./AlsaUpgrade-1.0.24-1.sh: command not found

```:-|

I play music and got no sound. I guess i need tu update my ALSA, but i cant :(

```
amsama@ubuntu:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.

```

---

### Post by xoppaw on 2011-02-17
> **amsama said:**
> ```
amsama@ubuntu:~/Downloads$ sudo ./AlsaUpgrade-1.0.24-1.sh -d
[sudo] password for amsama: 
sudo: ./AlsaUpgrade-1.0.24-1.sh: command not found

```:-|

I play music and got no sound. I guess i need tu update my ALSA, but i cant :(

```
amsama@ubuntu:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.

```

this is the same errror i'm getting on a fresh install of xbmc live....
anyone gotten around this?

---

### Post by Yellow Pasque on 2011-02-18
Try it again.. ;)

---

### Post by xoppaw on 2011-02-18
i downloaded the script again, and here is what happens: 

```

maddox@xbmclive:~$ sudo ./AlsaUpgrade-1.0.24-2.sh
[sudo] password for maddox: 
sudo: ./AlsaUpgrade-1.0.24-2.sh: command not found


```

---

### Post by Yellow Pasque on 2011-02-18
You appear to lack very basic terminal skills or there's a slight typo with the commands and you're trolling me. Either way, I can't help you, but I'm sure someone can. :)

---

### Post by ethan1701 on 2011-02-18
> **amsama said:**
> ```
amsama@ubuntu:~/Downloads$ sudo ./AlsaUpgrade-1.0.24-1.sh -d
[sudo] password for amsama: 
sudo: ./AlsaUpgrade-1.0.24-1.sh: command not found

```:-|

I play music and got no sound. I guess i need tu update my ALSA, but i cant :(

```
amsama@ubuntu:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.

```

Did you download the script prior to trying to run it?
If not (or if you're not sure), please read through this post from the beginning and try again.

-Ethan

---

### Post by plexluthor on 2011-02-19
@amsama

Try making the script executable with something like "chmod +x AlsaUpgrade-1.0.24-2.sh" and then doing "sudo ./AlsaUpgrade-1.0.24-2.sh -d" and see if that works.

---

### Post by plexluthor on 2011-02-19
I found this page helpful, too, since I don't want to use my on-board HDMI:

[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

I had to add "load-module module-alsa-sink device=hw:1,7" to /etc/pulse/default.pa and the other stuff on that page.  That got my sound working, but killed my ability to control volume from my keyboard, and the system sound preference thing doesn't load.  But I can still do volume within an application, so this is a good-enough solution for now.

Thanks for the latest version of the upgrade script.

---

### Post by Ufoeke on 2011-02-22
> **xoppaw said:**
> i downloaded the script again, and here is what happens: 

```

maddox@xbmclive:~$ sudo ./AlsaUpgrade-1.0.24-2.sh
[sudo] password for maddox: 
sudo: ./AlsaUpgrade-1.0.24-2.sh: command not found


```

sudo chmod -c 775 AlsaUpgrade-1.0.24-2.sh

Worked for me

---

### Post by lkjoel on 2011-02-22
> **plexluthor said:**
> @amsama

Try making the script executable with something like "chmod +x AlsaUpgrade-1.0.24-2.sh" and then doing "sudo ./AlsaUpgrade-1.0.24-2.sh -d" and see if that works.
Rather:
```
sudo chmod +x AlsaUpgrade-1.0.24-2.sh
sudo ./AlsaUpgrade-1.0.24-2.sh

```
Just adding +x to your current user will not affect Sudo.

---

### Post by legend_gibby on 2011-02-23
right ok im new to ubuntu and a bit stupid lol

my mic aint working with skype but is working with sound recorder situated in the application at the top of the desk top!!!

What is the problem i have, ive been into skype and tried to sort things out in there.....nbo joy
been in to GNOME ALSA mixer.....no joy there
Been into the Alsamixer in terminal......still no joy!

can anyone plesea help me as im now totaly stuck!!!!

here is a list of stuff about my system!

james@james-AO751h:~$ uname -a
Linux james-AO751h 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux
james@james-AO751h:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
james@james-AO751h:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.23+dfsg-1ubuntu4                              ALSA driver configuration files
iF  alsa-driver-linuxant                           1.0.23.1-k2.6.31-17-generic-1                     ALSA driver enhanced for Conexant HDA modem support
ii  alsa-utils                                     1.0.23-2ubuntu3.4                                 Utilities for configuring and using ALSA
ii  bluez-alsa                                     4.69-0ubuntu2                                     Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                         ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.30-2                                         GStreamer plugin for ALSA
rc  libsdl1.2debian-alsa                           1.2.14-6ubuntu3                                   Simple DirectMedia Layer (with X11 and ALSA options)
ii  linux-alsa-driver-modules-2.6.35-25-generic    2.6.35-25.201102141252                            Ubuntu-supplied Linux modules for version 2.6.35-25-generic ALSA snapshots
james@james-AO751h:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC272X


Here is the spec!

Processor Speed
1.33 GHz
RAM
1 GB
Weight
3 lb
Screen Size
11.6 inches
Screen Size Type
widescreen
Graphics Card
Intel Graphics Media Accelerator 500
Storage Capacity (as Tested)
160 GB
Networking Options
802.11g
Processor Name
Intel Atom Z520

hope i can get help ASAP

---

### Post by svyatoy.ioan on 2011-02-25
this script really worked for me!!! big thanks!!! i have asus xonar stx sound card and after upgrade to ubuntu 10.10 it stopped work (drivers loaded, multimedia soft works, but no sound). i've tried many times to compile alsa 1.0.24 from sources, but after installation compiled modules didn't want to load beause of linker errors.

---

### Post by SebSmith on 2011-02-26
still not recognizing  my intel hda card. what else can i do?

---

### Post by patapra on 2011-02-26
just want to say thanks! i tried to upgrade to alsa 1.0.24 manually and completely busted my sound. tried reinstalling 1.0.23 from repositories to no avail.. tried to debug a 1.0.24 compilation error to no avail.. used your script and everything works again! i prolly have remnants of old alsa stuff somewhere, but all i care is that its working again! thanks

---

### Post by jda8818 on 2011-03-05
Thanks to soundcheck, Temujin (sp), and Lidex (from days gone by):

Thanks to you guys, new 10.04.2 32-bit image install and the latest Alsa-Upgrade-1.0.24-2 script worked perfectly, as well as adding the line to the the alsa.conf file, which in my case added sound to firefox via flash.

I guess upcoming kernel updates will overwrite this fix, but oh well ...

Many thanks again!

JA

---

### Post by Yellow Pasque on 2011-03-05
> I guess upcoming kernel updates will overwrite this fix, but oh well ...

Boot into the new kernel and run the script with -i again. After you reboot (or restart ALSA), all should work fine again.

---

### Post by lidex on 2011-03-06
> **SebSmith said:**
> still not recognizing  my intel hda card. what else can i do?

Start a new thread with alsa-info link included and PM me with the url.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by GrayFoxbh on 2011-03-08
Today for some obscure reason instead of going out in Brazilian's carnival I was at home trying to configure my Acer 3820t to work with Ubuntu 10.10. The sound was great but I've decided to upgrade and all I've done was messing the driver and the sound suddenly stop working.
So after 5hours of Google I've found this thread, ran the script and it worked perfectly. 
Thank you very much!!!!

---

### Post by deadman29 on 2011-03-10
I seem to be having difficulties with this alsa upgrade. I get an error when I begin the installation process " -i " and here's the error I come across :

" checking for new_panel in -lpanelw... no
configure: error: panelw library not found"

any help would be appreciated

---

### Post by Yellow Pasque on 2011-03-10
Did you have synaptic or some other package manager open when you ran -d part? panelw is part of the libncursesw5-dev, which should have been installed in the -d phase.

---

### Post by Atlantys on 2011-03-12
Hi Temüjin,

Thank you so much for this script, after running it with no errors I got the sound working properly through my headphones and I also got the function keys working (all of them not only for controlling sound volume)

BUT without the headphones in, the sound will only come through the subwoofer. I've got an MSI GT729 ([http://www.msi.com/product/nb/GT729.html#/?div=Overview](http://www.msi.com/product/nb/GT729.html#/?div=Overview)) with a 4.1 Dolby system and if I could get at least the stereo speakers working I'll be happy. 

I removed pulseaudio then reinstalled it, I added that line to alsa.conf and nothing works. I can't enable 4.1 anywhere. Or at least stereo through the front speakers not mono through the subwoofer.

Can you please help?

Linux Mint 10 Julia \n \l
2.6.35-22-generic-pae

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Mar 13 2011 for kernel 2.6.35-22-generic-pae (SMP).

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC1200
Codec: LSI ID 1040

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
07:00.1 Audio device: ATI Technologies Inc HD48x0 audio


Thank you!

---

### Post by tacit1 on 2011-03-13
When running the script on the first step with ```
sudo ./AlsaUpgrade-1.0.24-2.sh -d
```
I get a whole lot of these:

```
WARNING: The following packages cannot be authenticated!
  alsa-oss
E: There are problems and -y was used without --force-yes

```

```
Maverick 2.6.35-27-generic x86_64
```

Tried running with Sudo and as root.  No joy.

---

### Post by gdhamell on 2011-03-14
Thanks for this. I was having that issue with sound only playing from one application. I purged whatever alsa was on my system from the vanilla install, and reinstalled using this script. Viola I can run multiple programs and hear sound! There was most likely an easier way to go about this, but whatever! Haha.

---

### Post by soundcheck on 2011-03-21
Hi folks.

---

I'd like to thank Temüjin for taking this project on.

It's not that I became lazy:
I'm  busy  in tweaking and supporting the Squeezebox Touch community with my modification scripts (Touch Toolbox 2.0) to improve its sound quality. 
The Touch is running an embedded Linux, which I'm heavily tweaking. 

---

I just installed 2.6.38 and was surprised not to find Alsa 1.0.24  in there.

After updating my own old script I ran into the same problem as you guys:

"No sound" 

I thought , must have been a while since I played around with all this.


Good to find that thread and the solution over here. :D

I btw. removed Pulseaudio. Since then I feel much better. ;)


Cheers

---

### Post by soundcheck on 2011-03-21
Hi there.

Just to share a finding.

Just figured that my HDSP Mixer app (handles RME soundcards) wouldn't work with current alsa-tools 1.0.24.1

The issue has been fixed in the current alsa-tools git.

Howto:

git clone git://git.alsa-project.org/alsa-tools.git alsa-tools

just copy the content of ./alsa-tools over to /usr/src/Alsa-1.0.24/alsa-tools-1.0.24.1/

sudo cp -r ./alsa-tools/*  /usr/src/Alsa-1.0.24/alsa-tools-1.0.24.1/

and than run the upgradescript with option -t.



Cheers

---

### Post by soundcheck on 2011-03-21
..

---

### Post by johnnydotexe on 2011-03-23
Been having a problem getting audio/mic to work on my rig with mint10 on a USB flash drive, went that route so my internal HDD/XP install weren't/aren't harmed(specifically my MBR) .  It's my understanding that this script works on mint so I gave it a try.

1.  The install process went well from the looks of it, no errors or anything.

2.  The result of "cat /proc/asound/version" is...

```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Nov 24 2010 for kernel 2.6.35-22-generic-pae (SMP).

```

...which was the first sign that something wasn't right.  Pretty sure that needs to be .24?

3.  The result of "aplay" is nothing, nothing happens at all.  It did this before the script as well.

4.  None of the sound test commands work, I keep getting told that no $ command is found.

5.  No different results so far in regards to my sound/mic issue.

To clarify the problem and desired result...I'm trying to get the sound and mic jacks on the front panel of my case to be recognized by linux.  At this time neither seem to function at all.  As for the rear jacks, center/green works but mic doesn't.  I'm running an Asus Crossfire IV Formula board and using the integrated Xtreme-Fi sound, codec VT2020, which is supposed to be supported by Alsa.  Yes, all jacks on front and rear work on my XP install, and the peripheral being used isa Razr headset.  I use TS3 to test sound and mic, btw, as I have nothing else installed at this time and no media to play...I'm just running this install on an 8gb USB flash drive to try to get back in to linux and maybe actually make the full switch this time...but it's stupid problems like no sound that send me running right back to windows. :(

---

### Post by Silent Voice on 2011-03-24
hey there guys... well what can i say, i'm new at Linux running it for a few days (Ubuntu 10.10 x64)
when i was trying to update alsa to 1.0.24 though this script i continuously get this at compilation process:
.....Decompress Driver source v1.0.24-
Compile Driver........
cd: 18: can't cd to alsa-driver-1.0.24
configure: WARNING: unrecognized options: --with-cards
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... ./version: 1: 1.0.24.1: not found

my kernel is .28 <_<

any suggestions? ^^
thanks in advance
and sorry for my "good" english

---

### Post by Yellow Pasque on 2011-03-24
> **Silent Voice said:**
> hey there guys... well what can i say, i'm new at Linux running it for a few days (Ubuntu 10.10 x64)
when i was trying to update alsa to 1.0.24 though this script i continuously get this at compilation process:
.....Decompress Driver source v1.0.24-
Compile Driver........
cd: 18: can't cd to alsa-driver-1.0.24
configure: WARNING: unrecognized options: --with-cards
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... ./version: 1: 1.0.24.1: not found

my kernel is .28 <_<

any suggestions? ^^
thanks in advance
and sorry for my "good" english
It sounds like downloading failed. Try that again.

---

### Post by johnnydotexe on 2011-03-24
> **johnnydotexe said:**
> Been having a problem getting audio/mic to work on my rig with mint10 on a USB flash drive, went that route so my internal HDD/XP install weren't/aren't harmed(specifically my MBR) .  It's my understanding that this script works on mint so I gave it a try.

1.  The install process went well from the looks of it, no errors or anything.

2.  The result of "cat /proc/asound/version" is...

```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Nov 24 2010 for kernel 2.6.35-22-generic-pae (SMP).

```...which was the first sign that something wasn't right.  Pretty sure that needs to be .24?

3.  The result of "aplay" is nothing, nothing happens at all.  It did this before the script as well.

4.  None of the sound test commands work, I keep getting told that no $ command is found.

5.  No different results so far in regards to my sound/mic issue.

To clarify the problem and desired result...I'm trying to get the sound and mic jacks on the front panel of my case to be recognized by linux.  At this time neither seem to function at all.  As for the rear jacks, center/green works but mic doesn't.  I'm running an Asus Crossfire IV Formula board and using the integrated Xtreme-Fi sound, codec VT2020, which is supposed to be supported by Alsa.  Yes, all jacks on front and rear work on my XP install, and the peripheral being used isa Razr headset.  I use TS3 to test sound and mic, btw, as I have nothing else installed at this time and no media to play...I'm just running this install on an 8gb USB flash drive to try to get back in to linux and maybe actually make the full switch this time...but it's stupid problems like no sound that send me running right back to windows. :(

Any ideas?  I also have a thread going over on the Mint 10 forum and no one has offered a solution yet.  ALSA supports my hardware, so this issue is probably just some simple/stupid setting somewhere or a missing file or something.

---

### Post by Silent Voice on 2011-03-24
> **Temüjin said:**
> It sounds like downloading failed. Try that again.


no, i'm sure its not failed. besides, i tried like 6 times and always get this damn error <_>

well probably my fault (nah, i'm sure its my fault lol). as a newbie i'm doing terrible things around there with my system, so its might be a side effect...
anyway, i just made a pure reinstall or system, updating kernel atm.. will let ya know when i'll try updating alsa again

---

### Post by lidex on 2011-03-24
@johnnydotexe
What about ```
aplay -l
```
Anyway, try this:
```
echo "options snd-hda-intel model=6stack-digout " | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by johnnydotexe on 2011-03-24
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT2020 Digital [VT2020 Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

If that second command inputs the line "options snd-hda-intel model=6stack-digout" at the end of the alsa-base.conf file...I've already done that several days ago, after having it set to "auto" as well.  No matter what I try, I can only get audio from the rear green/center port(didn't try the other channel ports).  Nothing from the front audio port, and both the front and rear mic ports don't work.

---

### Post by Silent Voice on 2011-03-24
yeaah sorry 'twas all my fault...
everything was installed without a single problem, the only one persone to blame is me lol
sorry for my previous posts ^^

---

### Post by Yellow Pasque on 2011-03-24
> **soundcheck said:**
> I'd like to thank Temüjin for taking this project on. 

You're a much better BASH scripter than I am and you wrote the guts of the script. Thanks for that. I can't speak for everyone, but I understand you using your talents elsewhere on your own interests/projects.

---

### Post by Zuba on 2011-03-30
Worked for me, and it fixed VLC errors :) Easy to use and quick way to update alsa, thanks.

---

### Post by ironear on 2011-04-04
Thankyou for you guys very very much.I has this problem very long times ago but can't resolve it.

Tag: Asus, A42F, headphone, audio, problem,  alsa, no sound

---

### Post by GTS300 on 2011-04-14
[FONT=Calibri][SIZE=3]No Audio over HDMI[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I have two Acer 3700 NetTop’s, one I have had for 6 months and is working fine but I have just purchased a new 3700 and installed the same software and updates (Ubuntu 9.10 and Nvidia 260.19.29 video drivers and installer Alsa 1.0.24.2). [/SIZE][/FONT][FONT=Calibri][SIZE=3]However I can’t get the audio to work over HDMI on the new 3700. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]When I run alsamixer on the new 3700, it displays the mixer controls but there is no PCM volume control however there is on the old unit so [/SIZE][SIZE=3]I figure this is where the problem is but I have not been able to work out how to fix it.[/SIZE][/FONT]
[FONT=Calibri][COLOR=#181818][FONT=Calibri]The following links are the ALSA Information Script results for each 3700:[/FONT][/COLOR][FONT=Calibri][/FONT][/FONT]
[SIZE=3][FONT=Calibri]Not working Acer 3700                  [/FONT][/SIZE][[FONT=Calibri][SIZE=3]http://pastebin.com/2eqQdES2[/SIZE][/FONT]]("http://pastebin.com/2eqQdES2")
[SIZE=3][FONT=Calibri]Working Acer 3700                        [/FONT][/SIZE][[FONT=Calibri][SIZE=3]http://pastebin.com/VAyPQhcA[/SIZE][/FONT]]("http://pastebin.com/VAyPQhcA")

---

### Post by lean-mini on 2011-04-14
Muchas gracias temüjin!! me arregló el problema!

---

### Post by TiberiusT on 2011-04-16
@Temujin

M8...I am gonna build a statue of yu in my front garden...flashing neon...the full damn works. :razz::guitar:
Having been happily using 10.10 I reinstalled 10.04 x32 for overall home system compatibility, and no sound from Intel-hda ALC 887. Really, I've spent abt 10hours on it and then wham! your script in the first post sorted it.

Cheers and tks very much for your efforts.

May I ask someone a n00b question? I followed advice and am using the LTS version. I assumed that this automatically installs updates for all devices to ensure upto date compatibility etc etc. But it didn't, I think it was using Alsa 019 or something, which is very old. What's the point of using LTS then? Since my sound worked fine in Maverick...

T


```

############
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Apr 16 10:59:19 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      G31M-ES2L
Product Version:    


!!Kernel Information
!!------------------

Kernel release:    2.6.32-30-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff8000 irq 28


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
    Subsystem: 1458:a002


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=3stack
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : 3stack,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC887-VD
Address: 2
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0887
Subsystem Id: 0x1458a002
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC887-VD Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC887-VD Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC887-VD Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x2e 0x2e]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="ALC887-VD Digital", type="SPDIF", device=1
  Converter: stream=4, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="CD Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="CD Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x19 0x19] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411110f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x2: EAPD
  Pin Default 0x01014410: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19c40: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c50: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181344f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001373e: IN OUT HP EAPD Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x593301f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005c603: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = UNKNOWN
    DefAssociation = 0x0, Sequence = 0x3
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x014b6130: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=24
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  7 Apr 16 13:49 /dev/snd/controlC0
crw-rw----  1 root audio 116,  6 Apr 16 13:49 /dev/snd/hwC0D2
crw-rw----  1 root audio 116,  5 Apr 16 13:51 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  4 Apr 16 13:51 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  3 Apr 16 13:49 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  2 Apr 16 13:49 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  1 Apr 16 13:49 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Apr 16 13:49 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr 16 13:49 .
drwxr-xr-x 3 root root 220 Apr 16 13:49 ..
lrwxrwxrwx 1 root root  12 Apr 16 13:49 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfdff8000 irq 28'
  Mixer name    : 'Realtek ALC887-VD'
  Components    : 'HDA:10ec0887,1458a002,00100302'
  Controls      : 34
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 46 [100%] [30.00dB] [on]
  Front Right: Capture 46 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 16 [35%] [0.00dB] [off]
  Front Right: Capture 16 [35%] [0.00dB] [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        iface MIXER
        name 'Front Playback Volume'
        value.0 64
        value.1 64
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.2 {
        iface MIXER
        name 'Front Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Surround Playback Volume'
        value.0 64
        value.1 64
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.4 {
        iface MIXER
        name 'Surround Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Center Playback Volume'
        value 64
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 0
        }
    }
    control.6 {
        iface MIXER
        name 'LFE Playback Volume'
        value 64
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 0
        }
    }
    control.7 {
        iface MIXER
        name 'Center Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.8 {
        iface MIXER
        name 'LFE Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.9 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.10 {
        iface MIXER
        name 'CD Playback Volume'
        value.0 25
        value.1 25
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 300
            dbvalue.1 300
        }
    }
    control.11 {
        iface MIXER
        name 'CD Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.12 {
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.13 {
        iface MIXER
        name 'Line Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.14 {
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.15 {
        iface MIXER
        name 'Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.16 {
        iface MIXER
        name 'Front Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.17 {
        iface MIXER
        name 'Front Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.18 {
        iface MIXER
        name 'Channel Mode'
        value '2ch'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 '2ch'
            item.1 '6ch'
        }
    }
    control.19 {
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.20 {
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.21 {
        iface MIXER
        name 'Capture Volume'
        value.0 46
        value.1 46
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 46'
            dbmin -1600
            dbmax 3000
            dbvalue.0 3000
            dbvalue.1 3000
        }
    }
    control.22 {
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 16
        value.1 16
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 46'
            dbmin -1600
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.23 {
        iface MIXER
        name 'Input Source'
        value Mic
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic
            item.1 'Front Mic'
            item.2 Line
            item.3 CD
        }
    }
    control.24 {
        iface MIXER
        name 'Input Source'
        index 1
        value Mic
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic
            item.1 'Front Mic'
            item.2 Line
            item.3 CD
        }
    }
    control.25 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.26 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.27 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.28 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.29 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.30 {
        iface MIXER
        name 'IEC958 Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.31 {
        iface MIXER
        name 'IEC958 Capture Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.32 {
        iface MIXER
        name 'Master Playback Volume'
        value 64
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 0
        }
    }
    control.33 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.34 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
binfmt_misc
snd_seq_device
snd
soundcore
snd_page_alloc
nvidia
ppdev
parport_pc
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
atl1c
intel_agp
agpgart
lp
parport
usbhid
hid
floppy


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D2/init_pin_configs:
0x11 0x411110f0
0x12 0x411111f0
0x14 0x01014410
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x01a19c40
0x19 0x02a19c50
0x1a 0x0181344f
0x1b 0x02214c20
0x1c 0x593301f0
0x1d 0x4005c603
0x1e 0x014b6130
0x1f 0x411111f0

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   12.116080]   groups: 1 0
[   12.309915] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.309994]   alloc irq_desc for 28 on node -1
[   12.309997]   alloc kstat_irqs on node -1
[   12.310008] HDA Intel 0000:00:1b.0: irq 28 for MSI/MSI-X
[   12.310193] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.818736] CPU0 attaching NULL sched-domain.


```

---

### Post by alfabravoteam on 2011-04-17
Testing Natty beta2 and after a upgrade, the sound was gone... used your script and sound came back. Somehow, there's no way to control volume from the applet or the keyboard keys (i'm on a HP pavilion, so it comes with dedicated "touch keys" for sound).

The sound came back and that's good enough, thanks!


PS. How come Natty does not ships ALSA .24 yet?? :-/

EDIT: Amarok playback does not work. Guess it's related to gstreamer or something... sheesh

---

### Post by lidex on 2011-04-17
> **GTS300 said:**
> [FONT=Calibri][SIZE=3]No Audio over HDMI[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I have two Acer 3700 NetTop’s, one I have had for 6 months and is working fine but I have just purchased a new 3700 and installed the same software and updates (Ubuntu 9.10 and Nvidia 260.19.29 video drivers and installer Alsa 1.0.24.2). [/SIZE][/FONT][FONT=Calibri][SIZE=3]However I can’t get the audio to work over HDMI on the new 3700. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]When I run alsamixer on the new 3700, it displays the mixer controls but there is no PCM volume control however there is on the old unit so [/SIZE][SIZE=3]I figure this is where the problem is but I have not been able to work out how to fix it.[/SIZE][/FONT]
[FONT=Calibri][COLOR=#181818][FONT=Calibri]The following links are the ALSA Information Script results for each 3700:[/FONT][/COLOR][FONT=Calibri][/FONT][/FONT]
[SIZE=3][FONT=Calibri]Not working Acer 3700                  [/FONT][/SIZE][[FONT=Calibri][SIZE=3]http://pastebin.com/2eqQdES2[/SIZE][/FONT]]("http://pastebin.com/2eqQdES2")
[SIZE=3][FONT=Calibri]Working Acer 3700                        [/FONT][/SIZE][[FONT=Calibri][SIZE=3]http://pastebin.com/VAyPQhcA[/SIZE][/FONT]]("http://pastebin.com/VAyPQhcA")

You're missing this from alsa-base.conf:
```
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
```

Edit thusly:```

gksu gedit /etc/modprobe.d/alsa-base.conf
```
Save. Close. Reboot.

---

### Post by Yellow Pasque on 2011-04-17
> M8...I am gonna build a statue of you in my front garden...flashing neon...the full damn works.
Neon seems tacky. I would prefer something classic like marble. Get quarrying now!

> PS. How come Natty does not ships ALSA .24 yet?? :-/
EDIT: Amarok playback does not work. Guess it's related to gstreamer or something... sheesh
Natty does use 1.0.24. What phonon backend are you using? (look in systemsettings)
FWIW, I struggle with Phonon at times too.

---

### Post by cgtobi on 2011-04-23
Hi all, 
I keep having problems getting alsa to work properly on my zbox ID11 running Ubuntu 10.04.2.
I removed Pulse and upgraded alsa with this script. It workes for some time but after a bit of usage sometimes up to an hour the sound suddenly stops and I haven't found away to get it working again. Sometimes it suddenly works again (after a few reboots and trying to reinstall alsa etc) but then after a few minutes the sound disappears again. So I call you for help as I am really running out of ideas before I completely reinstall the whole thing from scratch.

Here is the output from alsa-info.sh
```

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Apr 23 22:36:55 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"


!!DMI Information
!!---------------

Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.
Product Version:   To Be Filled By O.E.M.


!!Kernel Information
!!------------------

Kernel release:    2.6.32-29-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcf7c000 irq 18


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
03:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 19da:a140
--
03:00.1 0403: 10de:0be3 (rev a1)
	Subsystem: 174b:3100


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: enable_msi=0 probe_mask=0xffff,0xfff2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : 65535,65522,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_hda_intel
	bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : 65535,65522,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC888
Address: 2
Function Id: 0x1
Vendor Id: 0x10ec0888
Subsystem Id: 0x19daa140
Revision Id: 0x100001
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC888 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC888 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC888 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x18 0x18]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19830: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40020601: [N/A] Line Out at Ext N/A
    Conn = 1/4, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01451120: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
Codec: Nvidia GT21x HDMI
Address: 1
Function Id: 0x1
Vendor Id: 0x10de000b
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Apr 23 18:54 /dev/snd/controlC0
crw-rw----  1 root audio 116, 32 Apr 23 18:54 /dev/snd/controlC1
crw-rw----  1 root audio 116,  6 Apr 23 18:54 /dev/snd/hwC0D2
crw-rw----  1 root audio 116, 37 Apr 23 18:54 /dev/snd/hwC1D1
crw-rw----  1 root audio 116, 24 Apr 23 18:54 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Apr 23 18:54 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 17 Apr 23 18:54 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116, 51 Apr 23 18:54 /dev/snd/pcmC1D3p
crw-rw----  1 root audio 116,  1 Apr 23 18:54 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Apr 23 18:54 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Apr 23 18:54 .
drwxr-xr-x 3 root root 260 Apr 23 18:54 ..
lrwxrwxrwx 1 root root  12 Apr 23 18:54 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 Apr 23 18:54 pci-0000:03:00.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfe9fc000 irq 16'
  Mixer name	: 'Realtek ALC888'
  Components	: 'HDA:10ec0888,19daa140,00100001'
  Controls      : 15
  Simple ctrls  : 8
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 30 [97%] [-1.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [on]
  Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]

!!-------Mixer controls for card 1 [NVidia]

Card hw:1 'NVidia'/'HDA NVidia at 0xfcf7c000 irq 18'
  Mixer name	: 'Nvidia GT21x HDMI'
  Components	: 'HDA:10de000b,10de0101,00100100'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 25
		value.1 25
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mic Boost'
		value.0 0
		value.1 0
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 31
		value.1 31
	}
	control.8 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.9 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.10 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 30
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.15 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
	}
}
state.NVidia {
	control.1 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.2 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.3 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
dm_crypt
snd_hda_codec_nvhdmi
snd_hda_codec_realtek
binfmt_misc
ppdev
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
arc4
snd_seq
snd_timer
snd_seq_device
ath9k
snd
mac80211
ath
cfg80211
soundcore
coretemp
led_class
nvidia
vga16fb
vgastate
psmouse
serio_raw
snd_page_alloc
lp
parport
dm_raid45
xor
usbhid
hid
fbcon
tileblit
font
bitblit
softcursor
uvesafb
intel_agp
usb_storage
r8169
mii
agpgart
ramzswap
xvmalloc
lzo_decompress
lzo_compress


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D2/init_pin_configs:
0x14 0x01014010
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x01a19830
0x19 0x411111f0
0x1a 0x411111f0
0x1b 0x411111f0
0x1c 0x411111f0
0x1d 0x40020601
0x1e 0x01451120
0x1f 0x411111f0

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:

/sys/class/sound/hwC1D1/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D1/driver_pin_configs:

/sys/class/sound/hwC1D1/user_pin_configs:

/sys/class/sound/hwC1D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   14.444174] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xfa7e0000, irq=17
[   15.111941] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.111954] hda_intel: codec_mask forced to 0xff
[   15.112035] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.610943] ppdev: user-space parallel port driver
--
[   16.554428] CPU3 attaching NULL sched-domain.
[   18.156008] ALSA hda_intel.c:712: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   18.788684] CPU0 attaching sched-domain:
--
[   18.788949]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   19.160022] ALSA hda_intel.c:1420: Codec #0 probe error; disabling it...
[   20.196013] ALSA hda_intel.c:1420: Codec #1 probe error; disabling it...
[   21.082150] r8169: eth0: link up
[   21.082162] r8169: eth0: link up
[   21.232512] ALSA hda_intel.c:1420: Codec #3 probe error; disabling it...
[   21.329679] hda_codec: ALC888: BIOS auto-probing.
[   21.330369] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   21.337631] HDA Intel 0000:03:00.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   21.337644] hda_intel: codec_mask forced to 0xf2
[   21.337727] HDA Intel 0000:03:00.1: setting latency timer to 64
[   23.531662] r8169: eth0: link up
[   23.707410] r8169: eth0: link up
[   24.392520] ALSA hda_intel.c:712: azx_get_response timeout, switching to polling mode: last cmd=0x400f0000
[   25.401521] ALSA hda_intel.c:1420: Codec #4 probe error; disabling it...
[   25.761747] __ratelimit: 15 callbacks suppressed
[   25.761757] type=1503 audit(1303577687.713:17):  operation="open" pid=1473 parent=1458 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[   26.440025] ALSA hda_intel.c:1420: Codec #5 probe error; disabling it...
[   27.481521] ALSA hda_intel.c:1420: Codec #6 probe error; disabling it...
[   28.520022] ALSA hda_intel.c:1420: Codec #7 probe error; disabling it...
[   29.404067] ioremap error for 0x0-0x2000, requested 0x10, got 0x0
[   36.337254] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   36.361216] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   37.136029] HDMI: detected monitor SAMSUNG
[   37.136033]      at connection type HDMI
[   37.136040] HDMI: available speakers: FL/FR
[   37.136048] ------------[ cut here ]------------
--
[   37.136067] Hardware name: To Be Filled By O.E.M.
[   37.136071] Modules linked in: dm_crypt snd_hda_codec_nvhdmi snd_hda_codec_realtek binfmt_misc ppdev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event arc4 snd_seq snd_timer snd_seq_device ath9k snd mac80211 ath cfg80211 soundcore coretemp led_class nvidia(P) vga16fb vgastate psmouse serio_raw snd_page_alloc lp parport dm_raid45 xor usbhid hid fbcon tileblit font bitblit softcursor uvesafb intel_agp usb_storage r8169 mii agpgart ramzswap xvmalloc lzo_decompress lzo_compress
[   37.136160] Pid: 1435, comm: hd-audio1 Tainted: P           2.6.32-29-generic #58-Ubuntu
--
[   37.136214]  [<c035456a>] snprintf 0x1a/0x20
[   37.136231]  [<faa0c64d>] snd_print_pcm_bits 0x5d/0x80 [snd_hda_codec]
[   37.136247]  [<faa157f7>] hdmi_show_short_audio_desc 0xf7/0x100 [snd_hda_codec]
[   37.136256]  [<c035456a>] ? snprintf 0x1a/0x20
[   37.136271]  [<faa1585f>] snd_hdmi_show_eld 0x5f/0xa0 [snd_hda_codec]
[   37.136286]  [<faa1593f>] ? snd_hdmi_get_eld 0x6f/0x2d0 [snd_hda_codec]
[   37.136301]  [<faa15b6c>] ? snd_hdmi_get_eld 0x29c/0x2d0 [snd_hda_codec]
[   37.136311]  [<fab95706>] hdmi_unsol_event 0x106/0x110 [snd_hda_codec_nvhdmi]
[   37.136321]  [<c013fc23>] ? finish_task_switch 0x43/0xc0
[   37.136334]  [<faa0c106>] process_unsol_events 0x56/0x70 [snd_hda_codec]
[   37.136344]  [<c0163c2e>] run_workqueue 0x8e/0x150
[   37.136357]  [<faa0c0b0>] ? process_unsol_events 0x0/0x70 [snd_hda_codec]
[   37.136366]  [<c0163d74>] worker_thread 0x84/0xe0
--
[   37.136408] ---[ end trace 6d8046dff2892005 ]---
[   37.136414] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
[   43.012789] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   43.036630] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   43.828045] HDMI: detected monitor SAMSUNG
[   43.828050]      at connection type HDMI
[   43.828056] HDMI: available speakers: FL/FR
[   43.828066] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
[   44.131770] CPU0 attaching NULL sched-domain.

```

If you need more info please let me know.

Thanks heaps in advance guys.

Cheers,
cgTobi

---

### Post by Yellow Pasque on 2011-04-23
The upgrade didn't work. You're still running ALSA 1.0.23

---

### Post by cgtobi on 2011-04-24
Ah, you're right. Well, it actually worked, but as the sound still didn't work I downgraded to 1.0.23. Let me upgrade again and post a new alsa-info output.

```

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Apr 24 08:28:44 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"


!!DMI Information
!!---------------

Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.
Product Version:   To Be Filled By O.E.M.


!!Kernel Information
!!------------------

Kernel release:    2.6.32-29-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcf7c000 irq 18


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
03:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 19da:a140
--
03:00.1 0403: 10de:0be3 (rev a1)
	Subsystem: 174b:3100


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: enable_msi=0 probe_mask=0xffff,0xfff2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : 65535,65522,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_hda_intel
	bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : 65535,65522,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC888
Address: 2
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0888
Subsystem Id: 0x19daa140
Revision Id: 0x100001
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC888 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC888 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC888 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="PCM Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="PCM Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1e 0x1e]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19830: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40020601: [N/A] Line Out at Ext N/A
    Conn = 1/4, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01451120: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
Codec: Nvidia GPU 0b HDMI/DP
Address: 1
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000b
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  6 Apr 24 10:24 /dev/snd/controlC0
crw-rw----  1 root audio 116,  9 Apr 24 10:25 /dev/snd/controlC1
crw-rw----  1 root audio 116,  5 Apr 24 10:24 /dev/snd/hwC0D2
crw-rw----  1 root audio 116,  8 Apr 24 10:25 /dev/snd/hwC1D1
crw-rw----  1 root audio 116,  4 Apr 24 10:24 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  3 Apr 24 10:24 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  2 Apr 24 10:24 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  7 Apr 24 10:25 /dev/snd/pcmC1D3p
crw-rw----  1 root audio 116,  1 Apr 24 10:24 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Apr 24 10:24 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Apr 24 10:25 .
drwxr-xr-x 3 root root 260 Apr 24 10:25 ..
lrwxrwxrwx 1 root root  12 Apr 24 10:24 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 Apr 24 10:25 pci-0000:03:00.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfe9fc000 irq 16'
  Mixer name	: 'Realtek ALC888'
  Components	: 'HDA:10ec0888,19daa140,00100001'
  Controls      : 16
  Simple ctrls  : 8
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 30 [97%] [-1.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]

!!-------Mixer controls for card 1 [NVidia]

Card hw:1 'NVidia'/'HDA NVidia at 0xfcf7c000 irq 18'
  Mixer name	: 'Nvidia GPU 0b HDMI/DP'
  Components	: 'HDA:10de000b,10de0101,00100100'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.2 {
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.4 {
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.6 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.7 {
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.8 {
		iface MIXER
		name 'Capture Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -1650
			dbmax 3000
			dbvalue.0 3000
			dbvalue.1 3000
		}
	}
	control.9 {
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -1650
			dbmax 3000
			dbvalue.0 -1650
			dbvalue.1 -1650
		}
	}
	control.10 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.11 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.12 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.13 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.15 {
		iface MIXER
		name 'Master Playback Volume'
		value 30
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 -150
		}
	}
	control.16 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
state.NVidia {
	control.1 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
dm_crypt
snd_hda_codec_hdmi
snd_hda_codec_realtek
binfmt_misc
ppdev
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
arc4
snd_seq_device
snd
ath9k
mac80211
ath
soundcore
cfg80211
snd_page_alloc
led_class
coretemp
nvidia
vga16fb
vgastate
psmouse
serio_raw
lp
parport
dm_raid45
xor
usbhid
hid
fbcon
tileblit
font
bitblit
softcursor
uvesafb
intel_agp
usb_storage
agpgart
r8169
mii
ramzswap
xvmalloc
lzo_decompress
lzo_compress


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D2/init_pin_configs:
0x14 0x01014010
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x01a19830
0x19 0x411111f0
0x1a 0x411111f0
0x1b 0x411111f0
0x1c 0x411111f0
0x1d 0x40020601
0x1e 0x01451120
0x1f 0x411111f0

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:

/sys/class/sound/hwC1D1/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D1/driver_pin_configs:

/sys/class/sound/hwC1D1/user_pin_configs:

/sys/class/sound/hwC1D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   14.531581] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xfa7a0000, irq=17
[   15.251214] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.251228] hda_intel: codec_mask forced to 0xff
[   15.251300] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.983933] ppdev: user-space parallel port driver
--
[   16.868251] CPU3 attaching NULL sched-domain.
[   18.293014] ALSA hda_intel.c:717: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   19.297012] ALSA hda_intel.c:1432: Codec #0 probe error; disabling it...
[   19.328133] CPU0 attaching sched-domain:
--
[   19.328341]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   20.333513] ALSA hda_intel.c:1432: Codec #1 probe error; disabling it...
[   21.368011] ALSA hda_intel.c:1432: Codec #3 probe error; disabling it...
[   21.485682] hda_codec: ALC888: BIOS auto-probing.
[   21.489401] HDA Intel 0000:03:00.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   21.489411] hda_intel: codec_mask forced to 0xf2
[   21.489477] HDA Intel 0000:03:00.1: setting latency timer to 64
[   22.087400] r8169: eth0: link up
--
[   24.487720] r8169: eth0: link up
[   24.537530] ALSA hda_intel.c:717: azx_get_response timeout, switching to polling mode: last cmd=0x400f0000
[   24.637208] r8169: eth0: link up
[   25.544024] ALSA hda_intel.c:1432: Codec #4 probe error; disabling it...
[   26.585521] ALSA hda_intel.c:1432: Codec #5 probe error; disabling it...
[   26.684808] __ratelimit: 15 callbacks suppressed
[   26.684819] type=1503 audit(1303633504.633:17):  operation="open" pid=1595 parent=1580 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[   27.620026] ALSA hda_intel.c:1432: Codec #6 probe error; disabling it...
[   28.661521] ALSA hda_intel.c:1432: Codec #7 probe error; disabling it...
[   29.584641] ioremap error for 0x0-0x2000, requested 0x10, got 0x0
[   31.578000] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   31.601902] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   32.388027] HDMI: detected monitor SAMSUNG
[   32.388031]      at connection type HDMI
[   32.388038] HDMI: available speakers: FL/FR
[   32.388047] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24
[   33.180525] HDMI: detected monitor SAMSUNG
[   33.180530]      at connection type HDMI
[   33.180537] HDMI: available speakers: FL/FR
[   33.180546] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24
[   38.445602] CPU0 attaching NULL sched-domain.
--
[   38.473317]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   39.705190] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   39.729130] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   40.573024] HDMI: detected monitor SAMSUNG
[   40.573028]      at connection type HDMI
[   40.573035] HDMI: available speakers: FL/FR
[   40.573045] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24
[   41.356032] HDMI: detected monitor SAMSUNG
[   41.356038]      at connection type HDMI
[   41.356044] HDMI: available speakers: FL/FR
[   41.356054] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24


```

---

### Post by onering on 2011-04-24
I'm using Ubuntu 10.04LTS 64bit and Asus Xonar DS sound card.  Upon initial installation of Ubuntu the sound card did not work.  After using this script the sound card now works great!

Thanks Temüjin for this great script!!!

:D

---

### Post by lidex on 2011-04-24
@cgtobi
The upgrade worked and your configuration issues remaining are beyond the scope of this thread. I would suggest starting a new thread and posting all relevant details there. You are using hdmi, correct? Is it onboard or graphics card? Have you tried disabling onboard audio?

---

### Post by cgtobi on 2011-04-25
@lidex: indeed the upgrade worked. and funnily enough audio works perfectly well since. And I tried upgrading and downgrading probably about 10 times. And I can't tell for sure what I did differently this time. I am puzzled. But to answer your questions, I am actually not using HDMI but optical out. This is a ZBOX ID-11 (Atom with ION2). If problems should occur again I'll open a new thread. But thanks for your attention.

Cheers,
cgTobi

---

### Post by coloradocut on 2011-04-26
Thanks!  This cured my Maverick laptop.

Regards

---

### Post by felipemartim on 2011-04-30
Thanks Temüjin!
It worked perfectly on my recently installed Natty that came with 1.0.23.

---

### Post by nightfever on 2011-05-03
It works - I get sound, but there's an issue: the sample rate is set to 48khz (e-mu 1212m card) and the playback is too fast. How do I change it?

---

### Post by 98174 on 2011-05-16
Thanks for this fix!
Finally got my sound back that disappeared after upgrade to 11.04 and me tinkering around a bit too much!

One request though: I have never managed to get sound to play through earbuds properly, it'll continue playing through the speakers for some odd reason.  I used to get around this by using the linuxANT package of ALSA, but they haven't supported it past 2.6.31, and as 11.04 is built on top of 2.6.38, this is frustraing.

Ideas?

---

### Post by CardexDave on 2011-05-23
Thank you!
I had messed up my system trying to install driver from Realtek website, and your script fixed my problems!
I'm running Ubuntu 11.04 Natty, kernel 2.6.38-8.
Great work!

---

### Post by sag0th on 2011-05-25
Hi
When trying the build part of the script(-c) I'm getting the following error:
```

/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libasound_module_pcm_a52.la] Error 1
make[2]: Leaving directory `/opt/Alsa-1.0.24/alsa-plugins-1.0.24/a52'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/Alsa-1.0.24/alsa-plugins-1.0.24'
make: *** [all] Error 2
```

Can someone PLEASE tell me what to do?
I tried:
**1)** edit the script with
```
PACKAGE=1.0.24

[i][color=red]# Make the script look for libav* in /usr/lib first:
PKG_CONFIG_PATH=/usr/lib/pkgconfig
export PKG_CONFIG_PATH[/color][/i]

setpack () {
DRIVER=alsa-driver-1.0.23
```

**2)** Build with CFLAGS=-fPIC;export CFLAGS

...but still...
I'm using ubuntu 9.10 64bit
Someone pls help! I'm freaking out...

// I build/installed alsa driver/utils/lib 1.0.23 but since then I don't have sound on flash and skype BUT I'm *able* to play mp3,movies,record sounds... only flash and skype. And that's the reason I tried this script

---

### Post by Yellow Pasque on 2011-05-27
@sag0th: if you don't have sound in flash and skype (and other apps that use alsa output), you probably need this: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

I'm not sure about the compile error at the moment.

---

### Post by sag0th on 2011-05-27
Temüjin, you've made my day! The flash is now with sound :D
My /etc/asound.conf was empty though...

...wow I can believe all my sounds are finally working! :D

---

### Post by Emanuele_Z on 2011-05-30
Hi,

apparently in Natty we still use 1.0.23.

Cheers,

Ps. Perhaps you guys have a hint for an issue I'm experiencing here: [http://ubuntuforums.org/showthread.php?p=10881251](http://ubuntuforums.org/showthread.php?p=10881251)

---

### Post by sag0th on 2011-05-30
@Emanuele_Z: Have you actually tried the upgrade script?

---

### Post by Emanuele_Z on 2011-05-30
> **sag0th said:**
> @Emanuele_Z: Have you actually tried the upgrade script?

I'd rather not update the default version in 11.04.
Anyway, managed to fix it with a sort of *hack* (I don't think modern distros should rely on this).

Here the answer: [http://ubuntuforums.org/showthread.php?p=10882342](http://ubuntuforums.org/showthread.php?p=10882342)

Cheers,
Ema

---

### Post by Soyud on 2011-06-08
Hi, I just write to say thank you.

The script has worked perfectly with Kubuntu Natty 11.04.

After 2 weeks of intense search trying to find a solution for an HP Pavilion Dv6, this finally solved the problem of detection of two sound cards.

Btw, works better uninstalling pulseaudio here.

Thank you very much again.

---

### Post by nychng on 2011-06-21
Hi there.. I was at Step 6 of the process ```
sudo ./AlsaUpgrade-1.0.24-2.sh -c 
```when it terminated with this error


```
checking for ALSA... configure: error: Package requirements (alsa >= 1.0.11) were not met:

No package 'alsa' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALSA_CFLAGS
and ALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


***************************************************************************
*  alsa-plugins-1.0.24 configure failed
***************************************************************************
```

Before this, I followed the advice of another thread and went to the Realtek website and downloaded the drivers to install much like this guy [http://ubuntuforums.org/showthread.php?t=1750697]("http://ubuntuforums.org/showthread.php?t=1750697"). 

Was hoping your script could solve my problem but ran into the error above. Please advise and thanks for your time!

---

### Post by nychng on 2011-06-21
> **nychng said:**
> Hi there.. I was at Step 6 of the process ```
sudo ./AlsaUpgrade-1.0.24-2.sh -c 
```when it terminated with this error


```
checking for ALSA... configure: error: Package requirements (alsa >= 1.0.11) were not met:

No package 'alsa' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALSA_CFLAGS
and ALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


***************************************************************************
*  alsa-plugins-1.0.24 configure failed
***************************************************************************
```

Before this, I followed the advice of another thread and went to the Realtek website and downloaded the drivers to install much like this guy [http://ubuntuforums.org/showthread.php?t=1750697]("http://ubuntuforums.org/showthread.php?t=1750697"). 

Was hoping your script could solve my problem but ran into the error above. Please advise and thanks for your time!

Upon further research, I was about to solve this through one of the following packages (Im not sure which one did the trick)

sudo apt-get install alsa-source libasound2-dev lib32asound-dev

---

### Post by duindain on 2011-06-24
Hi I've run this script with slight modification twice first time default settings this installed everything though the last step may have failed and it did not install the drivers for my on-board sound
> CARDS="all"
2nd time with the commented line for driver all set to hda-intel and this behaved the same after install> CARDS="usb-audio,hda-intel,hdsp,hrtimer,rtctimer"
I'm trying to get the intel corp 5 series/3400 series chipset hi def audio v 6 to work
  I'vetried livecd 10.04 lts and it worked straight away with no config so its not a hardware issue and the sound can work in Linux
Ive tried tons of fixes by people on random forums to get this working and no luck whatsever so far this script seems the most promising though

I had to change the ftp addresses because i cant seem to connect to them
So i added a Mirror variable
```

PACKAGE=1.0.24

setpack () {
DRIVER=alsa-driver-1.0.24
FIRMWARE=alsa-firmware-1.0.24.1
LIB=alsa-lib-1.0.24.1
PLUGINS=alsa-plugins-1.0.24
UTILS=alsa-utils-1.0.24.2
TOOLS=alsa-tools-1.0.24.1
OSS=alsa-oss-1.0.17
}
MIRROR="http://alsa.cybermirror.org"

```and changed the download code to the following
```

header "Downloading and extracting ALSA packages..."
wget $MIRROR/driver/$DRIVER.tar.bz2 && tar -xjf $DRIVER.tar.bz2 
wget $MIRROR/firmware/$FIRMWARE.tar.bz2 && tar -xjf $FIRMWARE.tar.bz2 
wget $MIRROR/lib/$LIB.tar.bz2 && tar -xjf $LIB.tar.bz2 
wget $MIRROR/plugins/$PLUGINS.tar.bz2 && tar -xvf $PLUGINS.tar.bz2 
wget $MIRROR/utils/$UTILS.tar.bz2 && tar -xjf $UTILS.tar.bz2 
wget $MIRROR/tools/$TOOLS.tar.bz2 && tar -xjf $TOOLS.tar.bz2 
wget $MIRROR/oss-lib/$OSS.tar.bz2 && tar -xvf $OSS.tar.bz2 

```This connects fine to one of the http mirrors listed on the alsa site I checked the versions match and it downloads fine for me

These are my versions of debugging info i see other ppl have posted in this thread hopefully someone will be able to spot the issue
sudo dmidecode -s system-product-name
P55A-UD3R 
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Jun 24 2011 for kernel 2.6.38-10-generic (SMP).

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.24+dfsg-0ubuntu1                              ALSA driver configuration files
ii  alsa-firmware-loaders                          1.0.24.1-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                       1.0.17-4                                          ALSA wrapper for OSS applications
ii  alsa-source                                    1.0.24+dfsg-0ubuntu1                              ALSA driver sources
ii  alsa-tools                                     1.0.24.1-0ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                 1.0.24.1-0ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                                     1.0.24.2-0ubuntu6                                 Utilities for configuring and using ALSA
ii  alsaplayer-alsa                                0.99.80-5build1                                   PCM player designed for ALSA (ALSA output module)
ii  alsaplayer-common                              0.99.80-5build1                                   PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                                 0.99.80-5build1                                   PCM player designed for ALSA (GTK+ version)
ii  bluez-alsa                                     4.91-0ubuntu1                                     Bluetooth ALSA support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                         ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.32-1ubuntu5                                  GStreamer plugin for ALSA
ii  libalsa-ocaml                                  0.1.4-2build1                                     OCaml bindings for the ALSA library
rc  libclalsadrv1                                  1.2.2-2                                           ALSA driver C++ access library
rc  linux-backports-modules-alsa-2.6.32-25-generic 2.6.32-25.24                                      Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
rc  linux-backports-modules-alsa-2.6.32-25-preempt 2.6.32-25.24                                      Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.

head -n 1 /proc/asound/card*/codec#*
Codec: ATI R6xx HDMI

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
Located at:
[http://www.alsa-project.org/db/?f=d1e599a334168ac371c932d0a135ab114baf4126](http://www.alsa-project.org/db/?f=d1e599a334168ac371c932d0a135ab114baf4126)

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

echo "options snd-hda-intel model=6stack-digout " | sudo tee -a /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=6stack-digout

I've attached the output from the script the only errors i noticed are at the final install step last 4 lines
Its not actually a zip file its text renamed to .zip

Thanks for anyone being able to help and take a look and thanks [Temüjin]("http://ubuntuforums.org/member.php?u=327594") for making this script
:)

---

### Post by Yellow Pasque on 2011-06-24
The script ran successfully. Don't worry about the last 4 lines (they pertain to legacy OSS support, which Ubuntu disables in their kernels). Run the alsa-info script or look at dmesg to see why the module isn't loading.

---

### Post by duindain on 2011-06-24
> **Temüjin said:**
> The script ran successfully. Don't worry about the last 4 lines (they pertain to legacy OSS support, which Ubuntu disables in their kernels). Run the alsa-info script or look at dmesg to see why the module isn't loading.
Sorry i should have mentioned im not fantastic with linux i can run commands follow examples change code around but i dont know alot of the background linux knowledge stuff
The info script was contained in the last post what is the command to view dmesg issues?
But i reran it as i changed one line in the config that was repeating a command that i added awhile ago, hda auto probe thing
This is the most current alsa info script
Your ALSA information is located at 
[http://www.alsa-project.org/db/?f=0d5cfc884159275d376e03f40351939b81ed7d40](http://www.alsa-project.org/db/?f=0d5cfc884159275d376e03f40351939b81ed7d40)

Im not really sure whats wrong other than its using the sound on my graphics card rather than onboard

---

### Post by lidex on 2011-06-24
> **duindain said:**
> Sorry i should have mentioned im not fantastic with linux i can run commands follow examples change code around but i dont know alot of the background linux knowledge stuff
The info script was contained in the last post what is the command to view dmesg issues?
But i reran it as i changed one line in the config that was repeating a command that i added awhile ago, hda auto probe thing
This is the most current alsa info script
Your ALSA information is located at 
[http://www.alsa-project.org/db/?f=0d5cfc884159275d376e03f40351939b81ed7d40](http://www.alsa-project.org/db/?f=0d5cfc884159275d376e03f40351939b81ed7d40)

Im not really sure whats wrong other than its using the sound on my graphics card rather than onboard

You have some cruft in your alsa-base.conf file:
```

snd-hda-intel: model=auto
snd-hda-intel: model=6stack-digout 
snd-hda-intel: model=6stack-digout 
snd-hda-intel: model=auto probe_mask=1
```

I'd imagine the probe mask option is causing your problem.

---

### Post by Yellow Pasque on 2011-06-24
> snd-hda-intel: model=auto
snd-hda-intel: model=6stack-digout 
snd-hda-intel: model=6stack-digout 
snd-hda-intel: model=auto probe_mask=1

It looks like you just keep adding options to alsa-base.conf. Please edit the file and only use one option at a time. If you want to keep old lines for reference, put a '#' in front of the line to comment it out.
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
> The info script was contained in the last post what is the command to view dmesg issues?
The command is simply:
```
dmesg
```
Don't worry about it though, as the alsa-info script includes the relevant dmesg lines.
```
[    9.963744] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.963779] HDA Intel 0000:00:1b.0: irq 55 for MSI/MSI-X
[    9.963795] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.040643] ALSA hda_intel.c:1459: no codecs initialized
[   10.040718] HDA Intel 0000:00:1b.0: PCI INT A disabled
```
It already looks like you tried probe-mask=1, but I would suggest trying different values of probe-mask up to 8.

EDIT: lidex jumped in and stole my thunder (again). Damn him! :P

---

### Post by lidex on 2011-06-24
> **Temüjin said:**
> 
EDIT: lidex jumped in and stole my thunder (again). Damn him! :P

Its for moments like these that I subscribe to this thread.:D

---

### Post by duindain on 2011-06-25
Sorry double post ;(

---

### Post by duindain on 2011-06-25
I tried modprobe stuff up to 5 with no changes i decided to try something crazy and ran the livecd 10.04 version and copied the alsa-conf from that to usb drive and copied over my normal version with that
It has no specific entries for hda stuff at all
so maybe they are stored somewhere else as well?
When that didn't help I reran the install script with cards=all it seems to be more healthy now definitely has a few entries in the alsa info script
No sound yet but getting closer I feel

In the sound preferences i still only see the entry for video card not on-board yet

Any suggestions spring to mind?

Your ALSA information is located at [http://www.alsa-project.org/db/?f=4c77d6d1a00930c2cdf512ebfa5d97781e2ae315](http://www.alsa-project.org/db/?f=4c77d6d1a00930c2cdf512ebfa5d97781e2ae315)

This is my current alsa-conf contents
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

```Thx for looking at this stuff everyone :)

---

### Post by duindain on 2011-06-25
Ok sound is working I went back to the live cd and copied blacklist to compare, my local version had an additional entry which I commented out 
I also had a hda-conf file which has the modprobe auto option stuff in it. Probably from a random suggested change to fix audio stuff. 
I deleted that and one lucky reboot later and bam sound.

Thanks everyone for your help awesome can finally watch stuff again heh ;)

---

### Post by Discombobulated on 2011-06-27
Many thanks soundcheck, Temüjin, lidex et al.

Fixed internal mic on Acer Aspire 4820T, running Ubuntu 10.4 LTS x64.

Don't know if this will help anybody else, but one final additional key to getting the mic to work with Skype was to install and run pavucontrol, unlock the inputs and set 'Front Left' (top) to 79% and 'Front Right' (bottom) to 0%.

It seems pulse sees this mono (mic) source as a pair of stereo channels, but the polarity is inverted on one channel, so the two 'out of phase' channels are added together, producing *no sound*.

Set them to equal values again if you want to record from a stereo source via input jack.

---

### Post by thanhquanky on 2011-06-27
```
Your ALSA information is located at http://www.alsa-project.org/db/?f=c7d40d34de7333ff20c829088de417d580468d3b
```

```
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Tue Jun 28 03:35:25 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name
Product Version:   System Version


!!Kernel Information
!!------------------

Kernel release:    2.6.38-8-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfea78000 irq 44
 1 [TigerJet       ]: USB-Audio - USB Internet Phone by TigerJet
                      TigerJet Network, Inc. USB Internet Phone by TigerJet at usb-0000:00:1d.0-2, fu


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
	Subsystem: 1043:82ea


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_usb_audio
	async_unlink : Y
	device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	ignore_ctl_error : N
	index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	nrpacks : 8
	pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: VIA VT1708B 8-Ch
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1106e721
Subsystem Id: 0x104382ea
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x10 [Audio Output] wcaps 0x411: Stereo
  Device: name="VT1708B Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
Node 0x11 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="VT1708B Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x1e0]: 44100 48000 88200 96000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x13 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="VT1708B Analog", type="Audio", device=0
  Amp-In caps: ofs=0x00, nsteps=0x14, stepsize=0x06, mute=1
  Amp-In vals:  [0x04 0x04]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
Node 0x14 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x14, stepsize=0x06, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x1e
Node 0x15 [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x1f0]: 32000 44100 48000 88200 96000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x16 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Control: name="Master Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Master Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Rear Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Control: name="CD Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="CD Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x18, stepsize=0x06, mute=1
  Amp-In vals:  [0x17 0x17] [0x18 0x18] [0x18 0x18] [0x18 0x18] [0x18 0x18] [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 6
     0x10 0x1f 0x1a 0x1b 0x1e 0x25
Node 0x17 [Audio Selector] wcaps 0x300501: Stereo
  Control: name="Input Source", index=0, device=0
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 5
     0x16* 0x1f 0x1a 0x1b 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x11
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x18
Node 0x1a [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Smart 5.1", index=0, device=0
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x01a19036: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x6
  Pin-ctls: 0x41: OUT VREF_50
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x26
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Independent HP", index=0, device=0
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x0181303e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0xe
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x1c [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x16
Node 0x1d [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Independent HP", index=0, device=0
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 2
     0x16* 0x25
Node 0x1e [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x02a19038: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x8
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x27
Node 0x1f [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x90370137: [Fixed] CD at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x7
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x20 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x074311f0: [Jack] SPDIF Out at Ext Rear Panel
    Conn = ATAPI, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Pin Complex] wcaps 0x400601: Stereo Digital
  Pincap 0x00010030: IN OUT EAPD
  EAPD 0x2: EAPD
  Pin Default 0x47c421f0: [N/A] SPDIF In at Ext Rear Panel
    Conn = RCA, Color = Grey
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x26
Node 0x23 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x27
Node 0x24 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x25 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
Node 0x26 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x24
Node 0x27 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x25
--endcollapse--


!!USB Mixer information
!!---------------------------
--startcollapse--

USB Mixer: usb_id=0x06e6c200, ctrlif=1, ctlerr=0
Card: TigerJet Network, Inc. USB Internet Phone by TigerJet at usb-0000:00:1d.0-2, fu
  Unit: 5
    Control: name="Headset Capture Volume", index=0
    Info: id=5, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=0, max=3840, dBmin=0, dBmax=1500
  Unit: 5
    Control: name="Headset Capture Switch", index=0
    Info: id=5, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 6
    Control: name="PCM Playback Volume", index=0
    Info: id=6, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=0, max=3840, dBmin=0, dBmax=1500
  Unit: 6
    Control: name="PCM Playback Switch", index=0
    Info: id=6, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  9 Jun 28 02:16 /dev/snd/controlC0
crw-rw----  1 root audio 116,  4 Jun 28 02:16 /dev/snd/controlC1
crw-rw----  1 root audio 116,  8 Jun 28 02:16 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  7 Jun 28 10:20 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  6 Jun 28 10:30 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  5 Jun 28 10:20 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  3 Jun 28 10:20 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116,  2 Jun 28 10:22 /dev/snd/pcmC1D0p
crw-rw----  1 root audio 116,  1 Jun 28 02:16 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jun 28 02:16 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Jun 28 02:16 .
drwxr-xr-x 4 root root 280 Jun 28 02:16 ..
lrwxrwxrwx 1 root root  12 Jun 28 02:16 usb-TigerJet_Network__Inc._USB_Internet_Phone_by_TigerJet_A921050108E1D2-01 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jun 28 02:16 .
drwxr-xr-x 4 root root 280 Jun 28 02:16 ..
lrwxrwxrwx 1 root root  12 Jun 28 02:16 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 Jun 28 02:16 pci-0000:00:1d.0-usb-0:2:1.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: TigerJet [USB Internet Phone by TigerJet], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: TigerJet [USB Internet Phone by TigerJet], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfea78000 irq 44'
  Mixer name	: 'VIA VT1708B 8-Ch'
  Components	: 'HDA:1106e721,104382ea,00100100'
  Controls      : 35
  Simple ctrls  : 19
Simple mixer control 'Master Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 24
  Mono:
  Front Left: Playback 23 [96%] [0.00dB] [on]
  Front Right: Playback 23 [96%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 24
  Mono:
  Front Left: Playback 24 [100%] [1.75dB] [on]
  Front Right: Playback 24 [100%] [1.75dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 27
  Mono: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 27
  Mono: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 24
  Mono:
  Front Left: Playback 24 [100%] [1.75dB] [on]
  Front Right: Playback 24 [100%] [1.75dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 24
  Mono:
  Front Left: Playback 24 [100%] [1.75dB] [on]
  Front Right: Playback 24 [100%] [1.75dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 4 [20%] [7.00dB] [on]
  Front Right: Capture 4 [20%] [7.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Rear Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Stereo Mixer'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 24
  Mono:
  Front Left: Playback 24 [100%] [1.75dB] [on]
  Front Right: Playback 24 [100%] [1.75dB] [on]
Simple mixer control 'Smart 5.1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [TigerJet]

Card hw:1 'TigerJet'/'TigerJet Network, Inc. USB Internet Phone by TigerJet at usb-0000:00:1d.0-2, fu'
  Mixer name	: 'USB Mixer'
  Components	: 'USB06e6:c200'
  Controls      : 4
  Simple ctrls  : 2
Simple mixer control 'PCM',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [15.00dB] [on]
Simple mixer control 'Headset',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 15
  Mono: Capture 8 [53%] [8.00dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		iface MIXER
		name 'Master Front Playback Volume'
		value.0 23
		value.1 23
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 24'
			dbmin -4025
			dbmax 175
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.2 {
		iface MIXER
		name 'Master Front Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Front Playback Volume'
		value.0 27
		value.1 27
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 27'
			dbmin -4725
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Surround Playback Volume'
		value.0 27
		value.1 27
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 27'
			dbmin -4725
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.6 {
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.7 {
		iface MIXER
		name 'Center Playback Volume'
		value 27
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 27'
			dbmin -4725
			dbmax 0
			dbvalue.0 0
		}
	}
	control.8 {
		iface MIXER
		name 'LFE Playback Volume'
		value 27
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 27'
			dbmin -4725
			dbmax 0
			dbvalue.0 0
		}
	}
	control.9 {
		iface MIXER
		name 'Center Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.10 {
		iface MIXER
		name 'LFE Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.11 {
		iface MIXER
		name 'Side Playback Volume'
		value.0 27
		value.1 27
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 27'
			dbmin -4725
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.12 {
		iface MIXER
		name 'Side Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.13 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 27
		value.1 27
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 27'
			dbmin -4725
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.14 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.15 {
		iface MIXER
		name 'Rear Mic Playback Volume'
		value.0 24
		value.1 24
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 24'
			dbmin -4025
			dbmax 175
			dbvalue.0 175
			dbvalue.1 175
		}
	}
	control.16 {
		iface MIXER
		name 'Rear Mic Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.17 {
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 24
		value.1 24
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 24'
			dbmin -4025
			dbmax 175
			dbvalue.0 175
			dbvalue.1 175
		}
	}
	control.18 {
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.19 {
		iface MIXER
		name 'Line Playback Volume'
		value.0 24
		value.1 24
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 24'
			dbmin -4025
			dbmax 175
			dbvalue.0 175
			dbvalue.1 175
		}
	}
	control.20 {
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.21 {
		iface MIXER
		name 'CD Playback Volume'
		value.0 24
		value.1 24
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 24'
			dbmin -4025
			dbmax 175
			dbvalue.0 175
			dbvalue.1 175
		}
	}
	control.22 {
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.23 {
		iface MIXER
		name 'Independent HP'
		value OFF
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 OFF
			item.1 ON
		}
	}
	control.24 {
		iface MIXER
		name 'Smart 5.1'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.25 {
		iface MIXER
		name 'Capture Volume'
		value.0 4
		value.1 4
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 20'
			dbmin 0
			dbmax 3500
			dbvalue.0 700
			dbvalue.1 700
		}
	}
	control.26 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.27 {
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 20'
			dbmin 0
			dbmax 3500
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.28 {
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.29 {
		iface MIXER
		name 'Input Source'
		value 'Stereo Mixer'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Stereo Mixer'
			item.1 'Rear Mic'
			item.2 'Front Mic'
			item.3 Line
			item.4 CD
		}
	}
	control.30 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.31 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.32 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.33 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.34 {
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.35 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
state.TigerJet {
	control.1 {
		iface MIXER
		name 'PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'PCM Playback Volume'
		value 15
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 15'
			dbmin 0
			dbmax 1500
			dbvalue.0 1500
		}
	}
	control.3 {
		iface MIXER
		name 'Headset Capture Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'Headset Capture Volume'
		value 8
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 15'
			dbmin 0
			dbmax 1500
			dbvalue.0 800
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_utf8
isofs
nls_iso8859_1
nls_cp437
vfat
fat
binfmt_misc
snd_hda_codec_via
snd_hda_intel
snd_usb_audio
snd_hda_codec
snd_hwdep
snd_usbmidi_lib
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
ppdev
i915
usbhid
usb_storage
uas
hid
psmouse
parport_pc
asus_atk0110
snd
serio_raw
drm_kms_helper
soundcore
snd_page_alloc
drm
i2c_algo_bit
video
lp
parport
r8169


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x01011012
0x1a 0x01a19036
0x1b 0x0181303e
0x1c 0x01014010
0x1d 0x0221401f
0x1e 0x02a19038
0x1f 0x90370137
0x20 0x074311f0
0x21 0x47c421f0
0x22 0x01016011
0x23 0x01012014

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   15.083020] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.243577] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.243635] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   15.243662] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.288722] usbcore: registered new interface driver snd-usb-audio



```

---

### Post by senjion on 2011-07-08
I am having an issue where my Sound Control is showing nothing on the Hardware Tab. Everything was previously working however I must have run something to muck it up recently.

I am currently on Alsa Driver 1.0.23 and tried running the upgrade script, but it seems that alsa-project.org is down as I cannot browse there and the script is coming back with the following:

***************************************************************************
*  Downloading and extracting ALSA packages...
***************************************************************************
--2011-07-08 17:42:39--  [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.24.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.24.tar.bz2)
           => `alsa-driver-1.0.24.tar.bz2'
Resolving ftp.alsa-project.org... 77.48.224.243
Connecting to ftp.alsa-project.org|77.48.224.243|:21... connected.
Logging in as anonymous ... 

Error in server response, closing control connection.
Retrying.

I have already tried purging everything ALSA/Pulse related and reinstalling but with no change in progress.

When my system boots up, I have sound on the login prompt, after login there is no longer any sound.

I have verified that my User is allowed to use audio devices.

When Running Ubuntu 10.10 off of the Installation Disk I also have working sound and my hardware shows in Sound Control.

Any suggestions before I get fed up and just reinstall?

---

### Post by Sorensiim on 2011-07-08
Mine stalls when trying to connect to the Alsa-project FTP, when trying to log in anonymously. Will try again tomorrow, the script was working great two days ago :)

---

### Post by senjion on 2011-07-08
Managed to modify the script to download the required files from an alsa-project.org mirror.

Everything executed properly, still no sound.

senjion@ZEDD:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Jul  8 2011 for kernel 2.6.38-8-generic-pae (SMP).

```
senjion@ZEDD:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
senjion@ZEDD:~$ speaker-test -Dplughw:1,0 -c2

speaker-test 1.0.24.2

Playback device is plughw:1,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM plughw:1,0
Playback open error: -2,No such file or directory
```

---

### Post by fabridelo on 2011-07-31
Hello


I partly solved, now in Vlc i have front,center and rear but no dolby 5.1.
In xbmc I ear only effect on front and rear when to flag 5.1
and good when flag 2.1 but no surraund.
I no have a solution any suggestion?

I have asus at3iont-deluxe and audio is alc887
I insert in alsa.conf  3stach-6ch-dig

bye

---

### Post by moccochoco on 2011-08-09
Wow this really works!
I have been searching the web for a usable solution for days with no luck, and then I stumbled upon this thread...
Worked like a charm.
I have a Lenovo ThinkPad R500 with an hda intel ICH9 soundcard, running Ubuntu 11.04 64 bits version and I have been compiling, erasing, reinstalling and recompiling almost compulsively, without luck until I tried out this upgrade script... Worked the first time!
This is simply fantastic!
Thank you for providing us with such a brilliant script!
The World really needs people like you!:D
Best Regards
Heidi Munksgaard
Denmark

---

### Post by fabridelo on 2011-08-25
Hello 

I install this script , work but no work alsamixer, no volume no center no lfe
My system is ubuntu 10.04 

Any suggestion?

---

### Post by lkjoel on 2011-08-25
Could you give us the link that this command gives you?
```
wget http://www.alsa-project.org/alsa-info.sh && bash alsa-info.sh

```
**

---

### Post by fabridelo on 2011-08-26
Hello

My alsa information are here:

 [http://www.alsa-project.org/db/?f=2bfcc433f0668f982fa401194a4e888642b81b14](http://www.alsa-project.org/db/?f=2bfcc433f0668f982fa401194a4e888642b81b14)

Thanks for the help

bye

---

### Post by inkb_hyc on 2011-08-27
:P thank you. I have saved the problem.

Mark...

---

### Post by fabridelo on 2011-08-30
hello

my alsa 1.024 on ubuntu 10.04 work!!!!!
i launched script with old kernel and then with new kernel i use option -i.
i have dolby sorraund 5.1 with dts but don't work alsamixer (gnome-alsamixer don't work too).
any suggestion?

bye

---

### Post by dimamyth on 2011-09-16
Thanks a lot, mate! I tried ~5 methods to restore sound on my Asrock FX890 after installing fresh realtek drivers, and only your solution worked fine.

---

### Post by skarbi on 2011-09-17
Solved my problem with no microphone (or just garbled noises) in Skype with HDA VIA VT82xx sound card (Ubuntu 10.04). Thanks!

---

### Post by lkjoel on 2011-09-17
> **fabridelo said:**
> hello

my alsa 1.024 on ubuntu 10.04 work!!!!!
i launched script with old kernel and then with new kernel i use option -i.
i have dolby sorraund 5.1 with dts but don't work alsamixer (gnome-alsamixer don't work too).
any suggestion?

bye
What's the output on AlsaMixer?

---

### Post by Samogon on 2011-09-19
Hello. Is there differences with debian6, 2.6.32-5-686, Asus XonarDG?
I have a lot of errors in this step: "sudo ./AlsaUpgrade-1.0.24-2.sh -c"
Log attached. Sorry for my english :)

---

### Post by nemesys79 on 2011-09-21
:popcorn:
Thank you all guys!!!
I followed this script step-by-step,
it worked for me 100% with no issues on a HP 630 Notebook,passed from an unknown Realtek chipset to "00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)" Now i have 2 analog 4.0 surround output channels that seems to be always muted,but the duplex output is working great!
In my last setup i could only hear sounds from headphones jack,and no mic working.Now the mic comes alive.

This thing was turning me crazy!

Here's my alsa information script output before this
[http://www.alsa-project.org/db/?f=ecf4ac3d121b9dd77d881f47e4233524fbf7953d](http://www.alsa-project.org/db/?f=ecf4ac3d121b9dd77d881f47e4233524fbf7953d)

---

### Post by .... on 2011-09-22
> **Samogon said:**
> Hello. Is there differences with debian6, 2.6.32-5-686, Asus XonarDG?
I have a lot of errors in this step: "sudo ./AlsaUpgrade-1.0.24-2.sh -c"
Log attached. Sorry for my english :)

The log is difficult for me to comprehend because I can't see where the exact error is. I'm sure there are differences in some package names and maybe the kernel module location.

---

### Post by shini-kire on 2011-09-22
> PRoblem:

```
make[2]: *** [libasound_module_pcm_a52.la] Error 1
make[2]: se sale del directorio «/opt/Alsa-1.0.24/alsa-plugins-1.0.24/a52»
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio «/opt/Alsa-1.0.24/alsa-plugins-1.0.24»
```

help please T__T

Solution:

> **.... said:**
> Rerun the script with -d option.** Make sure that no other package managers are open or you will not get the needed packages.** The package you're missing is libsdl1.2-dev

Hmm: This package is not in the alsaupgrade script. I wonder why no one complained of this error before :?
 thnks!  =) 

I Install this:

```
sudo apt-get install libsdl1.2-dev
```

thnks!

---

### Post by xevan on 2011-09-27
thanx :p

---

### Post by Enigmapond on 2011-09-27
Thank you for this. Worked like a charm! No errors.

---

### Post by darporfe on 2011-09-28
Hi there.

I install the alsa upgrade with no problems, now I can see all the outputs of my motherboard.

I have a Dolby Digital and DTS speakers system, and it's connected by a S/PDIF cable. In the alsamixer I can see it but I can't increase the level of it it just remains in "zero" I can adjust it (See attachment)

My motherboard is the Asus Crosshair IV, it comes with a Supreme X-Fi Integrated Sound Card, so it also comes with the S/PDIF output.

Also, this is the output from the aplay -L

> default:CARD=SB
    HDA ATI SB, VT2020 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio OutputThe IEC958 is there, so I really don't now what is wrong.

Any suggestions??

---

### Post by jacktucky on 2011-10-03
Hi I'm trying to use this script to get HDMI sound working on my Zotac MAGHD-ND01-U.

The first step of the script -d fails with many packages not available.  Attached is my log.  Here is an example of one of the errors.

```
E: Couldn't find package alsa-tools
```
```

Reading package lists... 0%
Reading package lists... 100%
Reading package lists... Done
Building dependency tree... 0%
Building dependency tree... 0%
Building dependency tree... 50%
Building dependency tree... 50%
Building dependency tree       
Reading state information... 0%
Reading state information... 0%
Reading state information... Done
E: Couldn't find package alsa-firmware-loaders
```

This is my first experience with Ubuntu and XBMC live.  I'd appreciate any help.  Thanks, Jack

---

### Post by nightfever on 2011-10-11
I'm getting an error while running the script in Oneiric:

```
seq_clientmgr.c:27:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[3]: *** [fastdep] Error 1
make[3]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore/seq'
make[2]: *** [_sfdep_seq] Error 2
make[2]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24'
make: *** [include/sndversions.h] Error 2

***************************************************************************
*  alsa-driver-1.0.24 make failed
***************************************************************************

```

Edit: could it be that Oneiric is using kernel version 3?
EDIT2: I found out smp_lock.h is missing, it was removed from newer kernel versions;
Can this be fixed? I got an older kernel version containing this file. Can anyone tell me at least where to put it?

---

### Post by richgj700 on 2011-10-15
> **nightfever said:**
> I'm getting an error while running the script in Oneiric:

```
seq_clientmgr.c:27:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[3]: *** [fastdep] Error 1
make[3]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore/seq'
make[2]: *** [_sfdep_seq] Error 2
make[2]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24'
make: *** [include/sndversions.h] Error 2

***************************************************************************
*  alsa-driver-1.0.24 make failed
***************************************************************************

```

Edit: could it be that Oneiric is using kernel version 3?
EDIT2: I found out smp_lock.h is missing, it was removed from newer kernel versions;
Can this be fixed? I got an older kernel version containing this file. Can anyone tell me at least where to put it?

Getting the same problem too in Oneiric, can anyone help?

---

### Post by flex80 on 2011-10-18
> **richgj700 said:**
> Getting the same problem too in Oneiric, can anyone help?

Same here... Was trying to get the subwoofer working on an ASUS G73SW and killed my sound. My preferred audio device in Phonon went from Internal Audio Analog Stereo to Dummy Output. I tried running the script to try to do a clean ALSA install but it failed w/ the same error in Oneiric.

---

### Post by nightfever on 2011-10-24
Guys, I think there's no need to run the whole script.
As I discovered, I only needed to download alsa-firmware from alsa-project.org, extract it and run ./compile, make, make install. Then restart and the kernel will be able to load the module with the firmware.

Try this ;)

---

### Post by jzaiat on 2011-10-28
> **nightfever said:**
> Guys, I think there's no need to run the whole script.
As I discovered, I only needed to download alsa-firmware from alsa-project.org, extract it and run ./compile, make, make install. Then restart and the kernel will be able to load the module with the firmware.

Try this ;)

Hello, I have the same problem... I've tried your solution but it is not working either (downloaded the firmware, run ./configure, make, make install, then reboot).

Any ideas?
Thanks
Jonathan

---

### Post by nightfever on 2011-10-29
> **jzaiat said:**
> Hello, I have the same problem... I've tried your solution but it is not working either (downloaded the firmware, run ./configure, make, make install, then reboot).

Any ideas?
Thanks
Jonathan
Are you sure you have all the packages installed and that your card is supported?

---

### Post by jzaiat on 2011-10-29
> **nightfever said:**
> Are you sure you have all the packages installed and that your card is supported?

Hi, I think my card is supported since it was working perfectly before upgrading from Natty to Oneiric... about the packages I'm not sure, for some reason I dont have to driver, here you can see more info about my configuration [http://www.alsa-project.org/db/?f=de79f0f3e5498f45362e1d8e911572f97daab012](http://www.alsa-project.org/db/?f=de79f0f3e5498f45362e1d8e911572f97daab012).
Thanks
Jonathan

---

### Post by Yellow Pasque on 2011-11-08
> **richgj700 said:**
> Getting the same problem too in Oneiric, can anyone help?

You need to use the -s option or manually add this one-liner patch after downloading: [http://git.alsa-project.org/?p=alsa-driver.git;a=commit;h=baca592e70a173500101f19447f35b188fab48c7](http://git.alsa-project.org/?p=alsa-driver.git;a=commit;h=baca592e70a173500101f19447f35b188fab48c7)

There could be other build issues in Oneiric, idk. I use Debian and suse nowadays.

---

### Post by jzaiat on 2011-11-08
> **Temüjin said:**
> You need to use the -s option or manually add this one-liner patch after downloading: [http://git.alsa-project.org/?p=alsa-driver.git;a=commit;h=baca592e70a173500101f19447f35b188fab48c7](http://git.alsa-project.org/?p=alsa-driver.git;a=commit;h=baca592e70a173500101f19447f35b188fab48c7)

There could be other build issues in Oneiric, idk. I use Debian and suse nowadays.


Hello, can you tell me in which command should I use the -s option? Thank you!
Jonathan

---

### Post by jzaiat on 2011-11-08
> **jzaiat said:**
> Hello, can you tell me in which command should I use the -s option? Thank you!
Jonathan

I figured it out, the -s option should be used instead of -d in the script: "./AlsaUpgrade-1.0.24-2.sh -s". But the snapshot url doesn't exist anymore... so, I tried to download the configure.in file and replace it manually before compiling (in /opt/Alsa-1.0.24/alsa-driver-1.0.24) but it doesn't work either, I get the same error: "fatal error: linux/smp_lock.h: No such file or directory".
What should I do?

Thanks for your advice.
Jonathan

---

### Post by tmow on 2011-11-27
Thanks a lot!

Unlucky I cannot download any of these files as I don't permissions...

It seems I should post at least 50 times.... Let's start

---

### Post by tmow on 2011-11-27
I can download the script... But I have the same error as above:


seq_clientmgr.c:27:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[3]: *** [fastdep] Error 1

---

### Post by fritz222 on 2011-12-02
Thank you for writing this awesome script!! :D

On my PC the script runs through without any problems but it doesn't update my Alsa.

The output of ```
cat /proc/asound/version
``` is still ```
xbmc@XBMCLive:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Feb  1 2011 for kernel 2.6.32-29-generic (SMP).

I have a XBMC Live install(Ubuntu 10.04 Lucid).


```Could somebody help me.
Thanks in advance.
Regards fritz222

---

### Post by lattensepp on 2011-12-11
Hi!

Have the same Problem with 10.04 LTS

reel@ReelBox:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Dec 21 2010 for kernel 2.6.32-26-generic (SMP).
reel@ReelBox:~$ 

Alsa mixer is new, but the driver not!

What's wrong?

regards

---

### Post by lidex on 2011-12-27
> **lattensepp said:**
> Hi!

Have the same Problem with 10.04 LTS

reel@ReelBox:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Dec 21 2010 for kernel 2.6.32-26-generic (SMP).
reel@ReelBox:~$ 

Alsa mixer is new, but the driver not!

What's wrong?

regards
Are you still having audio issues?

---

### Post by jmueller09 on 2011-12-31
thanks for this script

it fixed all sound issues i had lol, i'm impressed

---

### Post by lattensepp on 2012-01-07
"Are you still having audio issues"

Yes, problems with the Nvidia GT430 and Realtek ALC889 (OnBoard).
Cannot install newer alsa with this script.
My problem is also I use the reelbox Software wit eHD Card, so I have to use Kernel 2.6.32-36 (needed by the card) for watching tv


regards

---

### Post by Deviad on 2012-01-13
Hello everyone,
the snapshot drivers by tiwai are not anymore in the repository that was written in the script, googling around I found them here:
[http://mirror.nexcess.net/kernel.org/linux/kernel/people/tiwai/snapshot/](http://mirror.nexcess.net/kernel.org/linux/kernel/people/tiwai/snapshot/).
So change the URL accordingly in the script with this one:
[http://mirror.nexcess.net/kernel.org/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](http://mirror.nexcess.net/kernel.org/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)

At the moment I haven't had anymore the hateful error message caused by this: [http://git.alsa-project.org/?p=alsa-driver.git;a=commit;h=baca592e70a173500101f19447f35b188fab48c7](http://git.alsa-project.org/?p=alsa-driver.git;a=commit;h=baca592e70a173500101f19447f35b188fab48c7)

Thank you very much.

EDIT: I'm using Backtrack 5 RT1 based on Ubuntu 10.04 and I had an error at "make install time" regarding the absence of xmlto, so I had to install it.

---

### Post by Deviad on 2012-01-13
Thank you, thank you very much. It works great now! You saved my day!

EDIT: In order to help other people with my same laptop, here are the specs:
[http://www.alsa-project.org/db/?f=ae720d69b8126e409effc3b898b08cdaa7815db6](http://www.alsa-project.org/db/?f=ae720d69b8126e409effc3b898b08cdaa7815db6)

Samsung NP305V5A

---

### Post by Druegan on 2012-01-15
Hi folks,

Trying this script as a last ditch attempt to fix my audio without completely reinstalling the OS, but I'm getting failure in the compile step.. 
```
/usr/bin/ld: /usr/local/lib/libavcodec.a(allcodecs.o): relocation R_X86_64_32 against `ff_h263_vaapi_hwaccel' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libasound_module_pcm_a52.la] Error 1
make[2]: Leaving directory `/opt/Alsa-1.0.24/alsa-plugins-1.0.24/a52'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/Alsa-1.0.24/alsa-plugins-1.0.24'
make: *** [all] Error 2

***************************************************************************
*  alsa-plugins-1.0.24 make failed
***************************************************************************

```

Can anyone advise what this means?  I'm still very much a newbie and I don't really have a clue about scripts and compiling..

---

### Post by kgrodzicki on 2012-01-17
I got the same problem with smp_lock.h
```

.c pcm32.c rawmidi32.c timer32.c hwdep32.c seq32.c > .depend
ioctl32_new.c:23:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[3]: *** [fastdep] Error 1
make[3]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore/ioctl32'
make[2]: *** [_sfdep_ioctl32] Error 2
make[2]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24'
make: *** [include/sndversions.h] Error 2

***************************************************************************
*  alsa-driver-1.0.24 make failed
***************************************************************************

```

my kernel version: 3.0.0-14-generic

- K

---

### Post by c0reysc0tt on 2012-01-24
First, THANK YOU Temüjin for picking up this script and keeping it available.  Also, a huge thank you to Deviad for pointing out the things that were causing failures.

I had the same trouble a lot of you are posting about, so here's a complete list of what I did that finally got everything to install without errors:

[LIST=1]
[*]download the script and save it somewhere
[*]cd <your download directory>
[*]tar xzvf AlsaUpgrade-1.0.24-2.tar.gz
[*]chmod +x AlsaUpgrade-1.0.24-2.sh
[*]sudo apt-get install xmlto (I had to do this to avoid the make errors.) 
[*]apt-get update (the xmlto install in the previous command said it wasn't complete and the update was suggested.  Not sure everyone will need this step.)
[*]nano AlsaUpgrade-1.0.24-2.sh (or the text editor of your choice)
[*]find and change the tiwain ftp address to the http address Deviad gives above, save the file and exit your editor.
[*]sudo ./AlsaUpgrade-1.0.24-2.sh -d
[*]sudo ./AlsaUpgrade-1.0.24-2.sh -s
[*]sudo ./AlsaUpgrade-1.0.24-2.sh -c
[*]sudo ./AlsaUpgrade-1.0.24-2.sh -1
[*]sudo shutdown -r 0
[/LIST]

Hope it helps others.  Obviously not everyone is going to be missing the same things so I don't know if it will work for everyone, but it's what got me past the errors.  Rebooting now.

EDIT: upon closer look, the mixer was updated but not the drivers (sill on 1.2.23)  and still getting "Failed to initialize audio device" in XBMC.  *sigh*  I'm going to bed.  Will keep plugging away tomorrow.

---

### Post by Milos_SD on 2012-01-25
Has anyone been able to compile alsa 1.0.25? I'm having problems with alsa-utils:

```
./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether ln -s works... yes
checking for a sed that does not truncate output... /bin/sed
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.24... found.
checking for snd_ctl_open in -lasound... yes
checking for snd_ctl_elem_add_enumerated... no
configure: error: No user enum control support in alsa-lib

```

---

### Post by axeldamage on 2012-01-28
I've the same problem. I've compiled alsa-driver but not alsa-utils!

---

### Post by jellydog on 2012-01-30
Thanks so much. This fixed my Ubuntu 10.04 LTS install on my Dell XPS l502x system.:p

---

### Post by Yellow Pasque on 2012-01-30
The script installs libasound2-dev and the alsa-utils sees the old include files from that. You need to remove that package and then alsa-utils should build.

---

### Post by doomedforever on 2012-02-01
> **Temüjin said:**
> The script installs libasound2-dev and the alsa-utils sees the old include files from that. You need to remove that package and then alsa-utils should build.

excuse me, just remove this stuff with synaptic and then it should work, am i right? thanks!

---

### Post by Yellow Pasque on 2012-02-02
> **doomedforever said:**
> excuse me, just remove this stuff with synaptic and then it should work, am i right? thanks!
I've updated the Alsa-1.0.25 script to do it automatically.

---

### Post by doomedforever on 2012-02-02
thanks so much for your support! :)

---

### Post by doomedforever on 2012-02-02
well, i am sorry...your support is well much appreciated, but i got a error with the updated script, the last lines are:  *************************************************************************** *  Compiling utils... *************************************************************************** make: *** No rule to make target `clean'.  Stop. Reading package lists... Done Building dependency tree        Reading state information... Done The following packages were automatically installed and are no longer required:   libcaca-dev alsa-tools libslang2-dev libaudiofile-dev alsa-firmware-loaders libglu1-mesa-dev libesd0-dev libaudio-dev fxload libaa1-dev libpng12-dev Use 'apt-get autoremove' to remove them. The following packages will be REMOVED:   libasound2-dev libsdl1.2-dev 0 upgraded, 0 newly installed, 2 to remove and 19 not upgraded. After this operation, 6,250 kB disk space will be freed. (Reading database ... 241955 files and directories currently installed.) Removing libsdl1.2-dev ... Removing libasound2-dev ... Processing triggers for man-db ... Processing triggers for doc-base ... Processing 1 removed doc-base file(s)... Registering documents with scrollkeeper... N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension checking for a BSD-compatible install... /usr/bin/install -c checking whether build environment is sane... yes checking for a thread-safe mkdir -p... /bin/mkdir -p checking for gawk... no checking for mawk... mawk checking whether make sets $(MAKE)... yes checking whether NLS is requested... yes checking for msgfmt... /usr/bin/msgfmt checking for gmsgfmt... /usr/bin/msgfmt checking for xgettext... /usr/bin/xgettext checking for msgmerge... /usr/bin/msgmerge checking for style of include used by make... GNU checking for gcc... gcc checking whether the C compiler works... yes checking for C compiler default output file name... a.out checking for suffix of executables...  checking whether we are cross compiling... no checking for suffix of object files... o checking whether we are using the GNU C compiler... yes checking whether gcc accepts -g... yes checking for gcc option to accept ISO C89... none needed checking dependency style of gcc... gcc3 checking build system type... x86_64-unknown-linux-gnu checking host system type... x86_64-unknown-linux-gnu checking for ld used by GCC... /usr/bin/ld checking if the linker (/usr/bin/ld) is GNU ld... yes checking for shared library run path origin... done checking for CFPreferencesCopyAppValue... no checking for CFLocaleCopyCurrent... no checking for GNU gettext in libc... yes checking whether to use NLS... yes checking where the gettext function comes from... libc checking for cross-compiler... gcc checking for gcc... (cached) gcc checking whether we are using the GNU C compiler... (cached) yes checking whether gcc accepts -g... (cached) yes checking for gcc option to accept ISO C89... (cached) none needed checking dependency style of gcc... (cached) gcc3 checking whether ln -s works... yes checking for a sed that does not truncate output... /bin/sed checking for ALSA CFLAGS...  checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread checking for libasound headers version >= 1.0.24... not present. configure: error: Sufficiently new version of libasound not found.  *************************************************************************** *  alsa-utils-1.0.25 configure failed ***************************************************************************    i am running ubuntu 11.04 AMD64 with latest ubuntu kernel 2.6.38-13 and updates. thanks for reading.  keep up the great work. regards

---

### Post by PegHorse on 2012-02-02
Hi,

Well for me it works !
I had pops/crackles problems with old version so i had to test this.

So i have removed all i had about Alsa then i tried your script.
Everythings goes fine except the first installation he complained about libasound.

> 
Sufficiently new version of libasound not found.  
I remade the -i then it has successfully completed the installation.

But i had to fixe this which wasn't done automatically :
```

@hooks [
        {
                func load
                files [
                       [B] "/usr/share/alsa/pulse.conf"
                        "/etc/asound.conf"
                        "~/.asoundrc"[/B]
                ]
                errors false
        }
]

```As you put on your post first post.

There is also a single error after the run of Alsaconf. 

> 
/usr/sbin/alsaconf: ligne 899: /etc/modutils/sound: Aucun fichier ou dossier de ce type ( No files or directory found )
But the config seems to works fine because you fixed my issue.

Using LinuxMint12 100% compatible with Ubuntu Oneiric 11.10 AMD64

Thanks very much for your works !

---

### Post by Yellow Pasque on 2012-02-02
@doomedforever, I saw what I did wrong and corrected it. See if the new version (-3) works.

@PegHorse: yw. (Unfortunately,) there still seems to be strong demand for this script. I haven't seen a PPA that updates often enough and provides updates for all 50 (yes, that's an exaggeration) currently supported versions of Ubuntu.

---

### Post by doomedforever on 2012-02-02
> **Temüjin said:**
> @doomedforever, I saw what I did wrong and corrected it. See if the new version (-3) works.

@PegHorse: yw. (Unfortunately,) there still seems to be strong demand for this script. I haven't seen a PPA that updates often enough and provides updates for all 50 (yes, that's an exaggeration) currently supported versions of Ubuntu.

thank you a lot, so a 3rd time try... ;) hope it works. thanks for your fast response.

---

### Post by PegHorse on 2012-02-02
Since the sound is still working, can we fixe this error manually ?
Could you tell me what to edit and do ?

Because what will happen if i do a 3rd time your script even if my system is updated ?

---

### Post by doomedforever on 2012-02-02
> **Temüjin said:**
> @doomedforever, I saw what I did wrong and corrected it. See if the new version (-3) works.

@PegHorse: yw. (Unfortunately,) there still seems to be strong demand for this script. I haven't seen a PPA that updates often enough and provides updates for all 50 (yes, that's an exaggeration) currently supported versions of Ubuntu.

it seems to work now flawlessly with your upgraded script -3 version. ;) thanks very much!

---

### Post by PegHorse on 2012-02-02
> **doomedforever said:**
> it seems to work now flawlessly with your upgraded script -3 version. ;) thanks very much!

I've redone it, me too, just i had to add the bolded line again :)
Just a detail ! We can't download snapshots build, you should try with this URL : [http://www.alsa-project.org/snapshot/](http://www.alsa-project.org/snapshot/)

---

### Post by Yellow Pasque on 2012-02-02
I removed the snapshot feature for the moment as I'm deciding whether the snapshot is a good idea or if it's better just to clone git sources.

---

### Post by venik212 on 2012-02-02
If we *still* have such problem with getting sound, Linux is doomed.

---

### Post by doomedforever on 2012-02-03
> **venik212 said:**
> If we *still* have such problem with getting sound, Linux is doomed.

Its way better than the driver hell shite with winshit! ;)  further, it sounds way better. i'd never go back to poor windoze.

---

### Post by Nisuspi on 2012-02-03
Temüjin - thank you so much for this. I'd been having real problems getting the 1.0.25 to compile properly, but your script worked like a charm.

---

### Post by kgrodzicki on 2012-02-03
Hi,

I reinstalled alsa using the newest version of the script 1.0.25-3. It compiled and installed like a charm, but even though after restart I get:

```

$ aplay -l
aplay: device_list:252: no soundcards found...

```

I followed also "Sound Troubleshooting Guide" without success... My system recognize soundcard, but in Sound config I can see only Dummy output..
```

Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
01:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa90]

```

Do you have any more tips?

Ubuntu 11.10 MacBookPro 8,2

- K

---

### Post by fundipk on 2012-02-06
Thanks ... worked first time ...

---

### Post by Chronicical on 2012-02-14
Hi, I'm new to ubuntu and having some problems with the upgrade script. When running the compile, I'm getting the following error:

In file included from /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm.c:30:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/include/sound/pcm.h:434: error: field ‘latency_pm_qos_req’ has incomplete type
make[3]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm.o] Error 1
make[2]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/acore] Error 2
make[1]: *** [_module_/opt/Alsa-1.0.25/alsa-driver-1.0.25] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make: *** [compile] Error 2

Can anyone tell me what I'm doing wrong??

---

### Post by Marcelo Ruiz on 2012-02-16
Same thing on mine (Maverick x64):

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/hrtimer.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/hwdep.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/memory_wrapper.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/memalloc.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/sgbuf.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm.o
In file included from /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm.c:30:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/include/sound/pcm.h:434: error: field ‘latency_pm_qos_req’ has incomplete type
make[3]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm.o] Error 1
make[2]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/acore] Error 2
make[1]: *** [_module_/opt/Alsa-1.0.25/alsa-driver-1.0.25] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.25 make failed
***************************************************************************

```

Any ideas?

---

### Post by Marcelo Ruiz on 2012-02-19
Nobody?

---

### Post by Yellow Pasque on 2012-02-19
> **Marcelo Ruiz said:**
> Nobody?
I googled, but didn't see anything helpful. You might want to try a newer kernel (be sure to keep the old one).

---

### Post by Ambidextrous on 2012-02-19
Temüjin:  Thank you for this. It helped: now I have some sound... stereo, not 5.1, but better than the deafening silence which ensued after installing the Realtek Linux driver.

I'm using a cheap Motherboard with an on-board ALC662 chip.  Under Windows it comes with a utility to assign the shared inputs/outputs (microphone in shares a jack with centre/LFE out, line in shares with surround out) but if such a utility exists under Linux, I have yet to find it.  Further research is clearly in order.

](*,)

---

### Post by Yellow Pasque on 2012-02-19
> Under Windows it comes with a utility to assign the shared inputs/outputs (microphone in shares a jack with centre/LFE out, line in shares with surround out) but if such a utility exists under Linux, I have yet to find it.

Look no further: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

---

### Post by Ambidextrous on 2012-02-19
> **Temüjin said:**
> Look no further: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

Temüjin, you are a gentleman and a scholar... and there are very few of us left.  Many thanks.  

:D

---

### Post by Marcelo Ruiz on 2012-02-20
Thanks for your help. I finally ended up using your script to install alsa 1.24-2 in my Toshiba Qosmio X500. Now everything works as expected.
If someone has been having problems with it, please read post #3 here:
[http://ubuntuforums.org/showthread.php?p=11702897#post11702897]("http://ubuntuforums.org/showthread.php?p=11702897#post11702897")

---

### Post by J0nDaFr3aK on 2012-03-18
hi,
i've followed all the instructions posted in here but i still get this error message when i run this command

command run
```
sudo ./AlsaUpgrade-1.0.24-2.sh -d
```

error received
```
make[3]: *** [fastdep] Error 1
make[3]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore/ioctl32'
make[2]: *** [_sfdep_ioctl32] Error 2
make[2]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/opt/Alsa-1.0.24/alsa-driver-1.0.24'
make: *** [include/sndversions.h] Error 2

***************************************************************************
*  alsa-driver-1.0.24 make failed
***************************************************************************
```

can someone help me please?

EDIT: trying to install the drivers on BackTrack 5 R2. kernel version is 3.2.6 and i have the build-essential package installed
i also tried to install the drivers downloaded from the realtek website. the installation process succeeds but i still get no sound at all

EDIT: i get the same error even with alsa-driver-1.0.25

---

### Post by Yellow Pasque on 2012-03-19
@J0nDaFr3aK: You snipped the output after the actual error message..

---

### Post by Red3 on 2012-03-22
Just a quick thank you, worked perfectly first time.

My ears thank you too :D

---

### Post by anoopkumarm on 2012-03-23
hello,

During the installation, i did not find any problem, even though 'm unable to find my device on the [B]system setting->sound->hardware......

I'm not even getting the audio out or inputs

what can i do to resolve it.... suggest any method plz..... [/B]

I'm using ubuntu 11.10..... I can play files but no audio out. But in my second OS it is working as my system is a multi-boot system.

---

### Post by napapon on 2012-04-21
Hi,

I did the Alsa upgrade script posted by [Temüjin ]("http://ubuntuforums.org/member.php?u=327594")
for version 1.0.24.1, all went well, after rebooted, I heard sound when login,
I can played MP3 with sound, great. thanks for this.
Also played avi files with sound and pictures.

However, still no sound from Utubes but the video played ok.

Any suggestion and thanks much for your time.

---

### Post by Yellow Pasque on 2012-04-21
Have you added the bolded line to /usr/share/alsa/alsa.conf as instructed in the OP?

---

### Post by Marcelo Ruiz on 2012-04-21
It seems you have problems playing flash sound while you play other sounds.
To check if this is the problem do the following:
***Reboot*** your computer, login, do nothing but going to youtube to play a video. If you hear the sound it means flash can't play the sound while other programs are/were using the sound card.
If **this** is your issue, in a terminal type the following:

```
gksudo gedit /etc/asound.conf
```

enter your password to open gedit.
Then ensure the file content is as follows:

```

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

Then ***Reboot*** the computer and see if everything works as expected. 
I hope it helps! Good Luck!

---

### Post by axipher on 2012-04-21
I've tried running this script on Ubuntu 10.10 and get an error 2 on the compile stage of the script.  See attached text file (had to compress it due to forum upload limits)

---

### Post by Yellow Pasque on 2012-04-22
> **axipher said:**
> I've tried running this script on Ubuntu 10.10 and get an error 2 on the compile stage of the script.  See attached text file (had to compress it due to forum upload limits)
Due to kernel changes, you will probably have more luck with the 1.0.24 script. Ubuntu 10.10 is EOL/unsupported anyway.

---

### Post by axipher on 2012-04-22
> **Temüjin said:**
> Due to kernel changes, you will probably have more luck with the 1.0.24 script. Ubuntu 10.10 is EOL/unsupported anyway.

Thanks for the quick reply.  I'll give the 1.0.24 script a try and report back.  If that doesn't work than I might just have to upgrade Distros and hope nothing breaks.

---

### Post by crishv on 2012-04-22
thanks works great on my netbook HP2133 :p

---

### Post by crishv on 2012-04-22
Lost audio after rebooting :( . Install this version:
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.25.
Compiled on Apr 22 2012 for kernel 2.6.32-40-generic (SMP).

---

### Post by TimCastle on 2012-04-28
Thank you for your script. On Linuxmint Debian Edition, compiling failed with errors like 

```
/usr/src/linux-headers-3.2.0-2-common/arch/x86/include/asm/bitops.h:59:24: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’
/usr/src/linux-headers-3.2.0-2-common/arch/x86/include/asm/bitops.h:97:24: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’
/usr/src/linux-headers-3.2.0-2-common/arch/x86/include/asm/bitops.h: In function ‘clear_bit_unlock’:
/usr/src/linux-headers-3.2.0-2-common/arch/x86/include/asm/bitops.h:121:2: error: implicit declaration of function ‘barrier’ [-Werror=implicit-function-declaration]
```

But I'm on a 64 bit install.  So I modified line 331 in AlsaUpgrade-1.0.25-3.sh

```

./configure --with-kernel=/usr/src/linux-headers-$KERNEL --with-cards=$CARDS --with-card-options=all --with-sequencer=yes --with-oss=no --prefix=/usr || die "$DRIVER configure failed"
```

and deleted --with-kernel=/usr/src/linux-headers-$KERNEL 

Problem solved.

---

### Post by pastim on 2012-05-01
This (1.0.25-3) all worked very well indeed on 12.04 - thanks very much indeed.

I have a Creative XFi Fatality card, with a front panel (I/O driver panel).  This includes a headphone socket, and an SPDIF out socket (as well as sundry others which I use from time to time but haven't tried lately, such as Midi and additional analogue inputs).  The SPDIF out works fine now, which is really useful.

However, I can still find no way to get the headphone socket to work on ubuntu.  On Windows (I am dual-booted - for now at least) there is a switch you can set to get the headphone socket to override the speakers.  In the past several people have said there is no support for the front panel, but for digital out there now clearly is some, and I had hopes for the headphones.

I have checked 1.0.25 is installed.  Alsamixer shows the rear panel connections but not the front panel ones.

---

### Post by BLKMGK on 2012-05-11
> **Marcelo Ruiz said:**
> Same thing on mine (Maverick x64):

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/hrtimer.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/hwdep.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/memory_wrapper.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/memalloc.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/sgbuf.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm.o
In file included from /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm.c:30:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/include/sound/pcm.h:434: error: field ‘latency_pm_qos_req’ has incomplete type
make[3]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm.o] Error 1
make[2]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/acore] Error 2
make[1]: *** [_module_/opt/Alsa-1.0.25/alsa-driver-1.0.25] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.25 make failed
***************************************************************************

```

Any ideas?

EXACT same error here and the PPA I've found doesn't have a compilation for this kernel. Suggestions on getting past this? [-o<

---

### Post by Yellow Pasque on 2012-05-12
> **BLKMGK said:**
> EXACT same error here and the PPA I've found doesn't have a compilation for this kernel. Suggestions on getting past this? [-o<
As I said a few posts back:
> Due to kernel changes, you will probably have more luck with the 1.0.24 script. Ubuntu 10.10 is EOL/unsupported anyway.

---

### Post by BLKMGK on 2012-05-12
Unfortunately judging from the log errors I'm getting from the software I'm trying to run (XBMC) 1.0.25 ALSA appears to be required for sound playback. I'm attempting to confirm this with the developers now as up until their latest code changes this wasn't required. They have pushed out some changes to their code audio code that I'm compiling now in hopes that this fixes it for now.

Oh and I have used the 1.0.24 script but updated it for 1.0.25 and gotten the above error. The issue isn't your script I'm afraid but rather ALSA failing to compile on the installed kernel - no PPA version available either. IF I'm required to run the latest stable ALSA I may have to downgrade the kernel and then try your script again. I may also be forced to move to 11.04 at which point I'll be pulling my hair out getting rid of Unity I fear. I'll also likely be having to create, again, an .asoundrc file to get hardware working unless this ALSA performs some magic.

I gotta' say, and I know it's not your fault, sound on Linux (still) seems to be a real mess! Your script appears to do everything right near as I can tell and for that I thank you. I had just hoped for a solution that doesn't force me to make major changes to my systems (yes multiple machines).

---

### Post by Sonja on 2012-05-16
I get choppy audio or no audio at all.

[http://www.alsa-project.org/db/?f=87abcac4d835cffeb8f554b2ad54966a3132289c](http://www.alsa-project.org/db/?f=87abcac4d835cffeb8f554b2ad54966a3132289c)

Ideally, I want all audio (e.g. from VLC, Flash in chromium, etc.) to come out of pc speaker, except for skype whcih should use my usb headset.

Sonja

---

### Post by NitroZZeLLo on 2012-06-16
Installed 1.0.25 upgrade on Precise Pangolin and works perfect.

Thank you for your work!

---

### Post by amermc on 2012-06-24
Hello,

   The script is not working for me .. it fails when using -c and gives me :
alsa-oss-1.0.25 not found

I have : Linux deb64 3.2.0-2-amd64

I have tried the older script .. no luck .. says : alsa-firmware-1.0.24.1 not found though I have downloaded this package from source, compiled it and installed it.
Any clue ?

---

### Post by amermc on 2012-06-24
I have not completed the scrip steps ... my mixer is functioning again and also sound.

Thanks ;)

---

### Post by midnightstar on 2012-07-24
I get the following error at the second stage (running the .sh script with the -c switch)

Continue to configure and compile 1.0.25 [y/n]: y


***************************************************************************
*  Alsa packages(drivers/lib/util/firmware/oss) will be compiled
***************************************************************************

***************************************************************************
*  Prepare for compilation and installation...
***************************************************************************

***************************************************************************
*  Compiling drivers...
***************************************************************************
rm -f .depend *.o snd.map*
rm -f modules/*.o modules/*.ko
make: *** include: No such file or directory.  Stop.
make: *** [clean] Error 1
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
configure: error: cannot find install-sh, install.sh, or shtool in "." "./.." "./../.."

***************************************************************************
*  alsa-driver-1.0.25 configure failed
***************************************************************************

Any way I can get the missing files off the web? What exactly is going wrong here?

---

### Post by Yellow Pasque on 2012-07-24
^If you install shtool package, does that help?

---

### Post by faucon50 on 2012-07-29
Hi,

Is there any possibility to revert? I'm not sure if it's because of the upgrade or the new kernel but I have a problem with vlc who doesn't find the alsa output module. Thanks for any help.

Xubuntu 12.04
3.2.0-27-generic
RME 9632

---

### Post by underground on 2012-08-15
I want to revert to.
Is that possible? My webcamera's built in mic is not working with alsa version bigger than 1.0.23.

I try to compile 1.0.23 version on 3.2.0-29 kernel but i get the following error
```
cc1: fatal error: /lib/modules/3.2.0-29-generic/build/include/linux/modversions.h: No such file or directory
```

---

### Post by kbrunsting on 2012-09-08
thanks much for that script... I'm on Ubuntu 10.04.4 LTS, running Mythbuntu and I just swapped in a new ASRock motherboard that had Realtek ALC892 audio and I was getting no sound.  I'm not a strong linux person, but I followed your instructions for compiling/installing it and after watching many things flash across the screen, it said it was installed, I rebooted and sure enough after Mythtv came back up the audio was working again.

---

### Post by amanssan on 2012-10-21
Hi !

Is this script work on debian ?
Because i've an error when i compile :(

```
/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore/hrtimer.c:172: error: expected ‘{’ at end of input
make[5]: *** [/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore/hrtimer.o] Error 1
make[4]: *** [/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore] Error 2
make[3]: *** [_module_/opt/Alsa-1.0.24/alsa-driver-1.0.24] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-5-amd64'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.24 make failed
***************************************************************************

```same error with 1.0.25....

any idea ?

thanks

---

### Post by binloan on 2012-10-23
Anyone has an update on the alsa servers?

They seem to be down.

Edit: Changed sources. Works fine for me.

[https://www.dropbox.com/s/qbsv955x248wm7s/AlsaUpgrade-1.0.25-3.sh](https://www.dropbox.com/s/qbsv955x248wm7s/AlsaUpgrade-1.0.25-3.sh)

---

### Post by OnZy on 2012-10-26
> **amanssan said:**
> Hi !

Is this script work on debian ?
Because i've an error when i compile :(

```
/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore/hrtimer.c:172: error: expected ‘{’ at end of input
make[5]: *** [/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore/hrtimer.o] Error 1
make[4]: *** [/opt/Alsa-1.0.24/alsa-driver-1.0.24/acore] Error 2
make[3]: *** [_module_/opt/Alsa-1.0.24/alsa-driver-1.0.24] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-5-amd64'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.24 make failed
***************************************************************************

```same error with 1.0.25....

any idea ?

thanks

getting the something running ubunt 12.10

---

### Post by doomedforever on 2012-11-05
Hello Temüjin,

would you *please* upgrade your script for the latest ALSA 1.0.26? thanks in advance.
I just tried to replace 1.0.25 with 1.0.26 in your script, but it doesn't work...can't find
the ALSA Utils your script says then.

tia.

---

### Post by Yellow Pasque on 2012-11-05
@doomedforever: I've already made a few small edits and have the script ready. I need to test it on my Ubuntu VM's, and the ALSA ftp is still down (will try alternative link). Keep in mind that the ALSA kernel driver is still at 1.0.25 and only the userspace utils/libs have been updated to 1.0.26

---

### Post by doomedforever on 2012-11-05
> **Temüjin said:**
> @doomedforever: I've already made a few small edits and have the script ready. I need to test it on my Ubuntu VM's, and the ALSA ftp is still down (will try alternative link). Keep in mind that the ALSA kernel driver is still at 1.0.25 and only the userspace utils/libs have been updated to 1.0.26
thanks much for sorting this out, Temüjin. Would you please update it then when ALSA
Kernel 1.0.16 is avialable?

kind regards
~df~

---

### Post by tom21aek on 2012-11-22
Hello guys,
I'm trying the last 7 hours to find a solution with my 5.1 setup on my system but I've done some progress  but still I have a dead rear-left speaker and the mic isn't working.
Before upgrading to 2.6.38-16 kernel I couldn't see any 5.1 setting in the sound preferences. I've tried ALL the posted solutions here and in other sites by still I didn't fix the problem due to the failure of the script (1.0.24) to download the last files and then to start the -c & -i phase and running still alsa 1.0.23

I've looked into the entire thread but there is no updated script without any dead links like here

>            => `alsa-tools-1.0.24.1.tar.bz2'
Looking for ftp.alsa-project.org... 77.48.224.243
Connecting to ftp.alsa-project.org|77.48.224.243|:21... failed: Connection refused.
The results of the alsa-info.sh are below

[http://www.alsa-project.org/db/?f=167d722e06a32276656c0a2460185e65267bb250](http://www.alsa-project.org/db/?f=167d722e06a32276656c0a2460185e65267bb250)
Please help, I've reached to a dead end...

Thank you

---

### Post by icegood on 2012-12-01
Hi there! Have a couple of questions:

1) Which kind of model should i point out in alsa_setup.sh for[ my]("http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=27&Level=5&Conn=4&ProdID=166") device?
2) In my system there are two sound controllers
(first is Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] for Realtek audio device form link above
and integrated to videocard
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:aa68]
).
How it comes that after applying script alsa_setup.sh second controller became invisible? Does script tested well for multi audiocontrollers environment?

---

### Post by frankenst3in on 2012-12-07
x-fi hd on kubuntu natty here 
alsa 1.0.24 works fine for the sound output
no mic though....installing 1.0.25 and hoping that will solve it..

---

### Post by frankenst3in on 2012-12-07
x-fi hd kubuntu natty, alsa1.0.24 works for me, no mic though, dewd, i really hate this forum's interface!!!!!!!

---

### Post by em wai zee on 2012-12-12
> **Temüjin said:**
> Ok, here's the new ALSA upgrade script for ALSA 1.0.25. The script is not in line with Debian/Ubuntu rules for package handling. It just overwrites existing files. You won't see any changes on the ALSA package-ids within Synaptic!

The script recognizes severe problems during the installation and will stop automatically. It shouldn't mess up your setup.
If the script stops with an error-message nothing should have been touched!
In the worst case scenario the -r restore option restores your old system status as good as possible. It'll reinstall kernel, kernel-headers and Alsa related packages.

Ubuntu upgrades/updates might overwrite your Alsa installation once in a while (e.g. Major upgrades, kernel-upgrades or ALSA-package upgrades).
You just need to rerun the upgrade-script using the -i option in this case (if you still have the compiled sources on the disk).

Short Alsa-Upgrade script install instructions:

0. before you begin, close all package managers (Synaptic, Muon, Software Center, etc.)
1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xzvf AlsaUpgrade-1.0.25-3.tar.gz
4. chmod +x AlsaUpgrade-1.0.25-3.sh
5. sudo ./AlsaUpgrade-1.0.25-3.sh -d
6. sudo ./AlsaUpgrade-1.0.25-3.sh -c
7. sudo ./AlsaUpgrade-1.0.25-3.sh -i
8. sudo shutdown -r 0

Logging: I recommend to log all the upgrade steps, e.g.

script -a -c "./AlsaUpgrade-1.0.25-3.sh -d" /tmp/Alsa_1.0.25-1_upgrade_download.log

You'll find a log file /tmp/Alsa_1.0.25-3_upgrade_download.log as soon as the script is finished.
You need to run this procedure for every single step. Choose whatever logfile names.

Test and Troubleshooting

After reboot you can type:

cat /proc/asound/version

This will let you know if you're running the new version.

The easiest and most reliable test to verify if Alsa is working is "aplay" - the Alsa player application. If aplay won't work -- nothing else will work. Make sure that all your channels are unmuted and volume is up!

To get ALSA apps mixed in through pulseaudio, you need to add the bolded line to /usr/share/alsa/alsa.conf
```

@hooks [
        {
                func load
                files [
                        **"/usr/share/alsa/pulse.conf"**
                        "/etc/asound.conf"
                        "~/.asoundrc"
                ]
                errors false
        }
]

```

Hi, I have a "Dummy Output" problem in Ubuntu 12.10, upgraded from 10.04, running from Acer Travelmate 6292. I've managed to get to Step No. 5, then Step No. 6 gave me an error "alsa-driver-1.0.25  not found". I've attached the log instalation for Step No.5... Please please help me!

---

### Post by Yellow Pasque on 2012-12-12
> Hi, I have a "Dummy Output" problem in Ubuntu 12.10, upgraded from 10.04, running from Acer Travelmate 6292.
Please attach your ALSA info [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) 
Running the script is probably not the solution to your problem.

---

### Post by em wai zee on 2012-12-12
> **Temüjin said:**
> Please attach your ALSA info [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) 
Running the script is probably not the solution to your problem.

Thanks a lot. I've solved my "Dummy Output"! I just need to compile the ALSA Driver from its source each time Update Manager has done its kernel upgrading! :popcorn:

---

### Post by Kir_B on 2012-12-15
> **binloan said:**
> Anyone has an update on the alsa servers?

They seem to be down.

Edit: Changed sources. Works fine for me.

[https://www.dropbox.com/s/qbsv955x248wm7s/AlsaUpgrade-1.0.25-3.sh](https://www.dropbox.com/s/qbsv955x248wm7s/AlsaUpgrade-1.0.25-3.sh)


Thank you, Thank you, Thank you, Thank you!

And thank you Temüjin for assuming the maintenance of the script (I love watching it do it's magic)... It would be very helpful to others, if someone could update the initial post with the  updated script (I'd do it, but I don't have sudo powers, yet... Maybe I'll be granted such powers after a few more libations... ).

Thanks for sharing all your hard work everyone.

Kirby

---

### Post by MikesFrance on 2012-12-19
Having this "only HDMI output" problem with Ubuntu 12.10, I tried the script, but it seems to fail on the compilation part.

> In file included from /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/speakers.c:5:0:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c: In function ‘fwspk_card_free’:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c:664:2: erreur: implicit declaration of function ‘fw_device_put’ [-Werror=implicit-function-declaration]
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c: In function ‘fwspk_probe’:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c:721:2: erreur: implicit declaration of function ‘fw_device_get’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/speakers.o] Erreur 1
make[2]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire] Erreur 2
make[1]: *** [_module_/opt/Alsa-1.0.25/alsa-driver-1.0.25] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-3.5.0-21-generic »
make: *** [compile] Erreur 2

***************************************************************************
*  alsa-driver-1.0.25 make failed
***************************************************************************


I used the script posted by binloan, download part was OK...

---

### Post by nochtavio on 2013-01-06
> **MikesFrance said:**
> Having this "only HDMI output" problem with Ubuntu 12.10, I tried the script, but it seems to fail on the compilation part.



I used the script posted by binloan, download part was OK...

I've got this error also while compiling.

And it seems alsa completely gone in my netbook instead after using this script. Tried reinstalling alsa, but still gone.

---

### Post by Enigmapond on 2013-01-28
Thank you once again. The new script works great!

Cheers!):P

---

### Post by antirem on 2013-01-29
After runnning:
```
sudo ./AlsaUpgrade-1.0.25-3.sh -c
```

I get:
```
[...]
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/iso-resources.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/packets-buffer.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/fcp.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/cmp.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/amdtp.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/speakers.o
In file included from /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/speakers.c:5:0:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c: In function &#8216;fwspk_card_free&#8217;:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c:664:2: error: implicit declaration of function &#8216;fw_device_put&#8217; [-Werror=implicit-function-declaration]
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c: In function &#8216;fwspk_probe&#8217;:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c:721:2: error: implicit declaration of function &#8216;fw_device_get&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/speakers.o] Error 1
make[2]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire] Error 2
make[1]: *** [_module_/opt/Alsa-1.0.25/alsa-driver-1.0.25] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-22-generic'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.25 make failed
***************************************************************************
mae@mae:~/Desktop/alas$ 

```

Can anyone see what I'm doing wrong? Thanks!

edit: I'm on 12.10 64 bit.

---

### Post by Shogun7 on 2013-02-09
I keep getting the same speaker.o error too & I'm on 12.10 64 bit as well

edit:  I got it working...installed 12.04 64 bit, added medibuntu repo, and downloaded the alsa firmware

---

### Post by brisingrkill on 2013-02-15
am getting tis error on 1.0.25

```
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/vx'
make[2]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers'
make[2]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/ad1816a'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/ad1816a'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/ad1848'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/ad1848'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/cs423x'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/cs423x'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/es1688'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/es1688'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/galaxy'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/galaxy'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/gus'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/gus'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/msnd'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/msnd'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/opti9xx'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/opti9xx'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
Hunk #2 succeeded at 713 (offset 3 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/sb'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
Hunk #2 succeeded at 252 (offset -2 lines).
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
Hunk #2 succeeded at 1948 (offset 2 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/wavefront'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/wss'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa/wss'
make[2]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/isa'
make[2]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/synth'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/synth/emux'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/synth/emux'
make[2]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/synth'
make[2]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci'
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
Hunk #2 succeeded at 1680 (offset 9 lines).
Hunk #3 succeeded at 1725 (offset 9 lines).
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
Hunk #2 succeeded at 1313 (offset 6 lines).
Hunk #3 succeeded at 1356 (offset 6 lines).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #2 succeeded at 844 (offset -2 lines).
Hunk #3 succeeded at 998 (offset -2 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #2 succeeded at 3135 (offset -41 lines).
Hunk #3 succeeded at 3431 (offset -40 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #2 succeeded at 2136 (offset 5 lines).
Hunk #3 succeeded at 2512 (offset 5 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
Hunk #3 succeeded at 1217 (offset 5 lines).
Hunk #4 succeeded at 1427 (offset 16 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #2 succeeded at 2678 (offset 82 lines).
Hunk #3 succeeded at 2871 (offset 89 lines).
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #2 succeeded at 2514 (offset 20 lines).
Hunk #3 succeeded at 2524 (offset 20 lines).
Hunk #4 succeeded at 2539 (offset 20 lines).
Hunk #5 succeeded at 2550 (offset 20 lines).
Hunk #6 succeeded at 2561 (offset 20 lines).
Hunk #7 succeeded at 2644 (offset 20 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
Hunk #2 succeeded at 1187 (offset 7 lines).
Hunk #3 succeeded at 1247 (offset 7 lines).
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #3 succeeded at 1943 (offset 16 lines).
Hunk #4 succeeded at 1955 (offset 16 lines).
Hunk #5 succeeded at 1979 (offset 16 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ac97'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #2 succeeded at 2148 (offset -57 lines).
Hunk #3 succeeded at 2318 (offset -57 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ali5451'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/asihpi'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/asihpi'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 340 (offset -1 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/au88x0'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/aw2'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/aw2'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #3 succeeded at 1686 (offset 123 lines).
Hunk #4 succeeded at 1958 (offset 133 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ca0106'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/cs46xx'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/cs46xx'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/cs5535audio'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/cs5535audio'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ctxfi'
copying file alsa-kernel/pci/ctxfi/ctatc.c
patching file ctatc.c
Hunk #2 succeeded at 1272 (offset 24 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ctxfi'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1947 (offset 4 lines).
Hunk #2 succeeded at 2019 (offset 4 lines).
Hunk #3 succeeded at 2254 (offset 3 lines).
Hunk #4 succeeded at 2264 (offset 5 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
copying file alsa-kernel/pci/echoaudio/indigodjx.c
patching file indigodjx.c
Hunk #2 succeeded at 112 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/indigoiox.c
patching file indigoiox.c
Hunk #2 succeeded at 114 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
Hunk #2 succeeded at 125 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/echoaudio'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #2 succeeded at 68 (offset 1 line).
Hunk #3 succeeded at 674 (offset 1 line).
Hunk #5 succeeded at 1461 (offset 8 lines).
Hunk #6 succeeded at 1788 (offset 24 lines).
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 941 (offset 1 line).
Hunk #3 succeeded at 1634 (offset 6 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/emu10k1'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/hda'
copying file alsa-kernel/pci/hda/hda_intel.c
patching file hda_intel.c
Hunk #4 succeeded at 2603 (offset -1 lines).
Hunk #5 succeeded at 2619 (offset -1 lines).
Hunk #6 succeeded at 2635 (offset -1 lines).
Hunk #7 succeeded at 2648 (offset -1 lines).
Hunk #8 succeeded at 2679 (offset -1 lines).
Hunk #9 succeeded at 2802 (offset -1 lines).
copying file alsa-kernel/pci/hda/hda_beep.c
patching file hda_beep.c
Hunk #2 succeeded at 96 (offset 1 line).
Hunk #3 succeeded at 124 (offset 1 line).
Hunk #4 succeeded at 142 (offset 1 line).
Hunk #5 succeeded at 164 (offset 1 line).
Hunk #6 succeeded at 283 (offset 1 line).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/hda'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ice1712'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ice1712'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #2 succeeded at 2344 (offset 5 lines).
Hunk #3 succeeded at 2500 (offset 5 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/korg1212'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/lola'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/lola'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/lx6464es'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/lx6464es'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/mixart'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/mixart'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/nm256'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/nm256'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/oxygen'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/oxygen'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/pcxhr'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/pcxhr'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/pdplus'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/pdplus'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #3 succeeded at 2227 (offset 9 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/riptide'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/rme9652'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/rme9652'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/trident'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/trident'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/vx222'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/vx222'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
Hunk #2 succeeded at 2039 (offset 13 lines).
Hunk #3 succeeded at 2059 (offset 13 lines).
Hunk #4 succeeded at 2399 (offset 13 lines).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci/ymfpci'
make[2]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pci'
make[2]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa/codecs'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa/codecs'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa/core'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa/core'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa/fabrics'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa/fabrics'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa/soundbus'
make[4]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa/soundbus'
make[2]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/aoa'
make[2]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc'
copying file alsa-kernel/soc/soc-core.c
patching file soc-core.c
Hunk #3 succeeded at 1673 (offset 2 lines).
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/atmel'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/atmel'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/au1x'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/au1x'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/blackfin'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/blackfin'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/codecs'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/codecs'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/davinci'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/davinci'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/ep93xx'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/ep93xx'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/fsl'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/fsl'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/imx'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/imx'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/jz4740'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/jz4740'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/kirkwood'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/kirkwood'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/mid-x86'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/mid-x86'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/mxs'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/mxs'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/nuc900'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/nuc900'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/omap'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/omap'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/pxa'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/pxa'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/s6000'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/s6000'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/samsung'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/samsung'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/sh'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/sh'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/tegra'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/tegra'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/txx9'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc/txx9'
make[2]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/soc'
make[2]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/usb'
copying file alsa-kernel/usb/card.c
patching file card.c
copying file alsa-kernel/usb/endpoint.c
patching file endpoint.c
Hunk #2 succeeded at 73 (offset 1 line).
Hunk #3 succeeded at 88 (offset 1 line).
Hunk #4 succeeded at 172 (offset 1 line).
Hunk #5 succeeded at 199 (offset 1 line).
Hunk #6 succeeded at 352 (offset 1 line).
copying file alsa-kernel/usb/helper.c
patching file helper.c
copying file alsa-kernel/usb/quirks.c
patching file quirks.c
Hunk #3 succeeded at 238 (offset -1 lines).
Hunk #4 succeeded at 344 (offset -1 lines).
Hunk #5 succeeded at 362 (offset -1 lines).
Hunk #6 succeeded at 376 (offset -1 lines).
Hunk #7 succeeded at 389 (offset -1 lines).
Hunk #8 succeeded at 398 (offset -1 lines).
Hunk #9 succeeded at 415 (offset -1 lines).
copying file alsa-kernel/usb/midi.c
patching file midi.c
Hunk #2 succeeded at 250 (offset 2 lines).
Hunk #3 succeeded at 278 (offset 2 lines).
Hunk #4 succeeded at 392 (offset 2 lines).
Hunk #5 succeeded at 1036 (offset 18 lines).
Hunk #6 succeeded at 1135 (offset 25 lines).
Hunk #7 succeeded at 1152 (offset 25 lines).
Hunk #8 succeeded at 1162 (offset 25 lines).
Hunk #9 succeeded at 1887 (offset 27 lines).
Hunk #10 succeeded at 2276 (offset 38 lines).
copying file alsa-kernel/usb/mixer.c
patching file mixer.c
Hunk #2 succeeded at 104 (offset -26 lines).
Hunk #3 succeeded at 2120 (offset 97 lines).
Hunk #4 succeeded at 2213 (offset 116 lines).
copying file alsa-kernel/usb/mixer_quirks.c
patching file mixer_quirks.c
Hunk #2 succeeded at 68 (offset 5 lines).
copying file alsa-kernel/usb/stream.c
patching file stream.c
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/usb/6fire'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/usb/6fire'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/usb/caiaq'
copying file alsa-kernel/usb/caiaq/audio.c
patching file audio.c
Hunk #2 succeeded at 614 (offset 150 lines).
Hunk #3 succeeded at 693 (offset 166 lines).
copying file alsa-kernel/usb/caiaq/device.c
patching file device.c
copying file alsa-kernel/usb/caiaq/input.c
patching file input.c
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/usb/caiaq'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/usb/misc'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/usb/misc'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
Hunk #2 succeeded at 33 (offset 1 line).
Hunk #3 succeeded at 56 (offset 1 line).
Hunk #4 succeeded at 142 (offset 1 line).
Hunk #5 succeeded at 181 (offset 1 line).
Hunk #6 succeeded at 237 (offset 1 line).
Hunk #7 succeeded at 290 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #2 succeeded at 70 (offset 2 lines).
Hunk #3 succeeded at 318 (offset 2 lines).
Hunk #4 succeeded at 351 (offset 2 lines).
Hunk #5 succeeded at 367 (offset 2 lines).
Hunk #6 succeeded at 393 (offset 2 lines).
Hunk #7 succeeded at 409 (offset 2 lines).
Hunk #8 succeeded at 526 (offset 2 lines).
Hunk #9 succeeded at 549 (offset 2 lines).
Hunk #10 succeeded at 698 (offset 2 lines).
Hunk #11 succeeded at 1062 (offset 2 lines).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
Hunk #2 succeeded at 153 (offset 1 line).
Hunk #3 succeeded at 233 (offset 1 line).
Hunk #4 succeeded at 267 (offset 1 line).
Hunk #5 succeeded at 307 (offset 1 line).
Hunk #6 succeeded at 328 (offset 1 line).
Hunk #7 succeeded at 454 (offset 1 line).
Hunk #8 succeeded at 482 (offset 1 line).
Hunk #9 succeeded at 715 (offset 1 line).
Hunk #10 succeeded at 728 (offset 1 line).
Hunk #11 succeeded at 803 (offset 1 line).
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/usb/usx2y'
make[2]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/usb'
make[2]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pcmcia'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pcmcia/pdaudiocf'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pcmcia/pdaudiocf'
make[3]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pcmcia/vx'
make[3]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pcmcia/vx'
make[2]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/pcmcia'
make[2]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/misc'
make[2]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/misc'
make[2]: Entering directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire'
copying file alsa-kernel/firewire/cmp.c
patching file cmp.c
copying file alsa-kernel/firewire/iso-resources.c
patching file iso-resources.c
Hunk #2 succeeded at 17 (offset 1 line).
Hunk #3 succeeded at 31 (offset 1 line).
Hunk #4 succeeded at 52 (offset 1 line).
Hunk #5 succeeded at 141 (offset 1 line).
Hunk #6 succeeded at 200 (offset 1 line).
Hunk #7 succeeded at 242 (offset 1 line).
make[2]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire'
make[1]: Leaving directory `/opt/Alsa-1.0.25/alsa-driver-1.0.25'
make -C /usr/src/linux-headers-3.5.0-23-generic SUBDIRS=/opt/Alsa-1.0.25/alsa-driver-1.0.25  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/hrtimer.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/hwdep.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/memory_wrapper.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/memalloc.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/sgbuf.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm_native.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm_lib.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm_timer.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm_misc.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/pcm_memory.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/rawmidi.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/timer.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/wrappers.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/misc_driver.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/sound.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/init.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/memory.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/info.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/control.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/misc.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/device.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/isadma.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/vmaster.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/ctljack.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/jack.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/snd.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/snd-hwdep.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/snd-timer.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/snd-hrtimer.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/snd-pcm.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/snd-page-alloc.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/snd-rawmidi.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_device.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_dummy.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_midi_emul.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_midi_event.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_virmidi.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_lock.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_clientmgr.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_memory.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_queue.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_fifo.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_prioq.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_timer.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_system.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_ports.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/seq_info.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/snd-seq.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/snd-seq-device.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/snd-seq-dummy.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/snd-seq-virmidi.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/snd-seq-midi-event.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/acore/seq/snd-seq-midi-emul.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/aloop.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/dummy.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/mtpav.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/mts64.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/portman2x4.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/serial-u16550.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/virmidi.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/snd-dummy.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/snd-aloop.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/snd-virmidi.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/snd-serial-u16550.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/snd-mtpav.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/snd-mts64.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/snd-portman2x4.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/mpu401/mpu401_uart.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/mpu401/mpu401.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/mpu401/snd-mpu401-uart.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/mpu401/snd-mpu401.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/opl3/opl3_lib.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/opl3/opl3_synth.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/opl3/snd-opl3-lib.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/pcsp/pcsp.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/pcsp/pcsp_lib.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/pcsp/pcsp_mixer.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/pcsp/pcsp_input.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/pcsp/snd-pcsp.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/vx/vx_core.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/vx/vx_hwdep.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/vx/vx_pcm.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/vx/vx_mixer.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/vx/vx_cmd.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/vx/vx_uer.o
  LD [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/drivers/vx/snd-vx-lib.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/lib.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/iso-resources.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/packets-buffer.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/fcp.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/cmp.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/amdtp.o
  CC [M]  /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/speakers.o
In file included from /opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/speakers.c:5:0:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c: In function ‘fwspk_card_free’:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c:664:2: error: implicit declaration of function ‘fw_device_put’ [-Werror=implicit-function-declaration]
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c: In function ‘fwspk_probe’:
/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c:721:2: error: implicit declaration of function ‘fw_device_get’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire/speakers.o] Error 1
make[2]: *** [/opt/Alsa-1.0.25/alsa-driver-1.0.25/firewire] Error 2
make[1]: *** [_module_/opt/Alsa-1.0.25/alsa-driver-1.0.25] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.25 make failed
***************************************************************************

```

will try 1.0.24

---

### Post by Yellow Pasque on 2013-02-15
I'm guessing that the 1.0.25 alsa-kernel tarball is too old to work on Ubuntu 12.10 (and Ubuntu 12.10 already has a newer version of ALSA anyway, so I'm not sure why people are trying to "upgrade").

---

### Post by kelargo on 2013-02-22
I have a EMU-1212m  v1 card and the latest 12.10 new install of Ubuntu Studio.

The card gets recognized as a snd-emu10k1 device. 

In alsamixer, I can see the ADAT channels appear. The displayed name of the card is "emu-1010"  not "emu-1212"

When I go into jack, the extra input channels are not available and I get an error. Something is not quite correct in how the alsa module is getting loaded. 

[http://ubuntuforums.org/showthread.php?t=2118643](http://ubuntuforums.org/showthread.php?t=2118643)

---

### Post by Yellow Pasque on 2013-02-22
> **kelargo said:**
> I have a EMU-1212m  v1 card and the latest 12.10 new install of Ubuntu Studio.

The card gets recognized as a snd-emu10k1 device. 

In alsamixer, I can see the ADAT channels appear. The displayed name of the card is "emu-1010"  not "emu-1212"

When I go into jack, the extra input channels are not available and I get an error. Something is not quite correct in how the alsa module is getting loaded. 

[http://ubuntuforums.org/showthread.php?t=2118643](http://ubuntuforums.org/showthread.php?t=2118643)
None of that seems relevant to this thread...

In fact, I'm going to request this thread be closed because it's impossible to manage without being able to edit the OP (which I'm unable to do for some reason). The script has lost relevancy in newer Ubuntu releases anyway. In most cases, there is a better way to upgrade ALSA (using ALSA hda dkms or a newer kernel).

---

### Post by cariboo on 2013-02-22
Closed by request.

---

