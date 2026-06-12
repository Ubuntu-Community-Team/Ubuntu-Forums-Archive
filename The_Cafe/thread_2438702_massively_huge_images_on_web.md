---
title: "massively huge images on web"
date: 2020-03-16
forum: The Cafe
---

### Post by Skaperen on 2020-03-16
this is not an ubuntu issue so i am here in the cafe.

i have a series of images i'd like to put on the web in full size.  my HD size screen only shows about 1/3 of one image.  i have t scroll down to see the rest of the image.  i have 429 of these images so HTML that simply loads them all is not going to work.  i've seen sites which load images as you scroll down, but they leave the images loaded so it will run out of memory or bog down the system swapping eve with this. are there any suggestions?

---

### Post by sdsurfer on 2020-03-17
>  i've seen sites which load images as you scroll down

Do you mean "lazy load?" This is done with jQuery/Javascript and I am pretty sure applies **only** to multiple images and content blocks. The idea is the content will fill up the viewport + a little more, detect the scroll position, and keep loading content as the user scrolls via Ajax requests. I find it annoying for various personal reasons. :-)

I really don't think lazy load will work with large images. You have a single image loaded as a file, it is one request to the server, that is what loads. The pixel ratio of the image to the pixel ratio of your viewport is what you are seeing. The browser will allow you to scale it to fill the window, that's about all you have to work with.

You could **try** a splicing scheme with lazy load where it loads pieces as you scroll, but this has it's own issues, namely, the user can't capture the entire image on download.

If you need to load them all on a single page, this is likely a GUI design issue. I would suggest automating a process that generates smaller versions for initial display, "clickable" to the high rez full version. This would amount to a faster load time and better end user experience.

---

### Post by Skaperen on 2020-03-17
these pictures need to be viewed in consecutive order.  i don't want to have a thumbnail index.  i can reduce the size of the images to page width and make that link to the full size image.  but, even then, it is too much to load every image at the same time.  i've seen web pages that do this, but have no idea how it would be done.

---

