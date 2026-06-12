---
title: "edit LARGE picture"
date: 2009-07-06
forum: Ubuntu Studio
---

### Post by aeltester on 2009-07-06
Hey guys,

I made this 627 Megapixel Panorama view (from 50 10MP pictures) using Hugin. Now, 50 times 10 is only 500 Megapixels, you're right. The thing is that hugin dumbly adds large black areas where there is no picture.
So after creating a panorama with hugin, one has to crop the picture.
I have been using Gimp for that job. The problem: this panorama is a 2.6 GB tif file. I've only got 2 gigs of Ram.

Which program could I use to losslessly convert tif to JPEG (which is smaller, eh?)? convert says the picture is too large.
Which program would let me view the picture? digikam, eye of Gnome and gthumb won't.
Is there a tool for editing? gimp won't open that one because it appently tries to fully load it into ram.

should I give creating a 10 gig swap partition a shot?

thanks
:P

---

### Post by Cheesemill on 2009-07-06
You cannot convert losslessly to a .jpg
JPG is by definition a lossy format.

I think that any image editor that you try is going to attempt to load the entire image into RAM, so make sure that your RAM + swap is big enough for the task.

Increasing your /tmp may also help.

---

### Post by unutbu on 2009-07-06
aeltester,  Hugin itself can crop off the black part:

Click the Stitcher tab, then click the "Calculate Field of View" and "Calculate Optimal Size" button. Then click the "Preview panorama" icon in the tool bar. If you still see too much black around the edges, you can use the sliders to manually adjust the field of view. (Click the "Auto" button so see the effect of moving the sliders automatically.)

When you have the preview as you want it, then go back to the Stitcher tab and click "Stitch now!"

PS. Under the Stitcher tab, you can also manually set the "Panorama Canvas Size". This is the final width and height of your stitched panorama. So if ultimately you do not need a 2.6 GB final image, you can reduce the number of pixels here.

---

### Post by lukeiamyourfather on 2009-07-06
Assuming you're on a 64-bit system either get more memory or make your swap huge. There's no trick to working with a 500+ megapixel image, its just going to take more resources.

Some command line tools might make it a little quicker to work with like this if you just need to do basic operations like convert, resize, compress, crop. etc.

[http://www.graphicsmagick.org/](http://www.graphicsmagick.org/)

GIMP is a fully featured editor which might be overkill and use more resources than you need. I think GM is in the Ubuntu repositories too, but be aware that there's a 64-bit and 32-bit version that are separate installs. Cheers!

---

### Post by aeltester on 2009-07-06
thanks for all the constructive input guys!

> **Cheesemill said:**
> You cannot convert losslessly to a .jpg
JPG is by definition a lossy format.
oh... I thought 100% quality meant that...

> **Cheesemill said:**
> I think that any image editor that you try is going to attempt to load the entire image into RAM, so make sure that your RAM + swap is big enough for the task.

Increasing your /tmp may also help.
thanks, will try.

> **unutbu said:**
> aeltester,  Hugin itself can crop off the black part:

Click the Stitcher tab, then click the "Calculate Field of View" and "Calculate Optimal Size" button. Then click the "Preview panorama" icon in the tool bar. If you still see too much black around the edges, you can use the sliders to manually adjust the field of view. (Click the "Auto" button so see the effect of moving the sliders automatically.)

When you have the preview as you want it, then go back to the Stitcher tab and click "Stitch now!"

PS. Under the Stitcher tab, you can also manually set the "Panorama Canvas Size". This is the final width and height of your stitched panorama. So if ultimately you do not need a 2.6 GB final image, you can reduce the number of pixels here.
cool, thank you. but now that it has needed over 8 hours (on dual 3GHz with 1.5 gigs RAM left for hugin only) I'll probably keep your tip in mind for the next pans.


> **lukeiamyourfather said:**
> Assuming you're on a 64-bit system either get more memory or make your swap huge. There's no trick to working with a 500+ megapixel image, its just going to take more resources.

Some command line tools might make it a little quicker to work with like this if you just need to do basic operations like convert, resize, compress, crop. etc.

[http://www.graphicsmagick.org/](http://www.graphicsmagick.org/)

GIMP is a fully featured editor which might be overkill and use more resources than you need. I think GM is in the Ubuntu repositories too, but be aware that there's a 64-bit and 32-bit version that are separate installs. Cheers!
GM looks great! thanks so much! I just need to find out what /usr/bin/gm convert: Error fetching data for field "BitsPerSample". (a.tif). should be telling me.
do you have any suggestions?

thanks again

---

### Post by lukeiamyourfather on 2009-07-06
> **aeltester said:**
> 
GM looks great! thanks so much! I just need to find out what /usr/bin/gm convert: Error fetching data for field "BitsPerSample". (a.tif). should be telling me.
do you have any suggestions?


Is the image 8-bits per channel or 16-bits per channel? The Q8 is for 8-bits per channel images and the Q16 is for 16-bits per channel. Cheers!

---

### Post by aeltester on 2009-07-07
I made the pan by stitching JPEGs which are 8bits as I understand.
should the pan have the same amount?

ill try...

thanks again for your help

I tried:
/usr/bin/gm convert a.tif a.jpg                        

which threw the error.

I also tried:
/usr/bin/gm convert Q8 a.tif a.jpg
/usr/bin/gm convert Q16 a.tif a.jpg
/usr/bin/gm convert -Q8 a.tif a.jpg
/usr/bin/gm convert -depth 8 a.tif a.jpg

which all threw errors at me.
how should I use it?

---

