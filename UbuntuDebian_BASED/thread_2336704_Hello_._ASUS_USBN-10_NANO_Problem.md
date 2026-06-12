---
title: "Hello . ASUS USBN-10 NANO Problem"
date: 2016-09-10
forum: Ubuntu/Debian BASED
---

### Post by dani2004 on 2016-09-10
Hello. I am new in ubuntu forums and i hope you guys can help me in a problem. I saw you help a different guy here on topic : [https://ubuntuforums.org/showthread.php?t=2199100&page=3](https://ubuntuforums.org/showthread.php?t=2199100&page=3) and [https://ubuntuforums.org/showthread.php?t=2241067&highlight=.+ASUS+USBN-10+NANO](https://ubuntuforums.org/showthread.php?t=2241067&highlight=.+ASUS+USBN-10+NANO) , but it doens't work for me.

I have the same problem with the ASUS USBN-10 NANO : [https://www.asus.com/Networking/USBN10_NANO/](https://www.asus.com/Networking/USBN10_NANO/). Kali Linux don't recognize it and i don t know why. When i open terminal and list lsusb , it doesn't appear there.
Hope you can help me.

Thank you in advance guys.

---

### Post by wildmanne39 on 2016-09-10
*Thread moved to **Ubuntu/Debian BASED**.*

Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by dani2004 on 2016-09-10
[ATTACH]271062[/ATTACH]

---

### Post by ajgreeny on 2016-09-10
Nothing showing there either; you appear not to have a wifi adapter that is being detected.

Have you tried a live Ubuntu 16.04 OS to see if Ubuntu detects the adapter?  There are sometimes big differences in OSs, even those derived from and built upon Ubuntu.

---

### Post by wildmanne39 on 2016-09-10
Are you running ubuntu in virtualbox? are you trying to set wireless up in virtualbox?

When you ran the wireless script did you have the usb adapter plugged in?
Thanks

---

### Post by dani2004 on 2016-09-11
@ajgreeny I will try now.
@Wild Man. Yes , I'm running Kali Linux in virtual box. My bridge adapter from laptop works fine and i can access the internet ( wire connected ) . I want to set wireless up . Yes , it was plugged in.
I ran another wireless script right now. I think it's like the other.
[ATTACH]271069[/ATTACH]
When I try to attach the device in virtualbox, it give me this error: USB is busy with the previous request. Try again later.

Update : @ajgreeny Same Result. Ubuntu don't recognize it.

Update 2 : Finally i think I got it working. It was a problem from VirtualBox with USB filters. The solution is here if anyone is facing with this problem:
[http://superuser.com/questions/683034/oracle-virtualbox-connecting-usb-device](http://superuser.com/questions/683034/oracle-virtualbox-connecting-usb-device)
[https://forums.virtualbox.org/viewtopic.php?f=6&t=39104#p176270](https://forums.virtualbox.org/viewtopic.php?f=6&t=39104#p176270)

Thank guys for trying to help me.

---

### Post by wildmanne39 on 2016-09-11
I was suspecting an issue with virtualbox and usb being read correctly. I am glad you got it working.
Enjoy!

---

