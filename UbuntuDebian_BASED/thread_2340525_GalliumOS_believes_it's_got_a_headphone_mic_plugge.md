---
title: "GalliumOS believes it's got a headphone mic plugged in when it doesn't"
date: 2016-10-19
forum: Ubuntu/Debian BASED
---

### Post by Ivo_Degn on 2016-10-19
Hello community!
I've been trying to solve this issue for 2 months now and can't figure it out alone. Been going through every solution I found on the web and it didn't work.

I'm using GalliumOS on a Toshiba Chromebook 2. A while ago I began having difficulties using my microphone, every now and then it wouldn't work. Rebooting would usually fix it. It was in the beginning related with a certain set of headphones I used, though I don't know what caused the problem exactly.
In pulseaudio Input Devices the Port only has the option "Headset Microphone (unplugged)" even if the headset is not plugged in. I should be able to select byt-max98090, but the option doesn't show up. 
If I use zoom for conference calls, the internal options allow me to set byt-max instead of the non-existing Headset Microphone.

I've been reinstalling alsa, pavucontrol, using different headsets, not using headsets. 

I'd really appreciate some help here :)

Thanks!
Ivo

---

### Post by jeremy31 on 2016-10-19
Moved to Ubuntu/Debian based

---

### Post by neu5eeCh on 2016-10-20
Probably won't be able to help you, but is it possible this is a hardware problem? 

In case you haven't already done it, one way to gather evidence might be to run one or two distros (not Ubuntu based) in live mode. See if they also give you troubles. If they do, I would strongly point the finger at the hardware.

Is there a way for you to test USB mic and headphone?

---

### Post by Ivo_Degn on 2016-10-21
Thanks for moving and thanks for the answer.
No, the microphone does work, occasionally in skype and hangouts, always in zoom.us, so I think it's about the settings. I also just discovered that after it's been used in zoom, the microphone works (little blue bar in Input Devices in pavucontrol moves when I speak), though the setting is still Headphone Mic.

---

### Post by neu5eeCh on 2016-10-22
I still have an HP DV1000 32bit laptop that I love. It's one of the best laptops I've ever owned and my kids and I continue to use it. It remains fast and reliable. Abandoning Windows XP, I put Ubuntu 8.04 (way back when). It would be another 4 years before I finally got the microphone to work. The solution just magically appeared one day. I doubt it will be of any help to you, but it might set you off in the right direction? Here it is, copied and unedited from my Tomboy notes:

