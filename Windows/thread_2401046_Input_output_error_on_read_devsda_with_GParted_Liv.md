---
title: "Input output error on read /dev/sda with GParted Live"
date: 2018-09-12
forum: Windows
---

### Post by lcfiorini on 2018-09-12
Hello everybody,

I've been trying to reinstall Windows on a i5 Dell Vostro 260S with GParted live, but everytime I boot it on a DVD it fails to detect the WD 1.0 Tb disk. It displays several messages of input/output errors that I click on "Ignore". They also show the Retry option, but if I click on Retry it enters a loop asking me to retry it again and again and again. I've already read some similar problems here and the corresponding outputs, but whenever I type them I get different results without a distant hint of what to do with them. Here are the threads I've already read unsuccessfully:

[https://ubuntuforums.org/showthread.php?t=1710706](https://ubuntuforums.org/showthread.php?t=1710706)
[https://ubuntuforums.org/showthread.php?t=1778717](https://ubuntuforums.org/showthread.php?t=1778717)

Thank you so much.

---

### Post by yancek on 2018-09-13
What happens when you simply boot the windows install DVD?  What are you trying to do with GParted, create partitions?  Do you have any OS on the computer or the drive you refer to if it is a secondary drive?  When you say it fails to detect the drive, are you referring to the windows installer/GParted or both?  Is there anything (data, another OS) on the WD drive?  You might boot GParted and post an image of your drive(s) which might help someone to suggest something.

---

### Post by lcfiorini on 2018-09-13
I'm just trying to reinstall Windows 7 with its original factory standards. Later on I plan to update to Windows 10. But I need to reformat the HD in order to use the provided Windows 7 boot CD. Whenever I try to run Gparted id displays several times the message "Input/Output error during read on /dev/sda1". Just like this picture here [https://i.stack.imgur.com/LI4Jb.png](https://i.stack.imgur.com/LI4Jb.png)

It also displays another similar message with a yellow attention triangle: "Error fsyncing/closing /dev/sdb1: input/output error"

Very similar to this picture here [https://i.stack.imgur.com/2B0Eq.png](https://i.stack.imgur.com/2B0Eq.png)

---

### Post by howefield on 2018-09-13
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2018-09-13
Once again, what happens when you boot and try to install from the windows CD/DVD?  Generally, booting it and starting the install should install and overwrite everything on the disk.  Does your windows installation disk not boot?  I don't understand why you think you need to reformat with GParted, you should be able to do that with the valid windows installation DVD.

---

### Post by lcfiorini on 2018-09-13
Just trying it. I will post here any news as soon as I get something.

---

### Post by lcfiorini on 2018-09-14
Voilà! Windows 7 setup DVD has just made it! Thank you everybody for the attention. I still have lots of things to do with Dell support, I just can't install any of their drivers/programs. See you all.

---

