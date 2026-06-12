---
title: "Streaming music over power lines"
date: 2006-02-28
forum: The Cafe
---

### Post by simon_is_learning on 2006-02-28
Don't know if this is the right subforum but I'll give it a try.

My idea. 

When I heard that it nowdays is possible to send up to 1mbps data over your own powerlines in your own house, I got an idea.

Then it would be possible to stream...

What you would have to use is another protocol then IP, becouse idealy the streamed audio should be avaliable in every jack. 
So just simply stream it right out.

my though involves no computer. 
rather a box width a hardware codec 
my first question:
**Has anyone heard of a hardware ogg-codec?**

so your computer simply sends out signal. Then it gets coded again, away it goes. 
(When you have a computer - a digital direct signal in is optional of course)
But the benefits of beeing non-dependent of a computer I like. Then you can stream your stereo, or you can stream a live-event - just tap a signal from the mixer.

the next problem is the power lines
my next question:
**Does anyone know any standard that is Open Source?** 
Becouse maybe some modifications have to be made.

But I have to say that i got this Idea today - and I havn't done any major researchs. 

My third Question:
**has this already been done?**

Now... Give me all your doubts an we can discuss.

---

### Post by QUASAR_FREAK on 2006-02-28
Transmit under power lines? thats with some special hardware or is in determinate Country?

---

### Post by simon_is_learning on 2006-02-28
maybe my English isn't so good. 

