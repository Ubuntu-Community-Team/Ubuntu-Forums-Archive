---
title: "PC hang-up 30min after boot + problems with GUI, solved by &quot;alt&quot; button"
date: 2020-01-23
forum: Ubuntu, Linux and OS Chat
---

### Post by alexgross88 on 2020-01-23
Dear Ubuntu-experts, 
I have two issues, one of which I could solve recently by accident with a rather strange workaround. Let me start with my specs:

OS: 
Ubuntu 18.04.3 LTS
64-bit

GNOME: 
3.28.2

PC: 
cpu: Intel® Xeon(R) CPU E5-2698 v3 @ 2.30GHz × 32
memory: 64GB
gpu: NVS 310/PCIe/SSE2 (display) + 2x Nvidia GTX 1070 (for CUDA)
OS on a 256GB SSD
Data on another 1TB SSD

Issues:
1) I recently installed a software called Scipion (for electron microscop analysis), written in Python and Java. I had big problems with the GUI running smoothly. In 80% of the cases, new windows wouldnt open, or if they open, they stayed grey. Only after several minutes (and sometimes not at all) would the GUI appear fully usable. I tried a lot of stuff, reinstallation, removing JAVA and reinstall, testing different java versions. 
The "solution" I discovered by accident. When I switched windows using "alt+tab", I realized that the GUIs started to work. So I figured, that whenever the GUI is stuck, i simply need to press "alt" to get it working. So now in 80% of the cases when I open a window, I need to press "alt" and everything works just fine.
This workaround allows me to work with the software, but is obviously somewhat cumbersome. 

Does anyone has ever experienced such a situation with other programs? I believe it has something to do with the OS and my workstation? Maybe sth with Python?

My second issue is similar strange:

2) When I boot my PC, it hangs-up after some time, between 10min and 60min. It just stops working, than after 1-2min it reboots. After that all is fine. I tend to leave my PC running to avoid being interrupted by a reboot after 1h of working on sth...

Does anyone has a tip for these issues?

Thanks in advance
Best
Alex

------------------------------------------------------------------

To increase chances for a solution (as I expect this issue not to be  too common) I posted the same question on other platforms:


[forum.ubuntuusers.de]("https://forum.ubuntuusers.de/topic/1-pc-haengt-sich-ca-30min-nach-dem-hochfahren-/#post-9129918")
[askubuntu_question1]("https://askubuntu.com/questions/1205404/problems-with-gui-workaround-by-pressing-alt-button-problem-still-exists")
[askubuntu_question2]("https://askubuntu.com/questions/1205379/pc-hang-up-30min-after-boot")

[ubuntu-forum.de]("http://www.ubuntu-forum.de/artikel/67947/1-pc-h%C3%A4ngt-sich-ca-30min-nach-dem-hochfahren-auf-2-gui-eines-programmes-nur-durch-alt-dr%C3%BCcken-aktivierbar-old-title-pc-hang-up-30min-after-boot-problems-with-gui-solved-by-alt-button.html#post400211")

---

