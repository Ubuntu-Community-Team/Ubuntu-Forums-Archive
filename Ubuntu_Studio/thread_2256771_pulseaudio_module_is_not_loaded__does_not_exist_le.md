---
title: "pulseaudio module is not loaded / does not exist leading to no sound from android"
date: 2014-12-14
forum: Ubuntu Studio
---

### Post by alsdkjhf23465 on 2014-12-14
Hi all,
I am trying to route audio from my android phone, to my ubuntu studio pc. 
The pc services offered correctly and are scanned by my phone; ie my phone sees the pc as an *audio sink*.
So it can pair, connect and play audio through the pc, BUT I hear no sound and the reason is there is no bluetooth device showing up in pulseaudio control.
indeed 

[INDENT][FONT=Lucida Console]
pactl list short modules | grep blue
9       module-bluetooth-policy[/FONT][/INDENT]

shows that the module **module-bluetooth-discover** that everyone talks about is not there. 
syslog says that it is actually there but does not load due to some error
[INDENT][FONT=Lucida Console]
Dec 14 12:38:47 starmaze pulseaudio[2663]: [pulseaudio] module-bluetooth-device.c: /org/bluez/942/hci0/dev_50_32_75_B3_DA_31 is not a valid BlueZ audio device.
Dec 14 12:38:47 starmaze pulseaudio[2663]: [pulseaudio] module.c: Failed to load module "module-bluetooth-device" (argument: "path=/org/bluez/942/hci0/dev_50_32_75_B3_DA_31 address=50:32:75:B3:DA:31 profile=a2dp_source source_properties=device.icon_name=blueman card_properties=device.icon_name=blueman"): initialization failed.[/FONT][/INDENT]

I have also asked in askubuntu.com. Here is the full length of the question and all the references I have come across [http://askubuntu.com/questions/561233/bluetooth-does-not-appear-in-pulseaudio-as-a-possible-source-sink]("http://askubuntu.com/questions/561233/bluetooth-does-not-appear-in-pulseaudio-as-a-possible-source-sink"), but I have not found a solution yet. 

Do you have any Idea what is going on?

---

### Post by ub-newbie on 2015-11-07
I just got my Android Tablet sending audio from Pandora thru the PC to the stereo. I'm on 12.04 (x64) using GDM.
Let me see if I can help.

A few questions:  

1.  in "**/etc/bluetooth/audio.conf**" do you have "**enable=gateway,source**"

2. did you edit "**/etc/pulse/default.pa**" - remove the comments around "**module-bluetooth-discover**"

3. You might try manually loading 'bluetooth-discover' and 'loopback' modules.  
On my system the command is:  
"*pactl load-module module-loopback source=bluez_source.XX_XX_XX_XX_XX_XX sink=combined*"
(the XX's represent the MAC of my tablets BT - can be seen using "**d-feet**" (a GUI program), 
and I am sending the audio to the 'combined' sink)

You can see your available sinks using "*pacmd*" then "*list-sinks*"  (you can also see sources with "*list-sources*"

3.  run "*pactl list | grep bluetooth*" & "*pactl list | grep loopback*" to see if everything is loaded correctly 

When I look in '*PulseAudio Volume Control*":
Input Devices : Tablet  (I see audio levels jumping)
Output Devices: Simultaneous output to Build-in Audio (I see audio levels jumping)
Configuration: Table, Profile = A2DP

Hope this helps.  I have it running now, but it won't survive a reboot..
Problems I still have not fixed.  Automatic loading of the 'loopback' module. - Also, only works for my Tablet

---

