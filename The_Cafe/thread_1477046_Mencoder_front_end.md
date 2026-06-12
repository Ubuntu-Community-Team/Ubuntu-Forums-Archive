---
title: "Mencoder front end"
date: 2010-05-08
forum: The Cafe
---

### Post by praveesh on 2010-05-08
Do anybody know a mencoder frontend that works in Ubuntu ? I tried konverter, gmencoder and a few others . But nothing worked well . If anybody know a working ffmpeg frontend other than winff please tell that too .

---

### Post by FakeOutdoorsman on 2010-05-08
> **praveesh said:**
> Do anybody know a mencoder frontend that works in Ubuntu ? I tried konverter, gmencoder and a few others . But nothing worked well . If anybody know a working ffmpeg frontend other than winff please tell that too .

VLC can convert videos if I remember correctly.  An alternative to WinFF may be [sinthgunt](http://code.google.com/p/sinthgunt/), but I've never tried it myself.  Why not use FFmpeg directly?

---

### Post by kio_http on 2010-05-08
Arista transcoder
WinFF
Iriverter

---

### Post by praveesh on 2010-05-08
> **FakeOutdoorsman said:**
> VLC can convert videos if I remember correctly.  An alternative to WinFF may be [sinthgunt](http://code.google.com/p/sinthgunt/), but I've never tried it myself.  Why not use FFmpeg directly?

it's not for me . It's for my friend who is not familiar with command line .

---

### Post by praveesh on 2010-05-08
> **kio_http said:**
> Arista transcoder
WinFF
Iriverter

I'll try

---

### Post by Ultra Cronic on 2011-11-13
> **FakeOutdoorsman said:**
> VLC can convert videos if I remember correctly.  An alternative to WinFF may be [sinthgunt](http://code.google.com/p/sinthgunt/), but I've never tried it myself.  Why not use FFmpeg directly?

:( I just tried stinthgunt and it's a magor fail, due to the fact you can't import .jpg's from a folder and compile them to a movie. BUT you can do this with the the command line; 

[ffmpeg -r 30 -b 3000 -i %09d.jpg filename.mp4]

     where as the folder full of still pix jpg's was named with 9 characters that is what the %09d.   stands for; 9 digits.
The default compression was to blurry so I was hoping the mencoder gui would help. Alot of crash BANG WAM BOooom!!! 
Experimenting with command line codecs calls.:confused:

---

