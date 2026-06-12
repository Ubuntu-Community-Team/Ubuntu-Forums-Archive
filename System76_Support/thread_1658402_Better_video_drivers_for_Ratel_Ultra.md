---
title: "Better video drivers for Ratel Ultra?"
date: 2011-01-02
forum: System76 Support
---

### Post by azion1995 on 2011-01-02
A 2nd question, if you will.

I've noticed some video artifacts while playing various linux games. Not major ones, but enough to be a bit annoying. What chipset, specifically, does the Ratel Ultra use? I know it says Intel High Definition Graphics, but is there a model number which I could use to find updated drivers for it?

Thx,
-Z

---

### Post by nevius on 2011-01-03
> **azion1995 said:**
> A 2nd question, if you will.

I've noticed some video artifacts while playing various linux games. Not major ones, but enough to be a bit annoying. What chipset, specifically, does the Ratel Ultra use? I know it says Intel High Definition Graphics, but is there a model number which I could use to find updated drivers for it?

Thx,
-Z

If you're into gaming, it would be better to buy a $50 nvidia PCIe graphics card and install it yourself (a fairly simple procedure).

---

### Post by azion1995 on 2011-01-03
I'm not 'into gaming' per se, I'd just prefer if the video didn't have various artifacts when I do run a game. If there aren't better drivers than the ones packaged by System76, then so be it.

-Z

---

### Post by isantop on 2011-01-04
Actually, the default drivers are the best ones available. Intel produces their own Open Source drivers, and they are included with Ubuntu. We don't package them since they're already in there.

---

### Post by cascade9 on 2011-01-04
> **azion1995 said:**
> I'm not 'into gaming' per se, I'd just prefer if the video didn't have various artifacts when I do run a game. If there aren't better drivers than the ones packaged by System76, then so be it.

-Z

There are newer intel-xserver-xorg drivers around than what is packaged with ubuntu 10.10 (older ubuntu versions will have even older intel video drivers). You could try finding a PPA to get the newest drivers, I know one used to exist. ;)  
 
I agree with nevius. Adding an nvidia card would be cheap and easy. (as long as there is a PCIe slot anyway)

---

### Post by isantop on 2011-01-05
There is a PCIe slot, but there may not be room; it's a tight fit for a WiFi card, and a full size GPU is out of the question. I'd recommend the smallest one you can find. However, you may get slightly lower performance than with the built-in, since the graphics in the Ratel are optimized to work quickly. A guy at Intel summed it up perfectly for me; with a discreet graphics card, or older integrated graphics, it's like the GPU is in New York City, and the CPU is in LA, and they have to talk to each other, while the setup in the Ratel has the GPU in Phoenix, with the CPU still in LA. Still quite a distance, but much closer. Powerful GPUs make up for this because they can send more data and process it faster, but you'll need to get one that is a good deal faster to make up for the distance, and they may be too big.

---

### Post by cascade9 on 2011-01-05
> **isantop said:**
> A guy at Intel summed it up perfectly for me; with a discreet graphics card, or older integrated graphics, it's like the GPU is in New York City, and the CPU is in LA, and they have to talk to each other, while the setup in the Ratel has the GPU in Phoenix, with the CPU still in LA. Still quite a distance, but much closer. Powerful GPUs make up for this because they can send more data and process it faster, but you'll need to get one that is a good deal faster to make up for the distance, and they may be too big.

Sounds like an intel 'engineer'/salesman to me. Its sort of accurate...if you can 'move' from city to city at lightspeed. :P 

Since its just using the i5 graphics, its not going to have any advantages over a video card.....well, unless you install a very old video card. (if it was sandy bridge there that might be different).

---

### Post by isantop on 2011-01-07
Well, the options in the Ratel are based on Clarkdale, which is the step between the old architecture and the new. With the old, the GPU was on a completely separate section. Now, they're both on the same chip (i.e. they both go in the same socket). Sandy Bridge has both on the same die, so it's even lower latency, but the theory is the same.

Here's a good article: [http://hothardware.com/Reviews/Intel-Clarkdale-Core-i5-Desktop-Processor-Debuts/?page=2](http://hothardware.com/Reviews/Intel-Clarkdale-Core-i5-Desktop-Processor-Debuts/?page=2)

---

