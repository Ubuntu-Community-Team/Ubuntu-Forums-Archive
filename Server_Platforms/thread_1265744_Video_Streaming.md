---
title: "Video Streaming"
date: 2009-09-13
forum: Server Platforms
---

### Post by Java6 on 2009-09-13
Hi Everyone!
    Is there any way I can stream live Video from, for example a USB webcam or a Video Card? I was going to set up a small webcasting system and do not have any hardware yet. Any Ideas for Hardware and Software? So is there any way to stream video from webcams or other Video Input devices? I would want the software to be free and able to stream in MPEG4 or some other format that I could play back in Flash? Thanks for any help on this topic.

BTW, any suggestions on hardware I should or can use that is ubuntu-compatible?


:popcorn:

---

### Post by cariboo on 2009-09-14
I was given a webcam that attaches to a server, that connects to a network, similar to [this]("http:////cgi.ebay.com/USB-CCTV-Web-Camera-IP-Video-Server-With-2-USB-Port_W0QQitemZ220277522548QQcmdZViewItemQQptZPCA_Video_Conferencing_Webcams?hash=item3349904074&_trksid=p3286.m20.l1116"), It uses a java applet to display the output in a browser.

---

### Post by Java6 on 2009-09-14
I'll take a look at that. Is there a way to display it in a Flash Thing?
{edit}
That camera looks nice, but is there something with more resolution? Or something where I can just plug in any video source? I saw those cards everywhere for $15 or so that have a video input. Do you know which of those are supported my Ubuntu?{/edit}

---

### Post by cariboo on 2009-09-14
I have an ATI card with s-video and composite inputs for video capture, I've never used it as I really don't like ATI :), but I may try it later on this week.

Have a look [here]("http://www.linuxtv.org/wiki/index.php/Main_Page") for supported devices.

---

### Post by Java6 on 2009-09-15
OK. I'll take a look at it. I might buy a card later this week.

---

### Post by kustomjs on 2009-09-15
well I just got my webcam installed on my server and I am using a logitech quickcam and it works perfect just make you install webcam-server  by going sudo apt-get install webcam-server.

or use this guide: [http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2](http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2)

---

### Post by Lars Noodén on 2009-09-16
You'll probably want to take a look at Icecast first:

[http://www.icecast.org/faq.php](http://www.icecast.org/faq.php)

[http://www.icecast.org/ezstream.php](http://www.icecast.org/ezstream.php)


Maybe FFMPEG will be of use, maybe not:

[http://ffmpeg.org/](http://ffmpeg.org/)

---

### Post by Lars Noodén on 2009-09-16
> **Java6 said:**
> 
    ...I would want the software to be free and able to stream in MPEG4 or some other format ...



Flash, though pushed heavily by Youtube, is not Free.  non-Free formats just make life harder (and more expensive) for everybody.  


Ogg Theora is recognized now in Firefox, so in addition to MPEG you can give Theora a try.

---

### Post by Java6 on 2009-09-16
I will give it a try. But by flash I mean that it could be displayed in an Flash file. I can do Flex too :P I think flash is able to do MPEG, but not sure. ELse I will use the Theora support, I think firefox and safari have these implemented and then use a Flash Applet as fallback.

---

### Post by Lars Noodén on 2009-09-16
> **Java6 said:**
>  I think flash is able to do MPEG,

Three years of drift away from Open Standards... Flash is different than MPEG.  Further, MPEG is more or less open.  Flash is proprietary.  It wasn't really intended for video anyway though being a container format it can get abused as one.  ;) 

Flex:
[http://www.techper.net/2007/12/28/flash-is-still-closed-source-and-proprietary-technology/](http://www.techper.net/2007/12/28/flash-is-still-closed-source-and-proprietary-technology/)


If you're looking for open format sites:

	[http://thevideobay.org/](http://thevideobay.org/)
	[http://commons.wikimedia.org/](http://commons.wikimedia.org/)
	[http://dailymotion.com/](http://dailymotion.com/)

---

### Post by Java6 on 2009-09-16
Sorry. I meant Flex. So is there a way for it to render MPEG or OGG Theora?

---

