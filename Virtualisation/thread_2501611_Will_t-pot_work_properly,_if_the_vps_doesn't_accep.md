---
title: "Will t-pot work properly, if the vps doesn't accept nested virtualization via the SVM"
date: 2024-10-14
forum: Virtualisation
---

### Post by Xpdin on 2024-10-14
[COLOR=#0C0D0E][FONT=-apple-system]First, I have installed Windows, on the vps, but in order for the t-pot to work on Windows, Docker Desktop had to be installed.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]In order for Docker Desktop to work properly, the vps, has to have nested virtualization via the SVM flag enabled. Unfortunately, the vps stuff said, the nested virtualization via the SVM flag is disabled on their vps, and they can not start it. So I can not use t-pot on Windows, via the vps in discussion, because Docker Desktop can not work without virtualization via the SVM flag. After that, I have installed Ubuntu server on the vps . Considering the the vps can not enable virtualization via the SVM flag, will I be able to use t-pot on Ubuntu, considering that t-pot can not work on Windows withoud Docker Desktop, and Docker Desktop can not work on Windows if on the vps virtualization via the SVM flag, it is not turned on.[/FONT][/COLOR]

---

