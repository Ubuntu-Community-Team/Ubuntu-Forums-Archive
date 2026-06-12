---
title: "6 - 10 channel recording - basic compatible interface?"
date: 2009-11-05
forum: Ubuntu Studio
---

### Post by texla on 2009-11-05
Hey all - I'm thinking about upgrading a 2 channel recording setup to something with a minimum of 6 ins (1/4 inch or xlr) and a maximum of 10 ins - but we might settle for 4 inputs since we're doing this on the cheap. Budget is just $200-$300 for the interface.  This is only for recording band demo stuff for now and maybe pro stuff later...

We are recording now with 2 tracks in from a Zoom H4 into Ardour on a Ubuntu Studio 9.10 setup.  I thought I could just buy another interface from Presonus or M-Audio with a few more ins that would do the trick and use it with Ardour and Jack - but from the forums I'm reading, this  seems to be a difficult and not too easy task.  Is that true?  Any tips or hardware I should look at or avoid?  Is there somewhere else I should be looking online for a list of ubuntu studio compatible hardware?  

These are a few interfaces I was thinking about:
[PreSonus FIREBOX 24-bit/96kHz FireWire Recording System (4ins/6 outs)]("http://www.music123.com/PreSonus-FIREBOX-24-bit-96kHz-FireWire-Recording-System-184133-i1125347.Music123") - $200
[PreSonus FIRESTUDIO MOBILE (8 ins/2 outs)]("http://www.music123.com/PreSonus-FIRESTUDIO-MOBILE-620681-i1471883.Music123") - $300

or is a soundcard a better idea?
[M-Audio Delta 1010LT 24-Bit 96kHz PCI Card - 10 ins/outs]("http://www.zzounds.com/item--MDOD1010LT")  - $100

Any info or direction at all would be much appreciated! :biggrin:

---

### Post by trulan on 2009-11-05
I love my Presonus Firepod.  They are now discontinued.  But I would highly recommend a firewire interface if you want that many inputs.  There are a few settings involved in getting a firewire interface to work, but it's not hard at all and there are quite a few of us on here who use them.

Check the Ffado list to see if a firewire device is supported before purchasing:
[http://www.ffado.org/?q=devicesupport/list](http://www.ffado.org/?q=devicesupport/list)

---

### Post by texla on 2009-11-05
Cool - thanks, Trulan!  Very encouraging info...

---

### Post by texla on 2009-11-13
Found the Inspire 1394 from Presonus - 
it's only 4 channels but it was on sale for under $150 and you can daisy chain them later to get another 4 (up to 16 total).  Yes, it's working great with Ardour!  A very easy setup, too thanks to this page: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

no idea if the daisy chain setup will work but I don't see why not.  The only down side is that two of the input channels are RCA inputs but that's not too bad - I have an old mixer I can use to bring two separate channels from the left/right outs. :popcorn:

---

### Post by kayosiii on 2009-11-14
I have used the firebox and the firepod. Firepod works very well indeed - I got mine second hand off ebay. The firebox doesn't have access to the internal mixer easily so you will probably want a seperate external preamp for the back two ports. The newer Presonus firewire cards, can be gotten to work with ubuntu but require the development version of ffado... (they won't be supported in libffado-1.0)...
Focusrite is a company that is very proactive in it's linux support you should check out their offerings - also it looks like Maudio might be comming to the party.

---

### Post by AutoStatic on 2009-11-14
With the band we record with a Focusrite Saffire Pro 10 I/O. I use it at home too and works very well with Ubuntu. Have no idea though if it's successor, the Saffire Pro 24 I believe, is that easy to set up as well.

---

