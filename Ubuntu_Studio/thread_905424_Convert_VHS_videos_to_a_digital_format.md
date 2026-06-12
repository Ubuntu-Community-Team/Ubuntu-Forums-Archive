---
title: "Convert VHS videos to a digital format"
date: 2008-08-30
forum: Ubuntu Studio
---

### Post by EpidemikE on 2008-08-30
Does anyone know of any tutorials or guides on how to do this on Ubuntu?

My specs are 2GB of ram, AMD X2 4400+ @2.3GHz, Asus M2A-VM HDMI mobo, AverMedia M780 PCI-E TV Tuner card.

I have all the necessary components except for the software to capture video but I don't know what software to use. I also am not sure on how to check and see if Ubuntu sees the tuner card.

I would really appreciate any help as I am trying to preserve some old family movies of someone who is leaving us.

---

### Post by herteljt on 2008-08-30
> **EpidemikE said:**
> Does anyone know of any tutorials or guides on how to do this on Ubuntu?

My specs are 2GB of ram, AMD X2 4400+ @2.3GHz, Asus M2A-VM HDMI mobo, AverMedia M780 PCI-E TV Tuner card.

I have all the necessary components except for the software to capture video but I don't know what software to use. I also am not sure on how to check and see if Ubuntu sees the tuner card.

I would really appreciate any help as I am trying to preserve some old family movies of someone who is leaving us.

To check and see if Ubuntu sees the tuner card type:
```
lspci | grep Multimedia
```

It should return something like:
```
03:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```
(only with your cards info)

As far as transferring your VHS videos this link may help:

[http://ubuntuforums.org/showthread.php?t=875948](http://ubuntuforums.org/showthread.php?t=875948)

If you can't find a solution through that thread I may know another way, but I would try using Kino first as it has a much nicer user interface.

---

### Post by EpidemikE on 2008-08-30
Thanks, I will look into the information you posted.

I read somewhere that you can use your digital camcorder as a pass through to convert VHS from a VCR to a computer using firewire. I am going to look into it. 

I hope I can do this because I really don't want to resort to windows to do this.

Is there something similar to the device manager for Ubuntu that I can use to see manage drivers and such for my card.

---

### Post by herteljt on 2008-08-30
> **EpidemikE said:**
> Thanks, I will look into the information you posted.

I read somewhere that you can use your digital camcorder as a pass through to convert VHS from a VCR to a computer using firewire. I am going to look into it. 

I hope I can do this because I really don't want to resort to windows to do this.

Is there something similar to the device manager for Ubuntu that I can use to see manage drivers and such for my card.

This is similar to my other idea.  If you hook up your VCR's out to your tuner card's in then you will be able to play movies on your vcr and watch them through your tuner card (you'll need to be on whatever channel you vcr uses).  You can then record the video as you would regular tv.  I use a program called tv-viwer to watch tv and it has some recording features (it is still being developed).  

If you want to install tv-viewer go to the following link.

[http://home.arcor.de/saedelaere/info_eng.html](http://home.arcor.de/saedelaere/info_eng.html)

It requires several packages to be installed namely:

ivtv-utils, tcl, tk, libtk-img, xosd-bin, xdg-utils and scantv

You'll also need to have VLC installed.

To record video using tv-viewer following the instructions in the user guide.

[http://home.arcor.de/saedelaere/doc_eng.html](http://home.arcor.de/saedelaere/doc_eng.html)

I hope this gives you some ideas :)

---

### Post by EpidemikE on 2008-09-02
I just ran the grep command you specified and what I recieved was:

```
02:00.0 Multimedia video controller: Micronas Semiconductor Holding AG Unknown device 0720
```

Any Suggestions?

---

### Post by cotcot on 2008-09-03
I keep a text file with instructions that I use when I do a clean reinstall.
One of the topics is capture VHS with a PVR150 card (it is a collage of different quotes I found on the forum):

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


I hope this will give you some inspiration.

---

