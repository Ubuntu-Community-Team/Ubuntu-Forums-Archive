---
title: "setting up zoneminder and a conexant 878a card"
date: 2014-05-14
forum: Server Platforms
---

### Post by hong2221 on 2014-05-14
I've been trying to set up zoneminder on my one computer but I believe my capture card isn't properly installed or have the right parameters. I tried to manually define a card type the bttv configuration file but it isn't working properly. Suggestions?

the system I'm running is a Pentium 4, 2gb ram, Conexant 878A 8-Port Video Capture Card, and 4 cameras hooked up right now. I got two HD, one SATA 1tb, another is IDE 120 GB. I have Ubuntu 12.04 32bit server edition installed on the 120 GB. I did the Ubuntu Server 12.04 64-bit with Zoneminder 1.27 the easy way install guide. 

I'm able to get into my serverip/zm but I can't seem to good video. All three of my cameras a flickering or showing a blue screen.

---

### Post by dannyboy79 on 2014-05-14
can you link to the guide you used to install zoneminder please. 

also, can you attach dmesg output. run the ```
dmesg > dmesg.txt
``` command in a terminal so that it spits the output into a text file, then open pastebin or other similar website and post all the output there and then come here and paste the link. This prevents users from posting a ton of log information when it can just be hosted on pastebin. we can go from there once you post the requested information.

---

### Post by hong2221 on 2014-05-14
installation link: [http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_12.04_64-bit_with_Zoneminder_1.27_the_easy_way](http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_12.04_64-bit_with_Zoneminder_1.27_the_easy_way)

Also, I'm fairly new to using terminal commands on ubuntu server. How do I go about from sending that text file by email or sending it somewhere I can upload it? I'm so used to having a gui.

---

### Post by dannyboy79 on 2014-05-15
ah, that's right you don't have a GUI. There's a command line tool that I use to upload text to pastebin, it's called pastebinit. To install it you would issue
```
sudo apt-get install pastebinit
```
and then to use it just issue something like the following
```
cat dmesg.txt | pastebinit
```
and that will result in a link that can be copied and pasted onto the forums here. I am not sure but based on what I am reading on the pastebinit ubuntu webpage, you may even be able to skip the step of first outputting the dmesg command into a text file and you may be able to just run the following
```
dmesg | pastebinit
```

On a side note, if you're used to using a GUI you could always install a really lightweight desktop manager like openbox or similar. On my server i run xubuntu personally.

---

### Post by hong2221 on 2014-05-26
> **dannyboy79 said:**
> ah, that's right you don't have a GUI. There's a command line tool that I use to upload text to pastebin, it's called pastebinit. To install it you would issue
```
sudo apt-get install pastebinit
```
and then to use it just issue something like the following
```
cat dmesg.txt | pastebinit
```
and that will result in a link that can be copied and pasted onto the forums here. I am not sure but based on what I am reading on the pastebinit ubuntu webpage, you may even be able to skip the step of first outputting the dmesg command into a text file and you may be able to just run the following
```
dmesg | pastebinit
```

On a side note, if you're used to using a GUI you could always install a really lightweight desktop manager like openbox or similar. On my server i run xubuntu personally.

Hey thanks, sorry I was busy the past weeks. 

