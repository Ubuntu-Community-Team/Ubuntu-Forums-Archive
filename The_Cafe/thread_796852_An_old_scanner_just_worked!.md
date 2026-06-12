---
title: "An old scanner just worked!"
date: 2008-05-16
forum: The Cafe
---

### Post by retrow on 2008-05-16
We had a bit of office cleanup today. Lots of old computer hardware was sent to the warehouse. Most of the hardware is so old that its not even worth reselling, so most of it ends up in landfills.

So from underneath a pile of cables there was a HP 4200C scanner which was discontinued about a decade ago. Our office assistant wanted us to keep it in our lab since we run to her office each time we need to scan some document. We tried finding a XP driver for it and tried installing it. It asked for a XP disk. We provided the disk and the installation was successful. We tried scanning a piece of paper, and got a 'dll file missing' error. A Mac guy connected it to his MBP running Leopard and it didn't even register its presence.

Then as a last resort we connected it to my Ubuntu desktop. Xsane wasn't installed, so I apt-get installed it and fired it up. And to everyone's surprise, we were able to scan with excellent resolution. It only went up till 600 dpi unlike the modern ones which go up to 1200dpi (and possibly beyond), but 600 dpi is also quite high res.

So it seems like Ubuntu Linux saved the scanner from ending up in a landfill. But the downside is that people will be coming to my desk if they want to scan something.

---

### Post by nick09 on 2008-05-16
Amazing what ubuntu can do.

I was even able to install my parent's 8( or 9'ish) year old HP Deskjet 712C which is way too slow for my taste.:lolflag:

---

### Post by Kingsley on 2008-05-16
sehr gut!

---

### Post by Ripfox on 2008-05-16
Nice. I threw away an old scanner today. Makes me feel like a dummy now.

---

### Post by northwestuntu on 2008-05-16
i have a 7yr old scanner with ubuntu and it works great.

"ubuntu saving the environment one scanner at a time" :)

---

### Post by CREEPING DEATH on 2008-05-16
Linux is absolutely fantastic for reutilization of older equipment: computers, printers, scanners, and more!

CD

---

### Post by retrow on 2008-05-17
A little continuation to the printer story from yesterday. One of my lab colleague stopped by my desk a while ago to scan some notes. He mentioned how power saving options were missing from Xsane. I said, "But you could just unplug the power cord when the scanner is not in use", to which he replied, "That would require you to restart your computer each time you wanted to scan something. They didn't have devices that got auto-detected after OS booting was completed, back before 2000."

Without any further comment, I unplugged the power adapter and plugged it back in. As soon as we fired up Xsane, it was ready to go :) Seems like with Linux you can make devices do stuff that they weren't even designed to do. Another cool feature was text character recognition (sudo apt-get install gocr) which makes life so much easier when you are scanning some printed material, which you can save as text instead of saving it as an image.

Now I will save electricity by just unplugging the scanner when not in use. Come to think of it, thats what everyone should be doing anyway, but everyone learns this lesson in their own way.

---

### Post by gameryoshi600 on 2008-05-17
congrats on saving the environment.

---

### Post by bufsabre666 on 2008-05-17
ah linux, is there anything you cant do?

---

### Post by OZFive on 2008-05-17
Xsane is not my fav scanner software, I suggest you try out gscan2pdf, it is in the repos and I feel the interface is MUCH cleaner and easier to use.  Try it out!

---

### Post by retrow on 2008-05-17
Thanks for recommending gscan2pdf OZFive :)

I tried it out, but its saving and scanning options seemed pretty limited (or were hidden in a place I couldn't find). Brightness/contrast/gamma control, selecting a region from preview, and exporting to image formats is present in Xsane, but I wasn't able to find those in gscan2pdf.

The interface is definitely nice and clean though :) Thanks again.

---

### Post by &#932;itus on 2008-05-17
This thread is just what linux needs, I wish I could read such success storys every day :)

---

### Post by OZFive on 2008-05-18
> **retrow said:**
> Thanks for recommending gscan2pdf OZFive :)

I tried it out, but its saving and scanning options seemed pretty limited (or were hidden in a place I couldn't find). Brightness/contrast/gamma control, selecting a region from preview, and exporting to image formats is present in Xsane, but I wasn't able to find those in gscan2pdf.

The interface is definitely nice and clean though :) Thanks again.


Your welcome, gscan2PDF can export into most image formats other than PDF.  It is after you click the save icon that you are presented with the options of what format.  It is in the upper right hand corner of the save dialog. 

I m not sure about the brightness/contrast/gamma controls.  I am not even sure they are made up yet for the program.

---

