---
title: "Convert analog video (VHS, minidv) to digital formats"
date: 2008-07-31
forum: Ubuntu Studio
---

### Post by EpidemikE on 2008-07-31
Hello all. I was looking into getting setting up Ubuntu to do some conversion of old home VHS movies. I was wondering what software would I need and any suggestions on a tuner card?

I was also curious if I could do the same for my minidv Canon camcorder. It has a USB connection and I was curious as to what can be done.

I would really appreciate any help on this.

I am currently running Hardy x64. I was also considering Ubuntu Studio since its more setup "out of the box" for multimedia stuff.

---

### Post by Creative2 on 2008-07-31
NOT SURE IT WILL WORK for your dv camera but you could try kino to install correctly you should follow this 

[http://fuocotools.byethost13.com/index.php?topic=103.0](http://fuocotools.byethost13.com/index.php?topic=103.0)

but sometime this damned host is down so here there is italian version maybe you can translate with google 

[http://wiki.ubuntu-it.org/Hardware/Video/TelecameraDv?highlight=%28telecameradv%29](http://wiki.ubuntu-it.org/Hardware/Video/TelecameraDv?highlight=%28telecameradv%29)

---

### Post by EpidemikE on 2008-07-31
I will try that. This is the video tuner card that I am considering on getting.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815100014](http://www.newegg.com/Product/Product.aspx?Item=N82E16815100014)

---

### Post by DPic on 2008-07-31
I can't get Kino to work and i read [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) but the instructions stop after saying to use "sudo modprobe..." and after that there is just information without instruction on what to do with it

---

### Post by Creative2 on 2008-08-01
well have you tried with my tutorial ? 

and have you seen this [http://www.kinodv.org/article/view/161/1/9/](http://www.kinodv.org/article/view/161/1/9/) 
?

---

### Post by cotcot on 2008-08-02
For VHS I bought the Hauppauge PVR 150 and capture the VHS that is encoded by the PVR with this code 
```
v4l2-ctl -i 1
cat /dev/video0 > test.mpg 

```
The first line is to select the source : either and 2 when connected with a composite cable (from your VHS device to the PVR) or 1 in case of an S-video cable. If you use a scart to S-video or composite adapter make sure that you have one with VHS out or bi-directional (with a switch on the adapter to select IN or OUT).
I guess that this will work with the Avermate video card from the suggestion above.

---

### Post by gomadtroll on 2009-03-02
> **Creative2 said:**
> well have you tried with my tutorial ? 

and have you seen this [http://www.kinodv.org/article/view/161/1/9/](http://www.kinodv.org/article/view/161/1/9/) 
?

AFAIKT, Kino is firewire only. Other-wise nice video :-)

---

### Post by punx45 on 2009-03-02
> **EpidemikE said:**
> 
I was also curious if I could do the same for my minidv Canon camcorder. It has a USB connection and I was curious as to what can be done.



the USB cable for the miniDV camera is probably for transferring stills that most camcorders are capable of.   

USB is not capable of carrying DV streams, but the camera should have a firewire/dv/IEE1394 output, which you could use in conjunction with a firewire card and software to capture the dv video, preserving its digital state.   most dv cams also have composite outputs that you could capture with the same method as your VHS setup.   

you might also want to look at the ubuntu studio? edition, which i believe has alot of the video capture/edit etc. utilities already installed.

---

### Post by lenswipe on 2009-03-02
uhhh, minidv is already in digital format...

"mini digial video"

---

### Post by alegallo on 2009-03-04
right, mini-dv is digital video, but you'll need a firewire connection to make it work, not only in Linux, in Windows too.

USB MIGHT work, but it's really sloooooooooow, not even worth a try ;)

---

### Post by unoodles on 2009-03-04
> **alegallo said:**
> right, mini-dv is digital video, but you'll need a firewire connection to make it work, not only in Linux, in Windows too.

USB MIGHT work, but it's really sloooooooooow, not even worth a try ;)

I beg to differ.

I have a DIAMOND USB video capture device. It did not work in kino (or anything else I tried for that matter).

It *did* work on Windows (using software that came with it). And it was fast.

---

### Post by liame on 2009-07-06
Hi all,

i have the same problem with a sony miniDV camera.
I want to move it to my laptop (msi wind u100Plus) but the laptop doesn't have a firewire connection, only usb.
I am running ubuntu jaunty and when i connect the cam to the laptop ubuntu doesn't even see it.
The cam's owner does it on windows through the usb connection (and without being slow).

any ideas for me?

thanks

---

### Post by kayosiii on 2009-07-06
> **unoodles said:**
> I beg to differ.

I have a DIAMOND USB video capture device. It did not work in kino (or anything else I tried for that matter).

It *did* work on Windows (using software that came with it). And it was fast.

Alegallo's comment is referring to video from dv based camera only. Which you can transfer by firewire only. You are talking about an Analog to Digital converter. You are both correct Kino does DV via firewire. Windows AFAIK can't do DV via USB. Kino does not do Analog Capture cards.

---

