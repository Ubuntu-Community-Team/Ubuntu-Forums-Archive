---
title: "Transparency problem with Gimp for image manipilation."
date: 2009-09-05
forum: Ubuntu Studio
---

### Post by Omnios on 2009-09-05
Hi guys I am back to using Ubuntu , was using arch but want more stability because I started a business and need professional photo editing. 

 I noticed a problem with Gimp in I am doing some photo editing and am trying to combine some graphics where I have to add transparency to one of the graphics. The problem is that on some of the graphics when I open them the eraser with transparency will not work and it tries applying the set color to the eraser instead. I really need to get this solved as I have some production graphics for a webstore I am trying to prepare and want to get things finished to order some product. 

 Currently thinking it has something to do with the image color setting and played around with that but got no where with it.

 Your help would be greatly appreciated.

 Tom

---

### Post by ceciliaFX on 2009-09-05
I can't tell what the problem is blindly, but make sure that the image in question is Selected, make sure it has an alpha channel (right click on the layer in the layers window and if you need to ADD that alpha channel), and make sure the image is RGB and not indexed.

make sure the whole image is selected or NOT selected

---

### Post by ScorpKing on 2009-09-05
Something else that might help is to create a new transparent layer and then merge the transparent layer and the problem layer. Make sure that the transparent layer is below the problem layer before you merge them.

---

### Post by Spaceman9 on 2009-09-05
ceciliaFX is right. Just right click on the layer in the layer window and in the drop down menu left click on Add Alpha channel. Then you can use the Eraser Tool to erase any part of the image.

GIMP has a good user manual you can install from the Ubuntu repos. Also there's a book in the repos called Gorkking the GIMP. If you have Miro installed you can download tuts from Meet the GIMP and also youtube has some good tuts.

---

### Post by demuxer on 2009-10-29
ceciliaFX is the woman!
 I wonder how easy to resolve is that problem, was new for me and I found this post.
:o
thanks for your help

---

