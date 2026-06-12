---
title: "porting problem ubuntu touch in my phone"
date: 2016-11-03
forum: Ubuntu Phone and Tablet
---

### Post by Jaladhi_R_Trivedi on 2016-11-03
I am trying to port ubuntu touch os on my samsung galaxy s2 GT-s7562 running on custom ROM android 4.0.1 . I successfully followed all the steps as outlined in [https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/?_ga=1.248674823.1673989972.1432205029](https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/?_ga=1.248674823.1673989972.1432205029) upto the command > adb reboot bootloader on giving this command the phone goes in the download mode and gets disconnected from the ubuntu desktop. So I can not proceed further. What should I do to overcome this obstacle? Kindly guide
There is one thing I forgot to tell I've rooted my android and has cwm recovery installed

---

### Post by krusty8 on 2016-11-05
> **Jaladhi_R_Trivedi said:**
> I am trying to port ubuntu touch os on my samsung galaxy s2 GT-s7562 running on custom ROM android 4.0.1 . I successfully followed all the steps as outlined in [https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/?_ga=1.248674823.1673989972.1432205029](https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/?_ga=1.248674823.1673989972.1432205029) upto the command  on giving this command the phone goes in the download mode and gets disconnected from the ubuntu desktop. So I can not proceed further.  

I'm really not a expert on this topic, but my understanding is that the phone is *supposed* to be disconnected from the desktop at this point. 

But, you might not be able to proceed with the fastboot command which is listed next, because I think samsung devices do not support fastboot. If I remember it right heimdal is the samsung equivalent to fastboot. What exactly you need to do with that, I really can't answer. I can only tell you that disconnection is expected at that moment and fastboot is unlikely to work.

> What should I do to overcome this obstacle? Kindly guide
There is one thing I forgot to tell I've rooted my android and has cwm recovery installed

You might want to talk to the people at ubports.com . Also, not sure how deep your background with porting on android is, but you might want to compile android (cyanogenmod) for your device first and install that in order to make your self familiar with some of the steps before porting ubuntu touch.

---