[http://en.wikipedia.org/wiki/Power_line_communication](http://en.wikipedia.org/wiki/Power_line_communication)

---

### Post by gord on 2006-02-28
whats the point? you might as well just set up a very small radio station which covers just around your house (to avoid any legal consiquinces) and just pipe your music to that.

---

### Post by simon_is_learning on 2006-03-02
Just a idea as I said.

would be cool to have such gadgets

---

### Post by mips on 2006-03-02
[QUOTE=simon_is_learning]Don't know if this is the right subforum but I'll give it a try.

My idea. 

When I heard that it nowdays is possible to send up to 1mbps data over your own powerlines in your own house, I got an idea.

Then it would be possible to stream...

What you would have to use is another protocol then IP, becouse idealy the streamed audio should be avaliable in every jack. 
So just simply stream it right out.

my though involves no computer. 
rather a box width a hardware codec 
my first question:
**Has anyone heard of a hardware ogg-codec?**

so your computer simply sends out signal. Then it gets coded again, away it goes. 
(When you have a computer - a digital direct signal in is optional of course)
But the benefits of beeing non-dependent of a computer I like. Then you can stream your stereo, or you can stream a live-event - just tap a signal from the mixer.

the next problem is the power lines
my next question:
**Does anyone know any standard that is Open Source?** 
Becouse maybe some modifications have to be made.

But I have to say that i got this Idea today - and I havn't done any major researchs. 

My third Question:
**has this already been done?**

Now... Give me all your doubts an we can discuss.[/QUOTE]


1. Dunno
2. Ethernet (One of the 802.xx standards)
3. Yes

There are many companies making powerline communications devices. They usually implement it via a standard ethernet jack so as long as you have a LAN card you are fine. The devices plug into the wall socket with a pass-through for power devices and also provides an ethernet rj-45 jack for data.

TCP/IP is more than suitable for streaming. Multicast or Unicast is what you would use in this scenario and is catered for in the TCP/IP protocol stack. If you want to flood the stream to ALL devices simply designate it as Broadcast traffic but it is not recommended or the correct way to do.

Nothing wrong with doing the above in your house.

Power line communications has even been taken further with specialised hardware that caters for an entire neighbourhood to provide Internet access to households.

---

### Post by mips on 2006-03-02
Some examples:

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416874725&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416874725&pagename=Linksys%2FCommon%2FVisitorWrapper)
[http://www.netgear.com/products/details/XE104.php](http://www.netgear.com/products/details/XE104.php)
[http://www.netgear.com/products/details/XE102.php](http://www.netgear.com/products/details/XE102.php)
[http://www.billion.com/product/powerline/bipac7560g.htm](http://www.billion.com/product/powerline/bipac7560g.htm)
[http://www.billion.com/product/powerline/bipac2060.htm](http://www.billion.com/product/powerline/bipac2060.htm)

There are many more out there...

Apologies, I incorrectly linked to two PoE products which is not the same and the links have been removed.

---

### Post by FLeiXiuS on 2006-03-02
In my opinion, setting this up would be near pointless for audio casting.  This has risen the factor that we can now use one universal line to connect our Power, Telephony, and Internet (Available in some areas).  The reason why people haven't blasted MP3's down the line is due to it's restrictions.  The frequencies it'd be given to avoid interfering would only allow near 24kbps @ 22kHz.  This is not my ideal of PERFECT audio.  Considering 128kbps @ 44kHz still has some audio imprefections. 

But hey, if you'd like to have that then do it.  I would rather take the extra pairs in a CAT5 cable and cable up some speakers.  This way I'd have one line which is pre-run punch down to my switch and my audio block.  No need to run extra wires.  I've done a lot with 1 cat 5 cable.  Lets see, with the line I have running from my room to the upstairs, it's one line keep that in mind.  It's a single CAT5 cable, 2 pairs for internet, 1 pair for speakers, and the last pair for telephony.  Just depends on how you crimp it!

---

### Post by rfruth on 2006-03-02
BPL = bad idea

---

### Post by beast2k on 2006-03-02
Powerlines? Danger Will Robinson Danger, ZAP!!

---

### Post by mips on 2006-03-03
[QUOTE=FLeiXiuS]The reason why people haven't blasted MP3's down the line is due to it's restrictions.  The frequencies it'd be given to avoid interfering would only allow near 24kbps @ 22kHz.  This is not my ideal of PERFECT audio.  [/QUOTE]

Please elaborate how you get to these figures (24kb/s) ? 

In my book 14Mb/s (or higher, 170Mb/s) is more than sufficient for audio as these are some figures you can expect depending on your implementation. Pretty much the same as a normal LAN environment.

If you can stream HDTV broadcast over your home power network why not some pisswilly audio stream...

---

### Post by mips on 2006-03-03
[QUOTE=rfruth]BPL = bad idea[/QUOTE]

Why is it a bad idea ?

---

### Post by mips on 2006-03-03
[QUOTE=beast2k]Powerlines? Danger Will Robinson Danger, ZAP!![/QUOTE]

Best you sell all your electrical appliances then ;)

---

### Post by simon_is_learning on 2006-03-03
I actually found it:
[http://www.intellon.com/applications/networkedentertainment.php](http://www.intellon.com/applications/networkedentertainment.php)

But my Idea is still abit different. Becouse it wouldn't involve a computer. It would have a hardware codec.

Still wondering if someone have heard of a ogg-hardware codec, that could stream preferably in realtime (of course not so important - just stream it.) 

Thanks for your shown intresst by the way ;)

---

### Post by mips on 2006-03-03
[QUOTE=simon_is_learning]
Still wondering if someone have heard of a ogg-hardware codec, that could stream preferably in realtime (of course not so important - just stream it.) 
[/QUOTE]

When you say ogg-hardware codec I assume you mean a standalone device that would take either an analog or digital audio source (CD or RCA input), encode it into ogg format and stream it via a ethernet port ?

Even a standalone device would represent a PC without monitor/keyboard. It would have analog audio inputs, CD-ROM & optional hard drive. This type of device would still have a processor, memory & software of some sort as encoding is a cpu intensive process. 

Is the above what you are looking for ???

---

### Post by mips on 2006-03-03
You could probably build something like the above using off the shelf components, stripped linux OS & OSS software.

**_Hardware_**
mini-ITX motherboard (Via, AMD Geode NX or Pentium-M chipset)
Soundblaster or better audio card
CD-Rom/HD/Flash memory, would be nice to use flash mem with no moving components to to store OS and apps + swap file.
Fast RAM
[http://www.mini-itx.com/](http://www.mini-itx.com/)
[http://www.via.com.tw/en/initiatives/spearhead/mini-itx/](http://www.via.com.tw/en/initiatives/spearhead/mini-itx/)
[http://www.epiacenter.com/](http://www.epiacenter.com/)
[http://linuxdevices.com/articles/AT8275095591.html](http://linuxdevices.com/articles/AT8275095591.html)


**_Software_**
Stripped version of Linux like DSL or some other distro used in embedded type applications.
IceCast2 Server
Ices2 Source/Live encoder
Icecast2 & Ices2 can be found here, [http://www.icecast.org/index.php](http://www.icecast.org/index.php)

You would offcourse have to customise the software and do some design work if you dont want to use a normal keyboard & monitor for I/O purposes and require a simple keypad/LCD display or something of the sort.

---

### Post by mips on 2006-03-03
To receive the audio stream without a PC something like this would be nice, [http://www.slimdevices.com/](http://www.slimdevices.com/)

---

