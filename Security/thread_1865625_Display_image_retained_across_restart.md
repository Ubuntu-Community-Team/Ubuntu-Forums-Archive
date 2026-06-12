---
title: "Display image retained across restart"
date: 2011-10-20
forum: Security
---

### Post by KonfuseKitty on 2011-10-20
Yesterday I re-installed Ubuntu 10.10 and upgraded to the latest graphics driver (11.9) for my integrated ATI card from AMD. Just now, as I restarted the computer after some installations, after logging in, for a fraction of a second the image of the display as it was before restart flashed - the browser window with the website it was open on, a file manager window in front of it. I recognised the view from how it was less than a minute before. How is this possible? Is the driver caching the view? Could this be a security issue?

---

### Post by CharlesA on 2011-10-20
Probably just the video card flushing the memory.

---

### Post by KonfuseKitty on 2011-10-20
Could you explain? How can the memory contents survive across restart? BTW, I tested it again just now and it happened again. Never noticed this before.

---

### Post by CharlesA on 2011-10-20
I'm not quite sure why it happens since I haven't had it happen to me, but I seem to recall a couple threads about it popping up from time to time.

---

### Post by OpSecShellshock on 2011-10-20
Try shutting down completely rather than restarting. Wait for a few minutes, then start up again, and see if it still happens.

---

