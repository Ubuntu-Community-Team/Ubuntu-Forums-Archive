---
title: "Nvidia-current reverted back in QQ."
date: 2012-10-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-10-06
Nvidia-current is reverted back to the version 304.43 to cope with nvidia-cuda-toolkit.

Here:
[https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.51.really.304.43-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.51.really.304.43-0ubuntu1)

---

### Post by mc4man on 2012-10-06
The revert was in response to this bug (only affected unity
[https://bugs.launchpad.net/unity/+bug/1057000](https://bugs.launchpad.net/unity/+bug/1057000)

---

### Post by grahammechanical on 2012-10-06
I have just read the bug report. Interesting reading. This is what concerns me:

The bug is reported on 2012-09-26 as relating to version 304.51 of the Nvidia driver that is being pushed out by the ubuntu-x-swat ppa. Which I do not have enabled on this 12.10 install.

So, why did I get this particular driver installed on my system with yesterday's standard update.

I note this post in that bug report:

> Looks like Alberto has already uploaded 304.51 to quantal.

The comment was made in a post on 2012-10-05.

So, why did a driver with a known issue get pushed into the standard Quantal repositories?

Just when I thought it was safe to go back into the Nvidia water!

If I chose to tick the proposed repository box or install an experimental ppa then I expect problems. And I ought to be ready to fix it.

Surely the purpose of using these experimental repositories is to identify issues before they get into the main trunk.

Regards.

---

### Post by robtygart on 2012-10-06
I am still using 304.48 (Kubuntu) with out a problem, I never got around to the offical upgrade. 

Since I am Kubuntu I shoould be fine right?

---

### Post by Rukiri on 2012-10-06
I installed the driver from nvidia 304.51, and there's really no bugs that could be found.. 
I wonder if there running mid-range cards? As there are known issues with the 4x and 5x series but 6X is pretty gosh darn stable.

---

### Post by funicorn on 2012-10-06
I choose to hold nvidia-current, 304.51 works fine, better thant 304.43.

---

