---
title: "Vector vs. Raster graphics?"
date: 2009-10-05
forum: The Cafe
---

### Post by dragos240 on 2009-10-05
What are the ups and downs of each. Vector as in inkscape, and raster as in GIMP. Why don't people use vector more?

Also, why do people use vector for icons more?

---

### Post by uberdonkey5 on 2009-10-05
I suppose it depends on detail of the vector and raster graphics and what image you are using. The vector is more scaleable.. in that as you enlarge it doesn't become pixilated. However, if you are not rescaling it, raster is fine since the screen is pixels anyway, so the raster graphics can be at same resolution as the screen.

---

### Post by MC707 on 2009-10-05
They use vector in icons more because unlike windows (in which .ico files contain 4~ icons of different sizes), vector icons just need to have a single vector file which automatically scalates.

Vector seems to be a little more difficult to work with (at least for me anyway). I tried Inkscape but I surrendered, I didn't understand how to work things out. Raster is a bit more simple to work (IMHO), or maybe it's because people are already used to working with raster, and just like windows users, they are hesitant to switch or use both.

Taken from [fileformat.info]("http://www.fileformat.info/mirror/egff/ch04_09.htm")
Advantages of vector files include the following:

    * Vector files are useful for storing images composed of line-based elements such as lines and polygons, or those that can be decomposed into simple geometrical objects, such as text. More sophisticated formats can also store 3D objects such as polyhedrons and wire-frame models.

    * Vector data can be easily scaled and otherwise manipulated to accommodate the resolution of a spectrum of output devices.

    * Many vector files containing only ASCII-format data can be modified with simple text editing tools. Individual elements may be added, removed, or changed without affecting other objects in the image.

    * It is usually easy to render vector data and save it to a bitmap format file, or, alternately, to convert the data to another vector format, with good results.

Some drawbacks of vector files include the following:

    * Vector files cannot easily be used to store extremely complex images, such as some photographs, where color information is paramount and may vary on a pixel-by-pixel basis.

    * The appearance of vector images can vary considerably depending upon the application interpreting the image. Factors include the rendering application's compatibility with the creator application and the sophistication of its toolkit of geometric primitives and drawing operations.

    * Vector data also displays best on vectored output devices such as plotters and random scan displays. High-resolution raster displays are needed to display vector graphics as effectively.

    * Reconstruction of vector data may take considerably longer than that contained in a bitmap file of equivalent complexity, because each image element must be drawn individually and in sequence.

[Check this article for some insight on vector vs raster.]("http://designwashere.com/design-battle-vector-vs-raster/")

---

### Post by markbuntu on 2009-10-05
A raster file is a static image, to change one item the entire image must be rewritten. A vector file is just a list, to change one item only that items desctiption needs to be changed and this can be done somwehere else since a vector file can be a just list of pointers to other files that describe the objects. It is a very powerful and effective method for rendering moving or changing objects but takes a lot more processing power, mental and machine.

All the cgi and animation studios use vector graphics almost exclusively.

---

