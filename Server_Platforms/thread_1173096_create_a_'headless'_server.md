---
title: "create a 'headless' server"
date: 2009-05-29
forum: Server Platforms
---

### Post by andyrowe on 2009-05-29
I have a storage server with ubuntu server 9.04 loaded and running pretty well. I can access the box remotely and soon will stick it in the back room with the other servers. Can I just restart the computer with no monitor, keyboard or mouse plugged in? Will the server run normally or is there something else I need to do to configure it to be 'headless'? (I assume that is the meaning of the term)

---

### Post by trundlenut on 2009-05-29
You may need to change the bios settings or it might complain about the lack of keyboard.  I have an old proliant 800 and that works fine without a keyboard/mouse and monitor.

---

### Post by andyrowe on 2009-05-29
well... I guess I could leave a keyboard plugged into it. It's the monitor that I don't have room for as the only thing laying around are old CRTs

---

### Post by grantemsley on 2009-05-29
Before you move it, try turning the system on with no keyboard and mouse (just the power cable and monitor).  If you don't get any errors, you're all set.

If you DO get an error like "No keyboard found. Press F1 to continue", you have to change a setting in the BIOS.  Usually it's on the very first page called "Halt on Error" or something to that effect.

---

