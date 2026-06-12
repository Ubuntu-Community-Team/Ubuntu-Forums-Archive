---
title: "old video"
date: 2008-09-25
forum: Ubuntu Studio
---

### Post by DarinB on 2008-09-25
I have old videos from school 26 years old how can i put them into my computer hardy heron.

---

### Post by aeiah on 2008-09-25
you'll need a video input device and a VCR. a video input device could just be a tv card. just plug the vcr in with the coax cable or s-video like you would in a tv and let videocapping software record it like it would record a tv channel. a better solution would probably to buy a proper video input device that's designed to be used for that sort of thing but they're usually more expensive and less versatile (ie, you can use your tv card to, well, watch tv too).

the other option includes just buying one of those combi devices that has a dvd recorder and vcr in one unit but that'd be a waste of money.

just make sure you get a compatible tv card / device. one that has s-video input or even component would be best, although i suspect the video quality will be limited by the VHS, not the transfer method.

---

### Post by DarinB on 2008-09-25
1 what tv card would be supported by hardy and which application do i use??

---

### Post by lisati on 2008-09-25
An alternative to a TV card which I sometimes use is a combo DVD recorder and VCR which I use to copy my old VHS tapes to DVD+/-RW - I can then import the DVD contents into whatever editing software I'm using at the time.

---

### Post by Crafty Kisses on 2008-09-25
I'm pretty sure Pinnacle had some software that did this and like a capture card, but I'm not sure if it will work with Ubuntu.

---

### Post by lisati on 2008-09-25
> **Codename said:**
> I'm pretty sure Pinnacle had some software that did this and like a capture card, but I'm not sure if it will work with Ubuntu.

The software I have from Pinnacle can use a capture card, but unfortunately it's Windows, and I haven't tried it with Ubuntu under Wine, so no thoughts here that would be of help to the OP. I also remember seeing somewhere that Pinnacle do offer capture cards: again I have no experience of using them with Ubuntu.

---

### Post by DarinB on 2008-09-26
wow it does seem complicated sending them out is a fortune, and maybe not worth it. whats the shelf life of vhs tapes???

---

### Post by cotcot on 2008-09-26
I have video tapes of about 15 years in pretty good shape. I bought a Hauppauge PVR 150 and searched how to capture the video. I keep my findings in a text file of which I put the PVR150 section in the quote below.
> Capture VHS with Hauppauge PVR150
The solution is to place the variable in /etc/environmentvlc will appear in your "Multimedia" packages list.* Click it to run it.* Use "File>Open Capture Device" and then click the "PVR" tab to get to your PVR settings.* Set "Norm" to "NTSC" (if you're in the USA, or "PAL" if Europe), and if you're using Channel 3 for the VCR output, then set the frequency to 61250.* Then click the "Advanced" button to open the rest of the needed settings.
What video input is my PVR150 currently using
As you probably already know, the PVR150 can capture off it's build in TV tuner (input 0), a SVIDEO source (input 1), or a COMPOSITE video source (input 2). You can always see what video input the PVR-150 is currently using by running the command:
v4l2-ctl -I
In which case you will probably see an output like this:
Video input : 0 (Tuner 1)
Step 2:Changing the capture input
To switch your PVR-150 to use the SVIDEO input run the command:
v4l2-ctl -i 1
If you are using the composite video input on your PVR-150 you will want to run:
v4l2-ctl -i 2
There are more inputs you can use. To get a listing of all of them and what number they correspond to run:
v4l2-ctl -n
If this sort of thing excites you you can find many more detail about v4l2-ctl at: [http://www.ivtvdriver.org/index.php/V4l2-ctl](http://www.ivtvdriver.org/index.php/V4l2-ctl)

In terminal 
cat /dev/video0 > test.mpg 
play deinterlaced
mplayer -vf pp=lb /dev/video0 


Hope this can help you.

---

### Post by Crafty Kisses on 2008-09-26
> **lisati said:**
> The software I have from Pinnacle can use a capture card, but unfortunately it's Windows, and I haven't tried it with Ubuntu under Wine, so no thoughts here that would be of help to the OP. I also remember seeing somewhere that Pinnacle do offer capture cards: again I have no experience of using them with Ubuntu.

Yeah to my knowledge people have mixed experiences with the Pinnacle software under Wine, some people say it works fine, but others say they have a lot of issues.

---

### Post by dabl on 2008-10-01
How To: This is a little old, but I think it's all still correct:

[http://kubuntuforums.net/forums/index.php?topic=3085164.0](http://kubuntuforums.net/forums/index.php?topic=3085164.0)

:)

---

### Post by aeiah on 2008-10-01
all you really need is a tvcard and a howto that tells you how to record tv programs, as its really the same signal. if you go down that route that is. as for compatible cards, i think mythtv will have the most extensive list of linux compatible cards, or perhaps you can find some good examples of ones that work under ubuntu out-of-the-box

---

