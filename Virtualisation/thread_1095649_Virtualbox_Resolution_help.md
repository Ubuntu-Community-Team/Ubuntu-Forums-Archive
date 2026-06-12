---
title: "Virtualbox Resolution help?"
date: 2009-03-13
forum: Virtualisation
---

### Post by Ebicoustic on 2009-03-13
Hi I am running Vista Home Premium 64bit as my host OS and using Virtual box to run Ubuntu 8.10. My resolution in virtual box cannot go above 800x600 and I have a monitor capable of producing 1280x800. I have tried editing xorg.conf but when I use gksu gedit /etc/x11/xorg.conf it opens to a blank document. I have tried the whole guest additions and nothing happens. I have been looking through these forums and google for three days now and finally am posting. I am somewhat new to linux and am having one heck of a time with this. I have tried everything and nothing is happening. I keep trying to edit xorg.conf and look through that like I said but there is nothing, absolutly nothing in the document. I am at the point of exploding and throwing my computer out the window lol. Please someone hellp me. All I wish to do is to change the resolution of the window to something higher than 800x600 cause lets face it, one cannot do anything in that small of a window and a window this small....is horrible...please help!

---

### Post by Ebicoustic on 2009-03-14
nevermind found out how...
drag and drop the vboxlinuxaddition right into terminal while using root...guest addition fixed itself...

---

### Post by konqueror7 on 2009-03-14
just a note, you opened **/etc/x11/xorg.conf** instead of **/etc/X11/xorg.conf**...;)

---

