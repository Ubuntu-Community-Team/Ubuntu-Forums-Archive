---
title: "Pundit P1-AH2 Motherboard Case Connection Raidmax Tornado"
date: 2009-07-04
forum: System76 Support
---

### Post by Cr4shJunkie on 2009-07-04
I have a System 76 Sable.  I recently upgraded my PSU and got a video card which didn't fit in the Sable case, so I got a new case.

The only problem I'm having is the new case connection to the motherboard.  The connector on the Sable is just one connector, so it slips on the motherboard with no confusion.  The Raidmax connector includes 5 smaller connectors- Power SW, Reset SW, a circle with a "-" through it, Power LED+, +- H.D.D. LED.  I need to know what order these go in on the motherboard.

I've never done this before, its the first time I've even opened my box.  I've tried several different combinations and obviously none of them have worked.  I'd rather not fry anything.. if that's possible.

Here is with the System 76 connector (left):
[IMG]http://i674.photobucket.com/albums/vv103/dudz01/sys761a.jpg[/IMG]

Without connector (left, colorful squares):
[IMG]http://i674.photobucket.com/albums/vv103/dudz01/sys762a.jpg[/IMG]

Raidmax connectors (Power SW, Reset SW, a circle with a "-" through it, Power LED+, +- H.D.D. LED):
[IMG]http://i674.photobucket.com/albums/vv103/dudz01/RM-1.jpg[/IMG]

Can anyone tell me how to connect this to the Sable's motherboard?

Thanks

---

### Post by thomasaaron on 2009-07-06
I've built a few of those. And if memory serves, the pin-outs are written (nearly microscopically) next to the pins. So you *should* be able to tell where they go.

I did some googling and couldn't find any pin-out for that mobo.

I may be able to open one up and help you, though. If you can't tell by the writing on the mobo, let's take this to email.

---

### Post by Cr4shJunkie on 2009-07-06
> **thomasaaron said:**
> I've built a few of those. And if memory serves, the pin-outs are written (nearly microscopically) next to the pins. So you *should* be able to tell where they go.

I did some googling and couldn't find any pin-out for that mobo.

I may be able to open one up and help you, though. If you can't tell by the writing on the mobo, let's take this to email.
I took another look and used a magnifying glass, there are 3 rows of tiny numbers next to the pins on rectangle metal(?) bars or something.  Could that be what you're referring to?  They were pretty hard to see even with the magnifying glass, but I do know the bar in the middle had a "501" on it.  The other two bars I believe had four numbers.  

If those are the labels you're talking about, I'll take another look and try to figure out what numbers are there.

I'll PM my email address to you.

Thanks for your help.

---

### Post by thomasaaron on 2009-07-07
Here's a PDF that has a lot of mobo info on it.

[http://www.unitycorp.co.jp/support/download/manual/barebones_manual/e2574_p1-ah2.pdf](http://www.unitycorp.co.jp/support/download/manual/barebones_manual/e2574_p1-ah2.pdf)

---

### Post by Cr4shJunkie on 2009-07-07
I found that PDF too, it wan't much help. Thanks though

---

### Post by thomasaaron on 2009-07-08
Not sure where else to point you, then. Looked at the mobo here, and it isn't clear how you would tell which of the plugs go where. 

That pdf has the best pin-outs I've found.

---

### Post by jdb on 2009-07-08
> **thomasaaron said:**
> Not sure where else to point you, then. Looked at the mobo here, and it isn't clear how you would tell which of the plugs go where. 

That pdf has the best pin-outs I've found.

Look on page 4-9.

jdb

---

### Post by Derath on 2009-07-08
(Coming from someone who enjoys building his own desktop systems)

Somewhat agreed jdb, the top of 4-9 does show the activity LEDs header which would take care of the PowerLED +/- (PLED+/-) and the HDD +/- (IDE_LED+/-)

Unfortunately the manual does not say where the power switch and reset switch are. and in regards to the circled line, I have not seen that marking on anything, check the case manual to see what that wire is for specifically.

For the power and reset switches, here's a recommendation, if you look at the old case, you might be able to see the wires coming from the power switch to the wire harness that you described, if you can determine the color of the wires and where they fit in that harness, you should be able to match that with the new case.

I do see the connector you're talking about in the image, and unfortunately I believe the Asus is premade, S76 wouldn't have been the one to make that harness. It does look like you need the red, green, and black jumpers there, the I think following the wires from that harness to where they lead in the case would be the best option to determine which goes where. For example, the wire plugged in the red colored jumper are red and white, if you follow those to the front of the case, you might be able to see if they are connected to the power switch, in which case the POWER SW would go in that spot, and I can't tell the colors of that wire from the photo, but if there's a white and another color, white would go to the left.

Hope this helps!

---

