---
title: "Viruses and WINE"
date: 2012-05-29
forum: Security
---

### Post by ExSuSEusr on 2012-05-29
Here's a question....

This is a hypothetical story to a question that I don't quite know the answer to myself.  So, I thought this would be a good place to ask.

Let's say you're running Ubuntu.  You have a program you created an ISO image from, from your previous install of Windows.  You didn't realize it at the time, but the program you created the ISO image from had a Windows virus attached to it.

Ok...

Let's say the virus was a keystroke logger (that's all I could think of).  So, you open the program through WINE and at the same time you decide to check your bank account.  So you open a browser and go to your bank's web page.  

Now, since you have the program (with the virus attached) running - CAN it theoretically record your keystrokes and send your information to whomever?

What about if you are running a different Windows program through WINE.... CAN it theoretically do the same - even if the program with the virus is not running?

What about if WINE is not running at all?

Just a curiosity I had....

---

### Post by Hungry Man on 2012-05-29
Is the browser in WINE? 
If it is, yeah, you could potentially get keylogged.
If it isn't I seriously doubt it, especially if you aren't running WINE as root.

---

