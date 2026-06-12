---
title: "who's having camera problems in gutsy?"
date: 2007-10-23
forum: The Cafe
---

### Post by fuscia on 2007-10-23
i am. my laptop even recognizes the model of the camera but says it can't lock the device (this is in kubuntu). anyone else?

---

### Post by Tundro Walker on 2007-10-23
Hey, Fuscia.

My sister had an old Olympus camera (with serial cable to hook to computer and everything...yeah, freakin old), and I was originally having trouble with it.

But, I got gtkam, and it detected it ok after fiddling around.  gtkam is a gui that uses the gphoto2 command-line program, and it has an extensive set of serial & usb cameras it can detect.

If I remember right, the hard part was just figuring out I had to use gtkam (which you can get in the repo's).  From there, it detected and d/l'ed the pics, but since it was over a serial cable, it tood like forever to post the thumbnails...  Let me rephrase that...when I originally got it going, it was taking so long to show a thumbnail that I thought the program had locked up.  So, I killed it and tried again.  When it did the same thing second time, I decided to just wait it out and see what happened.  About 10 minutes later, all 30-50 shots on the camera were showing up with thumbnails to peruse.  When I selected the ones to d/l to comp, it took a very long time for them to transfer via the serial cable (*ugh*).

I got tired of that, and decided to get my own digital cam.  Since I was already using Ubuntu, I made sure to get one that was recommended for Linux (got a Canon Powershot A460).  I took some photos, hooked it up via its USB cable, but nothing happened (I was expecting it to just auto-detect).  I opened up gtkam, but still nothing.

After a little web-surfing on the subject, I read someone having the same issue, and they said some cameras have a toggle to put them into "camera" mode for picture taking, and then to put them into "preview/view" mode to look at the pictures on the cam.  They said you had to put the camera into "preview/view" mode, then the camera would get detected by gtkam like an external hard drive that has pics on it (like flipping your iPod from music mode to storage mode to get it to detect like a hard drive).  

On my little Powershot, it was a knob on the back I had to rotate to a "play" button symbol, as opposed to the various camera icon symbols which made it shoot pics.  It's worked fine for me ever since.

Hope this helps.

---

### Post by fuscia on 2007-10-24
turns out to have been just a kde problem. as soon as i installed thunar, i was fine, so i ended up dumping kubuntu and installing xubuntu, and now, "god's in his heaven, all's right with the world". (funny how one thing can push you over the edge.) thanks for the response, tundro.

---

