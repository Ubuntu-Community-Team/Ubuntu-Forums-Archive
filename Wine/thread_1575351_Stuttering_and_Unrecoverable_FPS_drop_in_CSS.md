---
title: "Stuttering and Unrecoverable FPS drop in CS:S"
date: 2010-09-15
forum: Wine
---

### Post by tekpunk on 2010-09-15
I couldn't find any fixes that actually fixed my problem, so I'm starting a new thread.  CS:S at certain points in during gameplay will suddenly start stuttering and the FPS will drop to about 1 or 2.  Eventually I will be dropped from the server with the message "client timed out".  After that I have to restart steam to get CS:S to function properly again. It seems to be correlated with HE nades, but not always.

Specs:
nVidia gforce 6800
pentium 4 3ghz dualcore
1gb ram

Terminal output from multiple sessions can be found in the attachment (.txt).

Any help would be great!!

---

### Post by beastrace91 on 2010-09-17
What Wine version? What graphics driver version? Normal CSS or the CSS Beta? Are you running in DX9 or DX8(.1)?

Help us, help you,
~Jeff

---

### Post by tekpunk on 2010-09-18
-Wine 1.2
-NVIDIA accelerated graphics driver (version current)<--Changed from 173,   no noticeable difference.
-Normal CSS
-software dx9 (according to CSS settings)
-hardware dx8 (according to CSS settings)

---

### Post by tekpunk on 2010-09-21
Any ideas?

---

### Post by beastrace91 on 2010-09-22
> **tekpunk said:**
> Any ideas?

Try changing Wine versions also try launching CSS with the argument -dxlevel 81

~Jeff

---

### Post by tekpunk on 2010-09-25
How do I revert back to an older version of wine?

---

### Post by mrshroom on 2010-09-26
Have you set the renderer to opengl instead of the default dri?

---

### Post by beastrace91 on 2010-09-27
> **tekpunk said:**
> How do I revert back to an older version of wine?

**sudo apt-get remove wine***

Then install the older version you would like.

~Jeff

---

### Post by tekpunk on 2010-09-28
> **mrshroom said:**
> Have you set the renderer to opengl instead of the default dri?

How would I go about doing that?

---

