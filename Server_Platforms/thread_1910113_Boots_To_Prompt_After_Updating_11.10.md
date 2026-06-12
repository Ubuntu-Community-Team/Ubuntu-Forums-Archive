---
title: "Boots To Prompt After Updating 11.10"
date: 2012-01-16
forum: Server Platforms
---

### Post by younglemon on 2012-01-16
I originally posted this in the new section but I didn't know if here would be more appropriate. 
 
**Boots To Prompt After Updating 11.10** 
I just updated software on my Ubuntu 11.10, 64 server edition. I upgraded to 11.10 when it was released and have been running without issue. I just updated software and now it boots to the text prompt. I can log in and everything seems to be there it's just that the desktop (I think its called Unity) is gone. 

I've seen several issues with graphics cards posted and I just don't know how this could have happened.

I apologize for repeated redudant questions. I'm sure that the answer is posted and I am missing it and I will continue to search the threads. In the meantime I'm going to attempt a new post.

---

### Post by CharlesA on 2012-01-16
Did you have any proprietary drivers installed? Does switching to tty7 with ctrl + alt + f7 do anything?

---

### Post by wyliecoyoteuk on 2012-01-16
A bit puzzled. The server edition doesn't have a GUI.

---

### Post by younglemon on 2012-01-16
When I recently connected the Western Digital My Book, there may have been drivers installed at that time, yes.  The drive worked and the system was recycled several times before the software update and issue began.
 
Thanks for yours and everyone's input.  I think I may have only made it worse by trying to determine what's happened.  I'll know soon.

---

### Post by CharlesA on 2012-01-16
> **wyliecoyoteuk said:**
> A bit puzzled. The server edition doesn't have a GUI.

Aye, that's true. I had thought that the OP has installed a GUI on it.

> **younglemon said:**
> When I recently connected the Western Digital My Book, there may have been drivers installed at that time, yes.  The drive worked and the system was recycled several times before the software update and issue began.
 
Thanks for yours and everyone's input.  I think I may have only made it worse by trying to determine what's happened.  I'll know soon.

I was talking about graphics drivers, but Ubuntu server doesn't have a GUI unless you install one yourself.

---

### Post by younglemon on 2012-01-16
I must have.  Do you know of a way I can tell?

---

### Post by wyliecoyoteuk on 2012-01-16
You could try 

sudo apt-get install ubuntu-desktop

---

### Post by younglemon on 2012-01-16
Thanks, it says that its already at the latest version.  Maybe I have to invoke it somehow?

---

### Post by younglemon on 2012-01-16
So this did it, thank you Charles.  I tried several things but it came back to Ctrl + Alt + F7.  What exactly worked here, can you explain it?

---

### Post by younglemon on 2012-01-16
So this did it, thank you Charles. I tried several things but it came back to Ctrl + Alt + F7. What exactly worked here, can you explain it?
 
 
It still has some problem and that may be  the result of attempting to figure out what happened.  It did go back into the desktop though and that is where its now reporting that the system experienced an error...wow!

---

### Post by CharlesA on 2012-01-16
Ctrl + Alt + f7 just switches to a different tty, the GUI usually runs on tty7. Not sure why it wasn't selected in the first place tho.

---

### Post by younglemon on 2012-01-28
Thank you very much!  All things still seem to be better and working well now, I am grateful for your support and the suppor of all that replied.

---

