---
title: "Xorg for remote connections only"
date: 2008-09-22
forum: Server Platforms
---

### Post by unless on 2008-09-22
Hi all,

I've got a customer with a Dapper server. From time to time, I'd like to run X apps (like etherape) on the server, exporting the display to my own machine.

Since the server is headless, there's absolutely no need for more than the most basic of xorg installations; I just want to get port 6000 open. I'll never be using X physically from the server itself.

What is an efficient way to install xorg server on this machine that avoids as much fluff as possible (e.g., no font server if I can get away with it)?

Thanks in advance for any info or nudges in the right direction.

---

### Post by Yannick Le Saint kyncani on 2008-09-22
You only need xorg the the machine which holds the screen and keyboard.

That means you don't need to install xorg on the server.

No need to open any port on the customer box either, port 6000 needs to be opened on your box.
X apps running on the customer box will contact your box to ask about keyboard/mouse events and draw on the X server.

---

### Post by unless on 2008-09-22
Yannick,

Thank you for pointing me in the right direction! I'm up and running now. I've even managed to push the X application through an ssh tunnel from the server to my machine.

Thanks again.

---

