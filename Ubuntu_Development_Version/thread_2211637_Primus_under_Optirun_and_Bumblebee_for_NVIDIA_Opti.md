---
title: "Primus under Optirun and Bumblebee for NVIDIA Optimus garbled image"
date: 2014-03-17
forum: Ubuntu Development Version
---

### Post by Furyhunter on 2014-03-17
Hello, I'm trying to run a glxgears program with bumblebee-nvidia (the proprietary driver plugin) and it produces the following garbage on the screen (picking up whatever was underneath it):

[IMG]http://i.imgur.com/JkevymL.png[/IMG]

This worked perfectly under 13.10. I did a dist upgrade to 14.04 to give it a shot and everything else seems to work fine, but bumblebee does not. The program otherwise runs fine.

Is it possible that mesa is bugged? This seems similar to other KMS-related garbage that appears under the Intel driver. I'm thinking it may also be Primus's GL library is bugged.

EDIT: Shrinking the window displays the glxgears image every frame that the window is resized. It appears the image is not being refreshed correctly.

---

### Post by jayobroin on 2014-03-31
I'm experiencing the same problem since upgrading to 14.04.

primusrun ran perfectly with 13.10, but produces either a garbage image or blank screen when I run it since upgrading.

optirun still works fine, but as a test I tried changing optirun's back-end from VirtualGL to primus, which caused optirun to produce the same garbage output.

The solution I'm using for the time-being is using primusrun with the [FONT=Ubuntu Mono]PRIMUS_UPLOAD=1[/FONT] flag, which seems to correct the problem.

---

