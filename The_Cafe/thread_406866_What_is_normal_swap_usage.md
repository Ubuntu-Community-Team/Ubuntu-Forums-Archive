---
title: "What is normal swap usage?"
date: 2007-04-11
forum: The Cafe
---

### Post by FuturePilot on 2007-04-11
I've been using Edgy lately on my laptop with 768MB of RAM and noticed that if I leave it on overnight I'm using around 8MB of swap the next morning. And I'm not using Beryl or anything. But when I used Dapper I could leave it on overnight with Beryl and XGL running and the next day there would still be 0 swap used. Did something change from Dapper to Edgy? Is this normal swap usage? Should I even be concerned about this? I've been playing around with the swappiness to see if it changes anything. It just seems to me that if there's any swap usage at all it means a decrease in performance.

---

### Post by dbbolton on 2007-04-11
i typically use about 70-150 MB of swap

---

### Post by mstlyevil on 2007-04-11
> **FuturePilot said:**
> I've been using Edgy lately on my laptop with 768MB of RAM and noticed that if I leave it on overnight I'm using around 8MB of swap the next morning. And I'm not using Beryl or anything. But when I used Dapper I could leave it on overnight with Beryl and XGL running and the next day there would still be 0 swap used. Did something change from Dapper to Edgy? Is this normal swap usage? Should I even be concerned about this? I've been playing around with the swappiness to see if it changes anything. It just seems to me that if there's any swap usage at all it means a decrease in performance.

8 MB of swap is not all that uncommon even with plenty of RAM. RAM usage fluctuates so at times you may be using more than you realize.

---

### Post by FuturePilot on 2007-04-11
Ok, did anything change from Dapper to Edgy though? Or could this be that Edgy just has some more stuff in it than Dapper? It seems that I almost never used swap with Dapper.

---

### Post by mstlyevil on 2007-04-11
Edgy has more driver modules and processes than Dapper does. That is the cost one pays for an operating system that improves hardware support and adds new functionality. 

I am running Debian right now and it uses about half the RAM that Edgy does upon initial boot. Debian has a lot less driver modules because of it's stance on free software.

---

### Post by FuturePilot on 2007-04-11
Ah, that's probably the reason. I though Edgy might be a little more robust than Dapper was.

---

### Post by yatt on 2007-04-11
I don't have a swap partition, but I remember that Dapper liked to split it about 70-30.

---

