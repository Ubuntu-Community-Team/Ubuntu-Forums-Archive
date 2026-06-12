---
title: "Error mounting SD card on new Pang"
date: 2009-06-02
forum: System76 Support
---

### Post by SCHolland on 2009-06-02
When I insert a SD card into the slot, nothing happens; the computer doesn't recognize it, I don't see it in the 'Places' area or in a file browser, nor can I access its contents.

What I do get is a cryptic error message from <dmesg>:

"mmc0: error -84 whilst initialising SD card"

A google search came up with similar experiences, but with different error numbers (if that matters??). Any thoughts, help, or suggestions? Do I need to give any other info?

Steven

---

### Post by SCHolland on 2009-06-02
Some background info:

This is a PNY SD disk that was used in a Canon camera. My fiance recently plugged it into her laptop (Win Vista) and transferred some files from the disk to her comp. When the card was put back in the camera, about a dozen or more pictures no longer show up in the camera's LCD screen.... So it could be a card issue...    

Just had fiance try again in Windows. It found errors on the disk and repaired them.  She had no trouble viewing the pictures, but when I tried I got the same error again.

---

### Post by thomasaaron on 2009-06-03
There are still some camera card formats/filesystems that Ubuntu cannot mount. We run into that every once in a while. SD cards from Palm devices sometimes cause trouble too.

Can you try a different SD card in the slot?

---

### Post by miniyak on 2009-06-05
I assume MS is one of the cards unsupported by ubuntu? The ms pro seems to fit in the pangolin, would it work if the right software was in order?

---

### Post by thomasaaron on 2009-06-06
MS filesystems aren't a problem. I usually see it with some camera cards and some Palm device cards.

---

