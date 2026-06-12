---
title: "Console Settings.. width, height"
date: 2005-06-05
forum: Server Platforms
---

### Post by koan on 2005-06-05
Hello, I am running Ubuntu as a server.  Once in a while I need to do things directly on the server console, which is set to the default 80x25.

"resize" tells me I cannot resize a VT100 emulated console. Is there a way to change the console screen width and height?

I suspect it is a case of switching to an ega setting on the vid card, but I can't see how to do it.  resizecons isn't present.

Thanks,

koan

---

### Post by tonym on 2005-06-07
At boot time add vga=ask to the kernel string.  You will then get a choice of sizes.

---

