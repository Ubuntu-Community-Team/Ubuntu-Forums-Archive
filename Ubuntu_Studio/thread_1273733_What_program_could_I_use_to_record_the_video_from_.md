---
title: "What program could I use to record the video from a dazzle capture card?"
date: 2009-09-23
forum: Ubuntu Studio
---

### Post by sagex24 on 2009-09-23
Hey,

[http://www.bestbuy.com/site/olspage.jsp?skuId=8853822&st=dazzle+dvc+plus+capture+card&type=product&id=1209166068566#tabbed-customerreviews](http://www.bestbuy.com/site/olspage.jsp?skuId=8853822&st=dazzle+dvc+plus+capture+card&type=product&id=1209166068566#tabbed-customerreviews)

I need some help using VLC to open a capture device and record this.  Right now it keeps opening up my webcam instead of the capture card.  I need some help getting the settings right / getting it to detect the card.

thanks

---

### Post by moe_syzlak on 2009-09-23
> **sagex24 said:**
> Hey,

I was wondering what program i could use to capture the video on my laptop from one of these capture cards:
[http://www.amazon.com/Pinnacle-Systems-82301006351-Dazzle-Recorder/dp/B001CBXEDG/ref=sr_1_1?ie=UTF8&s=software&qid=1253481590&sr=8-1](http://www.amazon.com/Pinnacle-Systems-82301006351-Dazzle-Recorder/dp/B001CBXEDG/ref=sr_1_1?ie=UTF8&s=software&qid=1253481590&sr=8-1)

or

[http://www.amazon.com/Pinnacle-Systems-82301006461-Dazzle-Creator/dp/B001C5DOWI/ref=pd_cp_sw_1](http://www.amazon.com/Pinnacle-Systems-82301006461-Dazzle-Creator/dp/B001C5DOWI/ref=pd_cp_sw_1)

The software that comes with it doesn't work with ubuntu i'm assuming, so what should i use?

thanks

I have some questions. Is that a capture/TV card?

Note: there needs to be drivers for hardware to work

---

### Post by moe_syzlak on 2009-09-23
Hey take a look at this too and see if the Video4Linux supports your hardware. [http://en.wikipedia.org/wiki/MythTV#Supported_tuner_cards](http://en.wikipedia.org/wiki/MythTV#Supported_tuner_cards)

---

### Post by sagex24 on 2009-09-26
Update:

I bought this today: [http://www.bestbuy.com/site/olspage.jsp?skuId=8853822&st=dazzle+dvc+plus+capture+card&type=product&id=1209166068566#tabbed-customerreviews](http://www.bestbuy.com/site/olspage.jsp?skuId=8853822&st=dazzle+dvc+plus+capture+card&type=product&id=1209166068566#tabbed-customerreviews)

I tried using the program Cheese to record but it would not work out.  The video lagged MAJORLY and was in black and white.  Please tell me what records capture cards?  The footage is coming from an xbox 360.  I have it hooked up to the USB of a laptop.  What program do i need.  Thanks.

---

### Post by sagex24 on 2009-09-26
I found that you can stream and save a capture device via VLC.  I need some help with the settings though.  Everytime I try to do it it opens up video from my webcam, not the capture card.

---

### Post by sagex24 on 2009-09-26
I've got the capture card stream playing in VLC, but it won't save the stream...  How does that work out?   

I'm using the same settings for both but when I save it saves the webcam, stream it streams the capture card.

---

### Post by Jose Catre-Vandis on 2009-09-26
If the input is an analog "TV" stream, **mencoder/mplayer** will happily capture/dump to incoming video.

For example I had to export some Wii game replays to PC for my son, and used the following command:

```
mencoder -tv norm=PAL:driver=v4l2:width=720:height=576:input=3:fps=25:amode=1 -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2500:aspect=16/9 -aspect 16:9 -o wiitest.avi tv://
```

I was using a composite cable as an input to my capture card

---

### Post by moe_syzlak on 2009-09-27
> **sagex24 said:**
> I've got the capture card stream playing in VLC, but it won't save the stream...  How does that work out?   

I'm using the same settings for both but when I save it saves the webcam, stream it streams the capture card.

VLC can do alot of crazy things. It can load a video file and output the same video in another format. VLC has a ton of options and it's a professional quality program (even if it doesn't look like it). VLC can be extended and scripted to do many things.

You can go over to the VLC forums and see what those dudes have to say about doing what you want to do. I think they have more experience than me when it comes to doing magic with VLC.

Links:
[http://forum.videolan.org/](http://forum.videolan.org/)

---

### Post by moe_syzlak on 2009-09-29
> **sagex24 said:**
> I've got the capture card stream playing in VLC, but it won't save the stream...  How does that work out?   

I'm using the same settings for both but when I save it saves the webcam, stream it streams the capture card.

Try reading the VLC documentation or asking on the VLC forums. The VLC guys would know more about saving streams than general n00bs on teh Ubuntu forems.

---

### Post by moe_syzlak on 2009-10-01
> **sagex24 said:**
> I've got the capture card stream playing in VLC, but it won't save the stream...  How does that work out?   

I'm using the same settings for both but when I save it saves the webcam, stream it streams the capture card.

Ask the VLC forum guys and post results back here.

---

### Post by kvarley on 2009-10-09
Sagex24 if you webcam appears instead of the dazzle unplug your webcam and plug the dazzle into the usb port the webcam was previously in. That should work.

---

### Post by kvarley on 2009-10-10
Here's a guide I've just written about how to get the Dazzle working in Ubuntu. Hope this helps.

[http://www.starcube.co.uk/2009/10/ubuntu-howto-capture-from-the-dazzle/](http://www.starcube.co.uk/2009/10/ubuntu-howto-capture-from-the-dazzle/)

---

