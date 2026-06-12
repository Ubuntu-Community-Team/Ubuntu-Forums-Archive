---
title: "How to stream desktop live to Justin.tv, ustream etc"
date: 2009-01-17
forum: Ubuntu Studio
---

### Post by Saytr on 2009-01-17
I am on Kubuntu 8.10. I would really like to stream my desktop live on sites like Justin.tv or Ustream. I tried installing screencast4linux but it keeps giving me an error so I really cant use it. are they any other similar ways I can try ??

---

### Post by sethtriggs on 2009-03-04
I would like to figure this out too - I'm subscribing to this thread, hehehe... though I am on Ubuntu. Maybe a solution would give me some insight.

-Seth

---

### Post by rylleman on 2009-03-05
[Webcam Studio]("http://webcamstudio.wiki.sourceforge.net/") might work for you?

---

### Post by sethtriggs on 2009-03-11
> **rylleman said:**
> [Webcam Studio]("http://webcamstudio.wiki.sourceforge.net/") might work for you?

Yes, I got it to work! Thank you, thank you thank you!

-Seth

---

### Post by rylleman on 2009-03-11
> **sethtriggs said:**
> Yes, I got it to work! Thank you, thank you thank you!
-Seth
You're welcome.
Can you give a quick brief on how you did it? (I never suceeded in broadcasting my desktop with Webcam studio).

---

### Post by Kat of Zion on 2009-03-11
> **sethtriggs said:**
> Yes, I got it to work! Thank you, thank you thank you!

-Seth

Yup.  I found WebcamStudio for Linux to work.  Im trying to determine how to get it to work with my 1280x800 resolution.  Do I need to set the "Desktop" source to output 320x240 or 640x480?

---

### Post by patrickballeux on 2009-03-28
> **Kat of Zion said:**
> Yup.  I found WebcamStudio for Linux to work.  Im trying to determine how to get it to work with my 1280x800 resolution.  Do I need to set the "Desktop" source to output 320x240 or 640x480?

You need to set manually your "Capture size" at 1280x800, and the output size at 320x240 (if your are broadcasting in that format).


Patrick

---

### Post by Kat of Zion on 2009-03-28
> **patrickballeux said:**
> You need to set manually your "Capture size" at 1280x800, and the output size at 320x240 (if your are broadcasting in that format).

Patrick
Yeah.  My problem is that on 320x240 it looks lousy since 1280x800 is a far bigger screen resolution.  I managed to get it down to a 640x480 resolution instead and have "mouse follow" turned on that way Ustreamers wont miss me selecting Photoshop items from the toolbox and then moving back to the drawing that I'm webcasting about.

Kat

---

### Post by 3003030 on 2009-04-13
Yes, I got it to work! Thank you, thank you thank you!






[RIGHT][justin tv]("http://justintvfutbol.blogspot.com") - [kombi]("http://www.kombi1.com") - [e-okul]("http://elektronikokul.blogspot.com")[/RIGHT]

---

### Post by MaindotC on 2009-05-30
How do you tell Webcam Studio to broadcast to ustream?  I didn't see any options for connecting it to ustream.

---

### Post by MaindotC on 2009-06-06
bump

---

### Post by MaindotC on 2009-06-25
I rtfm'd and I see what happens.  Now whenever I go to a flash-broadcast-enabled site like uStream or Livestream there's an option in the drop-down box for "vloopback module" and I just select that.  Only problem is it is extremely small - anyway to broadcast a screen larger than 320x240?

---

### Post by afrodeity on 2010-06-24
> **strAlan said:**
> I rtfm'd and I see what happens.  Now whenever I go to a flash-broadcast-enabled site like uStream or Livestream there's an option in the drop-down box for "vloopback module" and I just select that.  Only problem is it is extremely small - anyway to broadcast a screen larger than 320x240?


Where exactly, in the browser or in the WCS itself? I don't see it.

---

### Post by MaindotC on 2010-06-25
For Livestream, there should be an option in the Livestream Webcaster where you have a choice of which input to select.  It should look like this:
[[IMG]http://img375.imageshack.us/img375/862/screenshotre.png[/IMG]](http://img375.imageshack.us/i/screenshotre.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by afrodeity on 2010-06-27
Looks like you using the windows client? Did you get it to run in wine?

All I have is the ustreamtv java app that runs in my browser window.

UPDATE: Oops, I see its livestream, another website altogther.Silly me.

---

### Post by MaindotC on 2010-06-27
uStream version:
[[IMG]http://img638.imageshack.us/img638/291/screenshotkt.png[/IMG]](http://img638.imageshack.us/i/screenshotkt.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by dannyboy79 on 2010-08-24
im using wcs .54 in 10.04 regular ubuntu. i have a firewire (dv) device I want to broadcast but when i do it, the output that goes to ustream is only the top left quater of the screen. everything looks ok in wcs but in ustream it only shows the top left quarter of the screen. i don't have a picture now but i will put one up later after work. just wanted to get this post up so it would get noticed. i haven't even tried messing with audio yet.
my device is a dazzle hollywood dv bridge which captures SD only at 720x480. time warner tells me i have a 1mb upload, is that enough to even stream? i saw wcs has options for rescaling my dv source to 320x240, is it rescaling it and not centering it? i didn't see anything about size on the actual ustream broadcast page besides larger resolution which i did check that box. any help would be appreciated.

---

### Post by dannyboy79 on 2010-09-01
anyone else trying to stream a dv source? it kills my xbox live connection when i try to stream which leads me to believe that either wcs isn't compressing my upload stream at all or my connection of 1mb upload isn't going to work at all to stream live gameplay. any thoughts? should I somehow take the output from wcs and pipe it through ffmpeg to compress it to flash or something like that? also, i can't figure out how to get audio as I read that wcs doesn't pick up audio and I have to mess with pulseaudio somehow. any help please?

---

### Post by Fenix-TX on 2010-09-13
If anyone is insteresting in this, jtvlc it's a good solution to work with vlc and justin tv. Info about this here: [http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API](http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API)

---

### Post by dannyboy79 on 2010-09-14
> **Fenix-TX said:**
> If anyone is insteresting in this, jtvlc it's a good solution to work with vlc and justin tv. Info about this here: [http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API](http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API)
i've read that but it talks about streaming a file already complete and on your system. what about streaming a firewire DV device. example: i have a dazzle hollywood dv bridge which takes component input from my xbox 360, goes into the dazzle and the dazzle outputs DV via firewire to my 10.04 ubuntu install system. how can I grab that stream with vlc, encode it something more appropriate for streaming (like flash) depending on my upload connection and stream it to either justin.tv or ustream?

---

