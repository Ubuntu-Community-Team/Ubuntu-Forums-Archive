---
title: "Unofficial Snap Packaging for the GTK+ UVC Viewer(Guvcview)"
date: 2018-06-19
forum: Ubuntu, Linux and OS Chat
---

### Post by buo-ren-lin on 2018-06-19
After weeks of development and testing, I am thrilled to announce that the unofficial packaging work of the GTK+ UVC Viewer(a.k.a. Guvcview) has finally done.

[https://snapcraft.io/guvcview](https://snapcraft.io/guvcview)

Guveview is a USB Video Class(UVC) compatible camera viewer developed by Paulo Assis, aside from fundamental webcam application features like capturing a photo or video Guvcview also supports UVC Dynamic controls of Logitech products.

Unfortunately, the Guvcview distribution provided by the Ubuntu archive is often buggy and crashes a lot, which is the main motivation of the packaging (to allow users to install upstream released recent software).  Currently, we provide the current latest released version(2.0.5) and development revision(2.0.5-8-g9248669) via stable and beta channels and provide Intel x86/AMD64/armhf and ARM64 architecture builds for general desktop and embedded system users.

Although there is no progress as of now, we are working with the upstream to transfer the packaging work to them, this allows the greatest extent of possibility that the users of the feature-freezed GNU+Linux distribution can access the latest release of the upstream software.

### How to Install ###
```
# Install the snap package #
sudo snap install guvcview

# Connect the snap to optional security confinement interfaces #
## Required to enable the H264 Controls tab for cameras supporting H.264 hardware encoding ##
sudo snap connect guvcview:hardware-observe

## If you want to save captured media to `/media` or `/mnt` ##
sudo snap connect guvcview:removable-media
```

### Related Links ###
* Packaging recipe source code  
  [https://github.com/Lin-Buo-Ren/guvcview-snap](https://github.com/Lin-Buo-Ren/guvcview-snap)
* Upstream project  
  [https://sourceforge.net/projects/guvcview](https://sourceforge.net/projects/guvcview)

### Support ###
Please refer our project's issue tracker  
[https://github.com/Lin-Buo-Ren/guvcview-snap/issues](https://github.com/Lin-Buo-Ren/guvcview-snap/issues)

or create a new topic under `snap` category in the Snapcraft Forums  
[https://forum.snapcraft.io](https://forum.snapcraft.io)

### Join Snapcrafters ###
[https://forum.snapcraft.io/t/join-snapcrafters/1325](https://forum.snapcraft.io/t/join-snapcrafters/1325)

---

