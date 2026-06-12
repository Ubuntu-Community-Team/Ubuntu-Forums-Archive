---
title: "Zoom H5 Handy Recorder"
date: 2016-04-11
forum: Ubuntu Studio
---

### Post by Joel_Pettit on 2016-04-11
Hi all:

I'm a new Ubuntu Studio user.  I've tried to connect my Zoom H5 Recorder via USB to my machine, but nothing shows up.  Have any of you had any experiences with this piece of hardware?  Do you have any advice?

Anything you can offer would be greatly appreciated.

---

### Post by jejeman on 2016-04-13
What do you expect to show up?
How do you plan to use it? For what?

As I read the specs it will work just as stereo device. If you planned to use it as a sound card.

Plug it in and give
```
lsusb
```

---

### Post by Bucky Ball on 2016-04-13
Which version of Ubuntu are you using? No I don't have a H5, I have a H6. :) I plug mine in and there it is, named as the H6. I did nothing to get it going.

Plug it in, open a terminal and paste this in:

> dmesg

Hit enter and post the last part of the output about the device you just plugged in, please (use code tags, green link in my signature). Does it say anything about the Zoom H5? Let us know your OS.

---

### Post by Joel_Pettit on 2016-04-21
Got it working.  Thanks for the reply.

---

### Post by Bucky Ball on 2016-04-21
> **Joel_Pettit said:**
> Got it working.  Thanks for the reply.

Common courtesy on the forums to share with the community how. Also, please help future travelers further by marking the thread as solved (second link in my signature below for how). Thanks

Good luck and enjoy the H5. I love my H6. :D

---

### Post by Joel_Pettit on 2016-04-21
Oh sure.  I didn't do anything special to get it working, I was just looking in the wrong place to begin with.

When I opened up Ardour, the device was listed.

---

### Post by MartyBuntu on 2016-04-22
Good news!

---