### Post by azion1995 on 2011-01-10
OK, then, I'll check for a newer intel-xserver-org than what's currently on my system.

Thx,
-Z

---

### Post by SeanChet on 2012-02-19
I'm worried about this too, I just got the Ratel Ultra this weekend and the display doesn't seem to be as sharp as I'd like it to be. Some graininess and lines show when I play dvds.  I have an Asus VE228H 21.5in which is connected by a HMDI cable. The disk drive that comes with the Ratel and the  						 						2nd Generation Intel Core i5-2300 ( 2.80GHz / 3.10GHz Turbo Mode - 6MB cache - 4 Cores). If there's something to be done, let me know. I wouldn't mind getting something to go into the PCIe slot, but I'm not sure what would be best.

---

### Post by isantop on 2012-02-20
Graininess and lines are typically byproducts of the display and cable, rather than drivers. What type of connection are you using? DVI-DVI? DVI-VGA? We see the best results when using full digital connections, so going from HDMI, DVI, or DisplayPort to the same plug on the other end.

You might also try tweaking the monitor settings. Some of them have sharpness settings that, if set too high make the image look pixelated; too low, and the image looks blurry.

Also, is the Display CRT or LCD? If it's an LCD, do you have it set to the native resolution? 

Also, keep in mind that most DVDs are encoded in 720x480, which needs to be upscaled to display on larger displays. This process can make the picture blurry or grainy as well.

---

### Post by SeanChet on 2012-02-21
I have: 
Asus VE228H 21.5in screen
Connected by a HMDI cable
The  disk drive that comes with the Ratel
2nd  Generation Intel Core i5-2300 ( 2.80GHz / 3.10GHz Turbo Mode - 6MB cache  - 4 Cores)

I tried tweaking with the options on the screen, there are a handful preset display settings, some are better than others. 

Do you know of any software that would make the upscaling smoother? Or anything that would fit in my PCIe slot? Something good enough to be worth installing and small enough to fit?

---

### Post by isantop on 2012-02-21
> **SeanChet said:**
> I have: 
Asus VE228H 21.5in screen
Connected by a HMDI cable
The  disk drive that comes with the Ratel
2nd  Generation Intel Core i5-2300 ( 2.80GHz / 3.10GHz Turbo Mode - 6MB cache  - 4 Cores)

I tried tweaking with the options on the screen, there are a handful preset display settings, some are better than others. 

Do you know of any software that would make the upscaling smoother? Or anything that would fit in my PCIe slot? Something good enough to be worth installing and small enough to fit?

Not really. The issue is that you're taking an image that's 720x480 pixels in size, and trying to display it on a screen that has many more pixels (1920x1080, in your case).

There are two things the computer can do. It can do no processing, and display the video such that each pixel in the video file corresponds to each physical pixel in the monitor. The resulting playback will be clear and artifact free, but will only be about six inches wide and four inches tall on your monitor with black space around it.

The other thing the computer can do is "zoom in" the video, such that it fills the whole screen. This is the most common method, since it takes full advantage of the screen. This is called upscaling.

However, as with any zooming in, this process has the potential to loose clarity. For example, try finding a photo that's about that size normally, then zoom in so that it occupies more of the screen. It will also be blurry and/or pixelated.

There simply isn't anything you can do about this, unfortunately, since there isn't any additional data present in the video for what would be extra pixels. You can't create data out of nothing. You can guess, which is what actually happens, but this process isn't perfect by any means. If you actually want a clearer picture, you need to use a higher resolution source material.

---

### Post by SeanChet on 2012-02-21
Could I replace the disk drive with a Blu-Ray disk drive? Would that be possible given the system I have, or would i need something more? Could that work out my issue and do you recommend it? Also, thanks for all of the replies.

---

### Post by isantop on 2012-02-22
> **SeanChet said:**
> Could I replace the disk drive with a Blu-Ray disk drive? Would that be possible given the system I have, or would i need something more? Could that work out my issue and do you recommend it? Also, thanks for all of the replies.

You could replace the drive, but you wouldn't be able to play Blu-Ray videos since the format isn't supported in Ubuntu yet. There is some development in that area, but it's not as active as DVD was because the format is much more tightly controlled, and in general the industry is moving away from physical distribution and moving instead to digital distribution like streaming.

---

