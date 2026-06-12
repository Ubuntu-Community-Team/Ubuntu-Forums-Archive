---
title: "Firestarter Configuration"
date: 2008-05-16
forum: Security
---

### Post by LAKOTH on 2008-05-16
Hi i installed the firestarter firewall but i dont know if its working on not. for one it does not show incoming or outgoing traffick at all its says its on though. how should i configure it or what should i do so that my firewall works correctly. Plus i did the Gibson test which said that my port one was closed and not stealthed what does this mean and should i be worried or do something?

---

### Post by brian_p on 2008-05-17
> **LAKOTH said:**
> Hi i installed the firestarter firewall but i dont know if its working on not. for one it does not show incoming or outgoing traffick at all its says its on though. how should i configure it or what should i do so that my firewall works correctly. Plus i did the Gibson test which said that my port one was closed and not stealthed what does this mean and should i be worried or do something?

Sorry, I do not use firestarter so cannot really help there. A closed port will return a response to a request; a stealthed port does not but in neither case can a connection be made from outside to your machine. So there is no need to be worried or do anything about it.

---

### Post by hyper_ch on 2008-05-17
are you sure you need firestarter at all?

---

### Post by Meson on 2008-05-18
Closed vs Stealthed is of debatable importance.  Most likely you don't even need firestarter though, Ubuntu isn't installed with any open port.

Also, if you have a home router, or are on some sort of lan, the firewall test probably won't even touch your firewall ... you're testing one closer to the internet.

---

