---
title: "How to get your TV cards working under ubuntu 9.04, 9.10 and later."
date: 2009-11-08
forum: Tutorials
---

### Post by Hugh Mulqueen on 2009-11-08
Just like to say thanks to VirtualFab for the help on the mounting with options. You saved me hours of searching the internet. Sound.

1. Check dmesg for the TV card you are using.
        
**dmesg | grep bttv0**
      
[   10.679237] bttv0: Bt878 (rev 17) at 0000:03:06.0, irq: 20, latency: 32,
mmio: 0xfdcff000
                      detected: Hauppauge WinTV [card=10], **PCI subsystem ID is 0070:13eb**
[   10.679281] bttv0: 0070:13eb
[   10.679284] bttv0: using: Hauppauge (bt878) [**card=10**,autodetected]
[   10.679319] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   10.681808] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   10.713248] bttv0: Hauppauge eeprom indicates model#44805
    10.713250] bttv0: **tuner absent**
[
[   10.713253] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   10.713788] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   10.714324] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   10.732527] bttv0: registered device video0
[   10.732580] bttv0: registered device vbi0
[   10.732613] bttv0: PLL: 28636363 => 35468950 .. ok


2. If your card is detected correctly you should have the card number and the tuner number. My card number is 10, The device number is 0070:13eb. 

```
Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb. 
```

My card was correctly detected and the tuner was not as highlighted. If your card was not detected google the device number....... (or to be really technical the PCI subsystem ID).

NOTE: You can find the card and tuner numbers at the following websites:
(Before you ask the numbers that you take are the ones that start with a zero; ie tuner=0 - Temic
PAL (4002 FH5) )

Card numbers for bttv:

[http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv")

Tuner numbers are at:

[http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.tuner]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.tuner")

3. To find out the tuner number you first have to find out the make and model. To do that run the following command:

**dmesg | grep tuner**

I got the following output:

```
[     10.713237] tveeprom 1-0050: tuner model is TCL 2002MI_3H (idx 98, type 4)
[     10.713250] bttv0: tuner absent
```

4. Now comes the hard part. trawling through the internet to find what your looking for. Google is your friend in this step. I googled both tveeprom 1-0050 and TCL 2002MI_3H and found on the following from an arcive during the development of the driver.

[http://lists-archives.org/video4linux/15830-tcl-2002mi_3h-tuner-chip.html]("http://lists-archives.org/video4linux/15830-tcl-2002mi_3h-tuner-chip.html")

5. From the article I can see that I need to set the tuner number to 55 if I have no radio and 37 if I have a radio. I have to unload the bttv0 and the tuner modules first (if it's loaded) with the following command:
[B]
sudo rmmod bttv[/B]

6. Next I have to set the device numbers ( the card number and the tuner number ). With the following command:

**sudo modprobe bttv card=10 tuner=55**

7. To automate the commands create a file in /etc/modules.d called bttv.conf or something like that with the following command:

**sudo gedit /etc/modules.d/bttv.conf**

8. Then all you do is paste the following lines into the file:
```

options bttv card=10 tuner=55
```

And thats it!!!

Now I'm going to explain how to watch TV; The program that I like to use is Tvtime. You can get it
by typing:

**sudo apt-get install tvtime**

The installer will ask you whether you use PAL or NTSC and what part of the world you are.

1. Go to Applications > Sound & Video > Tvtime Television Viewer to launch the application.

2. Left click the screen > Channel Management > Disable signal detection.

3. Surf through the channels by pressing 1 [Enter], 2 , 3 etc....

4. When you find a channel you can fine tune it by going to Channel Management > Finetune Current Channel.

5. You can rename the channel numbers by going to Channel Management > Rename current channel.

6. Sit back relax and watch a bit of telly. :popcorn:
[B][I]
If there is anybody that has any trouble understanding the instructions or would like to edit them please post below.[/I][/B]

---

### Post by Xcoder on 2009-11-08
Thank you so much :), I'll test this soon.

---

### Post by Hugh Mulqueen on 2010-11-25
The ubuntu team fixed this bug in the LTS version. And they reversed the thing in Ubuntu 10.10. Theyr'e flippers. I'm going to post a bug report. And hopefully there going to fix it this time...
Anybody having the same problem post here...

---

### Post by Hugh Mulqueen on 2010-11-27
I think the last post is SPAM so can anybody confirm this?

---

### Post by Hugh Mulqueen on 2012-11-04
UPDATE: How to get your TV card working under ubuntu 12.04,12.10 and later and how to get sound working in TVtime.

Small edit: 
**Step 7.**
**sudo gedit /etc/modprobe.d/bttv.conf**

**Step 8.**
Etc...

Due to the ubuntu devs updating the system the old OSS driver for tvtime doesn't work anymore. 

Step 1.
**sudo gedit /etc/tvtime/tvtime.xml**

Step 2. 
Find MixerDevice in the file. (Ctrl+f will bring up the find box)

Step 3.
You will see the following line:
```
<!--
    This sets the mixer device and channel to use.  The format for OSS
    is device name:channel name.  Valid OSS channels are:
      vol, bass, treble, synth, pcm, speaker, line, mic, cd, mix, pcm2,
      rec, igain, ogain, line1, line2, line3, dig1, dig2, dig3, phin,
      phout, video, radio, monitor
    The format for ALSA mixer is device/channel (e.g., "default/Line"
    or "hw:0/CD")
   -->
  ** <option name="MixerDevice" value="default/Line"/>**
```

Edit the above line in bold, replace **"default/Line"** with [B]"hw:0/Line"
[/B]

Step 4. 
Save the file and restart TvTime if you havn't already done so.

Step 5.
Enjoy tvtime!!!

P.S. If you want my tvtime.xml you can find it here:
[URL="http://pastebin.com/JtwwaMhE"]http://pastebin.com/JtwwaMhE
[/URL]


Another thing Just downloaded this new program remuco-tvtime. Looks very good give it a go its a great way of turning your android device into a tvtime remote.

**sudo apt-get install remuco-tvtime**

Thats it off you go!!!:popcorn:

---

