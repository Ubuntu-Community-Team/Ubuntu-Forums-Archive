---
title: "Add Software to Reconstructor ?"
date: 2007-05-23
forum: Ubuntu Customization Guide
---

### Post by Sentinel-Being on 2007-05-23
I need to create a live cd with certain tools developed in house at my company. This live cd will be used for disaster recovery.

Utilizing Reconstructor, How can I add .DEB files to the image? Or even a new directory with files? Is this possible?

I am using the newest version of reconstructor with the 7.04 Desktop ISO.


Thanks!

---

### Post by SgtDude on 2007-05-24
See this thread:

[http://ubuntuforums.org/showthread.php?t=449396&highlight=reconstructor]("http://ubuntuforums.org/showthread.php?t=449396&highlight=reconstructor")

Basically you'll need to decompress the liveCD filesystem onto your HD using reconstructor (third page of the GUI), then copy your .deb's into the LiveCD-to-be's filesystem ( /home/yourusername/reconstructor/root/ ), then use the terminal in Reconstructor (which chroot's the LiveCD-to-be's filesystem and lets you run stuff as if you were running it on the LiveCD) to install your deb's.

Please post here if you are successful.

---

