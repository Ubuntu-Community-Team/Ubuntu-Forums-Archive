---
title: "Help: Audio, webcam, wireless network, mousepad not working after a sudden blackout"
date: 2014-04-03
forum: Ubuntu, Linux and OS Chat
---

### Post by Jezebel_Jimenez on 2014-04-03
Okaay, so I'm currently a Lubuntu-user and the title pretty much says the problems with my laptop as of the moment. I was just surfing the next approx. 10 hours, my audio, webcam, mousepad, and my wireless network worked perfectly fine then suddenly, there was a blackout. When the electricity got back a couple of minutes later, I turned my laptop back on. I immediately noticed that something was wrong. I NEED HELP. T.T

---

### Post by ajgreeny on 2014-04-03
Please do not multi-post the same thread on several forum sections; it dilutes responses and makes it difficult to follow through on this thread.

However, to try to sort out your problem begin by booting to a live system and in the terminal of that run command ```
sudo fdisk -l
``` to find your ubuntu root partition, and having found that ```
sudo e2fsck /dev/sdx#
``` where sdx# is your root partition.  Report back any problems it finds.

---

### Post by coffeecat on 2014-04-03
Thread closed.

This section is not for technical support and you have posted duplicates elsewhere in the support areas.

---

