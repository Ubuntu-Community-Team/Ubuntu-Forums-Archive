---
title: "KMPlayer x64 image retention problem"
date: 2019-10-29
forum: Windows
---

### Post by bobkemp on 2019-10-29
Hi -

 I'm using the latest update of KMPlayer x64 on a Windows 10 Dell x15. 

After playing Microsoft Solitaire Collection, I play a video and the cards are ghosted inside the KMPlayer full screen display. At first, I thought it might be the Dell computer flat screen display with a burned in image, but now I'm not so sure. 

The size of the apparent  burned in image is larger than the actual size in the game and in a different location on the player screen than the game screen. It's possible that the game is using a resolution different from KMPlayer (1920x1080), but I don't see how that would cause the image retention to be in a different spot on the screen. A burned in image should show up in exactly the same spot as it is a fault related to the actual pixels of the screen.

My first thought past the display fault was that a screen buffer holding the game image wasn't being cleared by the Player and was being summed into the final video image. 

The image seems to fade over time. This would make it seem like a display image retention fault. Yet the image doesn't show up using the Dell display diagnostic start up  test of single color screens.

It almost looks to me as though some transparency switch is being set which overlays the game buffer on top of the Player display and at some point in the Player running, that buffer is being cleared or overwritten by the Player. 

Anyone else experiencing this?

---

### Post by uRock on 2019-10-29
I see mention of Windows 10 and no mention of a Linux distro. Moved to **Windows** sub-forum.

---

