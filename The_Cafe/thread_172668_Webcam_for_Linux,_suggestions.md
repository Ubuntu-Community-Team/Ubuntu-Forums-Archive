---
title: "Webcam for Linux, suggestions?"
date: 2006-05-09
forum: The Cafe
---

### Post by dolny on 2006-05-09
I want to buy a rather cheap webcam that works nicely with Linux. Now I know about sites with lists of supported hardware, but I would like to hear your recommendations - from the people who used specific webcams. Thanks :)

---

### Post by louis_nichols on 2006-05-09
I have a Logitech QuickCam Chat and works well with the spca5xx driver. It cost only 30$ last summer. Now, I wouldn't say I recommend it, although I have no complaints about it. I'm just saying it works: it does the job and displays the image.

---

### Post by Kimm on 2006-05-09
I have a Creative NX webcam, works fine with spca5xx even though it might be somewhat old. 

You can allways check this list of webcams:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

[i]PS.
Doesnt work to good with kernels older than 2.6.15, so if your using Breezy I'd recommend upgrading to Dapper, or compiling a new kernel[/i]

---

### Post by Bandit on 2006-05-09
I got a Logitech QuickCam MESSENGER. IT doesnt work :(
I am looking for a good cheap cam myself also.

Cheers,
Joey

---

### Post by woedend on 2006-05-09
bandit,
the quickcam messenger does indeed work...at least for me :)
i can use it right now(IE - see out of it, snap pictures)...haven't used it for p2p yet.  It just won't work with the spca5xx drivers.
do a sudo make install on this package 
[http://home.mag.cx/messenger/source/qc-usb-messenger-1.2.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.2.tar.gz)

and do a modprobe quickcam and modprobe videodev  if needed.


let me know if it works for you.



as far as quality...its a little cheap webcam and i think it does its job nicely...naturally its not gonna take your high res supershots but gets the job done :).  Be sure its well lit though, this thing freaks out in dark lighting for me at least(keeps getting bright/dark bright/dark) every 30 seconds or so.

---

