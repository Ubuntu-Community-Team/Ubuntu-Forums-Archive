---
title: "VLC video capture with a Video4Linux device help"
date: 2008-08-08
forum: Ubuntu Studio
---

### Post by ezekiel000 on 2008-08-08
I've been trying to convert a vhs tape to a digital format with VLC through v4l. I've had some success but I've hit a couple of road blocks:

- I get a very low resolution output with the default settings and no video only audio output when I alter the settings for size. The current output is 320x240 I would like to get at least 600x450.

- I get lines across the video. As you can see in this sample record I did:
[http://rapidshare.com/files/135918728/1.mp4.html](http://rapidshare.com/files/135918728/1.mp4.html)
(The sample above has no sound as I didn't reattached the cable for the example it's not a problem.)

- I seem to get a very dark picture but when I change the brightness to anything but -1 it goes completely black, what sort of range/units is it working with? (I guess it would also be good to know the range/units the width and height settings use)

My TV Card is a KWorld 100SS DVB-T PCI Digital TV/HDTV Tuner inc Remote (VS-DVBTPCI/SS) I think.
The signal I'm recording is going into the composite? (Yellow cable) input for video and line-in 3.5mm jack on my sound card.

I've attached screenshots of each of the setting dialogue boxes to show all the setting that work at the moment. (When I tried other output formats VLC either crashed or the output file crashed Avidemux2).

Any help would be great.

---

### Post by ezekiel000 on 2008-08-15
No one has any experience with this? or any other program/method of recording vhs to avi/mp4?

The reason I'm doing this is I don't have vhs player anymore only dvd (so I'm having to borrow a vhs player)

Thanks in advance for any help.

---

### Post by chaos51 on 2009-02-03
You can try installing ivtv-utils (if you don't have it already) and then before starting vlc run
v4l2-ctl --set-fmt-video=width=640,height=480

Not sure if there is a place that you can set that so that it stays after a reboot/logoff but it might be a start.

Maybe that will help,

I just realised that you might not be using Intrepid 8.10 so what I said might not work for you (I'm guessing by your screen shots that you aren't using 8.10?)

---

### Post by chaos51 on 2009-02-03
With the lines are you referring to the one across the top or the ones throughout the video.  The ones throughout the video are normally because the video source is interlaced and you need to deinterlace the video.  I think vlc has various deinterlace settings, you might have to play with them a little to find the best one.

---