[http://ubuntuforums.org/showthread.php?t=2018599](http://ubuntuforums.org/showthread.php?t=2018599)

How to make hp dv1000 Mic work under Ubuntu 12.04
How to make hp dv1000 Mic work under Ubuntu 12.04

You need options snd-hda-intel model=auto enable=yes
in the last line of sudo gedit /etc/modprobe.d/alsa-base.conf

For Newbies, you can go directly to below "Tutorial Begin here."
and those that do not understand the above 2 lines
and those who has other brands and models
please read on.

I made this tutorial from

[https://answers.launchpad.net/ubuntu...uestion/202049](https://answers.launchpad.net/ubuntu...uestion/202049) which link to
[http://askubuntu.com/questions/75828...ne-not-working](http://askubuntu.com/questions/75828...ne-not-working)

Thanks actionparsnip (andrew-woodhead666) very much for the Answer.

dv1000, ( dv1729tu ) has succesfully working external mic jack.
Confirm with 12.04 fresh installed,
(after test succesful with 2 partitions of old-"staled" installed 12.04,
I decide to do fresh install to proof the tutorial)

10.04 Lts (in another partition of my dv1000) is not working at all,
even though using the same procedure.
Mic is still not working under Ubuntu 10.04.

******* If any can get it work please help report it here ************************
==============================================

Please note other brands and models should not use this tutorial as it is,
especially in NO.2 step.
Please look into
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
for more info on this issue.

Each brand of computer and each models need different "codes" to add to the last line,
or it may need to put "#", to disable codes, in front of certain "lines of codes" to get the microphone or speakers to work.
Or even it may need to do other "ways".

Please search in Google for your specific models if you have problems with these kinds.

When you are face bad luck that Ubuntu will not work out of the box.

To get help, best one on this Alsa sound issue

[https://answers.launchpad.net/ubuntu...ce/alsa-driver](https://answers.launchpad.net/ubuntu...ce/alsa-driver)
Steps to get help.

1. Register to the launchpad first
2. Login
3. Key in your question in the question box on the left upper conner.
4. give it 1-2 days someone should come in and help.

But [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php) where you are now,
is also very good place to search for previous samples of solutions,
but to get the fastest help it seem to be
[https://answers.launchpad.net/ubuntu...ce/alsa-driver](https://answers.launchpad.net/ubuntu...ce/alsa-driver)
================================================== ==================
links that may help you solve your problems on sound issue for Ubuntu
[https://answers.launchpad.net/ubuntu...ce/alsa-driver](https://answers.launchpad.net/ubuntu...ce/alsa-driver)
[http://askubuntu.com/questions/75828...ne-not-working](http://askubuntu.com/questions/75828...ne-not-working)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
[https://help.ubuntu.com/community/So...otingProcedure](https://help.ubuntu.com/community/So...otingProcedure)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[https://help.ubuntu.com/community/So...roubleshooting](https://help.ubuntu.com/community/So...roubleshooting)

================================================== ==================
Tutorial Begin here.

Before you continue, please test your external Mic first,
prefered dual boot windows on the same machine.
So we know for sure that the sound hardware of the computer and the microphone work 100%.

1. Open Terminal
(Click on "Dash Home" just key in T in the pop up search box, you will see Black Terminal icon)

key in or select copy and paste the following command line, into Terminal and press ENTER

sudo gedit /etc/modprobe.d/alsa-base.conf


Youe will be prompt to put pass word then,
you will have new pop up window with.(I highlighted the last 2 lines in blue)......>


# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
.............
..............
(I ommited these lines of codes to shorten the display samples).......
,,,,,,,,,,,,,,,,,,
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
==============================================

2. Sample vedio for this step.

The Youtube "How to fix not working microphone in Ubuntu 10.04"
[I]But do not use his full details,
but use the No.2 step in my tutorial instead for hp dv1000
And for my Ubuntu 10.04 it did not work at all for my hp dv1000
and you must do No.4 and No.5 step which are not in vedio,
so the video is just sample how to do step 2 only/I]
[http://www.youtube.com/watch?v=tULmqpe5Yos](http://www.youtube.com/watch?v=tULmqpe5Yos)

just add the following line

options snd-hda-intel model=auto enable=yes

to the last line of the "alsa-base.conf",

so you will have below, take notice of the last line in Red follow the previous last blue lines............>

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
.............
..............
(I ommited these lines of codes to shorten the display samples).......
,,,,,,,,,,,,,,,,,,
...............................
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=auto enable=yes
====================================
3. Click "Save" on Gedit Menu (Text Editor Menu)
4. and then REBOOT
======================================
After reboot.

5. go to "System Setting" and then double click on "Sound".

then Click on INPUT. TAB and "Unmute" the LINE IN.

MICROPHONE JACK is for external microphone so it is "LINE IN" as input port.
Microphone will not work if you leave this this LINE IN muted.


(I found it is muted by default, and many other confirm this in many posts in the ubuntuforum.org)
(How ever my "old-staled" installed Ubuntu 12.04, I did not have to unmute the Line IN,
it worked after the reboot, that may due to many experiments to solve the issues earlier)

For those who had install Classic Menu for Ubuntu 12.04,
you have to click the arrow on the right hand side of the "Choice Box" and choose Line IN,
instead of Microphone and Click UNMUTE Line IN.
(It should show Microphone in the "Choice Box" by defaut.)

NOW click on Sound Recorder , or install Skype and try to record the sound from the external mic.
IT SHOULD WORK.

=======================================
This tutorial is for Ubuntu 12.04 with "hp dv1000"
iF YOU HAVE other models please do "GOOGLE"

---

