---
title: "Camera Resolution"
date: 2007-04-08
forum: System76 Support
---

### Post by chooseopen on 2007-04-08
I am using camorama to play around w/ my Gazelle Performance's built-in webcam.  It seems to have very poor resolution. 
By default camorama is capturing at 320x240.  I thought this camera was capable of providing a better resolution than that.  Has anyone had any luck with getting better pictures/video than the sample one attached below?

Thanks
Jason

---

### Post by thomasaaron on 2007-04-09
If you go to VIEW and select LARGE, you can get 640x480.

Best,
Tom

---

### Post by klato on 2007-04-09
I tried changing view size in camorama, but it always bugs out and gives me an error message "Uable to capture image" then camorama closes.  Tried both small and large view with the same results.

---

### Post by chooseopen on 2007-04-09
Same here.  Choosing Small or Large, results in an error.  
Interestingly, the little graphic on the lens cover has the word "megapixel" which would indicate a better resolution than 640x480, right?  640x480 is commonly referred to as "VGA" in the digital camera arena....

-Jason

---

### Post by unique on 2007-04-10
Hey guys!
I was messing around with the camera on my Gazelle Performance...


Try this...  Open a Terminal and paste this into it.
```
camorama -M
```

You should have 640x480 now...   :)

And if you want it all the time just right click on your Applications menu and choose "Edit Menus"  and choose "Graphics" then right click on "Camorama Webcam Viewer" and choose properties.  Then just add -M in the Command line. 

So you should have camorama -M  

Save it and then when you click Applications, Graphics, Camorama Webcam Viewer it will always open at 640x480

---

### Post by jparadis on 2007-04-11
Hi,
Thanks for the camorama -M trick. The only problem is my color gets all out of wack when I run camorama -M. I get a 640x480 image but the problem is I'm blue. Kind of like the alien in the Enterprsie tv show. :confused: 

jp

---

### Post by klato on 2007-04-11
Cool that -M trick works here too...but I'm also pretty blue

---

### Post by unique on 2007-04-13
> **klato said:**
> Cool that -M trick works here too...but I'm also pretty blue

To fix the blue look right click in the effects pane then choose **"Add Filter" ** then choose **"Color Correction"**

---

### Post by klato on 2007-04-14
Cool, that worked!

---

