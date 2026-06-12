---
title: "[gazp9] Volume keys &quot;stick&quot; sometimes"
date: 2013-07-11
forum: System76 Support
---

### Post by rorschachwalter on 2013-07-11
Several times now, my volume has "stuck" when I've used the function keys to increase or decrease it. This means that sometimes the volume goes all the way down rapidly, which is just a slight annoyance. However, it also means the volume will rapidly increase *all the way to full*, which hurts my ears and wakes up the other people in the house when the laptop is plugged into speakers.

Any idea if this is an issue with the function keys, or if this is maybe something to do with the system itself somehow hanging and repeating the input? (Although it doesn't hang with other input.)

Any idea if System76 considers issues like this, like the BIOS switch for the battery alarm, like the HDMI audio not working after suspend, like the internal mic not working until an external mic is plugged in, like the keyboard not registering keystrokes because of poor physical design, reasons to accept a return with reimbursed shipping? Seems like a lot of issues that aren't really considered part of a "working" product.

---

### Post by screaminj3sus on 2013-07-11
I had almost forgotten about this issue (had gotten used to using my function keys sparingly and cautiously to avoid it), it is indeed very annoying.

I have the same issue with my lemu4. also happens with the play/pause and mute keys. not only does it cause the issues you mentioned, but I've noticed while it happens it also freezes ubuntu's interface. The one really annoying issue I've had with this laptop. I contacted system76 support about it, and they at first could not reproduce it (I had to send them a freakin' video of me demonstrating it before they could reproduce it :p), but eventually could and told me it was a "firmware issue", and to make sure I always hold in the fn key long enough (no ****?) but never did anything to actually resolve it. It would be nice if system76 could give us a bios/firmware update to fix this... If any system76 employees see this I'd like to hear if this was ever looked into, because this is a pretty severe firmware bug that appears to affect multiple models.

It only happens if you hit fn + the function key too rapidly. If you make sure to hold in fn for a second and then hit the function it always works. but its definitely very annoying to accidently trigger. When it triggers to make it stop hit the same fn + function key combo you hit to trigger it, slowly, and it should stop.

I don't have any of the other issues you mentioned with my lemu4 at least.

---

### Post by screaminj3sus on 2013-07-11
Here was system76's response when I reported this issue to them in nov 2012: 

> Ian

I see, I think I've found out what's going on here.

Because of the way the firmware handles the Fn Hotkeys, the handling isn't meant to work when both keys are pressed at nearly the same time. Basically, the motherboard gets confused about whether you intended to type a ` or if you deliberately pressed the Fn key first (Since the normal F-keys don't have any letters assigned to them, you don't see this with them).

My suggestion would be to take care and make sure you're holding down the Fn+key while you press ` to play/pause audio. This ensures that the hotkey is handled correctly.

At the very least I'd hope they fix the issue in future models...

---

### Post by rorschachwalter on 2013-07-12
> **screaminj3sus said:**
> It only happens if you hit fn + the function key too rapidly. If you make sure to hold in fn for a second and then hit the function it always works.

This is very useful. Thank you.

Although it actually makes me even more frustrated that this is a known issue with System76 machines and that they continue to sell them without fixing the problem.

---

### Post by isantop on 2013-07-12
We hadn't received any reports about problems with the Fn keys. We're currently working on a fix for the beeping issue, and will post an updated BIOS for people affected by this issue. If you're both having the problem, then go ahead and open a support ticket about this and we'll get it added to the queue. It may also be that you have a faulty keyboard, which can be replaced pretty easily.

---

### Post by screaminj3sus on 2013-07-12
> **isantop said:**
> We hadn't received any reports about problems with the Fn keys. We're currently working on a fix for the beeping issue, and will post an updated BIOS for people affected by this issue. If you're both having the problem, then go ahead and open a support ticket about this and we'll get it added to the queue. It may also be that you have a faulty keyboard, which can be replaced pretty easily.

Have you tried to reproduce this on a system76 machine? It doesn't appear to be a faulty keyboard, the keys never "physically" stick, it only happens with the fn keys, and only happens when you very quickly hit the fn key + the function key in quick succession, as opposed to holding the fn key for half a second or so and then hitting the fn key. the firmware seems to get "confused" when this happens. In my original support ticket I posted two videos showing how to reproduce it (one a screen capture, one actually showing the keyboard): 

[http://www.youtube.com/watch?v=52TaFzCDDkA&feature=youtu.be](http://www.youtube.com/watch?v=52TaFzCDDkA&feature=youtu.be)

[http://www.youtube.com/watch?v=5q7kzKTeTxo&feature=player_embedded](http://www.youtube.com/watch?v=5q7kzKTeTxo&feature=player_embedded)

The second one shows what to do on the keyboard to reproduce it. The videos also show how in addition to causing a "repeating action" like constant play/pause toggling, it also freezes unity because of the constant actions. You will also notice in the video when I reproduce it, I very "lightly" hit the keys to reproduce it, making it unlikely that the key is actually sticking or something.

---

### Post by isantop on 2013-07-12
Now that I look at the problem, we've actually seen this before, and it's due to a limitation in the way hotkeys are processed at the hardware level. That said, it's pretty easy to avoid it, and you should be able to get accustomed to it pretty quick. 

The beeping issue is definitely a bug, and we hope to have a fix available soon.

WRT the OP's other issues (Audio, etc.), I think they may be caused by a faulty update. Testing with a live environment would be the best way to single this out. [s]I can definitively say that these issues aren't occuring on our systems here in the office, so if they still have issues in the live desktop, then there's likely a hardware problem which would be covered for free repair under the warranty.[/s]EDIT: Actually, these were replciated, but they're being worked on for the next version of the driver and will be fixed soon.

---

### Post by rorschachwalter on 2013-07-12
So then System76 can't fix the keyboard issue, because it's a problem at the hardware level?

If not, does System76 have anything they *can* do for customers who don't find "you should be able to get accustomed to it" a viable solution?

The keyboard also requires keys to be pressed either quite hard or directly in the center in order to register keystrokes. It seems like it's just bad hardware, and it's something that it seems customers are justified in expecting better of. Maybe replacing Clevo's keyboard would be good going forward, if possible, or just moving away from Clevo entirely somehow.

In the meantime, the keyboard in the Gazelle is obviously bad hardware, and I'm left wondering what I'm supposed to do about it. Or, perhaps more accurately, what System76 should be doing about it.

---

### Post by isantop on 2013-07-15
I'm thinking you may have a bad (defective) keyboard. Do you have a support ticket open on it?

---

### Post by rorschachwalter on 2013-07-15
There's no ticket on it -- notebookcheck.com, numerous forums and other users, have complained about the same issues. I'll open a ticket now, but it seems it's just the way the hardware is.

---

