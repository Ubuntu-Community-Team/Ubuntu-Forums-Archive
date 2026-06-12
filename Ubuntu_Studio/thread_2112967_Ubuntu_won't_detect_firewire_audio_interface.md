---
title: "Ubuntu won't detect firewire audio interface"
date: 2013-02-06
forum: Ubuntu Studio
---

### Post by mhs2000 on 2013-02-06
hi guys 
i have a big problem 
i want to use Focusrite Saffire Pro 40 in ubuntu but ubuntu wont detect my audio interface 
i follow this guide step by step but 

[http://www.audiorecording.me/install...ntu-11-10.html](http://www.audiorecording.me/install...ntu-11-10.html)

but when i enter the following command
ls -l /dev/fw*
the output is 

crw------- 1 root root 251, 0 Feb 3 10:43 /dev/fw0

/dev/fw1 doesn't create when i power on my audio interface  
what is the problem ?

---

### Post by jejeman on 2013-02-06
Check the cable.
Look in dmesg for clues.

---

### Post by jejeman on 2013-02-06
Now I looked at ffado.org and it says
> This device is NOT supported in 2.0. It was included in the 2.1 release that introduced DICE support.You should check it out
[http://www.ffado.org/?q=node/862](http://www.ffado.org/?q=node/862)

---

### Post by mhs2000 on 2013-02-06
> **jejeman said:**
> Now I looked at ffado.org and it says
You should check it out
[http://www.ffado.org/?q=node/862](http://www.ffado.org/?q=node/862)

thx man for reply .
what does that mean ?
what should i do now?

---

### Post by jejeman on 2013-02-06
Well, you can sit and wait for Ubuntu Studio to ship the 2.1.0 version of ffado in 13.04 or whatever version. Eventualy it will come.

Or you can try and compile it yourself either 2.1.0 or the latest development version.

Or find out there a already compiled version of 2.1.0 or later. for example from here [https://launchpad.net/~kxstudio-team/+archive/ppa](https://launchpad.net/~kxstudio-team/+archive/ppa)

---

### Post by mhs2000 on 2013-02-06
> **jejeman said:**
> Well, you can sit and wait for Ubuntu Studio to ship the 2.1.0 version of ffado in 13.04 or whatever version. Eventualy it will come.

Or you can try and compile it yourself either 2.1.0 or the latest development version.

Or find out there a already compiled version of 2.1.0 or later. for example from here [https://launchpad.net/~kxstudio-team/+archive/ppa](https://launchpad.net/~kxstudio-team/+archive/ppa)

thx man but my question is how the other people can use Focusrite Saffire Pro 40 in ubuntu 11.10 like who wrote this installation guide ??
[http://www.audiorecording.me/focusrite-saffire-pro-40-in-ubuntu-11-10-installation-guide.html]("http://www.audiorecording.me/focusrite-saffire-pro-40-in-ubuntu-11-10-installation-guide.html")

---

### Post by jejeman on 2013-02-06
If you read carefully you will se that he installed the latest svn version of FFADO. And that has nothing to do with the fact he uses 11.10. (regarding the FFADO version).
So, what I have said earlier still applies.

---

### Post by ttoine on 2013-02-07
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
Have a look at that. It should help you getting everything working.

---