The link is
[http://paste.ubuntu.com/7522195](http://paste.ubuntu.com/7522195)

---

### Post by dannyboy79 on 2014-05-28
i see in your dmesg output you have a video device at /dev/video0 and /dev/video1, within zoneminder setup is that what you choose for the video devices? i'll have to take a look closer at the install guide you followed after work today.

also, here's some great tips for troubleshooting. [http://www.zoneminder.com/wiki/index.php/Troubleshooting](http://www.zoneminder.com/wiki/index.php/Troubleshooting)

---

### Post by hong2221 on 2014-06-01
i've tried a lot. i'm almost certain that i have to change the /etc/modprobe.d/bttv.config file... but it says read only and won't give me the permission to change it around. also i don't know the exact way to do this. help?

more info:
[http://bytebasket.com/index.php?option=com_content&view=article&id=82:configuring-zoneminder-on-ubuntu-1004&catid=45:how-to&Itemid=76](http://bytebasket.com/index.php?option=com_content&view=article&id=82:configuring-zoneminder-on-ubuntu-1004&catid=45:how-to&Itemid=76)

the vendor that I got the card from tells me "8-channel DVR surveillance video capture card features the conexant 878A chipset, PCI interface and supports composite input in PAL/NTSC formats at full D1 resolution.
SAME AS Hauppauge 1888 (OEM BY TEMPEST MICROSYSTEMS) - LINUX ONLY (NOT WINDOWS)"

Suggestions? I'm still having trouble editing and saving the bttv.conf file. It says I do not have the permission, so I did the gksudo gedit /etc/modprobe.d/bttv.conf file and it still doesn't let me. Any ideas?

---

### Post by dannyboy79 on 2014-06-02
gedit is a gui based text editor, you said you don't have a gui. you'll need to use nano or vi or vim, i suggest nano. so the command would be
```
sudo nano /etc/modprobe.d/bttv.conf
```
when done adding what you need to the file, hit ctrl+x to exit, click Y that you want to save your changes, and enter to save it to the same filename. that should be it, reboot your machine adn see if the bttv cards work now

---

### Post by hong2221 on 2014-06-02
^ yeah I used xfrce but it didnt allow me. using the sudo nano worked though. changing it to

options bttv card=0,0,0,0 tuner=4,4,4,4

doesn't work. when i do ls /dev it shows video0 and video1 and when i do ls pci i see bt787 card so what do you think i should try? I still see the same blue screen in my zoneminder. on channel 3, I see flickering signs of video.

---

### Post by hong2221 on 2014-06-02
double post. someone please delete this post. sorry

---

### Post by hong2221 on 2014-06-03
Interesting, one person says this card works with Windows 7 with another driver 

[http://www.cctvforum.com/viewtopic.php?t=25335](http://www.cctvforum.com/viewtopic.php?t=25335)

---

### Post by dannyboy79 on 2014-06-03
i would first find out if you're getting video from the raw device nodes, you can test with ```
cat /dev/video0 > video.ts
```
and then let that run for about 1 minute, then hit ctrl+c, that kills the command. then try to play the file on a machine that can play video files. if that works than it boils down to your config of zoneminder, if that results in a blue video again than you're config for your devices isn't right and Im not familiar with this card so i can't really help any further

---

### Post by hong2221 on 2014-06-05
> **dannyboy79 said:**
> i would first find out if you're getting video from the raw device nodes, you can test with ```
cat /dev/video0 > video.ts
```
and then let that run for about 1 minute, then hit ctrl+c, that kills the command. then try to play the file on a machine that can play video files. if that works than it boils down to your config of zoneminder, if that results in a blue video again than you're config for your devices isn't right and Im not familiar with this card so i can't really help any further


additional info from the vendor: 

This card is conexant BT878 aka BTTV and works with most versions of linux. The chip is still very popular although some of the documentation is not being updated anymore. Here is the original howto:

[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/BTTV.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/BTTV.html)

for ubuntu have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=153935](http://ubuntuforums.org/showthread.php?t=153935)

The unique feature of this card is that it has multiple Bt878 cards on board - it was originally used for a widely sold DVR product - you can download the software here:

[www.ftp3.net/downloads/tsunami-4.7.1.iso](www.ftp3.net/downloads/tsunami-4.7.1.iso)

---

### Post by hong2221 on 2014-06-05
> **dannyboy79 said:**
> i would first find out if you're getting video from the raw device nodes, you can test with ```
cat /dev/video0 > video.ts
```
and then let that run for about 1 minute, then hit ctrl+c, that kills the command. then try to play the file on a machine that can play video files. if that works than it boils down to your config of zoneminder, if that results in a blue video again than you're config for your devices isn't right and Im not familiar with this card so i can't really help any further

hey it's telling me that the resource is busy. what's in the way?

update- I got it but the video does not play. I've tried using smplayer and vlc.

I have also used vlc to try to stream from video0 and video1 and it does not work. so it's not the zoneminder config. suggestions?

---

### Post by dannyboy79 on 2014-06-06
from your dmesg report, it appears like your video1 isn't set up correctly. I see this for the first tuner
```
bttv: driver version 0.9.19 loaded
[   13.710148] bttv: using 16 buffers with 2080k (520 pages) each for capture
[   13.710721] bttv: Bt8xx card found (0)
[   13.710937] bttv: 0: Bt878 (rev 17) at 0000:03:0c.0, irq: 16, latency: 64, mmio: 0xfdbff000
[   13.710963] bttv: 0: subsystem: fe01:fcfd (UNKNOWN)
[   13.710969] bttv: 0: using: Tibet Systems 'Progress DVR' CS16 [card=131,insmod option]
[   13.711262] bttv: 0: tuner absent
[   13.711336] bttv: 0: Setting PLL: 28636363 => 35468950 (needs up to 100ms)
[   13.748098] bttv: PLL set ok
[   13.761893] bttv: 0: registered device video0
[   13.762187] bttv: 0: registered device vbi0
```

but the second card shows unkown device. I have no experience with bttv cards so I have no idea. I just would suggest that you get the cards working first before trying to get them to work in zoneminder. what are you connecting to the cards? i would think that matters.

---

