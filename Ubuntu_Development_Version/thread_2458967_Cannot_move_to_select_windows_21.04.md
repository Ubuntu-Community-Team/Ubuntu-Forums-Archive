---
title: "Cannot move to select windows 21.04"
date: 2021-03-07
forum: Ubuntu Development Version
---

### Post by tj-1 on 2021-03-07
Hello. I am unable to move windows without pressing the "super" key and i am unable to switch windows by clicking on them. This first occurred on Friday March 5th. I saved by data then reinstalled Ubuntu today and after updating, I have the same issue. I assume this is related to an update in gnome but I was not able to find any threads on this topic. I assume this problem is not unique to me as I have pretty typical hardware and this is a fresh installation. I have also tested different graphics drivers including Nvidia proprietary and Nouveau. 

Any help or confirmation I am not alone with this would be appreciated. Thank you.

[COLOR=#808080]Update: I "solved" the issue by installing proposed updates. Can anyone point me to where I would see discussion on a bug like this? My searches came up with nothing.[/COLOR]

Update 2: After a reboot, the issue came back. It appears to come and go but mostly exists. Everything may work normally for a few minutes then when I open a window such as the terminal, windows stop responding to click-drags and change focus.

---

### Post by Wise Ferret on 2021-03-08
This seems to be the problem reported [here]("https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1917926").

---

### Post by Frogs Hair on 2021-03-08
Confirmed on Ubuntu Budgie  as well.

---

### Post by corradoventu on 2021-03-08
Can confirm the problem in Xorg. Problem does not occur in Wayland.

---

### Post by Frogs Hair on 2021-03-10
Fixed after updates.

---

