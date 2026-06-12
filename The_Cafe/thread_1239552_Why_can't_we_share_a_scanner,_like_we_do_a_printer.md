---
title: "Why can't we share a scanner, like we do a printer?"
date: 2009-08-13
forum: The Cafe
---

### Post by swoll1980 on 2009-08-13
Drives me nuts! I can't understand why the can't be shared in the same way the printers are.

---

### Post by jacktar on 2009-08-13
Probably because its an input device rather than an output device.

---

### Post by Maheriano on 2009-08-13
Maybe you could hold hands while you place the paper on the scanner?

---

### Post by oldsoundguy on 2009-08-13
> **jacktar said:**
> Probably because its an input device rather than an output device.

And therein lies the answer!!

(but I do wonder if something like a KVM switch could be employed?)(hmmmmmm ... something more to be explored!!)

---

### Post by koenn on 2009-08-13
> **jacktar said:**
> Probably because its an input device rather than an output device.
sort of.

They can be shared, or at least, there exist such a thing as a "network scanner" : you scan somehing and it delivers the result to a network shared folder, or it stores it on an internal hard drive where you can retrieve it with http or so.
That's mostly implentend on network-capable MFCs (Copiers/printer/scanner/... combinations)

---

### Post by koenn on 2009-08-13
> **oldsoundguy said:**
> And therein lies the answer!!

(but I do wonder if something like a KVM switch could be employed?)(hmmmmmm ... something more to be explored!!)

There used to be these things to "share' parallel (printer) ports - maybe the same could be done with usb ? 

or a 'scan daemon' that runs on the pc that has the scanner, and can be used over the network, sort of like X is able to network keyboards and monitors  ? 
I wonder if someone has thought of this before (hm, let me go patent that)

---

### Post by doorknob60 on 2009-08-13
You could set up a shared folder with SAMBA, set up a VNC server on the computer with the scanner, and when you need to scan something, use VNC to access the computer with the scanner, and save it into the shared folder. Not perfect, but it would work :P

---

### Post by forrestcupp on 2009-08-13
> **swoll1980 said:**
> Drives me nuts! I can't understand why the can't be shared in the same way the printers are.

I've been annoyed with that, too.  You can't even do it in Windows.

---

### Post by leef on 2009-08-13
You can use sane to share a scanner;

[http://www.linux.com/archive/articles/57798](http://www.linux.com/archive/articles/57798)

Not sure if sane is ported to windows or Mac OS though.

---

### Post by Biochem on 2009-08-13
> **oldsoundguy said:**
> And therein lies the answer!!

(but I do wonder if something like a KVM switch could be employed?)(hmmmmmm ... something more to be explored!!)

I used to have a KVM with a shared USB port. I can confirm that it works very well.

---

### Post by MikeTheC on 2009-08-13
Actually, swoll, many many moons ago, UMAX's scanners (I'm thinking of the Vista S6E) could be shared. It worked fairly well, the main downside at the time being the relatively limited amount of processor speed and RAM on the host system.

---

### Post by jcwmoore on 2009-08-13
I share my scanner through a web page on my server,  [http://scannerserver.online02.com/]("http://scannerserver.online02.com/")

I used this to share my scanner across my network, and tweaked it to allow direct scanning of pdfs.

---

### Post by FuturePilot on 2009-08-13
I'm not sure if I understand. My printer/scanner/copier works over the network. :confused:

---

### Post by steveneddy on 2009-08-13
My HP All-in-one is shared across the network.

When scanning, just select the folder named accordingly for each PC on the network.

I even have my daughter scan documents to my desktop PC that I access via Remote Desktop so i can get documents that are at home.

The printer/scanner just asks you which folder to send the document to and it's done.

I've never tried to share my old flatbed scanner but may try next time I'm home.

---

### Post by starcannon on 2009-08-13
+1 steveneddy's post #14
I can share a scanner if it is part of an All-in-One printer; particularly easy is my HP printer with built in wifi. I've never tried with stand alone scanners though.

---

### Post by HermanAB on 2009-08-13
One word: SANE

SANE can scan and serve the scanner up as a network service.

Just install SANE, it can do what you want, Windoze too:
[http://www.xs4all.nl/~ljm/SANE-faq.html#97](http://www.xs4all.nl/~ljm/SANE-faq.html#97)

---

### Post by Old Marcus on 2009-08-14
I've never seen the point of sharing a scanner. You have to physically go to the scanner to place the object to be scanned, so accessing it from 2 rooms away seems pointless.

The only time I could see the point is if you have a room of computers (for instance, at uni) but only one scanner.

---

### Post by starcannon on 2009-08-14
> **Old Marcus said:**
> I've never seen the point of sharing a scanner. You have to physically go to the scanner to place the object to be scanned, so accessing it from 2 rooms away seems pointless.

The only time I could see the point is if you have a room of computers (for instance, at uni) but only one scanner.

True its only slightly more convenient; sharing the scanner lets me do it all from the computer I'm currently stationed at /shrug, sometimes I'm working on something on a laptop, I hop up, set document on scanner, grab coffee on the way back... blah blah you get the gist.

---

### Post by swoll1980 on 2009-08-14
I don't want my gf touching my computer. that's why I want her to be able to do it from hers. I will try sane, and let you know if it works for me. Thank you.

---

