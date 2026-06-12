---
title: "[SOLVED] Specific Image Block Addon"
date: 2008-12-06
forum: The Cafe
---

### Post by Yuki_Nagato on 2008-12-06
I know that there are Mozilla Firefox add-ons to block images on websites.  All images, some images, big images, right-clicked images.  But these seem tied statically to the website.

I am looking for an image blocker that, upon the user seeing an image they wish to be unseen, the user somehow designates that image as blocked.  Now when any image is being loaded, on any website, it is checked against the database of user designated images for similarities to blocked images.  If the program believes that the image is sufficiently similar to a blocked image, it drops a place holder instead, a bit like NoScript and multimedia.

Anything similar to this idea?

---

### Post by klange on 2008-12-06
AdBlock does this.

Right Click > AdBlock Image > select the first URL with the exact name of the image

---

### Post by p_quarles on 2008-12-06
I think the OP is looking for something that preemptively blocks images that it has determined might match a pattern. I.e., "I have blocked an image that looks similar to a popular shock image -- do you want to see it? y/n"

That could be done, but I imagine it would be resource intensive, and probably not very reliable.

---

### Post by fatality_uk on 2008-12-06
For this to work, an analysis of the image or the tags attached to the image would have to be performed. It's unlikely that any system could be setup effectively. Take for instance you wanted to block an adult image by using a tag/name. The website owner would just change the tag/nameto something bland.

Sorry to say, but I think it would be a nightmare to manage.

---

### Post by wmcbrine on 2008-12-06
> **p_quarles said:**
> That could be done, but I imagine it would be resource intensive, and probably not very reliable.Understatement of the year. :)

---

### Post by Yuki_Nagato on 2008-12-06
Thank you very much for the input.

I was just thinking of something like this image resizing algorithm and how it snakes through the image on color channels.

_[http://www.youtube.com/watch?v=vIFCV2spKtg]("http://www.youtube.com/watch?v=vIFCV2spKtg")_ - A demonstration of the resizing technique.

And p_quarles nailed what I wanted.

---

