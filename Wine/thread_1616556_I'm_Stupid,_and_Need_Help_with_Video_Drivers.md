---
title: "I'm Stupid, and Need Help with Video Drivers"
date: 2010-11-08
forum: Wine
---

### Post by the rent is too damn high on 2010-11-08
I've read thread after thread after thread, trying to solve this with the wonderful information they give.  Yet, after a month of frustrating effort, I've accomplished nothing.  I'm not getting something, or perhaps my video card is just incompatible with Maverick.

I'm using Ubuntu 10.10 on a Dell Latitude D610, and the card is an ATI Radeon X300.

I'm asking simply, how do I get this dreadful thing to work?

---

### Post by Grenage on 2010-11-08
I love your username!

I've not had much recent experience with ATI/AMD cards, but what is happening on your machine?

---

### Post by the rent is too damn high on 2010-11-08
I've been wanting to run WoW through Wine for some time now, but it just spits back at me in the terminal:

```
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting 
err:module:LdrInitializeThunk Main exe initialization for L"C:\\program  files\\world of warcraft\\wow.exe" failed, status c0000005 
```

The WoW people told me it was a Wine problem, and the Wine people told me it was a driver problem.  So, after attempts to get fglrx or the legacy stuff working, trying to reinstall a possibly corrupt opengl32.dll, and even trying different emulators, I finally got frustrated and threw away all my fglrx stuff.  Now I'm getting this message when I try to run that program:

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  198
  Current serial number in output stream:  198
```

---

### Post by the rent is too damn high on 2010-11-09
Help?     :frown:

---

### Post by Grenage on 2010-11-10
I would imagine that you'd want to use fglrx, so getting that working would be my first step; as you're using wine, disabling compiz would be my second step.

It might be worth 'reporting' your post, and asking for it to be moved to the Wine forum.  It's more likely to et seen by Wine veterans.

---

### Post by uRock on 2010-11-10
Moved as per the OP's request.

---

### Post by handy on 2010-11-11
> **the rent is too damn high said:**
> I've read thread after thread after thread, trying to solve this with the wonderful information they give.  Yet, after a month of frustrating effort, I've accomplished nothing.  I'm not getting something, or perhaps my video card is just incompatible with Maverick.

I'm using Ubuntu 10.10 on a Dell Latitude D610, and the card is an ATI Radeon X300.

I'm asking simply, how do I get this dreadful thing to work?

You will have to uninstall the Catalyst proprietary driver & install the Radeon FOSS driver files.

The reason being that from Catalyst 10.2 (from memory) your GPU amongst others are no longer supported by the Catalyst drivers.

Fortunately for you the FOSS drivers (which have had a lot of help from AMD) are working nicely these days. They aren't as fast in 3D yet as Catalyst, but in most other areas for most AMD/ATi GPU's they are working extremely well.

You may find something of use in the OP of this thread:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

& if you have trouble installing the Radeon FOSS stuff, if you post in the above thread you are more likely to get some help in that regard.

All the best. :)

---

### Post by the rent is too damn high on 2010-11-11
That did not fix the problem Handy, the error stays exactly the same.  Let's see if the thread you suggested can help any.

---

### Post by handy on 2010-11-11
> **the rent is too damn high said:**
> That did not fix the problem Handy, the error stays exactly the same.  Let's see if the thread you suggested can help any.

Whilst ever you try to run Catalyst (fglrx) on current operating systems, you will continue to be stopped with errors as your card has not been supported by Catalyst for some time now.

---

