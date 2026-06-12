---
title: "Display keeps jumping to Home Screen without input"
date: 2010-05-29
forum: Virtualisation
---

### Post by GeicoGecko on 2010-05-29
I'm running Ubuntu 10.4 under Virtual Box 3.2.0 on Windows 7 Eneterprise all running on a Samsung N110.

Since installing the Guest additions in Virtual Box, every time an application is launched, the application will be displayed for a couple of seconds and then the view jumps back to the home screen. I'm trying to ascertain what is causing the issue. 

If anyone has any suggestions I would really appreciate it.

---

### Post by cariboo on 2010-05-31
Since this is more a virtualization question than a netbook question, you may get better answers to your question here.

---

### Post by GeicoGecko on 2010-05-31
Thank you for moving it. 
 
I've managed to solve it tonight. I had to install 9.04 to work it out but it turns out that it's all to do with the 3d support in Ubuntu for vbox. Basically it doesn't work! I had enabled it early on but it's only when you install GA that the OS uses it and this is where things go wrong :(

---

