---
title: "Starling Windows Drivers?"
date: 2009-05-23
forum: System76 Support
---

### Post by Uzmati on 2009-05-23
Seems that I'll be forced to dual-boot my Starling for some work applications. 

I see that in the System76 Knowledge base there are Windows drivers for other hardware, do these yet exist for the Starling?

---

### Post by jjacobs2 on 2009-05-24
Depending on your applications it might be easier for you to use windows in a virtual machine in virtualbox.  There's no need for additional drivers that way and you have access to all your windows and linux programs without rebooting.  This may not work if you require directx support though.

---

### Post by Uzmati on 2009-05-24
I had tried that, but the recording and reporting software I'm using for work will not run within any virtual device or layer. Spent a week trying different solutions. 

I've already set up a small partition for Win7, and it actually works very well, but I've no control over the trackpad. If I knew the manufacturer I'd simply hit their website to see if the driver software is available.

---

### Post by thomasaaron on 2009-05-26
Windows drivers for the starling are here...
[http://knowledge76.com/index.php/Star1](http://knowledge76.com/index.php/Star1)

---

### Post by Uzmati on 2009-05-27
That's interesting. It looks like the touchpad driver is Synaptics. I've loaded the Synaptics driver previously only to have the touchpad lock up. That, and when I tried to load the Touchpad control onto my Ubuntu install, I was told the Starling didn't use a Synaptic touchpad. 

So is this is a work-around driver for Windows sake or is the touchpad really a Synaptic build?

---

### Post by thomasaaron on 2009-05-27
It is a Synaptics touchpad.

---

### Post by Uzmati on 2009-05-27
Most excellent. Thank you!

---

### Post by Uzmati on 2009-05-27
So how would I go about getting the Starling to recognize that it's a Synaptics touchpad?

---

### Post by thomasaaron on 2009-05-28
Ubuntu does recognize it as a Synaptics touchpad. Run this command...

cat /var/log/Xorg.0.log | grep -i Synaptics

Why that particular piece of software doesn't recognize it, though, I'm not sure.

---

### Post by slick666 on 2009-05-29
How well would a Starling do using Virtualbox to boot up a second OS? I know it's a netbook but the new atom processors have the hardware hyper-visor built ([http://processorfinder.intel.com/details.aspx?sSpec=SLB6P]("http://processorfinder.intel.com/details.aspx?sSpec=SLB6P")) in so I think it should be able to run something basic.

Just a thought

---

### Post by thomasaaron on 2009-05-29
We've never tried it, but my guess is that would probably bottle-neck the cpu. A virtual machine is pretty cpu intensive.

Also, with only 1GB of RAM to split between two OSes... that's probably not going to work very well.

---

