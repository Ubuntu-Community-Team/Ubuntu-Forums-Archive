---
title: "exim vs postfix"
date: 2009-02-23
forum: Server Platforms
---

### Post by shoaibi on 2009-02-23
I have Ubuntu 8.04 Hardy serving as a server for sometime now. This machine has rkhunter which depends on exim4. Issue is i need to install postfix on it for some bussiness of mine, postfix conflicts with exim and tries to remove it, which in turn removes rkhunter. I dont want this. 
Any method to get rkhunter and postfix working with each other?

---

### Post by songshu on 2009-02-23
if i'm not mistaking rkhunter depend on a MTA.

but that could be any MTA you want, remove exim, install postfix first and then install rkhunter.

that should do the trick

---

### Post by shoaibi on 2009-02-23
yup, thanks. It works..

---

