---
title: "Tascam US-122 (mkII) wont work!"
date: 2010-07-01
forum: Ubuntu Studio
---

### Post by Woolly Sammoth on 2010-07-01
Hi folks!
I've recently installed ubuntu studio and 64studio (the new 64studio v3 beta) and i wanna get my tascam usb audio interface working in either one (and thus break window's last shackle on my poor, poor form) but i can't and it's driving me nuts!

i've gone through a few different guides 

[http://ubuntuforums.org/showthread.php?t=431066](http://ubuntuforums.org/showthread.php?t=431066)
[everything seems to go ok until the "Plug in your usb cable and your tascam usb led should light up." bit.  I plug it in and nothing happens]

[http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)
[when it tells me to do 
"#mkdir /usr/share/alsa/firmware
#cd alsa-firmware-1.0.16 && mv * /usr/share/alsa/firmware"
the first line works but the second line produces a "bash: cd: alsa-firmware-1.0.16: No such file or directory" result.  the directory is there, if i go back a few steps then skip the "mkdir part" 'cause i've already made it i get loads of "mv: try to overwrite `/usr/share/alsa/firmware/aclocal.m4', overriding mode 0644" options ]

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)
[everything seems to work but the tascam doesn't show up when i check "lsusb"]



I wasn't sure if it's something to do with using a different version of ubuntu to the guides, having the mkII version of the us-122 or it's just me being far too me-ish and missing something obvious.  I also thought maybe i should try deleting the folders mentioned and starting again but didn't want to do this unless someone told me i wasn't going to kill my computer by stupidly deleting things all willy nilly.  

Sometimes i wish we could go back to when the height of technology was a sharp stick  :(

Any help would be really appreciated, cool points will be handed out like sweeties to anyone who can help!

Yours

w.s

---

### Post by AutoStatic on 2010-07-01
Hello, The US-122 differs from the US-122 MkII. The US122 is supported, the MkII is not afaik.

---

### Post by Woolly Sammoth on 2010-07-01
O, gosh darn it, i was afraid of that.  Looks like the insidious talons or microsoft windows will still hold dominion over my music making moods for a while then.

Thanks for replying though, at least i can stop wasting time trying to get it working now.

w.s.

---

### Post by johnsky on 2010-08-23
I also have a Tascam US-122 mkII , I'm stuck using windows for it.

It's the only thing I use windows for anymore.
The switching back and forth between windows and Ubuntu depending on if I want to record or do anything else gets rather annoying. Plus, I'm sure there's a whole load of resources out there in the Open community that can "liberate" my musical experimentation somewhat.

It would be wonderful if we could get the mkII to work under Ubuntu.

Unfortunately my knowledge is far too limited to contribute anything to the cause. Does anyone out there who knows what they're doing with ALSA, the mixers, drivers,  etc happen to own a US-122 mk II ?

If so, the community would absolutely fall in love with you if you could give us a how-to.:D

---

### Post by JC Cheloven on 2010-08-25
my 2p:

Tascam is plain hostile to gnu-linux. When a tascam device works is by hazard, they don't show any interest or facilitate their task to linux audio devels at all. If you like the free software way, you'd better to stay apart from tascam. 

I had a Tascam 1804fw device, and -like you- had to switch back to win2 everytime for audio stuff. At a point, I decided than freedom was more important. I sold out the device and bought another one (actually two, for different purposes). My global happiness coefficient has increased by 1% since then :)

JC

---

